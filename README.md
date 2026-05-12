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

## 🧠 System Architecture

```
┌─────────────────────────────────────────────┐
│              ESP32-S3 (Main Brain)           │
│                                             │
│  ┌──────────┐  ┌──────────┐  ┌───────────┐ │
│  │  Audio   │  │  Display │  │  Wi-Fi    │ │
│  │  Input   │  │  (TFT)   │  │  (API)    │ │
│  │ (INMP441)│  │  Face UI │  │  Backend  │ │
│  └──────────┘  └──────────┘  └───────────┘ │
│                                             │
│  ┌──────────┐  ┌──────────┐  ┌───────────┐ │
│  │  Audio   │  │  Servo   │  │  Camera   │ │
│  │  Output  │  │  Control │  │ (ESP32-S3 │ │
│  │(MAX98357)│  │  (later) │  │   CAM)    │ │
│  └──────────┘  └──────────┘  └───────────┘ │
└─────────────────────────────────────────────┘
```

### Communication Flow

```
[Button / Wake Word]
        │
        ▼
[Microphone Input (INMP441)]
        │
        ▼
[ESP32-S3: Audio Capture + Wi-Fi Send]
        │
        ▼
[Backend: STT → LLM → TTS]
        │
        ▼
[ESP32-S3: Command Router + State Machine]
        │
     ┌──┴──┐
     ▼     ▼
[Face]  [Servo / Action]
[TFT]   [Speaker Output]
```

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

## 🗂️ Repository Structure

```
aria-robot/
├── firmware/
│   ├── main/
│   │   ├── main.cpp
│   │   ├── state_machine.cpp
│   │   ├── audio_input.cpp
│   │   ├── audio_output.cpp
│   │   ├── face_display.cpp
│   │   ├── wifi_client.cpp
│   │   └── servo_control.cpp
│   ├── include/
│   └── CMakeLists.txt
├── hardware/
│   ├── wiring_diagrams/
│   ├── bom.md
│   └── schematics/
├── dashboard/
│   └── (future web app)
├── docs/
│   ├── architecture.md
│   ├── state_machine.md
│   ├── wiring_guide.md
│   ├── roadmap.md
│   └── build_log.md
├── assets/
│   ├── face_sprites/
│   └── demo_videos/
└── README.md
```

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

## 📅 Build Roadmap

### Phase 1 — Brain MVP (Weeks 1–5)

- [x] Repo setup and architecture planning
- [ ] TFT display wiring and face rendering
- [ ] State machine implementation
- [ ] Audio output (MAX98357 + speaker)
- [ ] Push-to-talk microphone input
- [ ] Wi-Fi connected AI response loop

### Phase 2 — Personality + Motion (Weeks 6–9)

- [ ] Emotion state engine
- [ ] Local command router
- [ ] First servo integration (head pan/tilt)
- [ ] Speech-motion sync
- [ ] Wake word / name activation

### Phase 3 — Cardboard Body Prototype (Weeks 10–12)

- [ ] Mechanical layout and dimension planning
- [ ] Cardboard chassis build
- [ ] 8-servo quadruped integration
- [ ] Basic gait: stand, sit, shuffle, waggle
- [ ] Power supply planning

### Phase 4 — 3D Printed Body (Future)

- [ ] Redesign frame for 3D printing
- [ ] Clean wire routing
- [ ] Improved head/face mounting
- [ ] Weight/balance optimization

### Phase 5 — Dashboard App (Future)

- [ ] Web-based control dashboard
- [ ] Servo calibration interface
- [ ] Behavior/personality configuration
- [ ] OTA updates
- [ ] Camera feed viewer
- [ ] Command log

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

## 🐛 Build Log

### Week 1

- [ ] Setup complete
- [ ] Architecture diagram drafted

> See full build log in [`docs/build_log.md`](docs/build_log.md)

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

## 📸 Demo

> Demo videos and photos will be added as the project progresses.

---

## 🛠️ Setup

### Prerequisites

- ESP-IDF or Arduino framework for ESP32
- Python 3.x (for tooling scripts)
- Wi-Fi network
- Backend API credentials (STT / LLM / TTS)

### Flash Firmware

```bash
# Clone the repo
git clone https://github.com/aishasalim/aria-robot.git
cd aria-robot/firmware

# Build and flash (ESP-IDF)
idf.py build
idf.py -p /dev/ttyUSB0 flash monitor
```

### Configure Wi-Fi and API

```cpp
// firmware/include/config.h
#define WIFI_SSID     "your-network"
#define WIFI_PASSWORD "your-password"
#define API_ENDPOINT  "your-backend-url"
```

---

## 📄 License

MIT License — feel free to fork, modify, and build your own robo-friend.

---
