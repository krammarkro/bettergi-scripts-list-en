# AAA Fontaine Ley Line Outcrop Notes & Instructions

## 0. Preface

- This code is for learning and entertainment purposes only. Please delete within 24 hours of downloading. Commercial use is prohibited. If you find bugs, feedback is warmly welcomed in the test group or via QQ 119996800.
- Thanks to Pingmianjing (平面镜) and D Daodan (D捣蛋) for their base routes and logic.

## I. Summary Notes


## II. Configuration Overview

1. **"Friendship Party" and "Combat Party"**: If "Friendship Party" is set (used to claim rewards after completing Ley Line Outcrops, as well as claiming Encounter Points and daily commission rewards), "Combat Party" must also be configured, otherwise the script cannot run.
   - Trivia: Condensed Resin only counts as one Ley Line Outcrop clear. When doing an all-in-one run, you don't necessarily have to craft Condensed Resin beforehand—you can claim daily rewards after running Ley Lines. If neither "Friendship Party" nor "Combat Party" is filled in, the script will not switch party for Ley Line Outcrops (it is recommended to match the party set in BetterGI settings).

2. **If "Claim Daily Commission Rewards upon completion" is checked, "Friendship Party" is required**: It is recommended to fill in both "Friendship Party" and "Combat Party" regardless of need (setting both to the same party is fine).

3. **"Farming Count"**: Defaults to 6. Each route contains 4–6 blossoms. If you do not want to farm too many times, choose Single Route mode; it will only clear blossoms within one route up to the "Farming Count". If "Resin Depletion Mode" is selected, it will continue searching for new routes after clearing one until Condensed Resin and Original Resin are depleted (it will not consume Fragile Resin, so rest assured).

4. **Select "1" by default to farm blue Ley Line Blossom of Revelation (Character EXP Materials), and "2" for golden Ley Line Blossom of Wealth (Mora)**.

5. **Configurable Excluded UIDs**: Prevents specified UIDs from farming Ley Line Outcrops, detected via OCR on the UID in the top-left corner of the Paimon menu. If multiple UIDs need exclusion, separate them with a slash "/", e.g., `12345678/99999999`. Tested: as long as the background behind the UID numbers has a clean color without animated namecards, recognition accuracy is 100%.

6. **Direct Run Mode**: After clearing one Ley Line Outcrop, if the next blossom is relatively close, runs directly instead of re-teleporting.

7. **Asynchronous Combat Detection**: Enabled by default. Please disable "Faster combat end detection" and "Rotate search for enemies" in the configuration group, as they may cause issues.


## III. Changelog

### v4.5 Fully Automated Fontaine Ley Line Outcrops (2026-08-04)

- Adapted to double-click use key
- Added character switching to prevent stuttering/glitching during Mavuika's motorcycle state

### v4.4 Fully Automated Fontaine Ley Line Outcrops (2026-06-19)

- Adjusted resin recognition bounding box to improve Original Resin detection rate.

### v4.3 Fully Automated Fontaine Ley Line Outcrops (2025-10-23)

- Fixed an unknown bug on some PCs where getting map center threw an exception when searching for Ley Line Outcrops; added retry mechanism with zoom adjustment upon error.

### v4.2 Fully Automated Fontaine Ley Line Outcrops (2025-10-21)

- Fixed region selection bug.
- Removed swimming detection logic, as BetterGI core now supports swimming detection and returning to combat node.

### v4.1 Fully Automated Fontaine Ley Line Outcrops (2025-09-26)

- **Optimizations**:
1. Removed dragging mode for finding Ley Line Outcrops; all searching now uses Adventurer Handbook.
2. USEMASK mode might fail on some devices; optimized image recognition modes.
3. Optimized disabling auto-pickup triggers to prevent accidentally opening Ley Line Outcrops prematurely.
4. Removed call to BetterGI auto-heal / food consumption feature (temporarily disabled due to bugs).

### v4.0 Fully Automated Fontaine Ley Line Outcrops (2025-09-11)

- **Optimizations**:
1. Optimized template matching for Condensed Resin and Transient Resin, switched to standard matching with dynamic thresholding based on resolution.

### v3.9 Fully Automated Fontaine Ley Line Outcrops (2025-09-10)

- **New Features**:
1. Added Primogem resin refill feature: when configured resin types are depleted and remaining runs > 0, Primogems can be used to replenish Original Resin and claim rewards.

- **Optimizations**:
1. Adapted to version 6.0 reward claiming UI.
2. Optimized timing for opening Adventurer Handbook to search for Ley Lines; added confirmation that the world map has opened before searching.
3. Optimized resin recognition accuracy.

### v3.8 (2025-08-30)

- **Optimizations**:
1. Switched to template matching for Condensed Resin detection using color mask templates; requires BetterGI version >= 0.47.1.
2. Lowered matching threshold for 2K and 4K resolutions to improve recognition accuracy.
3. Optimized handling for prematurely opened Ley Line Outcrops.

### v3.7 (2025-08-28)

- **Optimizations**:
1. Optimized memory release.

### v3.6 (2025-08-18)

- **Optimizations**:
1. During reward claiming, optimized error handling for automatically returning to Statue of The Seven to heal upon death or low HP.
2. Optimized special combat locations for Route 2 and Route 6.
3. Added swimming detection; returns combat failure upon detecting swimming status, retrying up to 2 times.
4. Supports BetterGI native Auto Taking Medicine (v48.0+):
   - Configure detection and consumption interval in "Real-time Triggers -> Auto Taking Medicine" (defaults recommended).
   - Currently supports HP recovery and revival food (requires NRE / Nutrition Generator; enable "Taking Medicine Detection" in JS config, disabled by default).
   - Buff food is currently unstable and not supported by this JS script.
5. Optimized log output and configuration display.

### v3.5 (2025-08-09)

- **Optimizations**:
1. Added error correction for resin recognition.
2. Optimized timing for asynchronous detection of prematurely opened Ley Line Outcrops.

### v3.4 (2025-08-07)

- **Optimizations**:
1. Optimized timing for opening Adventurer Handbook to reduce opening failures.
2. Added return function on party switch failure to prevent getting stuck on party setup screen.
3. If party switch fails or blossom cannot be found when claiming rewards, re-searches using map tracking.
4. Optimized default JS settings display and order.
5. Optimized combat location for the 2nd blossom on Route 6 to avoid swimming.

### v3.3 (2025-07-16)

- **Optimizations**:
1. Optimized logic for locating Ley Line blossom after combat, improving reward claiming success rate.
2. Optimized error handling for combat completion and reward claiming exceptions.
3. Fixed issue where Transient Resin could not be used.

### v3.2 (2025-07-05)

- **New Features**:
1. Defaults to searching Ley Line Outcrops via Adventurer Handbook, more stable than before.
2. Added recognition of both Ley Line types on the same route to skip non-target blossoms.
3. Added death detection to automatically recover and continue execution.

- **Optimizations**:
4. Optimized JS configuration display.
5. Handled special case for the 5th blossom on Route 2 to resolve issue with combat area being too far from blossom.
6. Set asynchronous combat as default.
7. Optimized reward claiming speed.

### v3.1 (2025-07-02)

- **Optimizations**:
1. Optimized OCR region for resin recognition.
2. Optimized log display.
3. Fixed image recognition constructor error.

### v3.0 (2025-07-01)

1. Automatically retries up to 2 times upon combat failure.
2. Optimized display logic when Transient Resin is present and Fragile Resin is not shown.
3. If Ley Line has already been defeated, proceeds directly to claiming rewards.

### v2.9 (2025-06-29)

1. Added resin count recognition to prevent running an extra route when resin is depleted.

### v2.8 (2025-06-26)

1. Reduced number of waypoints in direct run mode to prevent getting stuck.

### v2.7 (2025-06-21)

1. Optimized timeout settings.

### v2.6 (2025-06-20)

1. Fixed parameter error.
2. Optimized coordinates for approaching Ley Line blossoms and claiming rewards, removing unnecessary verification points for faster arrival and claiming.

### v2.5 (2025-06-19)

1. Adapted resin selection to version 5.7:
   - Instructions: Set resin order: 1=Condensed Resin / 2=Original Resin / 3=Fragile Resin / 4=Transient Resin, separated by `/`. Enter corresponding numbers (default: `1/2`, meaning Condensed Resin first, then Original Resin; unlisted types are not used).

### v2.4 (2025-06-13)

1. Handled 5th blossom on Route 2 to avoid teleporting into Emperor of Fire and Iron cave.
2. Adjusted OCR bounding box for reward claiming and added preferred resin type selection (adapted to 3x Ley Line Overflow).
3. Adjusted count-based execution logic to fix issue where count exceeds blossoms available on a single route.

### v2.3 (2025-05-28)

1. Optimized Ley Line blossom search logic.

### v2.2 (2025-05-24)

1. Added asynchronous combat end detection based on code by D Daodan and Qiu Yun.

### v2.1 (2025-05-12)

1. Updated UID recognition method (adapted to Genshin Impact UI changes).

### v2.0 (2025-05-03)

1. Rewrote Ley Line search route method, removed fuzzy search mode.
2. Added direct run mode: after completing a blossom, if the next blossom is close, run directly instead of re-teleporting (requires BetterGI v44.8+).

### v1.3 (2025-04-22)

1. Optimized detection during final reward claim to check whether accidental interaction with Ley Line Outcrop causes task failure.
2. Fixed issue in fuzzy mode where script continued searching when a blossom was not found.
3. Optimized startup route under fuzzy search.
4. Fixed software error caused by Ley Line Outcrop page detection.

### v1.2 (2025-04-14)

1. Optimized party switch timing to avoid exit due to switch failure.
2. Fixed inaccurate recognition on Route 2 in Fast Search mode.
3. Optimized early blossom detection timing.
4. Special handling: Route 2 in Fontaine (West Slopes of Mont Automnequi waypoint bottom-left 5th blossom) runs directly to avoid mistakenly teleporting to underground Crab.

### v1.1 (2025-04-10)

1. Fixed auto combat walking forward continuously.
2. Fixed issue where the first combat did not switch to the Combat Party.
3. Fixed filename typo for Route 1 3rd blossom.
4. Fixed issue where empty party name was treated as defined after deleting it from settings.
5. In Resin Depletion Mode, fixed issue where full route wasn't finished; now forcibly completes the full route.
6. Added fallback: if Ley Line route is not at initial position, fast mode won't find it but fuzzy search might; after route has been partially cleared, iterates through remaining blossoms on route regardless of resin status; restores resin check once found.
7. Optimized accuracy in Fast Search mode.
8. Optimized search range and coordinates in fuzzy mode.
