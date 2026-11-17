# Weekly Boss Automation Guide

## Configuration Group Settings & Precautions
1. Enable pathing movement in settings.
2. Disable auto-pickup during combat.
3. Enable combat configuration.
4. Set combat strategy selection to "Auto select based on active party".
5. Disable auto-detection of combat end.
6. Leave other settings at default.

## JS Configuration Notes
1. Both a revival dish and a recovery/healing dish must be configured to ensure proper revival.
2. Currently, vanilla BetterGI does not support in-combat revivals; detecting a fallen character immediately raises an error and teleports to a Statue of The Seven. The revival feature in this script runs a check before each combat cycle. Therefore, combat scripts should ideally swap each character in only once per cycle to prevent failed checks.
3. Single combat cycle duration refers to the time it takes for your combat script to complete one full rotation. This can be configured to two decimal places (e.g., 13.5 seconds). Do not enter inflated values (like hundreds of seconds), as this disables timing-dependent functions.
4. Weekly boss domain selection: Configure which weekly bosses you wish to challenge and how many times per boss.
