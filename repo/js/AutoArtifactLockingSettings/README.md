# 🔒 Auto Configure Artifact Locking Plans

## ✨ Script Introduction

This script is used to **automatically configure artifact locking plans**.

The locking plans originate from Bilibili creator @酸儒书生's [video guide](https://www.bilibili.com/video/BV13YHQzMEAT). The script automatically recognizes the game UI and configures all settings, saving you from the tedious process of manual setup.

## 🚀 Features

- 🎯 **Automatic Set Recognition** - Automatically detects artifact sets on the current interface using OCR
- ⚙️ **Batch Configuration** - Supports configuring lock plans for multiple artifact sets at once
- 🔄 **Overwrite Existing Plans** - Option to overwrite already existing lock plans
- ⏱️ **Adjustable Delay Factor** - Supports custom delay multipliers to adapt to varying device performance

## 📖 Instructions

### 1️⃣ Prerequisites

- Game resolution must be set to **16:9** (2560x1440 or 1920x1080)
- Game language set to **Simplified Chinese**
- In the Artifacts "Lock Assistance" screen, check options 1, 3, and 4 under "General Lock Plan", as shown in the picture:

  ![global-lock](assets/global-lock.jpg)

### 2️⃣ Configuration Options

Open the script settings in the Scheduler and configure the following options:

| Option | Description |
|:---|:---|
| Overwrite existing plans | When checked, deletes existing plans and reconfigures them |
| Delay factor | Default 1.2; increase to 1.4 or higher if running unstably |
| Artifact sets to configure | Check the sets you wish to configure; supports "Select All" |

### 3️⃣ Running the Script

1. Run this script in the Scheduler
2. Wait for the script to automatically complete all configurations

> Do not move your mouse or press keyboard keys while the script is running, as it will automatically control the game interface.

## 🛠️ Supported Sets

Currently supports artifact sets from versions 1.0 through 7.1 (Heart of the Furnace, Scarlet Proof).

## 💬 Issue Feedback

1. Locate the log file located in the `log` folder of your BetterGI installation directory, named `better-genshin-impact<YYYYMMDD>.log`.
2. Take a screenshot of the error log in the bottom-left corner of the screen.
3. Open an issue at https://github.com/babalae/bettergi-scripts-list/issues, **upload the screenshot and log**, and tag @bling-yshs.

## Changelog

- 1.0.4 (2026-11-17)
  - Updated click coordinates for 1, 2, 3, and 4 minor affixes to adapt to the new interface layout.

- 1.0.3 (2026-10-02)
  - Added `Heart of the Furnace` and `Scarlet Proof` sets.

- 1.0.2 (2026-07-10)
  - Added `Celestial Gift` and `Disenchantment in Deep Shadow` sets, removed `$any.plans[any].index` parameter.

- 1.0.1 (2026-03-10)
  - Cleaned up duplicate entries in `Artifacts锁定方案信息.json`; no functional script changes.

## 🙏 Acknowledgements

- Locking plans courtesy of: [@酸儒书生](https://space.bilibili.com/10411008)

## 👥 Authors

- [bling-yshs](https://github.com/bling-yshs)
- [Bedrockx](https://github.com/Bedrockx)
- [qwecxzpoi](https://github.com/qwecxzpoi)
