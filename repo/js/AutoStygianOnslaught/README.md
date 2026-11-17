# Auto Stygian Onslaught Precautions / Notes

## 0. Preface

- This script is provided for learning and entertainment purposes only. Please delete within 24 hours of download. Commercial use is prohibited. For bug reports, feedback is welcome in the test group or via QQ 119996800.
- This script is adapted from the Ley Line Outcrop and Boss All-in-One scripts.

## 1. Quick Summary & Precautions

1. **Pre-run Preparation**:
   - Please configure your combat party in `Stygian Onslaught` in advance.
2. **Combat Strength**:
   - Ensure your team has sufficient combat capability. In the current version, on combat defeat or execution error, it will only retry `once`.

## 2. Configuration Overview

1. **Artifact Rewards**:
   - By default, the script does not change the artifact reward selection.

2. **Boss Challenge Stage Selection**:
   - Required: Select which Boss challenge stage from top to bottom `(1 to 3)`, otherwise the script cannot run.

3. **Challenge Count**:
   - Default: `15` runs. If Resin is depleted during execution, the script will automatically exit.

4. **Resin Consumption Order**:
   - Separate numbers with `/` to configure the order of Resin consumption, e.g., `1/2` means use Condensed Resin first, then Original Resin.
   - Resin type mapping:
     - 1 = Condensed Resin
     - 2 = Original Resin
     - 3 = Fragile Resin
     - 4 = Transient Resin
   - Default: `1/2` (Use Condensed Resin first, then Original Resin; omitted types are not used).

5. **Maximum Combat Timeout**:
   - Default: `240` seconds. Generally does not need modification; recommended to match the Combat Timeout in the Configuration Group.

6. **Movement Time After Starting Combat**:
   - Default: `1` second (Note: unit is in `seconds`). Since the combat starting position is far from the Boss, adjust based on actual conditions. The default is usually sufficient.

7. **Combat Strategy Selection**:
   - `Use BetterGI Combat Configuration (Specified strategy below will be ignored)`: When selected, BGI will first check `Task Scheduler -> Configuration Group -> Settings -> Combat Configuration`. If combat settings are disabled there, it falls back to `Independent Tasks -> Auto Combat`.
   - `Specify Combat Strategy`: Enter the file name in the combat strategy name field (with or without `.txt` extension, omitting is recommended), e.g. `Archon Team (Advanced)`. If located in a subdirectory such as `AutoFight/community/Archon Team (Advanced).txt`, enter `community/Archon Team (Advanced)`.
   - Strategy file location: `BetterGI/User/AutoFight/`

8. **Specified Combat Strategy Name**:
   - When selecting `Specify Combat Strategy`, enter the specific strategy file name here.

9. **Outburst Period Time Cache (Experimental)**:
   - When the new pathing system is enabled, the end-time info will be read along the way; running within this window allows the script to finish immediately without repeated OCR checks.
   - This feature is experimental and currently cannot handle the transition gaps between versions.
   - When new pathing is disabled, this feature cannot be used because there is no step to read the time (only a warning is issued).

## Troubleshooting

<details>
<summary>No matching combat script found</summary>

This is usually caused by an error in the combat configuration:

- **Using BetterGI Combat Configuration**:
  1. Check `Configuration Group -> Settings -> Combat Configuration` to verify if the combat strategy is correct.
  2. If `Combat Configuration` in the Configuration Group is not enabled, check `Independent Tasks -> Auto Combat`.
  3. If issues persist, go to `Independent Tasks -> Auto Combat`, configure your desired combat strategy, switch parties manually in-game, and test-run combat manually. If it fails, consult the BGI documentation.

- **Specifying Combat Strategy**:
  1. Verify whether the configured combat strategy name is correct.
  2. File names containing `.txt` in the middle cannot be used properly (e.g. `.txtaa.txt` or `aa.txt.txt` will be normalized to `aa.txt`, causing a mismatch with the actual file).

</details>

<details>
<summary>Combat strategy file does not exist</summary>

- **Using BetterGI Combat Configuration**:
  1. Check `Configuration Group -> Settings -> Combat Configuration` to verify if the toggle is enabled and the strategy path is correct.
  2. If disabled, check `Independent Tasks -> Auto Combat`.
  3. If still problematic, manually test combat in `Independent Tasks -> Auto Combat`.

- **Specifying Combat Strategy**:
  1. Check if the specified combat strategy path is correct.
  2. Avoid filenames with duplicate `.txt` segments.

</details>

## 3. Changelog

### v2.5 (2026-08-26)
- **New Features**:
  1. Added new pathing system (faster recognition speed), enabled by default; falls back to legacy pathing automatically on failure.
  2. Added developer mode toggle: continues execution even outside outburst periods, and draws red bounding boxes around OCR detection regions for debugging.
  3. Added outburst period time cache (⚠ experimental feature): caches outburst period/calm phase timestamps to skip OCR checks on subsequent runs.
- **Optimizations**:
  1. Improved combat error handling: critical errors now throw and exit immediately rather than idling for the 240-second timeout.

### v2.4 (2026-08-20)
- **Optimizations**:
  1. Adapted for version 7.0; added recognition for new artifact sets.

### v2.3 (2026-07-04)
- **Optimizations**:
  1. Handled combat strategy path escaping; supported both with and without `.txt` extensions.
  2. Added new outburst period detection behavior to recognize calm phase interfaces without waiting 20 seconds before events start.
  3. Improved documentation descriptions and corrected configuration option names.

### v2.2 (2026-05-29)
- **New Features**:
  1. Added combat strategy configuration support for specifying custom strategy files.
- **Optimizations**:
  1. Improved combat execution logic and added exception handling.

### v2.1 (2025-09-18)
- **Optimizations**:
  1. Switched to standard template matching for Condensed Resin.
  2. Adapted for version 6.0 reward claiming interface, added Primogem refresh options and new artifact selections.
  3. Added party selection feature.

### v2.0 (2025-08-30)
- **Optimizations**:
  1. Switched to color mask template matching for Condensed Resin; required BGI version updated to 0.47.1.
  2. Adjusted matching threshold for 2K and 4K resolutions to improve accuracy.

### v1.9 (2025-08-28)
- **Optimizations**:
  1. Optimized memory release.
  2. Improved JS settings display.

### v1.8 (2025-08-09)
- **Optimizations**:
  1. Increased wait times when opening pages to prevent lag-induced errors.
  2. Corrected resin recognition error handling.
  3. Checked outburst status upon entering selection page.
  4. Adjusted domain entry detection to prevent keybinding conflicts with chat.

### v1.7 (2025-08-07)
- **Optimizations**:
  1. Checked outburst status upon entering selection page.
  2. Adjusted domain entry detection.

### v1.6 (2025-07-02)
- **Optimizations**:
  1. Improved timeout exit handling when Ley Line Outcrops are not found.
  2. Optimized OCR regions for Resin recognition.
  3. Refactored log output and code cleanups.

### v1.5 (2025-06-30)
- **New Features**:
  1. Retries twice on combat defeat before exiting domain to retry.
- **Optimizations**:
  1. Improved log display.
  2. Improved popup dialog handling when out of Resin.
  3. Optimized pickup blacklist deletion.
  4. Improved exception handling on various error states.
  5. Handled cases where Fragile Resin is hidden behind Transient Resin.

### v1.4 (2025-06-29)
- **New Features**:
  1. Added Resin check after claiming rewards; exits domain if insufficient to prevent redundant runs.
- **Optimizations**:
  1. Improved "Challenge Again" click logic with retry mechanism.
  2. Optimized auto-pickup code.
  3. Improved OCR recognition areas for difficulty and artifact selection.

### v1.3 (2025-06-28)
- **New Features**:
  1. Added automatic retry on combat defeat or execution error (retries once).
- **Optimizations**:
  1. Improved exit click timing and logic.
  2. Optimized forward movement logic after entering domain.
  3. Improved log messages.
- **Bug Fixes**:
  1. Fixed bug with selecting certain artifact sets by default.

### v1.2 (2025-06-27)
- **New Features**:
  1. Added artifact reward selection.
  2. Added automatic difficulty selection.
- **Optimizations**:
  1. Improved logical handling.
  2. Enlarged combat completion recognition area.

### v1.1
- Version information omitted.

### v1.0 (2025-06-27)
- Initial script release.
