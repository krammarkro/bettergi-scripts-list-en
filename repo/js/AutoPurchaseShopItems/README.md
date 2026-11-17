# Auto Purchase Shop Items - User Guide

## 📝 Feature Overview

This script automatically purchases items from various merchant shops throughout Genshin Impact, supporting three refresh cycles:
- **Daily Refresh Items**: Refreshes daily at 04:00 server time.
- **3-Day Refresh Items**: Refreshes once every 3 days.
- **Weekly Refresh Items**: Refreshes weekly on a designated purchase day.
- **Record System**: Tracks purchase timestamps to avoid duplicate visits, only purchasing refreshed items.
- **Tag System**: Supports batch disabling merchants by tag, or skipping specific goods by item name.
- **Smart Capacity Limit Handling**: When an item purchase fails due to "Inventory capacity reached", the script records the item and skips it across **all remaining merchants in the current run**, avoiding redundant interactions.
- **Item Presets**: Save and manage item loadouts via `preset_tool.html` in the script directory, selectable from the BetterGI dropdown menu (see [Item Presets](#-item-presets)).

## ⚡ Quick Start

### 1. Preparation & Precautions
1. **Game Resolution**: Set game window resolution to 1920×1080.
2. **Game Time**: The script automatically adjusts in-game time (day/night) as required.
3. **Inventory Space**: Ensure sufficient bag space before purchasing.
4. **Mora**: Ensure you have enough Mora in stock.
5. **Record System**: Purchase logs are saved under `record/<AccountName>/`.
6. **Single-Player Mode**: The script must be run in single-player mode.
7. **Refresh Timing**: Server daily reset occurs at 04:00 (GMT+8).
8. **Map Pathing Configuration**: In BetterGI settings, disable **Auto Pick** in "Map Pathing Walk Configuration" to prevent navigation interruptions caused by unintended pickups along the route.

### 2. First-Time Setup
1. Open the script settings in BetterGI.
2. Enter the item names you wish to purchase.
3. Configure the weekly item purchase mode.
4. Configure disabled merchants or tags.
5. Save settings.
6. Run the script from the game's main interface.

## ⚙️ Configuration Guide

1. **Account Name**: Enter your account identifier to separate purchase records per account (if left blank, UID is read automatically).
2. **Items to Purchase**: Enter item names separated by spaces (refer to the support table below).
   - We recommend copying item names directly from the table.
   - Entering a tag name will purchase all goods from merchants carrying that tag.
   - Entering `Artifact EXP` automatically purchases all Artifact EXP goods from all Artifact EXP merchants (Adventurer, Traveling Doctor, and Lucky Dog sets); you can also specify individual items like `Adventurer's Golden Goblet`.
   ```
   Example: Salt Pepper Crab Holy Water Matsutake Chenyu Adeptea Crab Roe Rare Goods
   ```
3. **Item Presets**: Select a saved preset from the dropdown list to purchase items designated in that preset.
   - Presets are managed via `preset_tool.html` in the script directory (see [Item Presets](#-item-presets)).
   - Selecting "Do Not Use Preset" (default) uses the items specified in the text input box above.
4. **Weekly Item Purchase Mode**:
   - `0`: Automatically handled according to the game system cycle.
   - `1-7`: Specify the day of the week to buy (1 = Monday, 7 = Sunday).
   - **Scope**: Covers all weekly refreshing items (Monday refreshes, Thursday refreshes).
   - **Monthly 1st Refresh Items**: Not affected by this setting; purchased whenever refreshed.
5. **Disabled Tags or Items**: Enter tags or specific item names to exclude, separated by spaces:
   ```
   Example: Rip-off Merchant Nod-Krai Karpillia Pop's Teas
   ```
   Excluded merchants or items will be skipped during execution. You can use nation/region tags (e.g. `Mondstadt`, `Liyue`) or category tags.
6. **Skip Time Adjustment Animation**: Skips time adjustment animation instantly if supported.
7. **Force Purchase Ignoring Records**: Ignores existing cooldown records and visits all eligible shops.
8. **Debug Mode**: Sub-options take effect only when Debug Mode is enabled:
   - **Show Detailed Logs**: Enables verbose execution logs.
   - **Specific NPC and Items**: Format: `Blanche Salt Pepper, Sara Flour`. Runs only the specified NPCs and purchases only designated goods (comma-separated). Entering only an NPC name purchases all items from that vendor.

### Purchase Records System

The script records purchase timestamps to avoid redundant trips:
1. **Daily Items**: Refreshes daily at 04:00 server time.
2. **3-Day Items**: Refreshes every 3 days.
3. **Weekly Items**: Refreshes weekly on Mondays (or user-defined day).
   - Monday refresh goods.
   - Thursday refresh goods (Artifact EXP merchants).
4. **Monthly 1st Items**: Refreshes on the 1st of each month at 04:00.

Records are saved to: `record/<AccountName>/records.json`

## 📦 Item Presets

Manage multiple purchase loadouts via `preset_tool.html` in the script directory without manually typing item lists each time.

### Workflow
1. Open `preset_tool.html` in **Edge or Chrome**.
2. Click "Select Script Folder" and select the script directory in BetterGI (`.../User/JsScript/Auto Purchase Items`).
3. Create new presets and list your item combinations (syntax matches the settings text input). Changes save automatically to `record/presets.json`.
4. In BetterGI script settings, select your preset from the "Item Presets" dropdown.

### Notes
- Presets are shared globally across accounts and preserved during script updates.
- Synchronizing presets updates options in BetterGI; you may need to reopen the JS script settings window in BetterGI to see updated choices.
- "Do Not Use Preset" is the reserved default option.

## 📋 Merchant and Item Support Table

| Region | Merchant | Daily Refresh | 3-Day Refresh | Weekly Refresh | Tags |
|--------|----------|---------------|---------------|----------------|------|
| Mondstadt-Windrise | Chloris | - | Snapdragon, Mint, Wolfhook, Valberry, Philanemo Mushroom | - | Roaming |
| Mondstadt-Springvale | Hopkins the Marvelous | Holy Water | - | - | Rare Goods |
| Mondstadt-Springvale | Draff | Raw Meat, Fowl, Bird Egg | - | - | |
| Mondstadt-City | Blanche | Salt, Pepper, Onion, Milk, Tomato, Cabbage, Potato, Wheat | - | - | General Store |
| Mondstadt-City | Sara | - | - | Flour, Cream, Smoked Fowl, Butter, Ham, Sugar, Crab Roe, Jam, Cheese, Bacon, Sausage | |
| Mondstadt-City | Flora | - | Sweet Flower, Windwheel Aster, Cecilia, Small Lamp Grass, Calla Lily | - | |
| Mondstadt-City | Shiliu | - | - | Adventurer's Golden Goblet, Adventurer's Tail Feather, Adventurer's Bandana, Adventurer's Flower, Adventurer's Pocket Watch | Artifact EXP Merchant |
| Mondstadt-Angel's Share | Charles | Wolfhook Juice, Berry & Mint Burst, Apple Cider, Sparkling Berry Juice | - | - | Independent Map, Rare Goods |
| Mondstadt-Millhaven | Bentham | - | - | Flour, Cream, Smoked Fowl, Butter, Ham, Sugar, Crab Roe, Jam, Cheese, Bacon, Sausage | |
| Mondstadt-Dornman Port | Phyllis | - | - | Flour, Cream, Smoked Fowl, Butter, Ham, Sugar, Crab Roe, Jam, Cheese, Bacon, Sausage | |
| Liyue-Harbor | Granny Shan | Xiao Lantern | - | - | |
| Liyue-Harbor | Shitou | Iron Chunk, White Iron Chunk, Noctilucous Jade | - | - | |
| Liyue-Harbor | Dongsheng | Salt, Pepper, Onion, Milk, Tomato, Cabbage, Potato, Wheat, Rice, Shrimp Meat, Tofu, Almond | - | - | General Store |
| Liyue-Harbor | Chef Mao | Fish, Crab | Bamboo Shoot, Lotus Head, Matsutake, Mushroom, Carrot, Radish, Jueyun Chili | Flour, Sugar, Sausage, Ham | |
| Liyue-Harbor | Uncle Sun | Fish, Crab, Shrimp Meat | - | - | |
| Liyue-Harbor | Uncle Gao | Fish | - | - | |
| Liyue-Harbor | Changshun | Potato | Cor Lapis, Electro Crystal | Sugar, Cheese | |
| Liyue-Harbor | Linlang | - | - | Traveling Doctor's Medicine Pot, Traveling Doctor's Owl Feather, Traveling Doctor's Handkerchief, Traveling Doctor's Silver Lotus, Traveling Doctor's Pocket Watch | Artifact EXP Merchant |
| Liyue-Harbor | Zhang Shun | - | - | Lucky Dog's Goblet, Lucky Dog's Eagle Feather, Lucky Dog's Silver Crown, Lucky Dog's Clover, Lucky Dog's Hourglass | Artifact EXP Merchant |
| Liyue-Harbor | Bolai | - | Apple, Sunsettia, Fish, Starconch | - | |
| Liyue-Harbor | Herbalist Gui | - | Qingxin, Violetgrass, Horsetail, Lotus Head, Mist Flower Corolla, Flaming Flower Stamen | - | |
| Liyue-Qiongji Estuary | Boss Zhu | Pop's Teas | - | - | Rare Goods |
| Liyue-Wangshu Inn | Verr Goldet | - | Matsutake, Silk Flower, Violetgrass | Butter, Sausage | |
| Liyue-Stone Gate | Pops Zhou | Pop's Teas | - | - | Rare Goods |
| Liyue-Qingce Village | Ms. Bai | - | Tofu, Almond, Silk Flower | Glaze Lily (Monthly) | |
| Liyue-Qingce Village | Pops Kai | Pop's Teas | - | - | Rare Goods |
| Liyue-Yilong Wharf | Fengtai | Rice, Tofu | Clearwater Jade, Cor Lapis, Noctilucous Jade, Violetgrass, Silk Flower, Jueyun Chili, Chenyu Adeptea | Crab Roe | |
| Liyue-Yilong Wharf | Lianfang | - | Chenyu Adeptea | - | |
| Inazuma-Ritou | Obata | Crab, Fish, Shrimp Meat | Sea Ganoderma | - | |
| Inazuma-Ritou | Qiuyue | Iron Chunk, White Iron Chunk, Electro Crystal | - | - | |
| Inazuma-Ritou | Yamashiro Kenta | Eel Meat | Sango Pearl | Lucky Dog's Goblet, Lucky Dog's Eagle Feather, Lucky Dog's Clover, Lucky Dog's Silver Crown, Lucky Dog's Hourglass | Artifact EXP Merchant |
| Inazuma-Ritou | Karpillia | - | Dandelion Seed | - | |
| Inazuma-Byakko Plain | Wakamurasaki | - | - | Omni-Ubiquity Net | |
| Inazuma-City | Aoi | Salt, Pepper, Onion, Milk, Tomato, Cabbage, Potato, Wheat, Rice, Shrimp Meat, Tofu | Naku Weed | - | General Store |
| Inazuma-City | Shimura Kanbei | Fish, Crab | Seagrass, Lavender Melon, Radish | Sausage, Bacon, Flour, Sugar | |
| Inazuma-City | Tomoki | Dango Milk | - | - | Rare Goods |
| Inazuma-City | Kiminami Anna | Delicious Mushroom Pizza | - | - | Rare Goods |
| Inazuma-Watatsumi Island | Kiyoko | - | - | Milk, Tomato, Potato, Wheat, Tofu | |
| Sumeru-Gandharva Ville | Ashpazi | Raw Meat, Fowl | Bird Egg, Rukkhashava Mushrooms | Spice | |
| Sumeru-City | Jut | - | Harra Fruit, Padisarah | Spice | |
| Sumeru-City | Afshin | - | - | Adventurer's Golden Goblet, Adventurer's Tail Feather, Adventurer's Bandana, Adventurer's Flower, Adventurer's Pocket Watch | Artifact EXP Merchant |
| Sumeru-City | Pam | Fish, Crab, Shrimp Meat | Seagrass | - | |
| Sumeru-City | Hamawi | Salt, Pepper, Onion, Milk, Tomato, Cabbage, Potato, Wheat, Rice, Tofu, Shrimp Meat | Harra Fruit, Zaytun Peach | - | General Store |
| Sumeru-Lambad's Tavern | Lambad | Fish, Crab, Glabrous Beans | Starshroom | Flour, Sausage, Bacon, Spice, Sugar | Independent Map |
| Sumeru-Puspa Café | Enteka | Coffee Beans | - | - | Independent Map |
| Sumeru-Port Ormos | Rama | Salt, Pepper | - | Spice, Sugar, Butter, Cheese | |
| Sumeru-Port Ormos | Butrus | Fish, Crab, Shrimp Meat | - | - | |
| Sumeru-Port Ormos | Qiuwei | - | Crystal Chunk, Cor Lapis, Noctilucous Jade, Silk Flower | - | |
| Sumeru-Port Ormos | Babak | - | Philanemo Mushroom, Dandelion Seed, Violetgrass, Qingxin, Naku Weed, Sango Pearl | - | |
| Sumeru-Vanarana (Dream) | Aramani | - | Sunsettia, Harra Fruit, Zaytun Peach, Rukkhashava Mushrooms, Kalpalata Lotus | - | Vanarana (Dream) |
| Sumeru-Aaru Village | Azalai | Fish, Raw Meat, Glabrous Beans | Starshroom, Ajilenakh Nut, Zaytun Peach | Flour, Spice, Sugar | Rip-off Merchant |
| Fontaine-Court of Fontaine | Boucicaut | Fonta, Salt, Pepper, Onion, Milk, Tomato, Cabbage, Potato, Wheat, Glabrous Beans, Almond, Fermented Juice | Mushroom, Marcotte | - | General Store |
| Fontaine-Court of Fontaine | Arouet | Fonta, Coffee Beans | - | - | |
| Fontaine-Court of Fontaine | Louis | Fonta | - | - | |
| Fontaine-Court of Fontaine | Eugenie | Tomato, Cabbage | Bulle Fruit, Marcotte, Sunsettia, Zaytun Peach, Ajilenakh Nut, Valberry, Rainbow Rose | - | |
| Fontaine-Hotel Debord | Sanguinetti | Fonta | - | Flour, Cream, Butter, Ham, Sugar, Crab Roe, Jam, Cheese, Bacon, Sausage | Independent Map |
| Fontaine-Fleuve Cendre | Crossa | - | - | Lucky Dog's Goblet, Lucky Dog's Eagle Feather, Lucky Dog's Silver Crown, Lucky Dog's Clover, Lucky Dog's Hourglass | Artifact EXP Merchant |
| Fontaine-Poisson | Hinterman | Fish, Crab, Shrimp Meat | Romaritime Flower, Tidalga, Subdetection Unit | - | |
| Fontaine-The Rusty Rudder | Pitot | Milk | - | Bacon, Ham, Sausage, Cheese | Rip-off Merchant |
| Natlan-Stadium of the Sacred Flame | Cintli | Potato | Candlecap Mushroom, Grainfruit, Cacahuatl, Embercore Flower, Withering Purpberry, Saurian Claw Succulent | - | |
| Natlan-Stadium of the Sacred Flame | Ekua | - | - | Lucky Dog's Goblet, Lucky Dog's Eagle Feather, Lucky Dog's Silver Crown, Lucky Dog's Clover, Lucky Dog's Hourglass | Artifact EXP Merchant |
| Natlan-Stadium of the Sacred Flame | Bunama | Salt, Pepper, Wheat, Onion, Milk, Tomato, Cabbage, Potato, Glabrous Beans | Mushroom | - | General Store |
| Natlan-Stadium of the Sacred Flame | Chanca | - | - | Flour, Cream, Butter, Ham, Sugar, Crab Roe, Jam, Cheese, Bacon, Sausage | |
| Natlan-Tequemecan Valley | Imix | - | Iron Chunk, White Iron Chunk, Crystal Chunk, Condessence Crystal, Spinel Fruit | - | |
| Natlan-Easybreeze Resort | Mutolina | - | Brilliant Chrysanthemum, Saurian Claw Succulent, Skysplit Gembloom, Sprayfeather Gill | - | |
| Nod-Krai-Nasha Town | Tsere | Salt, Pepper, Onion, Milk, Tomato, Cabbage, Potato, Wheat, Rye | - | - | General Store |
| Nod-Krai-Nasha Town | Lichea | - | Sweet Flower, Nocturnal Blossom, Frostlamp Flower | - | |
| Nod-Krai-Nasha Town | Katya | - | - | Flour, Cream, Smoked Fowl, Butter, Ham, Sugar, Crab Roe, Jam, Cheese, Bacon, Sausage | |
| Nod-Krai-Nasha Town | Reko | - | - | Lucky Dog's Goblet, Lucky Dog's Eagle Feather, Lucky Dog's Silver Crown, Lucky Dog's Clover, Lucky Dog's Hourglass | Artifact EXP Merchant |
| Nod-Krai-Nasha Town Flagship | Demian | "Piramida's Nightingale", Borderlands, Wild Berry Road | - | - | Rare Goods, Independent Map |
| Nod-Krai-Piramida | Kofice | Milk, Coffee Beans | Glowing Hornshroom, Dracolite | - | Rip-off Merchant |
| Snezhnaya-Snezhnaya Fortress | Grigory | Honey, Salt, Pepper, Onion, Milk, Tomato, Cabbage, Potato, Wheat | - | - | General Store |
| Snezhnaya-Snezhnaya Fortress | Kirillov | Kvass, Spiced Honey Drink, Winter Iced Brew | - | - | Rare Goods |
| Snezhnaya-Snezhnaya Fortress | Yaroslav | - | - | Lucky Dog's Goblet, Lucky Dog's Eagle Feather, Lucky Dog's Silver Crown, Lucky Dog's Clover, Lucky Dog's Hourglass | Artifact EXP Merchant |
| Snezhnaya-Old Courtyard Restaurant | Buturlina | - | - | Flour, Cream, Smoked Fowl, Butter, Ham, Sugar, Crab Roe, Jam, Cheese, Bacon, Sausage | Independent Map |
| Snezhnaya-Dawn Station | Zheleznov | Honey, Salt, Pepper, Onion, Milk, Tomato, Cabbage, Potato, Wheat | - | - | |
| Snezhnaya-New Kitezh | Sabesha | - | - | Flour, Cream, Smoked Fowl, Butter, Ham, Sugar, Crab Roe, Jam, Cheese, Bacon, Sausage, Smetana, Rye Flour | |
| Snezhnaya-New Kitezh | Flaisda | - | Red Beet, Glaciafruit, Snowball Flower, Rimecurrant, Cape Gooseberry, Fairy Mugwort, Crystal Pleated Mushroom | - | |
| Snezhnaya-New Kitezh | Plazena | Rye, Honey | - | - | Rip-off Merchant |

### Recognized Tags
- **Nations**: `Mondstadt`, `Liyue`, `Inazuma`, `Sumeru`, `Fontaine`, `Natlan`, `Nod-Krai`, `Snezhnaya`.
- **Special Tags**:
  - `Roaming`: Vendor moves along a route; purchase may occasionally miss.
  - `Rare Goods`: Unique or non-standard items (e.g. Holy Water, Pop's Teas).
  - `Independent Map`: Locations requiring loading into separate interiors/instances.
  - `Rip-off Merchant`: Sells goods at high markup without reputation discounts.
  - `Artifact EXP Merchant`: Vendors selling 2-star artifacts refreshing on Thursdays.
  - `General Store`: Daily ingredient general stores.

## 🔧 Adding New Goods & Merchants

### Adding New Goods
1. Capture an item icon screenshot (recommended: 90×90 pixels).
2. Save as PNG under `assets/images/`.
3. Add item entry under corresponding vendor in `assets/npcs.json`:
   ```json
   "_1d_foods": ["New Item"]
   ```

### Adding New Merchants
1. Record a path file to the merchant, saved as `assets/path/<Region>-<Location>-<Vendor>.json`.
2. Add merchant configuration entry in `assets/npcs.json`.

## ❓ FAQ

### Q: Why does the script not purchase anything?
A: Check:
1. Whether target goods are configured in settings.
2. Names match the table exactly.
3. Game resolution is 1920×1080.
4. Game is in single-player mode.
5. Items have not already been purchased (check cooldown records).

### Q: How can I reset purchase records?
A: You can:
1. Enable "Force Purchase Ignoring Records".
2. Delete `record/<AccountName>/records.json`.
3. Wait for the natural in-game reset.

## 📅 Changelog
<details>

### v3.7.2
- Added 9 new item materials.
- Added 3 Snezhnaya routes: Sabesha, Flaisda, Plazena.
- Adjusted route feature matching.

### v3.7.1
- Added custom recognition thresholds for items prone to false matches.
- Adjusted Fengtai pathing.
- Fixed wheat purchase issue.

### v3.7.0
- Added item presets managed via `preset_tool.html`.
- Route and log optimizations.

### v3.6.5
- Auto-disable "Force Purchase" after one run.
- Added retry for failed store screenshot matching.
- Adjusted Afshin and Linlang paths.

### v3.6.0
- Automatic stripping of corner brackets `「」` in item names for seamless matching.

### v3.3.4
- Added intelligent inventory capacity handling (blacklists full items for remaining merchants in the active run).

</details>

## 🤝 Contributing

Contributions for new merchants, items, paths, and tags are welcome!

---
> *Disclaimer: This script is intended solely for educational and research purposes. Please abide by the game's Terms of Service.*