## Chapter 11: AI Ethics, Safety, and Policy in Robotics — Practice Questions

**Q1.** An autonomous mobile robot (AMR) in a warehouse fails to detect a pallet partially obscured in low light and collides with a shelving unit, injuring a nearby worker. Investigation shows the perception model's object-detection confidence drops significantly in low-light conditions but this was never tested before deployment. Which statement BEST describes the root safety failure?

A) The robot's emergency stop button was not pressed in time
B) The robot exceeded its rated payload capacity
C) The facility's Wi-Fi network experienced latency during the incident
D) An unvalidated perception model edge case created a physical safety gap that oversight processes failed to catch

<details>
<summary>Answer</summary>

**Correct: D**

The core failure is a perception-model limitation (low-light performance) that was not validated before deployment, directly causing a safety zone/collision-avoidance failure.

**Why the others are wrong:**
- Emergency stop is a reactive control, not the root cause of the detection failure itself
- Payload has nothing to do with perception-based collision avoidance
- Network latency is a plausible distractor but not indicated by the scenario facts given

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A company deploys a collaborative robot (cobot) to work directly alongside human operators on an assembly line, sharing the same workspace with no fencing, using continuous contact-force limiting instead of maintaining a minimum separation distance. Which safety approach does this describe?

A) Speed and Separation Monitoring (SSM)
B) Category 0 emergency stop
C) Power and Force Limiting (PFL)
D) Safety-rated monitored stop only

<details>
<summary>Answer</summary>

**Correct: C**

Power and Force Limiting (PFL), defined under ISO/TS 15066, allows direct human-robot contact by capping forces/pressures to biomechanically safe thresholds instead of relying on distance.

**Why the others are wrong:**
- SSM relies on maintaining dynamic minimum distance via sensors, which the scenario explicitly rules out
- Category 0 stop is an immediate power-removal response, not a collaborative operating mode
- A monitored stop halts motion but doesn't describe continuous shared-workspace contact operation

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A robot manufacturer sells a general-purpose robotic arm. A third-party integrator attaches a custom gripper and writes control software that bypasses a built-in safety interlock to speed up a task. The modified robot later injures an operator. Who bears PRIMARY liability?

A) The manufacturer, because they built the original robot
B) The operator, because they were physically present
C) The integrator, because they modified the safety-critical system and disabled a protective function
D) Liability cannot be determined without a court ruling in every case

<details>
<summary>Answer</summary>

**Correct: C**

Liability generally follows the party that introduced the defect — here the integrator modified the system and disabled a safety interlock, making them primarily responsible under standard product liability allocation principles.

**Why the others are wrong:**
- The manufacturer's original product was compliant; liability shifts once a third party alters safety-critical functions
- The operator did not cause the defect and had no knowledge of the bypassed interlock
- While courts make final determinations, exam-level liability allocation principles are well-defined by role and causal action

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A company is selecting a safety standard for a new collaborative robot that will share workspace with humans without fencing. Which standard is the MOST directly applicable?

A) ISO/TS 15066 (collaborative robot safety)
B) ISO 10218 (industrial robot safety, general)
C) ISO 13482 (personal care robots)
D) IEC 61508 (generic functional safety only)

<details>
<summary>Answer</summary>

**Correct: A**

ISO/TS 15066 specifically extends ISO 10218 with collaborative operation requirements (SSM, PFL, hand-guiding, simultaneous motion) for human-robot shared workspaces.

**Why the others are wrong:**
- ISO 10218 covers general industrial robot safety but does not define collaborative operation thresholds
- ISO 13482 applies to personal care robots (e.g., assistive/mobility robots), not industrial cobots
- IEC 61508 is a generic functional safety standard underlying others but is not robot-specific

</details>

---

**Q5.** A safety engineer must choose between a Category 0 stop and a Category 1 stop (per IEC 60204-1) for a robot arm's emergency stop function. The application requires the arm to decelerate under control before power is removed, to avoid damaging a sensitive workpiece during stop. Which should be selected?

A) Category 0 stop
B) Category 2 stop
C) No stop category is needed if a light curtain is present
D) Category 1 stop

<details>
<summary>Answer</summary>

**Correct: D**

Category 1 stop provides a controlled deceleration before power removal, matching the requirement to stop safely without abrupt loss of motor control.

**Why the others are wrong:**
- Category 0 removes power immediately with no controlled deceleration, which could damage the workpiece or cause uncontrolled arm drop
- Category 2 maintains power to drives after stopping, which is not a true emergency stop behavior and is used for operational stops, not E-stops
- A light curtain is a sensing device, not a substitute for a defined stop category

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** For a robot's safety-related stop function, a risk assessment per ISO 13849-1 determines the function must mitigate severe, irreversible injury with high exposure and low probability of avoidance. Which Performance Level (PL) should this safety function target?

A) PLa
B) PLe
C) PLb
D) PLd

<details>
<summary>Answer</summary>

**Correct: B**

PLe is the highest performance level under ISO 13849-1, reserved for scenarios involving severe/irreversible injury, high exposure, and low avoidance probability.

**Why the others are wrong:**
- PLa is for the lowest risk scenarios (minor, reversible injury)
- PLb covers low-to-moderate risk, insufficient for severe irreversible injury scenarios
- PLd is commonly used for serious injury risk but is below PLe, which is required when avoidance probability is low and exposure is high

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A perception system responsible for detecting humans in a robot's safety zone must meet a Safety Integrity Level (SIL) under IEC 61508. The system is safety-critical and failure could directly cause severe injury in frequent operating scenarios. Which SIL rating is MOST appropriate for this function?

A) SIL 2 or SIL 3
B) SIL 0
C) SIL 1
D) SIL 4, the maximum, for all robotics perception systems

<details>
<summary>Answer</summary>

**Correct: A**

SIL 2–SIL 3 is the typical range for safety-critical industrial robotics functions with significant injury risk; SIL 4 is reserved for extremely high-risk systems like nuclear or rail, not typical robotic perception zones.

**Why the others are wrong:**
- SIL 0 implies no safety integrity requirement, inappropriate for a safety-critical detection function
- SIL 1 is too low for a function whose failure directly causes severe injury
- SIL 4 is reserved for the highest-consequence systems and is not the default/typical requirement for robotics perception; claiming it applies to 'all' systems is an overgeneralization

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q8.** Which statement correctly distinguishes 'human-in-the-loop' (HITL) from 'human-on-the-loop' (HOTL) oversight models for autonomous robots?

A) HITL and HOTL are interchangeable terms for the same oversight model
B) HITL means no human is involved; HOTL means a human performs every task manually
C) HOTL requires more human involvement than HITL in all cases
D) HITL requires a human to approve each action before execution; HOTL allows the robot to act autonomously while a human monitors and can intervene

<details>
<summary>Answer</summary>

**Correct: D**

HITL requires human approval before action execution (human is part of the decision cycle), while HOTL permits autonomous action with human supervisory monitoring and intervention capability, not prior approval.

**Why the others are wrong:**
- The terms describe meaningfully different levels of human involvement and are not interchangeable
- HITL does involve a human; this option describes 'human-out-of-the-loop' instead
- HOTL generally involves LESS direct involvement than HITL since the robot acts independently between interventions

</details>

---

