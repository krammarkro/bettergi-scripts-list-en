Shop artifact EXP refreshes weekly on Thursday at 4:00 AM server time. You can customize which merchants to purchase from (all selected by default).

Based on Original Resin value conversions, purchasing from all 9 merchants (45 2-star artifacts in total) is equivalent to trading 30 Resin worth of Mora for 51 Resin worth of Artifact EXP.

Therefore, salvaging artifacts into Mora is generally discouraged if you are short on artifact EXP.

**Resin Value Breakdown** (Benchmark: 1 Resin = 3,000 Mora ≈ 738 Artifact EXP)

- Mora Benchmark: 20 Resin Ley Line Blossom of Wealth = 60,000 Mora (World Level 8+ fixed drop)
- EXP Benchmark: 20 Resin Artifact Domain ≈ 14,760 EXP (statistical expectation, including 5-star artifacts used as EXP fodder)

| Item | Calculation | Resin Value |
|---|---|---|
| Mora Spent | 45 × 2,000 = 90,000 Mora | 30 Resin |
| Artifact EXP Gained | 45 × 840 = 37,800 EXP | ≈ 51 Resin |

**Execution Records & Multi-Account Support**

- Execution records are stored in `record/<AccountName>/records.json`, tracked independently for each merchant point.
- After purchasing 5 artifacts or when items are sold out, that merchant is marked as completed for the current week. Re-running before the Thursday 4:00 AM refresh will automatically skip finished merchants. If interrupted mid-run, re-running will resume from the breakpoint (skipping finished merchants and retrying incomplete or failed ones).
- If all selected merchants are already completed for the week, the script will skip execution directly.

**Account Name Setting**

- The account name distinguishes run records between different game accounts. Defaults to "Default", with records saved in `record/<AccountName>/records.json`.
- Illegal filesystem characters (`\ / : * ? " < > |`) in the name are automatically replaced with underscores.
- If left blank, OCR automatically detects the current game UID as the account name, falling back to the "Default" folder if recognition fails.

**Bypass Run Restrictions**

When checked, ignores existing records and forces a complete run across all selected merchants. Applies only to the current execution and unchecks itself automatically afterward.

## Changelog

### 2.6.5 (2026-09-08)
1. Changed record storage format to `.json` files, optimizing record file structures.
2. Added breakpoint resume support; see `Execution Records & Multi-Account Support`.
3. Added automatic account name detection via UID; see `Account Name Setting`.

### 2.6.4 (2026-09-01)
1. "Bypass Run Restrictions" changed to a single-use toggle that unchecks automatically after execution.
2. Added sold-out check for completion timestamps: when purchased quantity is 0, records completion only if all routes are sold out (already purchased this week); routes with purchase failures or errors are not marked as completed so they can be retried.
3. Optimized artifact quantity recognition: OCR now strips the last 5 characters to parse leading digits.

### 2.6.3 (2026-08-27)
1. Fixed an issue where merchant defaults were not loaded when the settings panel remained unopened, resulting in 0 purchases, and prevented failed runs from erroneously writing completion timestamps.
2. Adjusted manifest so the script name remains consistent across updates, with version features described in the summary.

### 2.6.2 (2026-08-21)
1. Added Snezhnaya merchant locations.

### 2.6.1 (2026-08-14)
1. Renamed routes.
2. Updated log output text.
3. Fixed route execution sequence.

### 2.6 (2026-08-06)
1. Added popup detection for expiring inventory items.
2. Converted merchant selection into multi-select checkboxes.
3. Added OCR recognition for purchased artifact quantities.
