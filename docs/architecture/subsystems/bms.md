# Battery Monitoring System (BMS)

## Purpose

The Battery Monitoring System (BMS) is responsible for monitoring the operating condition of the aircraft's battery and publishing battery state information.

During Phase 1 (MVP), the BMS is treated as a monitoring subsystem. It observes the battery but does not actively manage or regulate it.

---

# Responsibilities

The BMS shall:

- Measure battery voltage.
- Measure battery current.
- Estimate remaining battery capacity.
- Publish BatteryState.

---

# Interfaces

## Consumes

| Interface | Producer | Type | Description |
|-----------|----------|------|-------------|
| Battery | Battery | Power | Electrical power supplied by the battery for measurement and monitoring. |

---

## Produces

| Interface | Consumer | Type | Description |
|-----------|----------|------|-------------|
| BatteryState | Flight Controller | Data | Current battery operating state used for flight-critical power management. |
| BatteryState | Copilot | Data | Current battery operating state used for monitoring, diagnostics and reporting. |

---

# Internal Components

This subsystem contains no further logical decomposition.

---

# Operational Flow

```text
Observe Battery
        │
        ▼
Estimate Battery State
        │
        ▼
Publish BatteryState
```

---

# Operating Modes

This subsystem has no architecturally significant operating modes.

---

# Safety Responsibilities

This subsystem has no independent safety responsibilities.

Battery-related safety policies are evaluated by the Flight Controller and Copilot using BatteryState.

---

# Dependency Classification

## Flight-Critical

| Subsystem | Reason |
|-----------|--------|
| Battery | Provides the operating characteristics being monitored. |

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
| Battery Failure | BatteryState is no longer produced. |
| Internal Monitoring Failure | BatteryState is no longer produced. |

---

# Constraints

- Shall continuously monitor the battery while powered.
- Shall continuously publish BatteryState while operational.

---

# Future Enhancements

Potential future improvements include:

- Cell voltage monitoring.
- Cell balancing.
- Temperature monitoring.
- Battery fault diagnostics.
- Charge cycle tracking.
- Remaining battery lifetime estimation.
- Charging management.

---

# Notes

This document defines the logical architecture of the Phase 1 Battery Monitoring System (BMS).

The Phase 1 BMS is intended solely for battery monitoring. Active battery management capabilities may be introduced in future project phases.