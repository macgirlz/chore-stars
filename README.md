# Chore Stars ⭐

A family-friendly web app that helps kids track chores, earn stars, and play learning games—all in one place. No backend required: everything runs in the browser and data is stored locally.

## What it does

- **Multi-kid support** — Add multiple kids with custom names, emoji avatars, and theme colors. Switch between them from the header.
- **Chores** — Define chores with emojis, schedules (daily or one-time), and types (timed or quick). Set target duration and star rewards. Start, pause, or complete chores with optional timers.
- **Today** — Greeting, progress (e.g. “3/5 done”), total stars earned today, active chore cards, and a list of completed chores.
- **Wallet** — Total stars balance and transaction history. Add manual transactions (tied to a chore or custom) for bonuses or one-off rewards.
- **Calendar** — Browse past days and see completed sessions and credits.
- **Learn & Play** — Four built-in games, opened in an in-app overlay:
  - **Word Wizard** — Hangman-style word guessing (by grade and category).
  - **Harper's Sudoku** — Classic 9×9 Sudoku.
  - **Harper's Math Camp** — Math practice (multiplication, fractions, patterns, and more).
  - **Picture Puzzles** — Themed jigsaw-style puzzles (space, oceans, animals, world, etc.).
- **Parent PIN** — Optional 4-digit PIN to protect parent-only actions (e.g. editing transactions or settings).
- **Celebrations** — On chore completion: a celebration popup and flying stars to the wallet chip.

Data is stored in the browser’s `localStorage` (per kid: chores, sessions, timers, wallet). No server or account is required.

## How to run

1. Clone the repo and open the project folder.
2. Serve the files over HTTP (e.g. with a local server). Opening `index.html` via `file://` may work but can have limitations (e.g. iframes, storage).
3. Open `index.html` in your browser (e.g. `http://localhost:8080/` if using a local server).

Example with Python:

```bash
# Python 3
python3 -m http.server 8080
```

Then visit `http://localhost:8080/` and use the app. On first run you’ll be prompted to add a kid; you can add sample chores or create your own.

## Project structure

| File           | Purpose |
|----------------|--------|
| `index.html`   | Main app: Today, Chores, Wallet, Learn, Calendar; kid/chore/wallet logic; game launcher. |
| `word-wizard.html` | Word Wizard (hangman) game. |
| `sudoku.html`  | Harper's Sudoku game. |
| `math-camp.html`   | Harper's Math Camp game. |
| `puzzle.html`  | Picture Puzzles game. |

All logic and styles are in the respective HTML files (no separate build step). Games are loaded in an iframe from the main app’s **Learn** tab.

## Tech notes

- Vanilla HTML, CSS, and JavaScript.
- State: `localStorage` keys like `cs_kids`, `cs_active_kid`, and per-kid `cs_chores_<id>`, `cs_sessions_<id>`, `cs_timers_<id>`, `cs_wallet_<id>`.
- Responsive layout with a fixed header, bottom nav, and optional FAB on the Chores view.
- Timers are paused when the page is hidden (`pagehide`) so time doesn’t accrue in the background.

## License

Use and modify as you like. No warranty.
