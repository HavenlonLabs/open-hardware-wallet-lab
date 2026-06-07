# Building an Open Hardware Wallet – Step 2: Battery Charging, Voltage Monitoring & External SPI Flash

**一步一步做开源硬件钱包 — 第二步：锂电池充电、电池电压监测与外部 SPI Flash**

## Introduction / 介绍

After finishing the first power layer, the next step is to make the device more practical as a standalone hardware wallet.

A hardware signing device should not only receive power from USB-C. It also needs a battery charging path, a way to monitor battery voltage, and non-volatile storage for firmware data, configuration, logs, or future wallet-related metadata.

完成第一步电源层之后，下一步是让这个设备更接近一个可以独立工作的硬件钱包。

一个硬件签名设备不应该只依赖 USB-C 供电。它还需要电池充电路径、电池电压监测能力，以及用于固件数据、配置、日志或未来钱包相关元数据的非易失性存储。

This is the second stage of the Open Hardware Wallet Lab.

这是 Open Hardware Wallet Lab 的第二阶段。

## Current Progress / 当前进展

In this stage, we add three basic hardware blocks:

- Li-ion battery charging
- Battery voltage monitoring
- External SPI NOR Flash memory

本阶段增加三个基础硬件模块：

- 锂电池充电
- 电池电压监测
- 外部 SPI NOR Flash 存储

These blocks are still simple, but they are important for building a real device instead of just a powered circuit board.

这些模块看起来很基础，但它们决定了这个项目是否能从一块通电电路板，逐步变成一个真正的独立硬件设备。

## Figure 1 / 图 1

**Li-ion Battery Charging**

![Li-ion Battery Charging](images/sch_bat_charging.png)

This module uses the MCP73831 Li-ion battery charger IC.

The USB-C VBUS rail provides the charging input. The charger outputs to the VBAT rail, which can later be used as the battery power source for the device.

该模块使用 MCP73831 锂电池充电管理芯片。

USB-C 的 VBUS 电源轨作为充电输入，充电芯片输出到 VBAT 电源轨，后续可以作为设备的电池供电来源。

The PROG resistor sets the charging current. In this design, a 4.7kΩ resistor is used as the programming resistor.

PROG 电阻用于设置充电电流。本设计中使用 4.7kΩ 作为充电电流设定电阻。

The STAT pin is exposed as `BAT_STAT`, which can later be connected to an MCU GPIO to detect charging status.

STAT 引脚被命名为 `BAT_STAT`，后续可以接入 MCU GPIO，用于检测充电状态。

Main signals in this block:

```text
VBUS      USB-C input power
VBAT      Battery power rail
BAT_STAT  Battery charger status signal
GND       System ground
```

本模块主要信号：

```text
VBUS      USB-C 输入电源
VBAT      电池电源轨
BAT_STAT  电池充电状态信号
GND       系统地
```

## Figure 2 / 图 2

**Battery Voltage Monitoring**

![Battery Voltage Monitoring](images/sch_bat_monitoring.png)

This module provides a simple battery voltage sensing path.

VBAT is divided down through a resistor divider and sent to the MCU ADC input as `BAT_ADC`.

该模块提供一个简单的电池电压采样路径。

VBAT 通过电阻分压后，输出为 `BAT_ADC`，后续可以连接到 MCU 的 ADC 输入引脚。

A small capacitor is added near the ADC signal to reduce noise and make the sampled voltage more stable.

在 ADC 采样信号附近加入一个小电容，用于降低噪声，让采样电压更加稳定。

Main signals in this block:

```text
VBAT     Battery voltage input
BAT_ADC  Battery voltage ADC signal
GND      System ground
```

本模块主要信号：

```text
VBAT     电池电压输入
BAT_ADC  电池电压 ADC 采样信号
GND      系统地
```

This block allows firmware to estimate battery level, detect low battery conditions, and eventually display battery status to the user.

该模块可以让固件估算电池电量、检测低电压状态，并在未来把电池状态显示给用户。

## Figure 3 / 图 3

**External SPI NOR Flash Memory**

![External SPI Flash Memory](images/sch_spi_flash.png)

This module adds an external SPI NOR Flash memory.

The selected part is `W25Q64JVZPIQ`, a 64Mbit SPI Flash device.

该模块增加一颗外部 SPI NOR Flash 存储器。

当前选型为 `W25Q64JVZPIQ`，这是一颗 64Mbit 的 SPI Flash 芯片。

The flash is connected through a standard SPI interface:

```text
FLASH_CS#    Chip select
FLASH_CLK    SPI clock
FLASH_MOSI   MCU to Flash data
FLASH_MISO   Flash to MCU data
```

Flash 通过标准 SPI 接口连接：

```text
FLASH_CS#    片选信号
FLASH_CLK    SPI 时钟
FLASH_MOSI   MCU 到 Flash 的数据线
FLASH_MISO   Flash 到 MCU 的数据线
```

The `WP#` and `HOLD#/RESET` pins are pulled up to 3.3V so that the flash stays in normal operating mode.

`WP#` 和 `HOLD#/RESET` 引脚通过电阻上拉到 3.3V，让 Flash 保持在正常工作模式。

This external storage can later be used for non-sensitive configuration, logs, firmware metadata, or other device-side persistent data.

这颗外部存储器后续可以用于非敏感配置、日志、固件元数据，或其他设备侧持久化数据。

## Key Takeaways / 本阶段关键点

- A standalone hardware wallet needs a battery charging path, not only USB power.
- The MCP73831 provides a simple Li-ion charging solution.
- Battery voltage monitoring allows firmware to estimate battery level.
- External SPI NOR Flash provides persistent storage for device-side data.
- Clear signal naming makes later MCU integration easier.

- 一个独立硬件钱包不能只依赖 USB 供电，还需要电池充电路径。
- MCP73831 提供了一个简单的锂电池充电方案。
- 电池电压监测可以让固件估算电池电量。
- 外部 SPI NOR Flash 为设备侧数据提供持久化存储。
- 清晰的信号命名可以让后续 MCU 接入更简单。

## Current Hardware Stage / 当前硬件阶段

```text
Stage 1: USB-C Power Input & 3.3V LDO Regulation
Status: Draft completed

Stage 2: Battery Charging, Voltage Monitoring & External SPI Flash
Status: Work in progress
```

```text
第一阶段：USB-C 电源输入与 3.3V LDO 稳压
状态：草图完成

第二阶段：锂电池充电、电池电压监测与外部 SPI Flash
状态：进行中
```

## Next Steps / 下一步计划

The design is still a work in progress. Next hardware stages may include:

- MCU minimum system
- Reset and boot configuration
- Secure element interface
- Display and user input
- Buttons and confirmation path
- Full PCB layout
- Enclosure alignment

设计仍在进行中。下一阶段可能包括：

- MCU 最小系统
- 复位与启动配置
- 安全芯片接口
- 显示屏与用户输入
- 按键与确认路径
- PCB 完整布局
- 外壳对齐

## Repository Structure / 仓库结构

```text
docs/        Design notes and learning documents
hardware/    Schematics, PCB files, BOM, and Gerbers
firmware/    Firmware source code and drivers
enclosure/   3D enclosure files
tools/       Helper scripts and transaction tools
images/      Prototype and assembly images
```

## Safety Notice / 安全提示

This project is for learning, research, and open hardware exploration only.

Do not use the current design to store real assets.

Do not treat the current schematic, firmware, or enclosure files as production-ready security hardware.

Security hardware requires careful review, testing, manufacturing control, firmware validation, and threat modeling before it can be used in real environments.

该项目仅用于学习、研究及开源硬件探索。

不要使用当前设计存储真实资产。

当前原理图、固件或外壳文件不能视为可直接使用的安全硬件。

真正的安全硬件需要严格的审查、测试、生产控制、固件验证和威胁建模，才能投入真实环境使用。

## Project Repository / 项目仓库

The project repository is available here:

https://github.com/HavenlonLabs/open-hardware-wallet-lab

The repository will be updated step by step as the schematic, PCB, firmware, enclosure, and documentation evolve.

项目仓库地址：

https://github.com/HavenlonLabs/open-hardware-wallet-lab

后续原理图、PCB、固件、外壳和文档都会随着项目推进逐步更新。