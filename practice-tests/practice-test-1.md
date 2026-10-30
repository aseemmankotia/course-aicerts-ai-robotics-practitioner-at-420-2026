# Practice Test 1: AI+ Robotics Practitioner (AT-420): Exam-Focused Prep

- **Questions:** 46
- **Time limit:** 90 minutes
- **Passing score:** 70%%

> Answers are in `answer-key-1.md`. Track results in `score-tracker.md`.

---

**Q1.** A warehouse robot uses a camera mounted above its gripper to identify box dimensions before adjusting its grip strength. Which stage of the perception-plan-act loop is responsible for interpreting the raw camera data into usable information such as box edges and size?

A) Actuation
B) Perception
C) Planning
D) Motion control

---

**Q2.** An outdoor mobile robot must measure precise distances to obstacles across a 50-meter range while operating in direct sunlight. Which sensor type BEST meets this requirement?

A) LiDAR
B) Infrared proximity sensor
C) Ultrasonic sensor
D) Monocular RGB camera

---

**Q3.** To compute a differential drive mobile robot's linear and angular velocity from its left and right wheel speeds, which pair of parameters must be known in the kinematic model?

A) Motor torque and gear ratio
B) Battery voltage and current draw
C) Camera resolution and frame rate
D) Wheel radius and wheelbase (distance between wheels)

---

**Q4.** What is the primary difference between classical (non-AI) robotic control and AI-enabled robotic control?

A) Classical control relies on explicit pre-programmed rules, while AI control allows robots to learn and adapt behavior from data
B) Classical robots are always more expensive to build than AI-enabled robots
C) AI-enabled robots cannot use sensors, while classical robots require them
D) Classical robots use actuators while AI-enabled robots do not require actuators

---

**Q5.** A robotic arm receives a command to move a joint to a specific angle but repeatedly overshoots the target due to momentum before settling. Which element of robot control is responsible for correcting this during execution?

A) Open-loop actuation
B) Closed-loop feedback control
C) Perception
D) Path planning

---

**Q6.** A warehouse mobile robot autonomously navigates predefined aisles, avoids dynamic obstacles, and re-routes around blocked paths on its own. However, when it enters an unmapped area outside its operational design domain, it stops and requests a human operator to take control. Which autonomy level BEST describes this robot's behavior?

A) Level 2 - Partial automation (human must continuously supervise)
B) Level 3 - Conditional automation (system handles routine operation but requests human intervention for edge cases)
C) Level 4 - High automation (no human intervention required within its domain)
D) Level 1 - Operator assistance only (human performs the primary task)

---

**Q7.** In intelligent agent architecture design, what is the primary distinguishing characteristic of a deliberative (planning-based) agent compared to a purely reactive agent?

A) A deliberative agent maps sensor inputs directly to actions using fixed condition-action rules
B) A deliberative agent maintains an internal world model and generates a plan toward a goal before acting
C) A deliberative agent cannot be used in any real-time robotic application
D) A deliberative agent relies exclusively on a pre-trained reinforcement learning policy to select actions

---

**Q8.** A robot running a SLAM (Simultaneous Localization and Mapping) pipeline re-enters a corridor it mapped 20 minutes earlier. What is the specific purpose of the 'loop closure' step in this situation?

A) To filter LiDAR point cloud noise before the map is constructed
B) To synchronize timestamps across the robot's multiple sensor streams
C) To recognize the previously visited corridor and correct accumulated drift in the estimated trajectory and map
D) To compute the shortest path between the robot's current pose and a goal waypoint

---

**Q9.** A robotics engineer is implementing a pick-and-place routine on a robot arm using ROS 2. The task takes a variable amount of time to complete, the client needs periodic progress feedback while it runs, and the client must be able to cancel the task mid-execution. Which ROS 2 communication mechanism BEST fits this requirement?

A) A topic with publish-subscribe messaging
B) A service with synchronous request-response calls
C) An action with goal, feedback, and result messages
D) A parameter set on the node at startup

---

**Q10.** A team needs to generate large volumes of synthetic training data for robot perception, including photorealistic camera imagery and physically accurate LiDAR simulation, scaled across GPU clusters. Which simulation environment covered in the AT-420 curriculum is conceptually best suited for this?

A) NVIDIA Isaac Sim
B) Gazebo classic physics simulator
C) RViz visualization tool
D) rosbag data recording tool

---

**Q11.** A safety-critical emergency-stop command must be published over a ROS 2 topic such that delivery is guaranteed and any node that subscribes after the message was sent still receives the last published command. Which QoS policy combination should be configured on the publisher and subscriber?

A) Best Effort reliability with Volatile durability
B) Best Effort reliability with Transient Local durability
C) Reliable reliability with Volatile durability
D) Reliable reliability with Transient Local durability

---

**Q12.** What is the fundamental architectural difference in the communication middleware between ROS 1 and ROS 2?

A) ROS 1 uses DDS for decentralized discovery while ROS 2 uses a custom TCPROS master
B) ROS 1 relies on a central roscore master with custom TCPROS/UDPROS transport, while ROS 2 uses DDS for decentralized discovery and communication
C) Both ROS 1 and ROS 2 use an identical master-based architecture with no differences
D) ROS 2 eliminated network-based communication entirely in favor of local-only messaging

---

**Q13.** A mobile robot operating in a warehouse must identify and localize multiple obstacle types (pallets, forklifts, people) in real time from a single RGB camera feed, under a strict 30ms inference budget on an embedded GPU. Which approach BEST meets these requirements?

A) A classical Canny edge-detection pipeline followed by rule-based shape matching
B) A fully connected neural network trained on flattened raw pixel vectors
C) A recurrent neural network (RNN) that processes the image row-by-row as a sequence
D) A single-stage CNN-based object detector (e.g., YOLO-style architecture) trained on labeled warehouse images

---

**Q14.** A robot must fuse data from a camera and a LiDAR sensor to maintain reliable perception in both bright sunlight and low-light conditions. Which sensor fusion strategy BEST achieves robust, continuous perception across these varying conditions?

A) Use only the LiDAR sensor and disable the camera entirely in low light
B) Fuse camera and LiDAR features at an intermediate representation level, weighting each modality's contribution based on confidence
C) Concatenate raw camera pixels and raw LiDAR point coordinates into a single input vector without preprocessing
D) Alternate between camera-only and LiDAR-only perception depending on time of day, never combining the two

---

**Q15.** A robotics engineer needs to design a neural network that processes raw 3D LiDAR point cloud data directly, without first converting it into a 2D image or voxel grid. Which network architecture type is BEST suited for this configuration?

A) A point-based architecture (e.g., PointNet-style) designed to handle unordered, irregular point sets directly
B) A standard 2D convolutional neural network (CNN) applied directly to the (x, y, z) point list
C) A fully connected network with a fixed input size equal to the maximum possible number of points, zero-padded
D) A recurrent LSTM network that processes points in the order they were recorded by the sensor

---

**Q16.** In the context of neural control for robotic manipulators, what is the key distinction between an end-to-end deep learning control policy and a traditional modular perception-planning-control pipeline?

A) End-to-end policies map sensor input directly to actuator commands through a single trained network, whereas modular pipelines use separate, independently designed stages for perception, planning, and control
B) End-to-end policies require no training data at all, while modular pipelines must be trained on labeled datasets
C) Modular pipelines always execute faster than end-to-end policies regardless of hardware
D) End-to-end policies can only be used with wheeled robots, while modular pipelines work exclusively with robotic arms

---

**Q17.** A team is training a reinforcement learning policy for a robotic arm to perform a multi-step assembly task. The only reward signal is +1 when the assembly is fully completed and 0 otherwise. After 500,000 training steps, the agent has not learned any useful behavior. Which approach BEST addresses this problem?

A) Add dense intermediate rewards (reward shaping) for sub-goals like grasping and alignment
B) Increase the discount factor to 0.999 so future rewards propagate further back
C) Switch entirely to supervised learning using only labeled image data of the final assembled state
D) Reduce the action space to a single binary gripper open/close command

---

**Q18.** A legged robot policy trained entirely in a physics simulator performs well in simulation but fails immediately on the physical robot due to differences in friction, sensor noise, and actuator delay. Which technique BEST improves sim-to-real transfer for this scenario?

A) Train the policy exclusively on the most accurate single simulation model available
B) Deploy the simulation-trained policy directly and rely on the robot's onboard PID controller to compensate
C) Reduce the simulation timestep to improve numerical precision of the physics engine
D) Apply domain randomization by varying friction, noise, and latency parameters across training episodes

---

**Q19.** A robotics engineer must design a controller for a pick-and-place task where the arm's kinematics are fully known, the environment is static and well-characterized, and millimeter-level repeatable precision is required with no tolerance for exploration-based trial and error. Which approach is most appropriate?

A) A deep reinforcement learning policy trained with a sparse success/failure reward
B) An online policy-gradient RL agent that continues learning on the deployed hardware
C) A model-free RL agent trained from scratch with random exploration on the physical arm
D) A classical control approach using inverse kinematics and PID control

---

**Q20.** A team designs a reward function for a bipedal locomotion RL task that gives the agent +1 for every meter moved forward, with no other terms in the reward. After training, the robot learns to repeatedly fall forward to maximize forward displacement instead of walking stably. This outcome is an example of which issue?

A) Reward hacking caused by an incomplete reward function that omits stability and energy penalties
B) Catastrophic forgetting due to insufficient replay buffer size
C) Overfitting to the simulation's exact physics timestep
D) Vanishing gradients in the policy network's value function

---

**Q21.** A home-assistant robot uses an LLM to interpret the spoken command "bring me the thing I was drinking from earlier." The LLM generates a plausible-sounding but factually incorrect reference to a mug that was never used that day. Which mitigation BEST addresses this failure mode in LLM-driven robot instruction?

A) Increase the LLM's temperature setting to generate more creative interpretations
B) Ground the LLM's output against real-time perception and memory logs before executing the action
C) Replace the LLM entirely with a rule-based keyword matcher
D) Ignore the command and wait for the user to repeat it verbatim

---

**Q22.** In a human-robot voice interaction pipeline, which component is responsible for converting the robot's generated textual response into audible spoken output?

A) Text-to-Speech (TTS)
B) Automatic Speech Recognition (ASR)
C) Natural Language Understanding (NLU)
D) Dialogue Manager

---

**Q23.** A robot's intent-recognition module assigns a confidence score to each interpreted voice command before execution. The system is configured with a minimum confidence threshold of 0.75. A command is parsed with a confidence score of 0.52. What should the robot do, per best practice for safe command handling?

A) Execute the command since any recognized intent is better than none
B) Execute the highest-probability interpretation regardless of score
C) Shut down all NLP services until manually restarted
D) Ask the user for clarification instead of executing the ambiguous command

---

**Q24.** In a voice-controlled robot's NLP pipeline, what is the key functional difference between Automatic Speech Recognition (ASR) and Natural Language Understanding (NLU)?

A) ASR and NLU are interchangeable terms for the same speech processing stage
B) ASR transcribes spoken audio into text, while NLU extracts intent and entities from that text
C) ASR generates the robot's spoken replies, while NLU records user audio
D) NLU converts audio to text, while ASR determines the user's intent

---

**Q25.** A manufacturing robot must grasp a novel, previously unseen irregularly shaped object. Engineers want to use generative AI to produce candidate grasp trajectories rather than relying solely on a fixed library of pre-programmed grasps. Which approach BEST reflects the use of generative AI for robotic creativity in this scenario?

A) Use a generative model trained on grasp data to synthesize novel candidate grasp poses for the unseen object, then validate them via simulation or sensors
B) Hard-code a lookup table mapping object shapes to grasp poses
C) Disable the manipulation task and alert a human operator for every unseen object
D) Use only the nearest-neighbor match from the existing grasp library, even if dissimilar

---

**Q26.** A customer-service robot conducts a multi-turn conversation: "Order a pizza." → "What size?" → "Large." → "What toppings?" → "Same as last time." Which conversational AI component is primarily responsible for retaining and resolving the context (order details, slot values) across these multiple turns?

A) The text-to-speech synthesizer
B) The automatic speech recognizer
C) The acoustic noise-cancellation filter
D) The dialogue state tracker / dialogue manager

---

**Q27.** A warehouse robot uses an LLM-based pipeline to interpret spoken commands and convert them into executable action sequences. A worker says, 'Grab the box near the broken shelf and bring it to receiving.' Which architecture component is primarily responsible for translating this natural language instruction into a structured robot action plan?

A) A semantic parser or grounding module that maps language intent and referenced objects to the robot's action and perception APIs
B) A text-to-speech synthesis module that generates the robot's spoken confirmation
C) A SLAM module that builds a 2D occupancy grid of the warehouse
D) A PID controller that regulates the robot's wheel velocity

---

**Q28.** A company is designing a conversational interface for a humanoid service robot and wants it to maintain context across multiple turns of dialogue (e.g., remembering that 'it' refers to an object mentioned two sentences earlier). Which capability MUST the dialogue system implement to support this?

A) Increasing the robot's actuator torque limits
B) Replacing the camera sensor with a higher resolution model
C) Dialogue state tracking with conversational memory across turns
D) Reducing the LLM's token generation temperature to zero

---

**Q29.** A fulfillment center operates with human pickers also present on the warehouse floor, aisles reconfigured weekly, and inventory locations that shift with demand. Robots must navigate dynamically, re-route around obstacles and people, and travel to changing destinations to ferry totes to packing stations. Which robot category BEST fits this requirement?

A) An Automated Guided Vehicle (AGV) following fixed magnetic tape or wire-guided paths
B) A six-axis industrial robotic arm bolted to the packing station
C) A software RPA bot scheduling tote pickups in the warehouse management system
D) An Autonomous Mobile Robot (AMR) using onboard mapping, SLAM, and dynamic path planning

---

**Q30.** A hospital's billing department spends hours each day copying patient insurance numbers from a scanned intake form into three separate legacy systems that lack APIs, following the exact same rule-based steps every time with no physical movement involved. Which solution is the MOST appropriate automation choice?

A) A collaborative service robot with a robotic arm positioned at the admissions desk
B) An Autonomous Mobile Robot (AMR) to physically carry paperwork between departments
C) An industrial robotic arm retrofitted with a document scanner attachment
D) A software RPA bot that mimics the clerk's keystrokes and mouse actions across the three systems

---

**Q31.** What is the fundamental distinction the AT-420 curriculum draws between a physical robot and a software RPA bot (the 'digital robot')?

A) Physical robots sense and act upon the physical world via sensors and actuators, while RPA bots sense and act upon digital interfaces and data without physical embodiment
B) Physical robots can only operate in industrial settings while RPA bots can only operate in healthcare settings
C) Physical robots require AI while RPA bots never use any form of intelligent decision-making
D) Physical robots are always more expensive to deploy than RPA bots in every use-case

---

**Q32.** An RPA Center of Excellence is scoping candidate processes for automation at an insurance company. Which process characteristic makes a given workflow the MOST suitable candidate for RPA?

A) The process requires creative judgment and varies significantly case-by-case
B) The process requires physical handling of paper documents stored in a filing cabinet
C) The process is high-volume, rule-based, uses structured/semi-structured data, and has a low exception rate
D) The process changes its underlying business logic on a weekly basis

---

**Q33.** A manufacturer needs to perform precise, high-speed spot welding on vehicle chassis at fixed stations along an assembly line, repeating the identical motion thousands of times per shift. Which robot category is the standard solution for this use-case?

A) A mobile service robot that travels between welding stations
B) A software RPA bot orchestrating the welding schedule
C) A fixed-base industrial robotic arm programmed for repetitive high-precision motion
D) An Autonomous Mobile Robot (AMR) equipped with a welding torch

---

**Q34.** A hospital wants a robot that can autonomously navigate occupied corridors at night, avoid staff and equipment, and perform UV-C disinfection in patient rooms without any pre-mapped fixed track. Which type of robotic solution should be selected?

A) A software RPA bot scheduling cleaning staff shifts
B) A fixed-base industrial robotic arm with a UV-C attachment
C) An Autonomous Mobile Robot (AMR) service robot equipped with UV-C disinfection modules and dynamic navigation
D) An AGV following a wire embedded in the corridor floor

---

**Q35.** A finance department needs to automate repetitive invoice reconciliation that involves logging into an ERP system, extracting data via its API, and cross-checking it against a legacy accounting application's UI. No physical materials need to be moved or manipulated. Which solution BEST meets this requirement?

A) Deploy a collaborative robot (cobot) arm at the finance team's workstation to handle paperwork
B) Deploy a software RPA bot that automates the UI/API interactions between the ERP and accounting systems
C) Deploy an autonomous mobile robot (AMR) to physically carry printed invoices between departments
D) Deploy an industrial Cartesian robot to sort paper invoices by category

---

**Q36.** A warehouse operator needs robots to transport goods across a facility whose layout changes weekly, with workers, pallets, and forklifts creating unpredictable obstacles. The robots must reroute dynamically without requiring physical infrastructure changes. Which solution BEST meets these requirements?

A) An Automated Guided Vehicle (AGV) that follows fixed magnetic floor tape or embedded wires
B) An Autonomous Mobile Robot (AMR) using SLAM-based mapping and onboard obstacle-detection sensors
C) A statically mounted industrial robot arm bolted to the warehouse floor
D) A software RPA bot integrated with the warehouse management system's inventory database

---

**Q37.** A robotics startup wants a single model that can take a natural-language instruction like "pick up the red cup and place it on the shelf" along with a live camera feed, and directly output robot joint/gripper commands. Which class of model BEST fits this requirement?

A) A classical PID controller tuned per task
B) A Vision-Language-Action (VLA) foundation model
C) A rule-based finite state machine
D) A standalone large language model with no visual input

---

**Q38.** A logistics company deploys 200 small identical robots in a warehouse. There is no central controller; each robot follows simple local rules (avoid collisions, follow pheromone-like signals, communicate with nearby peers) and the fleet as a whole efficiently sorts packages even if individual units fail. This architecture is an example of which emerging robotics paradigm?

A) Centralized fleet management
B) Monolithic single-robot control
C) Swarm robotics
D) Supervisory teleoperation

---

**Q39.** In current robotics and AI discourse, the term "Physical AI" most precisely refers to:

A) Cloud-based AI services that only process text and images
B) Firmware that controls a robot's power supply
C) Any AI algorithm regardless of whether it interacts with the real world
D) AI systems embodied in machines that perceive, reason about, and act within the physical world

---

**Q40.** Which statement BEST captures a key distinction between modern humanoid robots and traditional fixed industrial robot arms, as emphasized in current robotics trends?

A) Humanoid robots are always slower and less accurate than industrial arms in every task
B) Humanoid robots are designed for versatility across human-built environments and tasks, while industrial arms are optimized for fixed, repetitive tasks in structured settings
C) Industrial arms can walk and navigate stairs, while humanoids cannot
D) There is no meaningful difference; the terms are interchangeable

---

**Q41.** To train a Vision-Language-Action (VLA) foundation model for robot manipulation, which combination of data is typically required?

A) Paired visual observations, natural-language instructions, and corresponding robot action trajectories
B) Only text transcripts of human conversations
C) Only simulated physics engine logs with no sensor data
D) Only labeled static images with no robot motion data

---

**Q42.** A research lab releases a single robot foundation model pretrained on manipulation data collected from many different robot embodiments and environments. When deployed on a new robot arm it has never seen, the model adapts to new pick-and-place tasks with only a handful of demonstrations. This capability is primarily enabled by which emerging trend?

A) Hard-coded per-robot calibration scripts
B) Single-task reinforcement learning trained from scratch on the new robot
C) Cross-embodiment generalist robot foundation models with few-shot adaptation
D) Manual re-programming of the control stack for each new robot

---

**Q43.** A robotics team wants to deploy a single foundation model that takes raw camera images and a natural language command like 'pick up the red cup and place it in the bin' and directly outputs low-level robot actuator commands, without hand-coding separate perception and planning pipelines. Which emerging class of model BEST fits this requirement?

A) A standalone convolutional neural network image classifier
B) A rule-based SLAM (Simultaneous Localization and Mapping) module
C) A Vision-Language-Action (VLA) model
D) A robotic process automation (RPA) bot scripted for UI tasks

---

**Q44.** A warehouse robotics company deploys autonomous forklifts that operate alongside human workers. During testing, a forklift fails to stop in time when a worker unexpectedly enters its path, causing a near-miss. Which design change BEST addresses the underlying safety gap according to responsible robotics deployment principles?

A) Increase the forklift's top speed so it completes tasks faster and spends less time near workers
B) Remove human workers entirely from the warehouse floor during all robot operating hours
C) Rely solely on post-incident logging to analyze near-misses after they occur
D) Add a redundant perception and emergency-stop system with a safety-rated minimum stopping distance, combined with a human oversight protocol for exceptions

---

**Q45.** In the context of liability for autonomous physical systems, which statement BEST reflects current responsible-AI robotics guidance on assigning accountability when a robot causes harm during an unsupervised task?

A) Liability is automatically eliminated once a system is certified as 'autonomous'
B) Liability can never be assigned to a robot's manufacturer under any circumstances
C) Accountability must be traceable across the deployment chain, including designers, deployers, and operators, with clear documentation of decision boundaries and human oversight responsibilities
D) Only the end user operating the robot at the time of the incident can be held responsible

---

**Q46.** A healthcare organization deploys a robotic triage assistant trained primarily on data from one demographic group. Post-deployment audits reveal it recommends longer wait times for patients outside that group with similar symptom severity. Which action represents the BEST response consistent with responsible, bias-aware deployment of autonomous physical systems?

A) Ignore the finding since the robot's hardware and sensors function correctly
B) Deploy the system only in facilities serving the original demographic group to avoid the issue
C) Suspend the biased recommendation feature, retrain on a representative dataset, and re-validate performance across demographic groups before redeployment
D) Add a disclaimer that the robot is 'experimental' without changing its behavior

---

