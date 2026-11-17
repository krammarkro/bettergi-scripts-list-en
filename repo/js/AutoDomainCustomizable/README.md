# Teleport and Auto Domain (Enhanced Edition)

This script is an enhanced version of the built-in **BetterGI** script.
It allows users to customize "Run Count", "Resin Type", and other advanced settings directly in the script configuration, supporting scheduled/cyclical material farming without altering global BetterGI settings.

---

⚠️ If you encounter any issues, **always** read the error message first, adjust settings according to the error instructions, and make sure you have **completely read** this guide. ⚠️

For issues you cannot resolve, please remove sensitive information (such as account names) from the log and submit an issue on GitHub. The modifier of this JS script does not have a QQ account.

It is **strongly recommended** to run in Debug mode before uploading logs.

Issues submitted without log files will be **ignored**.

The default log directory is `BetterGI\log\`.

---

## ✨ Key Features

* **Global Timezone Daily Reset**: Built-in timezone calculation logic automatically adapts to game server reset times.
* **Custom Resin Strategy**: Supports specifying run counts for each resin type, or automatically farming until resin is depleted.
* **Smart Party Switching**: Automatically switches to the specified party before entering the domain.
* **Fully Automated**: Automatic teleporting, domain entry, combat, and reward claiming.
* **Post-Run Processing**: Supports automatically salvaging artifacts upon completion.
* **Combat Strategy Selection**: Supports custom combat strategy files, allowing domain/party-specific combat logic.
* **Auto-Detect Limited-Time All-Open Events**: Automatically checks for in-game "All Domains Open" events via OCR.

---

## 🚀 Usage

⚠️ **Important**: This script's parameters must be configured in the **Scheduler**!

1. Add the script in the Scheduler.
2. **Right-click** the script and select **"Edit JS Script Custom Configuration"**.

### 📌 Required Settings

* **Target Domain to Enter**
  * Select your target domain from the dropdown menu.
  * **Note**: The three categories [Character Talent], [Weapon Ascension], and [Artifacts] are **mutually exclusive** (select only one). Selecting multiple categories will cause the script to terminate with an error.

<br>

* **Resin Strategy Configuration**
  * **Farm until resin is depleted (Highest Priority)**
    * If enabled, the script will **ignore** specific run counts configured below.
    * It uses resin sequentially according to the **Resin Consumption Order** setting until depleted. Resin types not included in the order list **will not** be consumed.

<br>

  * **Specify Run Count per Resin Type**
    * Only takes effect when "Farm until resin is depleted" is **disabled**.
    * The script will farm according to the specified run counts (if all four are 0, no combat will be performed).
    * Supported resin types:
      * **Condensed Resin**
      * **Original Resin (calculates minimum runs based on quantity)**
      * **Transient Resin**
      * **Fragile Resin**

### ⚙️ Optional Settings

* **[Risky] Force Run**
  * **Function**: Ignores date checks and limited-time all-open checks, entering the domain directly.
  * **Use Case**: Use when limited-time all-open auto-detection fails or when an event such as "Overflowing Mastery" is active.
  * **Warning**: If the material is not available today and no event is active, checking this option will result in farming the wrong materials.
  * **Priority**: Highest priority; checking this will bypass "Auto-Detect Limited-Time All-Open".

<br>

* **Auto-Detect Limited-Time All-Open**
  * **Function**: When the date does not match, automatically detects in-game all-open event status via OCR.
  * **Use Case**: Automatically detects events and enters domains when active without manual intervention.
  * **Advantage**: Eliminates the need to manually toggle the Force Run option.
  * **Limitations**: Adds approximately 10-15 seconds of detection time; takes longer and may encounter errors on low-spec/laggy devices.
  * **Note**: OCR recognition is done on a best-effort basis. There is room for optimization (such as multi-text matching or caching event end times). Currently provided for stability testing.

<br>

* **Idle Artifact Farming**
  * **Function**: When target materials (Talent/Weapon) are not available today and no event is active, automatically switches to farming artifacts.
  * **Use Case**: Safely consume resin on artifacts when target materials are not currently available.
  * **Configuration**: Must configure both target materials (Talent/Weapon) and the Artifact domain option.
  * **Priority**: Prioritizes target materials; switches to artifacts only when availability conditions are not met.
  * **Note**: If enabled alongside "Auto-Detect Limited-Time All-Open", OCR failure will trigger fallback to artifact farming.

<br>

* **Auto Switch to Specified Party**
  * Enter the party name (must match the in-game party name exactly, supports regex); leave empty to skip party switching.

<br>

* **Domain Run Count**
  * `0`: Farm until resin is depleted or specified resin counts are met (default).
  * `Number`: Forcibly stops after reaching this number of runs (regardless of remaining resin).

<br>

* **Wait Time After Combat**
  * Buffer delay in seconds after combat rewards/settlement (default: 5 seconds) to prevent premature exit or failed recognition due to PC loading lag.

<br>

* **Auto Salvage Artifacts on Completion**
  * **Function**: When enabled, automatically runs artifact salvage logic before concluding the task.
  * **Salvage Rarity**: Specify salvaging **1-4 Star** artifacts (configured via dropdown).

<br>

* **Enable Debug Mode**
  * Outputs more detailed log info for troubleshooting when errors occur.

<br>

* **Specify Combat Strategy**
  * **Function**: Designates the combat strategy file to use; defaults to auto-selecting strategy based on party.
  * **Strategy File Location**: `BetterGI/User/AutoFight/`
  * **Usage**: Select custom combat strategy in dropdown and enter the filename in the Combat Strategy Name field (extension is optional, leaving it off is recommended). Files are stored under `User/AutoFight` (e.g. `Hu Tao` looks for `User/AutoFight/Hu Tao.txt`; if in a subfolder like `AutoFight/community/Hu Tao.txt`, enter `community/Hu Tao`).
  
  **Tip**: Avoid filenames containing `.txt` in the middle (e.g. `.txtaa.txt`), as filename normalization will turn it into `aa.txt`.

<br>

---

## ⏰ Timezone Settings

The script reads BetterGI's global settings to determine today's material rotation.
Please ensure you go to **BetterGI Settings > Other Settings > Server Timezone Settings** and configure it correctly (e.g., UTC+08:00 for Official CN / Asia server).

---

## ⚠️ Known Issues

None currently.

---

## ⚠️ Modifying the Script

This script was modified with AI assistance. The author has no programming background.
Permission is granted for anyone to maintain, modify, rewrite, share, upload, or overwrite any part of this script without crediting or notifying the modifier (RJFAC).

* **Precautions**
  * Always **backup** before modifying.
  * Before submitting a PR, make sure to check:
      * Update the version parameter in `manifest.json`
      * Add your name and GitHub profile link to `manifest.json` authors
      * Update the Changelog section in `README.md`
      * Add your name and GitHub profile link to the Author section in `README.md`
  * Drop item names are standardized to the highest rarity (4-star for Talent Books / 5-star for Weapon Ascension Materials).

---

## 📜 Changelog

### v1.1.2 - [RJFAC](https://github.com/RJFAC)
* Fixed teleport issue caused by variant character in "Violet Court"

### v1.1.1 - [RJFAC](https://github.com/RJFAC)
* Added support for 7.0 Snezhnaya version
* Added Talent domain "Desolate Sacred Relic" and corresponding options "Philosophies of Charity", "Philosophies of Fortitude", "Philosophies of Glory"
* Added Weapon Ascension domain "Scar of Delusion" and corresponding options "Triumph of the Pale Star Army", "Revelry of the Cellared Spiritual Nectar", "The Frost Emperor's Farewell"
* Added Artifact domain "Inverted Glacial River" and corresponding options "Scarlet Proof / Heart of the Furnace"
* Updated instructions documentation
* Fixed missing Liyue Artifact domain "Ridge Watch" and options "Pale Flame / Tenacity of the Millelith"

### v1.1.0 - [lingyu](https://github.com/aaahai00)
* Added auto-detect limited-time all-open feature via OCR
* Added "Idle Artifact Farming" feature to farm artifacts when target materials are not available and no event is running
* Fixed combat strategy path bug, supporting subfolder strategy files
* Optimized combat strategy name input, handling path separators and `.txt` extensions automatically
* Optimized configuration UI layout

### v1.0.0 - [RJFAC](https://github.com/RJFAC)
* Added BetterGI notifications
* Added Artifact domain "Mountain Breeze's Crown of Thorns"
* Corrected version number to follow SemVer specifications

### v0.10 - [RJFAC](https://github.com/RJFAC)
* Adjusted combat strategy configuration method
* Added instructions in displayed logs
* Improved instructions documentation layout
* Debug mode now displays input arguments

### v0.8 - [Zephyr Bell](https://github.com/zephyr-bell)
* Added support for custom combat strategy files

---

## 👨‍💻 About Authors

* **Original Authors**: [huiyadanli](https://github.com/huiyadanli), iris, Ji
* **Modifiers**: [RJFAC](https://github.com/RJFAC), [Zephyr Bell](https://github.com/zephyr-bell), [lingyu](https://github.com/aaahai00)
* **Assisted By**: AI
