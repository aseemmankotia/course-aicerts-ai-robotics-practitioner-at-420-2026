## Chapter 6: Generative AI for Robotic Creativity — Practice Questions

**Q1.** A warehouse robotics team needs thousands of varied labeled images of objects on cluttered floors but cannot afford to physically stage and photograph every scenario. Which approach BEST meets this requirement?

A) Manually record additional real-world video footage for each scenario
B) Use a generative diffusion model combined with domain randomization to synthesize varied, labeled training images
C) Use a fixed-lighting CAD renderer that outputs the same scene repeatedly
D) Replace the perception pipeline with a text-to-speech module

<details>
<summary>Answer</summary>

**Correct: B**

Generative models paired with domain randomization produce large volumes of varied, realistic synthetic data cheaper and faster than manual capture, and improve sim-to-real robustness.

**Why the others are wrong:**
- Manual recording does not scale and is the exact cost problem being solved
- A fixed-lighting renderer with no variation fails to cover edge cases and is not generative
- Text-to-speech is unrelated to visual training data generation

</details>

---

**Q2.** A robot arm must handle novel objects it has never seen during training, and the team wants to avoid training a brand-new policy from scratch for every new object. What is the correct strategy?

A) Train a new policy from scratch for each new object
B) Hardcode fixed poses for every possible object
C) Replace the entire perception stack with a text-to-motion module
D) Fine-tune a pretrained vision-language-action foundation model on a smaller task-specific dataset

<details>
<summary>Answer</summary>

**Correct: D**

Foundation models encode broad, reusable priors from diverse demonstration data and can be fine-tuned efficiently for new objects/tasks, which is the core value of foundation models as building blocks.

**Why the others are wrong:**
- Training from scratch wastes time and data the foundation model already provides
- Hardcoding does not generalize to novel objects
- Text-to-motion addresses trajectory generation, not object perception/grasping generalization

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** During a simulation test, a generative task planner instructs the robot to grasp a hot pan with a bare manipulator because it 'looks safe' in the rendered scene. What does this illustrate?

A) Correct creative task planning that should be executed as-is
B) Expected, trustworthy foundation model behavior requiring no review
C) A successful example of sim-to-real transfer
D) Generative hallucination producing a physically unsafe action

<details>
<summary>Answer</summary>

**Correct: D**

The planner produced a confident but physically unsafe instruction not grounded in real-world hazards — the defining pattern of generative hallucination in physical actions.

**Why the others are wrong:**
- The plan is unsafe, not acceptable creative output
- Foundation model outputs still require safety validation, especially in novel/hazardous situations
- This is unrelated to sim-to-real transfer quality

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A design team wants to explore novel robot limb configurations and actuator placements before committing to a physical prototype. Which generative AI application is MOST appropriate?

A) Generative design exploration of robot morphology (e.g., evolutionary/generative structural search)
B) Text-to-speech synthesis for voice commands
C) A dialogue-based large language model agent
D) Text-to-motion trajectory generation

<details>
<summary>Answer</summary>

**Correct: A**

Generative design exploration targets the physical structure/morphology search space, which is exactly the stated requirement.

**Why the others are wrong:**
- Text-to-speech has no relation to physical structure design
- A dialogue LLM agent is for interaction, not morphology generation
- Text-to-motion generates movement, not body structure

</details>

---

**Q5.** Which generative technique is conceptually used to produce continuous, physically plausible robot arm trajectories, analogous to how diffusion models generate images?

A) Simple linear interpolation between two fixed waypoints
B) Diffusion-based trajectory/motion generation
C) A static lookup table of pre-recorded motions
D) Rule-based PID control alone

<details>
<summary>Answer</summary>

**Correct: B**

Diffusion-based motion generation models learn to iteratively denoise noisy trajectory samples into smooth, physically plausible motion sequences, conceptually mirroring image diffusion.

**Why the others are wrong:**
- Linear interpolation is not generative and ignores learned motion priors
- A lookup table cannot generalize to novel situations
- PID control executes trajectories but does not generate novel ones

</details>

---

**Q6.** A generative design pipeline produces a new robot chassis geometry intended for manufacturing. Which step MUST occur before sending it to physical production?

A) Send the design directly to 3D printing to save time
B) Skip review because foundation models are inherently trustworthy
C) Perform human-in-the-loop engineering and safety review of the generated design
D) Only check the manufacturing cost estimate

<details>
<summary>Answer</summary>

**Correct: C**

Human-in-the-loop review is the required safeguard against structurally unsound or unsafe generated designs before physical commitment.

**Why the others are wrong:**
- Skipping review risks unsafe or non-functional hardware
- Foundation models can hallucinate and are not inherently trustworthy without validation
- Cost estimation alone does not verify structural or safety soundness

</details>

---

**Q7.** Which statement BEST describes the role of a foundation model in robot skill learning?

A) A single-task model trained exclusively on one robot's data that cannot transfer
B) A purely symbolic rule engine with no learned components
C) A legacy approach fully replaced by hardcoded control logic
D) A large pretrained model providing general-purpose, transferable skills that can be fine-tuned across robots and tasks

<details>
<summary>Answer</summary>

**Correct: D**

Foundation models are defined by broad pretraining that enables reuse and fine-tuning as building blocks across multiple robots and tasks.

**Why the others are wrong:**
- This describes a narrow task-specific model, the opposite of a foundation model
- Foundation models are learned, not symbolic rule engines
- Foundation models are a current, actively used approach, not deprecated

</details>

---

**Q8.** Which practice MOST directly reduces the risk of a generative model causing a physically unsafe or hallucinated robot action during deployment?

A) Routing generated actions through a safety/constraint checker with human-in-the-loop review before execution
B) Removing human oversight to speed up deployment
C) Trusting the model's self-reported confidence score alone
D) Disabling simulation-based testing before deployment

<details>
<summary>Answer</summary>

**Correct: A**

A constraint checker combined with human review filters hallucinated or unsafe outputs before they reach actuators, directly mitigating the risk.

**Why the others are wrong:**
- Removing oversight increases risk rather than reducing it
- Model confidence scores do not reliably reflect real-world physical safety
- Disabling simulation testing removes an important validation stage

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

