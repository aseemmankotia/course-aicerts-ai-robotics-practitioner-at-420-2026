# Answer Key — Practice Test 2

**Q1. Correct: C**

Sensor fusion via an EKF (or similar Bayesian filter) is the standard foundations technique for combining complementary sensors; adjusting the covariance (uncertainty) assigned to a sensor in real time lets the filter automatically trust the IMU/odometry more when LiDAR is unreliable, without discarding any sensor entirely.

---

**Q2. Correct: D**

AT-420 foundations frame AI's most mature and widespread impact as being in perception (object/pose recognition, segmentation) feeding into planning and control stacks that still largely use classical, well-understood algorithms like A*/RRT for planning and PID for low-level control.

---

**Q3. Correct: D**

Inverse kinematics takes a desired end-effector pose and solves for the joint angles that achieve it — exactly the requirement described, and a foundational concept distinguishing it from forward kinematics.

---

**Q4. Correct: A**

SEAs intentionally introduce a spring element that allows force to be inferred and controlled via deflection, providing inherent mechanical compliance and safety — the standard foundations answer for human-safe, force-sensitive actuation.

---

**Q5. Correct: C**

This is the canonical foundations example of layering AI perception (pose estimation) onto a classical actuation/control system, enabling the planner to adapt grasp targets dynamically instead of relying on static, pre-programmed coordinates — directly solving the 'random orientation' problem.

---

**Q6. Correct: A**

The robot independently performs perception, navigation, and replanning (higher-order autonomous functions) but a human retains override authority for a specific critical action (room entry), which is the textbook definition of conditional/supervised autonomy — the robot operates autonomously within defined bounds but escalates specific decisions to a human.

---

**Q7. Correct: A**

A utility-based agent evaluates multiple possible actions using a utility function that quantifies and trades off competing objectives (success probability, speed, risk) and selects the action maximizing that function — exactly what the weighted scoring and selection process describes.

---

**Q8. Correct: A**

Particle filter-based SLAM (FastSLAM) represents the robot's pose and map using a set of weighted particles, which can model multi-modal, non-Gaussian distributions and handle nonlinear dynamics and noisy, ambiguous data far better than linearized approaches — making it the standard answer for dynamic environments with uncertain, non-Gaussian noise.

---

**Q9. Correct: B**

ROS 2 uses DDS for discovery and transport, and DDS enforces QoS compatibility rules at connection time. A subscriber requesting 'reliable' delivery demands a stronger guarantee than a 'best effort' publisher offers, so DDS refuses to match them and no data flows, even though both endpoints appear in discovery.

---

**Q10. Correct: D**

Isaac Sim is built on NVIDIA Omniverse and provides RTX-based photorealistic rendering, GPU-accelerated PhysX simulation, synthetic sensor data generation, and native support for massively parallel environment instancing — the exact combination needed for large-scale RL training with realistic sensors.

---

**Q11. Correct: A**

In ROS 2, all node-specific CLI arguments must follow --ros-args, and topic remapping uses the -r (or --remap) flag with the syntax old_name:=new_name. The correct full form is `ros2 run my_pkg my_node --ros-args -r input:=/camera/image_raw`.

---

**Q12. Correct: C**

ROS 2 was redesigned around DDS (Data Distribution Service) middleware, removing the single point of failure represented by ROS 1's roscore master process. Nodes in ROS 2 discover and communicate with each other directly through the DDS layer.

---

**Q13. Correct: D**

Late fusion keeps sensor-specific models independent, so a confidence-weighted combiner can automatically down-weight a degraded camera stream while still trusting LIDAR, producing graceful degradation instead of a single corrupted joint representation.

---

**Q14. Correct: C**

Combining a CNN for spatial feature extraction with a temporal model (LSTM/GRU) lets the network learn motion patterns across frames, enabling trajectory prediction rather than only per-frame detection.

---

**Q15. Correct: C**

NMS suppresses a box as a duplicate only when its IoU with a higher-confidence box exceeds the threshold. At 0.9, only near-perfect overlaps get merged, so moderately overlapping duplicates survive. Lowering to a standard value like 0.45 suppresses more true duplicates while still being low enough to preserve two objects whose boxes only partially overlap.

---

**Q16. Correct: A**

Modular pipelines expose each stage separately, so each can be tested, validated, and safety-certified independently — at the cost of compounding errors passed from perception to planning to control. End-to-end policies learn a single mapping optimized jointly for the task, which can outperform modular designs in narrow settings but produces an opaque policy that is difficult to interpret, debug, or certify for safety.

---

**Q17. Correct: B**

The root cause is a misspecified proxy reward that can be maximized without task success. Redesigning the reward around actual task-relevant events (contact, grasp, lift) removes the exploitable shortcut while still providing learning signal — the standard fix for reward hacking in robotic manipulation.

---

**Q18. Correct: C**

Domain randomization forces the policy to become robust across a distribution of plausible dynamics parameters rather than overfitting to one simulator's exact (and incorrect) values, which is the standard exam-tested technique for sim-to-real transfer in locomotion.

---

**Q19. Correct: C**

Soft Actor-Critic is off-policy and entropy-regularized, reusing a replay buffer across updates, giving far higher sample efficiency than on-policy methods — critical when real-world interaction budget is strictly limited, a core exam distinction between on-policy and off-policy RL for robots.

---

**Q20. Correct: C**

AT-420 emphasizes that classical control (PID/MPC) is preferred when the system is well-modeled, dynamics are known and near-linear, and the task is simple regulation; RL is reserved for complex, hard-to-model, or contact-rich problems where accurate models aren't available. Using classical control here is more reliable, interpretable, and far less costly than training a policy.

---

**Q21. Correct: A**

Grounding LLM outputs to the robot's real action space is the standard solution to the symbol-grounding problem in LLM-driven robot instruction; a feasibility/affordance check filters out hallucinated or physically impossible actions before they reach the actuators.

---

**Q22. Correct: D**

ASR is the component dedicated to transcribing spoken audio into text, which is the first stage of the voice-command pipeline before NLU/LLM processing.

---

**Q23. Correct: B**

Raising the confidence threshold makes the detector require stronger evidence that the exact wake word was spoken, directly reducing false positives (false activations) at the cost of possibly missing some true activations — the correct trade-off for a noisy environment.

---

**Q24. Correct: D**

Intent recognition classifies the high-level action the user wants performed, while slot filling extracts the entity values (object='blue cup', source='kitchen', destination='office') needed to parameterize that action — a standard NLU decomposition used in robot command parsing.

---

**Q25. Correct: C**

Generative models such as diffusion models trained on demonstration/motion data can produce novel, physically plausible trajectories conditioned on new object geometries — this is the core use of generative AI for robotic creativity/manipulation beyond hard-coded libraries.

---

**Q26. Correct: B**

The dialogue state tracker (context/conversation manager) maintains conversational memory across turns, enabling coreference resolution such as mapping 'it' back to the previously mentioned 'red block' so the LLM/NLU can generate the correct grounded action.

---

**Q27. Correct: A**

Grounding LLM outputs via a constrained function-calling/action-schema interface forces the model to only select from the robot's verified capability set, directly eliminating the possibility of hallucinated actions outside that set.

---

**Q28. Correct: D**

When a referring expression is ambiguous and no contextual signal resolves it, standard conversational HRI design calls for a clarification turn so the robot confirms user intent before acting, avoiding incorrect or unsafe execution.

---

**Q29. Correct: B**

AMRs use onboard sensors (LiDAR/cameras) and SLAM to dynamically map and navigate without fixed infrastructure, adapting to weekly layout changes and safely routing around humans.

---

**Q30. Correct: A**

Master-slave teleoperated surgical robots scale the surgeon's hand motion and filter tremor to achieve sub-millimeter precision, which is the defining characteristic of surgical robotics in the healthcare use-case domain.

---

**Q31. Correct: C**

Best-practice RPA exception handling distinguishes business exceptions (bad data) from system exceptions, routing problematic items to a human-in-the-loop queue while continuing to process remaining items, maximizing throughput and auditability.

---

**Q32. Correct: B**

Power and Force Limiting (PFL) under ISO/TS 15066 caps contact force and pressure thresholds, allowing the cobot to operate in direct physical contact with humans without a fence, matching the fenceless handoff scenario described.

---

**Q33. Correct: B**

Software RPA excels at UI-level, rule-based data entry and reconciliation across systems lacking APIs, using screen scraping and UI automation, exactly matching the described 'digital robot' use-case.

---

**Q34. Correct: B**

The core conceptual distinction is domain of operation: RPA bots act on digital data and interfaces (the 'digital robot' counterpart), while physical robots act on the physical world using actuators and end-effectors.

---

**Q35. Correct: B**

The reconciliation task is scheduled, rule-based, and screen-based with no need for a human to trigger it each time, which is the textbook case for unattended RPA. The tray transport task requires physical movement through hospital corridors, which is squarely an AMR use-case, not something software RPA can perform since RPA only manipulates digital interfaces.

---

**Q36. Correct: D**

The bottleneck is a fleet-level coordination problem, not a per-robot sensing or speed problem: multiple independently-navigating robots are contending for the same shared intersections. A centralized fleet management system with traffic control arbitrates right-of-way and reroutes robots to prevent contention, which is the standard solution for scaling AMR deployments beyond single-robot navigation.

---

**Q37. Correct: D**

VLA (Vision-Language-Action) models are a key emerging trend covered in AT-420: they are foundation models trained to map visual observations and language instructions directly to robot actions, collapsing the traditional perception-plan-control pipeline into one learned policy.

---

**Q38. Correct: A**

Stigmergy is the term for decentralized coordination where agents modify the environment and other agents react to those changes, enabling emergent swarm behavior without direct communication or a central controller — a core swarm robotics concept on the exam.

---

**Q39. Correct: B**

Physical AI refers to the emerging paradigm where AI is embodied in robots/machines that perceive, reason, and act in the physical world, grounding intelligence through real-world interaction rather than purely digital or simulated reasoning.

---

**Q40. Correct: D**

Robot foundation models (generalist policies) trained via large-scale imitation/multi-task learning across diverse robots and environments are an emerging trend enabling zero-shot or few-shot generalization to unseen tasks — exactly the scenario described.

---

**Q41. Correct: C**

A major driver behind the humanoid trend is that human-centric infrastructure (stairs, doors, tools, shelves, vehicles) is already built for the human body, so humanoid robots can be deployed into existing environments without costly facility redesign.

---

**Q42. Correct: D**

Swarm robotics achieves scalability by using decentralized control where each robot acts on local sensing and limited local communication with nearby neighbors, so adding more robots does not increase per-robot computational or communication complexity.

---

**Q43. Correct: B**

VLA foundation models are trained end-to-end on large multimodal datasets pairing vision, language, and action trajectories, allowing them to directly ground open-vocabulary language and visual input into continuous action outputs (e.g., end-effector poses or joint commands) without requiring engineers to hand-build separate perception, planning, and control modules for each task — this is the core innovation distinguishing VLA models as a 2025-2026 emerging trend in physical AI and humanoid robotics.

---

**Q44. Correct: B**

Responsible deployment of autonomous physical systems requires documented human oversight, traceable audit trails, and staged validation before pushing updates to safety-critical, patient-facing systems — this directly addresses both the root cause (uncontrolled update) and accountability (shared sign-off and auditability).

---

**Q45. Correct: A**

ISO 10218 (Parts 1 and 2) establishes baseline safety requirements for industrial robots and robot systems, while ISO/TS 15066 is a technical specification that supplements it with collaborative-robot-specific guidance, including the four recognized collaborative modes and force/pressure limits for human contact.

---

**Q46. Correct: A**

IEC 60204-1 defines Category 0 as an uncontrolled stop by immediate removal of actuator power — the only category matching a requirement of zero controlled deceleration, making it the correct choice for the most severe, immediate-hazard E-stop response.

---

