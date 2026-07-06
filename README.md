# Hi, I'm Barry Wu 👋

Final-year Electrical Engineering student at the National University of Singapore.
I build robot software — computer vision, autonomous navigation, and the embedded systems underneath them.

- 🤖 Computer Vision developer, **NUS RoboMaster** (RMUC 2026 season)
- 🎓 FYP: Adaptive Visual Enhancement for Object Detection via Deep Reinforcement Learning
- 📖 **[The full story of how I got here → JOURNEY.md](JOURNEY.md)**
- 📫 [barrywu5558@gmail.com](mailto:barrywu5558@gmail.com) · [LinkedIn](https://www.linkedin.com/in/barry-wu-314pi)

## The short version

**2025 — learned the stack from zero.** Built an "aimbot trainer" test rig with a friend:
STM32 + PID control of GM6020 gimbal motors, YOLOv8 detection on a RealSense + laptop,
then migrated to a Jetson Orin AGX + Hikrobot industrial camera with UART comms and
Kalman-filter target prediction.

**2026 — made it competition-grade.** On the NUS RoboMaster CV team: YOLOv11, particle
filter → extended Kalman filter, prediction and tracking of armor plates on real moving
robots, USB comms.

**Now — pushing detection further (FYP).** ROI-guided detection and a reinforcement-learning
feedback loop to improve detection rates without a bigger model.

[Read the full journey with reflections →](JOURNEY.md)

## Projects

| Project | What it is | Stack |
|---|---|---|
| [RoboMaster CV — RMUC 2026](https://github.com/nusrobomaster/RMUC_CV_2026_CPP) | Auto-aim vision pipeline for NUS RoboMaster's competition robots. My work: armor-plate pose estimation (solvePnP), yaw smoothing for gimbal control, camera intrinsics calibration. | C++, OpenCV, CUDA |
| FYP — Adaptive Visual Enhancement for Object Detection via Deep RL | Increasing real-time detection rates via ROI-guided inference with a reinforcement-learning feedback loop. *(writeup coming — code availability depends on university policy)* | Python, PyTorch |
| [Autonomous robots — EE4308](https://github.com/Javachipsfrappe/ee4308_project1) | A* path planning and a controller on a TurtleBot, plus drone simulation. NUS Autonomous Robot Systems. | Python, C++, ROS 2, Gazebo |
| [ESP32 Smart Vase](https://github.com/Javachipsfrappe/esp32-vase) | Personal hardware project: custom KiCad PCB (ESP32, regulated battery power, level-shifted NeoPixel driver) + firmware with multi-mode lighting and one-button UX. | KiCad, C++ (Arduino) |
