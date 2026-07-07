# 🎛️ DUB FX PAD — File Sampler

**A browser-based, offline-ready sample pad for dub, sound-system, and live FX performance — with a built-in tape-echo & spring-reverb unit inspired by the classic Roland RE-201 Space Echo.**

![status](https://img.shields.io/badge/status-active-brightgreen)
![type](https://img.shields.io/badge/type-single--file%20web%20app-blue)
![offline](https://img.shields.io/badge/offline-ready-success)
![license](https://img.shields.io/badge/license-MIT-lightgrey)

---

## ✨ Overview

DUB FX PAD is a **single self-contained HTML file** — no build step, no server, no dependencies to install. Open it in any modern mobile or desktop browser and you have a fully working sample pad:

- Load your own audio files (MP3, WAV, OGG, FLAC, AAC, M4A) as playable pads
- Organize sounds into categories (Sweeps, Lasers, One-Shots, Sirens, Ambient FX, plus your own custom categories)
- Run everything through a dub-style **tape delay + spring reverb** engine, modeled after classic tape echo units
- Mix, mute, favorite, rename, move, and reorder every sound
- Works fully offline once loaded — samples and settings persist locally on the device (IndexedDB + localStorage), no cloud, no accounts, no tracking

Built for live dub/sound-system performance, DJ FX, foley/soundboard use, or just messing around with a warm analog-style echo unit in the browser.

---

## TRY IT ONLINE!

https://definite-teal-5ka734sq.edgeone.dev

---

## 🚀 Getting Started

### Option 1 — Just open it
1. Download `dubpadfx.html` (or clone this repo).
2. Open the file directly in a browser (double-click, or drag it into a browser tab).
3. Tap **▶ POWER ON** to initialize the audio engine (required by browsers before any sound can play).
4. Tap **⊕ LOAD** to add your own audio files.

### Option 2 — Serve it locally (recommended for mobile testing)
Some mobile browsers restrict `file://` access to features like IndexedDB. If you run into issues, serve it over a local HTTP server instead:

```bash
# Python 3
python3 -m http.server 8080

# Node (http-server package)
npx http-server -p 8080
```

Then open `http://localhost:8080/dubpadfx.html` on your device (same Wi-Fi network for phones/tablets).

### Option 3 — Termux (Android)
The app ships with a default sample path pointing at:

```
/data/data/com.termux/files/home/storage/downloads/DubpadFX/
```

This is a convenience default for Android/Termux users who keep their sample library there — it's just a text hint shown in the Load modal, **not a requirement**. You can load files from anywhere using the standard file picker.

---

## 🎚️ Features

### Sample Pads
- Tap any pad to trigger playback instantly
- Long-press (or right-click on desktop) a pad to open its context menu:
  - ★ Add / Remove Favorites
  - ✎ Rename
  - ↗ Move to another category
  - ✕ Remove pad
- Pads auto-assign an emoji icon based on filename keywords (e.g. "laser", "kick", "siren", "drone"), or default to 🎵

### Categories
- Built-in: **Sweeps · Lasers · One-Shots · Sirens · Ambient FX · Favorites**
- Create unlimited **custom categories** with your own name, icon, and color
- Deleting a custom category safely relocates its sounds to Ambient FX (with confirmation if it isn't empty)

### ⇅ Pad Reordering
- Every category (and the "All" view) can be reordered exactly how you like via the **⇅ ORDINA** button
- Drag-and-drop list, works with mouse drag **and** touch drag on mobile
- Favorites have their own independent, savable order in the ★ FAVORITES modal

### 🎚️ Mixer — Per-Sound Volume & Delay Send
- Full-screen mixer view (**🎚 MIXER**) with one horizontally-scrollable channel strip per loaded sound
- Long, precise vertical faders with **±35 dB** of range and precision tick marks every 5 dB (major marks every 10 dB, 0 dB highlighted)
- **0 dB = the original, untouched volume of the loaded file** — nothing is pre-attenuated
- Live dB and percentage readout per channel
- Per-pad **DELAY** toggle: mutes *only* that sound's send into the tape-delay/echo repeats. Dry volume and the spring reverb are completely unaffected — useful for keeping a sound's ambience without letting it build up echo trails
- **RESET ALL TO 100%** restores every channel to 0 dB and re-enables delay on all pads in one tap

### 🎛️ Roland-inspired Space Echo Unit
A fixed control strip at the bottom of the screen, always available while you play:

| Control | Range | Description |
|---|---|---|
| **DELAY TIME** | 50 ms – 2.0 s | Tape delay time |
| **FEEDBACK** | 0 – 98% | Number of repeats |
| **SPRING REV** | 0 – 180% | Spring/plate reverb amount |
| **DRY/WET** | 0 – 100% | Blend between dry signal and effect |
| **MASTER VOL** | 0 – 100% | Overall output level |

**5 preset modes:**
- **DRY** — no effect, clean signal
- **ECHO** — tape delay only
- **SPRING** — reverb only
- **ECHO + SPRING** — both combined
- **DEEP DUB** — heavy feedback + long reverb tail, mostly wet, classic dub-out setting

**Tap Tempo / Manual BPM** — tap the **TAP** button to set delay time by feel, or type/step a BPM value (40–300) directly. The delay time syncs to the tempo automatically.

A hand-crafted **convolution impulse response** models a spring/plate reverb tank with pre-delay, irregular early reflections, dual-band diffuse tail, subtle inharmonic spring resonance, and decorrelated stereo channels — built entirely with the Web Audio API, no external samples required.

### 💾 Persistence
- All pads, categories, favorites, mixer levels, mute states, and echo settings are saved automatically to `localStorage`
- The actual audio file data is stored in **IndexedDB**, so your sample library survives page reloads and app restarts — fully offline, nothing uploaded anywhere
- On next launch, sounds are automatically restored and re-decoded

### 🗑️ Full Wipe
- The **🗑 WIPE** button performs a complete factory reset: all pads, categories, favorites, mixer settings, and stored audio data (IndexedDB + localStorage) are cleared
- Protected by a double confirmation, since the action is irreversible

### 📻 Visuals
- Reactive VU meter in the header driven by a live audio analyser
- Spinning reel / moving tape animation on the echo unit while a sound plays
- Color-coded categories throughout pads, tabs, and mixer strips
- Retro terminal/hardware aesthetic: scanlines, vignette, CRT-style glow, monospace + display fonts

---

## 🗂️ Project Structure

This is intentionally a **single HTML file** (`dubfx.html`) containing:

```
dubpadfx.html
├── <style>   → all CSS (theming, layout, animations)
├── <body>    → markup (init screen, header, tabs, grid, echo unit, modals)
└── <script>  → app logic:
    ├── State (S object) + persistence (localStorage + IndexedDB)
    ├── Web Audio engine (delay, reverb IR synthesis, compressor, analyser)
    ├── Pad management (add/remove/move/rename)
    ├── UI rendering (tabs, grid, mixer, modals, context menu)
    └── Controls (knobs, tap tempo, echo modes)
```

No bundler, no npm install, no external JS frameworks. The only external resource is the Google Fonts stylesheet (`Share Tech Mono` + `Orbitron`), loaded via CDN — everything else is self-contained.

---

## 🌐 Browser Support & Requirements

- Any modern browser with **Web Audio API** and **IndexedDB** support (Chrome, Firefox, Safari, Edge — desktop or mobile)
- A user gesture (tapping **POWER ON**) is required before audio can start, per browser autoplay policies
- Best experienced on a touch device for the tap/long-press pad interactions, but fully usable with mouse + right-click on desktop

---

## 🛠️ Customization

Since everything lives in one file, most tweaks are quick edits:

- **Categories** — edit the `CAT_META` object in the script to change built-in category labels, icons, or colors
- **Icon auto-detection** — extend `CAT_ICON_GUESS` to map more filename keywords to emoji
- **Reverb character** — tune `buildSpringIR()` (decay times, band-pass ranges, resonance frequencies) to shape the spring/plate tone
- **Echo modes** — the `modes` array inside `setMode()` defines the dry/wet/feedback/reverb blend for each of the 5 preset modes
- **Theme** — all colors are CSS custom properties under `:root` at the top of the stylesheet

---

## 🙏 Credits & Inspiration

Inspired by the aesthetic of classic **Space Echo**-style tape units and Jamaican & Italian dub sound-system culture.

Gear & brands referenced as an homage (original stylized badges, not official logos — no affiliation with any of these companies):

- **Roland** — Space Echo RE-201
- **Behringer**
- **NUX**
- **Korg**
- **Dubmatix**

Special thanks to **Paolo Baldini DubFader** — inspiration and guiding reference for the dub sound and mixing philosophy behind this project.

All trademarks and brand names mentioned belong to their respective owners. No official affiliation or endorsement is implied.

---

## ⚠️ Disclaimer

This project is a personal/creative audio tool. It does not collect, transmit, or store any data outside the user's own device — everything (files, settings, mixer levels) stays local in the browser's storage.

---

## 📄 License

Add your preferred license here (e.g. MIT, GPL-3.0). If unsure, [choosealicense.com](https://choosealicense.com/) can help you pick one.

```
MIT License

Copyright (c) [year] [author]

Permission is hereby granted, free of charge, to any person obtaining a copy...
```

---

## 🤝 Contributing

Issues and pull requests are welcome. Since it's a single-file app, most contributions can be made directly against `dubfx.html` — please keep the "no build step" philosophy intact when proposing changes.
