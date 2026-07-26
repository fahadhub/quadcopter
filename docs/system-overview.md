# System Overview

## 1. Mechanical System

The physical structure and moving components that generate and withstand the forces required for flight.

**Components**
- Frame
- Motors
- Propellers
- Landing Gear
- Battery Mount
- Fasteners
- Vibration Dampers
- 

---

## 2. Electronic System

The electrical hardware responsible for sensing, computation, power distribution, actuation, and communication.

**Components**
- Battery
- Power Distribution Board (PDB)
- Voltage Regulators
- Flight Controller
- ESP32
- Inertial Measurement Unit (IMU)
- Electronic Speed Controllers (ESCs)
- GPS Module *(optional)*
- Magnetometer *(optional)*
- Barometer *(optional)*
- Radio Receiver
- Bluetooth/Wi-Fi Module
- LEDs
- Buzzer
- Wiring & Connectors

---

## 3. Embedded Software

The firmware running on the flight controller that reads sensors, processes data, makes control decisions, and commands the hardware.

**Components**
- Hardware Abstraction Layer (HAL)
- Device Drivers
- Sensor Calibration
- Sensor Fusion
- Attitude Estimation
- Flight Control Algorithms
- PID Controller
- Motor Mixer
- ESC Driver
- Communication Stack
- Telemetry
- Failsafe
- Logging & Diagnostics

---

## 4. Communication System

The hardware and protocols that enable communication between the quadcopter and external systems for command, telemetry, and video transmission.

**Components**
- RC Controller
- Android Controller Application
- Radio Link
- Bluetooth
- Wi-Fi
- Telemetry Link
- Video Transmission System
- Communication Protocols
- Antennas

---

## 5. Flight Dynamics

The physical principles governing how the quadcopter generates lift, maintains stability, and responds to control inputs.

**Topics**
- Lift
- Thrust
- Drag
- Torque
- Newton's Laws of Motion
- Center of Gravity
- Center of Thrust
- Moments of Inertia
- Stability
- Roll
- Pitch
- Yaw
- Motor Mixing Theory

---

## 6. System Integration

An overview of how all subsystems interact to form a complete flight system.

**Topics**
- Power Flow
- Data Flow
- Control Loop
- System Architecture
- Hardware Interfaces
- Software Architecture
- Safety Mechanisms