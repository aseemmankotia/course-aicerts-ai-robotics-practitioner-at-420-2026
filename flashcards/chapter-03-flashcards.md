## Chapter 3: AI and Robotics Development Frameworks — Flashcards

| # | Front (Question) | Back (Answer) |
|---|-----------------|---------------|
| 1 | ROS 2 Topic communication pattern? | Publish/subscribe, asynchronous, many-to-many. Best for continuous data streams like sensor readings. Exam tip: publishers are never blocked waiting for subscribers. |
| 2 | ROS 2 Service communication pattern? | Synchronous request/response, one-to-one, caller blocks until response arrives. Exam tip: use for quick, single computations, not long tasks. |
| 3 | ROS 2 Action communication pattern? | Goal-based, long-running task with feedback and cancellation, built internally from topics + services. Exam tip: Action = goal + feedback + result. |
| 4 | What middleware does ROS 2 use for communication? | DDS (Data Distribution Service) — handles node discovery, serialization, and QoS-based real-time data exchange. |
| 5 | DDS QoS: Reliable vs Best Effort? | Reliable = guaranteed delivery, higher latency, used for critical commands/safety data. Best Effort = no guarantee, lower latency, used for high-frequency sensor data like camera feeds. |
| 6 | DDS QoS: Volatile vs Transient Local durability? | Volatile = late-joining subscribers miss prior messages. Transient Local = publisher retains last messages so late joiners still receive them. Exam tip: use Transient Local for state/config data. |
| 7 | Gazebo vs NVIDIA Isaac Sim — key difference? | Gazebo: lightweight, open-source physics simulation for fast functional testing. Isaac Sim: GPU-accelerated, photorealistic Omniverse-based simulation for synthetic data generation and RL training at scale. |
| 8 | Why use a 'simulation-first' development workflow in robotics? | Test and debug algorithms safely in simulated physics/sensors before deploying to real hardware, reducing risk and cost of damaging expensive robots. |
| 9 | Robotics software stack layers, bottom to top? | Driver → Middleware (ROS 2/DDS) → Perception → Planning → Control. Exam tip: Driver translates raw hardware signals into software messages. |
| 10 | What is a ROS 2 'package'? | The basic organizational unit in ROS 2 bundling nodes, launch files, configs, and dependencies for a specific functionality. |
| 11 | What is a ROS 2 'launch file' used for? | Starts and configures multiple nodes together with parameters and topic remappings in a single command, instead of launching each node manually. |
| 12 | Which ROS 2 communication type is built on top of both topics and services? | Actions — use topics for ongoing feedback/status and services for the initial goal request and cancellation, combining both patterns for long-running tasks. |
