# 🎛️ DUB FX PAD — File Sampler

**A browser-based, offline-ready sample pad for dub, sound-system and live FX performance — with a built-in tape-echo & spring-reverb unit inspired by the classic Roland RE-201 Space Echo. Made for phones and tablets first, fully usable on desktop.**

![status](https://img.shields.io/badge/status-active-brightgreen)
![type](https://img.shields.io/badge/type-single--file%20web%20app-blue)
![offline](https://img.shields.io/badge/offline-ready-success)
![platform](https://img.shields.io/badge/platform-Android%20%7C%20iOS%20%7C%20Desktop-orange)
![license](https://img.shields.io/badge/license-MIT-lightgrey)

<p align="center">
  <img src="https://i.ibb.co/8v59HxL/Screenshot-20261106-050700-com-android-chrome-Chrome-Tabbed-Activity.jpg" alt="DUB FX PAD running on Android Chrome" width="420">
</p>

---

## ✨ Overview

DUB FX PAD is a **single self-contained HTML file** — no build step, no server, no dependencies to install. Open it in any modern mobile or desktop browser and you have a fully working sample pad:

- Load your own audio files (MP3, WAV, OGG, FLAC, AAC, M4A) as playable pads
- Organize sounds into categories (Sweeps, Lasers, One-Shots, Sirens, Ambient FX, plus your own custom categories)
- Run everything through a dub-style **tape delay + spring reverb** engine, modeled after classic tape echo units
- Mix, mute, favorite, rename, move, resize and reorder every sound
- Hit **DELAY NOW** to throw an echo onto a sound that is *already playing* — and cut it again with a second tap
- Works fully offline once loaded — samples and settings persist locally on the device (IndexedDB + localStorage), no cloud, no accounts, no tracking

Built for live dub/sound-system performance, DJ FX, foley/soundboard use, or just messing around with a warm analog-style echo unit in the browser.

---

## TRY IT ONLINE!

https://definite-teal-5ka734sq.edgeone.dev

---

## 🚀 Getting Started

### Option 1 — Just open it
1. Download the `.html` file (or clone this repo).
2. Open it directly in a browser (double-click, or drag it into a browser tab).
3. Tap **▶ POWER ON** to initialize the audio engine (browsers require a user gesture before any sound can play). On supported browsers this also switches the app to **full screen** and keeps the screen awake while you play.
4. Tap **⊕ LOAD** to add your own audio files.

### Option 2 — Serve it locally (recommended for mobile testing)
Some mobile browsers restrict `file://` access to features like IndexedDB. If you run into issues, serve it over a local HTTP server instead:

```bash
# Python 3
python3 -m http.server 8080

# Node (http-server package)
npx http-server -p 8080
```

Then open `http://localhost:8080/<file-name>.html` on your device (same Wi-Fi network for phones/tablets).

### Option 3 — Termux (Android)
The start screen shows a default sample path hint:

```
/data/data/com.termux/files/home/storage/downloads/DubpadFX/
```

This is a convenience hint for Android/Termux users who keep their sample library there — it's just text, **not a requirement**. You can load files from anywhere using the standard file picker.

### 📲 Add to your home screen
Use your browser's menu → **Add to Home screen**. The app ships with an embedded home-screen icon (*Sweet Reggae Music*) and the name **DubPad FX**, so no extra files are needed. If you added an older version before, delete the old shortcut and add it again to refresh the icon.

---

## 🎚️ Features

### Sample Pads
- Tap any pad to trigger playback instantly (one sound at a time; switching pads fades the previous one out in 70 ms to avoid clicks)
- Long-press (or right-click on desktop) a pad to open its context menu:
  - ★ Add / Remove Favorites
  - ✎ Rename
  - ↗ Move to another category
  - ✕ Remove pad
- Pads auto-assign an emoji icon based on filename keywords (e.g. "laser", "kick", "siren", "drone"), or default to 🎵

### Categories
- Built-in: **Sweeps · Lasers · One-Shots · Sirens · Ambient FX · Favorites**
- Create unlimited **custom categories** with your own name, icon and color
- Deleting a custom category safely relocates its sounds to Ambient FX (with confirmation if it isn't empty)
- The **ALL** view is **automatically sorted by category**, in the same order as the tabs (built-ins first, then your custom ones). Inside each category the order you chose with ⇅ ORDINA is kept

### ⛶ Pad Size — 6 presets
**XXS · XS · S · M · L · XL** via the **SIZE** button. Phones and tablets have their own scales.
- **XS** shrinks icon and name to fit more pads on screen
- **XXS** shows the icon only (no name) for maximum density
- Your choice is remembered between sessions

### ⇅ Pad Reordering
- Every category (and the "All" view) can be reordered via the **⇅ ORDINA** button
- Drag-and-drop list, works with mouse drag **and** touch drag on mobile
- Favorites have their own independent, savable order in the ★ FAVORITES modal

### 🎚️ Mixer — Per-Sound Volume, Reverb & Delay Send
- Full-screen mixer view (**🎚 MIXER**) with one horizontally-scrollable channel strip per loaded sound
- Long, precise vertical faders with **±35 dB** of range and tick marks every 5 dB (major marks every 10 dB, 0 dB highlighted)
- **0 dB = the original, untouched volume of the loaded file** — nothing is pre-attenuated
- Live dB and percentage readout per channel
- Per-pad **REVERB** knob (0–100 %, perceptually scaled: 50 % really sounds about half as loud as 100 %)
- Per-pad **DELAY** toggle: mutes *only* that sound's send into the tape-delay/echo repeats. Dry volume and spring reverb are unaffected
- Changes are heard **immediately, even on the sound that is currently playing**
- **RESET ALL TO 100%** restores every channel to 0 dB and re-enables delay on all pads in one tap
- If the current Echo mode has no delay (DRY, SPRING) or no reverb (DRY), the mixer says so instead of showing controls that would do nothing

### 〰 DELAY NOW — one button, every pad
A single general button (not one per pad) that works on **whichever sound is playing right now**:
- Sound has its delay **off** in the mixer → first tap **turns the echo on** from that moment until the end of the sample
- Sound has its delay **on** in the mixer → first tap **cuts the echo**
- Tap again to bring it back, tap again to cut it, and so on — always for the current sound only
- On the next pad hit everything returns to the mixer's settings
- The button pulses and its LED lights up while the echo is forced on
- **When the Space Echo drawer is lowered, a compact version of the button stays visible** in the bottom-right corner, so it's always within reach
- Not available in **DRY** and **SPRING** modes (they have no delay output) — the app tells you

### 🎛️ Roland-inspired Space Echo Unit
A control panel always available while you play. On phones and portrait tablets it's a **drawer**: drag it down (or tap its handle) to get more room for pads, drag it up to bring it back — your choice is remembered. On wide tablets in landscape it becomes a **fixed side column** on the right.

| Control | Range | Description |
|---|---|---|
| **DELAY TIME** | 50 ms – 2.0 s | Tape delay time |
| **FEEDBACK** | 0 – 100 % (knob) | Number of repeats; non-linear, ear-tuned curve (about 1 repeat at the bottom, ~8 mid-way, ~60 at the top, capped below self-oscillation) |
| **DRY/WET** | 0 – 100 % | Blend between dry signal and effect |
| **MASTER VOL** | 0 – 100 % | Overall output level |

Reverb amount is set **per pad in the Mixer**.

**5 preset modes:**
- **DRY** — no effect, clean signal
- **ECHO** — tape delay only
- **SPRING** — reverb only
- **ECHO + SPRING** — both combined
- **DEEP DUB** — heavy feedback + long reverb tail, mostly wet, classic dub-out setting

**Tap Tempo / Manual BPM** — tap the **TAP** button to set delay time by feel, or type/step a BPM value (40–300) directly with **− / +**. The delay time syncs to the tempo automatically, and turning the DELAY TIME knob updates the BPM display.

A hand-crafted **convolution impulse response** models a spring/plate reverb tank with pre-delay, irregular early reflections, dual-band diffuse tail, subtle inharmonic spring resonance and decorrelated stereo channels — built entirely with the Web Audio API, no external samples required. The output chain ends in a compressor and a limiter.

### 💾 Persistence
- All pads, categories, favorites, mixer levels, reverb amounts, delay mutes, pad size, drawer state and echo settings are saved automatically to `localStorage`
- The actual audio file data is stored in **IndexedDB**, so your sample library survives page reloads and app restarts — fully offline, nothing uploaded anywhere
- On next launch, sounds are automatically restored and re-decoded

### ⬇ Export — ZIP of your samples
The **ZIP** button packs every loaded sample into a single `.zip` download. It's built in plain JavaScript with no libraries, using the "store" method (no recompression — audio files are already compressed — so it's fast and reliable).

### 🗑️ Full Wipe
- The **🗑 WIPE** button performs a complete factory reset: all pads, categories, favorites, mixer settings and stored audio data (IndexedDB + localStorage) are cleared
- Protected by a double confirmation, since the action is irreversible

### 🖥️ Display & comfort
- **Full screen on POWER ON** (where the browser allows it — Android Chrome, iPad, desktop) plus a **⤢ FULL / ⤡ ESCI** toggle
- **Screen Wake Lock** keeps the display on during a session
- Landscape tablet layout with a fixed Space Echo column, bigger touch targets and centered modals

### 📻 Visuals
- Reactive VU meter in the header driven by a live audio analyser
- Mirrored **output spectrum** (bass in the center, highs toward the sides) drawn after the limiter; it pauses itself when the drawer is lowered to save battery
- Spinning reel / moving tape animation on the echo unit while a sound plays
- Animated intro screen with a waving staff and floating notes
- Color-coded categories throughout pads, tabs and mixer strips
- Retro terminal/hardware aesthetic: scanlines, vignette, CRT-style glow, monospace + display fonts

### ❔ In-app guide & 🌐 English translation
- The **❔ INFO** button opens an in-app guide (start-up, daily use, Space Echo & DELAY NOW, home-screen install, how the app is built, where your audio files live)
- The interface is written in **Italian**. The optional **EN** button translates every on-screen text to English on the fly through the **Gemini API** (needs an internet connection and *your own* API key, set with the **⚙** button next to it). Translations are cached locally. Everything else in the app works fully offline and never needs a key.

### 🔎 SEO & sharing
The page ships with a full set of meta tags (description, keywords, robots), Open Graph and Twitter Card tags, schema.org `WebApplication` JSON-LD, a semantic `<h1>`, and a collapsible "about" section at the bottom of the page for search engines — in Italian and English.

---

## 🗂️ Project Structure

This is intentionally a **single HTML file** containing:

```
DubPadFX_Tablet.html
├── <head>    → SEO meta, Open Graph / Twitter, JSON-LD, embedded home-screen icons
├── <style>   → all CSS (theming, phone + tablet + landscape layouts, animations)
├── <body>    → markup (init screen, header, tabs, grid, DELAY NOW, echo unit, modals)
└── <script>  → app logic:
    ├── State (S object) + persistence (localStorage + IndexedDB)
    ├── Web Audio engine (delay, reverb IR synthesis, compressor, limiter, analyser)
    ├── Voice chain per pad (dry · delay send · reverb send) + DELAY NOW toggle
    ├── Pad management (add / remove / move / rename / reorder)
    ├── UI rendering (tabs, grid + sizes, mixer, modals, context menu)
    ├── Echo drawer (drag sheet), knobs, tap tempo, echo modes
    ├── ZIP export, VU meter, spectrum, intro animation, wake lock, fullscreen
    └── Optional EN translation layer (Gemini)
```

No bundler, no npm install, no JS frameworks. The only external resource is the Google Fonts stylesheet (`Share Tech Mono` + `Orbitron`), loaded via CDN; everything else is self-contained. The optional EN translation is the only feature that talks to a network service.

---

## 🌐 Browser Support & Requirements

- Any modern browser with **Web Audio API** and **IndexedDB** support (Chrome, Firefox, Safari, Edge — desktop or mobile)
- A user gesture (tapping **POWER ON**) is required before audio can start, per browser autoplay policies
- Full screen is not available to web pages on iPhone; it works on iPad, Android and desktop
- Best experienced on a touch device for the tap/long-press pad interactions, but fully usable with mouse + right-click on desktop

---

## 🛠️ Customization

Since everything lives in one file, most tweaks are quick edits:

- **Categories** — edit the `CAT_META` object in the script to change built-in category labels, icons or colors
- **Icon auto-detection** — extend `CAT_ICON_GUESS` to map more filename keywords to emoji
- **Reverb character** — tune the spring IR builder (decay times, band-pass ranges, resonance frequencies) to shape the spring/plate tone
- **Echo modes** — the `modes` array inside `setMode()` defines the dry/wet/feedback/reverb blend for each of the 5 preset modes
- **Feedback feel** — `fbCurve()` maps the knob position to repeat gain
- **Pad sizes** — the `.grid[data-size="…"]` rules in the CSS (phone block and tablet block) set the pad width and height for each preset
- **Theme** — colors are CSS custom properties under `:root` at the top of the stylesheet

---

## 🔐 Security note (API keys)

Because the app is a single public HTML file, **anything written inside it can be read by anyone who opens the page or the repository**. Never commit a private API key into the file. For the optional EN translation, enter your own Gemini key at runtime with the **⚙** button — it is stored only in your browser's `localStorage`. If a key was ever committed to a public repo, revoke it in your Google AI Studio / Cloud console and create a new one.

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

This project is a personal/creative audio tool. Your audio files, settings and mixer levels stay local in your browser's storage and are never uploaded anywhere. The only network request the app can make is the optional EN translation, which sends the interface's text labels (not your audio) to the Gemini API when you switch it on.

---

## 📄 License

Released under the **MIT License** — see the [`LICENSE`](LICENSE) file.

```
MIT License

Copyright (c) 2026 Swan Boccella

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

© 2026 **Swan Boccella**

---

## 🤝 Contributing

Issues and pull requests are welcome. Since it's a single-file app, most contributions can be made directly against the HTML file — please keep the "no build step" philosophy intact when proposing changes.
