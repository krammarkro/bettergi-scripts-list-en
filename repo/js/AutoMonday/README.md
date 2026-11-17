# Auto Monday (AutoMonday)

One-stop execution for various weekly and monthly tasks in Genshin Impact, including the Parametric Transformer, Escoffier Food Device, Battle Pass Weeklies, Omni-Ubiquity Net, Investment Coupons, and Stardust Exchange.

## Features

- **Parametric Transformer**: Select fuel materials and charge using Electro Crystals or Catalyst characters.
- **Escoffier Food Device**: Independently enabled with independent charging method selection.
- **Battle Pass Weeklies**: Cooking, Forging, Boss defeats, and Domain Challenges.
- **Max BP Level Detection**: Once BP reaches Level 50, individual Battle Pass weekly tasks can be skipped automatically.
- **Weekly Omni-Ubiquity Net Purchase**.
- **Weekly Investment Coupon Submission**.
- **Monthly Paimon's Bargains Stardust Exchange**: Intertwined Fate and Acquaint Fate.
- **Multi-Account Cooldown Tracking**: Continues executing remaining tasks even if an individual task fails.

## Usage

1. Add this script to the Scheduler.
2. Right-click the script and open JS Custom Configuration.
3. Enable desired tasks and configure corresponding settings.
4. After carefully reading this guide and precautions, check "I have carefully read the README".
5. Start the script from the game's main interface.

*It is recommended to enable only one task on your first run to verify that paths, teams, and combat strategies work as expected before enabling others.*

## Configuration Guide

| Setting | When Required | Description |
| --- | --- | --- |
| Account Name | Multi-account usage | Distinguishes cooldown records per account; single-account users may leave blank |
| Parametric Transformer Task | As needed | Select materials and charging method |
| Transformer Team | When using Catalyst charging | Enter team name containing the charging character |
| Escoffier Task | As needed | Operates independently from Transformer with its own cooldown tracking |
| Escoffier Team | When enabling Escoffier task | Must be a team containing Escoffier |
| Max BP Level Skip Options | As needed | Selectively skip Cooking, Forging, Boss, and Domain tasks when BP is maxed (Lv. 50) |
| Cooking Task | As needed | Specify dish name and quantity to cook |
| Forging Task | As needed | Choose between Crystal Chunk, Amethyst Lump, or Condessence Crystal |
| Combat Team | When enabling Boss or Domain tasks | Must configure corresponding auto-combat strategy |
| Omni-Ubiquity Net / Coupons | As needed | Ensure target regions and NPCs are unlocked before first use |
| Intertwined & Acquaint Fate Exchange | As needed | Executes once per month independently |

## Important Precautions

1. The dish chosen for the Cooking task must have "Auto-Cook" unlocked, with sufficient ingredients in your inventory.
2. The Forging task crafts 20 times; please prepare enough ore in advance.
3. Electro Crystal charging is fast, but may be affected by nearby enemies or mined crystal states. Catalyst character charging is slower but more consistent (currently supports Barbara).
4. Escoffier and the Parametric Transformer are two independent tasks with separate team settings, charging methods, and cooldowns. The Parametric Transformer records its next available execution time as **6 days and 22 hours** upon completion.
5. Mint is used as the default Transformer fuel. To use materials outside the configuration list, replace the corresponding template image in `assets/`; replacement items must belong to the same inventory category with identical filenames.
6. If any "Skip when BP is maxed" option is enabled, the script checks your Battle Pass level before starting weekly tasks. If detection fails, tasks continue as normal to avoid accidental skips.
7. Boss tasks target the Pyro Regisvine and Cryo Regisvine arenas; Domain tasks target Taishan Mansion (Mitachurl & Fatui Pyro Agent). Please configure compatible combat strategies in advance.
8. Omni-Ubiquity Net and Investment Coupon tasks require prerequisite maps or quests to be unlocked. Disable coupon tasks once the related achievements are completed.
9. Cooldown records are saved locally in the `record/` directory. Preserve this directory when updating the script.
10. Some weekly tasks can only be tested in-game once per week. If you encounter issues, please attach execution logs and reproduction steps.

## Disclaimer

- This project is for educational and communication purposes only. Do not use for commercial purposes or in violation of game terms of service.
- The script is provided "as is" without warranty of compatibility, security, or feature completeness. Users assume all account, data, and hardware risks.
- Configurations and run records are stored locally only; do not run on shared or untrusted machines.
- Malicious tampering or illegal usage is strictly prohibited. The developer reserves the right to terminate maintenance at the request of the game operator.

Using this script signifies that you have read and agreed to the above terms.

---

## Changelog

### 1.4.5 (2026.08.13)
1. Fixed a bug where successful pathfinding in the Escoffier Electro Crystal route triggered an extra navigation cycle, causing the task to fail.

### 1.4.4 (2026.07.28)
1. Optimized settings UI.
2. Added supplemental Escoffier Electro Crystal path.
3. When max BP skip is checked, task cooldown resets at 04:00 every Monday.

### 1.4.3 (2026.07.25)
1. Separated Parametric Transformer and Escoffier into independent tasks.
2. Removed Crystalfly Trap task.
3. Added BP max level check to selectively skip Cooking, Forging, Boss, and Domain tasks.

### 1.4.2 (2026.06.15)
1. Adjusted Transformer & Escoffier cooldown to 6 days and 22 hours.

### 1.4.1 (2026.06.01)
1. Added post-teleport delay for Catalyst charging mode in Transformer & Escoffier task to prevent failures caused by slow inventory loading.

### 1.4 (2026.01.26)
1. Added monthly Intertwined Fate and Acquaint Fate Stardust exchange.
2. Fixed various bugs.

### 1.3.8 (2026.01.19)
1. Redesigned dividers in the settings interface.

### 1.3.7 (2026.01.14)
1. Fixed minor bugs and clarified descriptions.

### 1.3.6 (2025.12.09)
1. Standardized recognition regions, avoiding direct reliance on `genshin.width`.

### 1.3.5 (2025.11.05)
1. Fixed a bug where failed Domain startup caused the script to fight in place until timeout.
2. Fixed an issue where debug info failed to display.
3. Refactored main routine for improved clarity and structure.

### 1.3.4 (2025.11.04)
1. Refactored OCR text recognition for proper resource disposal.
2. Code optimizations and added debug logging.
3. Fixed occasional failure when purchasing Omni-Ubiquity Nets.

### 1.3.3 (2025.10.27)
1. Fixed an issue where certain devices failed to return to the main interface promptly, blocking subsequent tasks.
2. Fixed an issue where characters occasionally took damage from Electro Crystals.
3. Cleaned up multiple logic edge cases.

### 1.3.2 (2025.10.24)
1. Changed account identification from OCR UID detection to manual text entry (prevents edge-case bugs, though resets legacy records).

### 1.3.1 (2025.10.09)
1. Improved Catalyst charging logic.
2. Fixed mismatched descriptions.
3. General logic improvements.

### 1.3 (2025.10.08)
1. Fixed record files being lost on update.
2. Fixed occasional issue preventing Transformer deployment.
3. Added Catalyst normal attack charging mode for Transformer and Escoffier as an alternative to mined Electro Crystals.

### 1.2.1 (2025.10.07)
1. Fixed occasional bugs in Investment Coupon and Transformer tasks.
2. Task failures no longer abort subsequent scheduled tasks.
3. General feature optimizations.

### 1.2 (2025.10.06)
1. Added Auto BP Weekly - Domain Challenge.
2. Added Auto BP Weekly - Weekly Cooking.
3. Added Auto BP Weekly - Weekly Forging.
4. Added Auto BP Weekly - Boss Challenge.
5. Added Auto Omni-Ubiquity Net purchase.
6. Added Auto Investment Coupon submission.

### 1.1 (2025.09.24)
1. Fixed issue where Escoffier could be electrocuted during cooking.
2. Added popup dismissal for expired inventory items.

### 1.0 (2025.09.20)
1. Initial release of AutoMonday V1.0!
2. Integrated Escoffier and Parametric Transformer into a single workflow using Electro Crystals for fast charging.