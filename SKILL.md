# Skill: Sonic DAS & TRAC Runner Game

## Description
This skill enables Intercom agents to interact with the Sonic DAS & TRAC browser game. Agents can read game state, submit scores to the P2P network, trigger coin collection events, and coordinate multiplayer sessions over Intercom sidechannels.

## Agent Instructions

### Available Commands

#### `GET_SCORE`
Retrieves the current game score from the active run.
```json
{
  "action": "GET_SCORE",
  "response": {
    "score": 1234,
    "trac_collected": 7,
    "speed": 8.5,
    "alive": true
  }
}
```

#### `SUBMIT_SCORE`
Broadcasts the final score to the Intercom P2P network after a run ends.
```json
{
  "action": "SUBMIT_SCORE",
  "payload": {
    "score": 4200,
    "trac_collected": 15,
    "trac_address": "YOUR_TRAC_ADDRESS_HERE",
    "timestamp": 1700000000
  }
}
```

#### `COLLECT_TRAC`
Emits a TRAC coin collection event to be logged on the replicated state layer.
```json
{
  "action": "COLLECT_TRAC",
  "payload": {
    "coin_id": "coin_xyz_123",
    "player": "YOUR_TRAC_ADDRESS_HERE",
    "value": 1
  }
}
```

#### `GAME_STATE`
Returns full current game state snapshot.
```json
{
  "action": "GAME_STATE",
  "response": {
    "running": true,
    "paused": false,
    "score": 800,
    "trac": 3,
    "best": 5200,
    "speed": 7.2,
    "obstacles_ahead": 2,
    "player": {
      "alive": true,
      "jumping": false,
      "sliding": false,
      "jumps_remaining": 2
    }
  }
}
```

#### `LEADERBOARD`
Requests the P2P leaderboard from connected peers.
```json
{
  "action": "LEADERBOARD",
  "response": {
    "entries": [
      { "trac_address": "addr1...", "score": 9999, "trac": 42 },
      { "trac_address": "addr2...", "score": 7800, "trac": 31 }
    ]
  }
}
```

---

## Sidechain Events

This skill emits the following events over Intercom sidechannels:

| Event | Trigger | Payload |
|---|---|---|
| `game:start` | Run begins | `{ timestamp, player_addr }` |
| `game:coin` | TRAC coin collected | `{ coin_id, total_trac }` |
| `game:death` | Player hits obstacle | `{ score, trac, speed }` |
| `game:highscore` | New personal best | `{ score, trac_addr }` |

---

## Replicated State Keys

The following keys are written to Intercom's replicated state layer:

- `scores/{trac_address}` — best score for each player
- `leaderboard/global` — top 100 scores across all players
- `trac_collected/{trac_address}` — cumulative TRAC coins gathered

---

## Setup for Agents

1. Clone this fork of Intercom
2. Load `index.html` in a browser
3. Connect to the Intercom P2P network using your Trac keypair
4. Agents will auto-discover the game skill and can send commands via sidechannel messages

---

## Notes

- All score submissions are signed with the player's Trac key
- The game runs entirely client-side; no server required
- Future versions will support live multiplayer racing over Intercom sidechannels
