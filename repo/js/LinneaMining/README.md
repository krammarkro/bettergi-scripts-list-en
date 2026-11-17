# Linnea Mining All-in-One

A dedicated script designed for auto-aim mining using Linnea, gathering reliably respawning mineral nodes regardless of ore variety.  
Includes Welkin Moon pop-up monitoring and can run across the 04:00 AM daily reset (though pop-ups appearing during active execution may cause temporary interruptions).  
Keeps configuration options to an absolute minimum for ease of use.

## Supported Regions

| Region | Status |
| --- | --- |
| Nod-Krai | ✅ Supported |
| Mondstadt | 🚧 Planned |
| Liyue | 🚧 Planned |
| Inazuma | 🚧 Planned |
| Sumeru | 🚧 Planned |
| Fontaine Surface | 🚧 Planned |
| Natlan | 🚧 In Progress |

## Instructions

**Important Note**: Linnea mining relies on recognizing yellow Geo-attribute minerals under Elemental Sight. Setting in-game graphics too low causes the yellow highlight to become pale, degrading recognition accuracy. As long as performance permits, please avoid lowering graphics settings excessively to save negligible power.

**Other Details**:
- The party **must include Linnea**. It is **not recommended** to bring **Columbina** in Nod-Krai, as rhinoceroses near certain ore nodes can disrupt mining.
- Configure auto-combat strategies properly; turning off auto-pickup after combat is recommended. Combat waypoints are only placed along unavoidable paths or high-yield locations.
- If you observe nodes where a single shot fails to break all ores, please report them (missed Iron Chunks or blocks obstructed by wildlife will generally not be altered).
- Awkwardly placed Iron Chunk nodes and other hard-to-reach minerals are intentionally omitted from routes due to low efficiency.

## Future Plans

> Note: Future features will continue to prioritize minimal configuration options, potentially referencing [AbundantOre](https://bgi.sh/?type=js&path=AbundantOre).  
> Multi-account support will not be implemented due to overall route duration.  
> Note: The current release is an early preview build to establish the workflow and prevent duplicate community projects. Full nation coverage and deeper route optimizations will be introduced in official releases.
