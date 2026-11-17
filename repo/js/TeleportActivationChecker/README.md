# Teleport Waypoint Activation Checker

Tool for systematically verifying whether map Teleport Waypoints, Statues of The Seven, Domains, and other teleport points can be successfully traveled to.

## Run Modes

- **Resume Previous Check**: Resumes from the last saved checkpoint; automatically re-tests errored points upon completion of the initial check.
- **Retest Errored Points Only**: Checks only waypoints that failed on the previous run or exceeded the slow response threshold.
- **Restart Full Check**: Clears all previous verification state and log files, starting afresh from the very first point.
- **View Check Report**: Does not perform teleportation; directly displays the summary and the list of points that failed on their final attempt. User cancellations are not falsely marked as unactivated.

## Check Results

- `local/results.log`: Raw step-by-step logs from each check.
- `local/checkpoint.json`: Checkpoint and waypoint states used to resume after stopping a run.
- `local/report.json`: User-facing summary report including passed, slow, failed, and pending points.

The script automatically saves progress when stopped. Teleport failure does not necessarily mean a waypoint is locked; errored waypoints are placed into a retry list, and decisions should be based on multiple retests.

During execution, a transparent overlay mask is displayed by default, showing current progress, waypoint info, elapsed time, and counts for passed, slow, and failed points. This can be toggled in script settings.

## Resource Files

- `assets/tp-points.json`: Map, coordinates, type, and regional info for waypoints to be checked.
- `assets/status-mask.html`: Source code for the live progress and status overlay.
- `assets/report-mask.html`: Source code for the final report display overlay.
