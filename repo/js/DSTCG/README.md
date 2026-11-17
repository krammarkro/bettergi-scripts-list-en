# Duel Saint of TCG (DSTCG)

An automated Genius Invokation TCG duel script based on BetterGI. It can be started at any phase of a duel (initial hand selection, dice reroll, action phase, or end phase). The script automatically manages card play, character switching, skill execution, elemental tuning, dice rerolling, and ending turns, logging every decision step to `logs/` for training local models.

## Feature Overview

- **Start at Any Phase**: Automatically detects the current screen (initial hand, dice reroll, action phase, end phase) and assumes control without needing to run from the opening screen. In the end phase, it waits for settlement without making unnecessary clicks. Before ending a turn, it closes the character/skill/hand details panel on the left (which obstructs the End Round button), and verifies initiative afterwards. If the board remains unchanged for approximately 3 minutes (20 consecutive decisions), it exits automatically and saves a screenshot to avoid hanging.
- **Automated Duels**: Recognizes both players' characters, HP, active slot, Energy, elemental attachments, dice, and hand cards, automatically selecting and executing actions.
- **Action Cards**: Automatically plays Event, Support, Location, and Equipment cards. Equipment and Artifact cards automatically target the active character and confirm. Only one item is equipped per character per slot; if already equipped, it targets other characters, or skips if all are occupied. When the Support zone is full (4 cards), only significantly superior Support cards will replace the weakest card on the field. Cards requiring manual target selection for summons (e.g. "Send Off") are skipped rather than wasting an action.
- **End Phase Settlement**: Calculates damage and healing from summons, friendly/enemy Support cards, and Location cards at the "End Phase", factoring them into mortality risk assessments, end-turn evaluations, and decision scoring to prevent wasting final dice on characters about to be eliminated by summons. Played cards read badge overlays (remaining uses, duration, countdown, elemental icons, and values). Dynamic effects like Shadowy Husks are read accurately from values rather than static card text.
- **Disabling State Awareness**: Statuses preventing action (such as Frozen) are recognized (`DISABLING_STATES`). When an active character is frozen, skills are avoided and switching is prioritized.
- **Elemental Reactions & DPS Optimization**: Reads enemy elemental attachments and weights skills by reaction value (+2 for Vaporize/Melt/Overloaded, plus AoE damage from Frozen, Electro-Charged, Superconduct, and Swirl). Evaluates off-field character Burst potential, switching to damage dealers when advantageous. Switches away from low-HP characters threatened by elemental reactions.
- **Dice Utilization**: Dice do not carry over between rounds. If the model considers ending the round while 2+ dice remain and positive-value card plays or attacks exist, it executes those actions (logged with mode `+usedice`).
- **Dynamic Costs & Buffs**: Reads actual card costs from card values (including cost reductions) and tracks round-specific discounts (Energy cost reductions, switch discounts, etc.).
- **Defensive Play & Dice Reservation**: Assesses lethal risks to the active character based on enemy burst capacity, elemental reactions, and end-phase damage. Prioritizes switching to healthy tanks, playing healing/shield cards, and reserving dice needed for character swaps.
- **Low Win-Rate Surrender**: When estimated win rate drops below a threshold (default 10%) while trailing in characters, or when HP deficit reaches 35%, automatically surrenders via Top-Right Settings → Concede Match → Confirm.
- **Elemental Tuning**: When dice are insufficient, automatically discards the lowest-value hand cards to convert dice, preserving high-value cards.
- **Automatic Reroll**: Preserves Omni dice and dice matching the active character's element.
- **Local Model**: Driven by a locally trained action evaluation model, falling back to built-in expert heuristics if the model file is missing or incompatible.
- **Match Logging**: Optionally writes decision trajectories to `logs/duel_*.log` (JSONL), recording board states, candidate actions, chosen moves, scores, and outcomes for training or match replays.

## Instructions

1. Game window must be 16:9, recommended 1920×1080 windowed mode.
2. Start this script in BetterGI, then enter a Genius Invokation TCG match at any screen.
3. The script terminates automatically when the match concludes and can be restarted from BetterGI.
4. For initial runs, testing on low-risk AI matches is recommended to verify recognition and input accuracy.

### Match Trajectories & Training

Enabling `writeTrace` records matches into `logs/duel_YYYYMMDD.log` (JSONL, one line per step). The file contains board state, candidate actions, selected action, expert/model scores, initial lineup, and match outcome. This can be imported directly via the Python management tools in `开发/` to incrementally train scoring models. Trajectories are stored locally and never uploaded.

The `logs/` directory is declared in `manifest.json` under `saved_files` and persists across script updates.

### Script Settings

| Setting | Description | Default |
|---|---|---|
| `useModel` | Enable local machine learning model; uses built-in expert heuristics when disabled | Enabled |
| `modelFile` | Model file path (relative to script root) | `assets/model/policy.json` |
| `actionDelayMs` | Delay after keyboard/mouse actions; increase on slower PCs | 200 |
| `handCountMode` | Hand count detection mode: Auto / Digit Recognition / Template Matching / Off | Auto |
| `useActionCards` | Recognize and play action cards; when disabled, hand cards are only used for tuning | Enabled |
| `scanZones` | Recognize Support and Summons zones for both sides | Enabled |
| `zoneClickFallback` | Click cards in zones for details when confidence is low | Enabled |
| `characterStateScan` | Click active characters to read states and faction status from details panel | Enabled |
| `writeTrace` | Write match trajectories to `logs/duel_*.log` for model training | Enabled |
| `detailLog` | Output verbose debug logs | Disabled |
| `autoSurrender` | Automatically surrender when estimated win rate is excessively low | Enabled |
| `surrenderThreshold` | Win rate surrender threshold (%): 0/5/10/15/20/25/30 | 10 |

## FAQ

- **Hand Card Shows "Unknown"**: Hover OCR did not recognize the card name. Unknown cards will not be played proactively, but participate in elemental tuning at median valuation without interrupting play.
- **Equipment/Artifact Not Equipped**: The script automatically clicks the "Confirm" button; if it fails repeatedly, it skips the card for the rest of the match.
- **Unable to Play Certain Cards**: Hand card count is verified prior to play with retries; after 4 consecutive failures, playing action cards is suspended for that match.
- **Stuck on a Screen**: Manually end the turn or close popups to resume. The script exits automatically if the board is unreadable or unchanged for 3 minutes (saving `debug_no_progress_*.png`).
- **Support / Summons Show Unknown**: New cards lacking templates will fallback to reading card details on click.
- **Clicks Do Not Register**: Increase `actionDelayMs` in settings (e.g. to 300~500 ms).

## Directory Structure

```
DSTCG/
├── main.js               # Main script
├── manifest.json         # BetterGI manifest
├── settings.json         # Settings UI
├── assets/               # Card database, models, recognition templates
├── logs/                 # Match trajectories and debug screenshots
└── 开发/                 # Developer tools (not needed for normal use)
```

## Known Limitations

- Calibrated for 16:9 PC client UI; other aspect ratios or cloud gaming require recalibration.
- Hand card names depend on hover OCR; layout shifts may cause cards to register as "Unknown".
- Event cards requiring secondary target selection (discovery, random selection, hand exchange, discarding) are skipped.
- Support cards and summons rely on template matching (calibrated at 1920×1080).
- Card cost templates currently include 0/1/2/3/5; unrecorded costs (4, 6) default to static database costs.

## Developer Documentation

For backend administration, dataset import, model training, template creation, and asset pack generation, see [开发/README.md](开发/README.md).

## Author

TeyvatFishing玳师 · Feedback Email: hijiwos@hotmail.com
