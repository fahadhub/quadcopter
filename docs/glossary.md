# Glossary

This document defines the architectural terminology used throughout the project.

The definitions in this document are considered authoritative and should be referenced by all architecture and design documentation.

---

# Responsibility

A capability or obligation owned by a subsystem.

Responsibilities define why a subsystem exists.

---

# Subsystem

A logical component that owns one or more related responsibilities.

A subsystem encapsulates the internal components required to fulfill its responsibilities and exposes well-defined interfaces to other subsystems.

Examples:

- Flight Controller
- Copilot
- Communication Interface
- IMU
- Battery Monitoring System

---

# Internal Component

A logical unit within a subsystem that owns a cohesive subset of the subsystem's responsibilities.

Internal components collaborate to fulfill the subsystem's overall responsibilities but do not expose interfaces directly to other subsystems.

Examples:

- Sensor Manager
- State Estimator
- Control Manager
- Safety Manager

---

# Interface

A well-defined contract through which two subsystems exchange information or energy.

Interfaces are classified as:

- Data
- Command
- Configuration
- Power

Interfaces define what is exchanged, not how it is implemented.

---

# Data

Information describing the current state of the system or its environment.

Data interfaces communicate facts.

Examples:

- IMUData
- FlightState
- BatteryState
- SystemHealth

---

# Command

A request for a subsystem to perform an action.

Commands express intent rather than implementation.

Examples:

- FlightCommands
- ActuatorCommand
- ArmCommand

---

# Configuration

Information used to modify the behavior or operation of a subsystem.

Configuration is typically infrequent and persistent.

Examples:

- PIDConfiguration
- SensorCalibration
- CommunicationConfiguration

---

# Power

An interface through which electrical energy is transferred between subsystems.

Power interfaces describe the flow of electrical energy rather than information.

Examples:

- BatteryPower
- ThreePhaseDrive
- RegulatedPower

---

# State

Information describing the current condition of a subsystem or the overall system.

Examples:

- FlightState
- BatteryState
- OperatingMode

---

# Condition

A boolean expression evaluated against one or more inputs or state variables.

Conditions determine whether policies become active.

Examples:

- Communication Lost
- IMU Healthy
- Battery Below Threshold

---

# Policy

A rule that defines what a subsystem should do when one or more conditions are satisfied.

Policies specify decisions rather than implementations.

Examples:

- Failsafe Policy
- Arming Policy
- Landing Policy

---

# Behavior

The observable actions performed by a subsystem while fulfilling its responsibilities or executing a policy.

Examples:

- Controlled Landing
- Publish FlightState
- Generate ThreePhaseDrive

---

# Algorithm

A deterministic computational method used by a subsystem to implement a behavior or produce a result.

Algorithms define how something is computed.

Examples:

- Sensor Fusion
- PID Controller
- Motor Mixer

---

# Telemetry

Operational information published by a subsystem for monitoring, diagnostics or logging.

Telemetry is intended for observation and shall not be required for normal subsystem operation.

---

# Operating Mode

A long-lived operational state of a subsystem.

Examples:

- Initializing
- Ready
- Armed
- Flying
- Landing
- Fault

---

# Failure

A condition in which a subsystem can no longer fulfill one or more of its responsibilities.

---

# Fault

An operating mode entered when a failure prevents safe or correct operation.

---

# Dependency Classification

A categorization of a subsystem's direct external dependencies according to their impact on system operation.

Only direct dependencies shall be documented. Transitive dependencies are intentionally omitted.

Dependency classifications are:

- Flight-Critical
- Mission-Critical
- Optional

---

# Flight-Critical Dependency

A direct external dependency whose loss prevents a subsystem from fulfilling its primary responsibility.

---

# Mission-Critical Dependency

A direct external dependency required to accomplish the intended mission but not required to maintain safe operation.

Loss of a mission-critical dependency shall be handled according to the appropriate policy.

---

# Optional Dependency

A direct external dependency that extends system capability but is not required for safe operation.