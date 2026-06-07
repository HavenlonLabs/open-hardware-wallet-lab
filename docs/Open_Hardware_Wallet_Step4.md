# Building an Open Hardware Wallet — Step 4: OLED Display & SE05X Secure Element

**一步一步做开源硬件钱包 — 第四步：OLED 显示接口与 SE05X 安全芯片接口**

## Introduction / 介绍

After adding Bluetooth, user input, LEDs, and mechanical features, the next stage focuses on making the device **visually interactive and securely able to sign transactions**.

完成蓝牙、用户按键、LED 与机械基准模块之后，本阶段关注让设备具备 **显示交互能力和安全签名能力**。

These modules do not complete the wallet yet, but they are critical for a usable and secure prototype.

这些模块尚不能完成整个钱包功能，但对于可用和安全的工程样机至关重要。

---

## Project Repository / 项目仓库

The project repository is available here:

https://github.com/HavenlonLabs/open-hardware-wallet-lab

The repository will be updated step by step as the schematic, PCB, firmware, enclosure, and documentation evolve.

项目仓库地址：

https://github.com/HavenlonLabs/open-hardware-wallet-lab

后续原理图、PCB、固件、外壳和文档都会随着项目推进逐步更新。

## Current Progress / 当前进展

This stage includes two main hardware blocks:

- OLED 1.3-inch FPC display interface
- SE05X secure element interface

本阶段包括两个主要硬件模块：

- OLED 1.3 寸 FPC 显示接口
- SE05X 安全芯片接口

Auxiliary components such as decoupling capacitors, pull-ups, and resistors are added as required for stable operation.

为保证稳定工作，还加入了去耦电容、上拉电阻等辅助元件。

Status:

```text
Stage 4: OLED Display & SE05X Secure Element
Status: Work in progress
```

---

## Figure 1 / 图 1

**OLED 1.3-inch Display Interface**

![OLED Display Interface](images/sch_oled.png)

This module connects the OLED display via a 30-pin FPC connector.  

Key signals:

```text
OLED_SDA   I2C data line
OLED_SCL   I2C clock line
OLED_RES#  Reset pin
VDD        Logic power supply
VCC        Charge pump / panel driver voltage
GND        Ground
```

模块通过 30pin FPC 接口连接 OLED 显示屏。

主要信号：

```text
OLED_SDA   I2C 数据线
OLED_SCL   I2C 时钟线
OLED_RES#  复位引脚
VDD        逻辑电源
VCC        面板驱动/升压电压
GND        地
```

Decoupling capacitors are added between VDD/VCC and GND to stabilize the power rails.

VDD/VCC 和 GND 之间加入去耦电容，以稳定电源。

---

## Figure 2 / 图 2

**SE05X Secure Element Interface**

![SE05X Secure Element Interface](images/sch_se05x.png)

This module adds the SE05X secure element for cryptographic operations.

Key signals:

```text
SE05_SDA  I2C data line
SE05_SCL  I2C clock line
SE05_ENA  Enable signal
VCC       3.3V power
GND       Ground
```

该模块增加 SE05X 安全芯片，用于加密和签名操作。

主要信号：

```text
SE05_SDA  I2C 数据线
SE05_SCL  I2C 时钟线
SE05_ENA  启用信号
VCC       3.3V 电源
GND       地
```

Decoupling capacitors and pull-up resistors are included to ensure stable I2C communication.

加入去耦电容和上拉电阻，以保证 I2C 通信稳定。

---

## Key Takeaways / 本阶段关键点

- OLED display provides user feedback and visual interface.
- SE05X enables secure cryptographic operations.
- Decoupling capacitors are critical for stable power and I2C operation.
- Together, these modules move the device closer to a usable hardware wallet.

- OLED 显示屏提供用户反馈和可视化界面。
- SE05X 芯片提供安全加密操作能力。
- 去耦电容对稳定电源和 I2C 通信至关重要。
- 这些模块组合让设备更接近可用的硬件钱包。

---

## Current Hardware Stage / 当前硬件阶段

```text
Stage 1: USB-C Power Input & 3.3V LDO Regulation
Status: Completed

Stage 2: Battery Charging, Voltage Monitoring & External SPI Flash
Status: Completed

Stage 3: Bluetooth, User Input, Status LEDs & Mechanical Basics
Status: Completed

Stage 4: OLED Display & SE05X Secure Element
Status: Work in progress
```

```text
第一阶段：USB-C 电源输入与 3.3V LDO 稳压
状态：完成

第二阶段：锂电池充电、电池电压监测与外部 SPI Flash
状态：完成

第三阶段：蓝牙模块、用户输入、状态指示灯与机械基础
状态：完成

第四阶段：OLED 显示接口与 SE05X 安全芯片
状态：进行中
```

---

## Next Steps / 下一步计划

Future stages may include:

- MCU minimum system
- Reset and boot configuration
- Secure element integration
- User interface firmware
- Display controller firmware
- Full PCB layout
- Enclosure alignment

未来阶段可能包括：

- MCU 最小系统
- 复位与启动配置
- 安全芯片集成
- 用户界面固件
- 显示控制固件
- PCB 完整布局
- 外壳对齐

---

## Repository Structure / 仓库结构

```text
docs/        Design notes and learning documents
hardware/    Schematics, PCB files, BOM, and Gerbers
firmware/    Firmware source code and drivers
enclosure/   3D enclosure files
tools/       Helper scripts and transaction tools
images/      Prototype and assembly images
```

---

## Safety Notice / 安全提示

This project is for learning, research, and open hardware exploration only.

Do not use the current design to store real assets.

Do not treat the current schematic, firmware, or enclosure files as production-ready security hardware.

Security hardware requires careful review, testing, manufacturing control, firmware validation, and threat modeling before it can be used in real environments.

该项目仅用于学习、研究及开源硬件探索。

不要使用当前设计存储真实资产。

当前原理图、固件或外壳文件不能视为可直接使用的安全硬件。

真正的安全硬件需要严格的审查、测试、生产控制、固件验证和威胁建模，才能投入真实环境使用。