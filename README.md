# Smart Parking Management System (ESP32)

An ESP32-based Smart Parking Management System that automates vehicle entry/exit using RFID authentication, maintains real-time parking occupancy using IR sensors, and improves safety with smoke/flame detection. When the ground-floor parking reaches full capacity, the system triggers a lift mechanism to transfer vehicles to an upper floor, reducing congestion and improving space utilization.

---

## Features

- **RFID-Based Access Control (RC522)**
  - Allows only authorized RFID tags/cards to open the gate
  - Keeps the gate locked for unauthorized tags

- **Automatic Gate Control (Servo Motor)**
  - Servo motor opens/closes the parking gate automatically after authentication

- **Real-Time Vehicle Counting (IR Sensors)**
  - **Entry IR Sensor** increments vehicle count
  - **Exit IR Sensor** decrements vehicle count
  - Calculates **Occupied Slots** and **Vacant Slots**

- **LED Dashboard Display**
  - Displays:
    - Total slots
    - Current number of parked vehicles (occupied)
    - Available slots (vacant)
  - Can indicate full-capacity status when vacant slots become zero

- **Lift Control for Full-Capacity Situation**
  - When the ground floor is full, a **Lift-Front IR Sensor** detects a vehicle near the lift area
  - ESP32 activates the motor driver to operate the lift motor and transfer the vehicle to the upper floor

- **Safety and Emergency Response**
  - **MQ-2 Smoke Sensor** + **Flame Sensor** detect hazards
  - Triggers **Buzzer/Siren**
  - Automatically **unlocks access points** for fast evacuation
  - Includes an **emergency arrangement for the upper floor (2nd Floor)**

---

## Hardware Components

- ESP32 Microcontroller
- RC522 RFID Reader + RFID Card/Tag
- IR Sensor Modules (Entry, Exit, Lift-Front)
- Servo Motor (Gate Control)
- L298N Motor Driver
- DC Motor (Lift Motor)
- MQ-2 Smoke Sensor
- Flame Sensor Module
- Buzzer / Siren
- LED Display (Dashboard)
- Power Supply Unit
- Jumper Wires / Breadboard / Connectors (as needed)

---

## Software & Tools

- **Arduino IDE**
- **C/C++ (Arduino framework)**
- Common libraries (depending on your setup):
  - `MFRC522` for RFID (RC522)
  - Display library for your LED/LCD module (if applicable)

---

## How the System Works (Workflow)

### Normal Operation
1. Vehicle arrives at the gate.
2. User taps RFID card/tag on RC522.
3. If authorized, ESP32 opens the gate using the servo motor.
4. Entry IR sensor detects the vehicle → **count increases**.
5. LED display updates **occupied/vacant** slots.

### Exit Operation
1. Vehicle leaves the parking area.
2. Exit IR sensor detects the vehicle → **count decreases**.
3. LED display updates **occupied/vacant** slots.

### Ground Floor Full + Lift Operation
1. When occupied slots reach total capacity → **vacant = 0** (ground floor full).
2. Vehicle approaches lift area.
3. Lift-front IR sensor detects the vehicle.
4. ESP32 activates L298N to run the lift motor.
5. Vehicle is transferred to the upper floor.

### Emergency (Fire/Smoke)
1. MQ-2 or Flame Sensor detects hazard.
2. ESP32 activates buzzer/siren immediately.
3. System switches to emergency mode and **unlocks gates/access points**.
4. Upper-floor emergency arrangement supports evacuation from 2nd floor.

---

## Project Demo

- **YouTube Demo Video:** https://youtu.be/Hy5_5QjNg3o

---

## Repository

- **GitHub Repository:** https://github.com/Nirab410/Micro-processor-Micro-Controller-Lab-Project

---

## Course Information

**Fall 25 CSE 426/CSE 4326 (D)**  
Microprocessor, Microcontroller and Interfacing Laboratory / Microprocessors and Microcontrollers Laboratory

---

## Future Improvements

- Add per-slot sensing (ultrasonic/load sensors) to improve occupancy accuracy
- Add Wi-Fi/app-based monitoring and logging
- Improve lift reliability using limit switches and load sensing
- Add power-fail safe mode (battery backup) for emergency operation

---

## License

This project is developed for academic purposes as part of the course laboratory project.
