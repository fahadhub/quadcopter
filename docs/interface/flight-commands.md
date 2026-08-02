# FlightCommands

## Purpose

FlightCommands represent operator requests that control the aircraft's flight.

---

# Producer

| Subsystem |
|-----------|
| Ground Station |

---

# Consumers

| Subsystem |
|-----------|
| Flight Controller |

---

# Interface Type

Command

---

# Definition

FlightCommands communicate the operator's desired aircraft behavior to the Flight Controller.

---

# Failure Behavior

If FlightCommands are unavailable, the Flight Controller shall execute the configured Failsafe Policy.

---

# Future Enhancements

Potential future enhancements include:

- Autonomous mission commands.
- Payload commands.
- Camera control commands.
- Formation flight commands.

---

# Notes

FlightCommands express operator intent. Interpretation and execution are the responsibility of the Flight Controller.