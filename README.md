# Hi, I'm Barry Wu 👋

Final-year Electrical Engineering student at the National University of Singapore.
I build robot software — computer vision, autonomous navigation, and the embedded systems underneath them.

- 🤖 Computer Vision developer, **NUS RoboMaster** (RMUC 2026 season)
- 🎓 FYP: Adaptive Visual Enhancement for Object Detection via Deep Reinforcement Learning
- 📫 [barrywu5558@gmail.com](mailto:barrywu5558@gmail.com) · [LinkedIn](https://www.linkedin.com/in/barry-wu-314pi)

## My robotics journeys

**🎯 [RoboMaster CV, 2025 → 2026](journey/robomaster.md)**: from an "aimbot trainer"
rig (STM32 + PID + GM6020) to the competition pipeline: keypoint PnP, solving the
yaw-ambiguity problem with a constrained ternary search, Hikrobot integration,
camera calibration, and the Python → C++ port.

**🧠 [FYP: Adaptive Visual Enhancement via Deep RL](journey/fyp.md)**: a PPO agent
that tunes the detector's confidence threshold and ROI at runtime instead of using
a bigger model. Sim-trained on a Gymnasium environment, hardware-ready via an
abstraction layer down to the STM32.

**🤖 [EE4308: Autonomous Robot Systems](journey/ee4308.md)**: four commit-by-commit
iterations from vanilla pure pursuit to A* + Regulated Pure Pursuit with adaptive
lookahead, proximity/curvature velocity regulation, and PI heading control.

## Projects

| Project | What it is | Stack |
|---|---|---|
| [RoboMaster CV — RMUC 2026](https://github.com/nusrobomaster/RMUC_CV_2026_CPP) | Auto-aim vision pipeline for NUS RoboMaster's competition robots. My work: armor-plate pose estimation (solvePnP), yaw smoothing for gimbal control, camera intrinsics calibration. | C++, OpenCV, CUDA |
| FYP — Adaptive Visual Enhancement for Object Detection via Deep RL | Increasing real-time detection rates via ROI-guided inference with a reinforcement-learning feedback loop. *(writeup coming — code availability depends on university policy)* | Python, PyTorch |
| [Autonomous robots — EE4308](https://github.com/Javachipsfrappe/ee4308_project1) | A* path planning and a controller on a TurtleBot, plus drone simulation. NUS Autonomous Robot Systems. | Python, C++, ROS 2, Gazebo |
| [ESP32 Smart Vase](https://github.com/Javachipsfrappe/esp32-vase) | Personal hardware project: custom KiCad PCB (ESP32, regulated battery power, level-shifted NeoPixel driver) + firmware with multi-mode lighting and one-button UX. | KiCad, C++ (Arduino) |
