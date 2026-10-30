# Practice Test 2: AI+ Robotics Practitioner (AT-420): Exam-Focused Prep

- **Questions:** 46
- **Time limit:** 90 minutes
- **Passing score:** 70%%

> Answers are in `answer-key-2.md`. Track results in `score-tracker.md`.

---

**Q1.** A warehouse AGV uses an IMU, wheel encoders, and LiDAR for localization, but reflective shelving causes erratic, high-variance LiDAR returns that corrupt pose estimates. Which approach BEST maintains accurate localization while mitigating the sensor issue?

A) Replace LiDAR entirely with a single high-resolution RGB camera and rely only on visual odometry
B) Increase the LiDAR scan rate so more samples are collected per second to average out the noise
C) Fuse IMU, wheel odometry, and LiDAR in an Extended Kalman Filter, dynamically increasing the LiDAR measurement covariance so unreliable readings are down-weighted
D) Disable wheel encoders since wheel slippage is a known error source, and rely solely on raw LiDAR scans

---

**Q2.** In the classical perception-plan-act robotics loop, which statement most accurately reflects where modern AI (deep learning) has had the greatest architectural impact, as framed in AT-420 foundations?

A) AI primarily replaces the 'act' stage, with neural networks directly commanding actuator torques in nearly all deployed robots
B) AI has fully replaced classical path planning with reinforcement learning across essentially all commercial robotic systems
C) AI eliminates the need for a distinct perception stage by mapping raw actuator feedback directly to high-level plans
D) AI primarily enhances the 'perception' stage (e.g., CNN-based object detection and semantic segmentation), while the 'plan' and 'act' stages still commonly rely on classical algorithms such as A* and PID control

---

**Q3.** You must configure a 6-DOF robotic arm's controller so that, given a desired end-effector position and orientation in the workspace, the system outputs the joint angles required to reach that pose. Which kinematic computation should the controller be configured to perform?

A) Forward kinematics
B) Jacobian transpose computation alone, without a full kinematic solve
C) Differential kinematics using only joint velocity feedback
D) Inverse kinematics

---

**Q4.** A robotics engineer is selecting an actuator for a lightweight prosthetic hand that must safely apply compliant, force-limited interaction with human skin and soft objects. Which actuator choice BEST satisfies this requirement?

A) A series elastic actuator (SEA), which incorporates an elastic element between the motor and load to enable compliant, force-controllable interaction
B) A hydraulic actuator, chosen for its high force output
C) A direct-drive DC motor with no mechanical compliance element
D) An open-loop stepper motor valued for precise positional repeatability

---

**Q5.** A legacy industrial arm performs pick-and-place using fixed, pre-programmed waypoints with no sensing. Management wants it to handle randomly oriented parts arriving on a conveyor without reprogramming waypoints for every new orientation. Which upgrade BEST reflects the AI-versus-classical-robotics integration pattern taught in AT-420 foundations?

A) Expand the set of hardcoded waypoints to cover additional known orientations
B) Upgrade the PLC controller to a faster model to reduce the overall pick-and-place cycle time
C) Add a vision-based perception module with 6D pose estimation that feeds a dynamic motion planner, recalculating grasp points for each part in real time
D) Add additional encoders to the conveyor motor to more precisely track belt speed

---

**Q6.** An autonomous mobile robot (AMR) in a hospital delivers medication and can navigate, avoid obstacles, and replan routes without any human input, but a remote operator must still approve the robot before it enters a patient's room for the final drop-off. According to the standard autonomy-level framework tested on AT-420, this robot operates at which level?

A) Conditional autonomy — the robot handles routine operation but defers to a human for specific high-stakes decisions
B) Full autonomy — the robot requires no human involvement at any stage
C) Assisted autonomy — a human actively drives navigation while the robot only assists with obstacle detection
D) No autonomy — all movement decisions are scripted paths with zero onboard decision-making

---

**Q7.** A warehouse picking robot must choose among several candidate grasp poses for an object. Each pose is scored using a function that weighs grasp success probability, time to execute, and risk of dropping the item, and the robot selects the pose with the highest combined score. Which type of intelligent agent architecture does this robot implement?

A) Utility-based agent
B) Simple reflex agent
C) Goal-based agent
D) Model-based reflex agent

---

**Q8.** A ground robot operating in a large, dynamic warehouse with constantly moving obstacles and sensor noise needs a SLAM approach that can represent multiple hypotheses about its pose and the map simultaneously, without assuming Gaussian noise. Which SLAM technique BEST fits this requirement?

A) Particle filter-based SLAM (e.g., FastSLAM)
B) Extended Kalman Filter SLAM (EKF-SLAM)
C) Occupancy grid mapping with a fixed global reference frame
D) Pure visual odometry without loop closure

---

**Q9.** A robotics team deploys two ROS 2 nodes on the same network: a camera driver publishing /image_raw with QoS reliability set to 'best effort', and a perception node subscribing to /image_raw with QoS reliability set to 'reliable'. The subscriber never receives any messages, though `ros2 topic list` shows both nodes are discovered correctly. What is the root cause?

A) The publisher and subscriber must be launched from the same terminal session for QoS negotiation to succeed
B) DDS QoS policies are incompatible: a 'reliable' subscriber cannot connect to a 'best effort' publisher because the publisher's guarantee is weaker than what the subscriber requires
C) ROS 2 requires a running roscore master to broker the QoS negotiation between publisher and subscriber
D) The topic must be remapped into a namespace before QoS policies are applied to the connection

---

**Q10.** A team is training a reinforcement learning policy for a warehouse mobile robot. They need photorealistic RGB and LiDAR sensor simulation, GPU-accelerated physics, and the ability to run thousands of parallel environment instances for policy training. Which tool is the BEST fit for this requirement?

A) rqt_graph
B) RViz2
C) Gazebo Classic
D) NVIDIA Isaac Sim

---

**Q11.** Which command correctly remaps the input topic 'input' to '/camera/image_raw' when launching a ROS 2 node from the command line?

A) ros2 run my_pkg my_node --ros-args -r input:=/camera/image_raw
B) ros2 run my_pkg my_node --remap /input /camera/image_raw
C) ros2 run my_pkg my_node --ros-args --param input:=/camera/image_raw
D) ros2 launch my_pkg my_node.launch.py --topic input=/camera/image_raw

---

**Q12.** Which statement correctly describes a core architectural difference between ROS 1 and ROS 2?

A) ROS 1 uses DDS for decentralized communication, while ROS 2 relies on a centralized master node for topic discovery
B) ROS 1 natively supports real-time control, while ROS 2 cannot support real-time systems due to its middleware design
C) ROS 2 eliminates the centralized ROS master and uses a DDS-based middleware for decentralized node discovery and communication
D) ROS 2 client libraries are written exclusively in Python, while ROS 1 client libraries are written exclusively in C++

---

**Q13.** A mobile warehouse robot combines a monocular camera and a 3D LIDAR for obstacle detection. During a dusty, low-light shift, the camera feed becomes unreliable while LIDAR performance stays stable. The perception team wants a fusion architecture that degrades gracefully when one sensor's input quality drops, rather than corrupting the entire perception output. Which sensor fusion strategy BEST meets this requirement?

A) Early fusion — concatenate raw camera pixels and LIDAR point cloud into a single tensor before one CNN processes both
B) Switch to LIDAR-only perception permanently, since LIDAR is unaffected by lighting conditions
C) Add an infrared illuminator to the camera and keep the existing early-fusion pipeline unchanged
D) Late fusion — process camera and LIDAR independently with separate models, then combine outputs using confidence-weighted voting

---

**Q14.** A warehouse robot must track moving forklifts across consecutive camera frames and predict their short-term trajectory to avoid collisions, not just detect their current position in a single frame. Which neural architecture BEST meets this requirement?

A) A single-frame YOLO-style object detector run independently on each incoming frame
B) A classical Kalman filter operating purely on odometry data, without any vision input
C) A CNN feature extractor feeding a temporal model (e.g., LSTM/GRU) that processes sequences of frame-level features to predict motion and future position
D) A convolutional autoencoder trained to flag visually anomalous frames in the video stream

---

**Q15.** A robot's object detection pipeline uses YOLO-style non-max suppression (NMS) with the IoU threshold set to 0.9. The perception team observes multiple overlapping bounding boxes reported for the same physical object, causing the grasp planner to attempt duplicate grasps. Which configuration change BEST resolves this while still correctly separating two genuinely adjacent, distinct objects?

A) Raise the IoU threshold further, to 0.99, to make suppression stricter
B) Disable NMS entirely and rely only on the confidence score threshold to filter boxes
C) Lower the IoU threshold to a more typical value, around 0.45, so more overlapping boxes are merged while distinct nearby objects remain separate
D) Raise the confidence score threshold to 0.99 while leaving the IoU threshold unchanged

---

**Q16.** Which statement BEST characterizes the trade-off between end-to-end deep reinforcement learning control policies and modular perception-planning-control pipelines for robotic manipulation, as emphasized in AT-420 neural control concepts?

A) Modular pipelines allow independent validation and certification of each stage (perception, planning, control), but errors can accumulate across stage boundaries; end-to-end policies optimize jointly for the task but are harder to interpret and certify
B) End-to-end policies offer better interpretability and easier debugging of individual failure causes than modular pipelines
C) End-to-end policies typically require less training data and generalize better to unseen tasks than modular pipelines
D) Modular pipelines are considered deprecated in modern robotics and are no longer used in production systems

---

**Q17.** A team trains a robotic arm to stack blocks using a dense reward based solely on reducing the gripper-to-block distance. After training, the arm hovers millimeters from the block indefinitely, maximizing reward without ever grasping or lifting it. Which approach BEST resolves this reward hacking behavior?

A) Switch from PPO to DQN, since DQN is not susceptible to reward hacking
B) Replace the proxy distance reward with a sparse task-completion reward plus shaping terms tied to genuine progress events, such as stable contact and successful lift
C) Increase the learning rate to force faster convergence past the exploit
D) Increase the episode time horizon so the arm has more time to complete the task

---

**Q18.** A quadruped robot policy trained in a single fixed-parameter physics simulator walks flawlessly in simulation but collapses within seconds on the physical robot, due to unmodeled friction, actuator latency, and mass-distribution discrepancies. Which approach BEST closes this sim-to-real gap?

A) Reduce the simulation timestep to improve numerical integration precision
B) Continue training in the same simulator for 10x more timesteps
C) Apply domain randomization during training by sampling friction coefficients, actuator delays, and link masses across ranges representative of real-world variation
D) Skip simulation entirely and train the policy from scratch using real-world trial and error

---

**Q19.** An engineering team must learn a continuous-control manipulation policy directly on a physical robotic arm, limited to 50,000 real-world interaction steps due to hardware wear concerns. Which approach is BEST suited to this sample budget?

A) On-policy PPO using batch updates of one million fresh steps each
B) Monte Carlo policy gradient (REINFORCE) without a value baseline
C) An off-policy, sample-efficient algorithm such as SAC combined with replay buffer reuse of past experience
D) Tabular Q-learning over a discretized version of the continuous action space

---

**Q20.** A mobile robot must maintain a fixed distance from a wall while moving at constant velocity in a static, well-characterized environment where the dynamics model is known accurately. Per AT-420 guidance on where RL fits relative to classical control, which approach is MOST appropriate?

A) A deep RL policy trained from scratch with a dense reward for wall-distance error
B) A model-free RL policy trained via unguided random exploration directly on hardware
C) A classical PID controller tuned to the known dynamics model
D) An RL policy trained with a sparse reward given only upon reaching a destination waypoint

---

**Q21.** A warehouse robot uses an LLM-based planner to convert natural-language commands like 'organize the top shelf' into a sequence of executable actions. The planner occasionally generates plans that sound reasonable but are physically impossible for the robot to perform, such as picking up an entire shelf unit. Which approach BEST resolves this failure mode?

A) Add an affordance/feasibility validation layer that checks each proposed action against the robot's actual capabilities before execution
B) Increase the LLM's sampling temperature so it generates more varied action sequences
C) Replace the LLM with a larger foundation model trained on more general text
D) Require the robot to narrate the plan aloud via text-to-speech before starting

---

**Q22.** In a human-robot interaction pipeline, a user speaks a command, and before the natural language understanding (NLU) module or LLM can process it, the robot must first convert the raw audio waveform into text. Which component performs this conversion?

A) Natural Language Generation (NLG) engine
B) Dialogue state tracker
C) Text-to-Speech (TTS) synthesizer
D) Automatic Speech Recognition (ASR) engine

---

**Q23.** A service robot's wake-word detector is deployed on a noisy factory floor and is triggering far too often on background chatter and machinery sounds that are not the actual wake word. The team needs to reduce these false activations without disabling the wake-word feature. Which configuration change should they make?

A) Lower the detection confidence threshold so more audio events are accepted as the wake word
B) Increase the detection confidence threshold required before the wake word is accepted
C) Disable noise-cancellation preprocessing to capture more audio detail
D) Switch from wake-word activation to continuous always-on listening for every utterance

---

**Q24.** In the NLU pipeline that parses a spoken command such as 'bring the blue cup from the kitchen to the office,' which statement correctly distinguishes intent recognition from slot filling?

A) Intent recognition extracts the object color and location parameters; slot filling identifies the overall action category
B) Intent recognition and slot filling are two names for the same NLU step
C) Intent recognition only applies to text input; slot filling only applies to speech input
D) Intent recognition identifies the overall goal (e.g., 'fetch and deliver object'); slot filling extracts the specific parameters such as object, source, and destination

---

**Q25.** A robotics research team wants to generate novel, physically plausible grasping trajectories for objects the robot has never encountered, rather than relying on a fixed library of pre-programmed grasps. Which generative AI application for robotic creativity BEST fits this need?

A) A rule-based inverse kinematics solver that only replays stored trajectories
B) A static lookup table mapping object categories to the single closest matching stored grasp
C) A generative model (e.g., diffusion-based) trained on motion data that synthesizes new manipulation trajectories conditioned on object geometry
D) A text-to-speech model used to announce the robot's intended grasp verbally

---

**Q26.** During a multi-turn conversation, a user tells a robot 'pick up the red block,' and two turns later says 'now put it on the shelf.' The robot must correctly resolve 'it' to mean the red block mentioned earlier. Which HRI system component is primarily responsible for maintaining this cross-turn context?

A) The automatic speech recognition (ASR) engine
B) The dialogue state tracker / context manager
C) The text-to-speech (TTS) synthesizer
D) The low-level motor controller

---

**Q27.** A warehouse robot uses an LLM to translate natural-language commands into action calls. During testing, the robot occasionally attempts actions that are not part of its actual capability set (e.g., 'weld the panel' when it has no welding tool), causing execution failures. Which approach BEST prevents this type of LLM-driven action hallucination?

A) Constrain the LLM's output to a grounded action schema or function-calling interface limited strictly to the robot's actual capability set
B) Increase the LLM's sampling temperature so it generates more varied action mappings
C) Replace the LLM with a larger general-purpose model trained on more internet text
D) Add more few-shot examples of multistep tasks without changing the allowed action vocabulary

---

**Q28.** A conversational home-assistant robot receives the voice command 'pick up the cup,' but its vision system detects two cups on the table and no prior context disambiguates which one is meant. Following best practice for human-robot conversational interface design, what should the robot do?

A) Pick up the object that is physically closest to the robot's current gripper position
B) Pick up whichever cup the object-detection pipeline returns first in its output list
C) Pick up both cups sequentially so the task is completed regardless of which one was intended
D) Trigger a clarification dialogue turn, asking the user which specific cup is meant before executing the action

---

**Q29.** A third-party logistics company operates a 500,000 sq ft fulfillment center with dynamic rack layouts that are reconfigured weekly to match seasonal demand. The company needs a robotic material-handling solution that does not require fixed magnetic tape, floor markers, or wired guidance infrastructure, while still safely navigating around a mixed human-robot workforce. Which type of robot BEST meets these requirements?

A) Automated Guided Vehicle (AGV) following magnetic floor tape
B) Autonomous Mobile Robot (AMR) using SLAM-based navigation
C) Fixed robotic arm on a gantry rail system
D) Wire-guided AGV using embedded floor wiring

---

**Q30.** A hospital wants to deploy a robotic system to perform minimally invasive procedures with sub-millimeter precision under direct surgeon control, including motion scaling and tremor filtering. Which category of robotics use-case does this represent?

A) Surgical robotics using master-slave teleoperation
B) Rehabilitation exoskeleton
C) Telepresence service robot
D) Autonomous mobile delivery robot

---

**Q31.** An RPA developer is configuring an unattended bot in an orchestrator to process invoices from a shared mailbox. The bot occasionally encounters invoices in a corrupted PDF format that cause the OCR extraction step to fail. Per RPA best practice, how should the bot be configured to handle this scenario?

A) Configure the bot to skip OCR entirely and proceed to approval without extracted data
B) Configure the bot to terminate the entire orchestrator job immediately on any OCR failure
C) Implement a business exception handler that routes the failed invoice to a human review queue and continues processing the remaining items
D) Configure the bot to retry the entire workflow from the beginning indefinitely until it succeeds

---

**Q32.** A manufacturer wants to install a robotic arm on an assembly line where human workers share the same workspace without a safety fence, directly handing off parts to the robot. The integrator must select a collaborative operating mode compliant with ISO/TS 15066 that limits the force and pressure exerted by the robot on contact with a human. Which collaborative operation type is this?

A) Hand-guiding
B) Power and force limiting (PFL)
C) Safety-rated monitored stop
D) Speed and separation monitoring

---

**Q33.** A logistics company wants to automate reconciling shipment data between its legacy ERP system (no API available) and a modern web-based customs portal, involving repetitive data entry, screen scraping, and rule-based decision logic across both systems. Which automation approach is MOST appropriate?

A) A reinforcement learning agent trained via trial-and-error directly on the production ERP system
B) Software Robotic Process Automation (RPA) bot performing UI-level screen interaction
C) An autonomous mobile robot to physically transport paperwork between departments
D) A physical robotic arm programmed to type on keyboards

---

**Q34.** Which statement BEST describes the fundamental distinction between a software RPA bot and a physical industrial robot, as framed in the AT-420 curriculum's comparison of 'digital robots' and physical robots?

A) Physical robots cannot use AI, while software RPA bots are inherently AI-driven
B) Software RPA bots manipulate digital information within software interfaces, while physical robots manipulate physical objects in the real world via actuators and end-effectors
C) Software RPA bots require ISO/TS 15066 safety certification, while physical robots do not
D) Software RPA bots are always more expensive to deploy than physical robots

---

**Q35.** A hospital pilots automation for two tasks: (1) reconciling medication orders by pulling data from three separate EHR screens on a scheduled nightly batch, a fully rule-based task with no exceptions requiring judgment, and (2) physically moving medication trays from the pharmacy to nursing stations on fixed routes. Which technology pairing BEST matches each task?

A) Attended RPA bot triggered manually each night for reconciliation; human couriers for tray transport
B) Unattended RPA bot for reconciliation; an Autonomous Mobile Robot (AMR) for tray transport
C) Industrial robotic arm for reconciliation; unattended RPA bot for tray transport
D) A single AMR with an embedded RPA software agent handling both reconciliation and tray transport

---

**Q36.** A warehouse operates 50 AMRs for order picking. Each AMR already uses LiDAR-based obstacle avoidance and navigates individually without colliding. During peak season, robots increasingly stall and queue at narrow aisle intersections, significantly slowing overall throughput even though no collisions occur. Which solution directly addresses this problem?

A) Replace all AMRs with AGVs that follow fixed magnetic tape paths
B) Upgrade each AMR's individual LiDAR sensors to a longer detection range
C) Increase the maximum travel speed setting on each AMR to reduce aisle occupancy time
D) Implement a centralized fleet management system with traffic control to coordinate intersection priority and routing across all AMRs

---

**Q37.** A robotics team wants a single end-to-end model that takes raw camera frames plus a natural-language instruction like 'pick up the red cup and place it on the shelf' and directly outputs low-level robot joint/actuator commands, without hand-engineered separate perception, planning, and control modules. Which emerging approach BEST fits this requirement?

A) A classical PID control loop tuned per joint
B) A rule-based finite state machine for each task
C) A SLAM-based navigation stack
D) A Vision-Language-Action (VLA) foundation model

---

**Q38.** In a swarm robotics deployment, individual robots coordinate by leaving and sensing markers (e.g., simulated pheromone trails) in the shared environment rather than communicating directly with each other or a central controller. What is this indirect, environment-mediated coordination mechanism called?

A) Stigmergy
B) Centralized task allocation
C) Teleoperation relay
D) Waypoint following

---

**Q39.** In the context of emerging robotics trends, which description BEST defines 'Physical AI'?

A) AI software deployed only on on-premises physical servers rather than the cloud
B) AI systems that learn and reason by perceiving and acting within the physical world through embodied interaction
C) A synonym for robotic process automation of digital office workflows
D) AI models trained exclusively in simulation with no real-world deployment

---

**Q40.** A research lab trains a single robot control policy on a massive, diverse dataset spanning many robot embodiments, environments, and tasks, then observes the policy can perform new manipulation tasks it was never explicitly trained on with little or no additional data. Which emerging robotics paradigm does this describe?

A) A single-task reinforcement learning agent trained from scratch per task
B) A hand-coded expert system with if-then task rules
C) A fixed finite state machine tuned to one robot arm
D) A generalist robot foundation model exhibiting cross-task/cross-embodiment generalization

---

**Q41.** A company is adopting the humanoid form factor for a warehouse robot instead of a custom wheeled or multi-arm design. Which reason is MOST commonly cited as the strategic driver for this design choice in emerging robotics trends?

A) Humanoids require significantly less onboard AI than wheeled robots
B) Humanoid regulations and safety certification are simpler than for other robot forms
C) The human form factor can operate in spaces and with tools/infrastructure already built for humans, avoiding environment retrofitting
D) Humanoid robots are consistently the cheapest robot platform to manufacture

---

**Q42.** A team wants to scale a swarm robotics system from 10 robots to 1,000 robots without redesigning the control algorithm or requiring full connectivity between every robot pair. Which control architecture property is essential to achieve this scalability?

A) A single leader robot broadcasting explicit commands to every follower
B) A centralized planner maintaining a full communication graph across all robots
C) A human teleoperator individually controlling each robot
D) Decentralized control relying only on local sensing and local neighbor communication

---

**Q43.** A robotics startup is building a humanoid assistant that must interpret open-ended natural language instructions such as 'pick up the red cup and place it on the shelf' and directly produce low-level end-effector actions, without engineers hand-coding a separate perception module, symbolic planner, and motion controller for every possible command. Which emerging robotics technology architecture BEST fits this requirement?

A) A classical SLAM-based navigation stack paired with a rule-based symbolic task planner
B) A Vision-Language-Action (VLA) foundation model trained end-to-end on large-scale multimodal robot demonstration data
C) A swarm robotics framework using decentralized consensus algorithms across multiple agents
D) A traditional RPA bot that uses screen-scraping and scripted macros to trigger pre-programmed robot routines

---

**Q44.** A hospital deploys a fleet of autonomous mobile robots (AMRs) for medication delivery. After a software update pushed by a third-party AI vendor, a robot misclassifies a pediatric patient as an obstacle and causes a minor collision. The hospital's risk team must decide how to adjust deployment practices. Which action BEST aligns with responsible AI/robotics deployment principles for accountability and human oversight?

A) Require the hospital to indemnify the vendor for all future incidents to simplify liability
B) Establish a documented human-in-the-loop override and incident audit trail requiring vendor sign-off before any future autonomous software updates are deployed to live patient-facing units
C) Disable the obstacle-detection system permanently since the update caused the problem, relying only on manual operation
D) Continue operations unchanged since the collision was minor and the vendor contractually accepted software liability

---

**Q45.** Which statement correctly distinguishes ISO 10218 from ISO/TS 15066 as tested in AT-420's robot safety standards coverage?

A) ISO 10218 specifies general safety requirements for industrial robots and robot systems, while ISO/TS 15066 provides supplementary technical guidance specifically for collaborative robot applications, including power and force limits and speed/separation monitoring
B) ISO 10218 defines power and force limiting thresholds for collaborative contact, while ISO/TS 15066 governs general industrial robot safety requirements
C) Both standards apply exclusively to software-based AI bias audits in robotics and are unrelated to physical safety
D) ISO 10218 and ISO/TS 15066 are identical in scope, with ISO/TS 15066 being a deprecated predecessor document

---

**Q46.** An engineer is configuring the emergency stop (E-stop) circuit for a collaborative robot arm per IEC 60204-1 stop categories. The design requirement states that in a hazard event, all power to the actuators must be removed immediately with no controlled deceleration phase. Which stop category satisfies this requirement?

A) Category 0 stop — an uncontrolled stop achieved by immediate removal of power to the machine actuators
B) Category 2 stop — a controlled stop with power retained to the drive system
C) Category 1 stop — a controlled stop where power is removed only after motion has ceased
D) Category 3 stop — a soft-stop initiated exclusively through a software watchdog timer

---

