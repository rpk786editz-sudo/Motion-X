---
title: "003 Software Architecture Document (SAD)"
document_id: MX-SAD-003
version: 0.2.0
status: Active
---

# 003 Software Architecture Document (SAD)

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
- Audio Thread (dedicated, real-time priority — sample-accurate playback and mixing, per Echo's role as authoritative sync clock, ADR-007, cannot share scheduling with non-real-time background work)
- Export Thread
- Background Worker Pool (includes on-device AI inference, per 019_AI_Features.md)

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
- 004_Architecture_Decision_Records.md
- 005–014_*.md (Core Engine Specifications)
- 017_API_Specification.md (elaborates Application Services / Core Engines layer boundary)
- 018_Testing_Strategy.md

## Revision History

- v0.1.0 Initial draft
- v0.2.0 Added Audio Thread to Threading Model (gap identified against 012_Audio_Engine.md / ADR-007); refreshed Related Documents
- 
