# [Not a TCG God] Raiden Shogun - Collei - Keqing

A fully automated Genius Invokation TCG PvE player for the Raiden Shogun, Collei, and Keqing deck, supporting both beginner and complete decklists. Raiden Shogun leads, building energy with Normal Attacks and Elemental Skills, replenishing team energy with "Secret Art: Musou Shinsetsu", and using skill summons to increase team Elemental Burst damage; Collei applies Dendro with her skill and "Sprout" passive, enabling Quicken reactions alongside Keqing's "Stellar Restoration", Electro-infused Normal Attacks, and "Starward Sword" piercing standby damage. Supports "Floral Sidestep" Dendro follow-ups, "Thundering Penance" enhanced infusion, and "Lightning Stiletto" swap-in skill casts with infusion.

Automatically handles opening mulligan, character selection, rerolling dice, card playing, character switching, and ending turns, intelligently allocating skill and switching resources according to hand cards, energy, and dice elements. Generates Electro dice with "Elemental Resonance: Woven Thunder", converts Omni dice with "The Bestest Companion!", and rerolls off-color dice with "Toss-Up". Supplements energy with "Elemental Resonance: High Voltage", "Starsigns", and "Calx's Arts", while coordinating character switches using "When the Crane Returned", "Shift of the Needle", and "Leave It to Me!". Performs Elemental Tuning when needed using expendable cards to secure required elemental dice. Adapts to "Thunder and Plant Boon" by selecting between "Cracking Thunder" and "Sharp Core" based on surviving characters and energy levels, taking advantage of Quicken field burst or skill cost reductions.

Selects equipment and food based on subsequent actions: equips "The Exile's Circlet" to battery standby characters with Bursts, equips "Gambler's Earrings" upon KO opportunities to recover Omni dice, and equips basic weapons on appropriate characters. Chooses "Lotus Flower Crisp" for damage reduction, "Mondstadt Hash Brown" and "Sweet Madame" for healing, "Northern Smoked Chicken" and "Minty Meat Rolls" to reduce Normal Attack costs, and "Verdict of Absolution" to heal injured units. Upon character knockout, smoothly passes the baton based on remaining HP, energy, frozen status, and available dice, using "I Haven't Lost Yet!" when requirements are met to gain Omni dice and energy.

**Author**: Giant Whale Is Also a Salted Fish (巨鲸也是咸鱼). **Version**: 1.4.2.

Execution logs are stored in `logs/`, cyclically preserving the last 10 launches (`run-slot-01.log` through `run-slot-10.log`). Manually archive logs if you need long-term records; new runs overwrite the oldest log file, with each log's `start` timestamp indicating the actual match start time.

Supports all three resolutions listed below with automatic UI layout adaptation. Please configure your resolution before starting and keep it consistent throughout the game; restart the BetterGI capture engine if you switch resolutions before launching the player.

## Usage Instructions

1. Use BetterGI **version 0.66.0 or newer**, set game display language to **Simplified Chinese**, and set client window resolution to **1920×1080, 2560×1440, or 2560×1600**.
2. Assemble your deck using either decklist below. Characters from left to right must be **Raiden Shogun → Collei → Keqing**; the script automatically selects Raiden Shogun as the active character.
3. Subscribe to and import the script into the BetterGI scheduler, then launch it for fully automated play.
4. Manually start a duel, pause at any of the following initial screens: **Initial Mulligan, First Character Selection, or First Dice Roll**, and start the script. Works regardless of whether character selection or rolling occurs first.

If you have just transitioned into the Action Phase, you can still start: configure "Action Phase Start" to **"Confirm New Game Unacted"**, and ensure neither side has played cards, cast skills, switched characters, or performed elemental tuning yet. Mid-game takeovers after actions have occurred are not supported.

Initial hand handling defaults to "Keep All", playing according to current match resources; you can also choose "Prioritize Equipment & Setup Cards" to mulligan specifically for key cards while keeping at most one copy of duplicate equipment. Default match timeout is 15 minutes (can be adjusted to 20 minutes for longer matches). Use BetterGI's stop button or stop hotkey to abort. The script plays one match per run; manually enter the next match before launching again.

## More Automated TCG Players & Subscriptions

If you enjoy this deck strategy, check out the author's other automated players: **Iansan-Gaming-Sayu (伊嘉早), Moon-Bloom (月绽放), and Mona-Sayu-Diluc (莫早卢)**. All four players are maintained in the [「Not a TCG God」Auto TCG Repository](https://github.com/sxy8161-debug/bettergi-tcg-scripts-release) and can be subscribed to independently. Decklists, instructions, and sharing codes are available on the repository homepage. Feedback and GitHub Stars are greatly appreciated!

To subscribe to the author's repository in BetterGI:

1. Open **Script Repository**, and on the **Git One-Click Update** page, set Update Channel to **Custom**.
2. Enter the repository URL below into the repository address field and click **Update Repository**:

   ```text
   https://github.com/sxy8161-debug/bettergi-tcg-scripts-release
   ```

3. Once updated, click **Open Repository**, find the desired automated TCG player, and click subscribe; subsequently use **One-Click Update Subscriptions** to fetch updates.

*Note: The URL above is the release repository, not the source code repo, and does not require a `repo.json` or branch path. If you prefer not to switch channels, download the ZIP from [Latest Releases](https://github.com/sxy8161-debug/bettergi-tcg-scripts-release/releases/latest) and extract it to BetterGI's `User/JsScript/<ScriptFolder>/`, ensuring `manifest.json` is at the root of that folder.*

[Source Code & Issue Tracker](https://github.com/sxy8161-debug/bettergi-tcg-scripts)

## Beginner Decklist

Uses 15 Action Card varieties, 2 copies of each, for a total of 30 cards. Character cards remain Raiden Shogun, Collei, Keqing.

| Action Card | Quantity |
| --- | ---: |
| Elemental Resonance: Woven Thunder | 2 |
| Elemental Resonance: High Voltage | 2 |
| Shift of the Needle | 2 |
| Leave It to Me! | 2 |
| The Bestest Companion! | 2 |
| Strategize | 2 |
| Starsigns | 2 |
| Calx's Arts | 2 |
| Lotus Flower Crisp | 2 |
| Mondstadt Hash Brown | 2 |
| Sweet Madame | 2 |
| Northern Smoked Chicken | 2 |
| Minty Meat Rolls | 2 |
| Gambler's Earrings | 2 |
| Floral Sidestep | 2 |
| **Total** | **30** |

## Complete Decklist

Uses 19 Action Card varieties for a total of 30 cards. Integrates Thunder and Plant Boon, Verdict of Absolution, The Exile's Circlet, etc.; upgrade to this list as your collection grows.

Deck Sharing Code (Complete):

```text
AhAA8i8PASDA81gPBjCw9JcPCUBw9ZkPCVCR9qMPJWDA+OUPDpFQC+YQDrFgDPEQD+AA
```

Import this code in the in-game Deck Editor to automatically build the deck below.

| Action Card | Quantity |
| --- | ---: |
| Elemental Transformation: Thunder and Plant Boon | 1 |
| Verdict of Absolution | 1 |
| Elemental Resonance: Woven Thunder | 2 |
| Elemental Resonance: High Voltage | 2 |
| Shift of the Needle | 2 |
| Leave It to Me! | 2 |
| The Bestest Companion! | 2 |
| Toss-Up | 2 |
| Strategize | 2 |
| Starsigns | 1 |
| Calx's Arts | 1 |
| I Haven't Lost Yet! | 2 |
| The Exile's Circlet | 2 |
| Gambler's Earrings | 2 |
| Lotus Flower Crisp | 2 |
| Northern Smoked Chicken | 1 |
| Mondstadt Hash Brown | 1 |
| Floral Sidestep | 1 |
| Thundering Penance | 1 |
| **Total** | **30** |

## Missing Cards & Card Substitutions

Both deck variants use the **exact same script**; no mode switching is required, and completing the full deck first is not mandatory. If you are missing cards, fill the remaining slots with available cards to reach 30; unsupported cards will not be played actively and will be utilized for Elemental Tuning.

Lightning Stiletto is generated by Keqing's Elemental Skill; Cracking Thunder and Sharp Core are generated by Thunder and Plant Boon—**do not attempt to add these tokens to your main deck**, as the script manages them automatically during play.

If a run halts unexpectedly, inspect BetterGI logs and `logs/` in the script directory. Attribution information can be found in [ATTRIBUTION.md](ATTRIBUTION.md).
