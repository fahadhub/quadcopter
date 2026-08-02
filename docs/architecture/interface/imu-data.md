# IMUData

## Purpose

IMUData represents the inertial measurements produced by the Inertial Measurement Unit (IMU).

---

# Producer

| Subsystem |
|-----------|
| Inertial Measurement Unit (IMU) |

---

# Consumers

| Subsystem |
|-----------|
| Flight Controller |
| Copilot |

---

# Interface Type

Data

---

# Definition

IMUData communicates the aircraft's measured linear acceleration and angular velocity.

---

# Failure Behavior

If IMUData is unavailable:

- The Flight Controller shall execute the configured Failsafe Policy.
- The Copilot shall continue operating using the remaining available system information.

---

# Future Enhancements

Potential future enhancements include:

- Magnetometer measurements.
- Barometric measurements.
- Sensor quality indicators.
- Measurement confidence.

---

# Notes

IMUData represents raw sensor measurements.

The Flight Controller uses IMUData for state estimation and flight control.

The Copilot uses IMUData for monitoring, diagnostics and reporting.