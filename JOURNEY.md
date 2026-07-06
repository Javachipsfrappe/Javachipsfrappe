<!--
Reflection prompts are marked [REFLECT: …] — replace each with 2–4 honest sentences
in your own words, then delete the prompt. Add photos/GIFs to assets/ and update the
image paths.
-->

# My robotics journey

How I went from never having touched a gimbal motor to building the vision pipeline
for NUS RoboMaster's competition robots — and where I'm taking it next.

---

## 2025 — The Aimbot Trainer: learning the whole stack

To learn robot auto-aim from first principles, I asked a mechanical-engineering friend
to build a test rig — a gimbal turret we called the **Aimbot Trainer** — and used it
to teach myself every layer of the stack:

<!-- ![Aimbot Trainer rig](assets/aimbot-trainer.jpg) — add the best photo/GIF from your Notion page -->

**Motor control.** GM6020 gimbal motors driven from an STM32, controlled with an RC
remote. This is where I learned embedded C, motor control protocols, and PID tuning.

> [REFLECT: what was hardest about PID tuning? What did a badly tuned loop look like
> physically — oscillation, overshoot? What finally made it click?]

**First vision pipeline.** Intel RealSense + laptop running YOLOv8 for detection.

**Migrating to real hardware.** Rebuilt the pipeline on a Jetson **Orin AGX** with a
**Hikrobot industrial camera** — the hardware competition robots actually run.

> [REFLECT: what broke when you moved from laptop+RealSense to Orin+Hikrobot?
> Driver issues, latency, camera triggering? What did you learn about deploying
> on embedded GPUs?]

**Closing the loop.** UART communication from the Orin to the STM32, so detections
actually drove the gimbal. Added target prediction with a **Kalman filter**,
building on [nusrobomaster/yolov8](https://github.com/nusrobomaster/yolov8).

---

## 2026 — RMUC season: making it competition-grade

The next season, on the [NUS RoboMaster CV team](https://github.com/nusrobomaster/RMUC_CV_2026_CPP),
we studied open-source work from other RoboMaster teams and rebuilt for competition:

- **YOLOv8 → YOLOv11** for detection
- **Particle filter → extended Kalman filter** for target state estimation
- **Prediction and tracking of armor plates on actual moving robots** — not a static rig
- **UART → USB** communication

My direct contributions include armor-plate pose estimation (solvePnP), yaw smoothing
for gimbal control, and camera intrinsics calibration
([commit](https://github.com/nusrobomaster/RMUC_CV_2026_CPP/commit/e7e0fe0)).

<!-- ![Tracking demo](assets/tracking-demo.gif) — THE key asset: 10–20 s clip of detection + tracking on a real robot -->

> [REFLECT: why did the particle filter lose to the EKF — compute cost, tuning,
> accuracy? What's different about tracking a real spinning robot vs. the static
> trainer?]

---

## Now — FYP: a different angle on detection

My final-year project takes another approach to making detection better, rather
than just running a bigger model:

- **ROI-guided detection** — increase detection rates by focusing compute where targets are
- **Reinforcement learning** to improve detection over time
- **A feedback loop** connecting tracking results back into detection

> [REFLECT: what's the hypothesis? E.g. "small-target detection fails at long range;
> an ROI policy can recover X% recall at the same FPS." State the measurable goal.]

---

## Also along the way

**EE4308 — Autonomous Robot Systems** ([repo](https://github.com/Javachipsfrappe/ee4308_project1)):
A* path planning and a trajectory controller on a TurtleBot, plus drone simulation.

**ESP32 Smart Vase** ([repo](https://github.com/Javachipsfrappe/esp32-vase)): a personal
hardware project — custom KiCad PCB around an ESP32 with regulated battery power and a
level-shifted NeoPixel driver, plus firmware with four lighting modes and a
debounced single/double-click button interface.

---

*Contact: [barrywu5558@gmail.com](mailto:barrywu5558@gmail.com) ·
[LinkedIn](https://www.linkedin.com/in/barry-wu-314pi)*
