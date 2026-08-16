# ESP32-WROOM-32 USB Development Board

A complete 2-layer ESP32-WROOM-32E development board designed in KiCad, integrating USB-to-UART programming, protected USB power input, 3.3 V regulation, BOOT/RESET control, GPIO expansion, and protected I²C interfaces.

![ESP32-WROOM-32 USB Development Board](docs/images/3d-front.png)

## Overview

This project presents the complete hardware design of a compact ESP32-WROOM-32E development board, including schematic capture, component selection, PCB layout, power distribution, interface protection, connectivity, and manufacturing-data generation.

The design combines a USB interface, USB-to-UART bridge, regulated 3.3 V power architecture, ESP32 boot and reset circuitry, GPIO expansion headers, and protected I²C connectivity into a single 2-layer PCB.

## Key Features

- ESP32-WROOM-32E based embedded hardware platform
- Micro-USB connectivity for power and USB communication
- CH340E USB-to-UART bridge powered from the 3.3 V rail
- AP2112K-3.3 low-dropout voltage regulator
- Protected USB power input with resettable fuse
- Dedicated USB ESD protection
- BOOT / GPIO0 programming control
- EN / RESET control
- GPIO expansion through dual 14-pin headers
- GPIO21 / GPIO22 dedicated to I²C SDA / SCL
- 4.7 kΩ I²C pull-up resistors
- AXGD10603NR low-capacitance ESD protection on I²C lines
- ESP32 antenna keepout consideration in PCB layout
- Local IC decoupling and bulk power filtering
- Complete KiCad schematic and PCB design
- Bill of Materials (BOM)
- Gerber and drill manufacturing outputs
- ERC and DRC verification completed

## Project Specifications

| Parameter | Specification |
|---|---|
| MCU / Module | Espressif ESP32-WROOM-32E-H4 |
| USB Connector | Micro-USB, Molex 105017-0001 |
| USB-UART Bridge | CH340E |
| CH340E Supply | +3.3 V |
| Voltage Regulator | AP2112K-3.3 |
| USB ESD Protection | SP0503BAHT |
| I²C ESD Protection | 2 × AXGD10603NR |
| I²C SDA | GPIO21 |
| I²C SCL | GPIO22 |
| I²C Pull-ups | 4.7 kΩ to +3.3 V |
| Logic Voltage | 3.3 V |
| PCB Layers | 2 |
| PCB Thickness | 1.6 mm nominal |
| Board Dimensions | 51.75 mm × 31.00 mm |
| CAD Platform | KiCad 9.x |
| Design Verification | ERC + DRC completed |
| Hardware Status | PCB not yet fabricated |

## Functional Architecture

```mermaid
flowchart LR
    USB[Micro-USB] --> ESD[USB ESD Protection]
    ESD --> FUSE[500 mA Resettable Fuse]
    FUSE --> V5[+5 V Rail]

    V5 --> LDO[AP2112K-3.3]
    LDO --> V3[+3.3 V Rail]

    V3 --> ESP[ESP32-WROOM-32E]
    V3 --> UART[CH340E USB-UART]
    V3 --> I2C[I²C Pull-ups]

    UART <-->|UART0| ESP

    BOOT[BOOT / GPIO0] --> ESP
    RESET[EN / RESET] --> ESP

    I2C --> SDA[GPIO21 / SDA]
    I2C --> SCL[GPIO22 / SCL]

    SDA --> ESP
    SCL --> ESP

    ESP --> GPIO[GPIO Expansion Headers]
