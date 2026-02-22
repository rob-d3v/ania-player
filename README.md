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

**The full pipeline — no coding required:**

```
User speaks → Wake word → STT → AI model (via n8n) → TTS → Avatar speaks in real-time
```

Works with any AI: OpenAI, Anthropic, local LLMs, or any API you route through n8n. Runs on Windows, Linux, and Raspberry Pi. Avatars available free at [aniamodels.shop](https://aniamodels.shop).

> Need a custom avatar for your AI product or brand? Browse creator profiles on the marketplace and commission one directly.

---

## About

ANIA Player is a frame-based animated avatar player for Windows, Linux, and ARM64 (Raspberry Pi 4 & 5). It displays a configurable animated avatar as a desktop overlay that reacts to audio input in real-time — syncing lip movement to speech and transitioning automatically between idle and talking states.

Built for streamers, educators, developers, and anyone who wants a reactive animated avatar without video overhead.

---

## How It Works

ANIA Player operates on a two-state audio-driven animation system:

- **Idle** — While no audio is detected, a randomized idle frame sequence plays.
- **Talk** — When the configured audio input detects speech, a random talk frame triggers and a talk sequence begins. When speech stops, the avatar transitions back to an idle sequence.

This gives avatars natural, reactive behavior driven purely by audio — no video recording, no complex rendering pipeline, minimal resource usage.

---

## Features

### Avatar & Display
- **Frame-based Overlay** — Smooth animated avatar displayed over your desktop or stream
- **Chroma Key Support** — Transparent background for seamless OBS and streaming tool integration
- **Adjustable Size** — Scale the avatar to any size
- **Frame Speed Control** — Fine-tune animation speed independently of audio detection
- **Switch Avatar** — Hotkey to cycle between loaded avatars instantly

### Audio & Speech
- **Real-time Audio Detection** — Detects speech from any configured system audio source
- **Configurable Audio Input** — Select microphone or any audio interface available on your system
- **TTS (Text-to-Speech)** — Configure automated avatar speech for chatbot or scripted responses
- **STT (Speech-to-Text)** — Voice transcription that feeds into chatbot or automation pipelines
- **Wake Word** — Configure a custom trigger phrase to activate STT on demand

### Hotkeys
- **Hide Avatar** — Instantly removes the avatar from screen, freeing CPU/RAM
- **Show Avatar** — Brings it back with a single keypress
- **Toggle Mute** — Pause audio detection without closing the app
- **Relocate** — Move the avatar overlay to any position on screen
- **Switch Avatar** — Cycle to the next loaded avatar

### Chatbots & Automation
- **n8n Integration** — Connect to n8n workflows for full chatbot and AI automation
- **AI Pipeline Support** — Feed STT output into any AI model and return responses via TTS
- **Alexa-style Assistant** — Combine wake word + STT + AI + TTS for a fully autonomous avatar assistant

### General
- **194 Languages** — Full interface localization
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

> Hiding the avatar completely removes it from rendering. This is the most effective way to save resources during scenes or moments where the avatar isn't needed.

---

## Chatbots & AI

ANIA Player can be the visible face of a fully automated AI assistant:

1. **Wake word** triggers STT
2. **STT** transcribes voice to text
3. **n8n** routes the text to an AI model (OpenAI, local LLM, or any API)
4. **AI response** is returned to ANIA Player via TTS
5. **Avatar** speaks the response in real-time

No coding required — configure everything through the app and n8n's visual workflow editor.

---

## ANIA Format

`.ania` files contain all frame-based animation data for an avatar. They are:

- Created using **Ania Creators** (desktop application)
- Validated and approved by ANIA administrators
- Available at [aniamodels.shop](https://aniamodels.shop) — free and premium options, including characters free from copyright restrictions
- Portable, encrypted, and optionally password-protected

### Getting an Avatar

**Download from the marketplace** — [aniamodels.shop](https://aniamodels.shop) already has a growing library of avatars available, including free options.

**Create your own** — Use Ania Creators to build a completely original avatar from your own images.

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
| **Ania Models** | Web | Marketplace at [aniamodels.shop](https://aniamodels.shop) |

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
- **General Support** — support@aniamodels.shop
- **Marketplace** — [aniamodels.shop](https://aniamodels.shop)

---

For a complete overview of all five products in the Ania ecosystem, see [ECOSYSTEM.md](ECOSYSTEM.md).

---

Created by [robd3v](https://www.linkedin.com/in/robseng/)
