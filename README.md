# Power Model for Battery Estimation

## 1. Overview
This repository contains the power consumption analysis and battery estimation for a project using the **Seeed Studio XIAO ESP32C3** microcontroller along with various peripherals. The calculations determine the appropriate battery size based on real-world usage profiles.

## 2. Components & Datasheets
The following table lists the components used in the project along with their respective datasheets:

| Component | Datasheet Link |
|-----------|---------------|
| **Seeed Studio XIAO ESP32C3** | [Datasheet](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/) |
| **TTP223 Capacitive Touch Sensor** | [Datasheet](https://www.electroschematics.com/wp-content/uploads/2013/01/ttp223-datasheet.pdf) |
| **WS2812 LED** | [Datasheet](https://cdn-shop.adafruit.com/datasheets/WS2812B.pdf) |
| **SSD1351 OLED Display** | [Datasheet](https://cdn-shop.adafruit.com/datasheets/SSD1351-Revision+1.3.pdf) |
| **Stepper Motor (28BYJ-48)** | [Datasheet](https://www.mouser.com/datasheet/2/758/stepd-01-data-sheet-1143075.pdf) |

## 3. Power Model & Battery Estimation
### **Power Model Spreadsheet**
The power model spreadsheet contains:
- **Power consumption** of each component in different usage states (Off, Sensing, Interactive).
- **Duty cycle analysis** to determine the time spent in each state.
- **Battery capacity estimation** based on total daily energy consumption.

### **Screenshots**
The following screenshots show the completed power analysis:
<img width="1435" alt="image" src="https://github.com/user-attachments/assets/566934e1-15c5-46e0-8201-f474206f43c6" />
<img width="1299" alt="image" src="https://github.com/user-attachments/assets/c963a1fb-115c-4b41-bcf6-6e23a6d4d180" />



## 4. Reflections
### **How to determine the "days of use" metric?**
The days of use were determined based on:
1. **Total daily power consumption** (mWh), calculated from individual component power usage and duty cycle.
2. **Battery capacity** (mAh) converted to available energy (mWh) considering regulator efficiency.
3. **Estimated runtime** = (Battery energy) ÷ (Daily energy consumption).

### **What is the optimum size for the battery in my device?**
The optimal battery size was chosen as **1000mAh (3.7V)**, as it provides sufficient energy for **approximately 3 days of operation**. If extended runtime is required, a **1200mAh or 1500mAh** battery could be used.

### **What hardware/software/cost/effort trade-offs could improve the user experience?**
Several trade-offs can optimize the system:
- **Hardware Optimization:**
  - Reduce LED brightness or duty cycle to save energy.
  - Use a more efficient DC-DC converter instead of an LDO to improve efficiency.
- **Software Optimization:**
  - Implement deep sleep modes for ESP32 when idle.
  - Optimize WiFi transmission frequency to minimize TX power usage.
- **Cost & Effort Considerations:**
  - A larger battery improves runtime but increases cost and weight.
  - Simplifying the circuit reduces power losses but might limit functionality.
