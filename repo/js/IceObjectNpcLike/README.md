# Ice Object NPC Likes Automation

Author: 一只低熵体 (Low Entropy Body)  
Version: `1.3.0`  
Estimated Total Likes Across All Routes: `48`

This script uses BetterGI pathing to navigate to Snezhnaya / Nod-Krai NPC locations, automatically placing two Ice Objects, waiting for Likes, dismantling them, and performing final cleanup. It does not read game memory, does not use network connections, third-party software, key/mouse macros, OCR, or Likes image recognition.

## Requirements & Prerequisites

- BetterGI `0.64.0` or higher;
- Simplified Chinese game client (UI elements and pathing rely on standard client layouts);
- 16:9 aspect ratio, at least `1920×1080`;
- BetterGI capture mode set to `BitBlt`;
- Minimap set to "Lock Orientation";
- Genshin Impact horizontal and vertical camera sensitivity kept at default value `3`;
- Keep default brightness, disable HDR, color filters, and GPU overlays;
- Ice Object hotkey set to `T`; relevant areas and Teleport Waypoints must be unlocked;
- Do NOT operate the keyboard or mouse while the script is running.

## Quest & Route Unlocks

- Completing Act IV ("Dawn After Snow") of the three settlement quests usually makes NPCs around Points 06, 07, 09, and 10 visible; Point 08 NPC appearance also involves the real-time next-day quest "Visitor in the Fresh Snow". Refer to: [Dawn After Snow Guide](https://www.bilibili.com/video/BV172bX6XEPm/), [Visitor in the Fresh Snow Guide](https://www.bilibili.com/video/BV1nqbX6fEDS/).
- Invisible NPCs do not necessarily prevent earning Likes: on some accounts where quests were incomplete and NPCs were invisible, placing Ice Objects still successfully yielded Likes during testing. The script does not verify quest progress or actual Likes; refer to your own in-game results.
- All routes require relevant areas and standard Teleport Waypoints to be unlocked. Point 12 prioritizes the "Special Recruitment Plan" quest entry shortcut; if teleporting or landing verification fails, it automatically falls back to the full route from the standard Teleport Waypoint. Unlocking the quest entrance waypoint is therefore not strictly required.

## Likes Mechanism

The following rules are derived from configuration data shared by [breadgrocery in PR #3613](https://github.com/babalae/bettergi-scripts-list/pull/3613), not from memory reading:

- Placing an Ice Object within approximately `15` meters of an NPC's spawn point or activity center triggers Like evaluation. Occlusion by buildings/walls or invisible NPCs due to quest states does not necessarily prevent Likes.
- An NPC listed as likable in data does not guarantee Likes on-site: some terrains or areas cannot support Ice Object placement. The route table lists only locations cataloged in this script, expecting `2` Likes per NPC across two placements.
- The script does not detect NPCs, trigger radii, or actual Likes received; if game updates alter scenes, actual in-game results take precedence.

## Usage

1. Subscribe to or import the script in BetterGI.
2. Right-click the script and select "Edit JS Custom Configuration".
3. Under "Enable Routes", select the Points to run (defaults to Points 01–12, toggle according to your account's progress).
4. Add the script to the Task Scheduler and run. For the first test run, using "Recommended Order" is suggested.

New configurations default to running all 12 Points, totaling an estimated `48` Likes. Actual Like quantities are not visually verified. When upgrading from older versions with preserved settings, the script keeps previous selections; please verify under "Enable Routes".

## Route Overview

| Route | Location | Likable NPCs | Expected Likes | Remarks |
|---|---|---|---:|---|
| Point 01 | Northland Bank Entrance | Izmaylov, Karelin, Yurova | 6 | Standalone route |
| Point 02 | Souvenir / Sigil Shop Entrance | Evlina, Tsisoslina, Lopushina, Blyushko | 8 | Standalone route |
| Point 03 | Cinder Canteen Entrance | Grigori, Tsylyanov | 4 | Standalone route |
| Point 04 | Restaurant Entrance | Eliseev | 2 | Standalone route |
| Point 05 | Near Blacksmith | Kuzmichev | 2 | Standalone route |
| Point 06 | Dawn Station Toy Stall | Cherkassky, Mayskaya | 4 | Passes heat recovery device along the way |
| Point 07 | Station Restaurant | Dustaya, Ignatov | 4 | Chains to 08, 09; passes heat recovery device |
| Point 08 | Station Torchside | Shishkina, Golovin, Yarkova | 6 | Chains after Point 07 |
| Point 09 | Station Platform | Letova | 2 | Chained route; uses alternate route if 08 is disabled |
| Point 10 | Inside Dawn Station | Khrutalyov, Timyakov, Dolokhov | 6 | Passes heat recovery device along the way |
| Point 11 | Torch Bookstore | Mo | 2 | Passes heat recovery device along the way |
| Point 12 | Winter Covenant Training Ground | Yaroviya | 2 | Prefers quest shortcut; falls back to standard waypoint on failure |

### Station Continuous Routes

- When Points 07, 08, and 09 are all enabled: `Point 07 → Point 08 → Point 09`; if Point 09 is disabled, finishes at Point 08.
- When Point 08 is disabled but Point 09 is enabled: Automatically switches to the `Point 07 → Point 09` full alternate route.
- When Point 07 is disabled: Points 08 and 09 (which depend on current position) are automatically skipped.

Continuous route groups are not interrupted by teleports or heat recovery trips.

## Operating Modes

- **Recommended Order**: Default mode. Executes in order: `01→02→03→06→05→04→07→08→09→10→11→12`. Disabled routes are skipped while maintaining 07–09 as a continuous group.
- **High Likes Priority**: Executes all enabled routes sorted by expected Likes in descending order.
- **High Yield Streamlined (6+ Likes)**: Executes only route groups with an expected yield of `6` Likes or higher.

When all routes are enabled, High Yield Streamlined mode executes the Point 07–09 chained group (12 Likes), Point 02 (8 Likes), Point 01 (6 Likes), and Point 10 (6 Likes), totaling an estimated `32` Likes.

## Heat & Camera Control

Upon starting, the script visits a fixed Statue of The Seven to restore thermal heat; heat recovers automatically within range without pressing `F`. When Points 01–12 are **all enabled**, all three operating modes only return to the Statue once at the very beginning. When any route is disabled, the script internally switches to returning to the Statue every `4` completed Points. Continuous route groups will not be broken up; if the next group exceeds the remaining allowance, heat is restored before starting the group. Heat strategy is managed automatically without manual user setup.

Based on recorded routes, Points 06, 07, 10, and 11 pass thermal heat recovery devices before placing Ice Objects, restoring an estimated `60` heat each time; two placements per Point consume approximately `10` heat. The Recommended Order executes Point 06 fourth to reach a recovery device earlier. The script **does not read actual heat levels or verify if in-transit recovery triggered**; the single initial Statue visit strategy relies on these recovery devices working normally.

After reaching each Point, the `orientation` at the end of the route locks the horizontal view. The script pushes the vertical camera to its upper limit, then pans down according to "Ice Object Placement Camera Angle" (default: `7500`).

On `3840×2160` (4K) or higher resolutions, the script waits an additional `800ms` after pressing `T`. On other resolutions, if UI animations lag behind clicks, you can manually enable this timing compensation.

## Common Settings

| Setting | Default | Recommendation |
|---|---:|---|
| Route Operating Mode | Recommended Order | Keep default for initial runs |
| Enable Routes (Multi-select) | Points 01–12 all selected | Deselect based on quest completion; Points 08/09 depend on 07 |
| Ice Object Camera Angle | 7500 | Controls final placement position |
| Force Enable 4K Timing Compensation | Disabled | Enable if clicks occur before UI animations finish on non-4K displays; 4K enables automatically |

## Troubleshooting & Limitations

- If multiple routes experience teleport click offsets simultaneously, completely exit and restart BetterGI.
- If pathing wobbles repeatedly, ensure `BitBlt` capture mode is used, minimap is locked to North, frame rate is stable, and try `2560×1440` if possible.
- If the script stops prematurely or encounters an error, manually verify whether an Ice Object remains and press `T` to exit the placement interface.
- Point 12 shortcut teleports and verifies minimap position first; if landing cannot be confirmed, it conservatively switches to the standard waypoint route.
- Expected Likes in logs come from route metadata; the script does not visually recognize actual Likes received, heat values, or deletion outcomes.

## Acknowledgments

Special thanks to [breadgrocery](https://github.com/breadgrocery) for sharing Likes mechanics and comprehensive NPC coordinate data in [PR #3613](https://github.com/babalae/bettergi-scripts-list/pull/3613), which made this route and NPC mapping table possible!
