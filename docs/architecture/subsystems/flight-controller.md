# Flight Controller

## Purpose

The Flight Controller is the real-time control subsystem responsible for stabilizing and controlling the aircraft.

It continuously estimates the aircraft state using sensor measurements and computes the actuator commands required to satisfy the received flight commands while maintaining stable flight.

The Flight Controller is the most time-critical subsystem in the drone.

---

# Responsibilities

The Flight Controller shall:

- Acquire sensor measurements.
- Process flight commands.
- Estimate the aircraft state.
- Compute actuator commands.
- Transmit actuator commands.
- Publish FlightState.
- Monitor flight safety.

---

# Interfaces

## Consumes

| Interface | Producer | Type | Description |
|-----------|----------|------|-------------|
| FlightCommands | Communication Interface | Command | Operator flight commands. |
| IMUData | Inertial Measurement Unit (IMU) | Data | Raw inertial measurements. |
| BatteryState | Battery Monitoring System (BMS) | Data | Current battery operating state. |
---

## Produces

| Interface | Consumer | Type | Description |
|-----------|----------|------|-------------|
| ActuatorCommand | ESCs | Command | Commands for all controlled actuators. |
| FlightState | Copilot | Data | Estimated aircraft state. |

---

# Internal Components

| Component | Responsibility |
|-----------|----------------|
| Sensor Manager | Acquire, validate and normalize sensor measurements. |
| State Estimator | Estimate the aircraft state from sensor measurements. |
| Control Manager | Process flight commands and compute actuator commands required to achieve the desired aircraft state. |
| Actuator Manager | Validate, route and transmit actuator commands to physical actuators. |
| Safety Manager | Evaluate safety policies, detect unsafe conditions and determine appropriate safety actions. |
| Mode Manager | Manage operating modes and state transitions. |
| Interface Manager | Manage the Flight Controller's external interfaces by publishing and consuming subsystem interfaces. |

---

# Operational Flow

```text
Acquire Inputs
│
├── Sensor Measurements
└── Flight Commands
        │
        ▼
State Estimator
        │
        ▼
Control Manager
        │
        ▼
Actuator Manager
        │
        ▼
Interface Manager
```

---

# Operating Modes

The Flight Controller supports the following operating modes:

- Initializing
- Ready
- Armed
- Flying
- Landing
- Fault

---

# Safety Responsibilities

The Flight Controller shall:

- Evaluate configured safety policies.
- Detect unsafe operating conditions.
- Validate sensor measurements.
- Constrain actuator commands.
- Transition to safe operating modes when required.

---

# Dependency Classification

## Flight-Critical

The following dependencies are required for the Flight Controller to fulfill its primary responsibility of maintaining stable and controlled flight.

| Subsystem | Reason |
|-----------|--------|
| IMU | Provides the sensor measurements required to estimate the aircraft state. |

---

## Mission-Critical

The following dependencies are required to accomplish the mission but are not required to maintain stable flight.

| Subsystem | Reason |
|-----------|--------|
| Communication Interface | Provides external flight commands. Loss of communication shall be handled according to the configured Failsafe Policy. |

---

## Optional

The following dependencies extend the system's capabilities but are not required for safe flight.

| Subsystem | Reason |
|-----------|--------|
| Copilot | Consumes FlightState for telemetry, logging and higher-level mission functionality. The Flight Controller shall remain fully operational without the Copilot. |

---

# Failure Behavior

| Failure | Expected Behavior |
|----------|-------------------|
| IMU Failure | Transition to the Fault operating mode. |
| Communication Loss | Evaluate and execute the configured Failsafe Policy. |
| Actuator Failure | Evaluate applicable safety policies and determine the appropriate response. |
| Copilot Failure | Continue normal flight. Telemetry and logging may be unavailable. |

---

# Constraints

- Deterministic execution.
- Low-latency processing.
- Safety-critical operation.
- Shall not depend on mission-critical or optional subsystems for stable flight.
- Shall continue operating despite telemetry or logging failures.

---

# Future Enhancements

Potential future improvements include:

- Adaptive control algorithms.
- Autonomous flight modes.
- GPS-assisted navigation.
- Vision-assisted stabilization.
- Sensor redundancy.
- Multi-IMU support.
- Dedicated Flight Controller processor.

---

# Notes

This document defines the logical architecture of the Flight Controller.

Implementation details, algorithms, interface definitions, policies and communication protocols are documented separately.