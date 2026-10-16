# KeyChess

**Think. Type. Take.**

KeyChess is a chess puzzle trainer built to improve focus. You don't drag pieces. You look at the position, think, and type the whole line: your moves and the opponent's replies. To type it, you have to calculate it first.

Version: **v0.5.1**

No account, no ads, no subscription. Progress is saved on your device only.

## How it works

1. Pick the number of puzzles (25, 50, 75 or 100), a rating band and a theme on the Home screen. The session starts right away.
2. The app plays the opponent's first move. The chip at the top shows how many moves you have to type.
3. Type the full line with the on-screen keyboard or your physical keyboard. Space enters a move. Press **Check**.
4. Puzzles you miss go to **Review**. Replay a session from **Training** to add cycles. **Stats** shows your progress.

### Show errors

The switch above the board controls error feedback:

- **On:** illegal moves turn red while you type, and wrong moves turn red after Check.
- **Off:** nothing turns red. You only learn whether the whole line is right or wrong, which is harder.

### Keyboard shortcuts

| Key | Action |
| --- | --- |
| `K Q R B N` | Piece letters |
| `a`-`h`, `1`-`8` | Files and ranks |
| `x`, `+`, `#`, `=` | Capture, check, mate, promotion |
| `o` / `O` / `0` | Castling (`O-O`, `O-O-O`) |
| `Space` | Enter the current move |
| `Backspace` | Delete last character |
| `Enter` | Check (or Next, when finished) |
| `Esc` | Clear everything typed |

Standard algebraic notation is expected. Symbols such as `x`, `+`, `#` and `=` are ignored when comparing your move, and a final checkmate move is accepted even if it differs from the stored solution.

## Screens

- **Home:** choose puzzle count, rating band and theme.
- **Training:** the Review list plus every saved session. Tap a session to replay it. Each session has a small **✕** to delete it, and a **Delete all sessions** button sits at the bottom of the list. Both ask for confirmation. Deleting sessions keeps your Review list and stats.
- **Stats:** puzzles solved, accuracy and a monthly calendar marking the days you trained.
- **Settings:** piece set and theme.
- **Info** and **Price/support** pages (the `i` and `$` buttons on Home).

### Themes

Mix, Mates, Forks, Pins, Skewers, Discovered, Deflection, Back rank, Hanging, Sacrifice, Double check, Trapped piece, Attraction, Clearance, Interference, Intermezzo, X-ray, Quiet move, Zugzwang, Smothered, Promotion, Opening, Middlegame, Endgame.

### Rating bands

`<1000`, `1000-1200`, `1200-1400`, `1400-1600`, `1600-1800`, `1800-2000`, `2000+`

### Pieces and color themes

- Pieces: Chessnut, RhosGFX
- Themes: Black, Sepia, Blue night

## Running it

KeyChess is a single static page with no build step. Because it loads puzzle files with `fetch`, it must be opened through a web server, not by double-clicking `index.html`.

```
KeyChess/
├── index.html
├── img/
│   └── friends.webp          (optional, shown on the $ page)
└── keychess_puzzles/
    ├── mix.json
    ├── mates.json
    ├── forks.json
    └── ...                   (one file per theme id)
```

Serve the folder with any static server, for example:

```
python3 -m http.server 8000
```

Then open `http://localhost:8000`.

If a puzzle file is missing or can't be loaded, the app tells you and falls back to two built-in demo puzzles.

## Puzzle file format

Each `keychess_puzzles/<theme>.json` is an array of puzzles. Each puzzle is an array:

```json
["id", "FEN", "move1 move2 move3 ...", rating]
```

- `id`: unique puzzle id (used to avoid repeats between sessions).
- `FEN`: the position **before** the opponent's first move.
- Moves in UCI format (e.g. `e2e4`, `e7e8q`). The first move is the opponent's move played automatically. The rest is the solution line.
- `rating`: puzzle rating, used for the rating bands.

The theme ids match the list above in lowercase without spaces: `mix`, `mates`, `forks`, `pins`, `skewers`, `discovered`, `deflection`, `backrank`, `hanging`, `sacrifice`, `doublecheck`, `trapped`, `attraction`, `clearance`, `interference`, `intermezzo`, `xray`, `quietmove`, `zugzwang`, `smothered`, `promotion`, `opening`, `middlegame`, `endgame`.

## Data and privacy

Everything is stored in your browser's `localStorage`. Nothing is sent anywhere.

| Key | Content |
| --- | --- |
| `kc_pref` | Preferences (puzzle count, rating band, piece set, theme, show errors) |
| `kc_s` | Saved sessions |
| `kc_r` | Review list |
| `kc_st` | Stats (played, solved, clean, days trained) |
| `kc_u` | Puzzles already used, to avoid repeats |

Clearing site data resets all progress.

## Credits

- **Puzzles:** Lichess open puzzle database (CC0). Not affiliated with Lichess.
- **Chess rules:** [chess.js](https://github.com/jhlywa/chess.js) by Jeff Hlywa (BSD 2-Clause), bundled in `index.html`.
- **Pieces:** Chessnut by Alexis Luengas (Apache 2.0). RhosGFX (CC0).
- **Code:** written with Claude, an AI assistant by Anthropic.
- **Created by** Carlos Nada, keychessapp@gmail.com


<!--
**keychessapp/keychessapp** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
