# Inertial Measurement Unit (IMU)

## Purpose

The Inertial Measurement Unit (IMU) is responsible for measuring the aircraft's inertial motion and orientation.

During Phase 1 (MVP), the IMU is treated as a sensor subsystem that provides raw inertial measurements to the Flight Controller and Copilot.

---

# Responsibilities

The IMU shall:

- Measure linear acceleration.
- Measure angular velocity.
- Publish inertial measurement data.

---

# Interfaces

## Consumes

| Interface | Producer | Type | Description |
|-----------|----------|------|-------------|

This subsystem consumes no interfaces.

---

## Produces

| Interface | Consumer | Type | Description |
|-----------|----------|------|-------------|
| IMUData | Flight Controller | Data | Raw accelerometer and gyroscope measurements used for flight control. |
| IMUData | Copilot | Data | Raw accelerometer and gyroscope measurements used for monitoring and diagnostics. |

---

# Internal Components

This subsystem contains no further logical decomposition.

---

# Operational Flow

```text
Measure Motion
        │
        ├────────► Flight Controller
        │
        └────────► Copilot
```

---

# Operating Modes

This subsystem has no architecturally significant operating modes.

---

# Safety Responsibilities

This subsystem has no independent safety responsibilities.

The Flight Controller is responsible for validating IMU measurements and determining their suitability for flight.

---

# Dependency Classification

## Flight-Critical

This subsystem has no flight-critical dependencies.

---

## Mission-Critical

This subsystem has no mission-critical dependencies.

---

## Optional

This subsystem has no optional dependencies.

---

# Failure Behavior

| Failure | Expected Behavior |
|----------|-------------------|
| IMU Failure | IMUData is no longer produced. |

---

# Constraints

- Shall continuously measure aircraft motion while powered.
- Shall continuously publish IMUData while operational.

---

# Future Enhancements

Potential future improvements include:

- Magnetometer integration.
- Barometer integration.
- Multiple IMUs.
- Built-in self-test.
- Temperature compensation.

---

# Notes

This document defines the logical architecture of the Phase 1 Inertial Measurement Unit (IMU).

The IMU is intentionally modeled as a simple sensing subsystem.

The Flight Controller uses IMUData for state estimation and flight control.

The Copilot uses IMUData for monitoring, diagnostics and reporting.