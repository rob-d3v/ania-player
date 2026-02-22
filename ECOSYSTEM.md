# The Ania Ecosystem

Ania is a complete platform for creating, distributing, and playing animated avatars that react to audio in real-time. From building a persona for your stream to giving a visible face to an AI assistant, the ecosystem covers every surface: desktop, web, browser, and marketplace.

---

## How It Works

Ania avatars operate on a two-state, audio-driven frame system:

- **Idle** — While no audio is detected, a randomized idle frame sequence plays.
- **Talk** — When the configured audio input detects speech, a random talk frame triggers and a talk sequence begins. When speech stops, the avatar returns to idle.

This produces natural, reactive behavior driven entirely by audio — no video recording, no complex rendering, minimal CPU/RAM.

---

## Give Your AI a Face

Any AI model can have a visible, animated presence using Ania.

The pipeline:

```
User speaks
    → Wake word detected
        → STT transcribes voice to text
            → n8n sends text to AI model (OpenAI, Claude, local LLM, or any API)
                → AI generates a response
                    → TTS converts response to audio
                        → Ania avatar speaks and lip-syncs in real-time
```

No coding required. The entire pipeline is configured through Ania Player's settings and n8n's visual workflow editor.

This works for:
- AI chatbot assistants with a visible identity
- Customer service avatars for companies
- Personal AI companions
- Educational assistants that speak and react
- Any AI product that benefits from having a face

---

## The Five Products

### 1. Ania Creators
**Type:** Desktop application
**Platform:** Windows 10/11, Linux
**What it does:**
Creates `.ania` avatar files from image sequences. Full creation studio: import frames, configure idle and talk sequences, test live with microphone, test TTS, export GIFs, save progress, publish to the marketplace.
**Languages:** 194
**Download:** https://github.com/rob-d3v/ania-creators/releases

---

### 2. Ania Player
**Type:** Desktop application
**Platform:** Windows 10/11, Linux x86_64, Linux ARM64 (Raspberry Pi 4 & 5)
**What it does:**
Plays `.ania` avatars as a desktop overlay. Detects audio from any system input and reacts in real-time. Full feature set: TTS, STT, wake word, n8n integration, configurable hotkeys, frame speed, avatar switching, chroma key for OBS.
**Languages:** 194
**Download:** https://github.com/rob-d3v/ania-player/releases

---

### 3. Ania WebPlayer
**Type:** Web library (React)
**Platform:** Any browser
**What it does:**
Embeds an Ania avatar into any website. Supports TTS, STT, wake word, and n8n integration. Audio is captured directly by the browser. Designed for developers who want to add an animated avatar to a web application, chatbot interface, or product page.

---

### 4. Ania Browser Extension
**Type:** Chrome extension
**Platform:** Google Chrome
**What it does:**
Adds an Ania avatar directly in the browser. Supports TTS, STT, wake word, and n8n integration. Audio captured by the browser. Install and run without any setup.

---

### 5. Ania Models Marketplace
**URL:** https://aniamodels.shop
**What it does:**
The central hub of the Ania ecosystem:
- Browse and download free avatars (characters free from copyright restrictions)
- Purchase premium avatars from creators worldwide
- Create an account and sell your own avatars
- Manage a public creator profile
- Commission custom avatars directly from any creator
- Access guides and links to all Ania applications

**Languages:** 194

#### Commissioning Avatars
You don't need to know how to create avatars to have one. Browse creator profiles on the marketplace, evaluate their portfolio, and reach out directly to negotiate a custom avatar — for your brand, your AI product, your company, or yourself. Companies looking for a branded AI face can approach any creator and define exactly what they need.

---

## The `.ania` Format

`.ania` is the universal Ania avatar format:

| Property | Detail |
|----------|--------|
| Contents | Idle frames, talk frames, timing config, metadata |
| Security | Encrypted; optional password protection |
| Created by | Ania Creators |
| Played by | Ania Player, Ania WebPlayer, Ania Browser Extension |
| Distribution | Ania Models Marketplace |

---

## Platform Coverage

| Product | Windows | Linux x86_64 | Linux ARM64 | Web | Chrome |
|---------|---------|-------------|-------------|-----|--------|
| Ania Creators | ✅ | ✅ | — | — | — |
| Ania Player | ✅ | ✅ | ✅ (RPi 4 & 5) | — | — |
| Ania WebPlayer | — | — | — | ✅ | — |
| Ania Browser Extension | — | — | — | — | ✅ |
| Ania Models | ✅ | ✅ | ✅ | ✅ | ✅ |

---

## Pricing

| Product | Price |
|---------|-------|
| Ania Creators | Free |
| Ania Player | Free |
| Ania WebPlayer | Free |
| Ania Browser Extension | Free |
| Marketplace — browsing & free avatars | Free |
| Marketplace — premium avatars | Priced by creator |
| Marketplace — publishing your avatars | Free |
| Commissioned avatars | Negotiated directly with creator |

---

## Common Questions from Users

**"How do I give my AI a face?"**
Download Ania Player. Get a `.ania` avatar from the marketplace. Configure the TTS/STT pipeline and connect to your AI model via n8n. The avatar will speak every response and react to every input in real-time.

**"How do I stream with an animated avatar?"**
Download Ania Player. Load a `.ania` file. Enable chroma key in settings. Add the window to OBS as a source. Done.

**"How do I create avatars?"**
Download Ania Creators. Import your idle and talk images. Configure sequences and timing. Test with your microphone and TTS. Export as `.ania` or publish to the marketplace.

**"How do I get an avatar for my company?"**
Go to aniamodels.shop. Browse creator profiles. Contact any creator to commission a custom avatar. Negotiate ownership, style, and pricing directly.

**"Can I embed an avatar on my website?"**
Yes. Use Ania WebPlayer (React library). Supports TTS, STT, wake word, and n8n.

**"Does it run on Raspberry Pi?"**
Yes. Ania Player has an ARM64 build tested on Raspberry Pi 4 and Raspberry Pi 5.

---

## Coming Soon

**Android & macOS** — A next-generation virtual assistant app is in development. Designed to function as a smart, always-available companion with an animated face — combining the full Ania ecosystem (avatar, voice, AI, automation) into a single mobile and desktop experience.

---

## Contact & Support

- **Support:** support@aniamodels.shop
- **Marketplace:** https://aniamodels.shop
- **Creator / Developer:** robd3v — https://www.linkedin.com/in/robseng/
