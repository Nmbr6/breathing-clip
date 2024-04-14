================
First-time Setup
================

|Arduino Libraries|
Install:
- M5StickCPlus2 (1.0.1)

Update:
-M5Family (0.1.3)
-M5Stack (0.4.6)
-M5Unified (0.1.14)

Accept all dependencies when installing or updating

|Arduino Board Manager|
Update:
- M5Stack (v2.0.7)

|Drivers|
The UART chip has changed going from M5StickCPlus to M5StickCPlus2.
So a new driver needs to be installed for a host computer to receive Serial data from the unit.
Install CH9102 driver here: https://docs.m5stack.com/en/core/M5StickC%20PLUS2 ('Driver Installation')
Choose appropriate installer for Windows or MacOS

|Header Files|
In your Arduino libraries folder, navigate to ...\Arduino\libraries\M5Unified\src\utility\imu
Open MPU6886_Class.cpp, then edit Line 61 to match this: setAccelFsr(Ascale::AFS_2G);
This adjusts the full-scale range of IMU data to its highest resolution (+/- 2G)


==============
Before Sketch Upload
==============
Edit Patient ID: set unique alphanumeric ID per unit (Line 24)
Edit WiFi credentials (Lines 27-28)


