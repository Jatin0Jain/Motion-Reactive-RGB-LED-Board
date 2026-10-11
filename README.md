# Motion-Reactive RGB LED Board

A compact, USB- or battery-powered PCB that senses motion with an accelerometer and drives an RGB LED from a PIC microcontroller. This is my first PCB design, created in EasyEDA.

![3D render](images/3d-render.png)

## Status

- Design-only project: **not fabricated**
- DRC (Design Rule Check) passed with **zero errors**
- Firmware: not written yet

## What it does

The board reads motion and orientation data from an accelerometer over I2C. The microcontroller can use that data to mix colors on an RGB LED, so the LED reacts to how the board is moved or tilted.

## Features

- **Power input:** micro-USB (power only) or a battery connector, combined through a Schottky diode-OR power path
- **Regulation:** TPS76933 3.3 V LDO regulator, with a power indicator LED
- **Microcontroller:** PIC16F1823 with an ICSP header for programming
- **Sensing:** KXTJ3-1057 accelerometer on the I2C bus
- **Output:** RGB LED (common anode) switched by three N-channel MOSFETs, one per color channel
- **Input:** user push button
- **Expansion:** breakout header exposing I2C and the button signal

## Block overview

| Section | Main parts |
|---|---|
| Power | Micro-USB, battery connector, SBAT54CLT1G diode pair, TPS76933 LDO |
| MCU | PIC16F1823, ICSP header, user button |
| RGB LED | RGB LED, 3x N-channel MOSFETs, current-limiting resistors, LED header |
| Accelerometer | KXTJ3-1057 with decoupling capacitors |
| Header | I2C (SDA/SCL), button, and power breakout |

## Images

| Schematic | Layout |
|---|---|
| ![Schematic](images/schematic.png) | ![Layout](images/layout.png) |

## Repository structure

```
.
├── README.md
├── LICENSE
├── hardware/
│   ├── source/          EasyEDA project file
│   ├── gerbers/         Zipped Gerber files
│   ├── schematic.pdf    Schematic in PDF form
│   └── bom.csv          Bill of materials
└── images/              Renders and screenshots
```

## Tools

- [EasyEDA](https://easyeda.com/) for schematic capture, PCB layout, and the 3D view

## How to open the design

1. Download the project file from `hardware/source/`.
2. In EasyEDA, go to **File > Open** and select the file.
3. The Gerbers in `hardware/gerbers/` can be viewed in any Gerber viewer.

## What I learned

- Planning the power path first makes the rest of the design much easier
- A slim board forces careful component placement and routing
- Footprints and pin mappings must be checked against datasheets every time

## Next steps

- Write firmware for the PIC (read the accelerometer, map motion to RGB color)
- Possibly fabricate and test the board

## Feedback

I'm a beginner in hardware design, so suggestions and corrections are very welcome. Feel free to open an issue or reach out.

## License

Released under the MIT License (see `LICENSE`). Change this to CERN-OHL if you prefer a hardware-specific license.
