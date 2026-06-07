# Open Hardware Wallet Lab

This repository documents an early open-source hardware wallet learning project.

It was created to explore how private keys can be generated, stored, and used inside a dedicated hardware device instead of a general-purpose computer.

The goal of this project is educational:
to understand the full path from hardware design, firmware, secure key handling, user confirmation, and transaction signing.

This project is not intended to be used as a production wallet or to store real assets.

## Why this project exists

Before building Havenlon, we explored the foundation of hardware-based key protection through a simple hardware wallet prototype.

That work led to a deeper question:

Protecting private keys is important.
But in high-risk systems, the harder problem is execution control.

## Repository structure

```text
docs/        Design notes and learning documents
hardware/    Schematics, PCB files, BOM, and Gerbers
firmware/    Firmware source code and drivers
enclosure/   3D enclosure files
tools/       Helper scripts and transaction tools
images/      Prototype and assembly images
