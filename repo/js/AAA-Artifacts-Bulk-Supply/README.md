# AAA Artifact EXP Bulk Supply

## 0. Features and Operating Principles

1. Automatically manages timing and selects routes based on the current schedule:
- Alternates between two 98-spot rich regular routes daily.
- Once the target activation time is reached (1 minute later than yesterday by default), it activates points first to lock in their respawn timers. If the regular route completes before reaching the target time, it switches to the Alternate Cleanup Route (running the **Alternate Cleanup Route** enables running the higher-yield **Priority Cleanup Route** the following day). Snezhnaya glass jars are only activated during Cleanup Extra A.
- After activation completes, it continues collecting the remaining regular route (investigation spots are NOT collected during activation; see [Investigation Spot Mechanics and Respawn Cooldown](#investigation-spot-mechanics-and-respawn-cooldown)).
- Finally, it runs the Cleanup and Extra routes in sequence.
2. Supports various artifact salvaging configurations (see Custom Configuration and instructions below).
3. Supports resume from breakpoint: rerunning within the same day automatically skips finished routes and proceeds with remaining ones (interrupting during the ~3-minute activation phase is not recommended).
4. Automatically detects failed routes and logs warnings, recommending manual exploration/teleport point unlocking.

## 1. Usage and Configuration

1. Add the script to the BetterGI Scheduler.
2. Right-click the script to edit JS Custom Configuration:
- **Artifact EXP Team Name**: Enter the team name used for collecting artifacts. Dehya or an E-skill healer is recommended as the active runner. Recommended characters: Dehya (high resistance, daytime movement speed bonus), Kaedehara Kazuha (some routes use Kazuha's skill to gather artifacts, improving pickup success rate).
- **Mob Clearing Team Name**: Enter your combat team name to clear regular mobs along artifact routes. Leave empty to skip mob clearing. **Requires a matching combat script.**
- **Minimum Time Interval**: Delay offset compared to yesterday (default 1 minute) before starting activation for cleanup and extra spots.
- **Max Extra Wait Time**: After collecting 98 spots, choose to wait up to N minutes to time extra over-cap spots. When total auto-delay exceeds `(30 + max extra wait time)` minutes, activation and Extra A reset automatically (daily auto-delay increases by 1 min by default); during reset, activation and Extra A are skipped.
- **Force Alternate Cleanup Routes**: Disabled by default. For users who want to collect other investigation materials (such as tea leaves) on alternate days by replacing files in the backup cleanup route.
- **Snezhnaya Route Activation Configuration**: Disabled by default. Activates Snezhnaya routes without picking up artifacts, locking in timers for future co-op jar farming.
- **Snezhnaya Extra Cleanup Route**: Disabled by default. Picks up artifacts along the Snezhnaya extra route for solo players. Do not enable if sharing/cross-farming in co-op.
- **Artifact EXP Salvage Mode**: Retain by default. Options include salvaging into EXP bottles (Sanctifying Unction) or Mora.
- **Account Name**: **No change needed for single accounts.** For multi-account setups, create separate configuration groups per account and enter the in-game account name to track records independently.
- **Furina**: Supports automatically switching Furina to Pneuma (healer) form as a survivability option during artifact runs. Ensures Furina stays in Pneuma form during artifact collection and switches back to Ousia for combat and script termination.

## 2. Quick Start

For first-time users, the following minimal configuration is recommended:

- Artifact EXP Team Name: The exact team name configured in BetterGI
- Mob Clearing Team Name: Leave blank if mob clearing is not needed
- Minimum Time Interval: `1`
- Max Extra Wait Time: `0`
- Cleanup Route: Uncheck "Co-op Cleanup Mode"
- High-Speed Mode: Uncheck
- Artifact EXP Salvage Mode: `Keep` (Retain)
- Pickup Mode: `Template Matching Pickup`

Recommended Presets:

| Mode | Scenario | Key Configuration |
|---|---|---|
| Stable Mode | First-time use, average PC performance | High-Speed Mode OFF; Salvage Mode: Keep; Pickup Mode: Template Matching; Max Extra Wait: 0 |
| High-Speed Mode | Focus on short runtime, acceptable yield drop | High-Speed Mode ON; skip activation and preparation routes; use express routes |
| Co-op Mode | Prepare investigation spots for co-op farming | Co-op Cleanup Mode ON; enter `autoOnline`; configure mob clearing team as needed; use BetterGI native pickup |

### Prerequisites

- Use a BetterGI version that supports this script's API. Current route metadata requires `bgi_version 0.45.0` with functional pathing/map tracking.
- Game resolution must be set to `1920×1080`; recognition areas and click coordinates are configured for this resolution.
- Keep in-game keybindings at default, especially the Interact/Pick Up key `F`.
- The Artifact EXP Team Name must match the team name in BetterGI configuration exactly.
- If a Mob Clearing Team is specified, an appropriate combat strategy must be configured for that team; leave blank to skip mob clearing.
- When using `BetterGI Native Pickup`, ensure `AutoPick` is enabled and properly configured in BetterGI.
- When enabling the Furina option, Furina must be present in the artifact team.
- Using Co-op mode and `autoOnline` requires an external tool that supports the corresponding command format.

### Configuration Format Constraints

- Account Name is used to generate record files: cannot contain `\ / : * ? " < > |`, cannot start or end with a space, cannot use Windows reserved device names, and must not exceed 255 characters.
- Minimum Time Interval and Max Extra Wait Time must be non-negative integers (in minutes).
- `TMthreshold`: Decimal between 0 and 1. Increase if false pickups occur; decrease if items are missed.
- `findFInterval`: In milliseconds, clamped between 16 and 200 ms.
- `autoOnline`: Format is `GameName-UID-TargetRoom`; do not use hyphens `-` within the name or room.
- Only fill in `autoOnline` when Co-op Cleanup Mode is enabled; leave empty for normal mode.

## 3. How It Works

### Investigation Spot Yields

| Type | Equivalent 1★ Artifacts | Average EXP | Average Mora | Formula |
|---|---|---|---|---|
| Common Spot | 1.35 | 567 EXP | 0 Mora | 65% chance of 1★ (420 EXP) + 35% chance of 2★ (840 EXP) |
| Rich Spot | 1.5 | 630 EXP | 200 Mora | 50% chance of 1× 1★ (420 EXP) / 50% chance of 2× 1★ (840 EXP) |

### Investigation Spot Mechanics and Respawn Cooldown

#### Misconception

❌ *Common Misconception*: Many players assume the **24-hour cooldown** begins when pressing `F` to investigate.

#### Actual Mechanics

✅ **Core Principle**:
- **The game engine only loads map assets within a fixed radius centered on the player. Investigation spots are activated and start their glowing visual effect at this moment (spots on active cooldown will not activate). The cooldown countdown begins as soon as the spot data enters memory.**
- **The daily limit of 100 interactive investigation spots resets at 04:00 AM server time. Once 100 spots are investigated, entering unloaded areas will no longer activate new investigation spots.** Within the currently loaded area, already activated spots do not disappear and can still be investigated.

#### Important Characteristics

- **Independent of whether you investigate/collect them**! Even if not picked up or if you log off, the CD continues ticking down. Example: If you pass through an area at 10:00 AM, triggering the 24-hour CD spot to glow, and leave, then return at 3:00 PM to pick it up, tomorrow this spot's CD will end at 10:00 AM and can be collected again.
- **Multiple loadings on the same day do not reset the timer**: Loading an investigation spot again before its CD expires (whether collected or not) will not reset the countdown.

### Route Configuration and Yields

#### Main Route Parameters

| Route Name | Investigation Spots | Rich Spots | Common Spots | Total EXP | Total Mora | Runtime | 98-Cap Rich % |
|---|---|---|---|---|---|---|---|
| Rich Route A | 162 | 105 | 57 | 99,099 | 22,600 | 69 min | 98/98 (100%) |
| Rich Route B | 135 | 105 | 30 | 83,790 | 21,000 | 53 min | 98/98 (100%) |
| ABE Route A | 137 | 33 | 104 | 77,742 | 6,600 | 41 min | 27/98 (27.5%) |
| ABE Route B | 138 | 34 | 104 | 77,868 | 6,800 | 43 min | 33/98 (33.6%) |
| Snezhnaya Extra | 34 | 34 | 0 | 20,400 | 5,100 | 6 min | 34/34 (100%) |

*Note: Snezhnaya routes only run alongside Cleanup Extra A. Please use a scheduled start time to stabilize activation timing for cleanup extra routes.*

#### EXP Formula

`Total EXP = (Rich Spots × 1.5 + Common Spots × 1.35) × 420`

Detailed Route Documentation: [Kingsoft Docs - Route Details](https://www.kdocs.cn/wo/sl/v13uXscL)

## 4. Route Structure

- **Activation**: Pre-loads spots to trigger cooldown timers early, allowing flexible collection timing later without worrying about cooldown desync.
- **Preparation**: A few spots need to be triggered into glowing spots beforehand without collecting them. Certain high-value rich spots are guarded by common mobs; these are cleared first before running the collection sequence.
- **Regular A**: Up to 98 investigation spots, alternated daily without needing timing delays.
- **Regular B**: Up to 98 investigation spots, alternated daily without needing timing delays.
- **Cleanup**: Investigation spots located in the immediate vicinity beyond the 100-spot limit.
- **Extra**: Spots that do not disappear upon reaching the daily cap (over-cap spots). Extra routes are affected by activation timing; when total auto-delay exceeds `(30 + max extra wait time)` minutes, activation resets automatically (+1 min auto-delay daily).
- **Snezhnaya Cleanup Extra A**: Glass jars with an independent 200 cap; special over-cap spots that require visiting 6 co-op worlds to max out (currently 34 per world).

### Execution Timeline

```text
Previous Activation Time
        │
        ├─ First half of Regular Route (Collecting, running until target time)
        │
        ├─ Target Activation Time reached: Activation / Preparation / Mob Clearing (No pickup)
        │
        ├─ Second half of Regular Route (Collecting)
        │
        └─ Cleanup Route + Extra Route (Collecting)
```

The regular route itself serves as part of the wait time for the target activation time; there is no idle waiting for 24 hours. Once the target time is reached, activation, preparation, and mob clearing are executed.

## 5. Team Configuration Recommendations

- **Adjust movement speed according to CPU performance**: If PC performance causes pathing drift or lower yields, reduce team movement speed (use shorter character models, omit Anemo Resonance, Lost Prayer to the Sacred Winds, Dehya's passive, etc.).
- **Active Runner**: Dehya preferred, or an E-skill healer like Barbara.
- **Dehya + The Bell**: High survivability + 10% movement speed bonus between 06:00 and 18:00 (optional JS setting to set time to day automatically).
- **Kaedehara Kazuha**: Recommended; the path has built-in E-skill vacuuming logic (runs fine without him). Jean can serve as an alternative; do not run both Jean and Kazuha simultaneously.
- **Anemo Resonance**: +10% Movement SPD, -15% Stamina Consumption.

## 6. Other FAQ

- **Why is it no longer picking up items?** Check if resolution is `1920×1080` and verify that keybindings have not been altered.
- **Why are yields much lower than expected?**
  1. Other routes may have been run earlier, accidentally consuming investigation spots.
  2. For the very first run, it is recommended to start later than any previous artifact runs to ensure spots have refreshed.
  3. Lower PC performance can cause pathing drift or overshooting; consider lowering graphics settings and closing background apps.
- **The script is too slow compared to ABE (40 mins)?** You can use ABE instead.
- **Can I pick up other items during artifact runs?** You can extract item images from the "All-in-One Mob Farming" JS and place them into `assets/targetItems` of this script.
- **An error occurred in the log:** If the character is still moving and functioning, it may be non-critical and can be ignored.
- **Feedback & Community**: QQ group 1109232869 (alternate group 1022240522).
