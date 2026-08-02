# ActuatorCommand

## Purpose

ActuatorCommand represents the desired actuator outputs computed by the Flight Controller.

---

# Producer

| Subsystem |
|-----------|
| Flight Controller |

---

# Consumers

| Subsystem |
|-----------|
| Electronic Speed Controller (ESC) |

---

# Interface Type

Command

---

# Definition

ActuatorCommand communicates the Flight Controller's desired actuator outputs to the Electronic Speed Controller (ESC).

---

# Failure Behavior

If ActuatorCommand is unavailable, the Electronic Speed Controller (ESC) shall cease updating actuator outputs.

---

# Future Enhancements

Potential future enhancements include:

- Camera gimbal commands.
- Payload deployment commands.
- Landing gear commands.
- Auxiliary actuator commands.

---

# Notes

ActuatorCommand expresses the Flight Controller's desired actuator behavior.

The interpretation and execution of ActuatorCommand are the responsibility of the Electronic Speed Controller (ESC).