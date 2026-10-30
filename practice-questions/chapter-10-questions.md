## Chapter 10: Emerging Technologies and Future Trends — Practice Questions

**Q1.** A robotics startup wants a single AI model to control a manipulator arm so it can pick and place dozens of unseen object types without task-specific reprogramming. Which approach BEST meets this requirement?

A) Hand-coded motion planning rules for each object category
B) A single-task reinforcement learning policy trained only on the known objects
C) A Vision-Language-Action (VLA) foundation model fine-tuned on diverse manipulation demonstrations
D) A fixed PID controller tuned for one gripper trajectory

<details>
<summary>Answer</summary>

**Correct: C**

VLA models are pretrained on broad vision-language-action data, giving them generalization across tasks and objects that single-purpose controllers lack.

**Why the others are wrong:**
- Hand-coded rules don't scale to unseen objects — requires reprogramming per object
- A single-task RL policy only generalizes to the task it was trained on
- PID control handles trajectory tracking, not high-level perception/decision-making

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A warehouse deploys 50 small mobile robots that must self-organize to cover floor space efficiently, with no central server, and must keep working even if 10 robots fail. Which design principle should the architecture follow?

A) Decentralized swarm coordination using local sensing and simple local rules
B) A centralized fleet manager that assigns every robot's path
C) A master-slave hierarchy where one robot commands the rest
D) Cloud-based batch scheduling recalculated every hour

<details>
<summary>Answer</summary>

**Correct: A**

Swarm robotics achieves robustness and scalability precisely because no single point of failure exists — each robot acts on local information, and global behavior emerges.

**Why the others are wrong:**
- A centralized manager is a single point of failure, violating the fault-tolerance requirement
- Master-slave still has a single point of failure if the master fails
- Cloud batch scheduling introduces latency and still depends on a central service

</details>

---

**Q3.** A humanoid robot manufacturer needs an on-board chip to run a transformer-based VLA model in real time for safety-critical manipulation, without relying on a network connection. Which solution fits BEST?

A) Stream all sensor data to a cloud GPU cluster for inference
B) A dedicated edge AI SoC designed for robotics inference (e.g., NVIDIA Jetson Thor class)
C) A general-purpose laptop CPU
D) A low-power microcontroller used for basic motor PWM signals

<details>
<summary>Answer</summary>

**Correct: B**

On-robot edge AI accelerators (NVIDIA's Jetson Thor-class SoCs) are purpose-built to run large transformer/VLA workloads locally with the low latency safety-critical control requires.

**Why the others are wrong:**
- Cloud inference adds network round-trip latency unsafe for real-time control
- General CPUs lack the parallel tensor compute needed for transformer inference at required speed
- Microcontrollers lack the compute for running foundation models at all

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** Which NVIDIA platform is primarily used to build a virtual replica of a robot and its environment for simulation-based training and fleet testing before real-world deployment?

A) NVIDIA Isaac Sim / Omniverse
B) Jetson Orin
C) TensorRT
D) CUDA Toolkit

<details>
<summary>Answer</summary>

**Correct: A**

Isaac Sim, built on Omniverse, is NVIDIA's platform for creating digital twins of robots and environments for photorealistic, physics-accurate simulation and training.

**Why the others are wrong:**
- Jetson Orin is an edge inference chip, not a simulation/digital-twin platform
- TensorRT is an inference optimization library, not a simulation environment
- CUDA Toolkit is the general GPU programming framework, not a digital twin tool

</details>

---

**Q5.** Which statement BEST describes the industry term 'Physical AI' as used in robotics in 2026?

A) AI software that only runs on physical on-premises servers rather than the cloud
B) A marketing term with no technical meaning distinct from traditional robotics
C) Robots that operate without any AI model, using only classical control theory
D) Embodied intelligence in which AI models learn to perceive, reason about, and act within the physical world via sensors and actuators

<details>
<summary>Answer</summary>

**Correct: D**

Physical AI refers to embodied foundation models that understand physical dynamics and translate perception into real-world action — the convergence of generative AI and robotics.

**Why the others are wrong:**
- This confuses 'physical' hardware deployment with the embodied-intelligence concept
- It is a specific technical concept tied to foundation models and embodiment, not just marketing
- Physical AI specifically implies AI-driven, not classical-control-only, systems

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** An engineer wants to adapt a pretrained VLA foundation model to a new bin-picking task on a factory floor. What is typically required?

A) Training an entirely new model from scratch with millions of labeled examples
B) No training at all — the base model works identically on any new task
C) A small set of task-specific demonstrations used to fine-tune the pretrained model
D) Only text descriptions of the task, with no demonstration data

<details>
<summary>Answer</summary>

**Correct: C**

Because VLA foundation models already encode broad vision-language-action priors, adapting to a new task typically requires only a small number of task-specific demonstrations (few-shot fine-tuning).

**Why the others are wrong:**
- Training from scratch wastes the pretrained priors and requires far more data than necessary
- Some adaptation is almost always needed for a new task/environment
- Action generation requires demonstration or interaction data, not text alone

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** Which swarm robotics coordination mechanism allows robots to communicate indirectly by modifying a shared environment, similar to ants leaving pheromone trails?

A) Centralized broadcast messaging
B) Master-slave polling
C) Round-robin task scheduling
D) Stigmergy

<details>
<summary>Answer</summary>

**Correct: D**

Stigmergy is the classic swarm robotics principle where agents coordinate indirectly through environmental traces rather than direct communication.

**Why the others are wrong:**
- Centralized broadcast requires a central coordinator, which swarms avoid
- Master-slave polling implies a hierarchy, not decentralized indirect coordination
- Round-robin scheduling is a centralized task allocation technique, not environmental signaling

</details>

---

**Q8.** What primarily distinguishes a Vision-Language-Action (VLA) model from a standard Vision-Language Model (VLM)?

A) A VLA model only processes text input and ignores images
B) A VLA model adds an action output head/tokens that generate direct robot control commands
C) A VLA model cannot use transformer architectures
D) A VLA model is always smaller in parameter count than a VLM

<details>
<summary>Answer</summary>

**Correct: B**

VLA models extend VLMs by adding an action modality — outputting robot-executable commands (e.g., joint positions or end-effector poses) alongside vision-language understanding.

**Why the others are wrong:**
- VLA models process both vision and text, just like VLMs, plus action output
- VLA models are typically built on the same transformer backbones as VLMs
- Parameter count is unrelated to the vision-language-action distinction

</details>

---

