# User Guide

This script mines mineral resources in descending order of route efficiency, records the respawn timers of ore nodes, automatically plans mining routes, and allows you to select ore types and mining regions.

- After starting, the script will mine continuously until **any** of the following three conditions is met:
  1. The number of mined ores reaches the specified target value.
  2. The mining duration reaches the specified target value.
  3. The current time exceeds the specified time range.

        Enter a time range or target time in China Standard Time (CST).

        For example, if you enter `10:30` and start mining at `7:00`, it will stop after mining for about 3.5 hours.

        For example, if you enter `03:50` and start mining at `22:00`, it will stop around `03:50` the next morning.

        For example, if you enter `23:00~03:50` and start mining at `23:30`, it will stop around `03:50` the next morning; if you start at `22:30`, the script will stop immediately because it is outside the preset time range.

  If none of the three conditions are configured, the script will stop after mining all available ores. Note that if you run this script for the first time, mining all ores may take more than a dozen hours.

- For surface mining, include **Linnea** or **Noelle** in your team; underwater mining does not have this restriction. For more details, see [Advanced Usage](#advanced-usage).
- Ore respawn times are recorded in the `local/persistent_data.json` file inside the script directory. Updating or reinstalling BetterGI may cause this data to be lost, so please back it up manually.
- The `Routes Requiring Combat` option provides four choices: `Mine Normally`, `Skip Only Elite Monster Combat Routes`, `Mine Only Combat Routes`, and `Skip All`. Choosing `Skip All` will not run any mining routes that require defeating monsters; choosing `Mine Only Combat Routes` will only run routes involving combat. Regardless of mode, characters may still get attacked occasionally by passing monsters on certain routes, so ensure your team maintains adequate survivability.

## Advanced Usage

- If you have multiple game accounts, you can enter a unique identifier string for each account in the last input box so that their respawn records are saved separately without interfering with each other. This string does not have to be the account's UID, as long as it is unique across your accounts.
- If you cannot complete certain routes due to unfinished map exploration quests and do not want to skip an entire region, you can add the script file names to `local/disabled_paths.txt` to skip those pathing scripts. Refer to `assets/disabled_paths.conf` for syntax.
- If you must use other characters for mining, enter the character and custom mining action in the custom mining action setting, such as `Dehya attack(2.0)`. You can also enter `默认` or `default` to use the mining action from global settings. Using this option may result in reduced yield or other issues, for which no guarantees or technical support can be provided.
- The script automatically checks team characters. If you want to use Linnea for mining, **do not** configure a custom mining action.
- The script automatically records the actual execution time of each route and stores it in `local/user_records.json`, separated by account and mining mode (Linnea/Claymore), keeping up to the 7 most recent records per route. This file is maintained automatically by the script with no manual editing needed. Updating or reinstalling BetterGI may cause these records to be lost, so you may back it up together with `persistent_data.json`.
- The "Duration Data Source" option determines where the route durations used for scheduling come from:
  - `Optimize Based on Execution Records` (default): Combines actual data from `local/user_records.json` and the "Exploration Factor" for optimized estimation.
  - `Use Route Default Data`: Uses the estimated values in `assets/statistics.json` directly.
- The "Exploration Factor" is only effective when `Optimize Based on Execution Records` is selected. Its value ranges from 0 to 1; higher values bias towards trying rarely run routes to gather data, while 0 means no optimistic correction is applied.

## Changelog

### 0.35.2
- Optimized several routes.

### 0.35.1
- Optimized several routes.

### 0.35
- Added Snezhnaya region mineral routes.
- Added the "Mine Only Combat Routes" option.
- Adjusted default route duration data.
- Optimized several routes.

### 0.34
- Added `local/user_records.json` to automatically record actual execution times for each route, stored separately by account and mining mode, keeping up to the 7 most recent runs per route.
- Added "Duration Data Source" and "Exploration Factor" options to optimize route time estimation based on real runtime data.
- Separated mining duration data by character mode (Linnea / Claymore).
- Changed route completion check to "near destination" evaluation, compatible with SIFT pathing files.
- Added option to exclude Snezhnaya.
- Optimized several routes.

### 0.33
- Optimized several routes for better compatibility with Linnea mining.

### 0.32
- Optimized Linnea mining logic.
- Optimized several routes for better compatibility with Linnea mining.

### 0.31
- Optimized Linnea mining logic.
- Optimized Linnea mining actions, special thanks to [@this-Fish](https://github.com/this-Fish).

### 0.30
- Fixed various bugs.

### 0.29
- Slightly optimized Linnea mining logic.

### 0.28
- Added experimental support for Linnea mining; stability is still being optimized.

### 0.27
- Added routes for Sea of Bygone Eras and Ancient Sacred Mountain regions.
- Redesigned custom settings interface.

### 0.25
- Fixed bug where map was unspecified in coordinate monitoring logic, special thanks to [@this-Fish](https://github.com/this-Fish).

### 0.22
- Added handling for expired item popups.

### 0.18
- Fixed bug in coordinate monitoring logic.

### 0.16
- Added real-time progress output to logs.

### 0.15
- Do not write records when subtasks end with unchanged coordinates.

### 0.14
- Allowed users to use BetterGI's default mining logic.

### 0.11
- Added option to exclude Nod-Krai region.

### 0.10
- Send notification messages when mining ends.
- Fixed bug where newly acquired ores were not recognized correctly.

### 0.9
- Added Rainbowdrop Crystal routes.

### 0.8
- Adapted for BetterGI 0.50.0, removed DPI scaling adaptation option.

### 0.7
- Allowed users to customize mining character and actions.

### 0.6
- Added option to skip combat routes with elite monsters.

### 0.5
- Updated route planning algorithm.

### 0.4
- Refactored custom configuration options.

### 0.3
- Switch team to the party configured in the settings group (if any) before starting.
- Added option to manually enable DPI scaling adaptation.

### 0.2
- Do not record tasks that finish very quickly.
- Supported custom configuration to skip specified pathing subtasks.
- Output start and end logs for pathing subtasks to facilitate log analysis.

### 0.1
- Initial release.
