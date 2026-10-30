## Chapter 7: NLP for Human-Robot Interaction — Practice Questions

**Q1.** A tabletop robot receives the voice command 'pick up the block' but two identical blocks are visible in its workspace. What should the system do?

A) Execute the grasp on whichever block is detected first by the vision system
B) Refuse the command entirely and end the interaction
C) Pick the block closest to the gripper without asking
D) Trigger a clarification dialogue asking the user which block they mean

<details>
<summary>Answer</summary>

**Correct: D**

Ambiguity in the referring expression means the grounding step cannot resolve a single referent; the dialogue manager must ask a clarifying question before acting.

**Why the others are wrong:**
- Acting on an arbitrary detection ignores unresolved ambiguity and risks wrong-object manipulation
- Refusing the command is overly conservative and not collaborative
- Assuming proximity is an unstated heuristic not confirmed by the user and may be wrong

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** An LLM generates a robot action plan that includes a joint trajectory violating the arm's kinematic limits. What is the correct system behavior?

A) Execute the plan because the LLM output is authoritative
B) Log the violation only after the motion completes
C) A safety guardrail layer validates the plan against kinematic and safety constraints and rejects or modifies it before execution
D) Permanently disable the LLM module

<details>
<summary>Answer</summary>

**Correct: C**

LLM-generated commands must pass through a validation/guardrail layer that checks feasibility and safety limits before any execution occurs.

**Why the others are wrong:**
- Treating LLM output as authoritative skips mandatory safety validation — a core exam trap
- Post-execution logging does not prevent physical damage or injury
- Disabling the LLM is an overreaction, not the standard mitigation pattern

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q3.** Which pipeline stage converts a raw audio waveform into a text transcript?

A) Natural Language Understanding (NLU)
B) Automatic Speech Recognition (ASR)
C) Dialogue Management
D) Text-to-Speech (TTS)

<details>
<summary>Answer</summary>

**Correct: B**

ASR performs the audio-to-text conversion; it is the first stage of the voice command pipeline.

**Why the others are wrong:**
- NLU operates on text to extract intent/entities, not raw audio
- Dialogue management handles conversation state, not audio transcription
- TTS performs the reverse operation, converting text to speech

</details>

---

**Q4.** The NLU module returns an intent classification confidence of 0.42, below the system's configured threshold of 0.6. What should the system do next?

A) Proceed with the best-guess intent
B) Shut down the interaction system
C) Trigger a clarification question to the user
D) Ignore the audio input and wait silently

<details>
<summary>Answer</summary>

**Correct: C**

Low-confidence intent classification should trigger a clarification dialogue rather than risk executing an incorrect action.

**Why the others are wrong:**
- Proceeding with a low-confidence guess risks incorrect or unsafe robot behavior
- Shutting down is disruptive and not the standard recovery mechanism
- Silently ignoring input provides no feedback loop for the user

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q5.** Which approach best solves the grounding problem of mapping the spoken word 'cup' to a specific physical object in the robot's camera view?

A) Look up 'cup' in a static dictionary of word definitions
B) Always require the human to physically point at the object
C) Default to selecting the object detected with the largest bounding box
D) Use a joint vision-language embedding to match the referring expression to a detected object in the scene

<details>
<summary>Answer</summary>

**Correct: D**

Grounding requires connecting linguistic symbols to perceptual data; joint vision-language embeddings align object detections with referring expressions.

**Why the others are wrong:**
- A dictionary definition provides no connection to the physical scene
- Requiring pointing is a fallback for failed grounding, not the primary technique
- Bounding box size is an arbitrary heuristic unrelated to the word's meaning

</details>

---

**Q6.** What is the 'grounding problem' in human-robot interaction?

A) Ensuring the robot's electrical chassis is properly grounded
B) The problem of a robot physically falling over
C) The challenge of connecting abstract language symbols to concrete physical referents and actions in the robot's environment
D) A network connectivity failure between robot and server

<details>
<summary>Answer</summary>

**Correct: C**

Grounding refers to mapping words and phrases to real objects, locations, and executable actions that the robot can perceive and act upon.

**Why the others are wrong:**
- Electrical grounding is an unrelated hardware/safety term that shares the word but not the concept
- Falling over is a balance/control issue, not a language issue
- Network connectivity is an infrastructure concern, not a language-to-world mapping problem

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** Which component is responsible for tracking conversational context, such as resolving 'it' or 'that one' across multiple turns with the robot?

A) Automatic Speech Recognition (ASR)
B) Dialogue management
C) Text-to-Speech (TTS)
D) The motor controller

<details>
<summary>Answer</summary>

**Correct: B**

Dialogue management maintains state across turns, including coreference resolution and deciding whether to ask for clarification or proceed to action.

**Why the others are wrong:**
- ASR only converts audio to text and has no memory of context
- TTS only produces spoken output and does not track state
- The motor controller executes physical motion, unrelated to language context

</details>

---

**Q8.** An LLM-driven robot is told to 'clean the kitchen quickly' and generates a plan that throws glass items into the trash to save time. What should the safety guardrail layer do?

A) Allow the plan since it technically satisfies the instruction to clean
B) Intervene and block the plan because it violates object-preservation and damage-avoidance constraints, even though it literally follows the instruction
C) Ask the human for approval only after the items are already thrown away
D) Proceed because the user emphasized doing the task quickly

<details>
<summary>Answer</summary>

**Correct: B**

Safety guardrails must catch literal but harmful interpretations of instructions, since LLMs can generate technically compliant but undesirable or damaging plans.

**Why the others are wrong:**
- Literal compliance does not guarantee safe or desirable behavior
- Approval after the fact does not prevent the damage
- Prioritizing speed over safety is exactly the failure mode guardrails are designed to catch

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

