# Only Big Bottles (Turbo Edition)

A high-speed variant based on original author **mno**'s BetterGI script "Only Big Bottles", designed to automatically select and dismantle artifacts into Artifact EXP bottles, maximizing the conversion into Sanctifying Essence (big bottles).

- **Author**: Purfeather
- **Version**: `1.0.1`
- **Compatibility**: Genshin Impact `7.0`, BetterGI `0.64`
- **Original Script**: [bettergi-scripts-list / 只要大瓶](https://github.com/babalae/bettergi-scripts-list/tree/main/repo/js/%E5%8F%AA%E8%A6%81%E5%A4%A7%E7%93%B6)

## Changelog

- `1.0.1`: Implemented tighter default click intervals for a noticeable speedup.

## Features

- Rapidly selects artifacts following the UI grid order, automatically salvaging upon reaching the target bottle threshold.
- Configurable maximum rarity allowed for salvaging.
- 5-star artifacts are strictly protected and never queued for salvaging.
- Supports two operating modes: "Only Big Bottles" (Sanctifying Essence) and "Only Small Bottles" (Sanctifying Unction).
- Detects current inventory counts of both bottle types, automatically toggling modes based on a configurable threshold.
- Configurable recognition threshold and click delay for balancing speed and stability.
- Skips ambiguous artifacts if recognition conflicts occur, preventing accidental selections.

## Usage

1. Add and run "Only Big Bottles (Turbo Edition)" in BetterGI.
2. Open Custom Configuration and set the maximum star rarity allowed for salvaging.
3. Select your target bottle type:
   - **Only Big Bottles**: Aims to maximize Sanctifying Essence production.
   - **Only Small Bottles**: Aims to maximize Sanctifying Unction production.
4. (Optional) For automated mode switching, fill in "Auto-switch threshold for small bottles":
   - When small bottle count >= threshold, switches to "Only Big Bottles".
   - When small bottle count < threshold, switches to "Only Small Bottles".
   - Leave blank to stick with the manually selected target mode.
5. On your first run, observe at least one full cycle to verify that recognition and clicking function properly.

## Parameter Tuning

Default recognition thresholds and click delays are pre-calibrated and generally do not require adjustment.

If artifacts are missed, slightly decrease the rarity recognition threshold; if false positives occur, slightly increase it. If clicks occasionally fail to register, increase the "Post-click stability delay".

Test with small batches first after adjusting settings.

## Resource Directory

`Assets/RecognitionObject` contains UI button assets, artifact star badges, bottle results, and inventory count templates; the `Inventory物品数字` subfolder contains numerical templates for digits `0` through `9`.