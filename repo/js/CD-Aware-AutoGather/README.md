# Features

- Automatically synchronizes your subscribed map pathing tasks.
- Automatically tracks cooldowns for various materials, with co-op support (identifies whose world gathering takes place in).
- Identifies inventory item quantities and runs routes dynamically until configured target counts are met.
- Convenient material selection interface with batch selection by region and category.
- Allows configuring one or more blackout time intervals where execution is halted.
- Automatically switches to suitable team compositions during gathering.

**If you encounter issues, [click here to submit feedback](https://github.com/babalae/bettergi-scripts-list/issues/new?template=bug_report.yml&script-name=CD-Aware-AutoGather:2.9.0&additional-info=保留此行以便通知Author:%20@Patrick-Ze%0A%0A---%0A)**

# Preparation Before Use

You must have subscribed to map pathing tasks beforehand. It is recommended to navigate to `Map Pathing` in the script repository and click `Subscribe` next to the `Local Specialties`, `Minerals`, and `Food and Alchemy` categories to subscribe to all routes within those groups.

(Future versions no longer require creating symbolic links and no longer conflict with the `Auto-update subscribed scripts` feature.)

# Run Modes

## 1. Scan Folders to Update Selectable Materials List

Scans subscribed map pathing tasks under the three major categories: `Local Specialties`, `Minerals`, and `Food and Alchemy`, and updates available options in the configuration menu.

After running this mode, open `Modify JS Custom Configuration` via right-click to view the newly populated configuration options.

Once scanning finishes, the script automatically sets the next run mode to `Gather Selected Materials`.

## 2. Gather Selected Materials

In this mode, the script executes gathering tasks for your selected items. After each JSON route completes, the script calculates its next respawn time and logs it to the record files in the `record` folder. On the next execution, unrespawned routes are skipped automatically.

During gathering, if all selected materials reach your configured target amounts, or if the current time enters a configured blackout interval, the script stops automatically.

You can select multiple materials simultaneously; the script will gather them in sequence.

The following options can be configured in this mode:

### Basic Configuration

| Option | Description |
|---|---|
| Filter Material Routes by Keyword | Defaults to blacklist mode. Routes whose file paths contain any specified keyword will be ignored during scanning. Other modes are detailed below. |
| Preferred Party Name | Switches to the designated party before starting gathering tasks. Leaves party unchanged if unset. |
| Alternative Party Name | Used when the preferred party lacks necessary gathering elements/mechanics.<br>Ensure the two party names do not contain each other (e.g. avoid naming them `Specialties` and `Specialties Alt`). |
| Blackout Time Intervals | The script will terminate immediately if started during these time periods, and will halt remaining routes if entered during execution. Supports multiple intervals separated by spaces, e.g. `05:20-09:28 21:28-00:20`. |
| Target Quantity | Enter target count; leave blank for unlimited. You can also enter `csv` to load detailed targets per material from a CSV file (detailed below). Special categories like `All-in-One Mob Farming` ignore this setting. |
| Account Name for Records | Leave blank to automatically detect UID and use it as the account identifier for respawn records. You can enter a custom account name (not recommended), but doing so may prevent proper cooldown tracking during co-op between your accounts. Use only if UID detection is unstable on your setup. |

### Material Gathering Configuration

This section is divided into 4 main categories; depending on your subscribed routes, only some may appear.

For user convenience:
- "Region" options are sorted in the order regions were released in the game.
- Sub-category options are sorted alphabetically.

**[Common Gathering Options]**

Features batch selection by category and region, grouping frequently gathered items together as shown below.

`Select by Category` and `Select Local Specialties by Region` allow bulk selection. These can be combined with individual item selections below for flexible target configurations.

For example, checking `Select by Category` -> Minerals + `Select Local Specialties by Region` -> Mondstadt + `Individual Local Specialties` -> Inazuma's Sakura Bloom.

![pic-1](https://ayaka20.ggff.net/CD-Aware-AutoGather/assets/pic-1.png)

**[Individual Local Specialties]**

![pic-2](https://ayaka20.ggff.net/CD-Aware-AutoGather/assets/pic-2.png)

**[Food and Alchemy]**

![pic-3](https://ayaka20.ggff.net/CD-Aware-AutoGather/assets/pic-3.png)

**[Route Version Selection for Items with Multiple Routes]**

If you have subscribed to multiple route versions for a single material, you can select which specific route(s) to run here.

If no specific route is selected, the first route version is executed by default.

![pic-4](https://ayaka20.ggff.net/CD-Aware-AutoGather/assets/pic-4.png)

### Recommended Team Compositions

Gathering tasks may require 4 elements: `Pyro, Hydro, Electro, Anemo`, along with a mining specialist and Nahida. You can configure two parties: `Miner + Nahida + Hydro + Electro` and `Miner + Nahida + Pyro + Anemo` to satisfy all gathering requirements. If you have Linnea, she is highly recommended as the mining slot character.

Once configured, the script evaluates character requirements before each route and automatically switches parties if the active lineup cannot fulfill the requirements.

Note: Party switching cannot occur during multiplayer co-op sessions, so please ensure your party composition is prepared beforehand when gathering in co-op.

# Advanced Usage

### 1. How to avoid manually checking new material routes after subscribing?

Take advantage of `Select by Category`. Simply select all three categories (or whichever ones you need), and any newly subscribed routes in BetterGI will be included automatically.

### 2. How to clear run records (reset material respawn timers)?

Records are stored in the `record` folder inside the script directory, organized in subfolders by UID (or custom account name). Open the folder and delete the `.txt` files corresponding to the materials you want to reset.

### 3. Advanced Keyword Filtering

By default, keywords operate in blacklist mode and routes containing them are omitted. You can prefix keywords with `include:` to switch to whitelist mode (e.g. `include:Without Nahida` will scan only routes containing "Without Nahida").

For advanced filtering, prefix with `regex:` to filter routes using regular expressions.

### 4. Setting Individual Target Quantities via CSV

If your goals are simple (e.g. all Local Specialties to 168 and Minerals to 100), you can add this script multiple times in the scheduler with different target counts.

For fine-grained targets, set the target quantity option to `csv`, then navigate to the account folder under `record/` to find `采集目标.csv` (Gathering Targets).

Open this CSV with Excel, WPS, or any text editor:

| Item | Target Quantity |
|---|---|
| Local Specialties | |
| Minerals | |
| Food and Alchemy | |
| Local Specialties\Liyue | |
| Local Specialties\Inazuma | |
| Minerals\Condessence Crystal | |
| Minerals\Rainbowdrop Crystal | |
| Food and Alchemy\Crystalfly | |
| Food and Alchemy\Pinecone | |
| Local Specialties\Liyue\Noctilucous Jade | |
| Local Specialties\Liyue\Starconch | |
| Local Specialties\Inazuma\Sakura Bloom | |
| Local Specialties\Sumeru\Rukkhashava Mushrooms | |

Leave the quantity blank to inherit targets from higher levels. Fill in specific numbers, save, and re-run the script.

**Quantities inherit hierarchically:**
- If a specific item has no target set, it inherits the target from its parent category.
- If no target is set anywhere up the hierarchy, quantity is unrestricted.
- Setting quantity to `0` disables gathering for that item.

# Acknowledgments

Version 2.0 was completely rewritten with the new API to address previous architectural limitations.

- Heartfelt thanks to [DuckEgg / huiyadanli](https://github.com/huiyadanli) and all BetterGI contributors for making our Teyvat journey so much smoother.
- Thanks to [FishmanTheMurloc](https://github.com/FishmanTheMurloc) for assistance in implementing image-free batch material scanning.
- Thanks to [JamisHoo](https://github.com/JamisHoo) for configuration UI optimizations.
- Thanks to [this-Fish](https://github.com/this-Fish) for coordinate-based record update logic and early respawn checks.
- Thanks to [JJMdzh](https://github.com/JJMdzh) for inventory scanning ideas and supplemental OCR mechanisms.

Special thanks to Kamisato Ayaka, who accompanied me throughout my journey in Teyvat.

![in-a-league-of-her-own](https://ayaka20.ggff.net/img/ayaka.png)
