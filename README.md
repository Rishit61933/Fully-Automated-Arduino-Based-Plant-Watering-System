# 🌱 Automated Arduino-Based Plant Watering System

> A fully automated smart irrigation system using Arduino Uno — monitors soil moisture, temperature, and humidity to water plants only when needed.

**Course:** ES116 — Principles and Applications of Electrical Engineering  
**Institute:** Indian Institute of Technology Gandhinagar  
**Author:** Rishi Soni (24110297)

---

## 📸 Demo

![Plant Watering System](./assets/system_photo.jpg)

---

## 🧠 How It Works

1. The **soil moisture sensor** continuously reads the water content in the soil
2. The **LM35** measures ambient temperature; the **DHT11** measures humidity
3. All readings are displayed live on a **16x2 LCD**
4. If soil moisture drops **below the threshold** and environmental conditions are suitable:
   - The **buzzer** sounds an alert
   - The **relay** activates the **water pump**
5. After watering for a set duration, the pump turns off and the loop repeats

### System Flowchart

```
Start → Read Moisture → Read Temp (LM35) → Read Humidity (DHT11)
      → Display on LCD → Is Moisture < Threshold?
            ├── YES → Sound Buzzer → Activate Pump → Wait → Deactivate Pump → Loop
            └── NO  → Sound Buzzer → Loop
```

---

## 🔧 Components Used

| Component | Purpose |
|---|---|
| Arduino Uno | Main microcontroller |
| Soil Moisture Sensor (Capacitive) | Reads volumetric water content |
| DHT11 Sensor | Measures ambient humidity & temperature |
| LM35 Sensor | Precision analog temperature measurement |
| 16x2 LCD Display | Displays real-time sensor readings |
| Relay Module | Controls the water pump safely |
| 5V Water Pump | Delivers water to the plant |
| Buzzer | Audible alert before watering |
| Breadboard + Jumper Wires | Circuit connections |
| Potentiometer | LCD contrast adjustment |
| Breadboard Power Supply | Powers external components |

---

## 🔌 Pin Connections

| Component | Arduino Pin |
|---|---|
| Soil Moisture Sensor (Analog Out) | A0 |
| LM35 (Analog Out) | A2 |
| DHT11 (Data) | D7 |
| Relay (IN) | D6 |
| Buzzer | D8 |
| LCD (Data/Control Pins) | D2, D3, D4, D5, D11, D12 |

> All VCC pins → 5V | All GND pins → Common GND

---

## 💻 Code

See [`plant_watering.ino`](./plant_watering.ino) for the full Arduino sketch.

**Key logic:**
```cpp
if (soilMoisture < MOISTURE_THRESHOLD) {
  digitalWrite(BUZZER_PIN, HIGH);  // Alert
  delay(2000);
  digitalWrite(RELAY_PIN, HIGH);   // Activate pump
  delay(WATERING_DURATION);
  digitalWrite(RELAY_PIN, LOW);    // Deactivate pump
}
```

---

## 📊 Results

- Real-time moisture, temperature, and humidity readings on LCD ✅
- Relay-controlled pump activates **only when needed** — conserving water ✅
- Moving average filter on LM35 for **stable temperature readings** ✅
- Capacitive sensor ensures **corrosion-resistant** long-term performance ✅
- Successfully tested on multiple soil types ✅

---

## 📁 Repository Structure

```
plant-watering-system/
├── README.md
├── plant_watering.ino       # Arduino source code
├── report/
│   └── ES116_PROJECT_REPORT_RISHI_24110297.pdf
└── assets/
    └── system_photo.jpg
```

---

## 📄 Report

The full project report is available in the [`report/`](./report/) folder.

---

## 🔮 Future Improvements

- Add Wi-Fi (ESP8266/ESP32) for remote monitoring via a mobile app
- Solar-powered for outdoor/off-grid use
- Multiple plant zones with individual thresholds
- Data logging to SD card or cloud (ThingSpeak, Blynk)

---

## 🙏 Acknowledgements

Thanks to the lab assistants at IIT Gandhinagar for their support and guidance throughout the project.

---

## 📚 References

1. [Arduino Uno — Arduino.cc](https://www.arduino.cc/en/Main/ArduinoBoardUno)
2. [Automatic Plant Watering System Using Arduino — Instructables](https://www.instructables.com/Automatic-Plant-Watering-System/)

---

*Note: Schematic and circuit diagrams in the project report are AI-generated for illustration purposes.*
