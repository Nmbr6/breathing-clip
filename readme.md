# Real-time Wearable Respiratory Monitoring System

This project develops a proof-of-concept real-time respiratory monitoring system designed to be non-intrusive, capable of capturing recognizable breathing signals, and transmitting the data over UDP. It is aimed at enabling respiratory based interactions, ensuring simple mounting and adaptability to different positions.

## Referencing

If you use the code or 3D print files included here for your research, please kindly cite the relevant papers in your publications. This support is critical for the continued development and maintenance of the software, as well as recognition of the effort by the authors. Relevant publications include:
* Employing Physiological Sensing for Exteroceptive-Interoceptive Sensory Substitution in NeuroHCI \[[link](https://dl.acm.org/doi/full/10.1145/3544549.3585897)] 
* Breathing based immersive interactions for enhanced agency and body awareness: a claustrophobia motivated study \[[link](https://dl.acm.org/doi/full/10.1145/3544549.3585897)] 
## Platform

- **Device**: [M5 StickC Plus2](https://docs.m5stack.com/en/core/M5StickC%20PLUS2), built on the ESP32-PICO-V3-02 SoC.
- **IMU**: MPU6886 6-axis IMU for motion tracking.
- **Power**: Equipped with a 200mAh battery.
- **WiFi**: Onboard 2.4GHz antenna utilizing the ESP32 WiFi stack for data transmission.


## Wi-Fi Transmitter Details

- **Wi-Fi Protocol**: 2.4GHz (802.11b/g/n).
- **UDP Port**: 1234 for data streaming.
- **Output Data Rate**: ~500Hz, corresponding to every 2ms.
- **IP Address**: Assigned dynamically.
- **Device Identifier**: Incorporates a "patient_id" as an unsigned 4-digit integer.
- **Packet Type**: 20-byte string format "patient_id,elapsedTime,ac_sig", where:
  - `patient_id` is an unsigned 4-digit integer.
  - `elapsedTime` is an unsigned 32-bit integer, indicating time in milliseconds since power-on, with a maximum stored value representing 49.7 days.
  - `ac_sig` is a signed 16-bit integer showing the accelerometer signal in G-force (units of 0.1mG).

## User Input/Output

- **Front Button**: Toggles the device's LED on or off.
- **Side Button**: Pauses or resumes the UDP stream, effectively toggling the stream state.
- **PWR Button**: Powers the device on (long press ~2 seconds) or off (long press ~6 seconds).

## First-time Setup

**Arduino Libraries**
- M5StickCPlus2 (1.0.1)
- M5Family (0.1.3)
- M5Stack (0.4.6)
- M5Unified (0.1.14)

Accept all dependencies when installing or updating.

**Arduino Board Manager**
- M5Stack (v2.0.7)

**Drivers**
- Install CH9102 UART driver [here](https://docs.m5stack.com/en/core/M5StickC%20PLUS2) ('Driver Installation').
Choose appropriate installer for Windows or MacOS.

**Header Files**
- In your Arduino libraries folder, navigate to <...\Arduino\libraries\M5Unified\src\utility\imu>
Open MPU6886_Class.cpp, then edit Line 61 to match this: setAccelFsr(Ascale::AFS_2G);
This adjusts the full-scale range of IMU data to its highest resolution (+/- 2G)
- To run the code effectively, modify the IMU header file within the M5StickC library to set the resolution to its maximum by editing the `MPU6886.h` file: change line 66 to `Ascale Acscale = AFS_2G;`.

## Before Sketch Upload

Edit Patient ID: set unique alphanumeric ID per unit (Line 24)
Edit WiFi credentials (Lines 27-28)

## Mounting

We suggest to methods for mounting - magnetic tape, or a 3D printed clip which can be found in the Git.
### Magnetic tape
 We used Magnetic tape with adhesive backing, with one segment attached to the device, and one simply placed inside the garment. 
 
### 3D printed clip
The STL for printing the clip can be found [here](https://github.com/Nmbr6/breathing-clip/blob/main/Sensor%20Clip.STL) in the GIT. We suggest printing it vertically, oriented so that the clip opening is facing up.

<p align="center">
   <img src="https://raw.githubusercontent.com/Nmbr6/breathing-clip/main/Figures/sensor%202.jpg?token=GHSAT0AAAAAACODQH7HHRZ7BNCIGNU4TO7WZRHVDFQ" width="400"/> 
</p>

## Placement

For optimal signal capture, the device should be placed over clothing on the clavicle, approximately midway between the sternoclavicular and acromioclavicular joints. The M5 StickC Plus2 should be perpendicular to the clavicle, ensuring accurate signal detection.

<p align="center">
  <img src="https://raw.githubusercontent.com/Nmbr6/breathing-clip/main/Figures/sensor%201.jpg?token=GHSAT0AAAAAACODQH7HNZP7RFBZG6IX2DH2ZRHVCOA" width="400"/>
</p>
