# Auto Pathfinding + Manual Combat Script Instructions v1.12

**Author**: JiJiMiao (吉吉喵)

**Supported Version**: BGI 0.64+

**Script Focus**: A semi-automated casual mob-farming script focused on **eliminating manual pathfinding while keeping combat and looting fully manual**. It automatically navigates along routes to find mobs and automatically pauses upon reaching combat spots, allowing the player to manually defeat enemies, open chests, collect drops, or gather Oculi freely. Includes built-in path hash verification, automatic cooldown management, and runtime logging.

## 1. Disclaimer

1. This script is an independently developed hobby tool intended solely for single-player entertainment and study, used locally with BetterGI.
2. The script only provides automated pathfinding assistance. All actions are initiated by the user at their own risk. The author assumes no responsibility for any account issues or related liabilities arising from its use.
3. Commercial use, reselling, repackaging, or using this script to disrupt game balance or engage in unauthorized AFK activities is strictly prohibited.
4. Users are responsible for any issues resulting from improper operation, path file errors, or manual mistakes.

## 2. Core Features

- **Auto-Pause at Combat Nodes**: Automatically detects combat points along the route and pauses execution upon arrival. After manually defeating the enemies, players can freely open chests, collect drops, and gather Oculi. Press the pause key when done to resume pathfinding to the next route waypoint.
- **Path Hash Verification**: Generates a unique hash from path coordinates to automatically adapt when paths are modified. Renaming files does not break them, preventing corrupted or outdated paths from running.
- **Auto Cooldown Management**: Intelligently tracks respawn cooldowns for materials and mobs, automatically skipping routes still on cooldown to prevent redundant pathfinding.
- **Runtime Cache**: Automatically records execution timestamps for each route to provide accurate cooldown tracking.

## 3. Settings

### 1. Pause Key (`virtualKey`)
Default: `VK_END` (End key). The script automatically triggers this key at combat waypoints to pause. Refer to keycode documentation if you wish to configure a custom key.

### 2. Skip Reload (`noReload`)
Default: `false`. Re-adapts paths and verifies key/path configurations on each launch.  
When enabled: Skips path conversion and directly loads cached paths for faster startup, ideal for fixed daily route farming.

## 4. Directory Structure

- `pathing/`: Stores raw mob farming paths. Subfolder names should match mob names listed in `materialsCD/怪物.txt` (custom names can be added).
- `materialsCD/`: Material respawn cooldown rules configuration.
- `user/output_combat_convert/`: Usable paths generated automatically by the script.
- `user/content_code_record.json`: Path hash and key cache records.
- `pathing_record/`: Path runtime durations and cooldown tracking records.

## 5. Precautions & Notes

1. This script only handles pathfinding; it does **not** include auto-combat. Standing idle at combat locations may cause characters to be eliminated by enemies.
2. If a character dies during a pause, revive manually and restart the script to continue.
3. To skip a specific route, stop the script, delete the corresponding path file, and restart.
4. Completed paths enter cooldown automatically and will not repeat.
5. Supports up to 6 directory nesting levels. Routes without combat nodes (pure gathering paths) will be skipped automatically.
6. After defeating enemies, collect chests and drops as needed, then press the pause key once to proceed to the next waypoint.

## 6. Feedback

This script is currently in beta testing. Feedback and questions are welcome on the BetterGI QQ channel: `bettergiv1`.

## 7. Changelog

- **v1.0**: Implemented combat auto-pause, path hash validation, auto cooldown management, custom pause key, and runtime caching.
- **v1.12**: Fixed cooldown calculation bugs.
