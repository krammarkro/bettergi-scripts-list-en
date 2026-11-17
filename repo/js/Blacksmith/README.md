# Auto Forging Mystic Enhancement Ore Script

## ⚠️ Disclaimer

> **Important: Please read the following carefully before use.**

### Usage Risks

This script is an open-source educational project intended strictly for personal study. **Commercial use or any violation of game terms of service is prohibited.** Misuse may result in game account sanctions. The developer assumes no direct or indirect liability.

### Limitation of Liability

This script is provided "AS IS" without warranties of compatibility, security, or feature completeness. The developer is not responsible for any account, data, device, or other losses resulting from its use.

### Prohibitions

Reverse engineering, malicious tampering, or using this script for illicit cheating tools is strictly forbidden. The developer reserves the right to cease maintenance at any time upon request from the game operator.

**Using this script signifies that you have read, understood, and agreed to all terms stated above.**

## 📞 Contact & Feedback

For questions or suggestions:  
📧 QQ: 1765137214 (The author has retired from the game; future developers are welcome to optimize and update)

---

## ✨ Feature Overview

- Compatible with Genshin Impact 7.0+
- Tested on BGI 0.64.0+
- Automatically travels to designated blacksmiths, using computer vision to select or prioritize ores for forging Mystic Enhancement Ore:
  - 🗺️ **Auto Navigation** - Smart pathfinding to the selected Blacksmith
  - 🔍 **Ore Recognition** - Multi-ore detection and automatic selection
  - 🎯 **Dual Forging Modes** - Provides both Auto and Manual priority modes
  - 📊 **Status Notifications** - Real-time desktop alerts and detailed execution logs
  - 🛡️ **Exception Handling** - Gracefully handles missing materials, recognition errors, and dialog blocks

## 📁 File Structure

```text
Auto Blacksmith Forging/
├── main.js              # Core logic
├── manifest.json        # Script metadata and base configuration
└── settings.json        # User custom configuration file
```

## 🚀 Quick Start

### 1. Install Script
Add this script to the BetterGI task scheduler.

### 2. Configure Parameters
Right-click the script, select "Edit JS Configuration", or modify `settings.json` directly:

```json
{
    "smithyName": "FontaineBlacksmith",
    "CondessenceCrystal": "Condessence Crystal",
    "CrystalChunk": "Crystal Chunk",
    "AmethystLump": "Amethyst Lump",
    "RainbowdropCrystal": "Rainbowdrop Crystal",
    "notice": true,
    "forgedOrNot": "Yes",
    "model": "Mode 1"
}
```

### 3. Ore Configuration Guide

**Default Supported Ores**:
- Crystal Chunk
- Amethyst Lump
- Condessence Crystal
- Rainbowdrop Crystal

**Ore Priority Rules**:
- The priority for each ore can be configured in `settings.json` from `0` to `4`.
- **Priority 0**: The ore is disabled and automatically excluded by the script.
- **Priority 1-4**: Lower numbers represent higher priority (1 is highest).
- **Tied Priorities**: If priorities match, ores are evaluated in default sequence: `Condessence Crystal > Crystal Chunk > Amethyst Lump > Rainbowdrop Crystal`.

## ⚙️ Features in Detail

### 🔧 Forging Modes

| Mode | Description |
| --- | --- |
| **Mode 1 (Auto)** | Automatically scans inventory to forge with the highest-quantity ore. Automatically falls back to manual priority mode if recognition fails. |
| **Mode 2 (Manual)** | Sequentially evaluates and uses primary and alternate ores strictly according to user-configured priority. |

### 🎯 Special Features

- **Claim Only**: If set to "No", the script only checks and claims completed forge items without starting new forgings.
- **Smart Fallback**: Automatically switches to manual priority mode if automated recognition fails.
- **Notifications & Logs**: Supports desktop notifications and detailed logging to track script status.
- **Error Handling**: Provides detailed prompts and auto-recovery for material shortages and repeated recognition failures.
- **Priority Filtering**: Automatically skips ores configured with priority `0`.

## 📋 Precautions & Notes

1. **Environment Requirements**: Ensure game resolution and BetterGI version meet script specifications.
2. **Window Status**: Keep the game window in the foreground and unobstructed while running.
3. **Keybindings**: Keep shortcut keys at default values (Map: `M`, Inventory: `B`). Mode 1 OCR may misread numbers if fonts or resolutions differ.
4. **Ore Priority**: Ensure at least one ore has a priority greater than `0`; otherwise, the script will terminate with an error.

## 📋 Custom Extensions: Adding New Ores and Blacksmiths

The script supports user-defined ores and blacksmith routes:

---

### 🔧 Adding a New Ore

#### 1. Add Forging Screen Icon
- Take a screenshot of the ore icon in the top-right corner of the Forging UI (recommended size: `21×21` px).
- Save as PNG under `assets/Picture/`.
- Use English names without punctuation or spaces (e.g., `NewOre.png`).

#### 2. Add Inventory Screen Icon
- Take a screenshot of the ore icon in the Inventory UI (recommended size: `75×75` px).
- Save as PNG under `assets/RecognitionObject/ItemImage/`.
- Use the same English naming convention (e.g., `NewOre.png`).

#### 3. Modify `main.js`
At the top of `main.js`, add the new ore information to:
- User Configuration
- `OreChineseMap`
- `orePriorityConfig`
- `nicknameOrder`
- `ingredientImageMap`
- Inventory item icons map

#### 4. Add Ore to `settings.json`
Add the new ore key and priority mapping at the end of `settings.json` following the existing format.

---

### 🔧 Adding a Blacksmith Route

#### 1. Record Route
1. Use BetterGI's path recording tool to record a route to the blacksmith.
2. Save as JSON under `assets/assets/Pathing/` (e.g., `SnezhnayaBlacksmith.json`).

#### 2. Update `settings.json`
Add the new blacksmith option under `smithyName` in `settings.json`.

---

## ❓ FAQ

**Q: The script does nothing after starting?**  
**A**: Troubleshoot with the following steps:
1. Verify game resolution meets requirements (`1920×1080` recommended).
2. Ensure BetterGI is version `0.48.2` or higher.
3. Verify script configurations and ensure at least one ore priority is > 0.
4. Ensure the game window is active in the foreground.
5. Check that in-game hotkeys are default (`M` for Map, `B` for Bag).

**Q: OCR misreads the ore quantities?**  
**A**: This is an inherent limitation of OCR. Switch to **Mode 2 (Manual Priority Mode)** for deterministic behavior.

---

## 📜 Changelog

### 2.4.3 (2026-08-29)
- **Optimized**: Natlan blacksmith route.
- **Added**: Support for Snezhnaya blacksmith.

### 2.4.2 (2026-04-28)
- **Added**: Custom extension documentation in README; added example mineral and route templates.

### 2.4.1 (2026-01-11)
- **Fixed**: Stuck issue caused by failed clicks on the forge dialog icon.

### 2.4.0 (2025-11-29)
- **Optimized**: Fixed overshooting on Natlan blacksmith route.
- **Added**: Supported Moon realm blacksmith and Rainbowdrop Crystal; overhauled ore priority sorting; priority 0 excludes ore.

### 2.3.1 (2025-08-30)
- **Fixed**: Notification error in Mode 1; inventory screen exit bug.

### 2.3.0 (2025-08-28)
- **Fixed**: Fontaine blacksmith overshooting.
- **Optimized**: Checked big map for completed forge reward icon before pathing for claim-only mode.
- **Added**: Mode selection (Mode 1 Auto / Mode 2 Manual); added Natlan Blacksmith support.

### 2.2.1 (2025-08-03)
- Accelerated forging speed and improved notification delivery.

### 2.1 (2025-06)
- Updated versioning scheme; adapted for version 5.7 daily forge limit increase from 3 to 4 batches.

### 2.0 (2025-05-22)
- Added automatic fallback to alternative ores when materials are insufficient or unread.

### 1.1 - 1.4 (2025-05)
- Added desktop notifications, image recognition selection, and bug fixes for Condessence Crystals.

---

**Last Updated**: April 28, 2026  
**Maintainer**: @呱呱z (GuaGuaz)
