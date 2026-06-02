# 🦞 Lobster Pinch

A webcam hand-tracking game. Lobsters swim around your screen — **pinch your thumb and index finger together** right on one to catch it. Rack up as many as you can before the timer runs out.

Built with [MediaPipe Hands](https://developers.google.com/mediapipe) running entirely in the browser. **Your camera feed never leaves your device** — there's no backend, nothing is uploaded.

## Play

👉 **https://ashleywolf.github.io/lobster-pinch/**

1. Click **Allow camera & play** and grant camera permission.
2. Hold your hand up in front of the webcam.
3. Pinch thumb + index together on a lobster to catch it.

Works best in a well-lit room with your hand clearly visible.

## Run locally

It's a single static file. Camera access needs a secure context, so use `https://`, `http://localhost`, or GitHub Pages — opening the file directly (`file://`) won't get camera permission in most browsers.

```bash
# any static server works, e.g.
python3 -m http.server 8000
# then open http://localhost:8000
```

## How it works

- `@mediapipe/hands` detects 21 hand landmarks per frame from the webcam.
- A **pinch** is the normalized distance between the thumb tip (landmark 4) and index tip (landmark 8) dropping below a threshold (with hysteresis to avoid flicker).
- The pinch midpoint becomes your on-screen cursor; if it's within the catch radius of a lobster while pinching, you snag it.

## Tech

Plain HTML/CSS/JS, no build step. MediaPipe loaded from CDN. Deployed via GitHub Pages.
