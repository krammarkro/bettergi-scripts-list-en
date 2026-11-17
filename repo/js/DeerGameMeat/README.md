# 🦌 Lauma 🕊 Columbina Raw Meat Farming

## 📖 Script Overview

This script takes advantage of Lauma and Columbina's unique ability to attract small animals in Nod-Krai and prompt badgers to dig up meat, thoroughly harvesting every drop of nourishment from the Nod-Krai ecology.  
The main difference from pure pathing routes is that this script automatically checks for rainy weather and waits for it to end, and automatically detects whether your party contains Lauma 🦌 or Columbina 🕊.  
Raw Meat respawns 12 hours after harvesting; plan your daily runs accordingly.

## 🚀 Efficiency

- **Theoretical Yield**: Up to 85 Raw Meat in ~13 minutes
- **Actual Yield**: Approximately 75 Raw Meat in ~12 minutes under normal conditions

## ⚠️ Prerequisites & Precautions (Must Read)

1. **Character Requirements**: Ensure your party includes "Lauma" or "Columbina", as well as "Kaedehara Kazuha". In the `Task Scheduler` settings, set `Lauma` or `Columbina` as the active movement/runner character.

![Settings](assets/settings.png)

2. **Route Conflicts**: Ensure you have not already run the `Rainbowdrop Crystal` or `Frostnight Scion` routes today, as those routes overlap with this Raw Meat route.
3. **Waypoints & Exploration**: Near the central Teleport Waypoint in Taigu Barrens, unlock the high-jump launch mechanism that requires finding 10 small robots.
4. **Game Window**: Make sure the game is running at 1920x1080 resolution to avoid issues (2560x1440 has no reported issues so far).

## ⚙️ Configuration Options

### Enable Wet Status Detection
- **Feature**: Automatically detects in-game Wet status (rain, etc.).
- **Purpose**: Small animals despawn during rain; the script advances in-game time until the weather clears.
- **Recommendation**: Keep enabled.

### Max Wait Count
- **Feature**: Sets the maximum number of attempts for the Wet status time adjustment.
- **Default**: 5 times.

### Run High-Risk Routes
- **Feature**: Choose whether to run perilous routes with Frostnight Scions where characters may easily fall.
- **Description**: High-risk routes yield abundant materials, but can be toggled off if needed.
- **Default**: Enabled.

### Team Name
- **Feature**: Name of the party to switch to.
- **Description**: Automatically switches to the specified party upon starting. Make sure to disable `Switch Party` in the general `Task Scheduler` settings.
