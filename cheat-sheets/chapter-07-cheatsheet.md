## Chapter 7 Cheat Sheet: NLP for Human-Robot Interaction
(Domain weight: 9% — heavily tested: instruction-to-action parsing, ASR→NLU→action pipeline, grounding/safety)

### Voice Command Pipeline (memorize order)
| Stage | Function | Input → Output |
|---|---|---|
| ASR | Speech recognition | Audio waveform → text transcript |
| NLU | Intent/entity extraction | Text → intent + slots + confidence score |
| Dialogue Mgmt | Context tracking, coreference, decision | Intent + history → next action (clarify/confirm/execute) |
| Action Planning | Grounds language into robot action | Resolved intent → executable action sequence |
| TTS | Speech synthesis | Text response → audio feedback |

**Exam trap:** Questions describing a pipeline failure (e.g., robot misunderstands a word) almost always test *which stage* failed. Mishearing = ASR. Wrong intent despite correct transcript = NLU. Wrong referent ('it') = Dialogue Management.

### The Grounding Problem
- Definition: mapping language symbols → physical referents/actions the robot can perceive/execute.
- Solved via: joint vision-language embeddings, scene graphs matching referring expressions to detected objects.
- NOT solved via: static dictionaries, keyword matching.
- Two grounding types tested: **perceptual grounding** (which object is 'the cup') and **capability grounding** (can the robot physically do this action).

### Ambiguity Resolution
| Trigger | Response |
|---|---|
| NLU confidence < threshold | Trigger clarification question |
| Multiple matching referents | Ask which one (e.g., "which block?") |
| Infeasible/ungrounded action | Reject or request alternative phrasing |

**Exam trap:** "Proceed with best guess" or "execute on first match" is always the wrong answer when ambiguity/low confidence is described.

### LLM-Driven Instruction Parsing
- LLMs translate natural language → structured action sequences (e.g., pick-place primitives, navigation goals).
- LLM output is **never executed directly** — must pass through a validation/guardrail layer.
- Guardrail layer checks: kinematic limits, collision/safety constraints, object-preservation policies, task feasibility.
- **Exam trap:** scenarios where literal instruction compliance causes harm (e.g., 'clean quickly' → throwing away valuables) test whether you flag the guardrail intervention as correct, not literal compliance.

### Conversational Interfaces for Collaboration
- Dialogue manager maintains multi-turn state (anaphora/coreference: 'it', 'that one').
- Clarification dialogues are a feature, not a failure — exam rewards systems that ask rather than guess.

### Safety Guardrails — Key Principle
LLM output → Guardrail/Validation Layer → Execution.
Never: LLM output → Execution (always wrong answer pattern).
Guardrails check: (1) kinematic/physical limits, (2) safety/collision constraints, (3) task/object policy compliance.

### Quick Memory Trick
**A-N-D-A-T**: ASR → NLU → Dialogue → Action → TTS — "AND Action Talks."
