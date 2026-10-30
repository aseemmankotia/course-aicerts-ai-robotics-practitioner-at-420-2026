## Chapter 8: Applied Robotics: Practical Use-Cases — Practice Questions

**Q1.** A 3PL warehouse has daily-changing pallet layouts, new SKUs added weekly, and workers walking through aisles unpredictably. The facility needs mobile robots that can reroute around obstacles without repainting floor markers every time the layout changes. Which solution BEST meets these requirements?

A) AGVs following magnetic tape embedded in the floor
B) Fixed industrial robot arms on rail systems
C) AMRs using SLAM-based dynamic path planning
D) Collaborative robots mounted on static workstations

<details>
<summary>Answer</summary>

**Correct: C**

AMRs build and update a map in real time (SLAM) and replan paths around obstacles, so layout changes don't require re-engineering physical guidepaths.

**Why the others are wrong:**
- AGVs require fixed infrastructure (tape/wire/magnets) — any layout change means re-installing guidepaths, which doesn't fit a weekly-changing SKU environment.
- Fixed industrial arms on rails are for repetitive stationary tasks, not facility-wide material transport around dynamic obstacles.
- Cobots are stationary/near-stationary manipulators for close human interaction at a single task point, not mobile transport across a warehouse.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A hospital wants a robotic platform for minimally invasive procedures that gives the surgeon direct real-time control with tremor filtering and motion scaling, operating from a console a few feet from the patient. Which robot type is BEST suited?

A) An industrial 6-axis welding robot repurposed with a scalpel end effector
B) A master-slave teleoperated surgical robot system (e.g., da Vinci-class)
C) An autonomous mobile disinfection robot
D) A fully autonomous surgical robot requiring no surgeon input

<details>
<summary>Answer</summary>

**Correct: B**

Surgical assist robots use master-slave teleoperation: the surgeon controls the instruments directly via a console, with the system providing tremor filtering and motion scaling — this is the standard exam-tested architecture for surgical robotics.

**Why the others are wrong:**
- Industrial robots are not certified for sterile, high-precision human-body contact and lack the required safety/regulatory certification for surgery.
- Disinfection robots are autonomous navigation/UV-emission platforms, unrelated to surgical manipulation.
- Fully autonomous surgery without surgeon input is not the current regulatory-approved model and is a common wrong-answer distractor; current FDA-cleared surgical robots are surgeon-controlled, not fully autonomous.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** A factory needs to palletize 25kg boxes at high throughput (one box every 2 seconds) with no human workers in the immediate work cell. Which robot class is the correct choice?

A) A collaborative robot (cobot) with power and force limiting
B) An AMR with a robotic arm attachment
C) A service robot designed for hospitality tasks
D) A caged industrial robot arm with high payload and speed

<details>
<summary>Answer</summary>

**Correct: D**

High-speed, high-payload palletizing with no humans in the cell is the classic use case for caged industrial robots, which can run at full speed/payload without the force/speed restrictions required for human proximity.

**Why the others are wrong:**
- Cobots are deliberately speed- and force-limited for human safety, making them too slow for 1-box-per-2-second high-throughput palletizing.
- AMRs are for transport between locations, not fixed high-speed pick-and-place cycle work.
- Service robots are built for human interaction in public/retail/hospitality settings, not industrial payload handling.

</details>

---

**Q4.** A hotel wants a robot to deliver towels and amenities to guest rooms, interacting with guests in hallways and using elevators autonomously. Which robot category fits this use case?

A) Industrial robot arm
B) Service robot (hospitality-class) with building system integration
C) AGV on a fixed magnetic track
D) Welding robot with vision guidance

<details>
<summary>Answer</summary>

**Correct: B**

Hospitality service robots are designed for unstructured public-facing environments, human interaction, and integration with building systems like elevators — exactly this scenario.

**Why the others are wrong:**
- Industrial robot arms are stationary manipulators, not mobile delivery platforms.
- AGVs need fixed guidepaths and can't navigate dynamic hallways with guests and elevators.
- Welding robots are industrial manipulators for fabrication, completely unrelated to delivery tasks.

</details>

---

**Q5.** Which standard specifically defines the biomechanical force and pressure limits used to configure power and force limiting (PFL) on collaborative robots operating near humans?

A) ISO 9001
B) IEC 61508
C) ISO/TS 15066
D) ISO 13485

<details>
<summary>Answer</summary>

**Correct: C**

ISO/TS 15066 is the technical specification that extends ISO 10218 with biomechanical contact force/pressure limits by body region, used to set PFL thresholds on cobots.

**Why the others are wrong:**
- ISO 9001 is a general quality management system standard, unrelated to robot safety.
- IEC 61508 covers general functional safety of electrical/electronic systems, not robot-specific biomechanical limits.
- ISO 13485 is a quality management standard for medical devices, not robot safety classification.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q6.** An autonomous UV-C disinfection robot is deployed in hospital hallways that remain occupied during operating hours. What safety configuration is mandatory before activation?

A) GPS-based outdoor positioning
B) Human-presence/occupancy detection that disables UV emission when people are nearby
C) Facial recognition to identify hospital staff
D) A fixed operating schedule with no sensors required

<details>
<summary>Answer</summary>

**Correct: B**

UV-C disinfection robots must include presence/motion detection (and often fencing or interlocks) that automatically shuts off UV emission when a person enters the area, since UV-C exposure is harmful to skin and eyes.

**Why the others are wrong:**
- GPS is for outdoor positioning and offers no occupant safety function indoors.
- Facial recognition identifies individuals but does nothing to prevent UV exposure.
- A fixed schedule alone does not account for unplanned human presence and is an exam trap for 'set and forget' thinking.

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** A small bakery wants a robot to pack pastries into boxes on the same table where employees work, without installing safety fencing, at low speed and light payload (under 5kg). Which robot class is appropriate?

A) A caged high-speed industrial robot
B) An AGV following a floor-embedded wire
C) A surgical-grade teleoperated robot
D) A collaborative robot (cobot) with speed and separation monitoring

<details>
<summary>Answer</summary>

**Correct: D**

Low payload, shared workspace with humans, no fencing, and lower speed are the defining criteria for cobots, which use power/force limiting and speed-and-separation monitoring to operate safely near people.

**Why the others are wrong:**
- Caged industrial robots require fencing/light curtains, which contradicts the no-fencing requirement.
- AGVs are for material transport along fixed paths, not tabletop manipulation tasks.
- Surgical teleoperated robots are for medical procedures, an unrelated and implausible-for-context distractor.

</details>

---

**Q8.** What is the fundamental distinction between an industrial robot and a collaborative robot (cobot)?

A) Industrial robots use electric motors while cobots use hydraulic actuators
B) Cobots are always wireless while industrial robots require wired power
C) Industrial robots can only be programmed in Python while cobots use block-based programming
D) Industrial robots are designed for high speed/payload behind guarding; cobots are designed with power/force limiting to work safely alongside humans without full guarding

<details>
<summary>Answer</summary>

**Correct: D**

The core distinction tested on the exam is safety design intent: industrial robots assume no human proximity and rely on physical guarding for speed/payload, while cobots are engineered (via PFL, SSM) to operate directly alongside humans.

**Why the others are wrong:**
- Actuator type (electric vs hydraulic) is not the defining safety/classification distinction.
- Wireless vs wired power is not a defining characteristic of either robot class.
- Programming language choice is vendor-specific and not a classification criterion between robot types.

</details>

---

