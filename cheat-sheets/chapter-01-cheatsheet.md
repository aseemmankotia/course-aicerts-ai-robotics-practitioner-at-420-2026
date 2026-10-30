# Chapter 1 Cheat Sheet: Robotics and AI Foundations

## Sensors: Proprioceptive vs Exteroceptive
| Type | Measures | Examples |
|---|---|---|
| Proprioceptive | Robot's own internal state | Joint encoder, IMU, gyroscope, force/torque sensor |
| Exteroceptive | External environment | Camera, LiDAR, ultrasonic, infrared proximity |

**Exam trap:** IMU/gyroscope feel 'external' but are proprioceptive — they measure the robot's own motion/orientation, not the environment.

## Actuators: Electric vs Hydraulic vs Pneumatic
| Type | Force | Precision | Cost/Maintenance | Best For |
|---|---|---|---|---|
| Electric | Moderate | High | Low-moderate | General-purpose, precise positioning |
| Hydraulic | Highest | Moderate | High (seals, fluid) | Heavy industrial loads, presses |
| Pneumatic | Low-moderate | Low (air compressible) | Low | Fast, simple on/off grip actions |

## Perception-Plan-Act (Sense-Think-Act) Loop
1. **Perception** — sensors feed raw data, built into a world model
2. **Plan** — decide next action using the world model
3. **Act** — actuators execute the chosen action

**Exam note:** This loop is a top-tested concept — expect direct 'which stage' questions.

## Kinematics
| Term | Input → Output | Notes |
|---|---|---|
| Forward Kinematics | Joint angles → End-effector pose | Single deterministic solution |
| Inverse Kinematics | End-effector pose → Joint angles | Often multiple/no solutions, computationally harder |

**Common mistake:** Swapping forward/inverse direction of computation.

## Degrees of Freedom (DOF)
- DOF = number of independent parameters needed to fully define position/orientation.
- Industrial arms commonly use 6 DOF (x, y, z, roll, pitch, yaw) to achieve full spatial pose control.

## Robot Taxonomy
| Category | Description | Example |
|---|---|---|
| Manipulator | Fixed-base arm | Welding/assembly arm |
| Mobile Robot | Moves through environment | AGV, drone |
| Humanoid | Human-like form, mobility + manipulation | Bipedal service robot |

## Robotics vs AI
- **Robotics**: engineering discipline — sense, plan, act in a physical system.
- **AI**: algorithms for intelligent decision-making/learning; does NOT require a physical body.
- **AI augmenting classical control**: using ML/RL to adapt fixed classical methods (e.g., RL-tuned PID gains, learned perception feeding a planner) rather than relying purely on static equations.

**Exam note:** Expect scenario questions asking whether a described behavior is 'classical control' or 'AI-augmented control' — look for adaptive/learned behavior as the signal for AI involvement.
