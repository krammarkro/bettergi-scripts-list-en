# Precautions / Notes for Recording Pathing Routes

## Naming Format
`{Nation}{RouteNumber}-{RegionOfFirstOutcropOrRoute}-{OutcropNumber}`

Rerunnable routes:
`{Nation}{RouteNumber}-{RegionOfFirstOutcropOrRoute}-{OutcropNumber}-rerun`

## Storage Path
`assets\pathing`

Rerunnable routes:
`assets\pathing\rerun`

## Recording Guidelines
- The first waypoint for Outcrop #1 must be a teleport.
- Use `target` to navigate to the Ley Line Outcrop location.
- For subsequent outcrops: if walking from the current position is closer, navigate directly without teleporting (i.e., the first waypoint must NOT be a teleport); if teleporting is closer, teleport instead. For rerunnable routes (`rerun`), the first waypoint must always be a teleport.
