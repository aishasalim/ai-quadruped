# 📅 Project Roadmap

This folder contains the full build roadmap for the AI-powered quadruped
robot, broken into 5 phases. Each phase has its own file with weekly
tasks, milestones, and demo goals.

> The roadmap is a living document. It will be updated as the project
> evolves, parts arrive, and priorities shift.

---

## 🗺️ Phase Overview

| Phase                                      | Name                     | Weeks | Status         |
| ------------------------------------------ | ------------------------ | ----- | -------------- |
| [Phase 1](./phase-1-brain-mvp.md)          | Brain MVP                | 1–5   | 🔄 In Progress |
| [Phase 2](./phase-2-personality-motion.md) | Personality + Motion     | 6–9   | ⏳ Planned     |
| [Phase 3](./phase-3-cardboard-body.md)     | Cardboard Body Prototype | 10–12 | ⏳ Planned     |
| [Phase 4](./phase-4-3d-print.md)           | 3D Printed Chassis       | TBD   | ⏳ Planned     |
| [Phase 5](./phase-5-dashboard.md)          | Dashboard App            | TBD   | ⏳ Planned     |

---

## 🎯 End Goal

A small (~30–40 cm), expressive, voice-enabled quadruped robot with:

- ESP32-S3 as the core embedded controller
- Voice input/output
- Animated face display
- Command-driven personality and emotional states
- Synchronized speech and movement
- 4 legs, 8 servos, lightweight chassis
- Web dashboard for control and configuration

---

## 🏁 Milestone Summary

### MVP — End of Phase 1

- [ ] Face display with animated states
- [ ] Push-to-talk voice input
- [ ] AI-powered voice responses
- [ ] Speaker audio output
- [ ] Core state machine working

### V1 — End of Phase 2

- [ ] Emotional state engine
- [ ] 1–2 head servos
- [ ] Speech-motion sync
- [ ] Wake word / name activation
- [ ] Idle animations

### V2 — End of Phase 3

- [ ] Cardboard quadruped body
- [ ] 8-servo walking prototype
- [ ] Synced verbal + movement routines
- [ ] Power supply figured out

### V3 — End of Phase 4

- [ ] 3D printed lightweight chassis
- [ ] Clean wire routing
- [ ] Polished face/head mount
- [ ] Stable locomotion

### V4 — End of Phase 5

- [ ] Web dashboard live
- [ ] Servo calibration UI
- [ ] Behavior configuration panel
- [ ] OTA updates
- [ ] Camera feed viewer

---

## 📦 Hardware Status

### Available Now

- ESP32-S3 (Freenove CAM)
- Raspberry Pi Pico W
- Arduino Nano V3.0
- INMP441 microphones x2
- MAX98357 amplifiers x2
- 1.8" TFT LCD display
- EC11 rotary encoder
- 4x4 keypad
- Breadboards, jumper wires, resistors, switches

### Still Needed

- 8× servo motors
- Servo driver board (PCA9685 or similar)
- IMU (MPU6050 or similar)
- LiPo battery + BMS
- Cardboard / foam for Phase 3 chassis
- 3D printed parts for Phase 4

---

## 📝 Notes

- Each phase file contains week-by-week tasks, milestones, and demo goals
- Progress is tracked with checkboxes inside each phase file
- Photos, wiring diagrams, and demo videos live in `assets/`
- Build log with weekly notes lives in `docs/build_log.md`
