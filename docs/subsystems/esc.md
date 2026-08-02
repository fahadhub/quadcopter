# Electronic Speed Controller (ESC)

## Purpose

The Electronic Speed Controller (ESC) is responsible for converting actuator commands into controlled three-phase electrical drive signals that drive a Brushless DC (BLDC) motor.

During Phase 1 (MVP), the ESC is treated as a simple black-box subsystem.

---

# Responsibilities

The ESC shall:

- Receive actuator commands.
- Generate controlled three-phase electrical drive signals.
- Drive the connected BLDC motor.

---

# Interfaces

## Consumes

| Interface | Producer | Type | Description |
|-----------|----------|------|-------------|
| ActuatorCommand | Flight Controller | Command | Desired command for the connected actuator. |
| BatteryPower | Battery | Power | Electrical power supplied to the ESC. |

---

## Produces

| Interface | Consumer | Type | Description |
|-----------|----------|------|-------------|
| ThreePhaseDrive | BLDC Motor | Power | Three-phase electrical drive supplied to the BLDC Motor subsystem. |

---

# Internal Components

This subsystem contains no further logical decomposition.

---

# Operational Flow

```text
Actuator Command
        │
        ▼
Generate Three-Phase Drive
        │
        ▼
BLDC Motor
```

---

# Operating Modes

This subsystem has no architecturally significant operating modes.

---

# Safety Responsibilities

This subsystem has no independent safety responsibilities.

System-level propulsion safety is managed by the Flight Controller.

---

# Dependency Classification

## Flight-Critical

The following dependencies are required for the ESC to fulfill its primary responsibility.

| Subsystem | Reason |
|-----------|--------|
| Flight Controller | Provides actuator commands required to drive the connected BLDC Motor. |
| Battery | Provides electrical power required to generate three-phase electrical drive. |
| BLDC Motor | Receives the generated three-phase electrical drive. |

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
| Battery Power Loss | The ESC ceases to generate three-phase electrical drive. |
| Internal ESC Failure | The ESC ceases to generate three-phase electrical drive. |

---

# Constraints

- Deterministic operation.
- Low-latency response to actuator commands.
- Shall continuously generate three-phase electrical drive while powered and receiving actuator commands.

---

# Future Enhancements

Potential future improvements include:

- Closed-loop RPM control.
- ESC telemetry.
- Current monitoring.
- Temperature monitoring.
- Fault reporting.
- Bidirectional motor operation.
- Custom ESC firmware.

---

# Notes

This document defines the logical architecture of the Phase 1 Electronic Speed Controller.

The ESC is intentionally modeled as a simple black-box subsystem. Future project phases may replace it with a custom-designed ESC that exposes additional interfaces, responsibilities and telemetry capabilities.