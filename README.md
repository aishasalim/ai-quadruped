# Robo-Friend: ESP32 Voice-Interactive Quadruped Brain

A small, expressive embedded robot platform built around an **ESP32-S3**, designed as a lightweight **voice-interactive robo-friend**. The project combines **audio input/output**, **face animation**, **Wi-Fi-connected AI responses**, and **servo-driven motion** as the control stack for a future quadruped robot.

This project starts as a **breadboard-based robot brain** and grows in stages:

1. **Voice + face + AI interaction**
2. **Head/servo motion**
3. **Cardboard quadruped prototype**
4. **3D-printed lightweight body**
5. **Dashboard app for control, calibration, and behavior management**

---

## Project Goals

- Build a compact **robot brain** on breadboard using an **ESP32-S3**
- Support **button-triggered voice interaction**, then later **wake word / name activation**
- Create an expressive **animated face UI** on a small TFT screen
- Integrate **AI-backed conversational responses** over Wi-Fi
- Add **servo-based gestures** and eventually synchronized body movement
- Prototype a **small quadruped robo-friend** with a target size of **30–40 cm max**
- Keep the robot **lightweight, playful, and personality-driven** rather than utility-focused

---

## Current Vision

The robot is intentionally designed as a **fun companion robot**, not a serious industrial platform.

Planned physical form:

- 4 legs
- 8 servos
- small head
- face display
- compact electronics box (“brains”)
- expressive voice + movement

The goal is for it to feel like a **robo friend**:

- listens when asked
- responds with speech
- shows emotion on its face
- reacts with head/body gestures
- can eventually walk, wiggle, greet, and “perform”

---

## Planned Features

### Core Interaction

- Push-button speech activation
- Wake-word / name activation
- Microphone input
- Text-to-speech output
- AI-generated conversational responses
- Local command handling for safe robot actions

### Expression

- Animated TFT face
- Emotional states:
  - idle
  - listening
  - thinking
  - speaking
  - sleepy
  - excited
  - confused
- Idle animations (blink, look around, etc.)

### Motion

- Head servo gestures
- Speech-motion synchronization
- Safe predefined action routines
- Later: 8-servo quadruped movement

### Intelligence

- Wi-Fi-based AI response pipeline
- Personality / behavior modes
- Command-to-action mapping
- Future camera-based reactions with ESP32-S3 CAM

### Long-Term

- Cardboard quadruped prototype
- 3D-printed body
- Dashboard app for:
  - servo calibration
  - command control
  - behavior mode switching
  - system status

---

## Hardware

### Main Controller

- **ESP32-S3** (primary robot controller)

### Available Components

- Raspberry Pi 4B (optional future support)
- Freenove ESP32-S3 CAM module
- Raspberry Pi Pico W
- Arduino Nano V3.0
- Arduino UNO R3
- 1.8" TFT LCD (128x160 SPI)
- INMP441 I2S microphone modules
- MAX98357 I2S amplifier breakout boards
- Rotary encoder
- 4x4 keypad
- Potentiometers
- Tactile switches
- DIP switches
- Breadboards, resistors, jumper wires

### Planned Additional Parts

- Servos
- Servo power distribution hardware
- Battery / external power supply
- Mechanical frame materials
- Cardboard prototype body
- Later: 3D-printed chassis parts

---

## System Architecture

### High-Level Flow

1. User activates robot by **button** (later wake word)
2. Robot enters **listening** mode
3. Audio is captured through microphone
4. ESP32 sends request over **Wi-Fi** to backend / AI service
5. Response is returned as:
   - interpreted command and/or
   - conversational response
6. Robot:
   - speaks reply
   - updates face expression
   - triggers safe motion routine if needed

### Control Philosophy

AI does **not** directly control raw motor values.

Instead:

- AI / command parser selects **safe predefined actions**
- embedded controller executes validated routines such as:
  - `nod`
  - `look_left`
  - `look_right`
  - `greet`
  - `sleep`
  - `happy_wiggle`

This keeps behavior safer, more debuggable, and easier to extend.

---

## Development Roadmap

### Phase 1 — Brain MVP

- ESP32 setup
- TFT face states
- push-button activation
- speaker output
- microphone input
- Wi-Fi communication
- simple AI response loop

### Phase 2 — Personality Layer

- emotional state machine
- local command routing
- expressive face behaviors
- idle animations
- character/personality tuning

### Phase 3 — Motion Starter

- first servo experiments
- head pan / tilt
- gesture routines
- speech-motion sync

### Phase 4 — Cardboard Quadruped

- lightweight body prototype
- 8-servo leg system
- basic movement routines
- verbal + movement interaction

### Phase 5 — Full Prototype Upgrade

- 3D-printed body
- cleaner packaging
- dashboard app
- camera integration
- servo calibration tools

---

## Repository Structure

```text
robo-friend/
├── firmware/            # ESP32 firmware
├── docs/                # diagrams, notes, roadmap, debugging logs
├── hardware/            # wiring notes, BOM, pinouts
├── assets/              # face animations, sounds, icons
├── dashboard/           # future control/dashboard app
├── demos/               # videos, screenshots, test captures
└── README.md
```
