# Building an Open Hardware Wallet – Step 1: USB-C Power Input & 3.3V LDO Regulation
**一步一步做开源硬件钱包 — 第一步：USB-C 电源输入与 3.3V LDO 稳压**

## Introduction / 介绍
A hardware wallet does not start from firmware. It starts from power.

Before a private key can be generated, before a screen can show a transaction, and before a signature can be produced, the device needs a clean and predictable power path.

硬件钱包不是从固件开始的，而是从电源开始的。

在私钥生成、屏幕显示交易和签名执行之前，设备首先需要一条干净且可预测的电源路径。

## Current Progress / 当前进展
This is the first stage of the Open Hardware Wallet Lab. Today we focus on:

- USB-C power-only input
- CC1 / CC2 5.1kΩ pull-down resistors
- ESD protection on VBUS and CC lines
- Shield / GND connections
- PMOS-controlled battery path
- 3.3V LDO regulated output

这是 Open Hardware Wallet Lab 的第一步。今天我们重点完成：

- USB-C 电源输入（Power Only）
- CC1 / CC2 下拉电阻 5.1kΩ
- VBUS 和 CC 线 ESD 保护
- 屏蔽层 / GND 接地
- PMOS 电池供电路径
- 3.3V LDO 稳压输出

### Figure 1 / 图 1
**USB-C Power Input & ESD Protection**

![USB-C Power Input](images/usb_c_power.png)

This module handles USB-C VBUS input, CC pull-down resistors, ESD protection, and shield grounding.

该模块处理 USB-C VBUS 输入、CC 下拉电阻、ESD 保护以及屏蔽接地。

### Figure 2 / 图 2
**VBUS / VBAT to 3.3V LDO Regulator**

![VBUS to 3.3V LDO](images/vbat_ldo.png)

This module converts input power to a stable 3.3V rail using a PMOS-controlled LDO, including input and output filtering capacitors.

该模块通过 PMOS 控制的 LDO 将输入电源转换为稳定的 3.3V 电源轨，包括输入和输出滤波电容。

## Key Takeaways / 本阶段关键点
- USB-C CC pull-down resistors (5.1kΩ) signal that the device is a sink.
- ESD diodes protect both VBUS and CC lines from voltage spikes.
- PMOS switches allow safe battery input path control.
- LDO regulator ensures a stable 3.3V supply for downstream circuits.
- Reliable power delivery is the foundation for future MCU and secure element integration.

- USB-C CC 下拉电阻（5.1kΩ）表示这是用电设备（sink）。
- ESD 二极管保护 VBUS 和 CC 线，防止电压尖峰。
- PMOS 开关允许安全的电池供电路径控制。
- LDO 稳压器确保下游电路得到稳定的 3.3V 电源。
- 可靠的电源设计是后续 MCU 和安全芯片接入的基础。

## Next Steps / 下一步计划
The design is still a work in progress. Next hardware stages include:

- MCU minimum system
- Secure element interface
- Display and user input
- Full PCB layout
- Enclosure alignment

设计仍在进行中。下一阶段计划完成：

- MCU 最小系统
- 安全芯片接口
- 显示屏及用户按键
- PCB 完整布局
- 外壳对齐

## Repository Structure / 仓库结构
```
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

