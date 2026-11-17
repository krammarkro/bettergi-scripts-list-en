# Daily Commissions via Encounter Points - User Guide

## Feature Overview

1. **Party Management**:
   - Automatically switches to a designated party (Friendship team).
   - Optional teleportation to a Statue of The Seven for party switching.
   - Dedicated Navigation Party: If your Friendship team includes characters not yet recognized by BetterGI, the script can switch to an established team for pathfinding, then switch back to claim rewards.

2. **Encounter Points Redemption**:
   - Automatically checks if Encounter Points can be claimed (requires spending 120 Original Resin).
   - Automatically claims Encounter Points rewards.

3. **Double Companionship EXP**:
   - **Claiming Daily Commission rewards using Encounter Points while inside a friend's Serenitea Pot awards Double Companionship EXP!**
   - **Requires starting with a 4-member party, but specific slots can be removed so <= 2 characters actually receive the EXP.**
   - Automatically enters a friend's Serenitea Pot.
   - Supports targeting specific friends or requesting access to multiple friends in sequence (up to 7).
   - Automatically removes designated party slots to optimize Companionship EXP distribution.

4. **Completion Check**:
   - Verifies that all 4 commission rewards can be redeemed before claiming.

5. **Adventurers' Guild Daily Reward**:
   - Automatically visits Katheryne at the designated Adventurers' Guild branch to claim bonus rewards.
   - Supports multiple regions (Mondstadt, Liyue, Inazuma, Sumeru, Fontaine, Nod-Krai, Snezhnaya, etc.).
   - Automatically interacts through dialogue to complete reward collection.

## Parameter Settings Guide

### Basic Settings
| Setting | Default | Description / Example |
| --- | --- | --- |
| Friendship Team Name | None | Team to switch to (e.g. "Friendship"). Leave blank to skip switching. |
| Dedicated Navigation Team Name | Blank | Optional. e.g. "Travel Team". Switches to this recognized team during pathing, then switches back before claiming rewards. |
| Disable Teleport to Statue of The Seven for Party Switch | Unchecked | When checked, skips teleporting to a Statue of The Seven to switch parties. |
| Complete Daily Commissions Directly via Encounter Points | Checked | Skips the Serenitea Pot double EXP flow (recommended when all characters have max Companionship). |
| Adventurers' Guild Region | "Mondstadt" | Target city branch (e.g. "Fontaine", "Nod-Krai"). |

### Serenitea Pot Double Companionship Settings
| Setting | Description / Example |
| --- | --- |
| Target Friend Name (Optional) | e.g. "Traveler123", "Paimon" |
| Friend Join Requests (<=7) | Number of friends to try joining (e.g. "5") |
| Remove Character in Slot 1 | Checked |
| Remove Character in Slot 2 | Checked |
| Remove Character in Slot 3 | Checked |
| Remove Character in Slot 4 | Checked |

## Recommended Workflow

### Double Companionship EXP Flow
1. Spend 120 Original Resin beforehand (to generate Encounter Points).
2. The script automatically enters your friend's Serenitea Pot.
3. Configured party members are removed from the team.
4. Opens the Adventurer Handbook to claim Encounter Points.
5. Returns to the overworld.
6. If a Dedicated Navigation Team is configured, switches to it and navigates to the Adventurers' Guild, then switches back to the Friendship team.
7. Claims the daily completion reward from Katheryne.

### Character Removal Strategy
- To maximize double Companionship EXP, keep only 2 characters needing Friendship in the party.
- Check the slot checkboxes corresponding to characters who should leave (Slot 1 is the leftmost character).
- **Note**: You cannot remove all 4 characters (at least 1 must remain).
- Removal occurs automatically upon entering the Serenitea Pot.

### Dedicated Navigation Team Strategy
- **When to Use**: If your Friendship team includes brand-new characters that BetterGI cannot yet identify, auto-pathing might fail.
- **How to Set**: Create an overworld team in-game consisting solely of well-supported older characters (e.g. "Travel Team"). Enter this name in "Dedicated Navigation Team Name".
- **Behavior**: After claiming Encounter Points and returning to the overworld, the script switches to the navigation team, paths to Katheryne, switches back to your Friendship team, and talks to Katheryne.

### Adventurers' Guild Region Selection
- Setting to **"Nod-Krai"** is recommended due to the short, unobstructed walking distance to Katheryne.

## FAQ

**Q: Why didn't the script enter a friend's Serenitea Pot?**  
A: Check:
1. Whether "Complete Daily Commissions Directly via Encounter Points" is checked (disables Teapot mode).
2. Friend name matches exactly (case-sensitive).
3. Friend's Teapot permission is set to "Direct Join".
4. Network connection is stable.
5. Character is not in combat.

**Q: Characters did not leave the party?**  
A: Check:
1. Whether slot checkboxes are correctly configured.
2. Whether the party screen is available and unlocked.

**Q: Why did party switching fail?**  
A: Possible causes:
1. Currently in Co-Op mode.
2. Incorrect party name in settings.
3. UI recognition failure.

**Q: Why were Adventurers' Guild rewards not collected?**  
A: Check:
1. Whether all 4 daily commissions were completed.
2. Whether rewards were already claimed today.
3. Pathing execution status.
4. Active team has 4 characters.
5. BetterGI version compatibility.

**Q: Pathing fails or reports unrecognized character?**  
A: Set up a "Dedicated Navigation Team" consisting of older, fully supported characters.

## Precautions

1. Game resolution must be set to **1920×1080**.
2. Entering friends' Serenitea Pots requires a **stable network connection**.
3. Double Companionship EXP requires claiming points inside a friend's Teapot with at most 2 characters present in your party.
4. Exact name matching is required when specifying target friends.
5. Ensure 120 Original Resin has been consumed so that all 4 Encounter Points can be claimed.
6. The Adventurers' Guild turn-in relies on auto-pathing; ensure the active party has 4 members before interaction.