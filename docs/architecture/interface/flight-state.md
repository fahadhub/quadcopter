# FlightState

## Purpose

FlightState represents the Flight Controller's current estimate of the aircraft's state.

---

# Producer

| Subsystem |
|-----------|
| Flight Controller |

---

# Consumers

| Subsystem |
|-----------|
| Copilot |

---

# Interface Type

Data

---

# Definition

FlightState communicates the Flight Controller's current estimate of the aircraft's motion and operating state.

---

# Failure Behavior

If FlightState is unavailable, the Copilot shall continue operating using the remaining available system information.

---

# Future Enhancements

Potential future enhancements include:

- Position estimation.
- Velocity estimation.
- Altitude estimation.
- Navigation state.
- Flight mode information.

---

# Notes

FlightState represents the Flight Controller's best estimate of the aircraft's state.

It is derived from IMUData and other available information through state estimation algorithms.