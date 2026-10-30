## Chapter 10 Cheat Sheet — Emerging Technologies and Future Trends

### Core Concept Map
| Concept | One-line definition | Exam angle |
|---|---|---|
| Physical AI | Embodied intelligence: AI that perceives + acts in the physical world | 'Convergence of generative AI + robots' |
| VLA model | Vision-Language-Action foundation model: VLM + action output head | Produces robot control commands, not just text |
| Swarm robotics | Many simple robots coordinating via local rules, no central controller | Robust to individual failures, scalable |
| Digital twin | Virtual simulated replica of robot + environment | Train/test before real deployment |
| Edge AI chip | On-robot SoC for local, low-latency inference | Avoids cloud round-trip latency for safety-critical control |

### VLA Model Landmarks
| Model | Org | Key Point |
|---|---|---|
| RT-2 | Google DeepMind | First major VLA; built on PaLI-X/PaLM-E |
| Gemini Robotics | Google DeepMind | VLA built on Gemini 2.0, 2025 |
| π0 (pi-zero) | Physical Intelligence | General-purpose, cross-embodiment robot model |
| Helix | Figure AI | Powers Figure 02/03 humanoids |

### Humanoid / General-Purpose Platforms
| Platform | Maker | Note |
|---|---|---|
| Optimus Gen 2+ | Tesla | Mass-manufacturing focus |
| Figure 02/03 | Figure AI | Uses Helix VLA |
| H1 / G1 | Unitree | Lower-cost, widely deployed |
| Atlas (electric) | Boston Dynamics | Fully electric, dynamic manipulation |

### Swarm Robotics Principles
- **Decentralization** — no single point of control or failure
- **Local sensing/communication only** — robots act on nearby info
- **Stigmergy** — indirect coordination via shared environment changes
- **Emergence** — global behavior arises from simple local rules
- Reference: Kilobot swarm (Harvard, 2014) — 1,024 robots self-organized

### Edge AI for Robotics
- Jetson Orin → prior-gen robotics edge chip
- Jetson Thor → newer SoC class built for transformer/VLA workloads on humanoids
- Why edge, not cloud: real-time control loops cannot tolerate network latency

### Digital Twins
- NVIDIA Isaac Sim / Omniverse = primary platform referenced on the exam
- Use case: simulate policy training + fleet-wide testing before physical rollout

### Common Exam Traps
1. Confusing VLM (vision-language only) with VLA (adds action output) — exam tests the distinction directly.
2. Assuming swarm robotics needs a central coordinator — it explicitly does NOT.
3. Assuming fine-tuning a VLA model needs massive new datasets — correct answer is usually small, few-shot demonstration sets.
4. Mixing up 'Physical AI' with 'physical/on-prem servers' — it refers to embodied intelligence, not deployment location.
5. Picking cloud inference for safety-critical real-time control scenarios — edge AI chips are the correct answer when latency/safety is mentioned.
