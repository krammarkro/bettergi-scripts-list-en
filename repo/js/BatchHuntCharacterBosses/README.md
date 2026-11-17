# Batch Hunt Character Ascension Material Bosses

## I. Feature Overview
1. Configure multiple character material bosses at once.
2. Saves progress when resin is depleted, resuming from the breakpoint on subsequent runs.
3. Supports three farming modes: One-Time, One-Time with Daily Limit, and Daily Repeating.

## II. Script Usage Guide
1. Add and run this JS script in the Scheduler.
2. Upon startup, the script opens a built-in configuration editor where you can add, delete, reorder, and modify Boss configurations.
3. Click "Save and Close"; the script saves configurations and begins hunting in list order.
4. Right-click the script -> Edit JS Script Custom Configuration, and uncheck "Open configuration editor on startup" for automated/AFK use.

### Option Explanations

1. **Combat Timeout**:
   - **Configured independently per boss**, in seconds (default: 240 seconds). If exceeded, combat is forcibly terminated.
   - **Make sure** the boss dies within this duration; there is no special handling for timeouts.

2. **Farming Mode**:
   > Farming requires Original Resin; runs will automatically stop if resin is depleted.
   - **One-Time**: Once the configured run count is reached, this boss configuration is completed and retired. Bosses are cleared sequentially in the order added. Requires configuring `Hunt Count`. The `Daily Limit Count` option is ignored.
   - **One-Time - Daily Limit**: Similar to One-Time, but caps daily runs using `Daily Limit Count`. Once the daily limit is hit, the script proceeds to the next boss in list order, repeating daily until the total count is fulfilled. Requires configuring both `Hunt Count` and `Daily Limit Count`.
   - **Daily Reset**: Farms up to `Daily Limit Count` every day; resets daily regardless of whether runs were completed. The `Hunt Count` option is ignored.

## III. Unsupported Bosses
The following bosses are currently unsupported:
* Anemo Hypostasis
* Golden Wolflord
* Cryo Hypostasis
* Bathysmal Vishap Herd

## IV. Using the Boss Configuration Editor
When launched with the editor enabled, the built-in configuration editor opens. You can add, delete, sort, and modify boss configs directly. After clicking "Save and Close", configs are written to `assets\config\config.json` and script execution continues.

## V. Bug Feedback & Suggestions
For any issues or feature requests, feedback is welcome:
* QQ Group: [1025022262](https://qm.qq.com/q/7i92V2JYF)
* GitHub Issues: [**Create an Issue**](https://github.com/1004452714/AutoBoss/issues)

## VI. Changelog
### 2026.11.10 V0.8.3
* Added Snezhnaya boss route support: **Wave Anchorer**
* Radiant Moonfly switched to auto-pathfinding (using `Radiant MoonflyGo to.json`), removing keymouse navigation and forced teleport tracking files.

### 2026.09.26 V0.8.2
* Added Snezhnaya boss route support: **Guardian Blade of Drifting Snow**

### 2026.08.12 V0.7
* Added route support for two bosses: **Immortal Construct**, **Chimeric Winged Lion**
* Immortal Construct now uses full pathfinding after combat.

### 2026.05.02 V0.6.2
* Added built-in Boss Configuration Editor.

### 2026.04.11 V0.6.1
* Fixed miscellaneous bugs.

### 2026.04.10 V0.6
* Added boss route support.
* Fixed issue where adding boss mode had no effect.

### 2025.11.16 V0.5
* This update may reset and does not support older versions of `config.json`; backing up and reconfiguring is strongly recommended.
* Added two farming modes:
  * **One-Time - Daily Limit**: Similar to One-Time, but limits daily runs to `Daily Limit Count`; proceeds to the next boss once daily limit is met, repeating daily until total count is reached.
  * **Daily Reset**: Farms up to `Daily Limit Count` daily; count resets every day.
* Added support for two boss routes: **Knuckle Duckle**, **Frostnight Herra**.

### 2025.08.23 V0.3
* Fixed bug where premature teleport occurred before rewards were successfully claimed.
* Fixed bug where runs were counted as completed even if rewards failed to claim.
* Updated boss list display formatting.

### 2025.08.21
* Fixed unreleased screenshot resource leak.
* Updated map tracking files.

### 2025.08.21 V0.1
* Initial release.
