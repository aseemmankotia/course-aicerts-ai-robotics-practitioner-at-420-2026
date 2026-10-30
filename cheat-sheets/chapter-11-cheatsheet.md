# Chapter 11 Cheat Sheet: AI Ethics, Safety, and Policy in Robotics

## Core Safety Standards
| Standard | Scope | Key Point |
|---|---|---|
| ISO 10218 (Parts 1 & 2) | General industrial robot safety | Manufacturer (Part 1) + integrator (Part 2) requirements |
| ISO/TS 15066 | Collaborative robots | Extends ISO 10218; defines PFL and SSM methods |
| ISO 13482 | Personal care robots | Non-industrial, assistive/mobility robots |
| IEC 61508 | Generic functional safety | Basis for SIL ratings (SIL 1–4) |
| ISO 13849-1 | Safety-related control systems | Performance Levels PLa (low) to PLe (high) |
| IEC 60204-1 | Electrical equipment of machines | Stop Categories 0, 1, 2 |
| EU Machinery Regulation 2023/1230 | EU machinery/robot safety law | Replaces Machinery Directive; covers AI-driven safety components |
| EU AI Act | AI system regulation | Classifies safety components of robots as high-risk AI |

## Stop Categories (IEC 60204-1)
- **Category 0**: Immediate power removal — uncontrolled stop. Used for true emergency stops.
- **Category 1**: Controlled deceleration, then power removed. Used when abrupt stop risks damage/injury.
- **Category 2**: Controlled stop, power maintained. NOT used for E-stop; used for operational stops.

## Collaborative Operation Methods (ISO/TS 15066)
- **SSM (Speed and Separation Monitoring)**: Maintain dynamic minimum distance; slow/stop as human approaches.
- **PFL (Power and Force Limiting)**: Allow direct contact; cap force/pressure per body region.
- **Hand-guiding**: Human physically guides robot motion directly.

## Risk → Rating Mapping
| Risk Severity | Exposure | Avoidance Probability | Typical PL | Typical SIL |
|---|---|---|---|---|
| Minor, reversible | Low | High | PLa–PLb | SIL 0–1 |
| Moderate | Moderate | Moderate | PLc | SIL 1–2 |
| Severe, irreversible | High | Low | PLd–PLe | SIL 2–3 |

(SIL 4 reserved for extreme-consequence domains like rail/nuclear — not typical for robotics.)

## Human Oversight Models
| Model | Human Role |
|---|---|
| Human-in-the-loop (HITL) | Approves each action before execution |
| Human-on-the-loop (HOTL) | Monitors autonomous action, can intervene |
| Human-out-of-the-loop | No active oversight during operation |

## Liability Allocation
- **Manufacturer**: design/build defects in the original product.
- **Integrator**: defects from system integration, custom end-effectors, modified safety logic.
- **Operator**: misuse, bypassing safeguards, inadequate maintenance.

## Bias in Perception Models — Safety Angle
Bias is a PHYSICAL safety issue when it causes uneven detection reliability (lighting, body size, skin tone, object type) across safety-critical zones — not only a fairness/ethics concern.

## Responsible Deployment Checklist
1. Validate perception models across edge cases (lighting, occlusion, demographics).
2. Define appropriate oversight model (HITL vs HOTL) based on autonomy risk.
3. Document liability chain across manufacturer/integrator/operator.
4. Ensure explainability of robot decisions for incident investigation.
5. Map safety functions to correct PL/SIL rating before deployment.
