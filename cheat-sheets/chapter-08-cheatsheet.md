## Chapter 8 Cheat Sheet: Applied Robotics Use-Cases

### Robot Class Quick-Match
| Scenario Signal | Robot Class |
|---|---|
| High payload, high speed, humans excluded | Industrial robot (caged) |
| Low-medium payload, shared workspace, no fencing | Cobot (PFL + SSM) |
| Dynamic warehouse, changing layout, obstacle avoidance | AMR (SLAM) |
| Fixed repetitive route, stable layout | AGV (guidepath) |
| Direct surgeon control, tremor filtering | Surgical teleoperated robot |
| Occupied space, pathogen reduction | UV-C disinfection robot (needs presence sensors) |
| Public-facing, guest/customer interaction | Service robot (hospitality/retail) |

### AGV vs AMR
| Feature | AGV | AMR |
|---|---|---|
| Navigation | Fixed guidepath (tape/wire/magnets) | SLAM, dynamic mapping |
| Layout change cost | High (re-infrastructure) | Low (software re-map) |
| Obstacle handling | Stops / cannot reroute | Reroutes dynamically |
| Best for | Stable, repetitive routes | Variable, shared-space environments |

### Industrial Robot vs Cobot
| Feature | Industrial Robot | Cobot |
|---|---|---|
| Guarding | Required (fencing/light curtains) | Often none (PFL/SSM) |
| Payload | Up to 1,000kg+ | ~3–20kg (some to ~35kg) |
| Speed | Full speed | Limited near humans |
| Safety standard | ISO 10218-1 | ISO 10218-2 + ISO/TS 15066 |
| Deployment cost/speed | Higher cost, slower redeploy | Lower cost, fast redeploy |

### Safety Standards Reference
| Standard | Covers |
|---|---|
| ISO 10218-1/-2 | Industrial robot and robot-system safety requirements |
| ISO/TS 15066 | Cobot biomechanical force/pressure limits (PFL) |
| ISO 13849 | Safety-related control system performance levels (PLd/PLe) |
| IEC 61508 | General functional safety (electrical/electronic systems) |

### Healthcare & Service Robotics Constraints
- Surgical robots: master-slave teleoperation, tremor filtering, motion scaling — NOT fully autonomous (regulatory requirement).
- Disinfection robots: mandatory occupancy/presence detection to disable UV-C near humans.
- Delivery robots: need elevator/building-system integration for multi-floor autonomy.
- Service robots (hospitality/retail): optimized for human interaction and unstructured public navigation, lower payload than industrial class.

### ROI & Deployment Checklist
- Cobots: lower upfront cost, faster changeover, better ROI for small-batch/variable production.
- Industrial cells: higher upfront cost (fencing, engineering), better ROI at high-volume, stable, high-speed tasks.
- AMR fleets: require Fleet Management System (FMS) for task allocation and traffic control — factor integration cost into ROI.

### Common Exam Traps
- Picking AGV for a dynamic/obstacle-rich environment (should be AMR).
- Assuming cobots can match industrial robot speed/payload (they can't — safety-limited).
- Choosing 'fully autonomous' for surgical robot questions (current standard = surgeon-controlled teleoperation).
- Forgetting mandatory human-presence sensors for UV-C robots in occupied spaces.
