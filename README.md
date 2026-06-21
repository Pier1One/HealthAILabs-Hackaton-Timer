# Hackathon Timer — SIIAM Health AI Labs

A single-file web app for managing hackathon schedules in real time. No server, no install, no build step — just open `index.html` in a browser.

## Features

- **Live countdown timer** — auto-detects the current activity from your wall clock; no manual start needed
- **Visual alerts** — timer turns orange at ≤5 min remaining, red and pulsing at ≤1 min
- **Audio chime** — plays a tone at each activity transition via Web Audio API (no external files)
- **+10 min postpone** — shifts the current activity's end time and the next activity's start time forward by 10 minutes
- **Full CRUD** — add, edit, and delete activities inline
- **Persistent** — schedule survives page reloads via `localStorage`
- **Offline** — no CDN or network dependency

## Usage

1. Download or clone this repo
2. Open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge)
3. Add your activities using the form at the bottom — enter a name, start time, and end time
4. The timer at the top will automatically show the current activity and count down to its end

## How It Works

- Activities are stored as `{ id, name, startTime, endTime }` in `localStorage` under the key `hackathon_schedule`
- Every second, the app compares the current wall-clock time against the schedule to determine the active activity
- The +10 min button only shifts the current activity's end and the immediately following activity's start — all other activities are unchanged
- Audio is generated programmatically using the Web Audio API (no `.mp3` files needed)

> **Note on audio:** browsers require a user gesture before playing audio. Clicking any button (Add, Edit, +10 min) before the first transition satisfies this requirement.

## Tech Stack

- Vanilla HTML, CSS, and JavaScript — no frameworks, no dependencies
- Web Audio API for chime generation
- `localStorage` for persistence

## License

MIT
