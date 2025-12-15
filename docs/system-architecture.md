# System Architecture

## High-Level Overview
The G27 Universal USB Adapter firmware is designed as a modular embedded system that dynamically adapts its behavior based on connected hardware and selected operating mode.

At boot time, the firmware determines the operating mode and builds the appropriate USB HID descriptor, ensuring maximum compatibility and clean integration with the host system.

---

## Architecture Diagram (Textual)

[ Power On / Reset ]
          |
          v
[ Read Mode Buttons ]
          |
          v
[ Select Operating Mode ]
          |
          v
[ Load EEPROM Calibration ]
          |
          v
[ Create USB HID Descriptor ]
          |
          v
[ Main Loop ]
     |        |
     |        +--> Pedal Processing (Analog Axes)
     |
     +--> Shifter Processing
            |--> Shift Register (Buttons)
            |--> Analog X/Y Axes
            |--> Gear Logic
            |--> Optional Calibration Routine
          |
          v
[ USB HID Reports to Host ]

## Core Responsibilities (Summary)
- Mode selection at boot using hardware buttons
- Dynamic USB HID descriptor creation
- Analog pedal processing
- Shifter input processing (Logitech and DIY)
- Optional EEPROM-based calibration

