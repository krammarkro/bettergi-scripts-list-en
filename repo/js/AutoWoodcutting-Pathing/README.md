## Precautions

**Before batch harvesting, please test your selected paths to avoid getting stuck or wasting time on unintended routes.**

The script supports detecting wood quantities in your inventory (disabled by default). You can specify wood types in the custom configuration (**detection may occasionally fail**).

Enabling inventory detection causes the manual harvest count in the custom configuration to **be ignored**, and **unrecognized wood types will not be harvested**.

Built-in paths are provided for reference. As the game and map update, they may **not always be optimal**. If you have better paths, contributions are warmly welcomed!

The script supports all wood types prior to Version 7.0:  
`Birch Wood, Cuihua Wood, Pine Wood, Fragrant Cedar Wood, Fir Wood, Bamboo Segment, Sandbearer Wood, Yumemiru Wood, Maple Wood, Aralia Wood, Otogi Wood, Brightwood, Karmaphala Wood, Adhigama Wood, Athel Wood, Tamarisk Wood, Platanus Wood, Linden Wood, Ash Wood, Cypress Wood, Torch Wood, White Chestnut Oak Wood, Explosive Wood, Mountain Date Palm Wood, Peach Palm Wood, Silver Fir Wood, Hazel Wood, Pedunculate Oak Wood, Alder Wood, Snow Poplar Wood, White Birch Wood, Bluebeech Wood, Larch Wood`

## Game Mechanics

Starting from Version 5.2, the cooldown for "The Boon of the Elder Tree" was reduced from 15 seconds to 5 seconds.

Logging out and back into the game resets wood harvesting states.

When you harvest your 11th tree, the 1st tree respawns; harvesting the 12th tree respawns the 2nd tree, and so forth in a continuous cycle.

## Loop Types

* **Unlabeled**: Starts from a Teleport Waypoint and repeats the path continuously.
* **Large Loop**: Starts from a Teleport Waypoint to navigate to the gathering area; executed only once.
* **Loop**: Contains no Teleport Waypoints to minimize loading screens and travel time; after running 1 Large Loop, repeats this loop continuously.

Because different team compositions yield different travel times, some wood varieties provide both standard paths and loop paths. Choose whichever suits your setup best by modifying `pathingMap` in [main.js](main.js).