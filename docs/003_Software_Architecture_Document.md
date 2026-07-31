# 003 Software Architecture Document (SAD)

Version: 0.1.0
Status: Draft

## Purpose
Define the high-level architecture of MotionX and the relationships between its major subsystems.

## Architecture Principles
- Modular design
- Separation of concerns
- Mobile-first
- Performance-first
- Non-destructive editing
- Offline-first
- Extensible architecture

## High-Level Layers

```text
UI (Jetpack Compose)
        │
Application Services
        │
Core Engines
        │
Platform Services
        │
Android OS
```

## Core Engines

- Aurora — Rendering Engine
- Chronos — Timeline Engine
- Apollo — Animation Engine
- Nebula — Effects Engine
- Atlas — Project Engine
- Vector — Shape Engine
- Glyph — Text Engine
- Echo — Audio Engine
- Horizon — Camera Engine
- Pulse — Expression Engine

## Cross-Cutting Systems

- Rendering Hardware Abstraction Layer (RHAL)
- Command-based Undo/Redo
- Autosave
- Asset Manager
- Diagnostics
- Logging

## Threading Model

- UI Thread
- Timeline Thread
- Rendering Thread
- Export Thread
- Background Worker Pool

## Storage

- Versioned .mxproj project format
- UUID-based object references
- Incremental autosave
- Crash recovery

## Technology Stack

- Kotlin
- Jetpack Compose
- Vulkan (preferred)
- OpenGL ES fallback
- Room
- Kotlin Coroutines
- Hilt

## Related Documents

- 001_Project_Charter.md
- 002_Product_Requirements_Document.md
- 004_Architecture_Decision_Records.md (planned)

## Revision History

- v0.1.0 Initial draft
