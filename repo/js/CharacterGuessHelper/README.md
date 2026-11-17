# Miliastra Wonderland - Character Guessing Helper

## Instructions

- Start this script while inside Miliastra Wonderland.
- Remember to stop the script after exiting Wonderland.
- Additional features are available in the Custom Settings to toggle as needed.
- Starting from version 3.0, full character voice line data is included.

## Data Maintenance

- Online Spreadsheet: https://docs.qq.com/sheet/DVlF4V1RhRXlQakZk
- Each category of voice lines occupies only a single column, with one voice line per line within each cell.
- When exporting to CSV, use the file name `千星奇域-猜Character辅助-Working表1.csv`.
- After exporting the CSV, execute:

```bash
node csv_to_json.js
```

## Data Structure

The CSV/Excel file uses compact columns, such as `Elemental Skill Voice Lines`, `Elemental Burst Voice Lines`, and `Join Party Voice Lines`. Multiple lines belonging to the same category are placed in the same cell, separated by newlines.

When generating `data.json`, it is automatically aggregated into an array structure:

```json
{
  "Character名": "Amber",
  "信息": {
    "Character名": "Amber",
    "性别": "女"
  },
  "台词": {
    "元素战技": ["靠你咯。", "兔兔伯爵，出击！"]
  },
  "命之座": ["一箭双丘丘!"],
  "天赋": ["百发百中"]
}
```
