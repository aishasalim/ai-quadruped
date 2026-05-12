# 🧠 Phase 1 — Brain MVP

> **Duration:** Weeks 1–5
> **Status:** 🔄 In Progress
> **Goal:** Build a working breadboard brain that can listen, think, and talk.

By the end of Phase 1, the robot should feel like a real interactive
system — even without a body. It should show a face, respond to button
presses, hear voice input, and speak back through a speaker.

---

## 🎯 Phase Goal

A desk-based robot brain that can:

- Show an animated face on the TFT display
- React to a button press
- Listen to a voice prompt
- Send audio/text to an AI backend via Wi-Fi
- Speak a response through the speaker
- Transition through visible states: idle → listening → thinking → speaking

---

## ✅ Week-by-Week Tasks

### Week 1 — Setup + Architecture

**Goal:** Get the development environment working and define the system
before building randomly.

#### Tasks

- [ ] Create GitHub repo and folder structure
- [ ] Flash ESP32-S3 and confirm toolchain works
- [ ] Draw system architecture diagram (v1)
- [ ] Define all hardware connections on paper before wiring
- [ ] Create this roadmap folder and all phase files
- [ ] Set up `docs/build_log.md`

#### Decisions to lock in this week

- [ ] Programming framework: ESP-IDF or Arduino?
- [ ] Audio pipeline: local capture or stream raw audio to backend?
- [ ] Backend: which STT / LLM / TTS services to use?
- [ ] Display library: TFT_eSPI or Adafruit GFX?

#### Milestone

ESP32-S3 boots, flashes cleanly, serial monitor works.

#### Demo Goal

30-second clip of the ESP32-S3 booting with "hello" printed to
serial monitor.

---

### Week 2 — Face + State Machine

**Goal:** Make it look like a robot before it talks.

#### Tasks

- [ ] Wire TFT display to ESP32-S3
- [ ] Get display working with a basic test image
- [ ] Draw first face assets:
  - [ ] Idle eyes (blinking)
  - [ ] Wide eyes (listening)
  - [ ] Loading dots (thinking)
  - [ ] Animated mouth (speaking)
  - [ ] Closed eyes (sleeping)
  - [ ] Happy face
  - [ ] Confused/tilted face
  - [ ] X eyes (error)
- [ ] Build finite state machine:
  - [ ] IDLE
  - [ ] LISTENING
  - [ ] THINKING
  - [ ] SPEAKING
  - [ ] SLEEPING
  - [ ] HAPPY
  - [ ] CONFUSED
  - [ ] ERROR
- [ ] Wire push button
- [ ] Button press triggers state change cycle for testing
- [ ] Add serial logging for every state transition

#### Milestone

Button press visibly changes face and state on display.

#### Demo Goal

Press button → face cycles through:
IDLE → LISTENING → THINKING → SPEAKING → IDLE

---

### Week 3 — Audio Output (Robot Voice)

**Goal:** Get the robot to speak.

#### Tasks

- [ ] Wire MAX98357 amplifier to ESP32-S3
- [ ] Wire speaker to MAX98357
- [ ] Validate audio output path
- [ ] Play a test audio file or tone
- [ ] Implement TTS playback:
  - [ ] Generate audio from backend
  - [ ] Stream or buffer to MAX98357
- [ ] Sync face to SPEAKING state during playback
- [ ] Add hardcoded test phrases:
  - [ ] "Hello, I am online."
  - [ ] "Press the button to talk."
  - [ ] "I am thinking..."
  - [ ] "Nice to meet you."

#### Milestone

Robot speaks a phrase with animated speaking face.

#### Demo Goal

Button press → robot says "Hello, I am online." with face animated
in SPEAKING state.

---

### Week 4 — Voice Input (Push-to-Talk)

**Goal:** The robot can hear you.

#### Tasks

- [ ] Wire INMP441 microphone to ESP32-S3
- [ ] Validate I2S mic input
- [ ] Record short audio clip on button hold
- [ ] Send audio to STT backend via Wi-Fi
- [ ] Receive transcribed text back
- [ ] Log transcription to serial for debugging
- [ ] Add fallback: if Wi-Fi fails, respond with local phrase
- [ ] Add visual feedback:
  - [ ] Button held → LISTENING state
  - [ ] Button released → THINKING state

#### Milestone

Button press captures voice, transcription appears in serial log.

#### Demo Goal

Hold button, say "hello", see transcription logged:
