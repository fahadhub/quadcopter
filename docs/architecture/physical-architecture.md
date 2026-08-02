# Physical Architecture

## Purpose

This document describes the physical composition of the aircraft.

Unlike the subsystem architecture, which models functional responsibilities, the physical architecture models the hardware components that comprise the aircraft and their physical relationships.

---

# Physical Structure

The aircraft is composed of the following major assemblies:

```text
Aircraft
├── Frame
│
├── Power System
│   ├── Battery
│   ├── Voltage Regulator
│   └── Wiring Harness
│
├── Flight Electronics
│   ├── Flight Controller
│   ├── IMU
│   ├── Battery Monitoring System (BMS)
│   ├── Communication Interface
│   └── Copilot
│
└── Propulsion System
    ├── ESC ×4
    ├── BLDC Motor ×4
    └── Propeller ×4
```

---

# Power Distribution

The battery supplies electrical power to the propulsion and flight electronics.

```text
Battery
│
├── ESC ×4
│
├── Voltage Regulator
│      │
│      ├── Flight Controller
│      ├── IMU
│      ├── BMS
│      ├── Communication Interface
│      └── Copilot
│
└── Battery Monitoring System
```

---

# Control Flow

Flight commands propagate through the propulsion system as follows.

```text
Ground Station
        │
        ▼
Communication Interface
        │
        ▼
Flight Controller
        │
        ▼
ESC ×4
        │
        ▼
BLDC Motor ×4
        │
        ▼
Propeller ×4
```

---

# System Information Flow

Operational information is aggregated and transmitted to the Ground Station.

```text
Battery Monitoring System
        │
        ▼
     Copilot
        ▲
        │
Flight Controller
        │
        ▼
Communication Interface
        │
        ▼
Ground Station
```

---

# Mechanical Structure

The Frame provides the structural platform for all onboard hardware.

It provides mounting interfaces for:

- Battery
- Flight Controller
- IMU
- Battery Monitoring System
- Communication Interface
- Voltage Regulator
- ESCs
- BLDC Motors
- Propellers

---

# Notes

This document describes the physical composition of the Phase 1 (MVP) aircraft.

Detailed mechanical design, manufacturing, dimensions and material selection are documented separately.