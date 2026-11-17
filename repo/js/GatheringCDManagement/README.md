# Gathering CD Management

---

### 1. 📌 Overview
1. A tool to automatically manage "Gathering Route Cooldowns (CD)".
2. Sequentially executes different gathering routes (e.g., mining, local specialties) while automatically skipping routes that have not yet respawned.
3. Uses template matching for item pickups: low resource overhead, avoids accidental investigation points, detects full inventory capacity, and links full items to blacklists (excluding full materials from efficiency calculations).

---

### 2. 🚀 Quick Start

<details>
<summary><b>1. Prepare Route Files</b></summary>

- Subscribe to required map pathing routes from the BetterGI script repository. Downloaded routes are placed in `User/AutoPathing`.

</details>

<details>
<summary><b>2. Minimalist Mode</b></summary>

Copy all desired map pathing files into the `pathing/` directory under `User/JsScript/Gathering CD Management` (subfolder depth does not matter; symbolic links via `mklink` are also supported).

- Add this script to a configuration group, right-click and select **Custom Configuration**, check "Only refresh custom configuration", set Path Group Count to `0`, and run the script once.
- Locate **Priority Materials** in settings, then specify the materials and quantities you need to collect each day.
- Configure a suitable team based on route characteristics and enter the team name under **Priority Materials Team Name**.
- Run the script. It will automatically search relevant paths and terminate once quota is met or all available routes are on cooldown.
- Targets reset daily at 04:00 server time. Over time, the script records yield and duration per route, prioritizing higher-efficiency routes first.
- **Forging Ore** encompasses Crystal Chunk, Amethyst Lump, Condessence Crystal, and Rainbowdrop Crystal; specifying `Forging Ore*160` covers daily forging needs.
- Loop Modes:

  | Mode | Behavior |
  | :--- | :--- |
  | No Loop | Iterates through all path groups sequentially; runs each route once without retrying. |
  | Retry Group | Loops within each group until all routes in that group have run twice or are on CD before moving to the next group. |
  | Global Loop | Restarts scan from Group 1 Route 1 after each completed route, prioritizing routes with fewer than 3 runs until all routes hit 3 runs or are on CD. |

  > Routes on cooldown are skipped automatically without altering overall sequence logic.

</details>

<details>
<summary><b>3. Advanced: Path Groups</b></summary>

- When a single team cannot handle all routes, organize paths into separate folders inside `pathing/`. Each top-level folder corresponds to a selectable Path Group.
- Check "Only refresh custom configuration", set Path Group Count to your desired number, and run the script once.
- Reopen Custom Configuration to assign folders and teams to each Path Group.
- Priority collection respects settings assigned to corresponding Path Groups.
- Groups are executed in sequence; when all routes in one group are on cooldown or below threshold efficiency, the script advances to the next group.
- **Timed Stop**: Specify a cutoff time to stop gathering early (useful before the 04:00 reset).
- Separate configuration groups do not share settings or path groups, but share CD records under the same Account Name.
- CD Types:
  - "Once Daily" mode: Gathered between 04:00–16:00 resets at 04:00 next day; gathered at other hours resets after 12 hours.

</details>

<details>
<summary><b>4. Recommended Gathering Teams</b></summary>

Tailor your team to the materials being gathered:

- **Fowl / Raw Meat**: Bring characters like Kirara whose passives avoid startling birds/beasts.
- **Crystalfly / Crab / Frog**: Bring characters like Sayu whose passives avoid startling wildlife.
- **Sakura Bloom / Dracolite**: Bring an Electro character (Catalysts like Lisa or Yae Miko are recommended).
- **Nahida**: Required for routes utilizing Nahida's elemental skill harvesting.
- **Dehya**: High-HP Dehya in the lead walking slot provides damage reduction and prevents accidental deaths along routes.

**Example Setup:**
- Team Name: `Dehya + Yae Miko + Nahida + Jean`
- Path Folder: `Specialties 1`
- Handles: Electro Crystals, Mist Flowers, Sakura Blooms, Dracolite, Nahida-tagged nodes, Dandelion Seeds, and untagged standard nodes.

⚠️ *Note: Pay attention to different material respawn cycles. Do not mix materials with widely differing CDs into the same path group.*

</details>

---

### 3. 📁 Directory Structure
- `main.js`: Main program entry.
- `settings.json`: UI configuration layout.
- `pathing/`: Directory for map pathing files.
- `blacklists/`: Per-account item blacklist JSON files.
- `record/`: Runtime records and cooldown timestamps per account.

---

### 4. ⚙️ Additional Features

1. **Structured Logging**: Outputs execution progress formatted for log analysis tools.
2. **Skip Post-Route Coordinate Verification**: Forces cooldown recording even if routes end imperfectly or stall unexpectedly.
3. **Food Processing**: Periodically processes ingredients (e.g. Flour) during gathering runs.
4. **Auto-Recovery**: Automatically breaks free from Frozen status and revives fallen party members to keep gathering uninterrupted.

---

### 5. 📞 Contact & Community
- **QQ Group**: `1109232869` (Backup: `1022240522`)

---

### 6. 📋 Schedule Execution
<details>
<summary>Click to view details</summary>

#### Feature Description

Gathering CD Management supports executing `schedule` files, running multiple map pathing routes or JS sub-scripts sequentially.

#### File Format

```json
{
  "schedule": [
    { "action": "start", "task": "Task Name", "count": 1 },
    { "action": "wait", "task": "Task Name" }
  ],
  "tasks": [
    {
      "name": "Task Name",
      "type": "autopathing",
      "filePath": "pathing/route.json"
    }
  ]
}
```

#### schedule Array

Defines task sequence:

| Field | Type | Required | Description |
|---|---|---|---|
| `action` | string | Yes | Action type: `start` or `wait` |
| `task` | string | Yes | Task name matching `name` in `tasks` |
| `count` | number | No | Repetition count (for `start`, default: 1) |

- `start`: Starts task. Synchronous by default unless `async: true` is set in the task.
- `wait`: Waits for an async task to finish.

#### tasks Array

Defines available tasks:

| Field | Type | Required | Description |
|---|---|---|---|
| `name` | string | Yes | Unique task identifier |
| `type` | string | Yes | Task type (`autopathing`, `js`, `keymousescript`) |
| `filePath` | string | Yes | Path relative to Gathering CD Management root |
| `settings` | object | No | Arguments passed to sub-script |
| `async` | boolean | No | Runs asynchronously when true (default: false) |

**Supported Task Types:**

| Value | Description | filePath Example |
|---|---|---|
| `autopathing` | Map Pathing | `pathing/Mining/Crystal.json` |
| `js` | Sub-script | `subJs/script_folder/` |
| `keymousescript` | Key/Mouse Script | `assets/scroll_down.json` |

</details>

---

### 7. 📦 Related Tools
- All-in-One Mob Farming
- Wholesale Artifact EXP
- Co-Op Group Artifact EXP
- Gathering CD Management
- Lock 4-Star Instructor
- Only Big Bottles
- Computer Benchmark
- Turbo Food Processing

---

### 8. 📋 Changelog

<details>
<summary>Click to view history</summary>

#### 2026/08/01
1. Fixed loop logic in "Retry Group" mode.
2. Added auto-handling for Frozen status and character revival.
3. Added "Once Daily" CD reset mode.
4. Upgraded loop mode to dropdown menu with "Retry Group" and "Global Loop".
5. SIFT path support for destination coordinate checks.

#### 2026/02/28
1. Refactored code architecture.

#### 2026/02/26
1. Mouse wheel scrolling triggers only when scroll icon is recognized.

#### 2026/02/18
1. Added handling for inventory capacity limits during food processing.

#### 2026/02/17
1. Added notification for priority phase and path group switches.
2. Log optimizations.

</details>