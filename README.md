# Arduino Nano Rebuild

A from-scratch redesign of an Arduino Nano-compatible board, designed in Altium Designer: schematic, PCB layout and 3D review.

## Overview

| Item | Detail |
|---|---|
| MCU | ATmega328P (TQFP-32) |
| USB-to-serial | FT232RL, micro-USB connector |
| Headers | 2 x 15-pin (P1, P2) in the Nano pinout, plus 2x3 ICSP header (J2) |
| Reset | Tactile switch with 1k pull-up, DTR auto-reset through the FT232RL |
| Indicators | Power LED, TX/RX LEDs driven from the FT232RL CBUS pins, D13 LED |
| Protection | Schottky diode (RB751S40) between USB 5 V and the board 5 V rail |
| Tools | Altium Designer |

## Schematic sections

- **Microcontroller:** ATmega328P with crystal and load capacitors, AVCC/AREF decoupling, 1k series resistors on RX/TX, D13 LED.
- **USB to serial:** FT232RL with USB connector, status LEDs and decoupling.
- **Power:** USB 5 V rail with Schottky diode and bulk/bypass capacitors; VIN input stage.
- **Headers:** Nano-compatible digital (D0-D13), analog (A0-A7), 5 V, 3V3, VIN, GND and RESET.

## Files

- `schematic/` Altium schematic and PDF export
- `pcb/` Altium PCB layout and 3D renders
- `images/` Top and bottom 3D views

## Status

Design stage only: schematic and PCB layout are complete and reviewed in 3D. The board has not been fabricated or tested.

## Notes / known issues

To verify before fabrication:

- VIN regulator: U2 is currently a MAX6101 (1.25 V reference); it needs to be replaced with a 5 V LDO or regulator for VIN to power the board.
- Crystal: X1 is labelled 32.768 kHz; the ATmega328P at the standard Arduino configuration needs a 16 MHz crystal with matching load capacitors.
