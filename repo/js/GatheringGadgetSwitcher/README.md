# Gathering Gadget Switcher

Automatically finds and equips the following gadgets from the Inventory Gadgets tab:

- `Seed Dispensary`: Suitable to place before plant seed-gathering routes.
- `The Boon of the Elder Tree`: Suitable to place before automated woodcutting scripts.
- `NRE (Menu 30)`: Suitable to place before gathering or combat scripts that require recovery.

The script only handles swapping the equipped gadget; route tracking and woodcutting tasks continue to be handled by their respective scripts. If the requested gadget is already equipped, the script detects the "Unequip" state and exits immediately.

## Usage

1. Add this script to a scheduler configuration group.
2. Right-click to open "Modify JS Custom Configuration".
3. Select `Seed Dispensary`, `The Boon of the Elder Tree`, or `NRE (Menu 30)`.
4. Place the script right before the corresponding gathering/farming task.

Example orchestration:

```text
Gathering Gadget Switcher (Seed Dispensary)
Plant Gathering Route
Gathering Gadget Switcher (The Boon of the Elder Tree)
Auto Woodcutting - Map Pathing Version
Gathering Gadget Switcher (NRE (Menu 30))
Combat / Gathering Script Requiring Recovery
```

## Requirements

- The account must already possess the selected gadget.
- Start from the game main UI.
- Verified on BetterGI `0.64.0` at `1920×1080` resolution.

## Verification Notes

- Seed Dispensary correctly recognizes "Equipped" and "Switch" states; after equipping, Sweet Flower routes consistently collect "Sweet Flower Seed".
- The Boon of the Elder Tree successfully swaps in from Seed Dispensary; subsequent woodcutting scripts detect the Boon and complete a Birch Wood route, logging 75 Birch Wood collected.
- NRE (Menu 30) successfully swaps in from Seed Dispensary; after equipping, the script detects the "Unequip" button state.

## Asset Documentation

The three PNG files in `assets/RecognitionObject` are actual in-game recognition templates for the gadgets. Templates exclude quickbar slot numbers, status corner badges, star ratings, and quantity text.
