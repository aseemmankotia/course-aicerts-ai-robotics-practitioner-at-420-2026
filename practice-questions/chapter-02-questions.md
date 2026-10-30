## Chapter 2: Autonomous Systems and Intelligent Agents — Practice Questions

**Q1.** A warehouse robot operates among forklifts and workers whose positions change unpredictably every second. The robot must adjust its trajectory within milliseconds to avoid collisions, without recomputing a full route. Which navigation approach BEST fits this requirement?

A) Global path planning using A* on a static occupancy grid
B) Offline route optimization computed once before the shift starts
C) Reactive navigation using a local obstacle-avoidance method (e.g., Dynamic Window Approach)
D) Waiting for a human operator to manually redirect the robot each time

<details>
<summary>Answer</summary>

**Correct: C**

Reactive navigation operates on immediate sensor data at high frequency, making it suited for fast, local obstacle avoidance in dynamic environments.

**Why the others are wrong:**
- A* on a static grid assumes a map that doesn't change moment-to-moment and is too slow to recompute for every moving obstacle.
- Offline optimization cannot respond to obstacles unknown at planning time.
- Manual redirection defeats the purpose of autonomy and cannot react fast enough.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A drone enters a collapsed building with no GPS signal. It must determine its own position while simultaneously building a usable map of the unexplored interior. Which technique directly addresses this requirement?

A) Dead reckoning using wheel odometry only
B) GPS-based waypoint navigation
C) Static map lookup from a pre-loaded floor plan
D) SLAM (Simultaneous Localization and Mapping)

<details>
<summary>Answer</summary>

**Correct: D**

SLAM is specifically designed to build a map of an unknown environment while simultaneously tracking the agent's position within it.

**Why the others are wrong:**
- Dead reckoning alone drifts over time and provides no mapping capability.
- GPS is unavailable in this scenario, making this option infeasible.
- A pre-loaded floor plan assumes the environment is already known, contradicting the scenario.

</details>

---

**Q3.** An engineer must fuse noisy, nonlinear IMU and camera pose data into a single reliable state estimate for a ground robot, assuming the uncertainty is approximately unimodal (single Gaussian belief). Which technique is the BEST fit?

A) Simple weighted average of the two raw sensor readings
B) Raw IMU integration with no correction
C) Extended Kalman Filter (EKF)
D) Particle Filter with 10,000 particles

<details>
<summary>Answer</summary>

**Correct: C**

EKF is the standard technique for fusing nonlinear sensor data under a unimodal Gaussian uncertainty assumption, linearizing the system around the current estimate.

**Why the others are wrong:**
- A simple weighted average ignores each sensor's uncertainty model and nonlinearity, producing a poor estimate.
- Raw IMU integration drifts unboundedly without correction from another sensor.
- Particle filters are better suited to multimodal, highly non-Gaussian beliefs; they are heavier-weight than needed here.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A team builds an autonomous ground vehicle where an LLM-based agent handles high-level route decisions (reasoning takes ~2 seconds) and a separate controller must avoid obstacles at a 50 Hz loop rate. How should the architecture be structured?

A) Run the LLM reasoning step inside the 50 Hz obstacle-avoidance loop so every control cycle gets a fresh decision
B) Decouple the loops: the LLM agent sets high-level goals/waypoints on a slow cadence, while a separate fast reactive controller handles real-time obstacle avoidance
C) Replace the 50 Hz controller entirely with the LLM agent to simplify the architecture
D) Run the LLM only once at startup and never update high-level goals again

<details>
<summary>Answer</summary>

**Correct: B**

Hybrid architectures decouple slow, high-level agentic reasoning from fast, low-level reactive control, since LLM-based reasoning cannot meet real-time loop rates.

**Why the others are wrong:**
- A 2-second reasoning step cannot execute at 50 Hz (20 ms per cycle), making this infeasible.
- Removing the fast controller would leave the robot unable to react to obstacles in real time.
- Never updating goals would make the robot unable to adapt to changing conditions.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** A mobile robot performs its task independently, but a human operator continuously monitors its status and can intervene or override the robot's actions at any time. Where does this system fall on the autonomy spectrum?

A) Teleoperated
B) Supervised / semi-autonomous
C) Fully autonomous
D) Manual operation

<details>
<summary>Answer</summary>

**Correct: B**

Supervised autonomy describes a system that executes tasks on its own while a human monitors and retains override capability.

**Why the others are wrong:**
- Teleoperated means a human directly controls every action in real time, which is not the case here.
- Fully autonomous implies no human monitoring or intervention capability at all.
- Manual operation means the human performs the task directly, not the robot.

</details>

---

**Q6.** A vehicle automatically controls steering and speed on the highway, but the driver must continuously watch the road and keep hands near the wheel, ready to intervene instantly. Which automation level does this describe?

A) SAE Level 1
B) SAE Level 2
C) SAE Level 3
D) SAE Level 4

<details>
<summary>Answer</summary>

**Correct: B**

SAE Level 2 (partial automation) requires the driver to continuously monitor the environment and remain ready to take over immediately, even though the system controls steering and speed.

**Why the others are wrong:**
- Level 1 automates only a single function (e.g., either steering or speed, not both).
- Level 3 allows the driver to disengage attention until the system explicitly requests takeover — continuous monitoring is not required.
- Level 4 requires no driver supervision within its defined operational domain.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** An autonomous delivery robot receives conflicting sensor readings about whether a crosswalk is clear, due to sensor noise. Which approach allows it to make a well-informed decision despite this uncertainty?

A) Ignore the uncertain sensor and proceed using a fixed rule
B) Use only the single most recent sensor reading and discard all history
C) Use probabilistic reasoning (e.g., a POMDP or Bayesian belief update) to weigh the conflicting evidence
D) Halt indefinitely until all sensors report identical values

<details>
<summary>Answer</summary>

**Correct: C**

Probabilistic frameworks like POMDPs explicitly model partial observability and noisy sensing, allowing the agent to act on a belief distribution rather than requiring certainty.

**Why the others are wrong:**
- Ignoring uncertain data discards useful information and increases collision risk.
- Using only the latest reading discards the benefit of fusing information over time.
- Waiting for identical sensor values may never happen in a noisy real-world environment, causing the robot to stall indefinitely.

</details>

---

**Q8.** What is the KEY difference between the classical robotics sense-plan-act loop and an agentic AI sense-reason-act loop built on an LLM?

A) There is no meaningful difference between the two loops
B) The agentic loop always runs faster than the classical robotics loop
C) The classical loop uses natural language reasoning internally
D) The classical loop runs synchronously at high frequency for direct control, while the agentic loop uses slower symbolic/natural-language reasoning, typically for high-level planning decoupled from real-time control

<details>
<summary>Answer</summary>

**Correct: D**

Classical sense-plan-act loops execute at control-loop frequencies (ms range), while LLM-based reasoning takes seconds and is generally reserved for higher-level decision-making decoupled from tight control loops.

**Why the others are wrong:**
- The loops differ meaningfully in latency, representation, and typical use case.
- LLM reasoning is substantially slower than classical control-loop computation, not faster.
- Classical robotics loops use numerical/geometric state representations, not natural language.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

