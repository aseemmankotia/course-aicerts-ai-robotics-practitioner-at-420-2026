## Chapter 1: Robotics and AI Foundations — Practice Questions

**Q1.** A warehouse AGV end-effector must grasp a pallet at a specific pose. The controller must compute the required joint angles from the desired end-effector position. Which process is being performed?

A) Inverse kinematics
B) Forward kinematics
C) Proprioceptive sensing
D) Perception-plan-act loop

<details>
<summary>Answer</summary>

**Correct: A**

Inverse kinematics computes joint angles from a desired end-effector pose — the opposite direction of forward kinematics.

**Why the others are wrong:**
- Forward kinematics computes end-effector pose FROM known joint angles, the reverse direction.
- Proprioceptive sensing measures internal robot state, not a kinematic computation.
- The perception-plan-act loop is the overall control cycle, not the specific kinematic calculation.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A humanoid robot uses an onboard IMU to detect its own tilt and balance relative to gravity, without referencing any external landmark. This is an example of:

A) Proprioceptive sensing
B) Exteroceptive sensing
C) Actuation feedback
D) Inverse kinematics

<details>
<summary>Answer</summary>

**Correct: A**

An IMU measures the robot's own internal orientation and acceleration, making it a proprioceptive sensor by definition.

**Why the others are wrong:**
- Exteroceptive sensors (cameras, lidar) measure the external environment, not the robot's own state.
- Actuation feedback is a general term, not the sensor category being tested here.
- Inverse kinematics is a motion-planning calculation, unrelated to sensing.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** An industrial press robot must move very heavy loads with high continuous force in a demanding factory environment. Which actuator type BEST meets this requirement?

A) Electric servo motor
B) Pneumatic actuator
C) Stepper motor
D) Hydraulic actuator

<details>
<summary>Answer</summary>

**Correct: D**

Hydraulic actuators deliver the highest force density, making them the standard choice for heavy-load industrial applications like presses.

**Why the others are wrong:**
- Electric servos offer precision but lower maximum force relative to hydraulics for heavy press-type loads.
- Pneumatic actuators are limited by air compressibility, giving lower force stability for heavy sustained loads.
- Stepper motors are suited to precise low-to-medium torque positioning, not heavy industrial force output.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** Which robot taxonomy category BEST describes a fixed-base industrial arm welding car frames on an assembly line?

A) Mobile robot
B) Manipulator
C) Humanoid
D) Autonomous underwater vehicle

<details>
<summary>Answer</summary>

**Correct: B**

Manipulators are fixed-base robotic arms designed for tasks such as welding and assembly.

**Why the others are wrong:**
- Mobile robots move through an environment; this arm has a fixed base.
- Humanoid robots mimic the human body form, which is not implied here.
- Autonomous underwater vehicles operate underwater and are unrelated to a factory arm.

</details>

---

**Q5.** A sidewalk delivery robot must detect pedestrians and obstacles ahead to avoid collisions. Which sensor category should be prioritized for this task?

A) Proprioceptive
B) Exteroceptive
C) Internal encoder
D) Gyroscope

<details>
<summary>Answer</summary>

**Correct: B**

Exteroceptive sensors such as cameras, lidar, and ultrasonic sensors perceive the external environment, including obstacles and pedestrians.

**Why the others are wrong:**
- Proprioceptive sensors measure internal robot state, not external objects.
- Encoders measure internal joint/wheel rotation and are proprioceptive.
- Gyroscopes measure internal orientation and angular velocity and are proprioceptive.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** In the Perception-Plan-Act loop, which stage integrates raw sensor data into an internal world model before an action is decided?

A) Act
B) Plan
C) Perception
D) Actuation feedback

<details>
<summary>Answer</summary>

**Correct: C**

The Perception stage processes raw sensor data into a usable representation of the world state.

**Why the others are wrong:**
- Act is the execution stage, which occurs after planning, not before perception.
- Plan uses the perceived world model to decide actions, but does not build the model itself.
- Actuation feedback is not a formally defined stage of the perception-plan-act loop.

</details>

---

**Q7.** A robotics engineer integrates a reinforcement learning policy that adjusts a robotic arm's joint PID gains in real time based on sensed deviations. This is BEST described as:

A) Classical kinematics only
B) Pure proprioceptive sensing
C) AI augmenting classical control
D) Forward kinematics computation

<details>
<summary>Answer</summary>

**Correct: C**

Using a learned policy to adapt classical PID control parameters is a direct example of AI augmenting classical robotics control.

**Why the others are wrong:**
- Classical kinematics alone does not involve adaptive, learning-based parameter tuning.
- Sensing is involved, but the question targets the control-augmentation concept, not the sensing category.
- Forward kinematics is a position computation and is unrelated to PID gain tuning.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** What is the fundamental distinction between 'robotics' and 'AI' as tested on the exam?

A) Robotics is the engineering discipline combining perception, control, and actuation in physical systems; AI is the field of algorithms enabling decision-making/learning, which may or may not be embodied
B) Robotics refers only to software algorithms, AI refers only to hardware systems
C) Robotics and AI are synonymous terms used interchangeably
D) AI always requires a physical body, robotics does not

<details>
<summary>Answer</summary>

**Correct: A**

This reflects the standard definitional distinction: robotics covers physical sense-plan-act systems, while AI covers algorithms for intelligent behavior that need not be embodied.

**Why the others are wrong:**
- This reverses the actual roles of software/hardware in each field.
- The two fields are related but are distinct disciplines with different scopes.
- AI does not require physical embodiment — chatbots and recommendation systems are AI without a body.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

