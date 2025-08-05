# Klipper Config for Sunlu S9 Plus with SKR Mini E3 v3

![Sunlu S9 Plus](https://placehold.co/800x300/1e293b/ffffff?text=Sunlu%20S9%2B%20with%20Klipper)

Welcome! This repository contains a refined and optimized Klipper configuration for the **Sunlu S9 Plus** 3D printer, specifically upgraded with a **BigTreeTech SKR Mini E3 v3** mainboard.

The goal of this project is to create a robust, high-performance, and community-driven configuration that helps users get the most out of this large-format printer.

---

## ⭐ Key Features

This configuration has been carefully tuned and includes several enhancements over a basic setup:

* **🚀 Performance Tuned:** Settings are geared towards high-quality, high-speed printing with a starting acceleration of 5000 mm/s².
* **〰️ Input Shaper Ready:** The config includes the necessary `[adxl345]` section. Just run the resonance tests to unlock faster, ghost-free printing.
* **🌐 Optimized Bed Mesh:** A "Balanced" 7x7 bicubic bed mesh is configured to provide excellent first-layer accuracy across the large 310x310mm bed without taking excessive time.
* **🤖 Smart Macros:** Includes robust `START_PRINT` and `END_PRINT` macros that streamline the printing process. The start macro heats the bed first, probes for the mesh, and then heats the nozzle to prevent oozing.
* **🛡️ Safe & Reliable:** Implements virtual Z-endstop using the probe for higher accuracy and reliability. Stepper motor currents have been adjusted for cooler, quieter operation without sacrificing torque.
* **🧹 Clean & Commented:** The configuration is heavily commented and organized into logical sections, making it easy to read, understand, and modify.

---

## ⚙️ How to Use

**❗️ IMPORTANT:** This is not a drop-in file. You **must** perform your own calibrations. Every printer is slightly different.

1.  **Download the Files:** Download the `printer.cfg` and `Macro.cfg` from this repository.
2.  **Verify Your MCU ID:** This is the most common point of failure. SSH into your Raspberry Pi and run `ls /dev/serial/by-id/*`. Copy the result and replace the `serial:` value in the `[mcu]` section of `printer.cfg`.
3.  **Initial Startup & Checks:** After uploading the config, restart Klipper. Ensure there are no errors and that all heaters and fans respond correctly.
4.  **Critical Calibrations:** You **must** run the following calibrations for your specific machine:
    * **PID Tuning:** Run `PID_CALIBRATE HEATER=extruder TARGET=210` and `PID_CALIBRATE HEATER=heater_bed TARGET=60`.
    * **Probe Z-Offset:** This is crucial for your first layer. Run `PROBE_CALIBRATE` and follow the steps carefully.
    * **Input Shaper:** Follow the official Klipper documentation to run the resonance tests using the ADXL345. Update the `[input_shaper]` section with your results.
    * **Pressure Advance:** Once Input Shaper is tuned, calibrate Pressure Advance for your specific filament.
    * **Extruder E-Steps:** Calibrate the `rotation_distance` in the `[extruder]` section.

---

## 🤝 How to Contribute

This project thrives on community contributions! If you have an improvement, a bug fix, or a better macro, please share it.

We welcome contributions of all kinds:
* Fine-tuning speed and acceleration settings.
* Improving the purge line or other macros.
* Adding support for different mods or hardware.
* Enhancing the comments and documentation.

### Contribution Steps:

1.  **Fork the Repository:** Click the "Fork" button at the top right of this page.
2.  **Create a Branch:** Create a new branch in your fork for your changes.
    ```bash
    git checkout -b feature/my-awesome-improvement
    ```
3.  **Make Your Changes:** Edit the files and commit your changes with a clear, descriptive message.
    ```bash
    git commit -m "feat: Improve purge line for faster start"
    ```
4.  **Push to Your Fork:**
    ```bash
    git push origin feature/my-awesome-improvement
    ```
5.  **Open a Pull Request:** Go to the main repository and open a new Pull Request. Provide a clear description of your changes and why you think they should be included.

Let's work together to make this the best Klipper config for the Sunlu S9 Plus!

---

## ⚠️ Disclaimer

Use this configuration at your own risk. Incorrectly configured firmware can cause damage to your printer. Please ensure you understand the settings you are changing.
