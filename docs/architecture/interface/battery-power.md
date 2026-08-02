# BatteryPower

## Purpose

BatteryPower represents the electrical power supplied by the Battery subsystem.

---

# Producer

| Subsystem |
|-----------|
| Battery |

---

# Consumers

| Subsystem |
|-----------|
| Electronic Speed Controller (ESC) |
| Voltage Regulator |
| Battery Monitoring System (BMS) |

---

# Interface Type

Power

---

# Definition

BatteryPower transfers electrical energy from the Battery subsystem to the aircraft's power consumers.

---

# Failure Behavior

If BatteryPower is unavailable, connected subsystems shall cease operation.

---

# Future Enhancements

Potential future enhancements include:

- Redundant battery support.
- Hot-swappable battery support.
- Power distribution redundancy.

---

# Notes

BatteryPower represents the primary electrical power interface within the aircraft.

The Battery subsystem is responsible for supplying BatteryPower.

The characteristics of BatteryPower are determined by the Battery subsystem and consumed by downstream power distribution components.