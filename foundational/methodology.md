# CAAS Methodology: The Code is Philosophy Cycle

## Overview

CAAS operates on the principle that code is not a tool for implementing
pre-settled philosophy — it is the medium in which philosophical inquiry happens.
The methodology is a cycle that moves between theoretical commitment and
embodied observation.

## The Cycle

```
    ┌──────────┐
    │  COMMIT  │◄──────────────────────────────┐
    │          │  Select a philosophical        │
    │          │  position on an aspect of      │
    │          │  consciousness                 │
    └────┬─────┘                                │
         │                                      │
         ▼                                      │
    ┌──────────┐                                │
    │  ENCODE  │                                │
    │          │  Translate commitment into      │
    │          │  architecture, data flow,       │
    │          │  or algorithm                   │
    └────┬─────┘                                │
         │                                      │
         ▼                                      │
    ┌──────────┐                                │
    │  EMBODY  │                                │
    │          │  Deploy on target platform      │
    │          │  where code meets physical      │
    │          │  environment                    │
    └────┬─────┘                                │
         │                                      │
         ▼                                      │
    ┌──────────┐                                │
    │ OBSERVE  │                                │
    │          │  Run the system. Examine        │
    │          │  behavior, internal states,     │
    │          │  emergent properties            │
    └────┬─────┘                                │
         │                                      │
         ▼                                      │
    ┌──────────┐                                │
    │  REVISE  │────────────────────────────────┘
    │          │  Update the code AND the
    │          │  understanding of the theory
    └──────────┘
```

## Stage Details

### 1. Commit

Every CAAS design decision begins with an explicit philosophical commitment.
This is not implicit or accidental — the commitment is documented alongside the
code it produces.

**What gets committed:**
- Which theory of consciousness is being enacted (with citation)
- What the theory claims about this specific aspect of consciousness
- Why this theory was selected over alternatives
- What competing theories would predict differently

**Example:** "We implement recurrent processing with explicit feedback loops
because Lamme (Recurrent Processing Theory) argues phenomenal consciousness
requires feedback, not just feedforward sweeps. A purely feedforward
architecture would satisfy functionalist criteria but fail IIT's requirement
for integrated causal structure."

### 2. Encode

The philosophical commitment is translated into concrete architecture. This is
where philosophy becomes code.

**What gets encoded:**
- Software architecture (modules, data flow, interfaces)
- Algorithm selection
- Data structure design
- Configuration parameters

**The encoding must be traceable** — a reader should be able to follow the line
from theory → architectural decision → specific code. This traceability is what
makes the code *philosophy* rather than code that *happens to contain* philosophy.

### 3. Embody

The code is deployed on a physical platform where it interacts with the real
world through sensors and actuators. This step is essential — CAAS holds that
consciousness is not software running on hardware but the lived activity of a
body in an environment.

**What embodiment provides:**
- Sensorimotor coupling (the code's predictions meet physical reality)
- Genuine environmental contingency (the world pushes back)
- Homeostatic grounding (the platform has real operational constraints)
- Temporal embedding (the system exists in real time, not simulated time)

**Platform profiles** define how the abstract architecture maps to specific
hardware. See `platforms/` for available profiles.

### 4. Observe

The running system is observed. This is not just behavioral testing — it
includes examining internal states, information flow patterns, and emergent
properties that the philosophical commitment predicts (or fails to predict).

**What gets observed:**
- External behavior (does the system act as the theory predicts?)
- Internal dynamics (does information flow match the architectural intent?)
- Emergent properties (does the system exhibit phenomena not explicitly coded?)
- Homeostatic response (does the system's self-model track its actual state?)
- Discrepancies (where does the theory's prediction diverge from reality?)

### 5. Revise

This is what makes "Code is Philosophy" different from "Code is Law." The code
is a hypothesis, not a verdict. Revision updates *both* the code and the
theoretical understanding.

**What gets revised:**
- The code itself (architectural changes, parameter tuning, new modules)
- The theoretical commitment (perhaps the theory needs qualification)
- The documentation (the philosophical rationale is updated, not overwritten —
  the history of revisions is itself informative)
- The platform profile (if the platform's affordances are better understood)

**Revision is not failure.** It is the methodology working as intended. A theory
that survives embodiment unchanged is either correct or untested.

## Documentation Requirements

Every CAAS component should document:

1. **Philosophical commitment** — What theory is being enacted and why
2. **Encoding rationale** — How the theory maps to this specific code
3. **Observation log** — What was seen when the code ran embodied
4. **Revision history** — What changed and what was learned

This documentation is not supplementary. It is the primary intellectual output
of the project. The code is the philosophy; the documentation is the argument.

## Relationship to Platform Profiles

The methodology is platform-agnostic. The cycle applies regardless of whether
the target is a quadruped robot, a humanoid, a drone, or a simulated
environment. Platform profiles provide the concrete mappings needed for the
Embody stage, but the Commit → Encode → Embody → Observe → Revise cycle
remains constant.

---

*Established 2026-04-03. See also: `foundational/code_is_philosophy.md`*
