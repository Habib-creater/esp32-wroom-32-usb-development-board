# ESP32-WROOM-32 USB Development Board

A complete 2-layer ESP32-WROOM-32E development board designed in KiCad, integrating USB-to-UART programming, protected USB power input, 3.3 V regulation, BOOT/RESET control, GPIO expansion, and protected I²C interfaces.

![ESP32-WROOM-32 USB Development Board](docs/images/3d-front.png)

---

## Overview

This project presents the complete hardware design of a compact ESP32-WROOM-32E development board, including schematic capture, component selection, PCB layout, power distribution, interface protection, signal connectivity, design-rule verification, and manufacturing-data generation.

The design combines a Micro-USB interface, USB-to-UART bridge, regulated 3.3 V power architecture, ESP32 boot and reset circuitry, GPIO expansion headers, and protected I²C connectivity into a single 2-layer PCB.

The complete design package includes the KiCad schematic and PCB source files, bill of materials, manufacturing outputs, design documentation, and verification records.

---

## Key Features

- ESP32-WROOM-32E based embedded hardware platform
- Micro-USB connectivity for power and USB communication
- CH340E USB-to-UART bridge powered from the +3.3 V rail
- AP2112K-3.3 low-dropout voltage regulator
- Protected USB power input with resettable fuse
- Dedicated USB ESD protection
- BOOT / GPIO0 programming control
- EN / RESET control
- GPIO expansion through dual 14-pin headers
- GPIO21 / GPIO22 dedicated to I²C SDA / SCL
- 4.7 kΩ I²C pull-up resistors
- AXGD10603NR low-capacitance ESD/TVS protection on I²C lines
- Local IC decoupling and bulk power filtering
- ESP32 antenna-region and RF keepout consideration
- 2-layer PCB layout
- Complete KiCad schematic and PCB source files
- Bill of Materials (BOM)
- Gerber and drill manufacturing outputs
- Electrical Rules Check (ERC) completed
- Design Rules Check (DRC) completed

---

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

---

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
```

---

## Schematic

The complete electrical schematic is available as a PDF for detailed review.

**[📄 View ESP32-WROOM-32 Schematic PDF](docs/ESP32-WROOM-32-Schematic.pdf)**

The editable KiCad schematic source is also included:

**[Open KiCad Schematic](hardware/kicad/ESP32-WROOM-32.kicad_sch)**

---

## PCB Layout

The PCB is a compact **51.75 mm × 31.00 mm, 2-layer design** with a nominal thickness of 1.6 mm.

### Layout 1

![ESP32-WROOM-32 PCB Layout 1](docs/images/layout_1.png)

### Layout 2

![ESP32-WROOM-32 PCB Layout 2](docs/images/layout_2.png)

The PCB layout considers:

- ESP32 antenna region and RF keepout
- USB interface routing
- Power distribution
- Ground return paths
- Local IC decoupling
- Component placement
- Manufacturing clearances
- Board-edge constraints
- Signal routing

---

## PCB Routing

![ESP32-WROOM-32 PCB Routing](docs/images/pcb-routing.png)

---

## 3D Board Views

### Front View

![ESP32-WROOM-32 3D Front View](docs/images/3d-front.png)

### Back View

![ESP32-WROOM-32 3D Back View](docs/images/3d-back.png)

### 3D View 2

![ESP32-WROOM-32 3D View 2](docs/images/3d_2.png)

---

## Design Verification

The schematic and PCB were reviewed using KiCad's electrical and physical design verification tools.

### Electrical Rules Check (ERC)

ERC was completed to review:

- Power connectivity
- Pin electrical types
- Net connectivity
- Unconnected pins
- Driver conflicts
- Interface connections
- Electrical rule violations

### Design Rules Check (DRC)

PCB DRC was completed to review:

- Track clearances
- Pad clearances
- Via clearances
- Board-edge clearances
- Copper constraints
- Solder-mask constraints
- Connectivity
- Manufacturing-rule constraints

### Verification Summary

| Verification Item | Status |
|---|---|
| Schematic ERC | ✅ Completed |
| PCB DRC | ✅ Completed |
| Net Connectivity | ✅ Reviewed |
| Component Footprints | ✅ Reviewed |
| Board Dimensions | ✅ Verified |
| Manufacturing Outputs | ✅ Generated |
| PCB Fabrication | Not yet performed |
| Hardware Bring-up | Not yet performed |
| Electrical Measurements | Not yet performed |
| RF Validation | Not yet performed |

---

## Manufacturing Data

The repository includes the generated manufacturing data:

- Gerber copper layers
- Solder-mask layers
- Silkscreen layers
- Paste layers
- Board outline
- Drill files

**[View Manufacturing Documentation](docs/MANUFACTURING.md)**

---

## Bill of Materials

**[View Bill of Materials](hardware/bom/ESP32-WROOM-32_BOM.csv)**

---

## Repository Structure

```text
ESP32-WROOM-32-USB-Development-Board/
│
├── README.md
├── LICENSE
├── CHANGELOG.md
├── .gitignore
├── .gitattributes
│
├── hardware/
│   ├── kicad/
│   │   ├── ESP32-WROOM-32.kicad_pro
│   │   ├── ESP32-WROOM-32.kicad_sch
│   │   └── ESP32-WROOM-32.kicad_pcb
│   │
│   ├── bom/
│   │   └── ESP32-WROOM-32_BOM.csv
│   │
│   └── fabrication/
│       └── gerbers/
│
├── docs/
│   ├── ESP32-WROOM-32-Schematic.pdf
│   ├── SCHEMATIC.md
│   ├── ARCHITECTURE.md
│   ├── PINOUT.md
│   ├── MANUFACTURING.md
│   ├── VALIDATION.md
│   │
│   └── images/
│       ├── 3d-front.png
│       ├── 3d-back.png
│       ├── 3d_2.png
│       ├── layout_1.png
│       ├── layout_2.png
│       └── pcb-routing.png
│
├── project/
│   ├── design-notes.md
│   ├── repository-audit.md
│   └── SHA256SUMS.md
│
└── archive/
    └── original/
