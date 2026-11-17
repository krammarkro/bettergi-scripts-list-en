# Character EXP Calculation Script - User Guide

## 1. Precautions
* Cannot run while in Co-Op mode.
* OCR recognition has a small probability of deviation; simply rerun if a value appears inaccurate.
* The generated calculation report is for reference only; in-game values are authoritative.

## 2. Overview
1. Automatically detects specified characters' current level and current EXP.
2. Calculates total EXP required to reach the target level.
3. Optional: Scans current inventory EXP materials for aggregated calculation.
4. Automatically generates a detailed calculation report saved as a text file.

## 3. Usage & Configuration Guide
1. In the BetterGI Scheduler, click "+ Add → JS Script", locate this script, and add it to your configuration group.
2. Right-click the script entry in the configuration group and select **Modify JS Script Custom Configuration**.
3. Upon completion without errors, a report text file named `exp_result_YYYYMMDD_HHMMSS.txt` is created under the `test/` folder in the script directory.

**Custom Configuration Settings:**

1. **Target Character (Required)**:
   - Format: Single character name or multiple characters separated by commas (supports both English and Chinese names and aliases).
   - Example: `"Keqing, Ganyu, Zhongli"`
2. **Target Level (Required)**:
   - Format: Integer representing desired level.
   - Example: `90` (Range: 2–90).
3. **Calculate with Inventory EXP Books (Optional)**:
   - Scans inventory EXP materials and provides a consolidated balance analysis.

## 4. Directory Structure
* `main.js`: Main script entry.
* `manifest.json`: Script metadata manifest.
* `settings.json`: User configuration schema.
* `test/`: Saved text reports.
* `lib/`: Dependent JavaScript template utilities.
* `assets/`: Recognition template images.

## 5. Sample Generated Report

```text
=== Genshin Impact Character Level Up EXP Record [2026/01/01 16:05:06] ===

=== [Character Data] ===
[Jahoda]
    Current Level: Lv. 1
    Current EXP: 0
    EXP Needed to Reach Lv. 90: 8,362,650

=== [Character EXP Material Data] ===
    Hero's Wit:
    Quantity: 300
    Total EXP: 6,000,000

    Adventurer's Experience:
    Quantity: 561
    Total EXP: 2,805,000

    Wanderer's Advice:
    Quantity: 100
    Total EXP: 100,000

=== Record End ===
Total Characters: 1 | Combined EXP Needed for Lv. 90: 8,362,650
Inventory Material Types: 3 | Total Stored EXP: 8,905,000
EXP Surplus: +542,350 (Exceeds requirement)

Current World Level: 9
Single Blossom of Revelation Reward (20 Original Resin):
    Hero's Wit: 4~5
    Adventurer's Experience: 6~7

================ Calculation Result ================
Inventory EXP materials are sufficient to meet the target level requirement; no further farming needed.
```