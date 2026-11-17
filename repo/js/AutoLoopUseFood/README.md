# 🍱 Auto Buff Food Replenishment Instructions

## ✨ Core Features

- 🎯 **Dual-Mode Intelligent Switching**  
  `Coordinate Positioning` (fast & flexible) + `Name Search` (stable & efficient)
- ⏲️ **Independent Cooldown Management**  
  Set independent consumption intervals for each food item (per-second precision)
- 🔄 **Multi-Queue Parallel Execution**  
  Run multiple food schemes concurrently without interference

---

## 🛠️ Configuration Guide

### 1️⃣ Coordinate Positioning Mode (Recommended)

**Format**: `row,column,interval_seconds(optional)`  
**Example**: `"2,3; 4,5,60"`

| Configuration | Description | Default |
| --- | --- | --- |
| `2,3` | Food at Row 2, Column 3 | 300 s |
| `4,5,60` | Food at Row 4, Column 5 (60-second interval) | - |

> ✅ **Advantage**: Fastest execution speed, highest stability  
> 📌 **Tip**: Open Inventory and count from the top-left corner (Row 1, Column 1 = `1,1`)

---

### 2️⃣ Name Search Mode

**Format**: `Full Food Name,interval_seconds(optional),index(optional)`  
**Example**: `"Sweet Madame,120; Teyvat Fried Egg,60,2"`

| Configuration | Description |
| --- | --- |
| `Sweet Madame,120` | Uses first matching item (120-second interval) |
| `Teyvat Fried Egg,60,2` | Uses second matching item (60-second interval) |

> ⚠️ **Note**: Names must match exactly (including spaces and symbols).  
> 🔍 Search logic: Scans inventory in order from left to right, top to bottom.

---

## ⚠️ Key Limitations

### ❗ Target Confirmation / Pop-up Foods Prohibited

```diff
- HP Recovery / Revive foods (e.g., "Teyvat Fried Egg", "Sweet Madame")
+ Only supports buff foods without character-target confirmation pop-ups (e.g., "Mondstadt Hash Brown", ATK/DEF potions/dishes)
```

> The script automatically cancels modal dialog pop-ups, so targeted healing foods will not take effect.

### ⚡ Parameter Rules

| Parameter | Description | Default | Range |
| --- | --- | --- | --- |
| Interval | Cooldown duration before re-use (seconds) | 300 | ≥ 30 |
| Index | Selection order for items with identical names | 1 | ≥ 1 |
| Delimiters | Item separator: `;` or `；` | - | Compatible with both English & Chinese punctuation |
| | Parameter separator: `,` or `，` | | |

---

## 🚀 Best Practices

1. **Mode Priority**
   ```mermaid
   graph LR
   A["Preferred: Coordinate Mode"] --> B["Fallback: Name Search Mode"]
   ```
2. **Cooldown Settings**
   - Regular buffs: 300 seconds
   - Strong buffs: ≥ 300 seconds
3. **Multi-Queue Tips**
   - Avoid configuring foods in the exact same slot.
   - Keep cooldown intervals consistent for similar food items.
   - Manually organize your inventory before the first run.

> 📅 Last Updated: 2025.08 | ⚙️ Applicable Version: v0.48+
