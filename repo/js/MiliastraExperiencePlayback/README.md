# 🌌 Miliastra Wonderland · EXP Farming (Playback Clear Edition)

### 🌟 Feature Overview

- 🎥 Randomly selects and executes a stage completion script based on multiple user-recorded replays.
- 📅 Weekly: Automatically and repeatedly clears designated Wonderland stages, tracks weekly EXP progression, and skips automatically upon hitting the weekly cap.
- 🧺 Supports deleting stage save files to re-challenge (disabled by default), increasing farming efficiency (subject to potential future game patches).
- 📆 Daily: Clears specified daily Wonderland stage quests (disabled by default) and claims stage rewards upon completion.
- 🏞️ Automatically returns to the continent of Teyvat after completion to prevent blocking subsequent automation routines.

## 📋 Must Read Before Use

- Do **NOT** run this script in co-op-restricted areas or special instances (e.g., Court of the Silver Moon, Flamefeather Valley, White Birch Snowgrave), otherwise you cannot enter Miliastra Wonderland.
- Each completion awards **20** base EXP. Depending on achievements completed, each achievement awards an additional **50** EXP. Deleting stage saves allows achievements to be earned repeatedly.
- If enabling `deleteStageSave`, **it is strongly recommended to clear out unused stage saves beforehand** to keep the list short, minimizing scroll times and recognition errors. Also adjust `expPerAttempt` accordingly (e.g., set to 270 if your replay unlocks 5 achievements) to reduce total runtime.
- If built-in replays become outdated or broken, use BetterGI's built-in **[Record & Playback]** tool to record your own clear routine after entering the stage.
- After recording, copy the recorded script into the `assets/playbacks` directory under this script folder (renaming files for clarity is recommended).
- Right-click to configure script settings (including stage ID/keyword, replay file pool, EXP per attempt, etc.).
- Choose popular, simple single-player stages with low risk of being taken down (refer to the average clear time in the stage description; e.g., stone simulators, wish simulators, scenic sightseeing maps).
- **It is recommended to slightly extend recorded clear durations** to reduce the risk of stages being delisted.
- Daily reward collection will not claim chests with elective reward options (e.g., in Chronicles of the Realms, it claims EXP rewards but skips choice-based milestone rewards).

### 📖 Usage Instructions

1. Add this script to your Configuration Group.
2. Right-click the script to edit custom settings.
3. Configure the planned stage room info, replay files, and options.
4. Click run.

### 🛠️ Script Configuration

| Option | Description | Notes | Default |
| --- | --- | --- | --- |
| `weeklyEnabled` | Execute weekly stage clear tasks | | `true` |
| `room` | Wonderland stage keyword or stage GUID | | `20031486040` |
| `playbacks` | Replay file pool for stage clears | Comma-separated, randomly chosen; copy custom replays to `assets/playbacks` | `美景音乐播放器Settlement.json` |
| `expPerAttempt` | EXP gained per attempt | If deleting saves is enabled, add 50 EXP per achievement completed | `20` |
| `deleteStageSave` | Delete stage save file | Allows re-achieving milestones for extra EXP | `false` |
| `deleteStageSaveKeyword` | Stage save deletion keyword | Matches the [Stage] column in the stage save list | `音乐播放` |
| `expWeeklyLimit` | Weekly EXP cap | | `4000` |
| `force` | Force execution even if weekly cap is reached | | `false` |
| `thisAttempts` | Specific number of clear attempts | 0 for automatic calculation | `0` |
| `dailyEnabled` | Execute daily stage clear tasks | | `false` |
| `dailyRooms` | Daily stage keywords or stage GUIDs | Comma-separated | `24429042323,28644538672,45694132064` |
| `dailyPlaybacks` | Random pool of daily replay files | Semicolon separates different stages; commas separate variations for the same stage | `通关回放1.json,通关回放2.json;30秒按1通关.json;轰鸣木桩Settlement.json` |
| `dailyRewards` | Claim daily rewards | Attempts to claim Chronicle EXP and daily activity rewards | `["Chronicles of the Realms", "绮衣珍赏", "奇趣盛邀", "星境彩馈"]` |
| `dailyLimit` | Daily clear limit per individual stage | | `1` |
| `dailyForce` | Force run ignoring daily stage limits | | `false` |
| `closeStageDialog` | Close guide dialog before executing replay | Disable if your replay handles manual dialog closing | `true` |
| `goToTeyvat` | Return to Teyvat upon task completion | | `true` |

### ❗ Precautions

- Ensure the game aspect ratio is `16:9`. Restart BetterGI if resolution is changed in-game.
- Maintain a stable network connection while running the script.
- Configure emergency stop hotkeys in advance to pause or terminate the script when necessary.

### 🗂️ Version History

- [Version History](https://github.com/breadgrocery/miliastra-experience-playback/tree/main/versions)
- [Changelog](https://github.com/breadgrocery/miliastra-experience-playback/blob/main/CHANGELOG.md)

## 🐛 Feedback & Issues

[breadgrocery](https://github.com/breadgrocery/miliastra-experience-playback)
