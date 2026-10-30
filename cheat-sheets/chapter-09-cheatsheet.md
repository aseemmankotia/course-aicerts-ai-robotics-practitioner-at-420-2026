# Chapter 9 Cheat Sheet: RPA (Domain Weight 8%)

## RPA vs Physical Robotics
| Aspect | RPA (Digital Robot) | Physical Robotics |
|---|---|---|
| Operates on | Software/UI, applications | Physical world, objects |
| Example task | Copy data between systems, fill forms | Pick/place parts, weld, assemble |
| Interaction method | Mimics clicks/keystrokes/screen reads | Motors, sensors, actuators |
| Exam trap | Choosing physical robot for a digital task (or vice versa) | Same |

## Attended vs Unattended Bots
| Feature | Attended | Unattended |
|---|---|---|
| Trigger | Human, on-demand | Schedule/system event |
| Runs on | User's desktop | Server/VM |
| Human present? | Yes | No |
| Typical use | Front-office (call center assist) | Back-office (batch reconciliation) |

## When to Use RPA vs AI vs Physical Automation
| Scenario Clue | Best Fit |
|---|---|
| Structured, repetitive, rule-based digital task, no API | RPA |
| Unstructured data (scanned docs, free text, images) | AI/ML first, then RPA for downstream steps |
| Task requires judgment, classification, prediction | AI/ML |
| Task requires physically moving/manipulating objects | Physical robot |
| Mix of unstructured input + repetitive digital workflow | Intelligent Automation (RPA + AI) |

## RPA + AI = Intelligent Automation / IDP
- AI/OCR/NLP extracts & interprets unstructured data.
- RPA bot executes the resulting structured digital workflow (data entry, routing, reconciliation).
- Exam keyword pairing: "scanned invoices" + "ERP entry" → Intelligent Automation / IDP, not pure RPA.

## RPA Limitations
- **UI Brittleness**: UI layout/element changes break bots relying on selectors.
- **No physical capability**: cannot manipulate real-world objects.
- **Limited reasoning**: cannot handle unstructured/judgment-based tasks without AI augmentation.
- **Maintenance overhead**: requires ongoing monitoring as target apps change.

## Bot Governance & Lifecycle
- Stages: Design → Develop → Test → Deploy → Monitor → Maintain → Decommission.
- Centralized governance (Center of Excellence) standardizes security, deployment, and monitoring practices.
- Credential management: use secure vaults, never hardcode credentials in bot scripts (especially for unattended bots).
- Change management: proactively track target-application UI/workflow changes to reduce brittleness-related failures.

## Exam Traps to Remember
1. Confusing RPA (software) with physical robots (hardware) — they are NOT interchangeable.
2. Assuming pure RPA can process unstructured documents without AI.
3. Picking "add more bot licenses" as the fix for UI brittleness instead of governance/monitoring.
4. Mixing up attended (human-triggered, desktop) vs unattended (scheduled, server-based) bot definitions.
