# 🦞 Lobster Pinch.

A webcam hand-tracking game. Lobsters swim around your screen — **pinch your thumb and index finger together** right on one to catch it. Rack up as many as you can before the timer runs out. **Up to four hands can play at once**, and the game runs continuously — when time's up it shows your score for 10 seconds, then auto-starts the next round.

Built with [MediaPipe Hands](https://developers.google.com/mediapipe) running entirely in the browser. **Your camera feed never leaves your device** — there's no backend, nothing is uploaded.

## Play

👉 **https://ashleywolf.github.io/lobster-pinch/**

1. Click **Allow camera & play** and grant camera permission.
2. Hold your hand (or several hands — one per player) up in front of the webcam.
3. Pinch thumb + index together on a lobster to catch it.

Rounds restart automatically, so you can keep playing without touching the keyboard.

Works best in a well-lit room with your hand clearly visible.

## Run locally

It's a single static file. Camera access needs a secure context, so use `https://`, `http://localhost`, or GitHub Pages — opening the file directly (`file://`) won't get camera permission in most browsers.

```bash
# any static server works, e.g.
python3 -m http.server 8000
# then open http://localhost:8000
```

## How it works

- `@mediapipe/hands` detects 21 hand landmarks per frame from the webcam, for up to four hands at once.
- A **pinch** is the normalized distance between the thumb tip (landmark 4) and index tip (landmark 8) dropping below a threshold (with hysteresis to avoid flicker).
- Each hand gets its own on-screen cursor; if a hand's pinch midpoint is within the catch radius of a lobster the moment it pinches, that player snags it (+1).

## Tech

Plain HTML/CSS/JS, no build step. MediaPipe loaded from CDN. Deployed via GitHub Pages.
