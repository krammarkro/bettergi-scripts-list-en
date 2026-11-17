# Character Development All-In-One

> [!WARNING]
> Please note: This script operates by farming items until a specified inventory count is reached. **Do not use/consume the materials mid-way before farming is fully completed!**
> 
> Reiterating: **DO NOT use the materials before the target quantity is completely farmed!**

Once the target item count is reached, execution will be skipped. If issues occur during farming, notifications will be sent, so **enabling JS notifications is strongly recommended**.

Currently, this script only farms **Character Ascension Materials (Boss drops), Talent Books, and Weapon Ascension Materials**. It does not perform character leveling or alchemy crafting (local specialties and enemy drops are not planned). It is recommended to add Auto Domain for Artifacts and Daily Commission reward claiming to your All-in-One Run as a fallback.

## Basic Workflow
After parsing the character development plan, the script checks available resin first. If resin is sufficient, it inspects your current inventory count for the target items. If items are insufficient, it teleports to the corresponding Domain or Boss to farm (factoring in alchemy crafting bonuses; actual items farmed may be slightly fewer). If a Domain is not open today, it will skip it upon detection. When target materials are fully collected, a notification is dispatched and the session data is recorded. To prevent unintended repeat farming, identical values may be treated as input errors; check "Clear Records" in settings to reset.

## How to Use
Open the HoYoLAB Enhancement Calculator, select the character you want to develop, confirm your build goals, and check the **total required materials** (**Note: Total required, NOT remaining materials needed!**). Enter these numbers sequentially. If you don't know the boss's name, click the boss drop icon in the calculator to inspect it.

### Input Format Examples:
- **Talent Books (Green - Blue - Purple)**: If you need 3 green (Teachings), 5 blue (Guide), and 1 purple (Philosophies) of Freedom books, enter `"3-5-1"`.
- **Weapon Materials (Green - Blue - Purple - Gold)**: If you need Mist Veiled materials with 0 green (Lead Elixir), 5 blue (Quenching Elixir), 11 purple (Gold Elixir), and 6 gold (Primo Elixir), enter `"0-5-11-6"`.
- Custom settings provide three common reference tiers.

## Configuration Group Settings & Precautions
1. Enable Map Tracking Movement Configuration.
2. Disable Auto Loot (Auto Pickup).
3. Enable Combat Configuration.
4. Combat Strategy: Choose "Auto select according to party" (test universal strategies on your own if desired).
5. Disable Auto Loot.
6. Leave other options at default. If character investment/DPS is lower, increase the combat timeout.

## Other Configuration Notes
Domain farming calls settings from the standalone task configuration. In Standalone Tasks -> Auto Domain, select your combat party, **but do not select any specific domain**. To farm Artifacts, configure Auto Domain in your All-in-One Run instead.

Due to map template matching limitations, traveling to bosses such as **Super-Heavy Landrover: Mechanized Fortress** and **Immortal Construct** uses keymouse scripts. The keymouse script assumes **Zhongli in Slot 1** with **no team movement speed buffs**. If navigation fails, please record your own keymouse script and replace the corresponding file in `assets/goToBoss`.

## Future Plans
- Remove duplicate value protection; instead, automatically change the material name to "None" once farming completes.
- Support shorthand material inputs (e.g. entering `888` to farm talent books for three skills from level 1 to level 8).
