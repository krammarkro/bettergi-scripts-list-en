# BetterGI Fully Automated Ley Line Outcrop Script User Manual

**Supports BetterGI 0.63.2 and above only!**  
**Supports Bitblt screenshot mode only!**  
**Supports V4 OCR model only!**  

The script is actively maintained and updated. If you encounter bugs not mentioned in Known Issues, please provide feedback to us, thank you very much!

## Table of Contents
- [Configuration](#configuration)
  - [Configure Map Tracking and Combat Strategies](#configure-map-tracking-and-combat-strategies)
  - [Statue of The Seven](#statue-of-the-seven)
  - [Enable HTTP Permissions](#enable-http-permissions)
- [Key Features](#key-features)
- [FAQ](#faq)
  - [Exits with an error immediately upon launch](#exits-with-an-error-immediately-upon-launch)
  - [Cannot find Ley Line blossom / Found blossom, strategy not found](#cannot-find-ley-line-blossom--found-blossom-strategy-not-found)
  - [Walks next to Ley Line blossom but doesn't activate it](#walks-next-to-ley-line-blossom-but-doesnt-activate-it)
  - [Skipped a point mid-route](#skipped-a-point-mid-route)
  - [All custom map pins disappeared after running](#all-custom-map-pins-disappeared-after-running)
- [Changelog](#changelog)
- [Routes](#routes)
  - [Mondstadt](#mondstadt)
  - [Liyue](#liyue)
  - [Inazuma](#inazuma)
  - [Sumeru](#sumeru)
  - [Fontaine](#fontaine)
  - [Natlan](#natlan)
  - [Nod-Krai](#nod-krai)
- [Special Thanks](#special-thanks)

## Configuration
Before running, you must configure the script and combat strategies.  
In the Scheduler, create a new Configuration Group and add the script to it. This script can only be used inside a Configuration Group.  
![](assets/image/image1.png)  
![](assets/image/image2.png)  
![](assets/image/image3.png)  
![](assets/image/image4.png)  
Right-click the script and select "Edit JS Script Custom Configuration" to configure the script according to your needs.  
![](assets/image/image5.png)  

### Configure Map Tracking and Combat Strategies
Click Configuration Group Settings, enable combat strategy configuration, **disable Auto Combat End Detection**, and configure the rest according to your team setup.  
> The script does not check if combat has ended by pressing L. Please make sure to turn off **Auto Combat End Detection**; failing to turn it off may cause premature combat termination!  
> For the same reason, auto-looting cannot be performed after combat; whether configured or not will not affect this.  
> Combat timeout MUST be greater than or equal to the time in the script configuration; if it is too short, the character will stand frozen!  
> The script forcibly enables auto-pickup; whether toggled on or off will not affect this.  

![](assets/image/image6.png)  

### Statue of The Seven
In BetterGI Settings, **disable Nearest Statue of The Seven**, and specify a specific Statue of The Seven (Avidya Forest in Sumeru is recommended if you have no special preference).  
If you have All-in-One Run mode enabled, this will be skipped to save time.  
> Do NOT enable **Move after teleporting to Statue of The Seven to heal**; this feature currently has many bugs!  

![](assets/image/image7.png)  

### Enable HTTP Permissions
The script requires HTTP permissions to check for updates.  
In the Configuration Group, right-click the script, select Edit General Configuration, and change JS HTTP Permission from **Disabled** to **Enabled**.  
![](assets/image/image9.png)  

## Key Features
- **Fully Automated Execution**: After configuration, simply click Run to clear all blossoms without manual intervention.
- **Auto Search Ley Line Blossoms**: Locates Ley Line blossom positions via the world map and executes subsequent routes.
- **Auto Claim Blossom Rewards (Condensed Resin prioritized)**: Prioritizes Condensed Resin when claiming rewards; when double reward events (Ley Line Overflow or Stellar Reunion) are active, double rewards are prioritized.
- **Double Drop Detection Mode**: When enabled, only farms Ley Lines when double drops are detected and exits automatically afterward—ideal for players only wanting event bonuses.
- **Material Pickup**: Automatically tracks and picks up enemy drops after claiming rewards. Paired with 20-resin mode, this provides efficient monster drop farming (triggers brief combat).
- **20-Resin Mode (Slow Monster Material Farming)**: Consumes only 20 resin per run, trading time efficiency for more mob drop opportunities. Works even better with Material Pickup.
- **Resin Depletion Mode**: Calculates required runs based on configured resin, and checks again upon completion; continues running if remaining unconsumed resin is detected (up to 3 rechecks).
- **Auto Stop on Insufficient Resin**: If resin runs out when claiming rewards, the script stops immediately. Configurable whether to consume Transient / Fragile Resin.
- **Claim Rewards with Companionship EXP Party**: Switches to your Friendship / Companionship party before claiming rewards to earn Companionship EXP.

## FAQ
### Exits with an error immediately upon launch
Check error messages and troubleshoot accordingly.

### Cannot find Ley Line blossom / Found blossom, strategy not found
The script has not adapted this location yet, please wait for script updates.  
If already supported, please submit full game window screenshot feedback.  
Note: To facilitate screenshot feedback, the map will not be closed when this error occurs, nor will custom pins be re-enabled!

### Walks next to Ley Line blossom but doesn't activate it
- Use Bitblt capture mode; the script only supports this.
- Switch OCR engine to V4; other engines are not supported.

### Skipped a point mid-route
When a Ley Line blossom is cleared, if another type of Ley Line blossom already exists at the next point, the next blossom will skip that point and spawn at the following location.  
The script will skip this occupied spot.  
![](assets/image/image8.png)  
For example here, a Mora blossom spawns on the spot of the next EXP blossom.

### All custom map pins disappeared after running
Open the world map, click Settings in the bottom-left corner, and turn on Custom Pins.  
This issue happens if the script terminates abnormally.

## Changelog
### 5.1
- Added double drop detection mode (only runs during double output events)
- Added material pickup feature (automatically picks up drops after claiming rewards)
- Added 20-resin mode (slow mob farming paired with material pickup)
- Fixed Condensed Resin recognition failure
- Fixed bug where script failed to terminate when OCR calculated runs > manual run count setting under resin depletion mode

### 5.0
- Added Snezhnaya routes
- Raised minimum BetterGI version requirement to 0.63.2

### 4.6
- Added Mondstadt routes for Moon v5 update

### 4.5
- Added Nod-Krai routes for Moon v4 update

### 4.4
- Added resin depletion mode
- Added option to take smaller value of run counts under resin depletion mode
- Added update notifications
- Added All-in-One Run mode
- Raised minimum BetterGI version requirement to 0.52.0

### 4.3
- Adapted to new reward claiming interface
- Fixed Nod-Krai recognition error and bug where searching via Adventurer Handbook always selected Nod-Krai
- Fixed bug getting stuck on reward claiming interface preventing other configurations
- Optimized Adventurer Handbook Ley Line search logic
- Added configuration option for whether to use Transient Resin

### 4.2
- Added Nod-Krai region

### 4.1
- Added search for Ley Line blossoms via Adventurer Handbook
- Fixed several error reports

### 4.0
- Adapted to Genshin Impact 5.7 update
- Fixed bug enabling custom map pins

### 3.5
- Reduced redundant log output
- Updated several error messages

### 3.4
- Refactored code structure
- Fixed several prompt errors

### 3.3
- Added combat failure route retry support
- Optimized navigation to Ley Line blossoms

### 3.2
- Added notification options

### 3.1
- Added several Liyue and Sumeru routes
- Adjusted Ley Line search and reward claiming logic

### 3.0
- Added routes: Sal Terrae, Yaoguang Shoal, Yaodie Valley, Tatarasuna, Watatsumi Island, Sulfurous Veins, Tilted Branch Cliff, Toyac Springs, Yashiori Island, Caishi Peak, Flower-Feather Clan, Narukami Island, Seirai Island
- Inazuma and Natlan routes are now fully completed
- Optimized combat logic by checking challenge outcome
- Full Ley Line blossom recognition
- Removed Force Run mode
- Optimized Ley Line search logic
- Optimized blossom activation and reward claiming logic
- Added priority for double rewards (Ley Line Overflow and Stellar Reunion)

### 2.1
- Refactored blossom localization to fetch in-game coordinates directly, reducing blossom search failures
- Added option to switch to Friendship party before claiming rewards (requires configuration)

### 2.0
- Added Fontaine: New Fontaine Research Institute, Lumidouce Harbor (completing all Fontaine routes)
- Fixed bug misidentifying resin as depleted when Condensed Resin was present
- Fixed infinite retry loop

### 1.0
- Initial script release

## Routes
Checked items indicate completed routes.

### Mondstadt
- [x] 1. Windrise

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Hilichurl x3<br>Wave 2: Hilichurl x1, Electro Hilichurl Shooter x2, Hydro Abyss Mage x1
2 | Wave 1: Large Electro Slime x1, Mutant Electro Slime x1, Electro Hilichurl Shooter x1<br>Wave 2: Large Electro Slime x1, Mutant Electro Slime x1, Hydro Samachurl x1, Cryo Hilichurl Shooter x2
3 | Wave 1: Treasure Hoarders: Scout x2, Treasure Hoarders: Gravedigger x1, Treasure Hoarders: Electro Potioneer x1<br>Wave 2: Treasure Hoarders: Marksman x1, Treasure Hoarders: Handyman x1, Treasure Hoarders: Electro Potioneer x1, Treasure Hoarders: Crusher x1
4 | Wave 1: Wooden Shield Hilichurl Guard x3, Hilichurl Grenadier x1, Pyro Slime x2<br>Wave 2: Hilichurl Berserker x4
5 | Wave 1: Large Hydro Slime x2, Cryo Whopperflower x1<br>Wave 2: Electro Slime x3, Cryo Whopperflower x1

- [x] 2. Springvale

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Large Pyro Slime x1, Electro Slime x2<br>Wave 2: Pyro Whopperflower x1, Electro Slime x3
2 | Wave 1: Large Pyro Slime x1, Pyro Slime x4<br>Wave 2: Pyro Whopperflower x2
3 | Wave 1: Pyro Hilichurl Shooter x2, Anemo Samachurl x1, Large Pyro Slime x1<br>Wave 2: Hilichurl Grenadier x2, Anemo Samachurl x1, Large Pyro Slime x1
4-1 | Wave 1: Pyro Slime x2, Hilichurl Grenadier x2<br>Wave 2: Electro Hilichurl Shooter x3, Pyro Abyss Mage x1
4-2/5-1 | Wave 1: Eye of the Storm x1

- [x] 3. Wolvendom (Fewer feature points, chance of failure)

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Treasure Hoarders: Scout x3<br>Wave 2: Treasure Hoarders: Handyman x2, Treasure Hoarders: Marksman x2
2 | Wave 1: Ruin Guard x1
3 | Wave 1: Pyro Hilichurl Shooter x2, Wooden Shield Hilichurl Guard x2<br>Wave 2: Blazing Axe Mitachurl x1, Anemo Samachurl x1, Hilichurl Grenadier x3
4 | Wave 1: Wooden Shield Hilichurl Guard x2, Electro Hilichurl Shooter x2, Hilichurl Grenadier x2<br>Wave 2: Pyro Abyss Mage x2

- [x] 4. Stormterror's Lair

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Treasure Hoarders: Scout x2, Treasure Hoarders: Handyman x1, Treasure Hoarders: Marksman x1<br>Wave 2: Treasure Hoarders: Scout x2, Treasure Hoarders: Crusher x1, Treasure Hoarders: Pyro Potioneer x1, Treasure Hoarders: Electro Potioneer x1
2 | Wave 1: Ruin Hunter x1
3 | Wave 1: Ruin Guard x1
4 | Wave 1: Fatui Skirmisher - Electrohammer Vanguard x1, Fatui Skirmisher - Anemoboxer Vanguard x1<br>Wave 2: Fatui Skirmisher - Pyroslinger Bracer x2, Fatui Skirmisher - Hydrogunner Legionnaire x1

- [x] 5. Temple of the Thousand Winds

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Wooden Shield Hilichurl Guard x2, Electro Hilichurl Shooter x1, Cryo Hilichurl Shooter x1<br>Wave 2: Electro Hilichurl Shooter x1, Cryo Hilichurl Shooter x1, Hydro Samachurl x1, Wooden Shield Hilichurl Guard x1, Wooden Shieldwall Mitachurl x1
2 | Wave 1: Wooden Shield Hilichurl Guard x2, Hilichurl Berserker x2<br>Wave 2: Hilichurl Berserker x3, Dendro Samachurl x1
3 | Wave 1: Treasure Hoarders: Scout x4, Treasure Hoarders: Marksman x1<br>Wave 2: Treasure Hoarders: Pyro Potioneer x2, Treasure Hoarders: Pugilist x1, Treasure Hoarders: Crusher x1
4 | Wave 1: Electro Slime x2, Hilichurl Berserker x2, Wooden Shield Hilichurl Guard x1<br>Wave 2: Electro Slime x2, Hilichurl Grenadier x2, Blazing Axe Mitachurl x1
5 | Wave 1: Wooden Shield Hilichurl Guard x2, Hilichurl Grenadier x2<br>Wave 2: Hilichurl Grenadier x2, Anemo Samachurl x1, Dendro Samachurl x1

- [x] 6. Stormbearer Mountains

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Large Cryo Slime x2, Large Hydro Slime x2<br>Wave 2: Cryo Hilichurl Shooter x2, Hydro Abyss Mage x1
2 | Wave 1: Hilichurl Grenadier x2, Anemo Samachurl x2<br>Wave 2: Electro Hilichurl Shooter x2, Hilichurl Grenadier x1, Blazing Axe Mitachurl x1
3 | Wave 1: Pyro Whopperflower x2<br>Wave 2: Electro Hilichurl Shooter x3, Pyro Abyss Mage x1
4 | Wave 1: Hilichurl Berserker x3<br>Wave 2: Wooden Shieldwall Mitachurl x2, Hydro Samachurl x2

- [x] 7. Dadaupa Gorge

**Total Ley Line Blossoms: 6**

Order | Enemies
--- | ---
1 | Wave 1: Wooden Shield Hilichurl Guard x2, Hilichurl Shooter x2<br>Wave 2: Hydro Abyss Mage x1, Cryo Hilichurl Shooter x2
2 | Wave 1: Hilichurl Fighter x3, Hilichurl Grenadier x1<br>Wave 2: Hilichurl Berserker x3, Blazing Axe Mitachurl x1
3 | Wave 1: Hilichurl Fighter x2, Wooden Shield Hilichurl Guard x2, Pyro Hilichurl Shooter x1<br>Wave 2: Blazing Axe Mitachurl x2
4 | Wave 1: Electro Hilichurl Shooter x2, Blazing Axe Mitachurl x1<br>Wave 2: Pyro Hilichurl Shooter x3, Dendro Samachurl x1
5 | Wave 1: Wooden Shield Hilichurl Guard x2, Hydro Samachurl x1<br>Wave 2: Wooden Shield Hilichurl Guard x2, Electro Hilichurl Shooter x1, Hydro Abyss Mage x1
6 | Wave 1: Large Hydro Slime x2, Cryo Whopperflower x1<br>Wave 2: Electro Slime x3, Cryo Whopperflower x1

### Liyue
- [x] 1. Stone Gate

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Treasure Hoarders: Marksman x2, Treasure Hoarders: Scout x1, Treasure Hoarders: Crusher x1<br>Wave 2: Treasure Hoarders: Gravedigger x1, Treasure Hoarders: Pyro Potioneer x1, Treasure Hoarders: Scout x1, Treasure Hoarders: Marksman x1
2 | Wave 1: Large Geo Slime x1, Geo Slime x3<br>Wave 2: Large Geo Slime x2, Geo Slime x2
3 | Wave 1: Pyro Abyss Mage x1, Electro Hilichurl Shooter x2<br>Wave 2: Blazing Axe Mitachurl x1, Cryo Hilichurl Shooter x2, Hydro Samachurl x1
4 | Wave 1: Wooden Shieldwall Mitachurl x2<br>Wave 2: Rock Shieldwall Mitachurl x2
5 | Wave 1: Geo Samachurl x2, Hilichurl Grenadier x2<br>Wave 2: Rock Shieldwall Mitachurl x2

- [x] 2. Sal Terrae

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Hilichurl Berserker x2, Hilichurl Grenadier x1, Dendro Samachurl x1<br>Wave 2: Electro Hilichurl Shooter x2, Pyro Abyss Mage x1
2 | Wave 1: Hydro Cicin x3, Large Cryo Slime x1, Cryo Slime x1<br>Wave 2: Electro Cicin Mage x1
3 | Wave 1: Stonehide Lawachurl x1
4 | Wave 1: Pyro Hilichurl Shooter x2, Hilichurl Berserker x1, Geo Samachurl x1<br>Wave 2: Electro Hilichurl Shooter x4, Geo Samachurl x1

- [x] 3. Yaoguang Shoal

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Hydro Slime x2, Cryo Whopperflower x1<br>Wave 2: Hydro Cicin x3, Electro Cicin Mage x1
2 | Wave 1: Ruin Guard x1
3 | Wave 1: Treasure Hoarders: Pugilist x1, Treasure Hoarders: Marksman x2, Treasure Hoarders: Pyro Potioneer x1<br>Wave 2: Treasure Hoarders: Scout x1, Treasure Hoarders: Handyman x1, Treasure Hoarders: Marksman x1, Treasure Hoarders: Seaman x1
4 | Wave 1: Cryo Hilichurl Shooter x2, Electro Hilichurl Shooter x1<br>Wave 2: Cryo Abyss Mage x1, Electro Hilichurl Shooter x1, Hydro Samachurl x1
5 | Wave 1: Large Pyro Slime x2, Pyro Slime x3<br>Wave 2: Pyro Whopperflower x2

- [x] 4. Liyue Harbor

**Total Ley Line Blossoms: 7**

Order | Enemies
--- | ---
1 | Wave 1: Geovishap Hatchling x2<br>Wave 2: Geovishap Hatchling x2
2 | Wave 1: Stonehide Lawachurl x1
3 | Wave 1: Fatui Skirmisher - Hydrogunner Legionnaire x1, Fatui Skirmisher - Cryogunner Legionnaire x1<br>Wave 2: Fatui Skirmisher - Anemoboxer Vanguard x1, Fatui Skirmisher - Electrohammer Vanguard x1
4 | Wave 1: Large Geo Slime x1, Geo Slime x4<br>Wave 2: Large Geo Slime x3
5 | Wave 1: Ruin Guard x1
6 | Wave 1: Cryo Hilichurl Shooter x2, Electro Hilichurl Shooter x1<br>Wave 2: Cryo Abyss Mage x1, Electro Hilichurl Shooter x1, Hydro Samachurl x1
7 | Wave 1: Large Pyro Slime x2, Pyro Slime x3<br>Wave 2: Pyro Whopperflower x2

- [x] 5. Mt. Tianheng

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Ruin Hunter x1
2 | Wave 1: Large Electro Slime x1, Mutant Electro Slime x1<br>Wave 2: Large Cryo Slime x1, Cryo Slime x3
3 | Wave 1: Hydro Abyss Mage x1, Cryo Slime x2<br>Wave 2: Cryo Abyss Mage x1, Electro Hilichurl Shooter x2
Branch Route 1: |
4 | Wave 1: Rock Shield Hilichurl Guard x4<br>Wave 2: Rock Shieldwall Mitachurl x2
Branch Route 2: |
4 | Wave 1: Blazing Axe Mitachurl x2<br>Wave 2: Rock Shieldwall Mitachurl x1, Geo Samachurl x1, Hilichurl Grenadier x2

- [x] 6. Mt. Aocang

**Total Ley Line Blossoms: 7/9**

Order | Enemies
--- | ---
1 | Wave 1: Pyro Slime x3, Pyro Whopperflower x1<br>Wave 2: Cryo Slime x3, Cryo Whopperflower x1
2 | Wave 1: Fatui Pyro Agent x1
3 | Wave 1: Electro Slime x4, Pyro Whopperflower x1<br>Wave 2: Large Geo Slime x2, Pyro Whopperflower x1
4 | Wave 1: Electro Slime x3, Hilichurl Berserker x2, Rock Shield Hilichurl Guard x1<br>Wave 2: Pyro Slime x2, Hilichurl Grenadier x2, Rock Shield Hilichurl Guard x2
Branch Route 1: | 
5 | Wave 1: Fatui Skirmisher - Electrohammer Vanguard x1, Fatui Skirmisher - Cryogunner Legionnaire x1<br>Wave 2: Fatui Skirmisher - Electrohammer Vanguard x1, Fatui Skirmisher - Pyroslinger Bracer x1, Fatui Skirmisher - Geochanter Bracer x1
6 | Wave 1: Stonehide Lawachurl x1
7 | Wave 1: Electro Cicin Mage x1, Electro Cicin x3
Branch Route 2: |
5 | Wave 1: Electro Cicin x2, Fatui Pyro Agent x1
6 | Wave 1: Rock Shield Hilichurl Guard x1, Pyro Hilichurl Shooter x3<br>Wave 2: Blazing Axe Mitachurl x1, Hilichurl Grenadier x2
7 | Wave 1: Large Electro Slime x1, Electro Slime x3, Hydro Slime x2<br>Wave 2: Large Electro Slime x1, Mutant Electro Slime x1, Electro Slime x3, Large Hydro Slime x2
8 | Wave 1: Large Cryo Slime x2<br>Wave 2: Large Hydro Slime x3
9 | Wave 1: Large Pyro Slime x2, Pyro Slime x3<br>Wave 2: Pyro Whopperflower x2

- [x] 7. Dunyu Ruins

**Total Ley Line Blossoms: 7**

Order | Enemies
--- | ---
1 | Wave 1: Electro Cicin x3, Hydro Cicin x3<br>Wave 2: Electro Cicin Mage x1
2 | Wave 1: Treasure Hoarders: Electro Potioneer x1, Treasure Hoarders: Pyro Potioneer x1, Treasure Hoarders: Marksman x1, Treasure Hoarders: Pugilist x1<br>Wave 2: Treasure Hoarders: Pugilist x1, Treasure Hoarders: Handyman x1, Treasure Hoarders: Electro Potioneer x1, Treasure Hoarders: Pyro Potioneer x1
3 | Wave 1: Large Cryo Slime x2<br>Wave 2: Cryo Whopperflower x1, Large Hydro Slime x2
4 | Wave 1: Pyro Abyss Mage x1, Electro Hilichurl Shooter x2<br>Wave 2: Cryo Abyss Mage x1, Electro Hilichurl Shooter x3
5 | Wave 1: Large Cryo Slime x2<br>Wave 2: Large Hydro Slime x3
6 | Wave 1: Large Pyro Slime x2, Pyro Slime x3<br>Wave 2: Pyro Whopperflower x2

- [x] 8. Nantianmen South

**Total Ley Line Blossoms: 7**

Order | Enemies
--- | ---
1 | Wave 1: Ruin Guard x2
2 | Wave 1: Stonehide Lawachurl x1
3 | Wave 1: Blazing Axe Mitachurl x2<br>Wave 2: Pyro Abyss Mage x1, Hilichurl Berserker x3
4 | Wave 1: Large Electro Slime x1, Electro Slime x4<br>Wave 2: Pyro Whopperflower x1, Electro Slime x4
5 | Wave 1: Pyro Abyss Mage x1, Electro Hilichurl Shooter x2<br>Wave 2: Cryo Abyss Mage x1, Electro Hilichurl Shooter x3
6 | Wave 1: Large Cryo Slime x2<br>Wave 2: Large Hydro Slime x3
7 | Plants: Flaming Flower x4<br>Wave 1: Large Pyro Slime x2, Pyro Slime x3<br>Wave 2: Pyro Whopperflower x2

- [x] 9. Nantianmen East

**Total Ley Line Blossoms: 2**

Order | Enemies
--- | ---
1 | Wave 1: Pyro Whopperflower x1, Pyro Slime x3<br>Wave 2: Geo Slime x4<br>Wave 3: Large Geo Slime x1, Geo Slime x2
2 | Wave 1: Fatui Pyro Agent x1
Branch Route 1: | 
3 | Wave 1: Treasure Hoarder x4<br>Wave 2: Treasure Hoarder x4
Branch Route 2: |
3 | Wave 1: Ruin Hunter x1
4 | Wave 1: Blazing Axe Mitachurl x1, Pyro Hilichurl Shooter x2<br>Wave 2: Anemo Samachurl x1, Electro Hilichurl Shooter x3

- [x] 10. Jueyun Karst

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Rock Shield Hilichurl Guard x4, Hilichurl Grenadier x1<br>Wave 2: Hydro Samachurl x2, Cryo Abyss Mage x1
2 | Wave 1: Rock Shield Hilichurl Guard x1, Pyro Hilichurl Shooter x3<br>Wave 2: Blazing Axe Mitachurl x1, Hilichurl Grenadier x2
3 | Wave 1: Large Electro Slime x1, Electro Slime x3, Hydro Slime x2<br>Wave 2: Large Electro Slime x1, Mutant Electro Slime x1, Electro Slime x3, Large Hydro Slime x2
4 | Wave 1: Large Cryo Slime x2<br>Wave 2: Large Hydro Slime x3
5 | Wave 1: Large Pyro Slime x2, Pyro Slime x3<br>Wave 2: Pyro Whopperflower x2

- [x] 11. Qingce Village

**Total Ley Line Blossoms: 6**

Order | Enemies
--- | ---
1 | Wave 1: Large Cryo Slime x1, Large Hydro Slime x2<br>Wave 2: Large Electro Slime x1, Mutant Electro Slime x1, Large Pyro Slime x1
2 | Wave 1: Treasure Hoarders: Marksman x1, Treasure Hoarders: Handyman x1, Treasure Hoarders: Pyro Potioneer x1, Treasure Hoarders: Scout x1<br>Wave 2: Treasure Hoarders: Scout x1, Treasure Hoarders: Gravedigger x1, Treasure Hoarders: Crusher x1
3 | Wave 1: Rock Shield Hilichurl Guard x1, Electro Hilichurl Shooter x1, Cryo Hilichurl Shooter x2<br>Wave 2: Electro Hilichurl Shooter x2, Cryo Abyss Mage x1
4 | Wave 1: Fatui Skirmisher - Electrohammer Vanguard x1, Fatui Skirmisher - Cryogunner Legionnaire x1<br>Wave 2: Fatui Skirmisher - Electrohammer Vanguard x1, Fatui Skirmisher - Pyroslinger Bracer x1, Fatui Skirmisher - Geochanter Bracer x1
5 | Wave 1: Stonehide Lawachurl x1
6 | Wave 1: Electro Cicin Mage x1, Electro Cicin x3

- [ ] 12. Guyun Stone Forest (Fewer feature points, difficult to record)

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Large Cryo Slime x2, Cryo Slime x3<br>Wave 2: Cryo Whopperflower x2
2 | Wave 1: Stonehide Lawachurl x1
3 | Wave 1: Fatui Skirmisher - Hydrogunner Legionnaire x1, Fatui Skirmisher - Cryogunner Legionnaire x1, Fatui Skirmisher - Anemoboxer Vanguard x1<br>Wave 2: Fatui Pyro Agent x1
4 | Wave 1: Hydro Abyss Mage x1, Cryo Hilichurl Shooter x3<br>Wave 2: Cryo Abyss Mage x1, Electro Hilichurl Shooter x2

- [x] 13. Mt. Xuanlian

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Hilichurl x3, Blazing Axe Mitachurl x1<br>Wave 2: Rock Shieldwall Mitachurl x2
2 | Wave 1: Electro Slime x2, Large Electro Slime x2<br>Wave 2: Large Hydro Slime x2
3 | Wave 1: Xuanwen Beast x2<br>Wave 2: Xuanwen Beast x2
4 | Wave 1: Hilichurl x2, Rock Shield Hilichurl Guard x1, Hilichurl Berserker x1, Hilichurl Grenadier x1<br>Wave 2: Blazing Axe Mitachurl x2

- [x] 14. Yaodie Valley

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Ruin Guard x2<br>Wave 2: Ruin Hunter x1
2 | Wave 1: Xuanwen Beast x2<br>Wave 2: Xuanwen Beast x2
3 | Wave 1: Hilichurl x3, Blazing Axe Mitachurl x1<br>Wave 2: Rock Shieldwall Mitachurl x2
4 | Wave 1: Xuanwen Beast x2<br>Wave 2: Xuanwen Beast x2

### Inazuma
- [x] 1. Narukami Island

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Ruin Cruiser x2<br>Wave 2: Ruin Destroyer x2
2 | Wave 1: Hydro Slime x5<br>Wave 2: Large Hydro Slime x2
3 | Wave 1: Nobushi: Kikouban x1, Nobushi: Hitsukeban x1, Nobushi: Jintouban x1
4 | Wave 1: Kairagi: Fiery Might x1, Kairagi: Dancing Thunder x1

- [x] 2. Tatarasuna

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Fatui Electro Cicin Mage x1, Mirror Maiden x1<br>Wave 2: Fatui Cryo Cicin Mage x1, Mirror Maiden x1
2 | Wave 1: Fatui Skirmisher - Geochanter Bracer x1, Fatui Skirmisher - Anemoboxer Vanguard x1<br>Wave 2: Fatui Pyro Agent x1, Mirror Maiden x1
3 | Wave 1: Treasure Hoarders: Hydro Potioneer x2, Treasure Hoarders: Seaman x2<br>Wave 2: Treasure Hoarders: Gravedigger x1, Treasure Hoarders: Crusher x1
4 | Wave 1: Ruin Scout x1, Ruin Defender x1<br>Wave 2: Ruin Destroyer x1, Ruin Cruiser x1
5 | Wave 1: Kairagi: Dancing Thunder x1, Nobushi: Jintouban x1, Treasure Hoarders: Cryo Potioneer x1, Treasure Hoarders: Hydro Potioneer x1<br>Wave 2: Kairagi: Dancing Thunder x1, Treasure Hoarders: Seaman x1

- [x] 3. Yashiori Island

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Kairagi: Fiery Might x1, Kairagi: Dancing Thunder x1
2 | Wave 1: Ruin Destroyer x3
3 | Wave 1: Nobushi: Kikouban x1, Nobushi: Hitsukeban x1, Nobushi: Jintouban x1<br>Wave 2: Nobushi: Kikouban x1, Nobushi: Hitsukeban x1, Nobushi: Jintouban x1
4 | Wave 1: Ruin Destroyer x3

- [x] 4. Watatsumi Island

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Electro Samachurl x1, Electro Hilichurl Grenadier x3<br>Wave 2: Electro Abyss Mage x2
2 | Wave 1: Anemo Specter x3, Large Anemo Slime x1<br>Wave 2: Hydro Specter x3, Large Hydro Slime x1
3 | Wave 1: Nobushi: Hitsukeban x1, Nobushi: Jintouban x2<br>Wave 2: Kairagi: Fiery Might x1, Kairagi: Dancing Thunder x1
4 | Wave 1: Fatui Skirmisher - Cryogunner Legionnaire x1, Fatui Skirmisher - Hydrogunner Legionnaire x1<br>Wave 2: Fatui Electro Cicin Mage x1, Fatui Cryo Cicin Mage x1
5 | Wave 1: Fatui Skirmisher - Cryogunner Legionnaire x1, Fatui Skirmisher - Electrohammer Vanguard x1<br>Wave 2: Fatui Skirmisher - Anemoboxer Vanguard x1, Fatui Skirmisher - Hydrogunner Legionnaire x1, Fatui Skirmisher - Geochanter Bracer x1

- [x] 5. Seirai Island

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Electro Samachurl x1, Electro Hilichurl Grenadier x3<br>Wave 2: Electro Abyss Mage x2
2 | Wave 1: Anemo Specter x3, Large Anemo Slime x1<br>Wave 2: Hydro Specter x3, Large Hydro Slime x1
3 | Wave 1: Nobushi: Hitsukeban x1, Nobushi: Jintouban x2<br>Wave 2: Kairagi: Fiery Might x1, Kairagi: Dancing Thunder x1
4 | Wave 1: Fatui Skirmisher - Cryogunner Legionnaire x1, Fatui Skirmisher - Hydrogunner Legionnaire x1<br>Wave 2: Fatui Electro Cicin Mage x1, Fatui Cryo Cicin Mage x1
5 | Wave 1: Fatui Skirmisher - Cryogunner Legionnaire x1, Fatui Skirmisher - Electrohammer Vanguard x1<br>Wave 2: Fatui Skirmisher - Anemoboxer Vanguard x1, Fatui Skirmisher - Hydrogunner Legionnaire x1, Fatui Skirmisher - Geochanter Bracer x1

### Sumeru
- [x] 1. Mawtiyima Forest

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Hydro Slime x2, Whirling Cryo Fungus x2<br>Wave 2: Winged Cryoshroom x1
2 | Wave 1: Cryo Slime x4<br>Wave 2: Large Anemo Slime x2
3 | Ruin Drake: Skywatch x1
4 | Wave 1: Eremite Crossbow x2, Eremite Linebreaker x1, Eremite Ravenbeak Halberdier x1<br>Wave 2: Eremite Crossbow x1, Eremite Axe Vanguard x1
5 | Wave 1: Hilichurl Berserker x2<br>Wave 2: Hilichurl Berserker x2, Dendro Samachurl x1

- [x] 2. Port Ormos

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Winged Cryoshroom x1, Whirling Cryo Fungus x2, Stretchy Anemo Fungus x1<br>Wave 2: Grounded Hydroshroom x2
2 | Wave 1: Winged Dendroshroom x1, Stretchy Pyro Fungus x2, Stretchy Geo Fungus x1<br>Wave 2: Winged Cryoshroom x2
3 | Wave 1: Winged Dendroshroom x1, Floating Hydro Fungus x2, Whirling Electro Fungus x1<br>Wave 2: Winged Cryoshroom x2
4 | Wave 1: Eremite Axe Vanguard x2, Eremite Linebreaker x1<br>Wave 2: Eremite Linebreaker x1, Eremite Sword-Dancer x1
5 | Wave 1: Eremite Crossbow x1, Eremite Sword-Dancer x1, Eremite Ravenbeak Halberdier x1<br>Wave 2: Eremite Crossbow x2

- [x] 3. Pardis Dhyai

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Ruin Drake: Earthguard x1<br>Wave 2: Ruin Drake: Skywatch x1
2 | Wave 1: Winged Cryoshroom x1, Floating Dendro Fungus x2<br>Wave 2: Winged Dendroshroom x1, Grounded Hydroshroom x1
3 | Wave 1: Eremite Linebreaker x1, Eremite Axe Vanguard x1, Eremite Ravenbeak Halberdier x1<br>Wave 2: Eremite Crossbow x2, Eremite Linebreaker x1, Eremite Sword-Dancer x1
4 | Wave 1: Stretchy Pyro Fungus x4<br>Wave 2: Large Pyro Slime x1, Stretchy Pyro Fungus x2, Whirling Electro Fungus x2

- [x] 4. Apam Woods

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Floating Hydro Fungus x3, Stretchy Anemo Fungus x1<br>Wave 2: Winged Cryoshroom x1
2 | Wave 1: Floating Hydro Fungus x2, Floating Dendro Fungus x2<br>Wave 2: Winged Dendroshroom x1
3 | Wave 1: Eremite Linebreaker x1, Eremite Crossbow x1, Eremite Ravenbeak Halberdier x1<br>Wave 2: Eremite Sword-Dancer x1, Eremite Axe Vanguard x1, Eremite Ravenbeak Halberdier x1
4 | Wave 1: Eremite Daythunder x1<br>Wave 2: Eremite Sunfrost x1
5 | Wave 1: Eremite Linebreaker x1, Eremite Crossbow x1, Eremite Axe Vanguard x1<br>Wave 2: Eremite Sword-Dancer x1, Eremite Ravenbeak Halberdier x1

- [x] 5. Aaru Village

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Eremite Crossbow x1, Treasure Hoarders: Pyro Potioneer x1, Treasure Hoarders: Marksman x1<br>Wave 2: Eremite Ravenbeak Halberdier x1, Eremite Axe Vanguard x1, Treasure Hoarders: Marksman x1
2 | Wave 1: Stretchy Electro Fungus x1, Whirling Electro Fungus x1, Stretchy Geo Fungus x1<br>Wave 2: Grounded Geoshroom x1, Stretchy Anemo Fungus x1
3 | Wave 1: Eremite Linebreaker x1, Eremite Sword-Dancer x1, Eremite Axe Vanguard x1, Eremite Crossbow x1<br>Wave 2: Eremite Sunfrost x1, Eremite Ravenbeak Halberdier x1
4 | Wave 1: Stretchy Pyro Fungus x1, Stretchy Geo Fungus x1, Whirling Pyro Fungus x1<br>Wave 2: Grounded Geoshroom x2, Stretchy Geo Fungus x1
5 | Wave 1: Eremite Desert Clearwater x1<br>Wave 2: Eremite Daythunder x1, Eremite Sunfrost x1

- [x] 6. Valley of Dahri

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Whirling Pyro Fungus x2, Whirling Electro Fungus x2<br>Wave 2: Grounded Geoshroom x1, Whirling Pyro Fungus x2
2 | Wave 1: Eremite Ravenbeak Halberdier x2, Eremite Axe Vanguard x1<br>Wave 2: Eremite Sunfrost x1, Treasure Hoarders: Pyro Potioneer x1
3 | Wave 1: Eremite Sword-Dancer x1, Eremite Ravenbeak Halberdier x1, Eremite Linebreaker x1<br>Wave 2: Eremite Daythunder x1, Eremite Ravenbeak Halberdier x2
4 | Wave 1: Eremite Axe Vanguard x1, Eremite Ravenbeak Halberdier x1, Treasure Hoarders: Pyro Potioneer x1, Treasure Hoarders: Electro Potioneer x1<br>Wave 2: Eremite Desert Clearwater x1, Eremite Crossbow x2

- [ ] 7. The Mausoleum of King Deshret (Fewer feature points, difficult to record)

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Fatui Pyro Agent x1, Fatui Skirmisher - Geochanter Bracer x1, Fatui Skirmisher - Pyroslinger Bracer x1<br>Wave 2: Fatui Skirmisher - Electrohammer Vanguard x1, Fatui Skirmisher - Anemoboxer Vanguard x1
2 | Wave 1: Stretchy Geo Fungus x3, Stretchy Pyro Fungus x1<br>Wave 2: Grounded Geoshroom x1, Whirling Pyro Fungus x2
3 | Wave 1: Primal Construct: Repulsor x1<br>Wave 2: Primal Construct: Prospector x1
4 | Wave 1: Eremite Linebreaker x1, Eremite Ravenbeak Halberdier x1, Eremite Crossbow x1, Eremite Axe Vanguard x1<br>Wave 2: Eremite Galehunter x1
5 | Wave 1: Eremite Stone Enchanter x1, Eremite Daythunder x1<br>Wave 2: Eremite Galehunter x1, Eremite Desert Clearwater x1

- [x] 8. Wounded Shin Valley

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Grounded Geoshroom x1, Stretchy Geo Fungus x1<br>Wave 2: Winged Dendroshroom x1, Floating Dendro Fungus x1
2 | Wave 1: Primal Construct: Prospector x1<br>Wave 2: Primal Construct: Reshaper x1, Primal Construct: Repulsor x1
3 | Wave 1: Eremite Desert Clearwater x1, Eremite Daythunder x1<br>Wave 2: Eremite Sunfrost x1, Eremite Scorching Loremaster x1
4 | Wave 1: Flying Serpent x3<br>Wave 2: Flying Serpent x1, Consecrated Flying Serpent x1

- [x] 9. Steel Dunes

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Primal Construct: Repulsor x1<br>Wave 2: Primal Construct: Reshaper x1, Primal Construct: Prospector x1
2 | Wave 1: Ruin Drake: Earthguard<br>Wave 2: Ruin Drake: Skywatch
3 | Wave 1: Grounded Geoshroom x1, Whirling Pyro Fungus x1<br>Wave 2: Grounded Hydroshroom x1, Floating Anemo Fungus x1, Floating Dendro Fungus x1
4 | Wave 1: Eremite Galehunter x1<br>Wave 2: Eremite Sunfrost x1, Eremite Floral Ring-Dancer x1

- [x] 10. Tunigi Hollow

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Consecrated Scorpion x1
2 | Eremite Scorching Loremaster x1
3 | Wave 1: Anemo Hilichurl Rogue x1, Pyro Hilichurl Shooter x2, Hydro Samachurl x1<br>Wave 2: Hydro Hilichurl Rogue x1, Blazing Axe Mitachurl x1
4 | Consecrated Red Vulture x1

### Fontaine
- [x] 1. West Slopes of Mont Automnequi

**Total Ley Line Blossoms: 5**

Order | Enemies
--- | ---
1 | Wave 1: Recon Log Mek (Ousia) x4<br>Wave 2: Suppression Specialist Mek (Ousia) x2
2 | Wave 1: Geological Survey Mek (Ousia) x2, Nimble Harvester Mek (Ousia) x2<br>Wave 2: Assault Specialist Mek (Ousia) x2
3 | Wave 1: Treasure Hoarders: Handyman x1, Treasure Hoarders: Seaman x1, Treasure Hoarders: Scout x2<br>Wave 2: Treasure Hoarders: Pyro Potioneer x2, Treasure Hoarders: Electro Potioneer x1
4 | Wave 1: Sternshield Crab x1, Armored Crab x3<br>Wave 2: Sternshield Crab x2
5 | Wave 1: Tainted Water-Splitting Phantasm x2<br>Wave 2: Tainted Water-Splitting Phantasm x1, Tainted Water-Spouting Phantasm x2

- [x] 2. Eastern Slopes of Mont Esus

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Recon Log Mek (Ousia) x1, Suppression Specialist Mek (Ousia - Pyro) x1<br>Wave 2: Recon Log Mek (Ousia) x1, Annihilation Specialist Mek (Ousia - Hydro) x1
2 | Wave 1: Fatui Skirmisher - Anemoboxer Vanguard x1, Frost Operative x1<br>Wave 2: Fatui Skirmisher - Pyroslinger Bracer x1, Wind Operative x1
3 | Wave 1: Arithmetic Enhancer Mek (Pneuma) x1, Construction Specialist Mek (Pneuma - Pyro) x1<br>Wave 2: Arithmetic Enhancer Mek (Pneuma) x1, Assault Specialist Mek (Pneuma - Pyro) x1
4 | Wave 1: Fatui Skirmisher - Pyroslinger Bracer x1, Electro Cicin Mage x1<br>Wave 2: Wind Operative x1, Frost Operative x1

- [x] 3. New Fontaine Research Institute

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Nimble Harvester Mek (Ousia) x2, Suppression Specialist Mek (Ousia - Pyro) x1<br>Wave 2: Assault Specialist Mek (Ousia - Electro) x1
2 | Wave 1: Geological Survey Mek (Pneuma) x2, Annihilation Specialist Mek (Pneuma - Electro) x1<br>Wave 2: Annihilation Specialist Mek (Pneuma - Electro) x1
3 | Wave 1: Annihilation Specialist Mek (Pneuma - Electro) x1, Suppression Specialist Mek (Pneuma - Dendro) x1<br>Wave 2: Annihilation Specialist Mek (Pneuma - Electro) x1
4 | Wave 1: Arithmetic Enhancer Mek (Ousia) x1, Recon Log Mek (Ousia) x2<br>Wave 2: Construction Specialist Mek (Ousia - Cryo) x1, Nimble Harvester Mek (Ousia) x1

- [x] 4. Lumidouce Harbor

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Tainted Water-Splitting Phantasm x2<br>Wave 2: Tainted Water-Splitting Phantasm x2
2 | Wave 1: Tainted Water-Spouting Phantasm x2<br>Wave 2: Tainted Water-Spouting Phantasm x2
3 | Wave 1: Armored Crab x5<br>Wave 2: Sternshield Crab x2
4 | Wave 1: Cherubic Sea Hare x2<br>Wave 2: Cherubic Sea Hare x2

- [x] 5. East Slopes of Mont Automnequi

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Wind Operative x1, Frost Operative x1<br>Wave 2: Wind Operative x1, Frost Operative x1
2 | Wave 1: Recon Log Mek (Pneuma) x3<br>Wave 2: Nimble Harvester Mek (Pneuma) x2
3 | Wave 1: Geological Survey Mek (Pneuma) x2<br>Wave 2: Annihilation Specialist Mek (Pneuma - Electro) x2
4 | Wave 1: Nimble Harvester Mek (Ousia) x2<br>Wave 2: Assault Specialist Mek (Ousia - Electro) x2

- [x] 6. Elynas

**Total Ley Line Blossoms: 6**

Order | Enemies
--- | ---
1 | Wave 1: Blazing Axe Mitachurl x1, Hilichurl Fighter x2<br>Wave 2: Anemo Hilichurl Rogue x1, Electro Samachurl x1
2 | Wave 1: Geological Survey Mek x2<br>Wave 2: Construction Specialist Mek x1, Nimble Harvester Mek x1
3 | Wave 1: Sternshield Crab x1, Armored Crab (Red) x2, Armored Crab (Green) x1<br>Wave 2: Sternshield Crab x2
4 | Wave 1: Tainted Water-Splitting Phantasm x2<br>Wave 2: Tainted Water-Splitting Phantasm x2
5 | Wave 1: Treasure Hoarders: Seaman x1, Treasure Hoarders: Scout x2, Treasure Hoarders: Electro Potioneer x1<br>Wave 2: Treasure Hoarders: Gravedigger x1, Treasure Hoarders: Seaman x1
6 | Wave 1: Assault Specialist Mek x1, Recon Log Mek x1<br>Wave 2: Annihilation Specialist Mek x1, Recon Log Mek x1

### Natlan
- [x] 1. Huitztli Hill

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Forged Sand Interrogator x1, Forged Sand Shieldbreaker x3, Tepetlisaur Whelp x1<br>Wave 2: Tepetlisaurus Warrior: Shard Striker x1, Tepetlisaurus Warrior: Rockbreaker Blade x1
2 | Wave 1: Treasure Hoarders: Scout x1, Treasure Hoarders: Pyro Potioneer x1, Treasure Hoarders: Hydro Potioneer x1<br>Wave 2: Treasure Hoarders: Scout x3, Treasure Hoarders: Pyro Potioneer x1, Treasure Hoarders: Hydro Potioneer x1
3 | Wave 1: Yumkasaur Whelp x2, Swiftstride Warrior: Line-Rider x1, Swiftstride Warrior: Wind-Roving Scout x1<br>Wave 2: Yumkasaurus Warrior: Whirling Leaves x2
4 | Wave 1: Forged Sand Interrogator x3, Forged Sand Shieldbreaker x1, Forged Sand Javelineer x1<br>Wave 2: Tepetlisaurus Warrior: Shard Striker x1, Tepetlisaurus Warrior: Rockbreaker Blade x1

- [x] 2. Sulfurous Veins

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Yumkasaur Whelp x1, Swiftstride Warrior: Wind-Roving Scout x1, Swiftstride Warrior: Heavy-Blade Messenger x1, Yumkasaurus Warrior: Flowing Skyfire x1<br>Wave 2: Swiftstride Warrior: Line-Rider x1, Yumkasaurus Warrior: Whirling Leaves x1
2 | Wave 1: Swiftstride Warrior: Line-Rider x3, Yumkasaur Whelp x2<br>Wave 2: Yumkasaurus Warrior: Flowing Skyfire x1, Yumkasaurus Warrior: Whirling Leaves x1
3 | Wave 1: Fatui Skirmisher - Pyroslinger Bracer x1, Fatui Skirmisher - Electrohammer Vanguard x1<br>Wave 2: Fatui Skirmisher - Pyroslinger Bracer x1, Fatui Skirmisher - Electrohammer Vanguard x1, Fatui Skirmisher - Cryogunner Legionnaire x1
4 | Wave 1: Yumkasaur Whelp x2, Swiftstride Warrior: Line-Rider x1, Swiftstride Warrior: Wind-Roving Scout x1<br>Wave 2: Yumkasaurus Warrior: Whirling Leaves x1, Yumkasaurus Warrior: Flowing Skyfire x1

- [x] 3. Caishi Peak

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Eroding Avatar of Lava x2<br>Wave 2: Eroding Avatar of Lava x2
2 | Wave 1: Tepetlisaur Whelp x1, Tepetlisaurus x1, Forged Sand Javelineer x1<br>Wave 2: Tepetlisaurus x2, Forged Sand Shieldbreaker x1, Forged Sand Interrogator x1
3 | Wave 1: Yumkasaur Whelp x1, Yumkasaurus x1, Yumkasaurus Warrior: Flowing Skyfire x1<br>Wave 2: Yumkasaur Whelp x1, Yumkasaurus x2, Swiftstride Warrior: Line-Rider x1
4 | Wave 1: Tepetlisaur Whelp x2, Forged Sand Javelineer x1, Tepetlisaurus Warrior: Rockbreaker Blade x1<br>Wave 2: Tepetlisaur Whelp x3, Tepetlisaurus x2, Tepetlisaurus Warrior: Shard Striker x1

- [x] 4. Toyac Springs

**Total Ley Line Blossoms: 2**

Order | Enemies
--- | ---
1 | Wave 1: Koholasaur Whelp x3, Flowing Blade Skirmisher x2<br>Wave 2: Koholasaurus Warrior: Waveshuttler x1, Koholasaurus Warrior: Reefsplitter x1
2 | Wave 1: Flowing Blade Skirmisher x1, Flowing Blade Grease-Saw x1, Flowing Blade Harpoon-Thrower x2<br>Wave 2: Koholasaurus Warrior: Waveshuttler x1, Koholasaurus Warrior: Reefsplitter x1

- [x] 5. Atocpan

**Total Ley Line Blossoms: 2**

Order | Enemies
--- | ---
1 | Wave 1: Tatankasaur Whelp x4, Ferocious Warrior: Human Ram x1<br>Wave 2: Tatankasaur Whelp x2, Tatankasaurus x2, Ferocious Warrior: Grappler x1
2 | Furnace Shell Mountain Weasel x1
3 | Wave 1: Tatankasaur Whelp x3, Tatankasaurus x1, Ferocious Warrior: Human Ram x1<br>Wave 2: Tatankasaur Whelp x3, Tatankasaurus x2

- [x] 6. Stadium of the Sacred Flame

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Secret Source Automaton: Hunter-Seeker x1<br>Wave 2: Secret Source Automaton: Hunter-Seeker x1
2 | Wave 1: Yumkasaur Whelp x1, Yumkasaurus x1, Swiftstride Warrior: Heavy-Blade Messenger x1, Yumkasaurus Warrior: Whirling Leaves x1<br>Wave 2: Yumkasaur Whelp x2, Yumkasaurus x1, Swiftstride Warrior: Heavy-Blade Messenger x1
3 | Wave 1: Yumkasaur Whelp x2, Swiftstride Warrior: Line-Rider x1, Yumkasaurus Warrior: Flowing Skyfire x1<br>Wave 2: Yumkasaur Whelp x2, Yumkasaurus x1, Yumkasaurus Warrior: Whirling Leaves x1
4 | Wave 1: Yumkasaur Whelp x2, Yumkasaurus x1, Yumkasaurus Warrior: Whirling Leaves x1<br>Wave 2: Yumkasaur Whelp x1, Yumkasaurus x2, Yumkasaurus Warrior: Whirling Leaves x1

- [x] 7. Masters of the Night-Wind

**Total Ley Line Blossoms: 3**

Order | Enemies
--- | ---
1 | Wave 1: Spiritspeaker Warrior: Contemplator x1, Spiritspeaker Warrior: Determinator x1, Iktomisaurus Chick x1<br>Wave 2: Spiritspeaker Warrior: Contemplator x1, Spiritspeaker Warrior: Determinator x1, Iktomisaurus Chick x1, Iktomisaurus Warrior: Cryocrystal Cannon x1
2 | Wave 1: Spiritspeaker Warrior: Contemplator x1, Spiritspeaker Warrior: Psychokinetic x1, Iktomisaurus Chick x1<br>Wave 2: Spiritspeaker Warrior: Contemplator x3, Iktomisaurus Warrior: Cryocrystal Cannon x1
3 | Wave 1: Secret Source Automaton: Hunter-Seeker x1

- [x] 8. Flower-Feather Clan

**Total Ley Line Blossoms: 3**

Order | Enemies
--- | ---
1 | Wave 1: Blazing Wayob Manifestation x1
2 | Wave 1: Qucusaurus Chick x2, Winged Warrior: Feathershedder x1, Winged Warrior: Skysoarer x1<br>Wave 2: Qucusaurus Chick x1, Winged Warrior: Skysoarer x1, Winged Warrior: Skymaster x1, Qucusaurus Warrior: Heartstar Hammer x1
3 | Wave 1: Qucusaurus Chick x1, Winged Warrior: Skymaster x1, Qucusaurus Warrior: Blazing Sky x1<br>Wave 2: Qucusaurus Chick x1, Winged Warrior: Skymaster x1, Winged Warrior: Feathershedder x1, Winged Warrior: Skysoarer x1, Qucusaurus Warrior: Blazing Sky x1

- [x] 9. Tilted Branch Cliff

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Koholasaur Whelp x3, Koholasaurus x1, Flowing Blade Skirmisher x1<br>Wave 2: Koholasaur Whelp x1, Koholasaurus x2, Flowing Blade Skirmisher x1
2 | Wave 1: Qucusaurus Chick x3, Qucusaurus x1, Winged Warrior: Skymaster x1<br>Wave 2: Qucusaurus Chick x2, Qucusaurus x2, Winged Warrior: Skymaster x1
3 | Wave 1: Koholasaur Whelp x3, Koholasaurus x1, Flowing Blade Grease-Saw x1<br>Wave 2: Koholasaur Whelp x2, Koholasaurus x2, Flowing Blade Skirmisher x1
4 | Wave 1: Mimetic Tepetlisaurus x1, Mimetic Yumkasaurus x1, Mimetic Koholasaurus x1<br>Wave 2: Mimetic Tepetlisaurus x1, Mimetic Yumkasaurus x1, Mimetic Koholasaurus x1

- [x] 10. Toyac Springs

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Koholasaur Whelp x3, Koholasaurus x1, Koholasaurus Warrior: Reefsplitter x1<br>Wave 2: Koholasaur Whelp x2, Koholasaurus x2, Koholasaurus Warrior: Waveshuttler x1
2 | Wave 1: Flow-Inverted Wayob Manifestation<br>Wave 2: Flow-Inverted Wayob Manifestation
3 | Wave 1: Koholasaur Whelp x3, Koholasaurus x1, Flowing Blade Harpoon-Thrower x1, Flowing Blade Skirmisher x1<br>Wave 2: Koholasaurus x2, Flowing Blade Harpoon-Thrower x1, Koholasaurus Warrior: Reefsplitter x1
4 | Wave 1: Koholasaur Whelp x3, Koholasaurus x1, Koholasaurus Warrior: Waveshuttler x1<br>Wave 2: Koholasaur Whelp x2, Koholasaurus x1, Flowing Blade Harpoon-Thrower x1, Flowing Blade Skirmisher x1

- [x] 11. Huhu Hill

**Total Ley Line Blossoms: 3**

Order | Enemies
--- | ---
1 | Wave 1: Tatankasaurus x2, Tatankasaur Whelp x1, Flowing Blade Harpoon-Thrower x1<br>Wave 2: Tatankasaurus x2, Tatankasaur Whelp x1, Tatankasaurus Warrior: Skybreaker x1
2 | Wave 1: Foliar-Swift Wayob Manifestation<br>Wave 2: Foliar-Swift Wayob Manifestation
3 | Wave 1: Qucusaurus Chick x3, Qucusaurus x1, Winged Warrior: Skymaster x1<br>Wave 2: Qucusaurus Chick x1, Qucusaurus x2, Winged Warrior: Feathershedder x1, Winged Warrior: Skysoarer x1

- [x] 12. Wavey Bay

**Total Ley Line Blossoms: 3**

Order | Enemies
--- | ---
1 | Wave 1: Iktomisaur Chick x1, Iktomisaurus x2, Spiritspeaker Warrior: Contemplator x1<br>Wave 2: Iktomisaur Chick x2, Iktomisaurus x2, Spiritspeaker Warrior: Contemplator x1
2 | Wave 1: Tepetlisaur Whelp x1, Tepetlisaurus x1, Forged Sand Interrogator x1, Forged Sand Javelineer x1<br>Wave 2: Tepetlisaur Whelp x1, Tepetlisaurus x2, Tepetlisaurus Warrior: Shard Striker x1
3 | Wave 1: Secret Source Automaton: Hunter-Seeker x1<br>Wave 2: Secret Source Automaton: Hunter-Seeker x1

### Nod-Krai
- [x] 1. Mossbone Wastes

**Total Ley Line Blossoms: 2**

Order | Enemies
--- | ---
1 | Wave 1: <br>Wave 2: 
2 | Wave 1: <br>Wave 2: 

- [x] 2. Lake Azure

**Total Ley Line Blossoms: 2**

Order | Enemies
--- | ---
1 | Wave 1: <br>Wave 2: 
2 | Wave 1: <br>Wave 2: 

- [x] 3. Hiisi Island

**Total Ley Line Blossoms: 4**

Order | Enemies
--- | ---
1 | Wave 1: Gleaming Charge: Frostnight Scion x1<br>Wave 2: Gleaming Charge: Frostnight Scion x1
2 | Wave 1: Oprichniki Vanguard x2, Oprichniki Healer x1, Close Combat Scout Landcruiser x1<br>Wave 2: ??? x1, Oprichniki Vanguard x2, Force Recon Scout Landcruiser x1
3 | Wave 1: Wilderness Exile x3<br>Wave 2: Wilderness Exile x2, Wilderness Hunter x1
4 | Wave 1: Oprichniki Grenadier x2, Oprichniki Vanguard x1, Oprichniki Healer x1<br>Wave 2: ??? x2, Oprichniki Hailstorm Cannoneer x1, Force Recon Storm Landcruiser x1

- [x] 4. Kuuvahki Experimental Design Bureau

**Total Ley Line Blossoms: 3**

Order | Enemies
--- | ---
1 | Wave 1: Oprichniki Line Trooper x2, Close Combat Scout Landcruiser x2<br>Wave 2: Close Combat Scout Landcruiser x1, Oprichniki Support Trooper x1, Oprichniki Hailstorm Cannoneer x1
2 | Wave 1: Oprichniki Support Trooper x1, Close Combat Storm Landcruiser x1, Force Recon Storm Landcruiser x1<br>Wave 2: Oprichniki Line Trooper x1, Force Recon Storm Landcruiser x1, Oprichniki Fireblade Shock Trooper x1
3 | Wave 1: Radiant Bladehorn x1<br>Wave 2: Radiant Bladehorn x1

## Special Thanks
- Thanks to Pingmianjing (平面镜) for creating the Fontaine Ley Line Outcrop script and Fontaine routes!
- Thanks to Qiu Yun (秋云) for providing many implementation ideas, convenient APIs, and code optimizations.
- Thanks to 起个名字好难的喵 for assisting script development.
- Thanks to V7 group members for testing before release.
- Thanks to test group members for helping record routes, providing accounts, and testing.
- Thanks to Huiyadanli (辉鸭蛋) for creating BetterGI!
