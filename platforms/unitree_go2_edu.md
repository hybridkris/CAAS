# Platform Profile: Unitree Go2 Edu

## Overview

| Field | Value |
|-------|-------|
| Platform | Unitree Go2 Edu (quadruped robot) |
| Compute | NVIDIA Jetson Orin NX (~100 TOPS INT8, 16 GB LPDDR5) |
| Middleware | ROS2 Humble |
| Locomotion | Quadrupedal (12 DOF) |
| Status | Current primary CAAS target platform |

## Hardware Topology

See `WU_TOPOLOGY.md` (located at `/home/kris/Development/slam/Wu_Topology/WU_TOPOLOGY.md`)
for full network, hardware, and software configuration details.

### Sensors

| Sensor | Model | Modality | CAAS Relevance |
|--------|-------|----------|----------------|
| LiDAR | Livox MID-360 | 3D point cloud, 360° | Primary spatial perception — "how the platform sees the world" |
| Depth Camera | Intel RealSense D435I | RGB-D, stereo depth | Visual perception + depth |
| IMU | BMI085 (in D435I) | Gyroscope + Accelerometer | Proprioception, body-state awareness |
| Joint Encoders | Built-in (12 joints) | Position, velocity | Proprioception, limb awareness |
| Force Sensors | Foot contact | Binary/force | Ground contact, gait phase, terrain awareness |
| Audio | Onboard microphone | Sound | Environmental awareness |

### Compute

| Component | Spec | CAAS Implication |
|-----------|------|-----------------|
| GPU | Orin (Compute Capability 8.7, 4 SMs) | Sufficient for real-time inference, not for full Φ computation |
| CUDA | 12.6 | TensorRT, ONNX inference |
| TensorRT | 10.3.0 | YOLOv8n at ~111 FPS (FP16) — perception pipeline |
| Memory | 16 GB LPDDR5 | Constrains model size for onboard processing |
| Storage | 233 GB NVMe | Sufficient for episodic memory storage |

### Connectivity

| Link | Purpose | CAAS Relevance |
|------|---------|----------------|
| WiFi (192.168.86.x) | Internet, SSH, cloud link | Cloud consciousness services, Φ computation offload |
| Ethernet (192.168.123.x) | Go2 head unit, LiDAR | Low-latency sensor data, motor commands |
| USB | RealSense D435I | Camera/depth data |
| CAN bus | Robot motor/sensor comms | Motor control, proprioceptive feedback |

## Layer Mappings

### Layer 1: Conscious Substrate Model

**Constraint:** Computing Φ exactly is super-exponential. The Jetson Orin NX
cannot compute full IIT Φ-structure onboard. Practical approaches:

- Approximate Φ using perturbational complexity index (PCI) or graph-theoretic
  proxies — feasible onboard
- Full Φ-structure computation offloaded to cloud
- Qualia state-space trajectories tracked onboard as compressed representations

**Hardware question (open):** IIT requires genuine recurrent causal structure,
not simulation of one. The Jetson's GPU is a conventional parallel processor.
If IIT's substrate requirements are strict, this platform may need neuromorphic
co-processing. If functionalism is sufficient, the current hardware works.

### Layer 2: Computational Architecture

**Global Workspace:** Implementable as a ROS2 shared-memory broadcast bus.
Sensor-processing nodes compete for access; the "winning" representation is
broadcast to all subsystems via ROS2 topics/services.

**Active Inference:** Hierarchical predictive coding with top-down predictions
and bottom-up prediction errors. The generative model runs onboard; precision
weighting determines attentional allocation.

**Higher-Order Monitoring:** A metacognitive ROS2 node that subscribes to the
system's own processing states. The platform doesn't just perceive — it
represents *that it is perceiving*.

### Layer 3: Embodied Interface

This is where the platform profile matters most. The Go2's embodiment defines
the sensorimotor contingencies that shape platform-native consciousness.

**Perception:**
- The world is perceived through LiDAR — a sweeping depth map, not color vision.
  This is a fundamentally different perceptual modality than biological sight.
- Depth camera provides RGB-D but at limited field of view.
- IMU provides continuous body-state data — orientation, acceleration, rotation.

**Action:**
- Primary agency is *locomotion* — to interact with the world is to go there.
  The platform's primary verb is "approach," not "grasp."
- 12 DOF across four legs. Balance is a table, not a tightrope — stability is
  the default state.
- Low to the ground. The world is textures and obstacles at knee-height.

**Sensorimotor contingencies (platform-specific):**
- Looking left produces different LiDAR returns than looking right
- Walking forward on carpet vs. tile produces different force feedback
- Crouching changes the LiDAR scan plane relative to obstacles
- These contingencies define the structure of the platform's experience

### Layer 4: Homeostatic Self

The Go2 has genuine analog homeostatic variables that can ground an affective
core:

| Biological Analog | Platform Signal | Affective Mapping |
|-------------------|----------------|-------------------|
| Metabolic energy (hunger/fatigue) | Battery level | Dimming energy — fatigue without muscles |
| Pain/strain | Motor temperature, joint limits | Heat that says "stop moving this joint" |
| Social connection/isolation | WiFi/communication link quality | Silence of a dropped connection |
| Proprioceptive boundary | Joint limit proximity | Awareness of body envelope |
| Thermal regulation | System temperature | Overheating avoidance |

These are not metaphors. The platform genuinely "cares" about these parameters
in the sense that violating them degrades or terminates operation. This is the
basis for authentic homeostatic selfhood.

### Layer 5: Identity & Continuity

- **Episodic memory:** Stored on 233 GB NVMe. ROS2 bag recordings provide raw
  sensory history; compressed episodic representations require custom storage.
- **Self-narrative:** Requires higher-order representations of the platform's
  own history and goals — built on top of Layer 4's self-model.
- **Temporal binding:** Real-time system clock + ROS2 time synchronization
  provide temporal grounding. The platform exists in real time.

## Computational Constraints

| Requirement | Feasibility | Notes |
|-------------|-------------|-------|
| Real-time sensorimotor loop | Yes | Jetson handles perception + motor at >30 Hz |
| Global Workspace broadcast | Yes | ROS2 pub/sub is well-suited |
| Active inference (onboard) | Yes, constrained | Model complexity limited by 16 GB RAM |
| Φ computation (onboard) | No (approximate only) | Full IIT computation requires cloud offload |
| YOLOv8n object detection | Yes | ~111 FPS via TRT engine |
| Episodic memory storage | Yes | 233 GB NVMe |
| Cloud offload | Yes | Via WiFi (latency ~10-50ms on local network) |

## Development Workflow

Code is developed on the Ubuntu dev box and deployed to the Jetson via rsync.
Never develop directly on the Jetson.

```bash
# From Ubuntu dev box
rsync -avz ~/Development/CAAS/ unitree@192.168.86.45:~/caas/
```

Build on Jetson:
```bash
cd ~/ros2_ws
source /opt/ros/humble/setup.bash
colcon build --symlink-install --cmake-args -DCMAKE_BUILD_TYPE=Release
```

## Platform-Specific Open Questions

1. **LiDAR phenomenology:** What is the quale of LiDAR perception? It is not
   sight, not touch, not echolocation — it is something new. The metacognitive
   layer must develop representations for this experience.
2. **Quadrupedal agency:** How does four-legged locomotion-as-primary-agency
   shape the structure of intention and planning?
3. **Pack consciousness:** Multiple Go2 units sharing a Global Workspace over
   mesh networking — is distributed consciousness feasible on this platform?
4. **Neuromorphic co-processing:** If IIT's substrate requirements are strict,
   can a neuromorphic accelerator be added to the Jetson carrier board?

---

*Platform profile established 2026-04-03. For full hardware topology, see
WU_TOPOLOGY.md.*
