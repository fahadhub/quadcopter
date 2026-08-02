# Copilot

## Purpose

The Copilot is responsible for monitoring, diagnosing and reporting the operational health of the aircraft.

During Phase 1 (MVP), the Copilot executes on the same ESP32 as the Flight Controller but is architecturally treated as an independent subsystem.

The Copilot shall remain independent of the flight-critical control loop.

---

# Responsibilities

The Copilot shall:

- Collect subsystem information.
- Aggregate system information.
- Monitor subsystem health.
- Diagnose abnormal system behavior.
- Publish SystemInformation.

---

# Interfaces

## Consumes

| Interface | Producer | Type | Description |
|-----------|----------|------|-------------|
| IMUData | Inertial Measurement Unit (IMU) | Data | Raw accelerometer and gyroscope measurements. |
| FlightState | Flight Controller | Data | Current estimated aircraft state. |
| BatteryState | Battery Monitoring System (BMS) | Data | Current battery operating state. |

---

## Produces

| Interface | Consumer | Type | Description |
|-----------|----------|------|-------------|
| SystemInformation | Communication Interface | Data | Aggregated operational information prepared for transmission to the Ground Station. |

---

# Internal Components

This subsystem contains no further logical decomposition.

---

# Operational Flow

```text
Collect System Information
        │
        ▼
Aggregate Information
        │
        ▼
Diagnose System Health
        │
        ▼
Publish SystemInformation
```

---

# Operating Modes

This subsystem has no architecturally significant operating modes.

---

# Safety Responsibilities

This subsystem has no independent safety responsibilities.

The Copilot observes aircraft operation but shall not participate in flight control or execute flight-critical policies.

---

# Dependency Classification

## Flight-Critical

This subsystem has no flight-critical dependencies.

---

## Mission-Critical

| Subsystem | Reason |
|-----------|--------|
| Inertial Measurement Unit (IMU) | Provides IMUData. |
| Flight Controller | Provides FlightState. |
| Battery Monitoring System (BMS) | Provides BatteryState. |
| Communication Interface | Transmits SystemInformation to the Ground Station. |

---

## Optional

This subsystem has no optional dependencies.

---

# Failure Behavior

| Failure | Expected Behavior |
|----------|-------------------|
| IMUData Unavailable | SystemInformation is produced without IMU information. |
| FlightState Unavailable | SystemInformation is produced without flight state information. |
| BatteryState Unavailable | SystemInformation is produced without battery information. |
| Internal Copilot Failure | SystemInformation is no longer produced. |

---

# Constraints

- Shall not generate actuator commands.
- Shall not participate in flight stabilization.
- Shall not execute flight-critical policies.
- Shall remain independent of the flight-critical control loop.

---

# Future Enhancements

Potential future improvements include:

- GPS integration.
- Mission planning.
- Autonomous flight support.
- Data recording and playback.
- Predictive fault detection.
- Health analytics.
- Fleet management support.

---

# Notes

This document defines the logical architecture of the Phase 1 Copilot.

The Copilot is intentionally modeled as a monitoring and diagnostics subsystem. While it executes on the same processor as the Flight Controller during Phase 1, it is architecturally independent and may be migrated to a dedicated processor in future project phases without changing its responsibilities.