## Chapter 10: Emerging Technologies and Future Trends — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | What does VLA stand for in robotics foundation models? | Vision-Language-Action. Exam tip: VLA = VLM + an action output head that generates robot control commands (e.g., joint targets) from camera + text input. |
| 2 | RT-2 (Google DeepMind) significance | One of the first major VLA models (2023), built on PaLI-X/PaLM-E, transferring web-scale vision-language knowledge to direct robot control. Exam tip: canonical early VLA example. |
| 3 | Physical Intelligence's π0 (pi-zero) model | A general-purpose robot foundation model (2024) designed to control multiple different robot embodiments from one base model. Exam tip: example of cross-embodiment generalization. |
| 4 | Stigmergy (swarm robotics) | Indirect coordination where robots communicate by modifying a shared environment (e.g., pheromone-like trails) rather than messaging each other directly. Exam tip: core decentralized coordination mechanism. |
| 5 | Three core properties of swarm robotics | Decentralization, local sensing/communication only, emergent global behavior. Exam tip: no robot holds global state — swarm is robust to individual robot failure. |
| 6 | Jetson Thor vs Jetson Orin | Jetson Thor is NVIDIA's newer robotics/humanoid SoC succeeding Orin, built for running transformer/VLA workloads at the edge with much higher AI compute. Exam tip: Thor = humanoid-class edge AI chip. |
| 7 | Why run VLA inference on-robot (edge) instead of the cloud? | Low-latency control loops, no dependency on network connectivity, and safety-critical response times. Exam tip: edge AI chips exist because cloud round-trip latency is unsafe for real-time manipulation. |
| 8 | Digital twin for a robot fleet | A virtual simulated replica of robots + their environment (e.g., NVIDIA Isaac Sim/Omniverse) used to train and test policies before real deployment and to monitor fleets. Exam tip: reduces real-world trial cost and risk. |
| 9 | 'Physical AI' (industry term) | Embodied AI models that perceive and act in the physical world — the convergence of generative AI and robotics (popularized by NVIDIA around CES 2024-2025). Exam tip: Physical AI = generative AI + physical embodiment. |
| 10 | Examples of general-purpose humanoid platforms (2025-2026) | Figure 02/03 (Figure AI, Helix VLA), Tesla Optimus Gen 2+, Unitree H1/G1, Boston Dynamics all-electric Atlas. Exam tip: these are general-purpose manipulation platforms, not single-task robots. |
| 11 | Fine-tuning a pretrained VLA foundation model for a new task | Requires only a small set of task-specific demonstrations (few-shot fine-tuning) because broad vision-language-action priors are already learned. Exam tip: contrast with training a narrow RL policy from scratch, which needs far more data. |
| 12 | Kilobot swarm milestone | Harvard's Kilobot project (2014) demonstrated a self-organizing swarm of 1,024 low-cost robots. Exam tip: classic reference example for large-scale decentralized swarm coordination. |
