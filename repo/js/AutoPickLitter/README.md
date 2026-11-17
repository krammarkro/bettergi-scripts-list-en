# Teyvat Chores

## 1. Introduction

This script automates collecting specific special items, completing certain achievements, and performing recurring interactions across Teyvat:

- **Mondstadt**: Holy Water [Collection]
- **Liyue**: Offer Incense to Pervases [Ritual]  
- **Inazuma**: Grand Narukami Shrine Fortune Slip [Ritual] [Achievement]
- **Inazuma**: Mysterious Conch Chests [Achievement] [Collection]
- **Fontaine**: Fortress of Meropide Free Meal [Achievement] [Collection]
- **Natlan**: Claim Saurian Egg [Collection]
- **Nordkal**: Lucky Wheel [Ritual]
- **Nordkal**: Today's Special [Collection]
- **Nordkal**: Claim Sugar Sculpture [Ritual] [Collection]
- **Snezhnaya**: Zapolyarny Ice Cream [Ritual] [Collection]

## 2. Environment Prerequisites

Before running this script, ensure the following game conditions are met:

- In-game settings should ideally be at default values.
- Key Archon Quests should be completed.
- Ensure essential Teleport Waypoints are unlocked.
- Game resolution must be set to `1920×1080`.
- World permissions set to `Do Not Allow Join`.
- Do NOT set Vesna as the active/runner character.

## 3. Precautions / Notes

Some features have quest prerequisites. Please verify that you have completed them:

<details>
<summary>Liyue: Offer Incense to Pervases</summary>

- Adventure Rank 40+.
- Complete Xiao's Story Quest: Alatus Chapter: Act I ("Butterfly's Dream").
- Day 2: Accept and complete Liyue World Quest "Hereafter: The Trail of Pervases".
- Day 3: Accept and complete Liyue World Quest "Hereafter: All Is Well".
- Day 4: Accept and complete Liyue World Quest "Hereafter: Return to the Mountains".

</details>

<details>
<summary>Inazuma: Grand Narukami Shrine Fortune Slip</summary>

If any of the following occur, related hidden world quests are not yet completed. Please complete them beforehand to avoid script hangs:

- First time deciphering a fortune slip at the Grand Narukami Shrine.
- Fortune slip dialogue contains "In the middle of a hazy night".
- Miss Gendou is missing from her post at the shrine.

Note: This series of hidden quests takes 4 real-world days to complete. Search for guides on "The Very Special Fortune Slip" or "Where the Dandelions Find Rest".

</details>

<details>
<summary>Inazuma: Mysterious Conch Chests</summary>

- Manually investigate the glowing spots and solve any nearby puzzle chests around Takashi's conch house beforehand.

</details>

<details>
<summary>Natlan: Claim Saurian Egg</summary>

- **Balanced Mode**: Balances egg types based on in-game inventory counts or local script records.
- **Random Mode**: Claims a random egg.
- **Specified Mode**: Claims your selected preferred egg type.

Note: When running this feature, the script checks whether the record file is at default values or changed to decide whether to open the Inventory for OCR egg identification.

</details>

<details>
<summary>Nordkal: Today's Special</summary>

- Accept and complete the World Quest "A Matter of Meals".

</details>

<details>
<summary>Nordkal: Claim Sugar Sculpture</summary>

- Claimed sugar sculptures are consumed by default to prevent filling up bag inventory slots.
- Ensure no characters in the party are fallen.
- Check if the Secret Archive prompt has been triggered (interact while carrying a Secret Archive character).
- For the Moon-Prayer Night sugar sculpture, the Nordkal main storyline must be completed.

Note: Character sugar sculptures require setting the party name containing the corresponding character.

</details>

<details>
<summary>Notification Content</summary>

- Inazuma Fortune Slip fortune text.
- Fortress of Meropide food item name & Fortune Slip content.
- Saurian egg quantities in Inventory.
- Nordkal Lucky Wheel result.

</details>

## 4. Usage Instructions

Follow these steps to configure and run the script:
1. Launch BetterGI.
2. Click **Auto**.
3. Click **Task Scheduler**.
4. Click **New Configuration Group**.
5. Set a name for your configuration group and confirm.
6. Click your newly created configuration group name.
7. Click **Add**.
8. Select **JS Scripts**.
9. Check **AutoPickLitter** and confirm.
10. Right-click **Teyvat Chores (AutoPickLitter)**.
11. Select **Edit JS Custom Configuration**.
12. Toggle the features you wish to run based on your preferences.

## 5. Changelog

### Version 2.2

- Complete code refactor.
- Re-routed and optimized individual paths.
- Added Illuga and Linnea sugar sculpture options.
- Added Snezhnaya ice cream feature.
- Reorganized README documentation.

Note: This is a major version update. Please reconfigure your settings.
