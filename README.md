# Quadcopter From Scratch

> A long-term engineering project to design, build, and understand a fully functional quadcopter from first principles.

## Project Vision

The goal of this project is to design and build a fully functional quadcopter where every major subsystem is engineered from scratch. Rather than assembling an existing flight controller or using an off-the-shelf firmware stack, the objective is to understand and implement the underlying engineering ourselves.

The finished quadcopter should be capable of stable flight and be controllable using either:

- A dedicated handheld controller
- A custom Android application acting as a virtual controller

This project prioritizes understanding, experimentation, and engineering ownership over rapid development.

---

# Objectives

The project aims to design, implement, and document:

- Airframe (body/frame)
- Flight controller hardware
- Power distribution
- Firmware
- Sensor drivers
- Sensor calibration
- Sensor fusion
- Flight stabilization
- Control algorithms
- Motor mixing
- ESC communication
- Communication protocols
- Android controller application
- Telemetry
- Testing procedures
- Complete documentation

Where practical, existing hardware components (motors, ESCs, sensors, batteries, etc.) may be used initially, but every component should be thoroughly understood before integration.

---

# Guiding Principles

## 1. Understand Before Using

Every subsystem should be understood before it is integrated into the project.

## 2. Build From First Principles

Whenever practical, algorithms and systems should be implemented from scratch instead of relying on existing drone software.

## 3. Document Everything

Every design decision, experiment, success, and failure should be recorded.

## 4. Modular Design

Each subsystem should be independently testable and replaceable.

## 5. Safety First

Hardware and software should always fail safely.

## 6. Iterative Development

Build small, test thoroughly, improve continuously.

## 7. Learning Over Speed

The objective is not to finish quickly.

The objective is to understand why every part of the quadcopter works.

---

# Project Philosophy

This project is intended to be an engineering notebook as much as it is a code repository.

Every design decision should answer questions such as:

- Why was this chosen?
- What alternatives were considered?
- What trade-offs exist?
- How can this be improved?

If six months pass without working on the project, the repository should contain enough documentation to immediately understand the current state of the system.

---

# Definition of Success

The project will be considered successful when it produces a quadcopter that:

- Can take off safely
- Can hover stably
- Can be manually flown
- Can be controlled using either:
  - A dedicated controller
  - A custom Android application
- Uses firmware, control algorithms, and supporting software developed within this project
- Is sufficiently documented that another engineer could reproduce it using only this repository

---

# Development Philosophy

This repository values:

- Engineering over shortcuts
- Understanding over imitation
- Documentation over memory
- Simplicity over unnecessary complexity
- Incremental progress over perfection

The goal is not simply to build a drone.

The goal is to become capable of designing one.

---

# Repository Structure

```
.
├── docs/
├── firmware/
├── hardware/
├── simulations/
├── tools/
├── test/
├── journal/
└── README.md
```

This structure will evolve as the project grows.

---

# Roadmap

- [ ] Project planning
- [ ] Hardware selection
- [ ] IMU bring-up
- [ ] Sensor calibration
- [ ] Sensor fusion
- [ ] Attitude estimation
- [ ] ESC control
- [ ] Single-motor testing
- [ ] PID controller
- [ ] Motor mixer
- [ ] Four-motor test bench
- [ ] First powered hover
- [ ] Manual flight
- [ ] Android controller
- [ ] Telemetry
- [ ] Autonomous features (future)

---

# License

This project is released under the MIT License unless otherwise specified.
