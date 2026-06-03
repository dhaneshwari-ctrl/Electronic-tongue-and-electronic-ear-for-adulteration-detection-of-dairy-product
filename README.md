# Electronic-tongue-and-electronic-ear-for-adulteration-detection-of-dairy-product
Multi-modal Edge ML dairy adulteration detection system built on an ARM Cortex-M4 (STM32F446ZE). Features a 4-phase sensor fusion pipeline (Optical, Electrical, Mechanical, Chemical) and an on-chip Random Forest classifier for real-time, non-destructive food quality diagnostics.
# Electronic Tongue and Electronic Ear for Adulteration Detection of Dairy Products

An automated, non-destructive edge computing system leveraging the high-performance **ARM Cortex-M4 (STM32F446ZE)** microcontroller to execute real-time food diagnostics. The device integrates optical, electrical, mechanical, and chemical sensors, executing a local Random Forest Machine Learning classifier to output an accurate purity verdict within 30 seconds.

Traditional laboratory testing for food purity is accurate but slow, expensive, and inaccessible to small-scale retailers. The "Purity Box" provides a digital, non-destructive solution that removes chemical handling from food environments and delivers instant, actionable data.

---

## 🌟 Technical Highlights for Recruiters
- **Hardware-Software Co-Design:** Developed a complete multi-modal sensor fusion pipeline on an STM32 platform utilizing bare-metal and Arduino-oriented abstraction layers.
- **Embedded Machine Learning:** Implemented a low-latency, low-footprint Random Forest decision tree model running entirely on-chip to minimize RAM/Flash constraints.
- **Safety-Critical Isolation:** Designed a dual-voltage circuit topology isolating sensitive 3.3V logic components from high-current 12V PTC heating elements using N-Channel Power MOSFETs.
- **Industrial Communication Protocol:** Leveraged a shared I2C bus hierarchy to orchestrate multiple independent target nodes (SSD1306 OLED Display & AS7341 Spectral Sensor) running in parallel.

---

## 📊 The 4-Phase Analytical Framework

The system executes four highly specialized physics-based diagnostic routines sequentially to screen for unauthorized chemical or compound manipulations:


| Phase   | Domain     | Physical Phenomenon       | Target Adulterant           | Embedded Hardware Signature                                |
|         |            |                           |                             |                                                            |
| **I**   | Optical    | Spectral Reflectance Dip  | Starch / Flour Thickeners   | Specific attenuation dip across 600nm–630nm channels       |
| **II**  | Electrical | Electrolytic Ion Mobility | Acid / Detergent / Soap     | Drastic impedance collapse triggering an ADC spike (>1500) |
| **III** | Mechanical | Kinetic Energy Damping    | Palm Oil / Analogue Fats    | Long-resonance vibration decay vs genuine spongy matrix    |
| **IV**  | Chemical   | Thermal Gas Liberation    | Urea / Chemical Fertilizers | Thermal breakdown to NH3 causing a drop in SnO2 resistance |

---

## 🛠️ Hardware Wiring Architecture (STM32F446ZE)
- **PA0:** Transistor Motor Driver Base (100ms High-Torque Mechanical Impulse Output)
- **PA1:** 27mm Piezoelectric Wave Pickup Array (Configured via ADC1_IN1)
- **PA4:** Gold-Plated Direct Injection Conductivity Probe B (Configured via ADC1_IN4)
- **PA5:** MQ-135 Gas Sensor Output Protective Divider Network (Configured via ADC1_IN5)
- **PB0:** High-Current IRFZ44N MOSFET Thermal Switch (Digital GPIO Output)
- **PC13:** Integrated Nucleo Active-Low User Control Button
- **PB8 / PB9:** Dedicated I2C1 Bus Array (Parallel Wiring Schema for Display and Optical Sensor)

---

## 📁 Repository Structure
```text
├── firmware/
│   └── src/
│       └── main.cpp         # Complete object-oriented production firmware
├── documentation/
│   └── architecture.md      # Extended sensor breakdown data sheets
├── .gitignore               # Strict build-bloat isolation mapping
└── README.md                # System documentation manual (This File)
```

---

## ⚙️ Compilation & Deployment Instructions
1. Clone the repository locally: `git clone https://github.com`
2. Open the `firmware/` folder in PlatformIO IDE or your preferred STM32 development tool.
3. Select your build target as **Nucleo-F446ZE**.
4. Install dependencies: `Adafruit_SSD1306` and `Adafruit_AS7341` via your library manager.
5. Connect your hardware components, ensuring a shared system common ground between the external 12V power supply and the STM32 GND pins.
6. Compile the workspace and flash the target binary image to the board.
