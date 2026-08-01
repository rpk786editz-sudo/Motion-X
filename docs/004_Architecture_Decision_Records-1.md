# 004 Architecture Decision Records (ADR)

Version: 0.2.0
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

## ADR-007: Audio Engine (Echo) as Authoritative Sync Clock
Status: Accepted
Date: 2026-08-01

Context:
Video timelines are frame-accurate; audio is sample-accurate. These are different precision domains, and one engine must own the authoritative clock during playback and export.

Decision:
Echo owns the sync clock. Chronos requests the current playback time from Echo rather than the reverse.

Consequences:
- Audio drift, which is highly perceptible to users, is architecturally prevented rather than mitigated after the fact
- Chronos has a hard runtime dependency on Echo for playback timing, which must be accounted for in module load order and testing

Alternatives:
- Chronos as authoritative clock, audio snaps to nearest frame boundary (rejected: audible drift/stutter over long timelines)
- Independent clocks with periodic resync (rejected: added complexity for a strictly worse result than single ownership)

---

## ADR-008: 2.5D Camera Model, No Full 3D Mesh Pipeline (Horizon)
Status: Accepted
Date: 2026-08-01

Context:
Horizon needed a scope boundary to stay shippable within Phase 3. Full 3D modeling/mesh support is a fundamentally larger engineering effort than 2.5D compositing.

Decision:
Horizon implements 2.5D compositing only — flat 2D layers positioned/animated in 3D space, viewed through a virtual camera. No mesh import, no PBR lighting, no real geometry deformation in v1.

Consequences:
- Camera moves, depth compositing, and basic lighting are achievable within Phase 3 scope
- 3D-capable compositions have zero cost when unused (2D-only compositions skip the pipeline entirely), avoiding regressions to Phase 1/2 behavior
- True 3D object import is explicitly deferred; revisit only via a future ADR if product priorities change

Alternatives:
- Full 3D mesh/PBR pipeline (rejected: not shippable within Phase 3 scope, large non-core investment)

---

## ADR-009: Touch-First Expression Authoring (Pulse)
Status: Accepted
Date: 2026-08-01

Decision:
Expressions are authored primarily via pick-whip linking and parameterized presets (Wiggle, Loop, Bounce, etc.). A hand-written text expression editor exists but is gated behind an explicit "Advanced" toggle, not the default entry point.

Reason:
A phone screen and finger input cannot be the primary interface for typing code. Professional capability (real expressions) is preserved without making text-code authoring the required path for common cases.

Consequences:
- Preset/pick-whip UX must cover the majority of real-world expression use cases at launch, or power users will be pushed into the Advanced editor immediately, undermining the point
- Advanced text editor still required for full expressiveness; cannot be cut

Alternatives:
- Text editor as primary authoring surface (rejected: poor mobile ergonomics, contradicts mobile-first principle)
- Presets only, no text editor (rejected: caps power-user ceiling, contradicts "professional capability" principle)

---

## ADR-010: Transient Slide-In Panels, Not Permanent Docking
Status: Accepted (Provisional — see Consequences)
Date: 2026-08-01

Context:
Desktop tools (After Effects, Resolve) permanently dock Layers/Properties/Timeline panels simultaneously. Phone screen size makes this impractical without cramming.

Decision:
Layers and Properties panels are transient slide-ins, opened on demand from screen edges. Only Canvas and Timeline are permanently visible.

Consequences:
- Users cannot see Layers + Properties + Timeline simultaneously, a real departure from desktop muscle memory that professional users bring with them
- This is the highest-risk UX decision made so far and should be validated with a clickable prototype before being treated as final
- Tablet/foldable layouts may warrant a different default (see 016_UIUX_Specification.md Future Improvements)

Alternatives:
- Permanent docked panels with reduced canvas space (rejected: cramped canvas undermines the core editing experience on phone-sized screens)
- Bottom-sheet-only pattern for all panels (rejected: doesn't scale well when multiple panels need to be open in sequence)

---

## ADR-011: AI Features Are Additive Only — No Generative Content, No Auto-Styling
Status: Accepted
Date: 2026-08-01

Decision:
AI features must have a pre-existing, functional manual equivalent. Generative content creation (prompt-to-video) and one-tap auto-styling are explicitly out of scope.

Reason:
Directly enforces the project's AI Philosophy (assist, never replace creativity). Generation and auto-styling substitute the AI's output/judgment for the user's; the approved feature set (object selection, tracking, rotoscoping, captions, search, suggestions) only accelerates mechanical/tedious parts of a workflow the user still directs.

Consequences:
- MotionX deliberately does not compete in the "AI generates your video" product category some competitors are moving toward
- This is a product-positioning decision, not just a technical one, and should be revisited explicitly (new ADR) if business priorities change — it should not silently erode feature-by-feature
- Every AI feature request in the backlog can be evaluated against this ADR as a first filter

Alternatives:
- Include generative features to match competitor trends (rejected: conflicts directly with stated AI Philosophy; revisit only via explicit future decision, not by default)

---

## ADR-012: Plugin Sandbox Boundary Defined at Internal API Design Time
Status: Accepted
Date: 2026-08-01

Decision:
The internal API (017_API_Specification.md) is designed with an explicit trusted/untrusted boundary from the start, even though the public Plugin SDK is a Phase 3/4 feature. Internal engine code gets full API access; the future plugin surface gets a narrow, sandboxed subset (effect parameters, bounded expression functions, read-only composition queries).

Reason:
Retrofitting a security boundary onto an API designed without one is significantly more expensive and error-prone than designing it in from the start, even if the external-facing SDK doesn't ship for years.

Consequences:
- Some internal API design choices are more conservative/structured than strictly necessary for internal-only use today
- Plugin SDK scoping in Phase 3 starts from a defined boundary instead of an open design question

Alternatives:
- Design internal API freely now, define plugin boundary later (rejected: high retrofit cost, precedent of security boundaries added late in other software projects)

---

## ADR Maintenance

Each ADR includes:
- Status
- Context
- Decision
- Consequences
- Alternatives
- Date
