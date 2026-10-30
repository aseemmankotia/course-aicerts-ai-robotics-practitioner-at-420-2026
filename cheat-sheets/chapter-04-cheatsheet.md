# Chapter 4 Cheat Sheet: Deep Learning for Robotics

## Exam Domain Weight: 9%
Heavily tested: CNNs for object detection/perception, sensor fusion (camera/LiDAR/IMU), neural vs classical control.

## Perception Pipeline
Sensor input (camera/LiDAR/IMU) → preprocessing → CNN feature extraction → task head (detection/segmentation) → output consumed by planning/control.

## Object Detection Architectures
| Type | Example style | Speed | Accuracy | Best for |
|---|---|---|---|---|
| Single-stage | YOLO-style | Fast (one pass) | Good | Real-time, edge-constrained robots |
| Two-stage | Faster R-CNN style | Slower (proposal + classify) | Higher | Offline/accuracy-critical, more compute available |

**NMS (Non-Maximum Suppression):** Post-processing step removing duplicate overlapping boxes via IoU threshold. Overlapping boxes on one object → tune/apply NMS.

## Object Detection vs Semantic Segmentation
| Task | Output | Use case |
|---|---|---|
| Object detection | Bounding boxes + class | Identify discrete obstacles/objects |
| Semantic segmentation | Per-pixel class map | Free-space/drivable-area navigation |

## Sensor Fusion: Camera + LiDAR + IMU
| Sensor | Strength | Weakness | Typical rate behavior |
|---|---|---|---|
| Camera | Rich semantic detail | Fails in low light/glare | Moderate rate |
| LiDAR | Accurate range, light-independent | Lower rate, sparse, no color | Lower rate than IMU |
| IMU | Very high-rate motion sensing | Drifts over time without correction | High rate |

**Fusion pattern (exam favorite):** Kalman-family filter (EKF/UKF) — IMU **predicts** pose at high rate; LiDAR/camera **corrects** drift at lower rate. If one sensor degrades (e.g., camera in low light), fusion re-weights toward the remaining reliable sensors rather than discarding any sensor outright.

## Neural Control vs Classical Control
| Aspect | Classical (PID/LQR/MPC) | Neural Network Control |
|---|---|---|
| Basis | Fixed math formula on error | Learned state→action mapping from data |
| Interpretability | High | Low |
| Stability guarantees | Yes (well understood) | No formal guarantee |
| Latency/determinism | Deterministic, fast | Variable, inference overhead |
| Best use | Low-level, high-frequency safety-critical loops | Higher-level perception-informed behaviors |

PID formula: `output = Kp·e + Ki·∫e dt + Kd·de/dt`

**Exam rule of thumb:** Safety-critical, high-frequency, deterministic loop → classical control. Complex nonlinear perception-to-action mapping where data is available → neural approaches, but not for the core stabilizing loop.

## Transfer Learning for Robot Vision
- Start from a model pretrained on a large general dataset.
- Freeze early (generic) layers; fine-tune later layers/head on small robot-specific dataset.
- Use when labeled data is scarce (e.g., a few hundred images) to avoid overfitting that occurs when training from scratch on small datasets.

## Edge/Compute Constraints
- Robots run on power/thermal-constrained embedded compute, not datacenter GPUs.
- Favor lightweight single-stage detectors and smaller segmentation backbones to minimize inference latency for real-time obstacle avoidance.
- Trade-off is always: accuracy vs latency/compute/power — the exam will give constraints and ask you to pick the model/architecture that fits them, not the most accurate one in isolation.

## Common Exam Traps
1. Assuming 'neural network' is always better than classical control — wrong for safety-critical, high-frequency loops.
2. Confusing object detection (boxes) with semantic segmentation (pixel masks) for navigation/free-space tasks.
3. Discarding a sensor (e.g., IMU) during fusion when it degrades, instead of re-weighting it in the fusion filter.
