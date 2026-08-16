# System Architecture

## Functional partition

```mermaid
flowchart TB
    USB[Micro-USB] --> ESD[USB ESD Protection]
    ESD --> FUSE[Resettable Fuse]
    FUSE --> V5[+5 V]
    V5 --> REG[AP2112K-3.3]
    REG --> V33[+3.3 V]

    V33 --> CH[CH340E USB-UART]
    V33 --> MCU[ESP32-WROOM-32E]
    CH <-->|UART0| MCU

    BOOT[BOOT / GPIO0] --> MCU
    EN[EN / RESET] --> MCU
    MCU --> SDA[GPIO21 / SDA]
    MCU --> SCL[GPIO22 / SCL]
    SDA --> IP[I²C Pull-ups + ESD]
    SCL --> IP
    MCU --> H[GPIO Headers]
```

## Power domains

| Rail | Source | Main loads |
|---|---|---|
| USB VBUS | Micro-USB | Input protection and 5 V domain |
| +5 V | VBUS through resettable fuse | AP2112K-3.3 input |
| +3.3 V | AP2112K-3.3 | ESP32-WROOM-32E, CH340E, I²C pull-ups, logic |
| GND | Board ground | Common return |

## Interfaces

- USB D+/D− → CH340E
- CH340E TXD/RXD ↔ ESP32 UART0
- GPIO21 → I²C SDA
- GPIO22 → I²C SCL
- GPIO0 → BOOT control
- EN → RESET control
- GPIO expansion → J2/J3

## Architecture summary

The design separates the USB input domain, regulated 3.3 V logic domain, USB-UART interface, ESP32 processing module, control circuitry, and external GPIO interfaces. The CH340E is powered from **+3.3 V**, while USB VBUS is used as the protected input source for the 5 V rail and the 3.3 V regulator.
