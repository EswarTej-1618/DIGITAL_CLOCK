

# 🕒 Multi-Mode Digital Logic Clock

A fully functional, **multi-mode digital clock** built entirely from scratch using **TTL (Transistor-Transistor Logic) ICs** — no microcontrollers, no pre-programmed modules. Every second counted, every LED lit, every mode implemented **purely with logic gates, counters, and passion**.

This project was created as a hands-on challenge in **digital electronics**, focusing on fundamental concepts like synchronous counters, BCD-to-7-segment decoding, and logic gate troubleshooting.

![Digital Clock](https://via.placeholder.com/600x400.png?text=Our+Digital+Clock+Project)
*Replace the placeholder with an actual image of your project*

---

## 🚀 Features

* **Standard Timekeeping:** Displays time in `HH:MM:SS` format.
* **Dual Time Modes:** Switchable between 12-hour (with AM/PM logic) and 24-hour modes.
* **Stopwatch Mode:** 10-hour stopwatch `HH:MM:SS`.
* **Day-of-the-Week Display:** A dedicated 7-segment display shows the day numerically: `0 = Sunday, 1 = Monday, … 6 = Saturday`.
* **Modular Design:** Clock divided into separate modules — seconds, minutes, hours, and day.

---

## 🛠️ Hardware Components

| Component                | Part Number  | Quantity  | Description                                    |
| ------------------------ | ------------ | --------- | ---------------------------------------------- |
| Decade Counter           | 7490         | 7         | Main counter for seconds, minutes, hours, days |
| BCD to 7-Segment Decoder | 7447         | 7         | Converts BCD to 7-segment display signals      |
| Quad 2-Input AND Gate    | 74LS08       | 1–2       | Reset logic & state detection                  |
| Triple 3-Input AND Gate  | 74LS11       | 1–2       | Complex state detection (e.g., 12-hour reset)  |
| Quad 2-Input OR Gate     | 74LS32       | 1–2       | Combines multiple reset conditions             |
| 7-Segment Display        | Common Anode | 7         | For digits and day display                     |
| Breadboards              | –            | 15        | Prototyping area                               |
| Power Supply             | –            | 1         | Stable 5V DC supply                            |
| Clock Pulse Source       | –            | 1         | 1 Hz signal (from 555 timer or FG)             |
| Wires                    | –            | Countless | Connections between components                 |
| Resistors                | ~330 Ω       | ~56       | Current limiting for 7-segment displays        |

---

## ⚙️ Circuit Design & Logic

The clock is a **cascade of synchronous counters** with a stable 1 Hz clock as the primary heartbeat. Each counter triggers the next: seconds → minutes → hours → days.

### 1️⃣ Seconds & Minutes Counters (00–59)

* **Units Digit:** `7490` configured as a BCD counter (0–9).
* **Tens Digit:** Second `7490` triggered on units overflow, counting 0–5.
* **Reset Logic:** When tens = 6 (`0110`), a `74LS08` AND gate triggers a reset to 00.

### 2️⃣ Hours Counter (12/24-Hour Modes)

* **24-Hour Mode (00–23):**

  * Cascaded `7490`s count hours; `AND` gates detect 24 to reset to 00.
* **12-Hour Mode (01–12):**

  * Logic detects 13 and resets hours to 01 instead of 00.

### 3️⃣ Day-of-the-Week Counter (0–6)

* Single `7490` IC triggered by hours overflow (midnight).
* Resets after reaching 7 (Sunday = 0, Saturday = 6).

### 4️⃣ Display Module

* Each `7490` output → corresponding `7447` decoder → 7-segment display.
* Current-limiting resistors protect LEDs.

---

## 🛠️ Troubleshooting: Our Biggest Challenge

Building 15 interconnected breadboards taught us **systematic debugging**:

**Common Issues:**

1. Wiring errors — misplaced or wrong connections.
2. Loose connections — intermittent faults.
3. Logic errors — wrong AND/OR combinations for reset conditions.
4. Floating TTL inputs — tied unused pins to VCC or GND.
5. Power distribution issues — voltage drops across breadboards.

**Our Debugging Strategy:**

* Modular testing of each block independently.
* Isolate & verify faulty modules.
* Signal tracing with logic probe/multimeter.
* Manual state forcing to validate reset logic.
* Team reviews to catch overlooked errors.

**Lesson Learned:**

> We failed multiple times, but every failure taught us patience, precision, and creative problem-solving. By the 4th complete attempt, the clock came alive perfectly.

---

## 👥 Team

This project is a **collaborative effort**:

* [Eswar Pavan Teja]
* [Sathish kumar]
* [Vinod Kumar]

---

## 🎯 Key Takeaways

* Hands-on mastery of **TTL logic and counters**.
* Importance of **modular design & systematic debugging**.
* Value of **teamwork, persistence, and iterative problem-solving**.

---



