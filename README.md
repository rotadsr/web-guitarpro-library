# Guitar Pro Library

A single-file browser app for opening, browsing, and playing Guitar Pro tabs — no installation or build step required.

Try it live: https://rotadsr.github.io/web-guitarpro-library/

## Features

- **Tab viewer & player** — renders score + tablature via [AlphaTab](https://alphatab.net), with play/pause/stop, seek bar, and tempo control
- **Library sidebar** — sample files included; drag-and-drop or open your own `.gp`, `.gp3`, `.gp4`, `.gp5`, `.gpx`, `.gptx` files
- **Search** — filter by song title, artist, genre, composer, album, or year
- **Mixer** — per-track mute, solo, volume, and pan knob
- **Sound selector** — change the MIDI instrument program per track (guitar, bass, drums, keys, brass, etc.)
- **Section navigation** — color-coded bar grid with section labels (Intro, Verse, Chorus, Solo, …); sections are auto-detected from the file or set manually
- **Metadata editor** — edit title, artist, genre, composer, album, year, and a YouTube URL per file; persisted in `localStorage`
- **YouTube sync** — link a YouTube URL to a tab and sync AlphaTab playback with the video (requires a web server — see below)
- **Score zoom & grid zoom** — independent zoom controls for the sheet music and bar grid

## Usage

Open `index.html` directly in a browser:

```
open index.html          # macOS
start index.html         # Windows
```

Most features work with a plain file URL. **YouTube sync requires a web server** because the YouTube IFrame API blocks `file://` origins. Serve from any static host:

```bash
python3 -m http.server 8080
# then open http://localhost:8080
```

Or deploy to [GitHub Pages](https://pages.github.com) — the included `.gp` sample files are committed alongside `index.html` and will load automatically.

## Adding your own tabs

Click **Open file…** in the sidebar and pick any Guitar Pro file. Files are loaded in-memory only — nothing is uploaded anywhere.

## Tech

- [AlphaTab](https://alphatab.net) (CDN) — score rendering and MIDI playback
- [YouTube IFrame API](https://developers.google.com/youtube/iframe_api_reference) (loaded on demand) — video sync
- `localStorage` — persists metadata, section overrides, and track settings per file
- Zero build step, zero dependencies to install
