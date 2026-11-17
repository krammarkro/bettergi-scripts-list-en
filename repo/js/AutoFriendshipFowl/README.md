# Auto Companionship EXP via Fowl ("Animal Friends" Random Event)

## Overview
- Obtains character Companionship EXP, Mora, and Enhancement Ore by completing the "Animal Friends" Random Event.
- Random Event rewards can be claimed up to 10 times daily.
- The script automatically ensures the game is in Single Player Mode.
- The script terminates after completing the event 10 times or if no reward is granted upon completion.
- Typical completion time is approximately 8 minutes in testing.

---

## Instructions

1. **Add Script**
   - Add the "Auto Friendship Fowl" script to your BetterGI Configuration Group. Do not run it standalone outside the scheduler.
2. **Configuration Group Settings**
   - No special settings required.
3. **JS Script Custom Configuration** (Right-click "Auto Friendship Fowl" in the scheduler → `Edit JS Script Custom Configuration`):
   - Enter your Companionship/Friendship team name (uses current team if left empty).
   - (Optional) Toggle whether to refresh Random Events by entering and exiting Miliastra Wonderland (if unchecked, refreshes via logout and relogin).
   - Ensure the selected Companionship team consists of 4 characters.
   - Ensure you have sufficient "Fowl" in your inventory.
