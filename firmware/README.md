# Firmware & Game Setup Guide

This folder contains the hex files and setup steps required to flash the Arduino Pro Micro and configure Force Feedback for PC titles, including specific workarounds for Forza Horizon 5.

---

## 1. Firmware Flashing Procedure

To convert the Arduino Pro Micro into a Force Feedback wheel controller, you must flash the `EMCLite0932.hex` binary using **XLoader**.

### Prerequisites
* **XLoader** utility
* **WheelTest** calibration tool
* Target Firmware: `EMCLite0932.hex` (located in this directory)

### Steps

1. Connect the Arduino Pro Micro to your PC via USB.
2. Launch **XLoader**.
3. Configure the settings:
   * **Hex file:** Select `EMCLite0932.hex`
   * **Device:** `Leonardo(32U4)`
   * **COM Port:** Select your Arduino's active port
   * **Baud rate:** `57600`
4. Click **Upload**.
   > **Note on ATmega32U4 Boards:** If XLoader throws a `Can't open port` error, double-tap the physical `RST` to `GND` pins on the Arduino to force it into bootloader mode, select the newly assigned bootloader COM port, and click **Upload** immediately.
5. Open **WheelTest.exe** to calibrate axis limits, verify encoder feedback, and test spring/damper Force Feedback effects.

---

## 2. Forza Horizon 5 Integration

Forza Horizon 5's input scanner aggressively rejects unrecognized DIY hardware IDs, resulting in immediate desktop crashes upon launch. To play FH5 without crashes, you must route signals through a virtual controller interface.

### Required Software Stack
* **vJoy:** Creates a virtual game controller device.
* **Forza EmuWheel:** Maps raw physical Arduino inputs to the vJoy virtual device.
* **Hush:** Mutes the physical Arduino ID so Forza only detects vJoy.

### Setup Workflow

#### Step A: Virtual Mapping (EmuWheel & vJoy)
1. Install and launch **vJoy**.
2. Open **Forza EmuWheel Configurator**.
3. Bind your physical steering axis, pedal axes, and buttons to the corresponding vJoy parameters.
4. Save the configuration.

#### Step B: Device Hiding (Hush)
1. Launch **Hush**.
2. Locate the physical Arduino Pro Micro / EMC Lite device in the list and click **Mute**.
   > **Important:** Do not mute the vJoy virtual device or standard game controllers.

#### Step C: Game Binding
1. Launch **Forza EmuWheel** and click **Start**.
2. Open **Forza Horizon 5**.
3. Navigate to **Settings > Controls > Wheel**.
4. Scroll right to select a **Custom Wheel Profile** (do not use default locked profiles).
5. Bind your steering, pedals, and mandatory menu actions.