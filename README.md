# 🤖 AI powered Quadruped

> A small, expressive ESP32-based robo-friend with voice interaction,
> animated face display, AI-powered responses, and a future
> quadruped body.

---

## 📖 Project Overview

AI powered Quadruped is a lightweight, expressive companion robot built around the
**ESP32-S3** microcontroller. The project combines embedded systems
engineering, voice interaction, AI-powered command processing, and
animated display output into a single cohesive platform.

The robot is designed in phases:

- **Phase 1:** Breadboard brain prototype with voice, face, and AI
- **Phase 2:** Head servo motion and speech-motion sync
- **Phase 3:** Cardboard quadruped body prototype
- **Phase 4:** 3D-printed chassis and polished build
- **Phase 5:** Dashboard app and advanced features

> This project is a personal hardware/embedded systems build.
> It is not a commercial product.

---

## 🎯 Goals

- Build a small, funny, expressive robot that feels alive
- Learn embedded systems, firmware, and hardware-software integration
- Create a modular, extensible embedded AI platform
- Target size: **30–40 cm max**
- Target personality: **funny, expressive, a little dramatic**

---

## 🔧 Hardware

### Current Hardware

| Component        | Part                     | Purpose                     |
| ---------------- | ------------------------ | --------------------------- |
| Main MCU         | ESP32-S3 (Freenove CAM)  | Brain, Wi-Fi, camera        |
| Secondary MCU    | Raspberry Pi Pico W      | Optional peripheral control |
| Microcontroller  | Arduino Nano V3.0        | Peripheral testing          |
| Microphone x2    | INMP441 (I2S)            | Voice input                 |
| Amplifier x2     | MAX98357 (I2S, 3W)       | Speaker output              |
| Display          | 1.8" TFT LCD 128x160 SPI | Face/status display         |
| Rotary Encoder   | EC11 360° with button    | Manual input / menu         |
| Keypad           | 4x4 matrix               | Debug / command input       |
| Breadboards      | SYB-170 mini x2          | Prototyping                 |
| Jumper wires     | 140-piece U-shape        | Connections                 |
| Resistors        | 300/600 piece 1% 1/4W    | Signal conditioning         |
| Tactile switches | 100-piece kit            | Input controls              |

### Planned Hardware (not yet acquired)

| Component                  | Purpose                         |
| -------------------------- | ------------------------------- |
| 8× servo motors            | Leg/head actuation              |
| Servo driver board         | Multi-servo PWM control         |
| IMU (MPU6050 or similar)   | Balance and orientation sensing |
| LiPo battery + BMS         | Portable power                  |
| Cardboard / acrylic / foam | V1 chassis prototype            |
| 3D printed parts           | Final chassis (Phase 4)         |

---

## 💻 Software Stack

| Layer              | Tech                                 |
| ------------------ | ------------------------------------ |
| Firmware           | C/C++ (ESP-IDF / Arduino framework)  |
| Audio pipeline     | I2S mic → ESP32 → Wi-Fi → backend    |
| Speech-to-text     | Cloud API (configurable)             |
| LLM                | API-based (configurable backend)     |
| Text-to-speech     | Cloud API → audio stream             |
| Display            | TFT SPI driver, custom face renderer |
| State machine      | Custom finite state machine          |
| Dashboard (future) | Web app (TBD)                        |

---

## 🤖 Robot States

| State       | Face              | LED          | Behavior                           |
| ----------- | ----------------- | ------------ | ---------------------------------- |
| `IDLE`      | Blinking eyes     | Soft glow    | Idle animations, occasional wiggle |
| `LISTENING` | Wide eyes         | Blue pulse   | Recording audio input              |
| `THINKING`  | Dots / loading    | Yellow pulse | Processing / API call              |
| `SPEAKING`  | Mouth animate     | White        | Playing TTS audio                  |
| `SLEEPING`  | Closed eyes       | Off / dim    | Low power, awaiting wake trigger   |
| `HAPPY`     | Happy face        | Green        | Triggered by command               |
| `CONFUSED`  | Tilted expression | Orange       | Unknown command                    |
| `ERROR`     | X eyes            | Red          | System error state                 |

---

## 🎮 Command Map

| Voice Command        | Action                          |
| -------------------- | ------------------------------- |
| "What is your name?" | Introduce self                  |
| "Tell me a joke"     | Random joke from LLM            |
| "How are you?"       | Random personality response     |
| "Go to sleep"        | Enter sleep mode                |
| "Wake up"            | Exit sleep mode                 |
| "Be happy"           | Switch to happy emotional state |
| "Be sad"             | Switch to sad emotional state   |
| "Status report"      | Report system status            |
| "Look left"          | Head pan servo left             |
| "Look right"         | Head pan servo right            |
| "Nod"                | Head tilt nod gesture           |
| "Dance"              | Perform dance routine           |
| "Take a picture"     | Capture image from ESP32-CAM    |

---

## 📐 Mechanical Specs (Target)

| Parameter | Target Value                   |
| --------- | ------------------------------ |
| Max size  | 30–40 cm                       |
| Legs      | 4                              |
| Servos    | 8 (2 per leg) + optional head  |
| Body      | Box frame with mounted brain   |
| Head      | Display face + optional camera |
| Weight    | As light as possible           |
| Power     | LiPo battery (portable)        |

---

## 🚀 Stretch Goals

| Feature                      | Priority |
| ---------------------------- | -------- |
| Wake word detection          | High     |
| Idle animations              | High     |
| ESP32-CAM visual reactions   | Medium   |
| Remote dashboard control     | Medium   |
| Touch sensor mood reactions  | Low      |
| Memory / personalization     | Low      |
| Autonomous wandering         | Low      |
| Multi-step scripted routines | Low      |

---

## 📄 License

MIT License — feel free to fork, modify, and build your own robo-friend.

---
