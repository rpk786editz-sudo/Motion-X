# 004 Architecture Decision Records (ADR)

Version: 0.1.0
Status: Active

## Purpose
Record significant architectural decisions and their rationale.

---

## ADR-001: Kotlin as Primary Language
Status: Accepted

Decision:
Use Kotlin for all Android application code.

Reason:
- Official Android language
- Excellent coroutine support
- Strong tooling
- Modern language features

Alternatives:
- Java
- Flutter/Dart

---

## ADR-002: Jetpack Compose UI
Status: Accepted

Decision:
Use Jetpack Compose as the UI framework.

Reason:
- Declarative UI
- Better state management
- Modern Android ecosystem

---

## ADR-003: Rendering Hardware Abstraction Layer (RHAL)
Status: Accepted

Decision:
Introduce an abstraction between the rendering engine and graphics APIs.

Reason:
- Easier maintenance
- Vulkan/OpenGL ES support
- Future portability

---

## ADR-004: UUID-Based Object References
Status: Accepted

Decision:
Assign a UUID to every persistent object.

Reason:
- Stable references
- Reliable serialization
- Simplifies future collaboration

---

## ADR-005: Command Pattern
Status: Accepted

Decision:
Implement editing operations as commands.

Reason:
- Undo/Redo
- Macro support
- Easier testing

---

## ADR-006: Non-destructive Editing
Status: Accepted

Decision:
Original assets are never modified.

Reason:
Professional editing workflow and safer user experience.

---

## ADR Maintenance

Each ADR includes:
- Status
- Context
- Decision
- Consequences
- Alternatives
- Date
