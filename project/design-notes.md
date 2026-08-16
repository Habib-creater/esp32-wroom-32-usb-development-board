# Design Notes

## Scope

This academic project presents the design of a compact ESP32-WROOM-32 development board integrating USB programming, serial communication, regulated 3.3 V power, GPIO access, and protected I²C connectivity.

## Primary components

- ESP32-WROOM-32E-H4
- CH340E USB-UART bridge (**+3.3 V supply**)
- AP2112K-3.3 LDO
- SP0503BAHT USB ESD protection
- AXGD10603NR I²C ESD/TVS protection
- Molex 105017-0001 Micro-USB connector

## Board geometry

- 2-layer PCB
- 51.75 mm × 31.00 mm outline
- 1.6 mm nominal thickness

## Design considerations

- GPIO12 is an ESP32 strapping pin and its configuration is treated as a design consideration.
- D4/D5 use AXGD10603NR as low-capacitance ESD/TVS protection for the I²C lines.
- The ESP32 antenna region is treated as an RF-sensitive area in the PCB layout.
- The CH340E is connected to the regulated +3.3 V logic domain.

## Project status

The repository represents the academic CAD design and associated engineering files. The physical board has not been fabricated or hardware-tested.
