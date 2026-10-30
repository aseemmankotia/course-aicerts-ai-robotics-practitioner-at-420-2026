## Chapter 3: AI and Robotics Development Frameworks — Practice Questions

**Q1.** A robotics company needs two nodes to exchange sensor data continuously at high frequency without either node blocking while waiting for a response. Which ROS 2 communication pattern should they use?

A) Topic
B) Service
C) Action
D) Parameter

<details>
<summary>Answer</summary>

**Correct: A**

Topics implement asynchronous publish/subscribe messaging, ideal for continuous streaming data like sensor readings without blocking either side.

**Why the others are wrong:**
- Service is synchronous request/response — it blocks the caller until a reply arrives, unsuitable for continuous streams.
- Action is designed for long-running goal-based tasks with feedback, not simple continuous data flow.
- Parameter is a configuration mechanism for node settings, not a data exchange pattern between nodes.

</details>

---

**Q2.** A robot arm must execute a long-running 'move to position' task where the client receives continuous progress feedback and can cancel the task mid-execution. Which ROS 2 communication type fits best?

A) Topic
B) Service
C) Parameter
D) Action

<details>
<summary>Answer</summary>

**Correct: D**

Actions are built specifically for long-running, goal-based tasks that provide feedback during execution and support cancellation.

**Why the others are wrong:**
- Topic provides no built-in mechanism for goal tracking, feedback, or cancellation semantics.
- Service only supports a single request and single response — no ongoing feedback or cancellation support.
- Parameter is used for node configuration values, not task execution.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A team wants to quickly test a new locomotion algorithm's physics behavior before deploying to real hardware, prioritizing fast iteration with lightweight 3D physics rather than photorealistic GPU rendering. Which tool best fits this need?

A) NVIDIA Isaac Sim
B) ROS 2 Topics
C) Gazebo
D) DDS

<details>
<summary>Answer</summary>

**Correct: C**

Gazebo provides open-source, lightweight physics simulation well suited for rapid iteration and functional testing of robot behavior.

**Why the others are wrong:**
- Isaac Sim is optimized for GPU-accelerated photorealistic rendering and large-scale synthetic data/RL training, which is heavier than needed here.
- ROS 2 Topics are a communication mechanism, not a simulation environment.
- DDS is the middleware protocol for message exchange, not a physics simulator.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** Which tool is best suited for generating large volumes of photorealistic synthetic training data for perception models and reinforcement learning?

A) Gazebo
B) rviz
C) NVIDIA Isaac Sim
D) rosbag

<details>
<summary>Answer</summary>

**Correct: C**

Isaac Sim, built on NVIDIA Omniverse, offers GPU-accelerated photorealistic rendering and physics designed for synthetic data generation and RL training at scale.

**Why the others are wrong:**
- Gazebo focuses on lightweight functional physics simulation, not photorealistic synthetic data generation.
- rviz is a visualization tool for sensor and robot state data, not a simulator for training data generation.
- rosbag is a tool for recording and replaying ROS message data, not generating synthetic training data.

</details>

---

**Q5.** Which middleware technology does ROS 2 use for node discovery and real-time data exchange?

A) MQTT
B) gRPC
C) AMQP
D) DDS

<details>
<summary>Answer</summary>

**Correct: D**

ROS 2 is built on DDS (Data Distribution Service), which handles node discovery, serialization, and configurable QoS-based real-time communication.

**Why the others are wrong:**
- MQTT is a lightweight IoT messaging protocol not used as ROS 2's core middleware.
- gRPC is a remote procedure call framework, unrelated to ROS 2's default communication layer.
- AMQP is a message queuing protocol used in enterprise messaging, not ROS 2's middleware.

</details>

---

**Q6.** A developer needs a critical safety message to reach a subscriber even if that subscriber joins the network late, accepting higher latency to guarantee delivery. Which DDS QoS configuration should be used?

A) Best Effort reliability, Volatile durability
B) Best Effort reliability, Transient Local durability
C) Reliable reliability, Volatile durability
D) Reliable reliability, Transient Local durability

<details>
<summary>Answer</summary>

**Correct: D**

Reliable reliability guarantees message delivery, and Transient Local durability caches the last published messages so late-joining subscribers still receive them.

**Why the others are wrong:**
- Best Effort with Volatile durability neither guarantees delivery nor retains messages for late joiners — least safe option.
- Best Effort reliability does not guarantee delivery even though durability would cache the message, failing the safety requirement.
- Volatile durability discards messages once sent, so a late-joining subscriber would miss them even with reliable delivery.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** Which ROS 2 file type is used to start multiple nodes together with specific parameters and topic remappings in a single command?

A) Launch file
B) package.xml
C) CMakeLists.txt
D) URDF file

<details>
<summary>Answer</summary>

**Correct: A**

Launch files (XML, Python, or YAML) define which nodes to start together along with their parameters and remappings, avoiding manual node-by-node startup.

**Why the others are wrong:**
- package.xml declares package metadata and dependencies, not runtime node startup configuration.
- CMakeLists.txt is used for build configuration in C++ ROS 2 packages, not for launching nodes.
- URDF files describe a robot's physical structure (links and joints), not node startup behavior.

</details>

---

**Q8.** In the standard robotics software stack, which layer sits directly between physical sensors/actuators and the middleware layer, translating hardware signals into software messages?

A) Control layer
B) Planning layer
C) Driver layer
D) Simulation layer

<details>
<summary>Answer</summary>

**Correct: C**

The driver layer interfaces directly with hardware, converting raw sensor/actuator signals into messages the middleware (ROS 2/DDS) can distribute.

**Why the others are wrong:**
- Control layer executes commands to actuators based on planning output, sitting above the stack near actuation, not at the hardware-interface boundary.
- Planning layer determines paths or task sequences using perception data, operating above the driver and middleware layers.
- Simulation is not a standard layer in the deployed robotics software stack — it's a separate development-time tool.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

