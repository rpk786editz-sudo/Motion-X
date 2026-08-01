# MotionX

> Professional Mobile Motion Graphics & Compositing Platform

## Vision

Build a professional motion graphics application for Android that brings desktop-class animation and compositing workflows to mobile devices — with an interface designed specifically for touch, not ported from desktop.

## Documentation Status

This repository is the official source of truth for MotionX engineering documentation. All specs are versioned Markdown files. No implementation decision is considered final until it has a corresponding document in `docs/`.

## Repository Structure

```text
motion-x/
├── README.md
├── docs/
│   ├── 001_Project_Charter.md
│   ├── 002_Product_Requirements_Document.md
│   ├── 003_Software_Architecture_Document.md
│   ├── 004_Architecture_Decision_Records.md
│   ├── 005_Rendering_Engine.md        (Aurora)
│   ├── 006_Timeline_Engine.md         (Chronos)
│   ├── 007_Animation_Engine.md        (Apollo)
│   ├── 008_Effects_Engine.md          (Nebula)
│   ├── 009_Project_Engine.md          (Atlas)
│   ├── 010_Shape_Engine.md            (Vector)
│   ├── 011_Text_Engine.md             (Glyph)
│   ├── 012_Audio_Engine.md            (Echo)
│   ├── 013_Camera_Engine.md           (Horizon)
│   ├── 014_Expression_Engine.md       (Pulse)
│   ├── 015_Roadmap.md
│   ├── 016_UIUX_Specification.md
│   ├── 017_API_Specification.md
│   ├── 018_Testing_Strategy.md
│   ├── 019_AI_Features.md
│   └── 020_MVP_Implementation_Checklist.md
├── prompts/
├── prototypes/
├── assets/
└── src/                                (future)
```

## Documentation Index

| # | Document | Status |
|---|---|---|
| 001 | Project Charter | Done |
| 002 | Product Requirements Document | Done |
| 003 | Software Architecture Document | Done |
| 004 | Architecture Decision Records | Active |
| 005 | Rendering Engine (Aurora) | Done |
| 006 | Timeline Engine (Chronos) | Done |
| 007 | Animation Engine (Apollo) | Done |
| 008 | Effects Engine (Nebula) | Done |
| 009 | Project Engine (Atlas) | Done |
| 010 | Shape Engine (Vector) | Done |
| 011 | Text Engine (Glyph) | Done |
| 012 | Audio Engine (Echo) | Done |
| 013 | Camera Engine (Horizon) | Done |
| 014 | Expression Engine (Pulse) | Done |
| 015 | Roadmap | Done |
| 016 | UI/UX Specification | Done |
| 017 | API Specification | Done |
| 018 | Testing Strategy | Done |
| 019 | AI Features | Done |
| 020 | MVP Implementation Checklist | Done |

## Numbering Convention

- `001–004` — Foundational planning docs (Charter, PRD, SAD, ADRs)
- `005–014` — Core engine specifications (10 engines named in the SAD get exactly one doc each, in dependency order: rendering → timeline → animation → effects → project → shape → text → audio → camera → expressions)
- `015` — Roadmap
- `016–019` — Cross-cutting specs (UI/UX, API, Testing, AI Features)
- `020+` — Execution artifacts (implementation checklists, per-phase tracking docs)
- New engines or major subsystems get the next free number in sequence; do not reuse or insert into an existing range.

## Project Status

**Phase 0 (Foundation) is complete.** All 10 engines named in the Software Architecture Document have specs, and the cross-cutting docs (Roadmap, UI/UX, API, Testing, AI) are all in place. ADRs 007–012 capture the architectural decisions made while writing the engine specs (see 004_Architecture_Decision_Records.md). Next: Phase 1 (MVP) implementation, tracked in 020_MVP_Implementation_Checklist.md.

## Core Principles

- Mobile-first, not a desktop port
- Professional, non-destructive workflows
- Performance-first (GPU-accelerated, 60 FPS preview target)
- Modular, extensible engine architecture
- Offline-first

## Related

See `015_Roadmap.md` for phased delivery (MVP → v1.0 → v2.0 → v3.0) and current blockers (pending engine specs).

Version: 0.3.0
