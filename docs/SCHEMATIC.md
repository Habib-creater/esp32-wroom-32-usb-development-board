# Schematic

The canonical schematic source is:

`hardware/kicad/ESP32-WROOM-32.kicad_sch`

The schematic represents the electrical architecture of the academic ESP32 development-board project. An earlier exported PDF is retained under `archive/original/` for traceability.

## Functional sections

1. USB input and ESD protection
2. 5 V input protection and distribution
3. 3.3 V regulation
4. USB-to-UART bridge (**CH340E powered from +3.3 V**)
5. ESP32-WROOM-32E module
6. BOOT / GPIO0 control
7. EN / RESET control
8. I²C pull-ups and ESD protection
9. GPIO expansion headers

## Key electrical domains

- USB VBUS forms the protected input / +5 V domain.
- AP2112K-3.3 generates the +3.3 V logic rail.
- The ESP32-WROOM-32E and CH340E operate from the +3.3 V domain.
- GPIO21 and GPIO22 form the I²C SDA/SCL interface.
