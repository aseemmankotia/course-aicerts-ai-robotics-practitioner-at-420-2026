# Answer Key — Practice Test 1

**Q1. Correct: B**

Perception is the stage where raw sensor data (camera images) is processed and interpreted into structured information the robot can use, such as object dimensions and position.

---

**Q2. Correct: A**

LiDAR provides precise, long-range distance measurements and is widely used outdoors because it is far less affected by ambient light interference than infrared sensors and provides better accuracy than ultrasonic at longer ranges.

---

**Q3. Correct: D**

Differential drive kinematics equations convert wheel angular velocities into robot linear and angular velocity using the wheel radius (to convert rotational to linear speed) and the wheelbase (to compute rotation from the speed difference between wheels).

---

**Q4. Correct: A**

The foundational distinction tested on AT-420 is that classical robotics follows fixed, explicitly programmed logic for every scenario, whereas AI integration lets the robot learn patterns, adapt to novel situations, and improve performance from data rather than requiring every case to be hand-coded.

---

**Q5. Correct: B**

Closed-loop feedback control continuously compares actual joint position against the target and adjusts actuator output in real time, correcting overshoot caused by momentum.

---

**Q6. Correct: B**

Level 3 (conditional automation) means the system independently handles most driving/operational tasks within its design domain but explicitly hands control back to a human when it encounters situations outside that domain - exactly matching the scenario's unmapped-area handoff.

---

**Q7. Correct: B**

Deliberative agents reason over an internal representation of the world state and search/plan a sequence of actions to achieve a goal before executing, in contrast to agents that react immediately to stimuli.

---

**Q8. Correct: C**

Loop closure detects that the robot has returned to a previously mapped location and uses that recognition to correct the accumulated odometry/pose drift, producing a globally consistent map and trajectory.

---

**Q9. Correct: C**

ROS 2 actions are purpose-built for long-running, preemptible tasks. They provide a goal request, continuous feedback messages during execution, a final result, and a built-in cancel mechanism — matching all three requirements.

---

**Q10. Correct: A**

Isaac Sim, built on NVIDIA Omniverse, is designed for photorealistic rendering, physically-based sensor simulation (cameras, LiDAR), and GPU-accelerated synthetic data generation at scale for training perception models.

---

**Q11. Correct: D**

Reliable QoS guarantees message delivery with retries, and Transient Local durability caches the last published message(s) so late-joining subscribers receive it — together satisfying both the delivery guarantee and late-join requirement.

---

**Q12. Correct: B**

ROS 1 depends on a single point-of-failure roscore master for node discovery using its own TCPROS/UDPROS transports, whereas ROS 2 adopts the DDS (Data Distribution Service) standard, enabling decentralized peer discovery, better real-time support, and improved reliability without a central master.

---

**Q13. Correct: D**

Single-stage CNN detectors are specifically designed for real-time multi-class object detection and localization, balancing accuracy and low-latency inference suitable for embedded GPUs.

---

**Q14. Correct: B**

Intermediate (feature-level) fusion allows the network to learn how to weight and combine complementary strengths of each modality dynamically, improving robustness when one sensor degrades (e.g., camera in low light), which is the core goal of sensor fusion in robotic perception.

---

**Q15. Correct: A**

Point-based architectures like PointNet are specifically designed to consume unordered, variable-length 3D point clouds directly, using permutation-invariant operations, which is the standard approach for processing raw LiDAR data without grid conversion.

---

**Q16. Correct: A**

End-to-end learning collapses perception, planning, and control into a single trained network mapping raw sensor data to actions, contrasting with modular pipelines that rely on explicitly engineered intermediate representations and separate stages.

---

**Q17. Correct: A**

Sparse terminal rewards make credit assignment nearly impossible over long horizons. Reward shaping introduces dense intermediate signals (e.g., progress toward grasp, correct alignment) so the agent gets feedback throughout the episode, which is the standard fix for sparse-reward robotic manipulation tasks.

---

**Q18. Correct: D**

Domain randomization trains the policy across a wide distribution of physical parameters (friction, sensor noise, actuator delay) so it learns robust behavior that generalizes to the unmodeled real-world dynamics, which is the standard sim-to-real transfer technique tested on the exam.

---

**Q19. Correct: D**

When kinematics are fully known and the environment is static and well-modeled, classical control (inverse kinematics plus PID) delivers precise, deterministic, and verifiable behavior without the sample inefficiency or risk of RL exploration — this is exactly the scenario where classical control is preferred over RL.

---

**Q20. Correct: A**

Rewarding only forward displacement without penalizing instability or energy use lets the agent exploit the metric literally — falling forward maximizes the single reward term, which is a textbook case of reward hacking from poorly specified reward design.

---

**Q21. Correct: B**

Grounding LLM outputs in sensor data, scene memory, and world state is the standard technique to reduce hallucination and ensure the robot's generated plan maps to verifiable reality before action execution.

---

**Q22. Correct: A**

TTS synthesizes audio waveforms from text, forming the final output stage of the voice interaction pipeline after a response has been generated.

---

**Q23. Correct: D**

When confidence falls below the configured threshold, the correct safety practice is to trigger a clarification dialogue rather than act on an uncertain interpretation, preventing unintended or unsafe actions.

---

**Q24. Correct: B**

ASR is the transcription stage converting raw audio into text, while NLU operates on that text to identify the user's intent and relevant entities, feeding the dialogue manager.

---

**Q25. Correct: A**

Generative AI for robotic creativity involves synthesizing novel solutions (such as grasp trajectories) beyond fixed rule sets or libraries, with validation steps to ensure feasibility and safety before execution.

---

**Q26. Correct: D**

The dialogue state tracker (part of the dialogue manager) maintains conversational context and slot-filling state across turns, enabling the system to resolve references like "same as last time" correctly.

---

**Q27. Correct: A**

Language grounding/semantic parsing bridges free-form NLP output with the robot's symbolic action and perception interfaces, resolving references like 'the box near the broken shelf' into actionable targets and task sequences.

---

**Q28. Correct: C**

Dialogue state tracking maintains context and references across conversation turns, which is essential for resolving anaphora like 'it' and sustaining coherent multi-turn human-robot interaction.

---

**Q29. Correct: D**

AMRs use onboard sensors (LiDAR/cameras) and SLAM-based mapping to build and update an understanding of their environment in real time, allowing them to re-route around people and obstacles and reach changing destinations without reprogrammed tracks — exactly what a dynamic, human-populated, reconfigurable warehouse requires.

---

**Q30. Correct: D**

This is a purely digital, rule-based, high-repetition data-entry task across legacy systems without APIs — the classic 'swivel-chair' use case that software RPA (the 'digital robot') is built for, replicating human UI interactions without any physical embodiment.

---

**Q31. Correct: A**

The curriculum frames RPA software bots as the 'digital robot' counterpart to physical robots: both follow a sense-think-act loop, but physical robots use sensors/actuators to perceive and manipulate the physical environment, while RPA bots perceive and manipulate software (screens, APIs, data fields) with no physical body.

---

**Q32. Correct: C**

RPA excels at automating repetitive, high-volume, rule-based processes operating on structured or semi-structured digital data with predictable, low exception paths — bots follow deterministic logic and struggle with ambiguity or frequent change.

---

**Q33. Correct: C**

Fixed-base industrial robotic arms are purpose-built for exactly this scenario: high-speed, high-precision, highly repetitive manipulation tasks at a stationary point on an assembly line, such as welding, as covered in the industrial robotics use-case material.

---

**Q34. Correct: C**

This is a healthcare service robotics use-case requiring autonomous navigation through dynamic, unmapped, human-occupied spaces — the defining capability of an AMR, which combines mobility, obstacle avoidance, and a task-specific payload (UV-C module) as covered under service robotics applications.

---

**Q35. Correct: B**

Software RPA is the 'digital robot' counterpart to physical robotics — it automates structured, rules-based digital tasks like UI navigation and API calls across systems, exactly fitting a data reconciliation workflow with no physical component.

---

**Q36. Correct: B**

AMRs use SLAM (Simultaneous Localization and Mapping) and onboard sensors to build and update maps in real time, letting them dynamically reroute around obstacles and adapt to layout changes without any fixed infrastructure.

---

**Q37. Correct: B**

VLA models are trained end-to-end on vision, language, and action data so they can map natural-language instructions and visual context directly to low-level robot actions, which is the emerging approach for generalist robot control.

---

**Q38. Correct: C**

Swarm robotics relies on decentralized, locally-interacting agents following simple rules to produce robust, scalable collective behavior without a central controller, exactly matching the described system.

---

**Q39. Correct: D**

Physical AI describes the convergence of AI and robotics where models are embodied in physical systems (robots, autonomous vehicles) that must perceive, reason, and act in the real world, as opposed to purely digital/virtual AI.

---

**Q40. Correct: B**

The emerging trend toward humanoid robots is driven by their general-purpose form factor that lets them operate in spaces and with tools built for humans, contrasting with industrial arms built for high-precision, repetitive tasks in controlled, structured environments.

---

**Q41. Correct: A**

VLA models are trained on large datasets combining camera observations, language instructions, and the action sequences a robot executed, so the model learns to jointly map perception and language to motor output.

---

**Q42. Correct: C**

Cross-embodiment generalist foundation models (e.g., RT-X style models) are pretrained on diverse multi-robot datasets, enabling transfer and rapid few-shot fine-tuning to new robots and tasks, which is a major current trend in robotics AI.

---

**Q43. Correct: C**

Vision-Language-Action models are a key emerging trend in robotics foundation models, trained to jointly process visual input and natural language instructions and output robot action sequences end-to-end, enabling generalist manipulation without separate perception/planning modules.

---

**Q44. Correct: D**

Safety-rated redundant perception, guaranteed stopping distance, and defined human oversight/exception handling are core requirements of physical safety design for autonomous systems operating near humans, directly addressing the failure mode observed.

---

**Q45. Correct: C**

Responsible robotics policy emphasizes distributed, traceable accountability across the full deployment chain (designer, integrator, deployer, operator) with documented oversight boundaries, rather than pinning liability on a single party or autonomy level.

---

**Q46. Correct: C**

Responsible deployment requires halting harmful biased behavior, retraining on representative data, and validating fairness across groups before returning the system to service, directly addressing the root cause of disparate outcomes.

---

