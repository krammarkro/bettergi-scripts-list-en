# Portable Waypoint Auto Monthly Renewal

## Overview
This script supports selecting either the normal Portable Waypoint or Zibai's gadget "Auspicious Canopy."
The script resets the Portable Waypoint cooldown every 6 days and keeps it renewed continuously on a monthly schedule.
On first launch, it will perform an initial renewal. Note that only one Portable Waypoint can exist on the map at a time.

## Usage Guide
1. First, create a pathing route using BetterGI's pathing editor (see the official guide if needed).
2. The first waypoint of the pathing route must be where you wish to place the Portable Waypoint. Set its type to `teleport` and its action to `force_teleport` (under Other). Save the finished route file as `续费.json` (Renewal) and place it in the script's `assets/` folder.
3. In addition, it is strongly recommended to record a full pathing route that navigates all the way to your target placement spot. If you haven't logged in for a long time or placed another waypoint temporarily, the old waypoint cannot be renewed directly; this recovery route will navigate your character to the spot to replace it. Name this file `恢复.json` (Recovery) and place it in the script's `assets/` folder.
4. After recording, always test both routes: ensure the recovery route navigates to the location properly, and ensure the renewal route teleports to the designated position without issues.

## Runtime Details
Recovery process: When the target waypoint to be renewed does not exist, teleportation will initially fail. This failure wait takes around 30 seconds due to BetterGI's internal timeout handling. Once detected, the script loads the recovery pathing file to walk back to the location and deploy a new waypoint.

## Future Plans
- Support for special locations not directly reachable via standard pathing.
- Option to renew until a specific target date.
