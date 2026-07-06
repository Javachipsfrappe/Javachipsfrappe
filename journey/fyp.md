<!--
Generated from the FYP repo (private) — README + commit history.
Barry: verify the "why" claims and add measured results when benchmarks are final.
-->

# FYP journey — Adaptive Visual Enhancement for Object Detection via Deep RL

**NUS EE4002R Final Year Project** · Department of Electrical and Computer Engineering
*(repo private pending university policy — code available on request)*

---

## The problem

Two seasons of [RoboMaster CV work](robomaster.md) kept hitting the same wall:
a detector with **static parameters** is always wrong somewhere. A confidence
threshold tuned for clean, close-range footage misses occluded or motion-blurred
plates; loosen it and false positives leak through when the scene is easy.
Same with the region of interest: full-frame inference wastes compute when the
target is small and far — exactly when you'd rather spend those pixels zoomed in.

The usual answer is a bigger model. My FYP asks a different question:
**can the pipeline learn to adjust itself?**

## The approach

I forked the team's detection pipeline (December 2025) as a validated starting
point rather than rebuilding a detector from scratch, and added a control layer:

```
Camera → YOLOv11-Pose (4-keypoint armor detection)
       → EKF tracker [cx, cy, vx, vy]  (temporal smoothing + stability score)
       → DRL agent (PPO): observes 7-D state, outputs [Δconf_threshold, Δroi_scale]
       → gimbal commands → STM32F4 over USB-CDC
```

A **PPO agent** (Stable-Baselines3, MLP policy) sits above the detector. Each
step it observes a 7-D summary of pipeline health — detection count, max/mean
confidence, track stability, miss rate, and its own current threshold and ROI
scale — and nudges the two knobs. The reward trades off detection quality
against misses and latency.

**Why these two knobs:** confidence threshold and ROI scale are the two
parameters whose "correct" value most obviously depends on scene state, and both
are adjustable at runtime with zero retraining of the detector.

**Why an EKF in the loop:** the agent needs a cheap, honest signal of whether
tracking is healthy. A 2-D constant-velocity EKF over the target centroid gives
temporal smoothing *and* a stability score that feeds the observation vector —
continuing the PF→EKF lesson from the team season.

**Why PPO:** the action space is continuous, the environment is noisy and
non-stationary, and PPO is the boring, stable choice that doesn't fall over
when the reward is dense but jittery.

## Sim-first, hardware-ready (April 2026)

The pipeline runs against a **Gymnasium environment** built from recorded
competition footage, so the agent trains without a robot
(`Add DRL adaptive detection pipeline (sim + hardware abstraction)`, 2026-04-17).
A **hardware abstraction layer** — abstract camera and serial interfaces with
sim implementations (video file / logging serial) and real ones (Hikrobot SDK /
STM32F4 USB-CDC) — means the trained agent deploys onto the physical gimbal by
swapping two constructor arguments, not rewriting the pipeline.

The benchmark suite logs per-step and per-episode metrics to CSV and generates
report figures comparing the **static-parameter baseline vs the DRL agent**
over matched episodes.

## Status

- [x] Full pipeline: detector, EKF tracker, PPO agent, sim environment, benchmarks
- [x] Hardware abstraction: sim camera/serial + Hikrobot/STM32 implementations
- [ ] Final benchmark numbers (baseline vs DRL) — in progress
- [ ] On-hardware validation on the gimbal rig

*The origin of all of this: [my RoboMaster journey](robomaster.md).*
