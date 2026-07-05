# PPS Watch  

### The Most Accurate Watch that Doesn't Tell Time.

[![Watch the video](https://img.youtube.com/vi/AHSqyuOPpf0/0.jpg)](https://youtu.be/AHSqyuOPpf0)


---

## What it does

- Receives GPS , achieves position/time fix
- Outputs 1PPS (one pulse per second) on the GPS module's hardware TIMEPULSE pin, silent until locked, active at 1Hz once locked
- Distributes that PPS signal across a BNC connector via buffered outputs
- Accepts an external PPS reference, compares it against the GPS PPS via a hardware XOR phase comparator, with LED indicators for PPS presence and phase offset
- No microcontroller. No firmware. The GPS module's hardware PPS pin drives the LEDs and BNC outputs directly through logic buffers.

## Hardware

- **GPS module:** u-blox MAX-M10S
- **Antenna:** External via SMA, no onboard antenna. Direct-mount stub antennas (Quectel YEGT001AA right-angle / YEGT002AA straight) screw directly onto the SMA connector, no cable
- **Buffering:** 2x 74HC125 quad buffer (GPS output side, external input side)
- **Comparator:** 74AHC1G86 single XOR gate
- **Indicators:** 0805 SMD LEDs -- 1x red (PPS), 2x green (fix / external PPS)
- **Power:** CR2450 coin cell, switched via SW1, V_BCKP always connected
- **Config port:** Qwiic (I2C) for one-time setup via u-center if needed
- **Connectors:** 2x BNC, 1x SMA (antenna), 1x Qwiic

See the schematic for full signal flow and the BOM for part numbers.

## CAD

This is a KiCad project. PCB mechanical design and 3D assembly were done in Fusion 360.

**Fusion 360 share link:** https://a360.co/4xXmWnG

## BOM

- ** BOM should be up to date! - https://www.digikey.ca/en/mylists/list/XIH163JVIJ
- ** R2 was a 0R resistor, but the BOM now includes a PTC instead.


| Reference | Qty | Value | Digikey Part No. |
|---|---|---|---|
| AE3 | 1 | YEGT002AA | [2958-YEGT002AA-ND](https://www.digikey.com/en/products/detail/quectel/YEGT002AA/17101891) |
| BT2 | 1 | BU2450SM-JJ-G | [BU2450SM-JJ-GCT-ND](https://www.digikey.com/en/products/detail/mpd-memory-protection-devices/BU2450SM-JJ-GTR/3028728) |
| C1 | 1 | 100pF C0G | 311-1111-1-ND |
| C2, C3, C4, C5 | 4 | 0.1uF | 311-4348-1-ND |
| D1 | 1 | LED Red 0805 | 160-1415-1-ND |
| D2 | 1 | PESD0402-140 | [PESD0402-140CT-ND](https://www.digikey.com/en/products/detail/littelfuse-inc/PESD0402-140/1968526) |
| D3, D4 | 2 | LED Green 0805 | [475-LGR971-KN-1TR-ND](https://www.digikey.com/en/products/detail/LG%20R971-KN-1/475-1410-1-ND/1802598) |
| J1, J4 | 2 | BNC 2466267-1 | 17-2466267-1-ND |
| J2 | 1 | CONSMA002-SMD-G-T | 343-CONSMA002-SMD-G-TCT-ND |
| J6 | 1 | Qwiic | 1568-14417-ND |
| L1 | 1 | Ferrite Bead | 490-1040-1-ND |
| R1 | 1 | 470R | 311-470ARCT-ND |
| R2 | 1 | 500mA PolyFuse | F2772CT-ND |
| R3, R6 | 2 | 10K | 311-10KARCT-ND |
| R4, R5 | 2 | 330R | 311-330ARCT-ND |
| SW1 | 1 | Power Switch SPDT | 401-2016-1-ND |
| U1 | 1 | MAX-M10S | 672-MAX-M10S-00BTR-ND |
| U3, U6 | 2 | 74HC125D | [74HC125DCT-ND](https://www.digikey.com/en/products/detail/toshiba-semiconductor-and-storage/74HC125D/6198795) |
| U5 | 1 | 74AHC1G86 | [296-1094-1-ND](https://www.digikey.com/en/products/detail/texas-instruments/SN74AHC1G86DBVR/276738) |

## Watch Assembly

### 3D Printed Parts

Print the following files from the `CAD/` folder:

- `CAD/pcb_frame_mount.stl` -- frame that holds the PCB
- `CAD/watch_band_mount.stl` -- mounts the band to the frame

### Watch Band

Any standard 22mm watch band works. Tested with:

[Bandini Nylon Sports Watch Band Strap 22mm](https://www.amazon.com/dp/B09R2BVRWQ)

### Hardware

- 2 x M2x6mm Flat Head Plastic Threading Screws to mount body to strap mount. - https://www.mcmaster.com/90485A415/
- 2 x M3x6mm Pan Head Plastic Threading Screws for mounting PCB to Body - https://www.mcmaster.com/99461A939/
- 2 x M3x35mm Round Head Machine Screws to mount strap. Just Thread into the plastic snugly https://www.mcmaster.com/92000A134/
---

*Felix Corp -- Idle Hands Dev R&D Division*
*Asset Tag: FC-IDH-UTC-001*