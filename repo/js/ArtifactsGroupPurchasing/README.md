# AAA Artifact EXP Co-op Group Run
> **Note: This feature requires the Mojang Co-op Tool to enable multiplayer.**

## 1. Features & Principles

1. **Core Principle of Co-op Group Runs**: Multiple players take turns hosting. Other members join the host's world to occupy spots and trigger investigation points. Because each player's world has **independent** investigation points (each with its own daily cap), N players taking turns as host can visit each other's worlds to harvest these additional investigation points loaded by teammates. This is why "group runs" yield significantly higher returns compared to solo artifact farming.
2. **Role Division** (determined by index: 0 = solo / 1 = host / >1 = teammate):
   - **Host (P1)**: Runs the complete route in their own world (pre-run → post-run), acting as the primary gatherer of yields.
   - **Teammates (P2/P3/P4)**: Enter the host's world and execute only "placeholder" routes to occupy corresponding spots (skipping the full route to prevent taking points or getting stuck), then leave after the host finishes that world.
3. **Two Independent Supplemental Route Toggles** (both disabled by default, completely independent):
   - (Pre-run / Extra Route): Check when running solo after co-op cleanup to execute the "Extra/Pre-run" branch.
   - (Snezhnaya Pots): An additional independent route ("Extra/Snezhnaya"), separate from the former and toggled independently.
4. **Resume from Breakpoint & Yield Reporting**: The script reports EXP/Mora for each round to the Mojang group run server, which manages leaderboards, daily caps, and automatic suspension upon disrupted runs (see [Section 4: Operational Principles](#4-operational-principles) for details).
5. **Auto Re-login Support**: Works in tandem with the Mojang Co-op Tool to automatically log back in after co-op sessions end.

## 2. Usage & Configuration

1. Update the script to the BetterGI scheduler via the Mojang Co-op Tool.
2. Right-click the script to modify JS Custom Configuration. The options are explained below:

### Co-op Run Configuration
- **Run Mode**:
  - `Use JSON Configuration File`: Reads co-op information from `匹配信息.json` to initiate co-op sessions.
- **Party Name Used During Run (`partyName`)**: Party name to switch to before entering co-op mode.
- **Character Slot Used During Run**: Slot index of the character to switch to before co-op.

### Cleanup Route Configuration
- **1P Cleanup Route**: The cleanup route run by P1 (host) in their own world. Options include `Fontaine Tower / Tea Leaves / Seiraimaru / Windrest Flower`, defaulting to `Fontaine Tower`. Do not change unless necessary.

### Supplemental Route Configuration
- **Run Extra Route / Co-op Cleanup**: Check when running solo after co-op cleanup. In normal mode, checking this runs the "Extra/Pre-run" branch; in auto-enter mode, it executes extra routes immediately after co-op completion.
- **Run Snezhnaya Pots Route**: An independent supplemental route ("Extra/Snezhnaya"). Executed only when checked; independent of "Extra Route". Enable in the Extra Artifact EXP configuration group.

### Other Configuration
- **Disable Perfectionist Mode**: When checked, executes routes even if party members are missing.
- **Debug**: When checked, skips route execution logic for debugging purposes only.
- **Auto Re-login**: After co-op concludes, automatically reconnects to Mojang using `匹配信息.json`. Enter the minimum required re-login count; disrupted runs do not consume attempts. After successfully hosting and finishing once, it automatically switches to non-host mode. Set to 0 to run only once and stop; enter >0 (such as 1) to ensure hosting.
- **Kick Early After 2/3P Route Completion**: Automatically kicks the corresponding placeholder teammate once their spot route finishes.
- **Co-op Waiting All-in-One Run / Post-Co-op All-in-One Run**: The All-in-One run triggered when reconnecting after a disrupted/normal session, or when finishing without further logins (requires Mojang Co-op Tool).
- **Use All Images for Whitelist Template Matching**: When disabled, selects the image with the most similar filename for each whitelisted teammate.
- **Enable Notifications**: Prints logs; recommended to leave enabled.
- **Pickup Matching Threshold**: Increase if misclicking, decrease if missing pickups; default `0.9`.
- **Detection Interval (ms)**: Delay between checking for the interact key `F`; default `100`.

## 3. Quick Start

### Prerequisites
- Recommended game resolution is `1920×1080` (recognition areas and coordinates are calibrated to this).
- Keep default game keybindings, especially the Interact/Pickup key `F`.
- Run both the Co-op Tool and BetterGI with administrator privileges.

### Co-op Account Guidelines
- **Account Names**:
  - Party names must not contain `\ / : * ? " < > |`, cannot start or end with a space, cannot use reserved Windows device names, and must be ≤ 255 characters.
- **Co-op Rules**:
  - Co-op is based on mutual benefit and fairness.
  - Manually quitting halfway through a run is prohibited.
  - Causing a run to crash or fail due to other reasons also incurs penalties.
- **Multi-Account Management**:
  - When running multiple accounts in co-op, assign each account an independent BGI and Mojang client folder.

## 4. Operational Principles

### Route Directory Structure
Script routes are located in `assets/ArtifactsPath/`, grouped by "Location", with each group containing subdirectories for stages:

| Directory | Meaning | Executed By |
|---|---|---|
| `Location/Pre-run` | Executed by host in their own world **before** P2/3/4 enter | Host |
| `Location/Post-run` | Cleanup route executed by host after kicking P2/3/4 | Host |
| `Location/Placeholder` | Routes run by teammates to hold designated spots in host world | Teammates (P2/P3/P4) |
| `Extra/Pre-run` | Solo supplemental route run after co-op cleanup | Host Solo |
| `Extra/Snezhnaya` | Independent supplemental route for Snezhnaya pots | Host Solo |

Common location groups: Resort, Opera House, Fontaine Tower, Seiraimaru, Tea Leaves, Tatarasuna, etc. (adjusted with version updates).

### Execution Timeline (Manual Login Illustration)
```text
Enter player name/UID and click login to join co-op room (departs when full)
        │
        ├─ Host in own world: Pre-run route, preliminary preparations.
        │
        ├─ Wait for teammates to enter host world.
        │
        ├─ Teammates execute placeholder routes to designated spots; host checks spots, failure treated as crashed run.
        │
        ├─ Host begins artifact EXP collection route.
        │
        ├─ Host kicks P2/3/4 placeholder members early once their spot routes finish.
        │
        ├─ Host executes post-run cleanup route.
        │
        └─ Extra Configuration Group: Host runs Extra/Snezhnaya supplemental routes solo.
```

### Mojang Group Run Server Rules
The JS script only handles collection and reporting; **yield logging, daily caps, penalty freezing, and leaderboards** are processed by an independent Mojang server:
- **Yield Cap**: Single-run EXP or Mora exceeding 150,000 is flagged (anti-cheat); combined daily EXP + Mora exceeding 260,000 is reset to zero on leaderboards.
- **Automatic Disruption Suspension**: Being the faulty party in a disrupted run suspends and logs out normal users after 2 occurrences, or trusted users after 100 occurrences in a day.
- **Leaderboards**: Display yields only; contain no restriction logic.
- **Points System**:
  - Hosting a run costs 3 points; teammates gain 1 point (first placeholder run of the day grants an extra 1 point).
  - In a crashed run, the at-fault party loses 6 points, while other participants receive 2 points in compensation.
  - Multiple crashes trigger the account freeze mechanism.
  - Players with the highest points have priority to host.
  - Additional features for points may be added in the future.
- **Co-op Order**:
  - Higher points get priority to become host.
  - Group members co-op for mutual benefit; veteran players also contribute dedicated alt accounts to hold spots.

## 5. Team Configuration Recommendations

- **Host (P1) Active Slot**: Priority given to Dehya (high resistance, provides movement speed) or Kaedehara Kazuha (groups artifact drops).
- **Movement Speed**: If computer performance is modest, lower party movement speed (use shorter character models, avoid double Anemo) for more reliable collection.
- **Placeholder Members**: Anemo characters preferred.

## 6. FAQ

- **Multiplayer artifact farming uses a dedicated tool developed by Mojang; you must pass a test run using the co-op test JS before participating.**
- **This script is intended for players who already have experience with artifact farming routes and know how to use BetterGI. For basic BGI questions, please refer to the main community group.**
- **How to test tools with the author**: QQ group 1109232869 (Mojang testing and feedback), backup group 1022240522.
- **Expected Yields**: Approximately 180,000 artifact EXP and 40,000 Mora daily; Snezhnaya adds roughly 20,000 EXP and 5,000 Mora; total time required is around 110 minutes.
- **Why is it not picking up items?**: Check if resolution is 1080p (higher/lower resolutions do not guarantee normal operation), and ensure `F` key has not been rebound.
- **Why are yields lower than expected?**: You may have run other routes earlier that triggered investigation points; after first setup or player changes, run later than the previous day to ensure points have respawned; lower PC performance can cause path drift—use compatibility mode or close background apps.
- **Auto Enter / Re-login does not respond**: Ensure Mojang is running in the background and UID / name images match in-game.
- **Errors during execution**: If the script is still running normally, you can ignore transient glitches.
- **Feedback**: Feedback is accepted only via QQ, not GitHub issues.
- **Mojang Suite (Partial List)**:
  - All-in-One Mob Farming: One-stop automated mob farming, supports picking up artifact EXP only.
  - AAA Artifact EXP Wholesale: Automatically timed solo artifact EXP route for maximum yield.
  - AAA Artifact EXP Co-op Group Run: Multiplayer co-op for enhanced artifact EXP yields.
  - Gathering CD Management: Manages and optimizes gathering routes with cooldown tracking.
  - Lock 4-Star Instructor: Automatically locks 4-star Instructor artifacts, supports filtering for 3 initial substats and Energy Recharge.
  - Only Big Potions: Decomposes artifacts into Sanctifying Essence wherever possible for cleaner inventory.
  - Mojang Utility Toolkit.
  - Benchmark Test: Tests PC performance for script execution.
  - Food Processing Turbo Version: High-speed food processing matching Gathering CD Management.
  - Join the community group for more tools.
