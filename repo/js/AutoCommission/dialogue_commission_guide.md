# AutoCommission Standard Dialogue Commission Creation Guide

> Welcome to contribute! Difficulty: ★★★☆☆  
> Thanks to Yunxian, Huan Suwei, Xiaoying, Tatai, and Unknown for collaborative development.

---

## 1. Pre-Creation Checklist
- Check the development tracking sheet for commission completion status.

---

## 2. Commission Details
- **Name**: The full commission quest title as displayed in the Quest menu (J).
- **Location**: Sub-region / area name shown in the top right of the map.

---

## 3. Creating Process Files
Path convention: `AutoCommission\assets\process\{CommissionName}\{CommissionLocation}\process.json`
- Save files using UTF-8 without BOM encoding.
- Keep all sub-process files (such as `pickup_meal.json`) in the same directory for easy relative referencing.

---

## 4. Process File Format Overview

### 4.1 Basic Structure
```json
[
  {
    "type": "<step_type>",
    "data": <value>,
    "note": "Optional console log note",
    "run": "<Optional sub-process filename, branching only>"
  }
]
```

### 4.2 Supported Step Types
| type | Function | data Example | Notes |
|---|---|---|---|
| `Commission Description Check` | Opens Quest menu (J) and checks quest description | `"Acquire the prepared meal"` | Supports `run` to jump to sub-process |
| `Location Check` | Checks if player coordinates are within distance ≤15 | `[-667, 2285]` | Supports `run` to jump to sub-process |
| `Pathing` | Executes map pathing navigation | `"tracking1.json"` | Relative path |
| `KeyMouse Script` | Executes keyboard/mouse action script | `"script1.json"` | Relative path |
| `Dialogue` | Auto-dialogue with priority branch choices | See details below | |
| `Keypress` | Presses a keyboard key | `"F"` or `{"action":"press","key":"E"}` | Supports complex key actions |
| `tp` | Force teleports to coordinates | `[100,200,true]` | Legacy |
| `Wait` | Waits for specified duration | `3000` (ms) | Defaults to 5000 ms |

---

## 5. Best Practices & Testing
1. Test routes end-to-end in clean environments.
2. Ensure dialogue options cover all branches.
3. Validate coordinates against game mini-map.
