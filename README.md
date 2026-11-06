# Braylein's Truck &amp; Dino Tap 🛻🦖

A bright, friendly tap game for young kids, themed around monster trucks and dinosaurs. The whole game is a **single self-contained `index.html`** with inline CSS and JavaScript. There is **no build step, no dependencies, and no external resources**, so it works fully offline. Just open the file in any modern browser (phone or desktop) and play.

## What it is

Trucks and dinosaurs pop up out of a field of 9 dirt mounds. Tap the monster trucks to score points. The dinosaurs are friends, so tapping one by accident costs a point and the dino does a little shake. Catch a lucky star for a bonus. Each round lasts 60 seconds, and scores are saved to a leaderboard.

Designed for a child on a phone: portrait layout, big bright chunky buttons that squish when pressed, large text (at least 18px), huge touch targets, gentle animated background, bouncy pop-ups, and happy synthesized sound effects.

## How to play

1. On the start screen, type your name (it is remembered for next time).
2. Tap **▶️ Play!** to begin a 60-second round.
3. Trucks and dinosaurs pop up one or two at a time, each visible for about a second.
   - Tap a **monster truck** (🛻 🚚 🚙) to score.
   - Leave the **dinosaurs** (🦖 🦕) alone, they are friends.
   - Grab a **star** (⭐) when it appears for a bonus.
4. When the timer reaches 0, the round ends with a confetti burst and your final score.
5. Tap **🔁 Play Again!** for another round, or **🏆 Leaderboard** to see the top scores.

Use the **🔊 / 🔇** button during a game to turn sound on or off. Sound is **ON by default**.

## Scoring

| Item | Emoji | Points |
|------|-------|--------|
| Monster truck | 🛻 🚚 🚙 | **+1** |
| Dinosaur (a friend!) | 🦖 🦕 | **-1** (score never goes below 0), dino shakes |
| Star (bonus) | ⭐ | **+3** |

A round is **60 seconds**, shown with a big countdown that turns red in the final 10 seconds.

## Leaderboard

- When a round ends, the game saves `{ name, score, date }` to your browser's `localStorage`.
- The **Leaderboard** screen (reachable from both the start screen and the end screen) shows the **top 10 scores, highest first**, with name, score, and date.
- The **🗑️ Clear board** button has a two-tap confirm step: tap once to arm it, tap again within a few seconds to actually wipe the local board.
- The leaderboard persists across page reloads.

## Online family board (optional) and offline fallback

The game includes one clearly marked **`FAMILY SCORES SERVER`** section that shares scores across the family:

- **POST** each finished score to `https://games.cardcauldrontcg.com/scores`
  - Headers: `X-Family-Key: family-games-2026` and `Content-Type: application/json`
  - Body: `{ "game": "braylein-truck-dino", "name": name, "score": score }`
- **GET** the shared board from `https://games.cardcauldrontcg.com/scores?game=braylein-truck-dino` with the same `X-Family-Key` header. When it loads successfully, the Leaderboard screen shows the online **🌐 Family board**.

This online piece is **fully optional and safe**:

- Posting is **fire-and-forget in the background** and never blocks or breaks gameplay.
- Every network call is wrapped in `try/catch` and uses an `AbortController` with a short (~2.5 second) timeout.
- On **any failure, timeout, or no connection**, the game **silently falls back** to the local `localStorage` leaderboard.
- The game is **fully playable with no internet connection**.

## Sound

All sound effects are synthesized at runtime with the **Web Audio API** (no audio files):

- a quick **pop** when you tap a truck,
- a happy little **cheer** arpeggio on a star,
- a soft low **tone** when you tap a dino.

The audio context is created and resumed on the first user gesture (required by browsers), and respects the on/off toggle.

## Tech notes

- Single file: `index.html` (one inline `<style>`, one inline `<script>`).
- Pure vanilla JavaScript, emoji + CSS graphics only, no images or external fonts.
- Validate the script with: extract the inline `<script>` body and run `node --check` on it.
