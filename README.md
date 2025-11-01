# 🚦 Built a Smart Traffic Management System Using Iot

## 📘 Introduction
This project implements a **Smart Traffic Management System** using an **ESP32 microcontroller** and **infrared (IR) sensors**.  
It dynamically adjusts traffic light timings based on real-time vehicle density, helping reduce congestion, fuel wastage, and waiting time.  
Additionally, a **local web dashboard** hosted by the ESP32 displays real-time lane status and vehicle counts via Wi-Fi.

---

## ⚙️ Features
- Real-time traffic monitoring using IR sensors  
- Dynamic signal control based on vehicle density  
- Web-based dashboard hosted on ESP32 (accessible via IP address)  
- Automatic priority handling for congested lanes  
- Vehicle count reset after each green phase  
- Fully autonomous operation without external server dependency  

---

## 🚗 Modes of Operation
### 1. Normal Mode
Each lane follows the standard sequence: **Green → Yellow → Red**.  
Signals change automatically at fixed time intervals if no congestion is detected.

### 2. Counting Mode
While a lane is **Red**, its IR sensor is active and counts passing vehicles in real-time.

### 3. Preemption Mode
If any **Red** lane’s vehicle count exceeds a threshold (e.g., ≥2), that lane is given **Green priority** after a 2-second all-red safety delay.

### 4. Reset Condition
Whenever a lane turns **Green**, its count resets to zero to prevent false accumulation.

### 5. Web Dashboard Mode
A built-in web server displays:
- Real-time signal status (Red, Yellow, Green)
- Live vehicle counts for each lane  
The dashboard auto-refreshes every second.

---

## 🔩 Components Required

| Component | Quantity |
|------------|-----------|
| ESP32 Microcontroller | 1 |
| IR Sensor | 4 |
| Red, Yellow, Green LEDs | 12 (3 per lane) |
| Resistors (220Ω) | 12 |
| Breadboard | 1 |
| Jumper Wires | As needed |
| USB Cable | 1 |

---

## 💻 Software Requirements
- **Arduino IDE** – for programming ESP32  
- **Web Browser** – for viewing the real-time dashboard  

---

## ⚡ Pin Configuration

| Component | ESP32 Pin |
|------------|------------|
| IR1 | 13 |
| IR2 | 12 |
| IR3 | 14 |
| IR4 | 15 |
| RED1 | 32 |
| YELLOW1 | 21 |
| GREEN1 | 16 |
| RED2 | 33 |
| YELLOW2 | 22 |
| GREEN2 | 17 |
| RED3 | 27 |
| YELLOW3 | 23 |
| GREEN3 | 18 |
| RED4 | 26 |
| YELLOW4 | 25 |
| GREEN4 | 19 |

---

## 🧠 Working Principle
1. **ESP32** reads all four IR sensors to detect vehicles.  
2. Each **Red** lane counts passing vehicles.  
3. When a lane’s vehicle count crosses a set limit, the ESP32 triggers **Preemption Mode**, giving that lane **Green priority**.  
4. After clearing congestion, normal cycling resumes.  
5. Real-time signal states and counts are shown on the web dashboard via Wi-Fi.  

---

## 🌐 Web Dashboard Access
1. Upload the code to ESP32 and power it on.  
2. Connect to the same Wi-Fi network as the ESP32.  
3. Check the Serial Monitor for the ESP32’s **IP address**.  
4. Open the IP address in a browser to view live data.  

The dashboard auto-refreshes every second and shows:
- Current signal status of each lane  
- Vehicle count for each lane  

---

## 🧩 Code Overview
- **Libraries Used:**  
  `WiFi.h`, `WebServer.h`  
- **Core Functions:**
  - `checkIR()` → Counts vehicles when lane is red  
  - `checkPreemption()` → Detects congested lanes  
  - `handlePreemption()` → Activates priority mode  
  - `handleNormalCycle()` → Handles normal signal rotation  
  - `getDashboardHTML()` → Generates live HTML dashboard  

---

## 🚀 Future Enhancements
- Integration with **Blynk** or **ThingSpeak** for cloud analytics  
- Replace IR sensors with **ESP32-CAM** for visual traffic detection  

---


## 👨‍💻 Author
**Vedhathiri K**  


---

## 🏁 Conclusion
This project demonstrates how an IoT-based adaptive traffic control system can improve urban mobility, reduce fuel waste, and offer a scalable foundation for future smart city applications.
