# Inventory Scan

Scans items across inventory tabs in Genshin Impact, detects the quantity of each item, writes a text summary report, and maintains historical records. When tracked materials are configured, their quantities are also sent via system notifications.

Items are identified by icon template matching; quantities are read using numerical template matching with OCR fallback. Because sampling coordinates are calibrated precisely for a 1920×1080 display, correct resolution is critical.

## Prerequisites

- Game resolution must be set to **1920×1080**. At other resolutions, coordinate misalignment will corrupt scanning accuracy.

## How to Use

Add this script to a configuration group. Default settings will perform a full scan. Results are saved in the `record/` directory; brief statistics (number of item types identified per tab) are printed to the log and notification.

## Settings

- **Account Name**: Distinguishes records for different game accounts. Results are written to `record/<AccountName>/`. Default: `默认账户` (Default Account).
- **Tracked Materials**: Names of specific materials you want to monitor, separated by commas (supports Chinese/English commas, semicolons, or newlines). Matched items are pushed via notification.
- **Scan Scope**: Six selectable tabs (all enabled by default). Uncheck tabs you do not wish to scan.
- **Discontinued Food**: Checklist of limited/event dishes. Check only dishes you actually possess. Unchecking removes them from recognition templates. (Default: all checked; see FAQ).
- **Debug**: Disabled by default. When enabled, creates a `scan-<timestamp>/` directory under `record/<AccountName>/` containing screenshots and cell-by-cell recognition details. Use only for troubleshooting as it increases disk usage and runtime.

## Scan Scope

| Name | Inventory Tab | Method |
| --- | --- | --- |
| Character Development Items | Character Development Items | Full page cell-by-cell matching |
| Food | Food | Full page cell-by-cell matching |
| Materials | Materials | Full page cell-by-cell matching |
| Forging Ore | Weapons | Fixed target list (Enhancement Ores) |
| Artifact EXP | Artifacts | Fixed target list (Sanctifying Essence, Sanctifying Unction) |
| Wish Resources & Mora | Precious Items | Fixed target list |

The first three tabs scan all items cell-by-cell against template libraries; items in the database with 0 quantity are displayed as `×0`. The last three tabs do not scan entire pages, but search for specific assets: Enhancement Ores on the Weapons tab; Sanctifying Essence/Unction on the Artifacts tab; and Masterless Starglitter, Masterless Stardust, Intertwined Fate, Acquaint Fate, Primogems, and Mora on the Precious Items tab.

## Result Files

Output files are created under `record/<AccountName>/`:

```
record/<AccountName>/
├── Scan Results.txt                Latest scan report (overwritten each run)
├── Scan Results History.txt        Historical records (retains up to 30 runs)
└── scan-<timestamp>/               Generated only when debug is enabled
    ├── pages/                      Page screenshots (e.g. Materials_p000.png)
    └── records.json                Cell recognition details (one JSON per line)
```

`Scan Results.txt` records timestamp, elapsed time, tab stats, item counts (unreadable quantities display as `?`), and an [Issues] section highlighting unrecognized cells or scroll errors.

## FAQ

### An item was not recognized
Check the `[Issues]` section in `Scan Results.txt`: unrecognized cells are listed with their adjacent items. Common causes:
- New items added in a recent game version not yet present in the template library.
- Resolution mismatch (not 1920×1080).
- Quantity reading failed (shown as `?`).
- Discontinued food settings misconfigured.

If you believe there is a script issue, enable `Debug`, run a scan, and send the timestamped debug folder along with the report to the author in BetterGI community groups.

### How to handle Discontinued Food
Check only the event/discontinued dishes you actually own. Unchecking removes them from template evaluation, speeding up scans.

### When to use Debug Mode
Keep it disabled during normal use. Enable it when troubleshooting missing items, incorrect counts, or false unrecognized cells.