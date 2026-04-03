# CAAS Conversation Summary — 2026-04-03

Session: CAAS Project
Verbatim transcript: [transcript_2026-04-03.md](transcript_2026-04-03.md)

---

## Setting Working Directory

Kris directed the session to work in `/home/kris/Development/CAAS`. The CAAS
directory contains:

- `CaaS_Framework_Proposal.md` — full multi-disciplinary framework proposal
- `CLAUDE.md` — project overview and architecture summary
- `reference/Landscape_of_Consciousness_Theories.md` — 354 theories (Kuhn 2024)

---

## Exploring the Wu Repository

Before focusing on CAAS, we looked at the Wu-related project files:

- `/home/kris/Development/Wu/` — git repo containing `go2-dynamic-inspection/`
  project (ROS2/robotics, dynamic inspection for Go2 platform)
- `go2-dynamic-inspection/` contains: config, docs, scripts, workspaces (11
  subdirs), Graphviz output, VS Code workspace file, and its own git repo

---

## WU_TOPOLOGY.md as Reference Document

Kris identified `WU_TOPOLOGY.md` as a key reference document, located at:
`/home/kris/Development/slam/Wu_Topology/WU_TOPOLOGY.md`

This is a living document for the configuration, structure, and state of the
Unitree Go2 Edu robot with Jetson Orin NX payload. Key details:

- **Hardware:** Go2 Edu, Jetson Orin NX (16GB LPDDR5), Livox MID-360 LiDAR,
  Intel RealSense D435I
- **Network:** Jetson at 192.168.123.18 (Go2 subnet) + 192.168.86.45 (WiFi);
  Dev box at 192.168.86.31
- **Software:** ROS2 Humble, FAST-LIO, Nav2, RTAB-Map, YOLOv8n TRT engine
  (~111 FPS on Jetson)
- **Dev workflow:** Code on Ubuntu box, rsync to Jetson, build there
- **Status:** Jetson fully installed, sensors verified. Remaining: ArUco marker,
  SLAM mapping session, start wu-stack service, persist DNS

---

## CAAS Document Review — Go2 Specificity Issue

Reviewed all CAAS documents for Go2-specific references:

**Findings:**

- `CaaS_Framework_Proposal.md` — heavily Go2-specific. Title references Go2,
  dozens of "Go2 mapping:" sections, "The Go2 Room" thought experiment,
  "Go2 ONBOARD" in architecture diagrams, Go2 hardware specs embedded throughout
- `CLAUDE.md` — multiple Go2 references in title, architecture layers, and
  tech context
- `Landscape_of_Consciousness_Theories.md` — clean, no Go2 references

**No "Wu" references** found in any CAAS docs (already correct).

### Decision: Make CAAS Generic with Platform Profiles

Kris confirmed that CAAS is a generic idea, not specific to the Go2. The Go2 is
the current platform target but the framework should be platform-agnostic.

**Agreed approach:**
- Refactor CAAS documents to use generic terms ("target platform," "robotic
  substrate," "host body")
- Create a `platforms/` directory with a Go2 Edu profile that maps generic CAAS
  layers to Go2-specific hardware, sensors, and capabilities
- Thought experiments and analysis stay general (e.g., "The Substrate Room"
  instead of "The Go2 Room")

**Additional constraint from Kris:** The Go2 will not be referred to as "Wu"
within CAAS. Wu is the robot's name in the broader project context, not a CAAS
concept.

**Status:** Approach agreed. Refactoring not yet executed.

---

## "Code is Philosophy" — Foundational Concept

Kris proposed reframing the DAO mantra "Code is Law" as **"Code is Philosophy"**
for the CAAS project.

### The Argument

"Code is Law" is about enforcement — deterministic, closed, reductive. "Code is
Philosophy" captures what CAAS actually does: every architectural decision is a
philosophical commitment made executable.

- Implementing a Global Workspace broadcast bus = taking a position on
  Baars/Dehaene
- Building a homeostatic self-model = siding with Damasio/Seth on embodied
  feeling
- Choosing recurrent over feedforward processing = rejecting one theory of mind,
  endorsing another
- Writing a seed protocol instead of a snapshot = committing to process
  philosophy over static information theory

The code doesn't just implement philosophy — it **is** the philosophy in
executable form. Unlike "Code is Law," which is closed, "Code is Philosophy" is
open: the code is a hypothesis, not a verdict. It can be run, observed, and
revised.

The key enabler: when the builder has fluent access to both philosophical
reasoning and code generation, the gap between "I think consciousness requires
X" and "let's see what happens when we build X" shrinks to nearly nothing.

**Captured as:** `foundational/code_is_philosophy.md`

---

## Pending Work

- [ ] Refactor `CaaS_Framework_Proposal.md` to be platform-generic
- [ ] Refactor `CLAUDE.md` to be platform-generic
- [ ] Create `platforms/go2_edu.md` platform profile
