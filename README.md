#PPS Watch
###A GPS-disciplined 1PPS reference wearable.

It doesn't tell you the time. It tells you exactly when each second begins, synchronized to the same atomic clocks that run GPS, the internet, cellular networks, and financial systems -- accurate to within ~100ns of UTC. That signal comes out on a BNC connector. Two of them, actually.

---

## What it does

- Receives GPS , achieves position/time fix
- Outputs 1PPS (one pulse per second) on the GPS module's hardware TIMEPULSE pin, silent until locked, active at 1Hz once locked
- Distributes that PPS signal across two BNC connectors via buffered outputs
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

## Status



---

*Felix Corp -- Idle Hands Dev R&D Division*
*Asset Tag: FC-IDH-UTC-001*