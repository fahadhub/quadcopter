````markdown
# Drone System Architecture (MVP)

## Overview

This document describes the logical architecture of the MVP quadcopter system. The architecture is designed to clearly separate responsibilities between flight control, telemetry, power management, and communication while remaining independent of the physical hardware implementation.

Although the MVP runs entirely on a single ESP32, the software is organized into independent logical subsystems. This allows future versions to migrate selected subsystems (such as the Copilot) onto dedicated processors without changing the overall architecture.

---

# System Overview

The system consists of the following major subsystems:

- Ground Station
- Communication Interface
- Flight Controller
- Copilot
- Inertial Measurement Unit (IMU)
- Battery Monitoring System (BMS)
- Battery
- Voltage Regulator
- Electronic Speed Controllers (ESCs)
- BLDC Motors

Each subsystem has a clearly defined responsibility.

---

# Ground Station

The Ground Station is the user interface for the drone.

Its responsibilities include:

- Displaying telemetry
- Sending flight commands
- Configuring the drone
- Monitoring system health
- Viewing battery information

The Ground Station never communicates directly with the Flight Controller. All communication occurs through the Communication Interface.

---

# Communication Interface

The Communication Interface manages all wireless communication between the drone and the Ground Station.

Responsibilities include:

- Receiving control commands
- Transmitting telemetry
- Managing the communication protocol
- Detecting communication failures

Although this is implemented as software on the ESP32 during the MVP, it is modeled as a separate subsystem because it has a distinct responsibility.

---

# Flight Controller

The Flight Controller is the real-time control system responsible for stabilizing the aircraft.

Its responsibilities include:

- Reading IMU measurements
- Performing sensor fusion
- Estimating aircraft attitude
- Running PID control loops
- Computing motor outputs
- Driving the Electronic Speed Controllers

The Flight Controller is the primary consumer of IMU data for flight control. The Copilot also consumes IMU data for monitoring, diagnostics and reporting.

Because stabilization is safety-critical, the Flight Controller operates at a high update frequency.

---

# Copilot

The Copilot is responsible for monitoring, diagnosing and reporting the operational health of the aircraft.

During the MVP it executes on the same ESP32 as the Flight Controller but is architecturally treated as an independent subsystem.

Responsibilities include:

- Collecting subsystem telemetry.
- Aggregating system information.
- Monitoring subsystem health.
- Diagnosing abnormal system behavior.
- Publishing SystemHealth.
- Preparing telemetry for transmission.
- Logging flight and system data.

Future versions may also include:

- GPS integration.
- Mission planning.
- Autonomous flight.
- Navigation.
- Data recording and playback.
- Predictive fault detection.
- Health analytics.

The Copilot does **not** perform flight stabilization or generate actuator commands.

It operates independently of the flight-critical control loop.

---

# Inertial Measurement Unit (IMU)

The IMU measures the motion of the aircraft.

It provides:

- Accelerometer measurements
- Gyroscope measurements

These measurements are published to both the Flight Controller and the Copilot.

The Flight Controller uses IMUData for state estimation and flight control.

The Copilot uses the same measurements for monitoring, diagnostics and reporting.

---

# Battery Monitoring System (BMS)

The Battery Monitoring System monitors the health of the battery.

The MVP implementation includes:

- Battery voltage
- Battery current (recommended)
- Estimated battery percentage
- Battery telemetry

The BMS forwards battery information to the Copilot for transmission to the Ground Station.

Future versions may include:

- Cell balancing
- Battery health estimation
- Temperature monitoring
- Charge management
- Fault detection

---

# Battery

The battery supplies electrical power to the entire drone.

It provides power to:

- Voltage Regulator
- Battery Monitoring System
- ESC 1
- ESC 2
- ESC 3
- ESC 4

The battery does not communicate with other subsystems.

---

# Voltage Regulator

The Voltage Regulator converts the battery voltage into a stable operating voltage suitable for the onboard electronics.

It powers:

- ESP32
- IMU

This separates the low-voltage electronics from the high-current motor system.

---

# Electronic Speed Controllers (ESCs)

Each BLDC motor has its own Electronic Speed Controller.

Responsibilities include:

- Receiving control signals from the Flight Controller
- Receiving electrical power from the battery
- Driving the three phases of the BLDC motor

Although many drones use a single **4-in-1 ESC board**, architecturally each ESC is considered an independent controller because each controls exactly one motor.

---

# BLDC Motors

The BLDC motors generate thrust.

Each motor:

- Receives electrical power from its corresponding ESC
- Produces thrust according to the commanded speed

The motors contain no control logic.

---

# Information Flow

The primary control flow is:

```
        IMU
       /   \
      ▼     ▼
Flight     Copilot
Controller
    ↓
ESCs
    ↓
Motors
```

The system information flow is:

```
Battery Monitoring System
        ↓
     Copilot
        ↑
Flight Controller
        ↓
Communication Interface
        ↓
Ground Station
```

---

# Power Flow

Power is distributed independently of the control architecture.

```
Battery
    ├── Voltage Regulator
    │       ├── ESP32
    │       └── IMU
    │
    ├── Battery Monitoring System
    │
    ├── ESC 1
    ├── ESC 2
    ├── ESC 3
    └── ESC 4
```

---

# Design Philosophy

The architecture separates responsibilities rather than hardware.

During the MVP:

- Flight Controller and Copilot execute on the same ESP32.
- Communication Interface is implemented as software.
- The BMS performs basic battery monitoring.

Future versions can migrate the Copilot onto a dedicated processor while preserving the logical architecture.

This separation minimizes redesign and enables the system to evolve from a simple manually controlled quadcopter into a more capable autonomous platform.
````
