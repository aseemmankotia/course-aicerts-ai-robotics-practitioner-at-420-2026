## RL for Robotics — Chapter Cheat Sheet (9% of exam)

### Core Loop
Agent observes **state** → selects **action** via **policy** → environment returns **reward** + next state. Goal: maximize cumulative reward.

### RL vs Classical Control (PID/MPC)
| Factor | Classical Control (PID/MPC) | RL |
|---|---|---|
| Dynamics model | Known/well-modeled | Can be unknown/learned |
| Guarantees | Formal stability proofs | No formal guarantees |
| Control frequency | Handles high-freq (e.g. 1kHz) natively | Often slower inference |
| Best for | Structured, safety-critical tasks | Complex, hard-to-model tasks (locomotion over rough terrain, dexterous manipulation) |
| Common hybrid | MPC for low-level stabilization + RL for high-level gait/behavior | — |

### Algorithm Quick Comparison
| Algorithm | On/Off-policy | Key trait |
|---|---|---|
| PPO | On-policy | Stable, widely used baseline, less sample-efficient |
| SAC | Off-policy | Replay buffer + entropy regularization → sample-efficient |
| TD3 | Off-policy | Deterministic, reduces overestimation bias (DDPG successor) |
| Model-based RL | Either | Learns dynamics model → best real-world sample efficiency |

### Reward Shaping Pitfalls (HEAVILY TESTED)
- **Reward hacking**: proxy reward maximized without achieving true task (e.g., hovering near object instead of grasping). Fix: add explicit success/contact terms.
- **Sparse reward**: slow learning; mitigate with potential-based shaping (preserves optimal policy, unlike arbitrary shaping).
- **Arbitrary dense shaping**: risks changing the optimal policy — avoid unless potential-based.

### Sim-to-Real Transfer (HEAVILY TESTED)
- **Gap causes**: mismatched contact/friction models, sensor noise, actuation latency, unmodeled dynamics.
- **Domain randomization**: randomize friction, mass/inertia, motor strength, sensor noise, latency (NOT just visuals, unless vision-based task).
- **Case study**: OpenAI Dactyl — trained entirely in sim with domain randomization, zero-shot transfer to real Shadow Hand.
- **Other mitigations**: system identification, domain adaptation, residual RL (learn correction on top of a base controller).

### Sample Efficiency
- Model-free (PPO/SAC) on real hardware = expensive, many rollouts needed.
- Model-based RL = learns dynamics model, plans/generates synthetic rollouts → far fewer real rollouts.
- GPU-parallel simulators (e.g., Isaac Gym) run thousands of environments in parallel on one GPU, making sim-based pretraining the dominant strategy before any real-hardware deployment.

### Policy Learning Domains
- **Locomotion (legged robots)**: hybrid MPC+RL common (ANYmal, Mini Cheetah); domain randomization critical for terrain/contact variation.
- **Manipulation/grasping**: reward design is the top failure point; contact-rich dynamics make sim-to-real especially hard; domain randomization + residual learning common fixes.

### Exam Traps
- Assuming more training steps fixes a sim-to-real failure (it doesn't — it's a model mismatch issue).
- Confusing on-policy (PPO) with off-policy (SAC/TD3) when a question asks about replay-buffer reuse.
- Picking RL when the scenario describes known dynamics + safety-critical + high-frequency control (classical control is correct).
