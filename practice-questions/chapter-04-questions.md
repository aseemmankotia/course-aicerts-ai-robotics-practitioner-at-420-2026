## Chapter 4: Deep Learning for Robotics — Practice Questions

**Q1.** A quadruped robot's joint controller must maintain stability at a 1 kHz control loop while a separate perception stack runs object detection at 15 Hz on the same onboard compute. Which architecture choice BEST meets the robot's safety and real-time requirements?

A) Keep a classical PID or model-based controller for joint-level control and run the neural network only in the perception pipeline
B) Replace the joint controller with a neural network trained end-to-end on joint torques
C) Run both control and perception on the same neural network to reduce compute overhead
D) Increase the control loop period to 15 Hz to match the perception stack

<details>
<summary>Answer</summary>

**Correct: A**

Classical controllers (PID, LQR, MPC) are deterministic, provably stable, and can execute reliably at kHz rates with negligible jitter — exactly what low-level joint stabilization requires. Deep learning perception runs orders of magnitude slower and is not deterministic, so it belongs in the higher-level perception/planning loop, not the safety-critical control loop.

**Why the others are wrong:**
- Neural controllers have no stability guarantees and inference latency/jitter at kHz rates is impractical on embedded compute — a known exam trap (students assume 'neural = better' everywhere)
- Combining control and perception into one network removes the determinism needed for joint stability and couples unrelated failure modes
- Slowing the control loop to match perception would destabilize the joint controller, which needs high-frequency feedback regardless of perception rate

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q2.** A warehouse AMR fuses a camera, a spinning LiDAR, and an IMU for localization and obstacle avoidance. The camera becomes unreliable in low-light aisles. Which design BEST preserves robot safety in this scenario?

A) Fuse LiDAR and IMU data with higher weighting when camera confidence drops, using a filter such as an Extended Kalman Filter
B) Disable all sensors except the camera and reduce robot speed
C) Discard the IMU since it only measures orientation, not obstacles
D) Switch entirely to a camera-only deep learning model trained on low-light images

<details>
<summary>Answer</summary>

**Correct: A**

Sensor fusion architectures (e.g., EKF/UKF) are designed to dynamically re-weight sensor inputs based on confidence/noise characteristics. LiDAR is largely illumination-independent and the IMU provides high-rate motion estimates, so down-weighting the degraded camera stream while leaning on LiDAR+IMU maintains safe operation.

**Why the others are wrong:**
- Relying solely on the degraded camera removes the robot's most reliable sensor in this condition and does not address the root problem
- The IMU contributes critical high-frequency pose/drift correction between LiDAR scans and should never be discarded in a fusion pipeline
- A camera-only model does not solve the fundamental sensing limitation in low light and ignores available LiDAR/IMU data

</details>

---

**Q3.** A delivery robot must run object detection on a power- and compute-constrained edge module (no discrete GPU, limited thermal budget) while maintaining near real-time perception for obstacle avoidance. Which detector design is the BEST fit?

A) A two-stage detector (e.g., Faster R-CNN style) for maximum accuracy regardless of latency
B) A single-stage detector (e.g., YOLO-style) optimized for a single forward pass, accepting a modest accuracy trade-off for lower latency
C) An ensemble of three different detection architectures voted together each frame
D) A detector that re-runs full-resolution inference on every pixel region independently

<details>
<summary>Answer</summary>

**Correct: B**

Single-stage detectors perform region proposal and classification in one pass, giving significantly lower latency and compute footprint — the right trade-off when edge compute/power/thermal budgets are limited and real-time obstacle avoidance matters more than marginal accuracy gains.

**Why the others are wrong:**
- Two-stage detectors (region proposal + classification) are more accurate but far more compute-intensive and slower, often infeasible on constrained edge hardware
- Ensembling multiplies compute and latency, the opposite of what a constrained edge module needs
- Independent per-region full-resolution inference (sliding window) is computationally prohibitive and was largely abandoned in favor of single-pass CNN detectors

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q4.** A robot navigating a hallway needs to identify which pixels correspond to drivable floor space versus walls and obstacles, not just detect discrete objects. Which perception task should the pipeline use?

A) Object detection with bounding boxes
B) Image classification of the whole frame
C) Semantic segmentation, classifying every pixel into a category such as 'floor' or 'obstacle'
D) Optical character recognition on surrounding signage

<details>
<summary>Answer</summary>

**Correct: C**

Semantic segmentation produces a per-pixel class label map, which directly yields a drivable-area mask needed for free-space navigation — bounding boxes from object detection don't describe continuous surfaces like floors.

**Why the others are wrong:**
- Bounding boxes localize discrete objects but cannot describe the irregular, continuous shape of a drivable floor region
- Whole-frame classification gives a single label for the entire image, not spatial information about where the floor is
- OCR is unrelated to free-space/navigation perception

</details>

---

**Q5.** An engineering team has only 300 labeled images of a new warehouse part but needs a robot vision model to recognize it reliably. Which approach is MOST appropriate given the limited data?

A) Use transfer learning: start from a model pretrained on a large dataset, freeze early layers, and fine-tune the later layers/head on the 300 images
B) Train a CNN from randomly initialized weights on the 300 images
C) Collect zero additional data and use a rule-based color filter instead of any neural network
D) Train a much larger, deeper network from scratch to compensate for limited data

<details>
<summary>Answer</summary>

**Correct: A**

Transfer learning reuses general low-level features (edges, textures) learned from large-scale pretraining and only fine-tunes higher layers for the new task, which performs well with small labeled datasets like 300 images — a core technique for robot vision tasks with limited data.

**Why the others are wrong:**
- Training from scratch on only 300 images leads to severe overfitting and poor generalization
- A hand-crafted color filter may work for trivial cases but doesn't generalize across lighting/pose variation the way a learned model does
- A larger from-scratch network needs even more data to avoid overfitting, making the data scarcity problem worse, not better

</details>

---

**Q6.** A robot fuses a 100+ Hz IMU with a 10 Hz LiDAR scan matcher for pose estimation. The IMU is high-rate but drifts over time; the LiDAR is accurate but slower and occasionally noisy. Which sensor fusion configuration is standard for this setup?

A) Average the IMU and LiDAR poses with equal, fixed weights at all times
B) Use the IMU alone and ignore LiDAR since it updates less frequently
C) Use a Kalman-family filter (e.g., EKF) that predicts pose from high-rate IMU integration and corrects drift using lower-rate LiDAR measurements
D) Use only LiDAR and discard IMU to avoid drift entirely

<details>
<summary>Answer</summary>

**Correct: C**

This predict-correct structure is the standard EKF/UKF fusion pattern: the IMU provides fast prediction between LiDAR updates, and LiDAR corrects accumulated IMU drift at its own (slower) rate — the canonical camera/LiDAR/IMU fusion design tested in robotics exams.

**Why the others are wrong:**
- Fixed equal weighting ignores each sensor's differing noise characteristics and update rates, producing poor estimates
- IMU-only estimation drifts unboundedly over time without a correcting sensor
- Discarding IMU loses the high-frequency motion information needed between LiDAR scans, increasing latency and reducing smoothness of pose estimates

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

**Q7.** An object detector on a robot is producing multiple overlapping bounding boxes for the same physical object. Which configuration step should be tuned to resolve this?

A) Increase the learning rate during inference
B) Decrease the input image resolution to zero
C) Apply or adjust the Non-Maximum Suppression (NMS) IoU threshold to suppress redundant overlapping boxes
D) Remove the classification head of the network entirely

<details>
<summary>Answer</summary>

**Correct: C**

Non-Maximum Suppression is the standard post-processing step in object detection pipelines that removes duplicate/overlapping boxes by keeping the highest-confidence box and suppressing others above an IoU overlap threshold.

**Why the others are wrong:**
- Learning rate is a training-time hyperparameter and has no effect during inference
- Reducing resolution to zero is nonsensical and would destroy the input entirely
- Removing the classification head would prevent the detector from identifying object classes at all

</details>

---

**Q8.** Which statement BEST describes the fundamental difference between classical PID control and neural network-based control for robots?

A) PID control uses a fixed, interpretable mathematical formula based on error, integral, and derivative terms, while neural control learns a mapping from states to actions from data and can model complex nonlinear behaviors without explicit equations
B) PID control learns from large datasets of demonstrations, while neural control uses fixed mathematical gains
C) Neural control always runs faster than PID control on embedded hardware
D) PID control and neural control are mathematically identical, differing only in naming

<details>
<summary>Answer</summary>

**Correct: A**

PID is a deterministic, interpretable control law (proportional + integral + derivative terms on error) with well-understood stability properties, while neural controllers learn an implicit state-to-action mapping from data, trading interpretability and guaranteed stability for the ability to capture complex nonlinear dynamics.

**Why the others are wrong:**
- This reverses the two approaches — PID uses fixed gains, not learned data; neural controllers are the ones trained on data
- Neural network inference is typically slower and less deterministic than evaluating a simple PID equation, making this false in general
- The two are fundamentally different paradigms (explicit control law vs. learned function approximator), not equivalent

> ⚠️ Frequently missed on the exam — read the options carefully.

</details>

---

