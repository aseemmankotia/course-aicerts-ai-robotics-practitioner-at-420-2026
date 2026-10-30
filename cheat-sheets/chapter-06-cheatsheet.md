## Chapter 6 Cheat Sheet — Generative AI for Robotic Creativity
**Domain:** Generative AI and NLP for Human-Robot Interaction (9%)

### Heavily Tested Areas
| Area | What the exam checks |
|---|---|
| Generative use-cases in robot design/creativity | Can you pick the right generative technique for morphology, motion, or planning tasks |
| Synthetic training data | Know diffusion models + domain randomization for scalable labeled data |
| Foundation models as building blocks | Know fine-tuning vs training-from-scratch tradeoffs |

### Application → Technique Map
| Goal | Technique | Notes |
|---|---|---|
| Explore novel robot bodies | Generative/evolutionary design search | Targets structure, not motion |
| Generate labeled training images | Diffusion model + domain randomization | Reduces manual data collection |
| Generate movement from language | Text-to-motion / text-to-trajectory | Must pass feasibility checks |
| Reuse skills across robots/tasks | Foundation model fine-tuning (e.g., VLA) | Avoids training from scratch |
| Sequence multi-step actions | Generative task planner (LLM-based) | Must validate against world/physics model |

### Diffusion Models vs GANs
| Model | Strength | Weakness |
|---|---|---|
| Diffusion | High fidelity, stable training | Slower sampling |
| GAN | Fast generation | Mode collapse risk |

### Risk: Generative Hallucination
- Definition: confident but physically unsafe/incorrect generated action or plan.
- Mitigation stack: constraint/safety checker → simulation validation → human-in-the-loop (HITL) review → execution.
- Exam trap: assuming a foundation model's fluent/confident output is automatically safe — it is not.

### Foundation Models as Building Blocks
- Pretrained broadly (vision + language + action) → reusable across robots/tasks.
- Correct path: fine-tune on task-specific data, NOT retrain from scratch.
- VLA (Vision-Language-Action) models are the canonical exam example.

### Human-in-the-Loop (HITL) Checklist
1. Generated robot design → engineering/safety review before manufacturing.
2. Generated trajectory/plan → feasibility + safety check before execution.
3. Never skip HITL because a model is "foundation-scale" — scale ≠ safety guarantee.

### Common Exam Traps
- Confusing text-to-motion (movement) with generative design (structure/morphology).
- Assuming synthetic data alone (without domain randomization) is sufficient for sim-to-real transfer.
- Treating model confidence scores as a substitute for a safety constraint checker.
- Choosing "train from scratch" over "fine-tune a foundation model" when a reusable pretrained model is available.
