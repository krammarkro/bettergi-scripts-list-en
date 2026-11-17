# 🎣 Teyvat Auto Fishing (Full Route + Custom Selection)

A fully automated fishing script based on BetterGI, supporting all trackable fishing spots across Teyvat.  
Provides flexible filtering, route control, automated fishing, and cooldown tracking. Ideal for daily collection, weapon exchange materials, and map-wide fishing.

---

## ✨ Features Overview

The script automatically tracks and completes all fishing spots supported by BetterGI, including navigation, time adjustment, fishing execution, and cooldown logging.  
(If updated fish data causes issues due to an outdated BetterGI version, update to the latest beta via `Settings` -> `Help` -> `Version Update` -> `Check for Beta Updates` in BetterGI).

---

## ⭐ Core Capabilities

- 🎯 **Flexible Filtering**: Customize tasks by region, fish species, and bait type.
- 🎁 **Direct Material Farming**: Direct target farming for exchange rewards (e.g. fish required for "The Catch").
- 🌗 **Automatic Time Adjustment**: Automatically switches between day and night based on target fish schedules.
- 🧭 **Special Spot Support**: Reaches fishing spots that cannot be navigated via normal map tracking.
- 🔁 **Resume from Specific Spot** (requires all fishing spots enabled).
- ⚔️ **Optional Combat Routes** (disabled by default).
- ⏱ **Custom Fishing Timeout**.
- ⏳ **Scheduled Auto-Stop (up to 24 hours)**.
- 💎 **4:00 AM Welkin Moon Claim** (optional).
- 📒 **Fishing Spot Cooldown Tracking** (records host world CD in co-op).
- 🧲 **Auto-Pickup** (optional).

---

## ⚠️ Important Precautions

1. Some spots involve combat; please avoid party characters that grant double Anemo resonance or non-sprint running speed buffs.
2. The pathing character **must use the medium male (teen boy) model**.
3. Fish + Bait Selection Logic:
   - All selected fish are added to the task list.
   - If a bait is chosen whose corresponding fish are not selected, all fish attracted by that bait are automatically added.
4. Mixed routes (Pathing + GCM) may occasionally freeze; you can disable keyboard/mouse (GCM) routes in the JS configuration.
5. Ensure **F2 is not bound to other functions** (used to detect multiplayer mode).
6. Tsurumi Island spots support automatically equipping the "Peculiar Pinion".

---

# 📘 Configuration Guide

## 📂 Basic Settings

<details>
<summary><strong>Filter Fishing Points</strong></summary>

### Farm Specific Material Exchanges
Field: `path_sort_material`
- When selected, other filters are ignored.
- Fast tracking for materials such as "The Catch", "Ako's Sake Vessel", and "Fleuve Cendre Ferryman".

### 🗺 Region Filter
Field: `path_sort_area`
- Multi-select.
- Options: Mondstadt, Liyue, Inazuma, Sumeru, Fontaine, Natlan, Snezhnaya, Nod-Krai, The Chasm: Underground Mines, Enkanomiya, Ancient Sacred Mountain.

### Fish Filter
Field: `path_sort_fish`
- Multi-select.
- Automatically synchronizes with bait choices if conflicts occur.

### Bait Filter
Field: `path_sort_bait`
- Multi-select.
- If corresponding fish are not selected, they will be automatically added.

### Disable Keyboard/Mouse Routes (GCM)
Field: `block_gcm`
- Disabled by default.
- Disables all GCM routes when enabled.

### Enable Combat Routes
Field: `block_fight`
- Disabled by default.

### Enable Tsurumi Island Routes
Field: `block_tsurumi`
- Requires owning the "Peculiar Pinion" gadget.

### Peculiar Pinion Usage Method
Field: `tsurumi_method`
- Method 1: Open Inventory to swap (default).
- Method 2: Quick-swap slot.
</details>

---

## ⚙️ Intermediate Settings

<details>
<summary><strong>Advanced Fishing Features & Built-in Parameters</strong></summary>

### Resume from Specified Spot
Field: `path_continue`
- Available only when all fishing spots are enabled.

### Unhooked Cast Timeout
Field: `time_out_throw`
- Default: 10 seconds.

### Overall Task Timeout
Field: `time_out_whole`
- Default: 300 seconds.

</details>

---

## 🧰 Advanced Settings

<details>
<summary><strong>Special Preferences</strong></summary>

### Notifications
Field: `Enable Notifications`
- Sends notifications on progress updates.

### Auto-Pickup
Field: `Enable Auto-Pickup`

### 4:00 AM Welkin Moon Claim
Field: `Enable 4 AM Welkin Claim`

### Fishing Spot Cooldown Tracking
Field: `Enable Fishing CD Tracking`
- Enabled by default.
- Automatically disabled for non-hosts in co-op.

### Custom CD Tracking Tag
Field: `Custom CD Record Identifier`
- Leave empty to use the account UID by default.
- Entering custom text uses that text as the tracking identifier for your world.

### Forced Shutdown Time
Field: `Hours` + `Minutes`
- Effective only when both values are set.

</details>

---

## 🧪 Developer Settings

<details>
<summary><strong>Debug Mode</strong></summary>

### Select Debug Fishing Spot
Field: `path_select`

### Debug Time
Field: `path_time`
- All Day / Daytime / Nighttime

### Debug Log
Field: `developer_log`
- Currently unavailable.

</details>

---

# 📍 Detailed Fishing Spot Reference

<details>
<summary>Click to expand</summary>

| Region | Spot Name | Type | Fish Species | Bait | Combat Route | GCM |
|---|---|---|---|---|---|---|
| Fontaine | E001-Fontaine-Fishing Point-Erinnyes Forest Foggy Forest Path Southwest | Standard | Medaka, Rippling Heartfeather Bass, Blazing Heartfeather Bass, Maintenance Mek: Water Body Cleaner, Maintenance Mek: Situation Controller, Maintenance Mek: Gold Leader | Fruit Paste Bait, Sour Bait, Flashing Maintenance Mek Bait |  |  |
| Fontaine | E002-Fontaine-Fishing Point-Erinnyes Forest Lumidouce Harbor Northwest | Standard | Streaming Axe Marlin, Rippling Heartfeather Bass, Maintenance Mek: Water Body Cleaner, Maintenance Mek: Gold Leader | Sugardew Bait, Sour Bait, Flashing Maintenance Mek Bait |  |  |
| Fontaine | E003-Fontaine-Fishing Point-Central Laboratory Ruins South | Standard | Medaka, Streaming Axe Marlin, Rippling Heartfeather Bass, Maintenance Mek: Initial Configuration, Maintenance Mek: Water Body Cleaner | Fruit Paste Bait, Sugardew Bait, Sour Bait, Flashing Maintenance Mek Bait |  |  |
| Fontaine | E004-Fontaine-Fishing Point-Marcotte Station Southwest | Standard | Streaming Axe Marlin, Blazing Heartfeather Bass, Maintenance Mek: Initial Configuration, Maintenance Mek: Situation Controller | Sugardew Bait, Sour Bait, Flashing Maintenance Mek Bait |  |  |
| Fontaine | E005-Fontaine-Fishing Point-Court of Fontaine Northeast | GCM | Streaming Axe Marlin, Rippling Heartfeather Bass, Blazing Heartfeather Bass, Maintenance Mek: Water Body Cleaner, Maintenance Mek: Situation Controller | Sugardew Bait, Sour Bait, Flashing Maintenance Mek Bait |  | Yes |
| Fontaine | E006-Fontaine-Fishing Point-Court of Fontaine South | Standard | Medaka, Streaming Axe Marlin, Maintenance Mek: Water Body Cleaner, Maintenance Mek: Situation Controller | Fruit Paste Bait, Sugardew Bait, Flashing Maintenance Mek Bait |  |  |
| Fontaine | E007-Fontaine-Fishing Point-Belleau Region Poisson Southwest | Standard | Medaka, Rippling Heartfeather Bass, Blazing Heartfeather Bass, Maintenance Mek: Water Body Cleaner, Maintenance Mek: Platinum Collection | Fruit Paste Bait, Sour Bait, Flashing Maintenance Mek Bait |  |  |
| Fontaine | E008-Fontaine-Fishing Point-Mont Esus East Slope East | Standard | Streaming Axe Marlin, Blazing Heartfeather Bass, Maintenance Mek: Initial Configuration, Maintenance Mek: Situation Controller | Sugardew Bait, Sour Bait, Flashing Maintenance Mek Bait |  |  |
| Fontaine | E009-Fontaine-Fishing Point-Beryl Region Elynas East | Standard | Streaming Axe Marlin, Rippling Heartfeather Bass, Blazing Heartfeather Bass, Maintenance Mek: Initial Configuration | Sugardew Bait, Sour Bait, Flashing Maintenance Mek Bait |  |  |
| Fontaine | E010-Fontaine-Fishing Point-Beryl Region Elynas Northeast | Standard | Sandstorm Angler, Rippling Heartfeather Bass, Maintenance Mek: Initial Configuration, Maintenance Mek: Water Body Cleaner, Maintenance Mek: Situation Controller | Sugardew Bait, Sour Bait, Flashing Maintenance Mek Bait |  |  |
| Fontaine | E011-Fontaine-Fishing Point-Romaritime Harbor North | Standard | Streaming Axe Marlin, Rippling Heartfeather Bass, Blazing Heartfeather Bass, Maintenance Mek: Water Body Cleaner, Maintenance Mek: Situation Controller | Sugardew Bait, Sour Bait, Flashing Maintenance Mek Bait |  |  |
| Fontaine | E012-Fontaine-Fishing Point-Morte Region Fort Charybdis Ruins South | Standard | Medaka, Rippling Heartfeather Bass, Blazing Heartfeather Bass, Maintenance Mek: Situation Controller, Maintenance Mek: Gold Leader | Fruit Paste Bait, Sour Bait, Flashing Maintenance Mek Bait |  |  |
| Fontaine | E013-Fontaine-Fishing Point-Morte Region Opera Epiclese South | Standard | Streaming Axe Marlin, Blazing Heartfeather Bass, Maintenance Mek: Water Body Cleaner, Maintenance Mek: Situation Controller, Maintenance Mek: Gold Leader | Sugardew Bait, Sour Bait, Flashing Maintenance Mek Bait |  |  |
| Fontaine | E014-Fontaine-Fishing Point-Nostoi Region Petrichor South | Standard | Streaming Axe Marlin, Rippling Heartfeather Bass, Blazing Heartfeather Bass, Maintenance Mek: Initial Configuration, Maintenance Mek: Water Body Cleaner, Maintenance Mek: Situation Controller, Maintenance Mek: Gold Leader | Sugardew Bait, Sour Bait, Flashing Maintenance Mek Bait |  |  |
| Fontaine | E015-Fontaine-Fishing Point-Court of Fontaine Opera Epiclese West | GCM | Streaming Axe Marlin, Rippling Heartfeather Bass, Blazing Heartfeather Bass, Maintenance Mek: Initial Configuration | Sugardew Bait, Sour Bait, Flashing Maintenance Mek Bait |  | Yes |
| Liyue | B001-Liyue-Fishing Point-Cloud Sea Liyue Harbor Southeast | Standard | Sweet-Flower Medaka, Dawncatcher, Crystalfish, Betta, Pufferfish | Fruit Paste Bait, Redrot Bait, Fake Fly Bait |  |  |
| Liyue | B002-Liyue-Fishing Point-Chenyu Vale Tea Hill | Standard | Medaka, Betta, Brown Shirakodai, Rusty Koi, Golden Koi, Jade Heartfeather Bass | Fruit Paste Bait, Redrot Bait, False Worm Bait, Fake Fly Bait, Sour Bait |  |  |
| Liyue | B003-Liyue-Fishing Point-Chenyu Vale Tea Hill East | Standard | Medaka, Dawncatcher, Crystalfish, Betta, Rusty Koi, Jade Heartfeather Bass | Fruit Paste Bait, Redrot Bait, Fake Fly Bait, Sour Bait |  |  |
| Liyue | B004-Liyue-Fishing Point-Chenyu Vale Mt. Xuanlian Southwest | Standard | Sweet-Flower Medaka, Dawncatcher, Akai Maou, Golden Koi, Jade Heartfeather Bass | Fruit Paste Bait, Redrot Bait, Fake Fly Bait, Sour Bait |  |  |
| Liyue | B005-Liyue-Fishing Point-Minlin Tianqiu Valley | Combat | Medaka, Crystalfish, Betta | Fruit Paste Bait, Redrot Bait | Yes |  |
| Liyue | B006-Liyue-Fishing Point-Minlin Mt. Aocang | Standard | Medaka, Sweet-Flower Medaka, Dawncatcher, Crystalfish, Abiding Angelfish | Fruit Paste Bait, False Worm Bait |  |  |
| Liyue | B007-Liyue-Fishing Point-Minlin Mt. Hulao East | Standard | Medaka, Sweet-Flower Medaka, Dawncatcher, Crystalfish, Betta, Brown Shirakodai | Fruit Paste Bait, Redrot Bait, False Worm Bait |  |  |
| Liyue | B008-Liyue-Fishing Point-Qiongji Estuary Guili Plains Northeast | Standard | Sweet-Flower Medaka, Betta, Akai Maou, Golden Koi, Rusty Koi, Brown Shirakodai | Fruit Paste Bait, Redrot Bait, False Worm Bait, Fake Fly Bait |  |  |
| Liyue | B009-Liyue-Fishing Point-Qiongji Estuary Luhua Pool | Standard | Sweet-Flower Medaka, Betta, Akai Maou, Golden Koi, Rusty Koi, Brown Shirakodai | Fruit Paste Bait, Redrot Bait, False Worm Bait, Fake Fly Bait |  |  |
| Liyue | B010-Liyue-Fishing Point-Bishui Plain Mt. Aocang East | Combat | Medaka, Dawncatcher, Crystalfish, Brown Shirakodai | Fruit Paste Bait, False Worm Bait | Yes |  |
| Liyue | B011-Liyue-Fishing Point-Bishui Plain Wuwang Hill South | Combat | Medaka, Sweet-Flower Medaka, Dawncatcher, Brown Shirakodai | Fruit Paste Bait, False Worm Bait | Yes |  |
| Liyue | B012-Liyue-Fishing Point-Bishui Plain Wangshu Inn West | Standard | Sweet-Flower Medaka, Betta, Akai Maou, Golden Koi, Rusty Koi, Brown Shirakodai | Fruit Paste Bait, Redrot Bait, False Worm Bait, Fake Fly Bait |  |  |
| Liyue | B013-Liyue-Fishing Point-Bishui Plain Yaodie Valley East | Standard | Medaka, Betta, Brown Shirakodai | Fruit Paste Bait, Redrot Bait, False Worm Bait |  |  |
| Liyue | B014-Liyue-Fishing Point-Bishui Plain Qingce Village Northeast | Standard | Sweet-Flower Medaka, Dawncatcher, Crystalfish, Betta, Brown Shirakodai, Bitter Pufferfish | Fruit Paste Bait, Redrot Bait, False Worm Bait, Fake Fly Bait |  |  |
| The Chasm: Underground Mines | ZB001-The Chasm-Fishing Point-Underground Waterway West | Standard | Medaka, Betta, Akai Maou, Brown Shirakodai, Bitter Pufferfish | Fruit Paste Bait, Redrot Bait, False Worm Bait, Fake Fly Bait |  |  |
| The Chasm: Underground Mines | ZB002-The Chasm-Fishing Point-Nameless Ruins West | Combat | Sweet-Flower Medaka, Dawncatcher, Crystalfish, Akai Maou, Pufferfish | Fruit Paste Bait, Redrot Bait, Fake Fly Bait | Yes |  |
| Inazuma | C001-Inazuma-Fishing Point-Yashiori Island Nazuchi Beach North | Combat | Medaka, Lunged Stickleback, Purple Shirakodai, Bitter Pufferfish | Fruit Paste Bait, Redrot Bait, False Worm Bait, Fake Fly Bait | Yes |  |
| Inazuma | C002-Inazuma-Fishing Point-Watatsumi Island Suigetsu Pool East | Combat | Medaka, Glaze Medaka, Dawncatcher, Crystalfish, Lunged Stickleback, Purple Shirakodai | Fruit Paste Bait, Redrot Bait, False Worm Bait | Yes |  |
| Inazuma | C003-Inazuma-Fishing Point-Watatsumi Island Sangonomiya Shrine North | Standard | Medaka, Glaze Medaka, Dawncatcher, Crystalfish, Lunged Stickleback, Purple Shirakodai | Fruit Paste Bait, Redrot Bait, False Worm Bait |  |  |
| Inazuma | C004-Inazuma-Fishing Point-Seirai Island Amakumo Peak North | Standard | Medaka, Dawncatcher, Crystalfish, Purple Shirakodai, Pufferfish | Fruit Paste Bait, False Worm Bait, Fake Fly Bait |  |  |
| Inazuma | C005-Inazuma-Fishing Point-Seirai Island Koseki Village Southeast | Standard | Glaze Medaka, Lunged Stickleback, Akai Maou, Golden Koi, Rusty Koi, Purple Shirakodai | Fruit Paste Bait, Redrot Bait, False Worm Bait, Fake Fly Bait |  |  |
| Inazuma | C006-Inazuma-Fishing Point-Kannazuka Amakane Island South | Standard | Glaze Medaka, Lunged Stickleback, Purple Shirakodai | Fruit Paste Bait, Redrot Bait, False Worm Bait |  |  |
| Inazuma | C007-Inazuma-Fishing Point-Narukami Island Ritou West | Standard | Glaze Medaka, Lunged Stickleback, Akai Maou, Pufferfish, Bitter Pufferfish | Fruit Paste Bait, Redrot Bait, Fake Fly Bait |  |  |
| Inazuma | C008-Inazuma-Fishing Point-Tsurumi Island Chirai Shrine West | Standard | Medaka, Glaze Medaka, Dawncatcher, Crystalfish | Fruit Paste Bait |  |  |
| Inazuma | C009-Inazuma-Fishing Point-Tsurumi Island Autake Plains Southwest | Standard | Medaka, Lunged Stickleback, Akai Maou, Purple Shirakodai | Fruit Paste Bait, Redrot Bait, False Worm Bait |  |  |
| Inazuma | C010-Inazuma-Fishing Point-Kannazuka Kujou Encampment Southeast | GCM | Raimei Angelfish | False Worm Bait |  | Yes |
| Enkanomiya | ZC001-Enkanomiya-Fishing Point-The Serpent's Bowels South | Standard | Crystalfish, Lunged Stickleback, Formalo Ray, Divda Ray | Fruit Paste Bait, Redrot Bait, Fake Fly Bait |  |  |
| Enkanomiya | ZC002-Enkanomiya-Fishing Point-The Serpent's Heart North | Combat | Dawncatcher, Akai Maou, Formalo Ray, Divda Ray | Fruit Paste Bait, Redrot Bait, Fake Fly Bait | Yes |  |
| Enkanomiya | ZC003-Enkanomiya-Fishing Point-The Serpent's Heart Northwest | Standard | Dawncatcher, Purple Shirakodai, Formalo Ray, Divda Ray | Fruit Paste Bait, False Worm Bait, Fake Fly Bait |  |  |
| Natlan | F001-Natlan-Fishing Point-Tecoloapan Bay East | Standard | Pseudoshark Unihornfish, Medaka, Floral Rapidfighting Fish, Diving Rapidfighting Fish, Dusk Sunfish, Greenwave Sunfish | Fruit Paste Bait, Spinelgrain Bait |  |  |
| Natlan | F002-Natlan-Fishing Point-Ochkanatlan East | Standard | Medaka, Greenwave Sunfish, Dusk Sunfish, Pseudoshark Unihornfish | Fruit Paste Bait, Spinelgrain Bait |  |  |
| Natlan | F003-Natlan-Fishing Point-Ochkanatlan Northeast | Combat | Greenwave Sunfish, Floral Rapidfighting Fish, Pseudoshark Unihornfish | Spinelgrain Bait | Yes |  |
| Natlan | F004-Natlan-Fishing Point-Ochkanatlan North | Standard | Medaka, Dusk Sunfish, Pseudoshark Unihornfish, Diving Rapidfighting Fish | Fruit Paste Bait, Spinelgrain Bait |  |  |
| Natlan | F005-Natlan-Fishing Point-Ochkanatlan South | Standard | Medaka, Floral Rapidfighting Fish, Diving Rapidfighting Fish, Greenwave Sunfish, Dusk Sunfish | Fruit Paste Bait, Spinelgrain Bait |  |  |
| Natlan | F006-Natlan-Fishing Point-Ochkanatlan West | Standard | Diving Rapidfighting Fish, Floral Rapidfighting Fish, Pseudoshark Unihornfish | Spinelgrain Bait |  |  |
| Natlan | F007-Natlan-Fishing Point-Ochkanatlan Northwest | Standard | Phony Phlogiston Unihornfish, Magma Rapidfighting Fish | Emberglow Bait |  |  |
| Natlan | F008-Natlan-Fishing Point-Toyac Springs | Standard | Magma Rapidfighting Fish, Phony Phlogiston Unihornfish | Emberglow Bait |  |  |
| Natlan | F009-Natlan-Fishing Point-Flower-Feather Clan North | Standard | Dusk Sunfish, Diving Rapidfighting Fish, Pseudoshark Unihornfish | Spinelgrain Bait |  |  |
| Natlan | F010-Natlan-Fishing Point-Flower-Feather Clan West | Standard | Medaka, Floral Rapidfighting Fish, Diving Rapidfighting Fish, Dusk Sunfish, Pseudoshark Unihornfish | Fruit Paste Bait, Spinelgrain Bait |  |  |
| Natlan | F011-Natlan-Fishing Point-Ancestral Temple East | Standard | Magma Rapidfighting Fish, Phony Phlogiston Unihornfish | Emberglow Bait |  |  |
| Natlan | F012-Natlan-Fishing Point-Atocpan West | Standard | Phony Phlogiston Unihornfish, Secret Source Scout Sweeper | Emberglow Bait |  |  |
| Natlan | F013-Natlan-Fishing Point-Atocpan Northwest | Standard | Magma Rapidfighting Fish, Phony Phlogiston Unihornfish, Secret Source Scout Sweeper | Emberglow Bait |  |  |
| Natlan | F014-Natlan-Fishing Point-Atocpan East | Standard | Medaka, Floral Rapidfighting Fish, Greenwave Sunfish, Dusk Sunfish, Pseudoshark Unihornfish | Fruit Paste Bait, Spinelgrain Bait |  |  |
| Natlan | F015-Natlan-Fishing Point-Colorfall Cliffs North | Standard | Medaka, Floral Rapidfighting Fish, Greenwave Sunfish, Pseudoshark Unihornfish | Fruit Paste Bait, Spinelgrain Bait |  |  |
| Natlan | F016-Natlan-Fishing Point-Huhu Hill Southwest | Standard | Floral Rapidfighting Fish, Diving Rapidfighting Fish, Dusk Sunfish, Pseudoshark Unihornfish | Spinelgrain Bait |  |  |
| Natlan | F017-Natlan-Fishing Point-Easybreeze Market Southwest | Standard | Medaka, Diving Rapidfighting Fish, Greenwave Sunfish, Dusk Sunfish | Fruit Paste Bait, Spinelgrain Bait |  |  |
| Ancient Sacred Mountain | ZF001-Ancient Sacred Mountain-Fishing Point-Sea of Shifting Sentience | Standard | Magma Rapidfighting Fish, Secret Source Scout Sweeper | Emberglow Bait |  |  |
| Mondstadt | A001-Mondstadt-Fishing Point-Dragonspine Skyfrost Nail West | Standard | Medaka, Venomspine Fish, Snowstrider, Tea-Colored Shirakodai | Fruit Paste Bait, Redrot Bait, False Worm Bait |  |  |
| Mondstadt | A002-Mondstadt-Fishing Point-Whispering Woods South | Standard | Aizen Medaka, Crystalfish, Venomspine Fish, Rusty Koi, Tea-Colored Shirakodai | Fruit Paste Bait, Redrot Bait, False Worm Bait, Fake Fly Bait |  |  |
| Mondstadt | A003-Mondstadt-Fishing Point-Stormbearer Mountains | Standard | Medaka, Aizen Medaka, Dawncatcher, Crystalfish, Venomspine Fish, Golden Koi, Tea-Colored Shirakodai | Fruit Paste Bait, Redrot Bait, False Worm Bait, Fake Fly Bait |  |  |
| Mondstadt | A004-Mondstadt-Fishing Point-Stormterror's Lair North | Combat | Medaka, Aizen Medaka, Dawncatcher, Crystalfish | Fruit Paste Bait | Yes |  |
| Mondstadt | A005-Mondstadt-Fishing Point-Stormterror's Lair South | Standard | Medaka, Aizen Medaka, Dawncatcher, Tea-Colored Shirakodai | Fruit Paste Bait, False Worm Bait |  |  |
| Mondstadt | A006-Mondstadt-Fishing Point-Dawn Winery Southwest | Combat | Aizen Medaka, Dawncatcher, Venomspine Fish, Akai Maou, Tea-Colored Shirakodai, Pufferfish, Bitter Pufferfish | Fruit Paste Bait, Redrot Bait, False Worm Bait, Fake Fly Bait | Yes |  |
| Mondstadt | A007-Mondstadt-Fishing Point-Springvale North | Standard | Medaka, Aizen Medaka, Venomspine Fish, Akai Maou, Tea-Colored Shirakodai, Pufferfish, Bitter Pufferfish | Fruit Paste Bait, Redrot Bait, False Worm Bait, Fake Fly Bait |  |  |
| Mondstadt | A008-Mondstadt-Fishing Point-Windrise South | Standard | Medaka, Aizen Medaka, Venomspine Fish, Tea-Colored Shirakodai | Fruit Paste Bait, Redrot Bait, False Worm Bait |  |  |
| Mondstadt | A009-Mondstadt-Fishing Point-Millhaven East | Standard | Venomspine Fish, Akai Maou, Golden Koi, Cerulean Doppeldrake | Redrot Bait, Fake Fly Bait |  |  |
| Mondstadt | A010-Mondstadt-Fishing Point-Dornman Port Southwest | Standard | Aizen Medaka, Dawncatcher, Crystalfish, Cerulean Doppeldrake | Fruit Paste Bait, Fake Fly Bait |  |  |
| Mondstadt | A011-Mondstadt-Fishing Point-Dornman Port South | Standard | Dawncatcher, Tea-Colored Shirakodai, Pufferfish, Bitter Pufferfish, Cerulean Doppeldrake | Fruit Paste Bait, False Worm Bait, Fake Fly Bait |  |  |
| Sumeru | D001-Sumeru-Fishing Point-Dar al-Shifa Southwest | Standard | Medaka, Dawncatcher, Akai Maou, True Fruit Angler, Lazurite Axe Marlin | Fruit Paste Bait, Redrot Bait, Sugardew Bait |  |  |
| Sumeru | D002-Sumeru-Fishing Point-Aaru Village | Standard | Medaka, Crystalfish, Sandstorm Angler, Sunset Cloud Angler, Halcyon Jade Axe Marlin | Fruit Paste Bait, Sugardew Bait |  |  |
| Sumeru | D003-Sumeru-Fishing Point-Debris of Panjvahe | Combat | True Fruit Angler, Sandstorm Angler, Sunset Cloud Angler, Lazurite Axe Marlin, Halcyon Jade Axe Marlin | Sugardew Bait | Yes |  |
| Sumeru | D004-Sumeru-Fishing Point-Mawtiyima Forest | Standard | Peach of the Deep Waves, Sunset Cloud Angler, Lazurite Axe Marlin, Halcyon Jade Axe Marlin | Sugardew Bait |  |  |
| Sumeru | D005-Sumeru-Fishing Point-Fane of Ashvattha North | Standard | Medaka, True Fruit Angler, Sandstorm Angler, Sunset Cloud Angler, Lazurite Axe Marlin, Halcyon Jade Axe Marlin | Fruit Paste Bait, Sugardew Bait |  |  |
| Sumeru | D006-Sumeru-Fishing Point-Mount Temur South | Standard | Dawncatcher, True Fruit Angler, Sandstorm Angler, Sunset Cloud Angler, Lazurite Axe Marlin, Halcyon Jade Axe Marlin | Fruit Paste Bait, Sugardew Bait |  |  |
| Sumeru | D007-Sumeru-Fishing Point-Yazadaha Pool | Standard | Akai Maou, True Fruit Angler, Sandstorm Angler, Sunset Cloud Angler, Lazurite Axe Marlin, Halcyon Jade Axe Marlin | Redrot Bait, Sugardew Bait |  |  |
| Sumeru | D008-Sumeru-Fishing Point-Vimara Village North | Standard | Medaka, True Fruit Angler, Sandstorm Angler, Sunset Cloud Angler, Lazurite Axe Marlin, Halcyon Jade Axe Marlin | Fruit Paste Bait, Sugardew Bait |  |  |
| Sumeru | D009-Sumeru-Fishing Point-Sumeru City South | Standard | Dawncatcher, Sandstorm Angler, Sunset Cloud Angler, Lazurite Axe Marlin | Fruit Paste Bait, Sugardew Bait |  |  |
| Sumeru | D010-Sumeru-Fishing Point-Port Ormos North | Standard | Crystalfish, True Fruit Angler, Sandstorm Angler, Sunset Cloud Angler, Lazurite Axe Marlin, Halcyon Jade Axe Marlin | Fruit Paste Bait, Sugardew Bait |  |  |
| Sumeru | D011-Sumeru-Fishing Point-Devantaka Mountain | Standard | Dawncatcher, True Fruit Angler, Sunset Cloud Angler, Halcyon Jade Axe Marlin | Fruit Paste Bait, Sugardew Bait |  |  |
| Nod-Krai | G001-Nod-Krai-Fishing Point-Clink-Clank Krumkake Craftshop North | Standard | Medaka, Azuregaze Crystal-Eye, Nightgaze Crystal-Eye, Common Axehead Fish, Veggie Mauler Shark | Fruit Paste Bait, Berry Bait, Refreshing Lakka Bait |  |  |
| Nod-Krai | G002-Nod-Krai-Fishing Point-Nothing Passage Northwest | Standard | Medaka, Azuregaze Crystal-Eye, Nightgaze Crystal-Eye | Fruit Paste Bait, Refreshing Lakka Bait |  |  |
| Nod-Krai | G003-Nod-Krai-Fishing Point-Blue Amber Lake | Standard | Common Axehead Fish, Frosted Axehead Fish, Blazing Axehead Fish, Veggie Mauler Shark, Neon Mauler Shark | Berry Bait, Refreshing Lakka Bait |  |  |
| Nod-Krai | G004-Nod-Krai-Fishing Point-Nasha Town Southwest | Standard | Medaka, Common Axehead Fish, Frosted Axehead Fish, Nightgaze Crystal-Eye | Fruit Paste Bait, Berry Bait, Refreshing Lakka Bait |  |  |
| Nod-Krai | G005-Nod-Krai-Fishing Point-Bureau of Lumidouce Mechanics North | Standard | Medaka, Azuregaze Crystal-Eye, Veggie Mauler Shark, Neon Mauler Shark | Fruit Paste Bait, Refreshing Lakka Bait |  |  |
| Nod-Krai | G006-Nod-Krai-Fishing Point-Bureau of Lumidouce Mechanics Southeast | Standard | Medaka, Common Axehead Fish, Frosted Axehead Fish, Nightgaze Crystal-Eye | Fruit Paste Bait, Berry Bait, Refreshing Lakka Bait |  |  |
| Nod-Krai | G007-Nod-Krai-Fishing Point-Light-Bathed Platform Southwest | Standard | Veggie Mauler Shark, Neon Mauler Shark, Azuregaze Crystal-Eye, Nightgaze Crystal-Eye | Berry Bait, Refreshing Lakka Bait |  |  |
| Nod-Krai | G008-Nod-Krai-Fishing Point-Frostmoon Workshop Northeast | Standard | Frosted Axehead Fish, Azuregaze Crystal-Eye, Nightgaze Crystal-Eye, Neon Mauler Shark | Berry Bait, Refreshing Lakka Bait |  |  |
| Nod-Krai | G009-Nod-Krai-Fishing Point-Frostmoon Workshop West | Combat | Medaka, Azuregaze Crystal-Eye, Nightgaze Crystal-Eye | Fruit Paste Bait, Refreshing Lakka Bait | Yes |  |
| Nod-Krai | G010-Nod-Krai-Fishing Point-Nightmare Wetland Northeast | Standard | Medaka, Veggie Mauler Shark, Neon Mauler Shark, Azuregaze Crystal-Eye | Fruit Paste Bait, Refreshing Lakka Bait |  |  |
| Nod-Krai | G011-Nod-Krai-Fishing Point-Piramida South | Standard | Medaka, Common Axehead Fish, Frosted Axehead Fish, Veggie Mauler Shark, Neon Mauler Shark | Fruit Paste Bait, Berry Bait, Refreshing Lakka Bait |  |  |
| Nod-Krai | G012-Nod-Krai-Fishing Point-Cliffwatch Camp West | Standard | Common Axehead Fish, Frosted Axehead Fish, Veggie Mauler Shark, Neon Mauler Shark, Azuregaze Crystal-Eye, Nightgaze Crystal-Eye | Berry Bait, Refreshing Lakka Bait |  |  |
| Frostmoon | ZG001-Frostmoon-Fishing Point-Ungien's Circle | Standard | Medaka, Frosted Axehead Fish, Azuregaze Crystal-Eye, Nightgaze Crystal-Eye | Fruit Paste Bait, Berry Bait, Refreshing Lakka Bait |  |  |
| Snezhnaya | H001-Snezhnaya-Fishing Point-Seashard Town | Standard | Medaka, Charcoal Snowfin, Frostpetal Starbloom Fish, Ruby Starbloom Fish | Fruit Paste Bait, Glimmering Bait |  |  |
| Snezhnaya | H002-Snezhnaya-Fishing Point-Seashard Town Southwest | Combat | Medaka, Charcoal Snowfin, Moonlight Snowfin, Frostpetal Starbloom Fish, Ruby Starbloom Fish | Fruit Paste Bait, Glimmering Bait | Yes |  |
| Snezhnaya | H003-Snezhnaya-Fishing Point-Volkodlak Tundra Central | Standard | Charcoal Snowfin, Moonlight Snowfin, Iridescent Starbloom Fish, Ruby Starbloom Fish, Frostpetal Starbloom Fish | Glimmering Bait |  |  |
| Snezhnaya | H004-Snezhnaya-Fishing Point-Hunter's Cabin North | Standard | Medaka, Charcoal Snowfin, Ruby Starbloom Fish, Frostpetal Starbloom Fish, Iridescent Starbloom Fish | Fruit Paste Bait, Glimmering Bait |  |  |
| Snezhnaya | H005-Snezhnaya-Fishing Point-Dewfall Town East | Standard | Frostpetal Starbloom Fish, Ruby Starbloom Fish, Iridescent Starbloom Fish, Charcoal Snowfin, Cream Snowfin, Moonlight Snowfin | Glimmering Bait |  |  |
| Snezhnaya | H006-Snezhnaya-Fishing Point-Dewfall Town Northeast | Standard | Medaka, Frostpetal Starbloom Fish, Ruby Starbloom Fish, Charcoal Snowfin, Moonlight Snowfin | Fruit Paste Bait, Glimmering Bait |  |  |
| Snezhnaya | H007-Snezhnaya-Fishing Point-Chantwave Cave West | Standard | Medaka, Charcoal Snowfin, Moonlight Snowfin, Iridescent Starbloom Fish, Ruby Starbloom Fish | Fruit Paste Bait, Glimmering Bait |  |  |

</details>

---

# 📬 Feedback & Support

- **Recommended Feedback Group**: BetterGI v7 Group (1029539994)
- **Feedback Email**: hijiwos@hotmail.com
