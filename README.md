# DIY Force Feedback Steering Wheel

> A high-performance, budget-friendly 24V Direct Drive / Belt-Driven Sim Racing Wheel powered by Arduino Pro Micro, BTS7960 motor driver, and an RS-775 motor.

---

## Project Overview

[INSERT A HIGH-QUALITY GIF OF THE WHEEL SPINNING IN FORZA / ASSETTO CORSA HERE]

### Key Specifications
* **Brain:** Arduino Pro Micro (ATmega32U4)
* **Motor Driver:** BTS7960 43A H-Bridge
* **Motor:** RS-775 High-Speed Motor @ 24V
* **Drive System:** 1:4 Belt Reduction (20T to 80T HTD-3M Pulleys)
* **Encoder:** 600 PPR Optical Rotary Encoder
* **Compatibility:** PC (Forza Horizon 5, Assetto Corsa, iRacing) via EMC Lite / Forza EmuWheel

---

## Bill of Materials (BOM)

| Component | Quantity | Approx. Cost | Notes |
| :--- | :--- | :--- | :--- |
| Arduino Pro Micro (5V/16MHz) | 1 | $6 | Must be ATmega32U4 |
| BTS7960 43A Motor Driver | 1 | $9 | Requires heatsink cooling |
| 24V 15A SMPS Power Supply | 1 | $18 | Powers the 775 motor |
| 600 PPR Optical Encoder | 1 | $12 | Channels A & B to Pins 0 & 1 |
| 10k Potentiometers | 2-3 | $3 | Gas, Brake, Clutch pedals |

---

## CAD & 3D Print Downloads

All files are designed for easy printing in PLA+ or PETG without supports.

* **[Download Complete CAD Package (.ZIP)](LINK_TO_YOUR_GITHUB_RELEASE_ZIP)**
* [View 80T Pulley STL Directly on GitHub](../CAD/pulleys/80T_Pulley.stl)
* [View Motor Mount Plate STL](../CAD/motor-mounts/Mount_Plate.stl)

> **Recommended Print Settings:** 0.2mm layer height, 4+ perimeter walls, 30% infill (Gyroid) for mechanical torque strength.

---

## Wiring & Circuit Schematic

[INSERT YOUR WIRING DIAGRAM IMAGE HERE]

### Pinout Mapping
* **RPWM / LPWM:** Arduino Pins 10 & 9
* **Driver Enable (R_EN / L_EN):** Arduino Pin 8 (Software 5V logic supply)
* **Encoder Channels A / B:** Arduino Pins 0 (RX) & 1 (TX) with 4.7k Pull-up Resistors
* **Pedals (Gas / Brake):** Analog Pins A0 & A1

---

## Step-by-Step Setup Guide

### 1. Flash the Firmware
1. Connect your bare Pro Micro to PC.
2. Load the diagnostic code from `/firmware/motor_test.ino` to verify driver logic.
3. Use EMC Configurator to flash the final Force Feedback firmware.

### 2. Forza Horizon 5 Configuration
To bypass FH5 input scanner crashes:
1. Run **vJoy** and **Forza EmuWheel**.
2. Hide the raw Arduino device using **Hush**.
3. Map custom axes inside Forza's *Custom Wheel Profile* menu.

---

## Media & Build Gallery

[Add photos of your physical wiring bench test, 3D printed parts, and full wheel assembly]