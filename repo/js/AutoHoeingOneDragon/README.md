# All-in-One Mob Farming

## 1. Features and Prerequisites

This script executes map pathing routes in BetterGI, offering route selection, path grouping, item pickup, item blacklists, medicine/recovery detection, Crystalfly trap assisted teleportation, dash attack ("dump truck") skill triggers, and run logging.

- Relies on BetterGI's JavaScript engine, map pathing, image recognition, and real-time trigger interfaces.
- Primary recognition areas are designed for a `1920×1080` game window. Other resolutions have not been equally validated.
- Running routes requires map pathing files and combat strategies compatible with the current BetterGI version.
- The script is launched via a BetterGI configuration group; team setups, combat strategies, and auxiliary settings in the group may influence execution results.
- Image recognition accuracy may be affected by window resolution, DPI scaling, HDR, visual filters, frame interpolation, or other display settings.
- The script does not evaluate whether character combinations are optimal, nor will it prompt or terminate due to team compositions. `validateTeamMembers` is solely used to confirm whether specified characters are present in the active party.

## 2. Quick Start

### Normal Mode

Minimal recommended configuration:

- `operationMode`: `Run Mob Farming Routes`
- `groupIndex`: `Path Group 1`
- `accountName`: Enter your account name (single-account users may keep the default)
- `targetEliteNum`: `400`
- `targetMonsterNum`: `2000`
- `pickup_Mode`: Choose template matching pickup, native BGI pickup, or do not pick up according to your preference

Fill in `partyName` if party switching is required by the script; otherwise leave it blank. On your first run, you can select "Debug Route Allocation" to inspect route assignments before selecting "Run Mob Farming Routes".

### Specified Monsters Only Mode

Minimal recommended configuration:

- `operationMode`: `Enable Specified Monsters Only Mode`
- `targetMonsters`: Enter target monster names, separated by commas
- `partyName`: Enter party name as needed
- `pickup_Mode`: Choose pickup mode as needed

This mode matches monster names in route filenames and descriptions, running only matching routes without applying normal route combination selection logic.

## 3. Team Composition Recommendations

The following are practical suggestions based on BetterGI and Genshin Impact versions at development time. Adapt them according to your own roster and testing.

### Shield & Healer Slots

Consider bringing a shielder and a healer to improve route run stability. Carrying two shielders is generally not recommended since shield health does not stack.

### Auto-Targeting Characters

Consider characters with automated target acquisition and minimal or controllable movement displacement:

- Furina: 25m auto-targeting range.
- Escoffier: 15m auto-targeting range.
- Ineffa: 10m range, dual-center targeting.
- Linnea: 25m auto-targeting range.
- Mavuika: 15m Fire Ring targeting range.
- Sandrone: Built-in specialized support in BetterGI; triggers headlock using `charge` command, requiring teammates to trigger corresponding Starburst states.

### Vacuum / Looting Characters

Groups with Elite mobs can include Kaedehara Kazuha or Jean to pull drops together and improve pickup rates (see [Purpose of Grouping](#purpose-of-grouping)).

### Recommended Teams

The following team comps are subjective suggestions:

<details>
<summary>Recommended Team Compositions & Features</summary>

- `Citlali / Furina / Escoffier / Kazuha`: Stable Freeze, high survivability, no Pyro/Electro to alter Floating Fungi drops, though damage output is moderate.
- `Mavuika / Furina / Citlali (or Nicole / Ineffa) / Kazuha`: Mavuika provides high damage multipliers and outstanding pathing mobility, greatly cutting travel time; lacks dedicated healing which may reduce consistency.
- `Kazuha / Furina / Linnea / Ineffa`: Lunar reaction team with modern scaling, stable shields, and healing.
- `Sandrone / Ineffa / Escoffier / Kazuha`: Viable Sandrone team with consistent Superconduct triggers; excels against multi-hit shield enemies.

</details>

## 4. Advanced Usage Tips

### Purpose of Grouping

Grouping allows different routes to utilize distinct party setups, combat strategies, pickup configurations, or running schedules. Overall target monster counts are configured exclusively in Path Group 1; grouping occurs after route combination selection.

<details>
<summary>Example: Splitting 400 Elites and 2000 Common Mobs</summary>

Assuming each Elite has a 2% chance to drop 4-star Artifact EXP (worth 2520) and an 8% chance to drop 3-star Artifact EXP (worth 1260), the expected Artifact EXP value per Elite is:

`0.02 × 2520 + 0.08 × 1260 = 151.2`

Elite routes therefore yield substantial extra Artifact EXP. If possible, bring Kaedehara Kazuha or Jean on Elite routes to collect drops. Common mob routes do not yield these extra Artifact EXP bonuses and do not require specialized vacuum looting.

Setup Steps:

1. In Path Group 1 configuration, set `targetEliteNum=400` and `targetMonsterNum=2000`. Configure `accountName`, priority tags, exclude tags, sorting, and auto-optimization.
2. In `tagsForGroup2`, enter `Common Mobs`. Routes tagged with `Common Mobs` containing only regular mobs will be allocated to Path Group 2.
3. Routes that do not match Path Groups 2 through 10 will remain in Path Group 1. Since the script does not automatically tag routes as "Elite", verify route assignments via Debug output.
4. Create two BetterGI configuration groups: set `groupIndex` to "Path Group 1" and "Path Group 2" respectively, using identical `accountName`. Each group can define its own party, combat strategy, pickup mode, and runtime limits.
5. Select "Debug Route Allocation" to inspect route assignments and statistics for `group1` and `group2`, then execute both groups as needed. Execution order is managed by the BetterGI Scheduler.

*Do not configure targets as 400-0 in Group 1 and 0-2000 in Group 2. These fields represent the overarching route combination goal, not independent per-group quotas.*

</details>

<details>
<summary>Adding Custom Routes</summary>

Standard BetterGI map pathing JSON formats are supported. Record or export routes using the BetterGI Map Pathing Editor, then place files in `pathing/0-保留/` (or its subdirectories). Minimal route structure:

```json
{
  "info": {
    "name": "Custom Route",
    "type": "collect",
    "version": "1.0",
    "description": "Route Info: Estimated time 60 seconds, Estimated income 0 Mora, Monsters: 4 Elite Local Legends (3x).",
    "map_name": "Teyvat",
    "bgi_version": "0.45.0",
    "tags": []
  },
  "positions": [
    {
      "id": 1,
      "x": 0,
      "y": 0,
      "action": "",
      "action_params": "",
      "move_mode": "walk",
      "type": "teleport"
    },
    {
      "id": 2,
      "x": 10,
      "y": 10,
      "action": "",
      "action_params": "",
      "move_mode": "walk",
      "type": "path"
    }
  ]
}
```

Route File Rules:

- Root object must contain `info` and `positions`. Waypoints, movement modes, actions, and parameters should conform to BetterGI specifications.
- `info.description` uses `预计用时[number]秒` (or estimated seconds) to provide estimated duration, e.g. `预计用时60秒`.
- Monster listings use `包含以下怪物：[count]只[monster_name]、...`. Monster names must match those in `assets/monsterInfo.json` to count towards target quotas and income calculations.
- `info.tags` is an array of strings, e.g. `["Hydro Immune", "High Risk"]`. Used for priority, exclusion, and group allocation.
- Map fields like `info.map_name` and `info.map_match_method` are passed to BetterGI; keep editor-exported values intact.

Run "Debug Route Allocation" after adding files to verify parsing, stats, and grouping.

</details>

<details>
<summary>Adding Custom Template Images</summary>

Place `.png` template files into `assets/targetItems/Other/保留/` or subdirectories. Filenames are used as item names for recognition and pickup logs. Numerical values in parentheses within filenames can specify matching thresholds. Templates are loaded at startup when using template matching pickup mode.

Template Image Sources:
1. Custom Screenshots: Crop the item name region from the in-game interaction list at native resolution and aspect ratio, saved as `.png`.
2. Gathering CD Management: Copy template images from that script's `assets/targetItems/` directory into this script's custom template folder.
3. Community Group: Obtain updated templates from QQ group `1109232869`.

</details>

<details>
<summary>Using Treasure Hoarder Random Events to Supplement Common Mobs</summary>

Treasure Hoarder random event quests spawn 7 common mobs per clear with high task efficiency. These events can be repeated up to 50 times daily (350 common mobs total).

To boost efficiency, append a combat friendship event task at the end of your schedule with "End early when no EXP/Mora gained" enabled, and configure this script's target to 400 Elites and 1700 Common Mobs (`400-1700`).

</details>

## 5. Configuration Item Guide

Fields are listed by category, matching names in `settings.json`:

### Execution Settings

<details>
<summary><code>operationMode</code>: Execution Mode</summary>

Options:
- `Run Mob Farming Routes`: Executes routes based on route selection and group configurations.
- `Debug Route Allocation`: Runs route selection and grouping without executing routes, outputting debug data.
- `Force Refresh All Run Records`: Reinitializes run records for the current account without running routes.
- `Enable Specified Monsters Only Mode`: Executes only routes whose filename or description matches target monsters.

</details>

<details>
<summary><code>groupIndex</code>: Executed Path Group</summary>

Selects the active path group (Path Group 1 through Path Group 10). The script processes only the selected group per run. Groups 2 through 10 read route selection settings from Group 1 under the same account.

</details>

<details>
<summary><code>partyName</code>: Party for Path Group</summary>

Enter party name in BetterGI. The script attempts to switch to this party under applicable modes. Leave blank to disable party switching.

</details>

<details>
<summary><code>validateTeamMembers</code>: Team Member Verification</summary>

Enter character names to verify, separated by commas. After switching parties, the script checks if these characters are present, retrying up to 3 times on failure. Leave blank to skip member verification.

</details>

<details>
<summary><code>sortMode</code>: Route Sorting Within Group</summary>

Options:
- `Original File Order`: Runs routes by filename order.
- `Efficiency Descending`: Sorts routes by calculated efficiency.
- `High Income First`: Prioritizes routes marked as high income.

Default: `High Income First`.

</details>

### Pickup Settings

<details>
<summary><code>pickup_Mode</code>: Pickup Mode</summary>

Options:
- `Template Matching Pickup (Artifact EXP and Monster Materials)`: Loads templates from corresponding directories for recognition.
- `Template Matching Pickup (Artifact EXP Only)`: Loads only Artifact EXP templates.
- `BGI Native Pickup`: Handled by BetterGI's `AutoPick` real-time trigger.
- `Do Not Pick Up Any Items`: Disables pickup logic.

Default: `Template Matching Pickup (Artifact EXP and Monster Materials)`.

</details>

<details>
<summary><code>onlyRelatedItems</code>: Recognize Only Route-Related Materials</summary>

Filters monster material templates based on monsters present in the current route during template pickup. Has no effect in Artifact EXP-only mode, native pickup, or no pickup mode.

Default: Disabled.

</details>

<details>
<summary><code>disableSecondCheck</code>: Disable Item Double-Check</summary>

Disables second-pass confirmation after recognizing an item template. May affect false positive/negative rates depending on templates and display conditions.

Default: Disabled.

</details>

### Route Selection and Grouping Settings

<details>
<summary><code>accountName</code>: Account Name</summary>

Distinguishes data in `settings/`, `records/`, and `blacklists/`. Use unique names for multiple accounts. Path Group 1 saves route selection parameters under this account name, which other groups read.

Default: `默认账户` (Default Account).

</details>

<details>
<summary><code>tagsForGroup2</code> through <code>tagsForGroup10</code>: Path Group Tags</summary>

Matches tags for Groups 2 through 10. Enter tags separated by commas. Routes are matched sequentially from Group 2 to Group 10; routes matching multiple groups are assigned to the earliest matching group. Routes not matched by any tags default to Path Group 1.

</details>

<details>
<summary><code>targetEliteNum</code>: Total Target Elite Mobs</summary>

Total Elite monster quota for the combined route selection. The script automatically reserves extra margin to compensate for missed spawns. This is a global target across all groups, not per group.

Default: `400`.

</details>

<details>
<summary><code>targetMonsterNum</code>: Total Target Common Mobs</summary>

Total Common mob quota for the combined route selection with automated safety buffer. Global target across all groups.

Default: `2000`.

</details>

<details>
<summary><code>priorityTags</code>: Priority Keywords</summary>

Routes containing these keywords in their file path, description, or tags are prioritized. Separate multiple keywords with commas.

</details>

<details>
<summary><code>excludeTags</code>: Exclude Keywords</summary>

Routes containing these keywords in their path, description, or tags are excluded from selection.

Default: `Floating Fungi, Local Legend, Narrow Terrain` (孢子, 地方传奇, 狭窄地形).

</details>

<details>
<summary><code>disableSelfOptimization</code>: Disable Self-Optimization</summary>

Disables dynamic route time adjustments based on historical runtime logs, relying primarily on estimated durations in route files.

Default: Disabled.

</details>

<details>
<summary><code>efficiencyIndex</code>: Mora vs Time Trade-off Factor</summary>

Accepts `0` or positive numbers. Higher values assign greater weight to Mora returns during route selection.

Default: `0.25`.

</details>

<details>
<summary><code>curiosityFactor</code>: Curiosity Factor</summary>

Value between `0` and `1`. Adjusts estimated duration of routes lacking historical records to encourage testing unvisited routes.

Default: `0`.

</details>

<details>
<summary><code>ignoreRate</code>: Ignore Ratio</summary>

Set to `>= 0` to enable. When the ratio of common mobs to elite mobs exceeds this threshold and the route lacks protected tags, the script treats the route's elite count as 0, classifying it as a common mob route. Default `-1` disables this feature.

Default: `-1`.

</details>

### Auxiliary Execution Settings

<details>
<summary><code>activeDumperMode</code>: Dump Truck Mode (Skill Rush)</summary>

Enter character slot indices (1-4) to trigger elemental skills in advance, separated by commas. Disabled for routes containing `keypress(T)`.

</details>

<details>
<summary><code>eatBuff</code>: Consume Food Between Routes</summary>

Enter food dish names, separated by commas. The script attempts to consume food between routes at 300-second intervals.

</details>

<details>
<summary><code>detectRevival</code>: Revival Food Detection Retries</summary>

Enter an integer > 0 to enable revival food detection and consumption. Checks are counted per minute with multi-pass confirmation.

Default: `0`.

</details>

<details>
<summary><code>detectHealthBar</code>: Healing Food Detection Retries</summary>

Enter an integer > 0 to enable HP bar checks and healing food consumption.

Default: `0`.

</details>

<details>
<summary><code>timeRule</code>: Blackout Time Windows</summary>

Supports formats like `8`, `8-11`, `23:11-23:55`, separated by commas. Single numbers represent the entire hour (e.g., `8` means 8:00 to 9:00). Leave blank for no time restrictions.

</details>

<details>
<summary><code>findFInterval</code>: Interaction Icon Check Interval</summary>

Wait time in milliseconds between checks for the pickup interaction icon.

Default: `100`.

</details>

<details>
<summary><code>pickupDelay</code>: Delay After Pickup Keypress</summary>

Delay in milliseconds after pressing the pickup key before the next recognition cycle.

Default: `50`.

</details>

<details>
<summary><code>rollingDelay</code>: Delay After List Scroll</summary>

Delay in milliseconds after scrolling the interaction list.

Default: `32`.

</details>

<details>
<summary><code>timeMove</code>: Scroll Cycle Duration</summary>

Period in milliseconds for scrolling the pickup list up and down.

Default: `1000`.

</details>

<details>
<summary><code>logMonsterCount</code>: Log Monster Count</summary>

Logs the route's expected elite and common monster counts upon route completion for auditing.

Default: Disabled.

</details>

<details>
<summary><code>disableAsync</code>: Disable Async Party Switching</summary>

Switches party change routines to synchronous execution mode.

Default: Disabled.

</details>

<details>
<summary><code>enableCoordCheck</code>: Enable Coordinate Verification</summary>

Executes coordinate checks at route completion. Useful when the host environment does not return route completion status, though it adds slight post-route processing time.

Default: Disabled.

</details>

<details>
<summary><code>useCrystalflyCatcher</code>: Crystalfly Trap Assisted Teleport</summary>

Enter Crystalfly Trap map coordinates in `X, Y` format. When conditions between current position, route start point, and the trap are met, the script opens the map, clicks the trap icon, and teleports toward the route starting point.

</details>

<details>
<summary><code>targetMonsters</code>: Target Monsters (Specified Monsters Mode)</summary>

Used exclusively when `operationMode` is set to `Enable Specified Monsters Only Mode`. Enter monster names separated by commas. Matches against route filenames and descriptions.

Default: Empty.

</details>

## 6. Execution Logic Overview

<details>
<summary>Startup & Config Loading</summary>

On launch, the script loads the active configuration. Path Group 1 writes route selection settings to `settings/{accountName}.json`, while subsequent groups read saved settings for that account. Templates, item blacklists, and run records are loaded before proceeding to the designated execution workflow.

</details>

<details>
<summary>Route Selection & Execution</summary>

Normal mode parses estimated duration, monster counts, returns, and tags from route files, applying priority/exclude keywords, self-optimization, and route combination algorithms. Selected routes are partitioned by group tags, and only the active `groupIndex` is executed during the run.

Specified Monsters Only Mode matches `targetMonsters` directly against filenames and descriptions, placing matched routes into Path Group 1.

</details>

<details>
<summary>Route Result Processing</summary>

When BetterGI returns a boolean `success`, the script adopts the status directly. If no return value exists and `enableCoordCheck` is active, start and end coordinates are verified.

If no return value is provided and coordinate check is disabled, the script cannot reliably verify completion. Failed routes, coordinate anomalies, failure to return to main UI, or disconnection screens prevent updating recorded run times and cooldowns.

</details>

<details>
<summary>Data Files & Directories</summary>

- `records/`: Stores route cooldowns, valid run durations, and template pickup history per account.
- `blacklists/`: Stores item pickup blacklists.
- `settings/`: Stores Path Group 1 route selection configuration per account.
- `Debug结果/` (Debug Results): Stores route allocation debug outputs.
- `pathing/0-保留/`: Custom user pathing routes.
- `assets/targetItems/Other/保留/`: Custom item recognition templates.

Run logs retain the 7 most recent valid run durations by default, and template pickup history tracks the 20 most recent unique item names.

</details>

## 7. Troubleshooting

### Route Not Selected

Check whether the route was matched by `excludeTags`, whether target quotas are already satisfied, whether it belongs to another group, or whether its description lacks parsable duration and monster count data.

### Debug Output Contains Old Files

Since BetterGI does not expose file deletion APIs to JS scripts, running "Debug Route Allocation" does not automatically clear previous files in `Debug结果/group1` through `group10`. Refer to `Debug结果/Route分配结果.txt` for authoritative route rosters, or clear the output folders manually before debugging.

### Item Pickup Not Working

Verify pickup mode, template directories, item blacklists, and game resolution (1920x1080). Template matching requires valid templates; native pickup requires BetterGI's `AutoPick` trigger.

### Route Run Records Not Updating

Verify whether the host returned `success` or if coordinate checks failed. Routes that fail, do not return to the main UI, encounter coordinate mismatches, or hit reconnect screens skip record updates.

### Crystalfly Trap Teleport Not Triggering

Verify coordinate format (`X, Y`), map coordinates, route start coordinates, and trap proximity conditions.

### Party Switch Failure

Ensure `partyName` matches the exact party name configured in BetterGI. If `validateTeamMembers` is configured, ensure those characters are present and correctly recognized.

## 8. Community & Related Projects

- QQ Group: `1109232869`.
- BetterGI Teabag Edition contains dedicated multiplayer mob-farming logic; join the group for details.
- Related Tools: All-in-One Mob Farming, Wholesale Artifact EXP, Multiplayer Group Artifact EXP, Gathering CD Manager, Lock 4-Star Instructor, Only Big Bottles, Magic Widget, Performance Benchmark, and Turbo Food Processing.
- Feedback and configuration discussions are welcome in the group chat.