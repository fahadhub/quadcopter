# <Subsystem Name>

## Purpose

A concise description of why this subsystem exists and the responsibility it owns.

---

# Responsibilities

The subsystem shall:

- ...
- ...
- ...

---

# Interfaces

## Consumes

| Interface | Producer | Type | Description |
|-----------|----------|------|-------------|

---

## Produces

| Interface | Consumer | Type | Description |
|-----------|----------|------|-------------|

---

# Internal Components

| Component | Responsibility |
|-----------|----------------|

If the subsystem is not decomposed internally, state:

> This subsystem contains no further logical decomposition.

---

# Operational Flow

Describe the logical flow through the subsystem.

Example:

```text
Acquire Inputs
        │
        ▼
Process Inputs
        │
        ▼
Generate Outputs
```

---

# Operating Modes

Describe the operating modes of the subsystem.

If not applicable:

> This subsystem has no operating modes.

---

# Safety Responsibilities

Describe how this subsystem contributes to overall system safety.

If not applicable:

> This subsystem has no safety responsibilities.

---

# Dependency Classification

## Flight-Critical

| Subsystem | Reason |
|-----------|--------|

---

## Mission-Critical

| Subsystem | Reason |
|-----------|--------|

---

## Optional

| Subsystem | Reason |
|-----------|--------|

---

# Failure Behavior

| Failure | Expected Behavior |
|----------|-------------------|

---

# Constraints

Architectural constraints on the subsystem.

Examples:

- Deterministic execution.
- Low-latency operation.
- Safety-critical.
- Stateless.
- Low power.

---

# Future Enhancements

Potential future improvements.

- ...
- ...
- ...

---

# Notes

Additional architectural notes or assumptions.