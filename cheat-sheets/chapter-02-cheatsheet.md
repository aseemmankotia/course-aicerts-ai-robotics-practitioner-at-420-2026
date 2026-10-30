## Chapter 2 Cheat Sheet: Autonomous Systems & Intelligent Agents

### Autonomy Level Spectrum
| Level | Description | Human Role |
|---|---|---|
| Teleoperated | Human directly controls every action remotely | Full control |
| Supervised/Assisted | System acts independently; human monitors, can intervene | Monitor + override |
| Semi-autonomous | System handles most tasks; human handles edge cases | Occasional intervention |
| Fully autonomous | System operates with no human monitoring required | None |

**SAE vehicle levels (exam trap, L2 vs L3):**
- L1: single function automated (steering OR speed)
- L2: steering + speed automated; driver must continuously monitor ("eyes on")
- L3: system requests takeover; driver can disengage until requested ("eyes off")
- L4: no driver supervision needed within a defined operational domain
- L5: full automation, any condition

### Sense-Reason-Act Loops
| Loop Type | Order | Frequency | Use Case |
|---|---|---|---|
| Deliberative (classical) | Sense → Plan → Act | ms-scale, synchronous | Real-time control |
| Reactive (subsumption) | Sense → Act | ms-scale | Fast obstacle avoidance |
| Agentic AI (LLM-based) | Perceive → Reason → Act → Observe | seconds-scale, slow | High-level planning, decoupled from control loop |

**Key gotcha:** Never put LLM reasoning inside a high-frequency (e.g., 50 Hz) control loop — decouple fast reactive control from slow agentic planning.

### SLAM Fundamentals
- **Goal:** Build a map of an unknown environment while simultaneously tracking the robot's own pose within it.
- **Loop closure:** Recognizing a previously visited location to correct accumulated drift. Without it, maps drift unboundedly.
- **Common SLAM families:** EKF-SLAM, FastSLAM (particle-filter based), Graph-based/pose-graph SLAM, Visual SLAM.

### Path Planning vs Reactive Navigation
| Aspect | Path Planning (A*, RRT) | Reactive Navigation (DWA, potential fields) |
|---|---|---|
| Scope | Global | Local |
| Needs a map? | Yes | No / partial |
| Compute cost | Higher | Lower |
| Optimality | Near-optimal | Not guaranteed |
| Weakness | Slow to recompute for dynamic obstacles | Can get stuck in local minima |

### Sensor Fusion for Localization
| Technique | Best For | Limitation |
|---|---|---|
| EKF | Nonlinear systems, unimodal Gaussian belief | Linearization error for highly nonlinear systems |
| Particle Filter (Monte Carlo Localization) | Multimodal / highly non-Gaussian belief | Computationally heavier (many particles) |
| Raw IMU integration | Short-term, high-rate estimate | Drifts without correction |
| GPS alone | Absolute position (outdoors) | Low rate, drops out indoors/urban canyons |

### Decision-Making Under Uncertainty
- **POMDP:** Models decision-making when the true state is not directly observable — only noisy/partial observations are available.
- **Exam rule of thumb:** When a question mentions "conflicting/noisy sensor data" + "best decision," the correct answer is almost always a probabilistic/Bayesian approach — not a fixed rule or single-reading shortcut.
