# SystemInformation

## Purpose

SystemInformation represents the Copilot's aggregated view of the aircraft's operational state.

---

# Producer

| Subsystem |
|-----------|
| Copilot |

---

# Consumers

| Subsystem |
|-----------|
| Communication Interface |

---

# Interface Type

Data

---

# Definition

SystemInformation communicates aggregated operational information prepared by the Copilot for transmission to the Ground Station.

---

# Failure Behavior

If SystemInformation is unavailable, the Communication Interface shall cease transmitting updated aircraft information.

---

# Future Enhancements

Potential future enhancements include:

- Mission information.
- Navigation information.
- GPS information.
- Payload information.
- Camera information.
- Health analytics.
- Flight history.

---

# Notes

SystemInformation aggregates information from multiple aircraft subsystems.

The Copilot is responsible for producing SystemInformation.

The Communication Interface is responsible for transmitting SystemInformation to the Ground Station.