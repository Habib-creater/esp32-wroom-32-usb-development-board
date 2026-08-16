# GPIO Header Pinout

The board exposes two 14-pin headers. Pin assignments below are taken from the PCB design nets.

## J2

| Pin | Net | Function / note |
|---:|---|---|
| 1 | GPIO22 | I²C SCL |
| 2 | TXD | ESP32 UART0 TX signal to USB-UART |
| 3 | RXD | ESP32 UART0 RX signal from USB-UART |
| 4 | GPIO21 | I²C SDA |
| 5 | GPIO19 | GPIO |
| 6 | GPIO18 | GPIO |
| 7 | GPIO5 | GPIO |
| 8 | TX | ESP32 TX breakout |
| 9 | RX | ESP32 RX breakout |
| 10 | GPIO4 | GPIO |
| 11 | GPIO2 | GPIO / boot-related usage should be considered in firmware |
| 12 | GPIO15 | GPIO / strapping considerations |
| 13 | GND | Ground |
| 14 | +3V3 | 3.3 V rail |

## J3

| Pin | Net | Function / note |
|---:|---|---|
| 1 | +5V | 5 V rail |
| 2 | GND | Ground |
| 3 | GPIO13 | GPIO |
| 4 | GPIO14 | GPIO |
| 5 | GPIO27 | GPIO |
| 6 | GPIO26 | GPIO |
| 7 | GPIO25 | GPIO |
| 8 | GPIO33 | GPIO / ADC capable |
| 9 | GPIO32 | GPIO / ADC capable |
| 10 | GPIO35 | Input-only GPIO / ADC capable |
| 11 | GPIO34 | Input-only GPIO / ADC capable |
| 12 | VN | ADC input (GPIO39) |
| 13 | VP | ADC input (GPIO36) |
| 14 | EN | Enable / reset |

## Dedicated control / interface signals

| Signal | ESP32 function |
|---|---|
| BOOT | GPIO0 bootstrapping control |
| EN | Chip enable / reset |
| SDA | GPIO21 |
| SCL | GPIO22 |
| RXD | UART0 RX |
| TXD | UART0 TX |

> GPIO34, GPIO35, GPIO36/VP, and GPIO39/VN are input-only on the classic ESP32. Firmware should account for their limitations.
