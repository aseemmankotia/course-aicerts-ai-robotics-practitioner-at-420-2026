## Chapter 3 Cheat Sheet — AI & Robotics Development Frameworks (9%)

### ROS 2 Communication Patterns
| Pattern | Model | Blocking? | Use Case |
|---|---|---|---|
| Topic | Pub/Sub, many-to-many | No | Continuous sensor streams, telemetry |
| Service | Request/Response, 1-to-1 | Yes (caller) | Quick one-off computation |
| Action | Goal/Feedback/Result | No (async goal) | Long-running tasks (navigation, arm movement) |

**Exam note:** Actions are built on topics (feedback/status) + services (goal/cancel).

### DDS Middleware
- DDS = Data Distribution Service — ROS 2's core middleware for discovery, serialization, real-time messaging.
- No central broker — peer-to-peer discovery between nodes.

### Key DDS QoS Policies
| Policy | Option A | Option B | When to Use |
|---|---|---|---|
| Reliability | Best Effort (fast, no guarantee) | Reliable (guaranteed, slower) | Camera feed = Best Effort; safety commands = Reliable |
| Durability | Volatile (no history for late joiners) | Transient Local (caches last messages) | Static config/state = Transient Local |
| History | Keep Last (N) | Keep All | Most robotics use Keep Last with small depth |

**Common mistake:** Choosing Reliable + Volatile for state data — message is guaranteed delivered but still missed by late subscribers since nothing is cached.

### Simulation Tools
| Tool | Purpose | Strength |
|---|---|---|
| Gazebo | Open-source physics simulation | Fast iteration, lightweight, good for early algorithm testing |
| NVIDIA Isaac Sim | Omniverse-based, GPU-accelerated | Photorealistic rendering, synthetic data generation, large-scale RL training |

**Exam note:** Gazebo = functional/physics testing; Isaac Sim = perception training data + photorealism + scale.

### Simulation-First Workflow
Develop → Test in simulation (Gazebo/Isaac Sim) → Validate behavior/physics → Deploy to real hardware. Reduces hardware risk and cost of bugs.

### Robotics Software Stack (bottom → top)
1. **Driver** — translates hardware signals (sensors/actuators) into software messages
2. **Middleware** — ROS 2 + DDS handles node communication
3. **Perception** — processes sensor data (vision, SLAM, sensor fusion)
4. **Planning** — determines path/task sequence from perception output
5. **Control** — sends commands to actuators to execute the plan

**Exam note:** Questions often ask 'which layer does X' — map the described function to driver/perception/planning/control precisely.

### Packages & Launch Files
- **Package**: organizational unit containing nodes, configs, launch files, dependencies.
- **Launch file**: starts multiple nodes at once with parameters/remappings (XML, Python, or YAML format in ROS 2).

**Common mistake:** Confusing package.xml (metadata/dependencies) with launch files (runtime node startup) — they serve different purposes.
