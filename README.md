# Open Hardware Wallet Lab

This repository documents an early open-source hardware wallet learning project.

It was created to explore how private keys can be generated, stored, and used inside a dedicated hardware device instead of a general-purpose computer.

The goal of this project is educational: to understand the full path from hardware design, firmware, secure key handling, user confirmation, and transaction signing.

This project is not intended to be used as a production wallet or to store real assets.

## Why this project exists

Before building Havenlon, we explored the foundation of hardware-based key protection through a simple hardware wallet prototype.

That work led to a deeper question:

Protecting private keys is important.

But in high-risk systems, the harder problem is execution control.

A hardware wallet protects the key.

An execution control system defines when, how, and under what conditions that key is allowed to be used.

This repository focuses on the earlier foundation: learning and documenting how a dedicated signing device can be designed from the hardware level upward.

## Current progress

This project is being developed step by step, starting from the hardware layer.

### Stage 1: Power and LDO

Current hardware focus:

```text
USB-C power-only input
CC pull-down resistors
ESD protection
Battery / VBAT power path
PMOS-based power control
LDO-based power rails
```

Status:

```text
Stage 1: Power and LDO schematic
Status: Completed
```

### Stage 2: Battery Charging, Voltage Monitoring & External SPI Flash

Current hardware focus:

```text
Li-ion battery charging using MCP73831
Battery voltage monitoring through resistor divider and MCU ADC input
External SPI NOR Flash using W25Q64JVZPIQ
```

Status:

```text
Stage 2: Battery Charging, Voltage Monitoring & SPI Flash
Status: Completed
```

### Stage 3: Bluetooth, User Input, LEDs & Mechanical Basics

Current hardware focus:

```text
Bluetooth connectivity
User buttons and keypad
Status LEDs
Mechanical mounting and test points
```

Status:

```text
Stage 3: Bluetooth, Input, LEDs & Mechanical
Status: Completed
```

### Stage 4: OLED Display & SE05X Secure Element

Current hardware focus:

```text
OLED 1.3-inch FPC display interface
SE05X secure element interface
Auxiliary decoupling and pull-up components
```

Status:

```text
Stage 4: OLED Display & SE05X Secure Element
Status: Completed
```

### Stage 5: MCU & System Essentials

Current hardware focus:

```text
STM32L476RET6 MCU minimum system
Debug and boot configuration
NRST reset circuitry
Analog power filter
Crystal oscillator
Decoupling capacitors
Test points for measurement
```

Status:

```text
Stage 5: MCU & System Essentials
Status: Completed
```

### Stage 6: PCB Layout

The project has now entered the **PCB layout and routing stage**.

Current focus:

```text
Placement of components
Routing of critical power and signal traces
Ground and analog plane design
Test point accessibility
Preparation for prototype manufacturing
```

Status:

```text
Stage 6: PCB Layout
Status: Work in progress
```

These steps mark the transition from schematic design to physical board realization.

这些步骤标志着项目从原理图设计向实际 PCB 制造过渡。

## Project repository

The project repository is available here:

https://github.com/HavenlonLabs/open-hardware-wallet-lab

项目仓库地址：

https://github.com/HavenlonLabs/open-hardware-wallet-lab

---

## Repository structure

```text
docs/        Design notes and learning documents
hardware/    Schematics, PCB files, BOM, and Gerbers
firmware/    Firmware source code and drivers
enclosure/   3D enclosure files
tools/       Helper scripts and transaction tools
images/      Prototype and assembly images
```

---

## Safety notice

This project is for learning, research, and open hardware exploration only.

Do not use the current design to store real assets.

Do not treat the current schematic, firmware, or enclosure files as production-ready security hardware.

Security hardware requires careful review, testing, manufacturing control, firmware validation, and threat modeling before it can be used in real environments.

该项目仅用于学习、研究及开源硬件探索。

不要使用当前设计存储真实资产。

当前原理图、固件或外壳文件不能视为可直接使用的安全硬件。

真正的安全硬件需要严格的审查、测试、生产控制、固件验证和威胁建模，才能投入真实环境使用。

---

## Relationship to Havenlon

This repository is an open hardware learning lab.

It is not the Havenlon production hardware design.

Havenlon focuses on hardware-enforced execution control for AI agents, Web3 treasury operations, and non-custodial payment workflows.

This lab documents an earlier and simpler foundation: how hardware-based key protection and signing devices are built from the ground up.

---

## License

See [LICENSE](LICENSE)
