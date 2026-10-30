## Chapter 5: Reinforcement Learning for Robotics — Practice Questions

**Q1.** A legged robot's RL locomotion policy achieves perfect walking in simulation across thousands of training episodes, but falls immediately when deployed on the physical robot walking on stairs. The simulation used accurate kinematics but default physics engine contact parameters with no randomization. What is the MOST likely cause?

A) Sim-to-real gap due to mismatched dynamics, contact models, and sensor noise between simulation and hardware
B) Insufficient training steps in simulation
C) PID controller gains set too low
D) Reward function was too sparse causing underfitting

<details>
<summary>Answer</summary>

**Correct: A**

Default, non-randomized contact/friction models and unmodeled sensor noise are the classic sim-to-real gap sources — the policy overfits to simulator-specific dynamics that don't match real hardware.

**Why the others are wrong:**
- Training converged to a stable sim policy already, so more steps wouldn't fix a dynamics mismatch that only appears on real hardware.
- No PID controller was described — this is an end-to-end learned policy, not a classical control stack.
- A sparse reward would show poor performance in simulation too; here the sim policy already works perfectly.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A robotic arm manipulation policy is trained with a reward equal only to the negative distance between the gripper and the target object. After training, the arm hovers its gripper just above the object indefinitely without ever closing it, maximizing reward without completing the task. Which fix BEST addresses this?

A) Reduce the number of training episodes
B) Add an explicit grasp-success/contact term to the reward instead of relying only on distance-to-object
C) Increase the learning rate
D) Increase reward magnitude uniformly

<details>
<summary>Answer</summary>

**Correct: B**

This is textbook reward hacking: the agent exploits an under-specified proxy reward (distance) rather than the true objective (task completion). Adding an explicit success/contact term closes the loophole.

**Why the others are wrong:**
- Shorter training wouldn't change what the reward function incentivizes — the exploit would persist or even appear earlier.
- Learning rate affects convergence speed, not what behavior is optimal under the given reward.
- Scaling the reward uniformly preserves the same optimal policy — hovering still maximizes reward, just with bigger numbers.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A 6-DOF industrial arm has a well-characterized dynamics model, operates in a highly structured environment, requires a 1kHz control loop, and must provide formal stability guarantees for a safety-critical process. Which approach is MOST appropriate?

A) Deep RL trained from scratch with sparse reward
B) Classical control (PID/MPC), since dynamics are well known and formal stability/safety guarantees are required
C) Pure imitation learning from human demonstrations
D) Model-free RL with random exploration

<details>
<summary>Answer</summary>

**Correct: B**

When dynamics are known, the task is structured, and provable stability/real-time guarantees are needed, classical control (PID/MPC) outperforms RL, which lacks formal guarantees and needs exploration that is risky at 1kHz on safety-critical hardware.

**Why the others are wrong:**
- RL from scratch requires extensive exploration that is unsafe and unnecessary when an accurate dynamics model already exists.
- Imitation learning inherits demonstrator suboptimality and still lacks the formal guarantees MPC provides for a known model.
- Random exploration directly on safety-critical hardware at 1kHz risks damage and violates the stability requirement.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A team has only a few hours of real robot time available for training and needs to learn a manipulation policy as sample-efficiently as possible. Which approach BEST fits this constraint?

A) Model-based RL that learns a dynamics model to plan or generate synthetic rollouts, reducing the number of real-world samples needed
B) Model-free PPO trained purely on physical hardware
C) Random search over policy parameters
D) Deploy a sim-trained policy directly with zero domain randomization

<details>
<summary>Answer</summary>

**Correct: A**

Model-based RL learns a dynamics model from limited real data and uses it to generate additional synthetic experience or plan actions, substantially improving sample efficiency compared to pure model-free methods.

**Why the others are wrong:**
- Model-free PPO is notoriously sample-hungry and typically requires far more real-world rollouts than a few hours can provide.
- Random search is even less sample-efficient than gradient-based RL and ignores learned structure entirely.
- Deploying a sim policy with zero domain randomization will likely fail on hardware due to the sim-to-real gap, and doesn't address the sample-efficiency requirement at all.

</details>

---

**Q5.** A team needs an off-policy, replay-buffer-based algorithm with entropy regularization for a continuous-control grasping task to maximize sample reuse. Which algorithm fits this description?

A) Soft Actor-Critic (SAC)
B) REINFORCE (vanilla policy gradient)
C) Proximal Policy Optimization (PPO, on-policy)
D) Tabular Q-learning

<details>
<summary>Answer</summary>

**Correct: A**

SAC is an off-policy, actor-critic algorithm that uses a replay buffer and an entropy bonus to encourage exploration, making it well suited to sample-efficient continuous control.

**Why the others are wrong:**
- REINFORCE is on-policy and high-variance, discarding data after each update rather than reusing it via a replay buffer.
- PPO is explicitly on-policy and does not use a replay buffer for off-policy updates.
- Tabular Q-learning requires discrete state/action spaces and cannot handle continuous control directly.

</details>

---

**Q6.** When applying domain randomization to close the sim-to-real gap for a legged locomotion policy, which set of parameters should be randomized?

A) Only the ground texture color
B) Only the simulator's random seed
C) Only the reward function's scalar weights
D) Physical parameters such as friction coefficients, mass/inertia distribution, motor strength, sensor noise, and actuation latency

<details>
<summary>Answer</summary>

**Correct: D**

Domain randomization targets the physical and sensing parameters most likely to differ between sim and real hardware — friction, mass/inertia, motor strength, sensor noise, and latency — forcing the policy to generalize across this uncertainty.

**Why the others are wrong:**
- Texture randomization helps vision-based policies but does nothing for the dynamics/contact mismatch that causes locomotion failures.
- Changing only the random seed varies the episode's randomness, not the actual physical parameters the policy must generalize over.
- Reward weights affect what is optimized for, not the physics discrepancy between simulation and the real robot.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** Why is potential-based reward shaping specifically favored over arbitrary dense reward shaping when designing robotics reward functions?

A) It increases the discount factor automatically during training
B) It replaces the sparse reward entirely with an imitation-learning signal
C) It adds dense shaping reward while provably preserving the original optimal policy
D) It changes the optimal policy to make training converge faster regardless of correctness

<details>
<summary>Answer</summary>

**Correct: C**

Potential-based reward shaping (Ng et al.) is mathematically guaranteed to leave the optimal policy unchanged while providing denser learning signal, unlike arbitrary shaping which can introduce unintended reward-hacking incentives.

**Why the others are wrong:**
- Potential-based shaping does not touch the discount factor; it adds a shaping term derived from a potential function.
- It supplements the original reward, it does not replace it with an imitation signal.
- Arbitrary shaping that changes the optimal policy is exactly the failure mode potential-based shaping is designed to avoid.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** In reinforcement learning terminology as applied to robotics, what is a 'policy'?

A) A mapping from observed state (or history) to an action or action distribution
B) The simulator's physics engine configuration
C) The scalar reward function used during training
D) A fixed lookup table of PID gains

<details>
<summary>Answer</summary>

**Correct: A**

A policy is the function (often a neural network) the agent uses to select actions given its current observation/state — this is the core object being optimized in RL.

**Why the others are wrong:**
- The physics engine configuration defines the environment/simulator, not the agent's decision-making function.
- The reward function defines the objective being optimized, not the action-selection mechanism itself.
- A fixed PID gain table is a classical control artifact, not a learned RL policy, and doesn't adapt via state-conditioned action selection in the RL sense.

</details>

---

