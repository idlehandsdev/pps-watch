# PPS Watch  

### The Most Accurate Watch the Doesn't Tell Time.

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

- ** BOM needs updated missing a few components! - https://www.digikey.ca/en/mylists/list/XIH163JVIJ

## Watch Assembly

### 3D Printed Parts

Print the following files from the `CAD/` folder:

- `CAD/pcb_frame_mount.stl` -- frame that holds the PCB
- `CAD/watch_band_mount.stl` -- mounts the band to the frame

### Watch Band

Any standard 22mm watch band works. Tested with:

[Bandini Nylon Sports Watch Band Strap 22mm](https://www.amazon.com/dp/B09R2BVRWQ)

### Hardware

- 2 x M2x6mm Flat Head Plastic Threading Screws to mount body to strap mount.
- 2 x M3x35mm Round Head Machine Screws to mount strap. Just Thread into the plastic snugly.
---

*Felix Corp -- Idle Hands Dev R&D Division*
*Asset Tag: FC-IDH-UTC-001*