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
Status: Work in progress
```

These blocks are still simple, but they are critical for making the device more practical and independent.

A hardware wallet should not only receive power from USB-C. It should also support a battery path, battery status detection, voltage monitoring, and persistent storage for device-side data.

## Project repository

The project repository is available here:

https://github.com/HavenlonLabs/open-hardware-wallet-lab

The repository will be updated step by step as the schematic, PCB, firmware, enclosure, and documentation evolve.

## Repository structure

```text
docs/        Design notes and learning documents
hardware/    Schematics, PCB files, BOM, and Gerbers
firmware/    Firmware source code and drivers
enclosure/   3D enclosure files
tools/       Helper scripts and transaction tools
images/      Prototype and assembly images
```

## Hardware status

The hardware design now covers both the initial power stage and early battery and storage modules.

Current focus:

```text
Power input
Power protection
Battery charging path
Battery voltage monitoring
External SPI Flash
LDO regulation
```

The schematic and PCB files are still not production-ready.

At this stage, the goal is not to produce a finished wallet, but to document the engineering process from the first power block to a complete prototype.

## Planned hardware blocks

The project will continue to add hardware blocks gradually.

Planned or upcoming areas include:

```text
MCU minimum system
Reset and boot configuration
Secure element interface
Display interface
Buttons and user confirmation path
PCB layout
Enclosure alignment
Firmware bring-up
```

## Safety notice

This project is for learning, research, and open hardware exploration only.

Do not use the current design to store real assets.

Do not treat the current schematic, firmware, or enclosure files as production-ready security hardware.

Security hardware requires careful review, testing, manufacturing control, firmware validation, and threat modeling before it can be used in real environments.

## Relationship to Havenlon

This repository is an open hardware learning lab.

It is not the Havenlon production hardware design.

Havenlon focuses on hardware-enforced execution control for AI agents, Web3 treasury operations, and non-custodial payment workflows.

This lab documents an earlier and simpler foundation: how hardware-based key protection and signing devices are built from the ground up.

## License

See [LICENSE](LICENSE).
