# BatteryState

## Purpose

BatteryState represents the current operating condition of the aircraft's battery.

---

# Producer

| Subsystem |
|-----------|
| Battery Monitoring System (BMS) |

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

BatteryState communicates the Battery Monitoring System's current assessment of the battery's operating condition.

---

# Failure Behavior

If BatteryState is unavailable:

- The Flight Controller shall execute the configured Failsafe Policy.
- The Copilot shall continue operating using the remaining available system information.

---

# Future Enhancements

Potential future enhancements include:

- Individual cell voltage information.
- Battery current measurements.
- Battery temperature.
- State of Charge (SoC).
- State of Health (SoH).
- Remaining flight time estimation.

---

# Notes

BatteryState represents the Battery Monitoring System's current assessment of the battery.

The Flight Controller uses BatteryState to evaluate flight-critical power management policies.

The Copilot uses BatteryState for monitoring, diagnostics and reporting.