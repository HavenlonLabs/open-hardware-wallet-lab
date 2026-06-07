# Building an Open Hardware Wallet — Step 5: MCU & System Essentials

**一步一步做开源硬件钱包 — 第五步：MCU 与系统关键模块**

## **Introduction / 介绍**

With the display and secure element integrated in Step 4, the next stage focuses on **the microcontroller, essential power and clock modules, and system test points**.

完成显示与安全芯片集成后，本阶段关注 **微控制器、关键电源与时钟模块以及系统测试点**。

These blocks form the backbone of the hardware wallet and are required for minimal system functionality.

这些模块构成硬件钱包的核心骨架，是最小系统功能运行所必需的。

------

## **Project Repository / 项目仓库**

The project repository is available here:

https://github.com/HavenlonLabs/open-hardware-wallet-lab

The repository will be updated step by step as the schematic, PCB, firmware, enclosure, and documentation evolve.

项目仓库地址：

https://github.com/HavenlonLabs/open-hardware-wallet-lab

后续原理图、PCB、固件、外壳和文档都会随着项目推进逐步更新。

------

## **Current Progress / 当前进展**

This stage includes seven main hardware blocks:

- Debug interface
- Boot configuration with test points
- NRST reset circuitry
- Analog power filter
- Crystal oscillator
- Decoupling capacitors
- STM32L476RET6 MCU minimum system

本阶段包括七个主要硬件模块：

- 调试接口
- 带测试点的启动配置
- NRST 复位电路
- 模拟电源滤波
- 晶振模块
- 去耦电容
- STM32L476RET6 MCU 最小系统

Auxiliary components such as pull-up resistors and decoupling capacitors are included as required for stable operation.

为保证稳定工作，还加入了上拉电阻和去耦电容等辅助元件。

Status:

```text
Stage 5: MCU & System Essentials
Status: Work in progress
```

------

## **Figure 1 / 图 1**

**Debug Interface**

Key signals:

```text
NRST      Reset line
DBG_TX    Debug UART transmit
DBG_RX    Debug UART receive
SWDCLK    SWD clock
SWDIO     SWD data
GND       Ground
+3V3      Power
```

主要信号：

```text
NRST      复位引脚
DBG_TX    调试 UART 发射
DBG_RX    调试 UART 接收
SWDCLK    SWD 时钟
SWDIO     SWD 数据
GND       地
+3V3      电源
```

------

## **Figure 2 / 图 2**

**Boot Configuration with Test Points**

Key signals:

```text
BOOT0     Boot mode selection
TP1, TP2  Test points for debugging
R27       Pull-down resistor
```

主要信号：

```text
BOOT0     启动模式选择
TP1, TP2  调试测试点
R27       下拉电阻
```

------

## **Figure 3 / 图 3**

**NRST Reset Circuitry**

Key signals:

```text
NRST      Reset line to MCU
TP3, TP4  Test points
R28       Pull-up resistor
C32       Reset capacitor
GND       Ground
```

主要信号：

```text
NRST      MCU 复位引脚
TP3, TP4  测试点
R28       上拉电阻
C32       复位电容
GND       地
```

------

## **Figure 4 / 图 4**

**Analog Power Filter**

Key signals:

```text
+3V3      Input power
L1        Inductor
C33, C34  Filter capacitors
VDDA      Analog MCU power
R29       0Ω resistor for grounding / jumper
GND       Ground
```

主要信号：

```text
+3V3      输入电源
L1        电感
C33, C34  滤波电容
VDDA      MCU 模拟电源
R29       0Ω 接地/跳线
GND       地
```

------

## **Figure 5 / 图 5**

**Crystal Oscillator: 8 MHz**

Key signals:

```text
Y1        8 MHz crystal
C30, C31  Load capacitors
OSCIN     MCU oscillator input
OSCOUT    MCU oscillator output
GND       Ground
```

主要信号：

```text
Y1        8 MHz 晶振
C30, C31  负载电容
OSCIN     MCU 晶振输入
OSCOUT    MCU 晶振输出
GND       地
```

------

## **Figure 6 / 图 6**

**Decoupling Capacitors**

Decoupling capacitors are connected across multiple power pins of the MCU to ensure stable voltage and reduce noise.

去耦电容跨接 MCU 多个电源引脚，以保证电压稳定并降低噪声。

------

## **Figure 7 / 图 7**

**MCU: STM32L476RET6 Minimum System**

This module integrates the microcontroller with all essential signals and power rails.

该模块集成了微控制器及所有必要信号和电源线路。

Key signals:

```text
PA0-PA15, PB0-PB15, PC0-PC15, PD2  MCU I/Os
VBAT, VDD, VDDA, VSS, GNDA      Power and ground pins
Boot, Reset, Debug UART, SWD     Control and programming interfaces
```

主要信号：

```text
PA0-PA15, PB0-PB15, PC0-PC15, PD2  MCU I/O
VBAT, VDD, VDDA, VSS, GNDA        电源与地
Boot, Reset, 调试 UART, SWD       控制与烧录接口
```

------

## **Key Takeaways / 本阶段关键点**

- Provides the minimal system to operate the MCU.
- Includes reset, boot, debug, power filtering, and oscillator modules.
- Decoupling capacitors stabilize MCU voltage rails.
- Together, these modules complete the functional core of the hardware wallet prototype.
- 提供 MCU 最小系统功能。
- 包含复位、启动、调试、电源滤波和晶振模块。
- 去耦电容稳定 MCU 电源。
- 这些模块组合完成硬件钱包原型的核心功能。

------

## **Current Hardware Stage / 当前硬件阶段**

```text
Stage 1: USB-C Power Input & 3.3V LDO Regulation
Status: Completed

Stage 2: Battery Charging, Voltage Monitoring & External SPI Flash
Status: Completed

Stage 3: Bluetooth, User Input, Status LEDs & Mechanical Basics
Status: Completed

Stage 4: OLED Display & SE05X Secure Element
Status: Completed

Stage 5: MCU & System Essentials
Status: Work in progress
第一阶段：USB-C 电源输入与 3.3V LDO 稳压
状态：完成

第二阶段：锂电池充电、电池电压监测与外部 SPI Flash
状态：完成

第三阶段：蓝牙模块、用户输入、状态指示灯与机械基础
状态：完成

第四阶段：OLED 显示接口与 SE05X 安全芯片
状态：完成

第五阶段：MCU 与系统关键模块
状态：进行中
```

------

## **Next Steps / 下一步计划**

Future stages may include:

- MCU firmware development
- Peripheral integration
- Full PCB layout
- Enclosure alignment

未来阶段可能包括：

- MCU 固件开发
- 外设集成
- PCB 完整布局
- 外壳对齐

------

## **Repository Structure / 仓库结构**

```text
docs/        Design notes and learning documents
hardware/    Schematics, PCB files, BOM, and Gerbers
firmware/    Firmware source code and drivers
enclosure/   3D enclosure files
tools/       Helper scripts and transaction tools
images/      Prototype and assembly images
```

------

## **Safety Notice / 安全提示**

This project is for learning, research, and open hardware exploration only.

Do not use the current design to store real assets.

Do not treat the current schematic, firmware, or enclosure files as production-ready security hardware.

Security hardware requires careful review, testing, manufacturing control, firmware validation, and threat modeling before it can be used in real environments.

该项目仅用于学习、研究及开源硬件探索。

不要使用当前设计存储真实资产。

当前原理图、固件或外壳文件不能视为可直接使用的安全硬件。

真正的安全硬件需要严格的审查、测试、生产控制、固件验证和威胁建模，才能投入真实环境使用。