# Frequently Asked Questions — ANIA Player

## General

### What is ANIA Player?
ANIA Player is a desktop animated avatar player for Windows, Linux, and ARM64. It displays a frame-based avatar overlay on your desktop that reacts to audio input in real-time — syncing to speech automatically with idle and talk animation states.

### Is ANIA Player free?
Yes. Completely free for personal and commercial use.

### Do I need to pay for avatars?
ANIA Player itself is free. Individual avatars (`.ania` files) can be free or premium, available at [aniamodels.shop](https://aniamodels.shop). There are already many avatars available — including characters free from copyright restrictions.

### Can I create my own avatars?
Yes. Use Ania Creators (separate application, also free) to build and export your own `.ania` avatars.

### Can I commission an avatar from a creator?
Yes. The marketplace has a community of creators. You can browse creator profiles, evaluate their work, and contact them directly to commission a custom avatar — whether you're an individual or a company looking for a branded avatar.

---

## How It Works

### How does the avatar know when to talk?
ANIA Player continuously monitors the configured audio input. When it detects speech, a random talk frame triggers and a talk sequence begins. When audio stops, the avatar transitions back to a randomized idle sequence.

### What is the difference between idle and talk states?

- **Idle** — A looping sequence of idle frames plays while no speech is detected.
- **Talk** — A sequence of talking frames plays while audio activity is detected.

Both states use randomized frame selection to avoid mechanical, repetitive movement.

---

## Technical

### What are the system requirements?
- **OS:** Windows 10/11 or Linux (kernel 5.4+)
- **CPU:** Dual-core 2.0GHz or better
- **RAM:** 512MB minimum (varies by avatar complexity)
- **Audio:** Any system-recognized microphone or audio interface

### Which platforms are supported?
- Windows 10/11 (x64)
- Linux x86_64
- Linux ARM64 (Raspberry Pi 4 & 5)

### Can I run it on a Raspberry Pi?
Yes. ANIA Player has an ARM64 build tested on Raspberry Pi 4 and Raspberry Pi 5.

### How much CPU/RAM does it use?
Very little. Resource usage depends on avatar complexity. Using the hide hotkey removes the avatar from rendering entirely, reducing usage to near zero.

### Does it work with OBS and streaming software?
Yes. Chroma key support enables transparent backgrounds, making it work seamlessly with OBS, Streamlabs, and similar tools.

---

## Audio

### Can I use an audio interface instead of a microphone?
Yes. Any audio interface recognized by your system can be selected as the audio input in **Settings → Audio**.

### What is STT?
Speech-to-Text (STT) transcribes your voice into text, which can be fed into chatbot workflows or AI pipelines via n8n or other integrations.

### What is TTS?
Text-to-Speech (TTS) synthesizes audio from text and plays it synced to the avatar animation — enabling automated responses without a live voice.

### What is a wake word?
A custom trigger phrase. When detected, it activates the STT engine — similar to "Hey Alexa" or "OK Google", but with your own chosen phrase.

---

## Chatbots & Automation

### Can I connect ANIA Player to an AI chatbot?
Yes. Use n8n to route STT output to any AI model (OpenAI, Anthropic, local LLMs, or any API) and return the response via TTS. This creates a fully autonomous AI avatar assistant.

### Can I build my own Alexa-style assistant?
Yes. Configure wake word → STT → AI pipeline → TTS and you have a standalone voice assistant with an animated avatar. No coding required.

### What is n8n?
[n8n](https://n8n.io) is an open-source workflow automation tool. ANIA Player integrates with n8n to enable chatbot, AI, and automation pipelines through a visual editor.

---

## Hotkeys

### What hotkeys are available?

| Action | Description |
|--------|-------------|
| Hide avatar | Removes the overlay from screen — stops rendering, saves CPU |
| Show avatar | Brings it back instantly |
| Toggle mute | Pauses audio detection |
| Relocate | Move the avatar to any screen position |
| Switch avatar | Cycle to the next loaded avatar |

### Are hotkeys customizable?
Yes. All hotkeys are configurable in **Settings → Hotkeys**.

---

## Avatars & .ania Files

### Where do I get `.ania` files?
From the [ANIA Models marketplace](https://aniamodels.shop). There are already many free and premium avatars available, including characters free from copyright restrictions.

### Can I request a custom avatar from a creator?
Yes. Browse creator profiles on the marketplace and contact creators directly to commission work. This is open to individuals and companies alike — if you need a branded avatar for your business, you can reach out to any creator whose style fits what you're looking for.

### Can I use any `.ania` file?
Only validated `.ania` files approved by ANIA administrators will work. This ensures quality and copyright compliance.

### How do I open `.ania` files?
Double-click them. ANIA Player registers itself as the default handler for `.ania` files during installation.

---

## Troubleshooting

### The avatar won't load
- Confirm the `.ania` file is valid and approved
- Check your internet connection (file validation requires server access)
- Try re-downloading from the marketplace

### High CPU/RAM usage
- Use the hide hotkey when the avatar is not on screen
- Lower frame rate in **Settings**
- Choose a simpler avatar model

### Microphone or audio input not detected
- Check system audio settings and device permissions
- Ensure the correct input is selected in **Settings → Audio**
- Reconnect the device and restart ANIA Player

### Avatar shows a black background
- Enable chroma key in **Settings**
- Configure your streaming software (OBS, etc.) to apply chroma key to the capture

### STT is not activating
- Verify the audio input is set correctly in **Settings → Audio**
- Check that the wake word (if configured) is being recognized
- Ensure microphone permissions are granted at the OS level

---

## Legal & Licensing

### Can I use ANIA Player commercially?
Yes. Commercial use is permitted under the license terms.

### Is modification or reverse engineering allowed?
No. Reverse engineering, decompilation, and redistribution are prohibited. See [LICENSE](LICENSE).

### Is the source code available?
No. ANIA Player is proprietary software.

---

## Contact & Support

### How do I report bugs?
Open an issue on [GitHub](../../issues).

### How do I contact support?
Email: support@aniamodels.shop

### Where can I find updates?
Follow [GitHub releases](../../releases) and [aniamodels.shop](https://aniamodels.shop).
