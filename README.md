# Braylein's Truck &amp; Dino Tap 🛻🦖

A bright, friendly tapping game for a young child playing on a phone. Monster
trucks pop out of dirt mounds, so tap them fast! Dinosaurs are friends, so leave
them alone. Now with 5 levels, coins, power-ups, and a shop full of rewards.
The whole thing is still one self-contained `index.html` file: inline CSS and
JavaScript, no external files, no build step, and it works fully offline.

## What it is

- A 3×3 field of dirt mounds. Monster trucks 🛻🚚🚙, dinosaurs 🦖🦕, and the
  occasional lucky star ⭐ pop up one or two at a time for about a second.
- 5 levels of growing difficulty. Each level is a 60-second round with a big
  countdown timer.
- Coins you earn by playing, spent in a shop on fun rewards (truck styles,
  scenes, horn sounds) and on in-round power-ups. There are no real-money
  purchases anywhere.
- Giant touch targets, chunky rounded buttons, bright colors, and a gentle
  animated background with drifting clouds, all emoji + CSS. The background
  re-themes to match the scene you have equipped.
- Happy WebAudio sound effects (a pop on tap, a cheer when the round ends, plus
  unlockable horn sounds) with a sound on/off button in the top-right corner.
  Sound is **on** by default.
- A confetti/star burst celebration when the round finishes.
- Per-player progress (coins, unlocked levels, owned and equipped rewards, and
  your best score on each level) saved on the device under your name.

## How to play

1. Open `index.html` in any phone or desktop browser (no internet needed).
2. Type your name in the friendly name box. It's remembered for next time, and
   your coins and progress are saved under that name.
3. Press **▶️ Play!**, then pick a level from the level select screen.
4. **Tap monster trucks** as they pop up. The tile bounces and pops.
5. **Don't tap the dinosaurs**, they're friends. If you tap one it shakes and
   you lose a point.
6. **Grab the stars** ⭐ for bonus points when they appear.
7. When the 60 seconds run out, see your final score and the coins you earned,
   then press **🔁 Play Again** or visit the **🏆 Leaderboard**.

## Scoring

| Thing you tap | Points |
| ------------- | ------ |
| 🛻 Monster truck | **+1** |
| ⭐ Star | **+3** |
| 🦖 Dinosaur (friend, don't tap!) | **-1** (never below 0) |

## Levels

The game has 5 levels. Each level is its own 60-second round, and the levels get
harder as you climb:

- Trucks and dinosaurs pop up **faster** and **stay up for less time**.
- **More dinosaurs** are mixed in (so you have to watch what you tap).
- **Stars get rarer**, so the easy bonus points dry up.

**Level 1 is gentle** and made for a young child: slow pop-ups, long up-times,
only about a quarter dinosaurs, and plenty of stars. By Level 5 things pop up
quickly, up-times are short, over half of the pop-ups are dinosaurs, and stars
are rare.

Each level has a **target score**. The level select screen shows every level
with its target and whether it is **locked** or **unlocked**. Finishing a round
with **at least the target score** unlocks the next level. You start with only
Level 1 unlocked.

| Level | Target score |
| ----- | ------------ |
| Level 1 | **10** |
| Level 2 | **15** |
| Level 3 | **22** |
| Level 4 | **30** |
| Level 5 | **40** |

## Coins

You earn coins just by playing. There are **no real-money purchases** anywhere
in the game.

- **1 coin for every 5 points** you score in a round (for example, 23 points
  earns 4 coins).
- A **+5 coin bonus** for beating that level's target score.

Your coin total is shown on the start screen (and on the level, shop, and
rewards screens) and is **saved per player** on the device. Spend coins in the
shop on rewards, or on power-ups during a round.

## Power-ups

Power-ups are bought with coins and used **during a round**. Their buttons show
the price, and a button is **disabled when you don't have enough coins**.

| Power-up | Cost | What it does |
| -------- | ---- | ------------ |
| 🐢 Slow-Mo | **8 coins** | Everything pops up slower for 10 seconds. |
| ⏱️ Extra Time | **6 coins** | Adds 10 seconds to the clock. |

## Shop &amp; Rewards

Visit the **🛒 Shop** to spend your coins on fun stuff. Everything you buy is
**saved per player**. Then open the **🎁 Rewards** screen to **select and equip**
what you own. Your equipped choices are saved per player too.

**Truck styles** (changes the trucks you tap):

| Style | Cost |
| ----- | ---- |
| Classic Trucks 🛻 | **free** |
| Builder Crew 🚛 | **20 coins** |
| Speedy Racers 🏎️ | **35 coins** |

**Scenes** (re-themes the animated background):

| Scene | Cost |
| ----- | ---- |
| Desert 🏜️ | **free** (default) |
| Jungle 🌴 | **15 coins** |
| Volcano 🌋 | **30 coins** |
| Snow ❄️ | **30 coins** |

**Horn sounds** (the sound a truck makes), all synthesized with Web Audio, no
audio files:

| Horn | Cost |
| ---- | ---- |
| Beep Beep 🔔 | **free** |
| Big Air Horn 📯 | **18 coins** |
| Clown Honk 🤡 | **18 coins** |
| Train Whistle 🚂 | **25 coins** |

Buying the Jungle, Volcano, or Snow scene and equipping it re-themes the whole
animated background, and it all stays offline and self-contained.

## Leaderboard &amp; where scores are saved

- **Online family leaderboard:** scores are submitted to a shared family scores
  server and the Leaderboard screen shows the family's top 10 (highest first)
  when the server is reachable. Submitting happens quietly in the background and
  never blocks or interrupts play.
- **Offline fallback (saved on the device):** every finished score is *always*
  also saved locally in your browser's `localStorage`. If there's no internet,
  or the server is slow or unavailable, the game still works perfectly and the
  Leaderboard falls back to the scores saved on **this device**. Your name is
  saved on the device too, so it's ready next time.
- The Leaderboard is reachable from both the start screen and the end screen and
  shows whether it's displaying the 🌐 family online board or the 📵 offline
  (this-device) board.
- A small **🗑️ Clear Board** option (with a confirm step) clears the scores
  saved on this device. It does not affect the family online board.

When a round ends, the game saves your score locally and submits it to the
family server exactly as before, in addition to awarding coins and updating your
progress.

## Technical notes

- Everything lives in a single `index.html`. No external resources, no build.
- The only network calls are to the family scores server, and they're kept in
  one clearly marked `FAMILY SCORES SERVER` section near the top of the script,
  each wrapped with a short timeout so a failure silently falls back to offline.
- Per-player progress (coins, unlocked levels, owned and equipped rewards, and
  the best score on each level) is saved in the browser's `localStorage` under
  the player's name, alongside the saved scores and the sound on/off setting.
- Sound uses the Web Audio API only (no audio files), including the unlockable
  horn sounds, so the game stays fully offline and self-contained.
