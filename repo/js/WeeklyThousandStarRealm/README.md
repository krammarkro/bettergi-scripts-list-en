# 🌌 Thousand Stars Realm · Auto Achievement EXP Farming

**⚠️ Note**: You do not need to search for maps manually. Achievement Mode requires specifically configured stages. If the default map is taken down, switch to Non-Achievement Mode to farm fixed 20 EXP stages.

> Achievement Mode stage requirements: Sufficient duration + automated completion settlement + in-stage achievements (mandatory).

---

## ❗ Important Notice & Disclaimer

This script relies on **deleting realm stage save data** to repeatedly obtain achievement EXP.

**What this means:**
- When deleting save data, progress in stages you play normally could potentially be cleared.

If you fully understand and accept this risk, check `I have read the disclaimer in the guide` in the script's *Custom JS Configuration* to proceed. Please ensure you accept potential losses before using this tool.

---

## 🔥 Fast Farming Method

Custom-created Thousand Stars Realm maps also grant EXP without needing full public approval: simply clicking Publish, previewing stage details, and favoriting the map from the popup is enough.  
This allows you to create an instant-clear map, favorite it during preview, and farm your unreleased map from your Favorites tab.  
The updated script has optimized click intervals, completing the weekly EXP cap in just 8 minutes and 45 seconds.  
A template map file is included under `BetterGI/User/JsScript/WeeklyThousandStarRealm/map` and can be imported in-game.

## 🌟 Features

* Automatically and repeatedly clears designated realm stages.
* Automatically deletes stage save data so achievement EXP can be re-earned.
* Tracks weekly EXP progress, stopping automatically upon reaching the cap.
* Automatically returns to Teyvat upon completion without interrupting scheduled tasks.
* Supports farming favorited maps with custom map name matching.

---

## 🛠️ Configuration Settings

| Setting | Description | Default |
| --- | --- | --- |
| **runJS** | Acknowledged disclaimer (must be checked to execute) | `No` |
| **room** | Stage keyword or GUID (single stage; uses default if empty) | `37135473336` |
| **achievementMode** | Achievement Mode (ensure stage features achievements) | `Yes` |
| **starMode** | Favorite Mode (ensure stage is valid and favorited) | `No` |
| **starRoomName** | Map name in favorites (substring match, avoid name collisions) | `碰碰墙` (Bumper Wall) |
| **thisAttempts** | Clear attempt limit (`0` = unlimited until weekly cap) | `0` |
| **weekMaxExp** | Weekly obtainable EXP limit | `4000` |
| **singleExp** | EXP gained per stage clear (cannot be zero) | `270` |

---

## ❗ Precautions

- The game window must maintain a **16:9** aspect ratio to prevent image recognition errors.
- Ensure `EXP gained per stage clear` matches actual stage rewards accurately; otherwise, remaining run calculations will be skewed.
- If the default map is delisted, manually enter a valid stage GUID.
- When enabling Favorite Mode, ensure `Map name in favorites` matches the exact target title.
- Do not pin the target map to the top of your favorites list, or search queries may fail!
- Both Achievement Mode and Favorite Mode can be enabled simultaneously provided the stage satisfies requirements.
- Red console errors indicating missing files can be safely ignored and will not cause operational issues.

---