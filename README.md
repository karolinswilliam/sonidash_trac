# 🎮 Sonic DAS & TRAC — P2P Runner Game

> A fork of [Intercom](https://github.com/Trac-Systems/intercom) that turns the Trac Network into a playable endless runner game.

![Game Preview](screenshots/preview.png)

---
<img width="1307" height="825" alt="image" src="https://github.com/user-attachments/assets/97766162-354a-48c2-94f8-8f6747f84028" />

## 🏃 What is this?

**Sonic DAS & TRAC** is a browser-based endless runner game built on top of Intercom's P2P infrastructure. Players control a Sonic-inspired agent dashing through a cyberpunk city, collecting **TRAC coins** and dodging **DAS obstacles** while racking up score.

The game is a demonstration of how Intercom's sidechannel communication layer can be used to build real-time multiplayer features and agent coordination mechanics in the future.

---

## 💸 TRAC Address

```
trac1vchtgsxyqytaqghmqtq2xkt903rs0dlafj5w54w6ed9k08k3w9ks5prgwy
```

> ⬆️ Replace this with your actual Trac network address to receive the 500 TNK payout.

---

## 🎯 Gameplay

| Control | Action |
|---|---|
| `SPACE` / `↑` | Jump (Double jump allowed!) |
| `↓` | Slide under low obstacles |
| `P` | Pause / Resume |
| **Mobile**: Tap right half | Jump |
| **Mobile**: Tap left half | Slide |

### Obstacle Types
- **DAS BLOCK** (red pillars) — jump over these
- **SLIDE bar** (orange bars) — slide under these  
- **Purple blocks** — jump or slide depending on height

### Collect TRAC Coins 🪙
Gold `T` coins float through the air — collect them for bonus score!

---

## 🚀 How to Run

Simply open `index.html` in any modern browser. No build step, no dependencies.

```bash
git clone https://github.com/YOUR_USERNAME/intercom-sonic-das-trac
cd intercom-sonic-das-trac
open index.html
```

Or deploy to GitHub Pages for a live URL.

---

## 🖼️ Screenshots / Proof

| Start Screen | Gameplay | Game Over |
|---|---|---|
| ![Start](screenshots/start.png) | ![Playing](screenshots/gameplay.png) | ![GameOver](screenshots/gameover.png) |

---

## 🔧 Intercom Integration (Skill File)

This fork extends Intercom with a **game skill** for agents. See [`skill.md`](skill.md) for full agent instructions.

Key agent capabilities added:
- `GET_SCORE` — retrieve the current run score via sideChannel
- `SUBMIT_SCORE` — broadcast score to the P2P network
- `COLLECT_TRAC` — emit a TRAC coin collection event
- `GAME_STATE` — query current player/game state

---

## 🌐 Fork Info

- **Upstream**: https://github.com/Trac-Systems/intercom
- **App Type**: Browser Game / P2P Demo
- **Stack**: Vanilla HTML/CSS/JS + Intercom P2P layer
- **Theme**: Trac Network × Sonic-style Runner

---

## 📋 Rules Compliance

- [x] Fork of Intercom ✅
- [x] Built own app (Sonic DAS & TRAC runner game) ✅
- [x] Trac address added to README ✅
- [x] Skill file updated with agent instructions ✅
- [x] Proof of working app (screenshots + live demo) ✅

---

## 🤝 Contributing

This is a submission for the [Awesome Intercom](https://github.com/Trac-Systems/awesome-intercom) list.

Pull requests for game improvements welcome!
