# Braylein's Truck &amp; Dino Tap 🛻🦖

A bright, friendly tapping game for a young child playing on a phone. Monster
trucks pop out of dirt mounds — tap them fast! Dinosaurs are friends, so leave
them alone. The whole thing is one self-contained `index.html` file: inline CSS
and JavaScript, no external files, no build step, and it works fully offline.

## What it is

- A 3×3 field of dirt mounds. Monster trucks 🛻🚚🚙, dinosaurs 🦖🦕, and the
  occasional lucky star ⭐ pop up one or two at a time for about a second.
- A 60-second round with a big countdown timer.
- Giant touch targets, chunky rounded buttons, bright colors, and a gentle
  animated desert/dino background with drifting clouds — all emoji + CSS.
- Happy WebAudio sound effects (a pop on tap, a cheer when the round ends) with
  a sound on/off button in the top-right corner. Sound is **on** by default.
- A confetti/star burst celebration when the round finishes.

## How to play

1. Open `index.html` in any phone or desktop browser (no internet needed).
2. Type your name in the friendly name box. It's remembered for next time.
3. Press **▶️ Play!** and start tapping!
4. **Tap monster trucks** as they pop up. The tile bounces and pops.
5. **Don't tap the dinosaurs** — they're friends. If you tap one it shakes and
   you lose a point.
6. **Grab the stars** ⭐ for bonus points when they appear.
7. When the 60 seconds run out, see your final score and press
   **🔁 Play Again** — or visit the **🏆 Leaderboard**.

## Scoring

| Thing you tap | Points |
| ------------- | ------ |
| 🛻 Monster truck | **+1** |
| ⭐ Star | **+3** |
| 🦖 Dinosaur (friend — don't tap!) | **−1** (never below 0) |

## Leaderboard &amp; where scores are saved

- **Online family leaderboard:** scores are submitted to a shared family scores
  server and the Leaderboard screen shows the family's top 10 (highest first)
  when the server is reachable. Submitting happens quietly in the background and
  never blocks or interrupts play.
- **Offline fallback (saved on the device):** every finished score is *always*
  also saved locally in your browser's `localStorage`. If there's no internet —
  or the server is slow or unavailable — the game still works perfectly and the
  Leaderboard falls back to the scores saved on **this device**. Your name is
  saved on the device too, so it's ready next time.
- The Leaderboard is reachable from both the start screen and the end screen and
  shows whether it's displaying the 🌐 family online board or the 📵 offline
  (this-device) board.
- A small **🗑️ Clear Board** option (with a confirm step) clears the scores
  saved on this device. It does not affect the family online board.

## Technical notes

- Everything lives in a single `index.html`. No external resources, no build.
- The only network calls are to the family scores server, and they're kept in
  one clearly marked `FAMILY SCORES SERVER` section near the top of the script,
  each wrapped with a short timeout so a failure silently falls back to offline.
- Sound uses the Web Audio API only (no audio files).
