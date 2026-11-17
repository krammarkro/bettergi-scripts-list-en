# Daily Harvest Stats

Tracks only gains (Mora, Salvageable Artifact EXP, Primogems) obtained **during farming script execution**: reads a baseline **before** farming, and reads again **after** farming: Harvest = End − Start. Any manual Mora expenditures or Artifact EXP consumed during artifact enhancement are **naturally excluded**.

```
📊 Daily Harvest Stats [Account: default-profile]
⏱ Tracking since 2026/6/19, recorded 5 farming days · 5 consecutive farming days
── Mora ──
Total: 2,500,000 / Today: 480,000 / Daily Avg: 500,000
── Artifact EXP ──
Total: 120,000 / Today: 30,000 / Daily Avg: 24,000
── Primogems ──
Total: 720 / Today: 40 / Daily Avg: 40
This Week: 3,500,000 (Daily Avg: 500,000) · Today vs Yesterday: +12.5%
```

## I. Key Requirement: Place Twice in Scheduler Group

The same script must be placed **before and after** your farming task group, configured with different "Execution Phase" settings:

```
[Daily Harvest Stats · Before Farming (Record Start)]  ← Records starting Mora/Artifact EXP
   ↓
[Your mob farming / gathering tasks...]
   ↓
[Daily Harvest Stats · After Farming (Settlement)]    ← Harvest = Current − Start, logs and reports
```

## Advanced Usage: Tracking Real Gains from "Manual Play"

Not limited to automated farming—if you want to track rewards earned while **playing manually** (opening chests, completing Daily Commissions, world exploration, manual mob farming, etc.):

1. **Before playing**: Run the script once set to "Before Farming" to record the baseline;
2. **Play freely**;
3. **After logging off**: Run the script set to "After Farming" to calculate settlement.

All Mora and Artifact EXP earned during your session will be accurately recorded and added to your cumulative totals and daily averages.
*(Note: Expenditures or enhancements during this window will offset gains; perform settlement before spending, as detailed in Section IV).*

## II. Calculation Principles

- **Measures only the farming window**: Any manual purchases or artifact leveling outside this window do not affect stats.
- **Negative gains ignored**: Farming only increases inventory values. If End < Start (suspected read error or non-farming expenditure), the segment is skipped to prevent corrupting totals.
- **Totals & Averages**: Total = sum of all farming day gains; Daily Average = Total ÷ Days Farmed.
- **Consecutive Days**: Consecutive service days counting backward from the most recent farming day (resets to 1 if a day is skipped). Weekly/monthly summaries and Day-over-Day / Week-over-Week comparisons are computed automatically.
- **Primogems as a Soft Metric**: Read from the same "Precious Items" inventory tab alongside Mora with zero extra overhead. Provided as a best-effort metric: read errors default to 0 and **never affect** Mora or Artifact EXP calculations. ⚠️ Fixed mob farming routes rarely spawn new chests, so **Primogems ≈ 0 is normal**; this metric is intended primarily for manual exploration sessions.
- **Interruption Resilient**: If farming terminates early without settlement, the next day's "Before Farming" run establishes a fresh baseline; incomplete prior sessions are safely discarded.

## III. Configuration Options

| Option | Description |
|---|---|
| Execution Phase | Before Farming (Record Start) / After Farming (Settlement) — set respectively on the two instances |
| Account Profile | Identifier for multi-account setups; leave blank for default profile |
| Track Mora / Track Artifact EXP | Independent toggle switches (must match across both instances) |
| Clear Account Stats | Set to "Yes" and run once to reset statistics |
| Send Notifications | Whether to send a notification report upon completion |

## IV. Task Placement & Consumption Precautions (Crucial for Accuracy)

This script measures the difference between "Before" and "After" readings. **Any consumption occurring between these two points will reduce recorded gains or trigger error skips**. Keep in mind:

### 1. Place "After Farming (Settlement)" before all consumption tasks

Place Settlement **before** the following tasks to prevent gains from being spent before calculation:

- **Artifact EXP sinks**: Auto **Artifact Enhancement**, applying stored EXP, Sanctifying Essence/Unction—once fed into equipped artifacts, EXP leaves the measurable pool.
- **Mora sinks**: Auto **Purchasing** (shops, resin, artifact EXP), **Alchemy Crafting**, **Talent/Weapon Leveling**, Serenitea Pot Realm Depot purchases, etc.

> Correct sequence: `Before Farming → Farming Tasks → [Daily Harvest Stats · After Farming] → Enhancement/Crafting/Purchase tasks`

### 2. "Auto Salvage" does not affect statistics

Salvaging converts artifacts into Sanctifying Unction or stored EXP. This script tracks both forms (Total = Unsalvaged Artifacts + EXP Potions + Stored EXP). Total value remains unchanged before and after salvaging. **Only actual artifact leveling consumes EXP from the pool**.

### 3. Place "Before Farming" immediately before farming tasks

EXP/Mora generated prior to the start checkpoint will not be counted. To track multiple farming tasks, place "Before Farming" ahead of all of them.

### 4. Avoid manual spending during the measurement window

Do not manually spend Mora or level artifacts between "Before" and "After" runs.

### 5. Locked artifacts are excluded from EXP

The filter checks "Unlocked" artifacts only; locked artifacts are not counted as salvageable EXP.

## V. Other Notes

- Requires **1920×1080 resolution without visual filters**. Mora and Primogems are read from the Precious Items tab; Artifact EXP is read from the Artifact Salvage interface.
- Keep Account Profile and tracking toggles **identical** between the "Before" and "After" instances.
- Running "After Farming" without a preceding "Before Farming" baseline will output "Farming start record not found" and skip.
- **Viewing Reports** (auto-refreshed each run):
  - `local/harvest_report.html`: Open in a web browser for visual summary cards, trend charts (Mora / Artifact EXP / Primogems), and paginated sortable tables with theme switching.
  - `local/harvest_report.txt`: Plain text version viewable in Notepad.
  - Summaries are also output in runtime logs and notifications.
- `local/harvest_stats.json` contains application data (with `.bak` backup); **do not edit manually**.

## VI. Frequently Asked Questions (FAQ)

**Q: First run only shows "Farming start recorded", why no harvest numbers?**  
A: This is normal. "Before Farming" only establishes the starting baseline; harvest numbers appear after running "After Farming (Settlement)".

**Q: Why does the report have no harvest numbers after only running Before Farming?**  
A: The report generated before farming displays historical totals only. Today's harvest is computed during the post-farming settlement.

**Q: Where can I view statistics?**  
A: Open `local/harvest_report.html` in your browser, or `local/harvest_report.txt` in Notepad.

**Q: If I farm multiple times on the same day, are days counted repeatedly?**  
A: No. Multiple runs within the same service day (reset at 04:00 server time) are aggregated into that day's total without inflating the day count.

**Q: How are late-night sessions across midnight handled?**  
A: The daily reset occurs at **04:00**. Crossing midnight before 04:00 counts as the same service day. Crossing 04:00 logs the session under the new service day. Totals and daily averages remain accurate regardless.

**Q: Can I re-run "Before Farming"?**  
A: Yes. The **latest run takes precedence** (overwriting the baseline), without corrupting historical data. Ensure the final "Before" run occurs before farming starts.

**Q: Why was today's harvest negative?**  
A: Net gains are calculated within the window. Negative values are treated as reading errors and skipped. If this occurs frequently, check whether "After Farming" is placed after enhancement or purchase tasks.

**Q: How is Artifact EXP calculated? Does it salvage my artifacts?**  
A: **It only reads data without modifying your items**. Total = Stored EXP + Unsalvaged Artifact conversion (1★ 420, 2★ 840, 3★ 1260, 4★ 2520) + EXP Potions (Sanctifying Unction ×2500, Sanctifying Essence ×10000). The script never clicks the confirm salvage button.

**Q: Can I restore data if I accidentally clicked "Reset/Clear Stats"?**  
A: Yes, if done quickly. The previous dataset is preserved in `local/harvest_stats.bak.json`. Copy and rename it to `harvest_stats.json` to restore. Once the script runs again, the backup will be overwritten.

**Q: How do I configure multiple accounts?**  
A: Enter a unique identifier in "Account Profile" for each account. Statistics will be tracked independently.

**Q: Will updating the script version wipe my stats?**  
A: No. Updates only affect code logic. Existing statistics (Mora, Artifact EXP, Primogems, day counts) are preserved safely.

## Future Plans
Upcoming versions plan to introduce tracking for **Character Materials & Local Specialties Collection**, providing a comprehensive daily gathering report.

## Changelog

### 1.3
- Fixed collective error discarding bug: Previously, an error in one metric (e.g. Artifact EXP) discarded all metrics. Now, metrics are evaluated independently; errors in one metric only skip that specific item, while valid metrics are recorded normally.
- Reports handle missing daily metrics gracefully with "—" placeholders, calculating averages only across valid measured days.

### 1.2
- Fixed daily average calculation for metrics added later (such as Primogems).
- Fixed weekly/monthly summary aggregation by aligning strictly to service days.
- Added time range toggles (7 / 30 / 180 / All days) to trend charts; removed daily detail truncation.
- Added "Today's Primogems" column to detail table, centered numerical data, and fixed row height issues.
- Upgraded long-term totals to persistent all-time counters independent of the detail window.
- Improved OCR reliability with double-read validation and wider bounding boxes for 10M+ values.

### 1.1
- Added **Primogems** tracking (Total / Today / Daily Avg, soft metric read alongside Mora).
- Added **Consecutive Farming Days**, **Weekly / Monthly Summaries**, and **DoD / WoW** comparisons.
- HTML report: added Primogems switch to trend chart and auto-pagination (12 days per page) for detail table.
- Added unit tests for tracking logic.

### 1.0
- Initial release: two-phase net harvest tracking excluding manual spending; negative value filtering; cross-day accumulation; multi-account support; interruption resistance.
