# ANIA Player

<p align="center">
  <strong>Desktop Avatar Player for Streams, Video Content, Chatbots & AI Assistants</strong>
</p>

<p align="center">
  <a href="#about">About</a> •
  <a href="#give-your-ai-a-face">Give Your AI a Face</a> •
  <a href="#how-it-works">How It Works</a> •
  <a href="#features">Features</a> •
  <a href="#download">Download</a> •
  <a href="#quick-start">Quick Start</a> •
  <a href="#hotkeys">Hotkeys</a> •
  <a href="#chatbots--ai">Chatbots & AI</a> •
  <a href="#system-requirements">Requirements</a> •
  <a href="#roadmap">Roadmap</a>
</p>

---

## Give Your AI a Face

Any AI model can have a visible, animated presence using ANIA Player.

Connect an avatar to your AI pipeline and it will speak every response, react to every input, and give your assistant a personality you can see.

**The full pipeline — no coding required, and since v1.1.0 no external tooling either:**

```
User speaks → Wake word → STT → LLM → TTS → Avatar speaks in real-time
```

All four stages now run **inside the player**, with twelve swappable engines. Out of the box it points at **local Ollama** — fully offline, no API key, no cloud. n8n is still supported; it is no longer required.

Works with any AI: OpenAI, Anthropic, local LLMs, or anything you route yourself. Runs on Windows, Linux, and Raspberry Pi. Avatars available free at [avatar.diatech.solutions](https://avatar.diatech.solutions).

> **v1.1.0 is a large release.** The avatar can now act as a **system webcam** in OBS, Zoom, Meet and Discord; lip-sync to ChatGPT's voice with **no audio configuration at all**; and be driven from a 34-verb CLI, `ania://` links, or opt-in remote control. Full details — and the limitations, stated up front — in **[RELEASE-v1.1.0.md](RELEASE-v1.1.0.md)**.

> Need a custom avatar for your AI product or brand? Browse creator profiles on the marketplace and commission one directly.

---

## About

ANIA Player is a frame-based animated avatar player for Windows, Linux, and ARM64 (Raspberry Pi 4 & 5). It displays a configurable animated avatar as a desktop overlay that reacts to audio input in real-time — syncing lip movement to speech and transitioning automatically between idle and talking states.

Avatars can also perform **actions** — custom animations created in Ania Creators and triggered on demand. Actions interrupt the current state instantly and play to completion, giving avatars expressive, reactive behavior beyond idle and talk.

Built for streamers, educators, developers, and anyone who wants a reactive animated avatar without video overhead.

---

## How It Works

ANIA Player operates on an audio-driven animation system with three states:

- **Idle** — While no audio is detected, a randomized idle frame sequence plays.
- **Talk** — When the configured audio input detects speech, a random talk frame triggers and a talk sequence begins. When speech stops, the avatar transitions back to idle.
- **Action** — A custom animation created by the avatar's author. Actions interrupt idle or talk instantly and play to completion. Triggered via hotkey, TTS, n8n workflow, or any configured input.

This gives avatars natural, reactive behavior driven purely by audio and events — no video recording, no complex rendering pipeline, minimal resource usage.

---

## Features

### Avatar & Display
- **Frame-based Overlay** — Smooth animated avatar displayed over your desktop or stream
- **Chroma Key Support** — Transparent background for seamless OBS and streaming tool integration
- **Adjustable Size** — Scale the avatar to any size
- **Frame Speed Control** — Fine-tune animation speed independently of audio detection
- **Switch Avatar** — Hotkey to cycle between loaded avatars instantly

### Virtual Camera *(new in 1.1.0)*
- **Your avatar as a webcam** — "Ania Virtual Camera" appears in OBS, Zoom, Meet, Discord and anything that accepts a camera
- **Scene compositor** — Layer screen capture, images and the avatar, with a drag-and-scale editor and a region picker
- One click on Windows (drivers bundled, MIT). Linux needs `v4l2loopback`. **No macOS support**

### Companion Mode *(new in 1.1.0)*
- **Lip-syncs to ChatGPT's voice with zero audio setup** — no Stereo Mix, no VB-Cable, no device list, no dialog
- **Automatic loopback resolution** — finds the device that captures what your speakers play, verifies it for 2 seconds, and says so honestly if it had to fall back to your microphone
- Corner-anchored, transparent, click-through, always on top. `Ctrl+Shift+A` always gives the window back

### Voice & AI *(rebuilt in 1.1.0)*
- **12 swappable engines** — 5 TTS (Piper local, Edge, ElevenLabs, Google Cloud, OpenAI), 5 STT (faster-whisper local, Google, Windows offline, ElevenLabs, Whisper), 2 wake word
- **Sentinela** — Ania's own wake-word engine: pt-BR tuned, single ONNX, 100% offline, self-calibrating, models verified by sha256
- **Floating chat window** with live partial transcription
- **Local by default** — Ollama, faster-whisper and Piper all run offline. Cloud engines are marked ☁ in the UI *before* you install them
- **Real-time audio detection** from any system audio source

### Marketplace & Library *(new in 1.1.0)*
- **Storefront inside the player** — search, category chips, animated previews, install with progress. No login, no account
- **Crash-safe local library** — atomic writes, SHA-256 verification, and a killed download never leaves a broken entry

### Automation & Control *(new in 1.1.0)*
- **34-verb CLI** — `aniaplayer tts "hello"`, `action`, `status --json`
- **`ania://` links** — a web page can open the player in companion mode, install an avatar, or start a pairing
- **Ania Link** — opt-in remote control by 6-character code, behind a 16-verb allowlist. **Off by default; with it off nothing connects out**
- **MQTT and MySQL** integrations, the latter read-only by default

### Actions
- **Custom Animations** — Avatars can perform any action defined by their creator: dances, jumps, greetings, reactions, and more
- **Interrupt-based** — Actions immediately interrupt idle or talk and play to completion
- **Unlimited** — The number of actions an avatar can have is defined entirely by its creator in Ania Creators
- **Multi-trigger** — Actions can be triggered via hotkey, TTS, n8n workflow, or any configured input

### Hotkeys
- **Hide Avatar** — Instantly removes the avatar from screen, freeing CPU/RAM
- **Show Avatar** — Brings it back with a single keypress
- **Toggle Mute** — Pause audio detection without closing the app
- **Relocate** — Move the avatar overlay to any position on screen
- **Switch Avatar** — Cycle to the next loaded avatar
- **Trigger Action** — Fire any configured avatar action instantly

### Chatbots & Automation
- **Built-in assistant** — wake word + STT + LLM + TTS, all in-app, pointed at local Ollama by default. *This is the "Alexa-style assistant" v1.0.0 described; it now ships rather than being assembled*
- **n8n Integration** — still supported for anyone who prefers to route through workflows
- **AI Pipeline Support** — Feed STT output into any AI model and return responses via TTS
- **Action Triggers via n8n** — Trigger avatar actions directly from workflow events
- **Plugin manager** — install engines from a UI that shows size, repository, licence and a ☁ Cloud / 🏠 Local badge before you commit

### General
- **192 Languages** — Full interface localization. *The Ania Link screens and companion mode are English-only for now; everything else falls back to English in those two areas*
- **Cross-Platform** — Windows 10/11, Linux x86_64, Linux ARM64
- **Raspberry Pi 4 & 5** — ARM64 build tested and supported
- **Minimal Resource Usage** — Optimized for low CPU/RAM; smart frame caching
- **Verified Avatars** — Server-side validation ensures only approved `.ania` files play

---

## Download

**Latest Release:** [Releases](../../releases)

### Supported Platforms

| Platform | Architecture |
|----------|-------------|
| Windows 10/11 | x64 |
| Linux | x86_64 |
| Linux ARM64 | Raspberry Pi 4 & 5 |

---

## Quick Start

1. Download the package for your OS from [Releases](../../releases)
2. Install or extract ANIA Player
3. Open a `.ania` avatar file — ANIA Player auto-associates with the format on install
4. Configure your audio input in **Settings → Audio**
5. Adjust frame speed, avatar size, and hotkeys as needed
6. *(Optional)* Configure TTS, STT, and wake word for automation
7. *(Optional)* Connect to n8n for chatbot and AI integration

---

## Hotkeys

All hotkeys are fully configurable in **Settings → Hotkeys**.

| Action | Description |
|--------|-------------|
| Hide avatar | Removes the overlay from screen — stops rendering, saves CPU |
| Show avatar | Brings the avatar back instantly |
| Toggle mute | Pauses audio detection without closing the app |
| Relocate | Drag or position the avatar anywhere on screen |
| Switch avatar | Cycle to the next loaded `.ania` avatar |
| Trigger action | Fire any configured avatar action instantly |

> Hiding the avatar completely removes it from rendering. This is the most effective way to save resources during scenes or moments where the avatar isn't needed.

---

## Chatbots & AI

ANIA Player can be the visible face of a fully automated AI assistant:

1. **Wake word** triggers STT
2. **STT** transcribes voice to text
3. **n8n** routes the text to an AI model (OpenAI, local LLM, or any API)
4. **AI response** is returned to ANIA Player via TTS
5. **Avatar** speaks the response in real-time

Actions can also be triggered from n8n workflows — for example, having the avatar wave when a user connects, or dance when a goal is reached.

No coding required — configure everything through the app and n8n's visual workflow editor.

---

## ANIA Format

`.ania` files contain all frame-based animation data for an avatar, including idle sequences, talk sequences, and any actions defined by the creator. They are:

- Created using **Ania Creators** (desktop application)
- Validated and approved by ANIA administrators
- Available at [avatar.diatech.solutions](https://avatar.diatech.solutions) — free and premium options, including characters free from copyright restrictions
- Portable, encrypted, and optionally password-protected

### Getting an Avatar

**Download from the marketplace** — [avatar.diatech.solutions](https://avatar.diatech.solutions) already has a growing library of avatars available, including free options.

**Create your own** — Use Ania Creators to build a completely original avatar from your own images, with your own custom actions.

**Commission a creator** — Browse creator profiles on the marketplace and contact any creator directly to request a custom avatar. This works for individuals and companies alike. If you want a branded avatar for your business, your stream, or your product — find a creator whose style fits, and negotiate directly.

---

## System Requirements

| Component | Minimum |
|-----------|---------|
| **OS** | Windows 10/11, Linux (kernel 5.4+) |
| **CPU** | Dual-core 2.0GHz |
| **RAM** | 512MB (varies by avatar complexity) |
| **Audio** | Any system-recognized microphone or audio interface |

---

## Roadmap

- **Android & macOS** — A next-generation mobile and desktop assistant app is in development. Designed to act as a smart virtual assistant, combining everything the Ania ecosystem offers into a single always-available companion experience.
- **Enhanced Customization** — More animation controls and visual effects

---

## ANIA Ecosystem

| Application | Platform | Description |
|-------------|----------|-------------|
| **Ania Player** *(this)* | Windows, Linux, ARM64 | Desktop avatar player |
| **Ania Creators** | Windows, Linux | Avatar creation studio |
| **Ania WebPlayer** | React / Any browser | Web integration library for developers |
| **Ania Browser Extension** | Chrome | Browser-native avatar player |
| **Ania Models** | Web | Marketplace at [avatar.diatech.solutions](https://avatar.diatech.solutions) |

---

## License

This software is distributed under a proprietary license. See [LICENSE](LICENSE) for details.

- Free to use for personal and commercial purposes
- Reverse engineering and decompilation prohibited
- Redistribution of modified versions not permitted
- Source code is not publicly available

---

## Support

- **Bug Reports & Feature Requests** — [GitHub Issues](../../issues)
- **General Support** — support@diatech.solutions
- **Marketplace** — [avatar.diatech.solutions](https://avatar.diatech.solutions)

---

For a complete overview of all five products in the Ania ecosystem, see [ECOSYSTEM.md](ECOSYSTEM.md).

---

Created by [robd3v](https://www.linkedin.com/in/robseng/)
