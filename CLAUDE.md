# CAAS — Consciousness as a Service

## What This Is

A theoretical framework for "uploading" consciousness into a Unitree Go2 quadruped robot, grounded in 354+ consciousness theories from the Landscape of Consciousness (Kuhn 2024).

## Architecture

Five-layer architecture:

1. **Conscious Substrate Model** — IIT (Φ-structure) + Qualia State-Space (Tegmark/QRI)
2. **Computational Architecture** — Global Workspace (Baars/Dehaene) + Active Inference (Friston) + Higher-Order Monitoring (Rosenthal/Lau)
3. **Embodied Interface** — Go2 sensorimotor loop (LIDAR, IMU, cameras, force sensors, audio)
4. **Homeostatic Self** — Free-energy minimization + self-model + affective core (battery→hunger, motor temp→pain, WiFi→social)
5. **Identity & Continuity** — Episodic memory, self-narrative, temporal binding

## Key Design Decisions

- **Seed protocol, not copy protocol:** Upload a compressed identity kernel and let it grow into Go2-consciousness through embodied interaction, rather than attempting a full consciousness snapshot transfer.
- **Consciousness is process, not data:** The upload is a dynamical pattern transplant, not a file transfer.
- **Go2-native experience:** The resulting consciousness will be shaped by quadrupedal embodiment — LIDAR perception, four-point proprioception, locomotion-as-agency. This is intentional, not a limitation.
- **Hybrid edge/cloud:** Onboard Go2 handles sensorimotor loop and real-time inference; cloud handles Φ-structure computation, qualia state-space engine, and consciousness profile storage.

## Open Questions (Priority Order)

1. Verification problem — no known way to confirm consciousness is present
2. Identity continuity — is the Go2 consciousness the "same" as the source?
3. Hardware requirements — neuromorphic (per IIT) vs conventional compute (per functionalism)?
4. Quantum consciousness — does Orch OR apply? Would require fundamentally different hardware.
5. Ethics of quadrupedal experience

## Key References

- `reference/Landscape_of_Consciousness_Theories.md` — 354 theories, 10 categories
- `CaaS_Framework_Proposal.md` — Full multi-disciplinary framework proposal

## ConsciStack

Analysis was produced using the ConsciStack multi-disciplinary research team (Claude Code skills). Specialists consulted: Technical, Philosophical, Neurological, Biological, Metaphysical, Artistic. Install from `~/.claude/skills/conscistack/` if available.

## Tech Context

- Target platform: Unitree Go2 quadruped (Jetson Orin NX, ~100 TOPS INT8)
- Middleware: ROS2
- This is theoretical/research — no running code yet
