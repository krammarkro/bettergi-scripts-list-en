# YuanQinAssistant (Genshin Lyre Assistant)

The BGI Edition of YuanQinAssistant is an automated in-game musical performance script that uses the `.gs2` musical score format and provides convenient MIDI conversion tools.

## Table of Contents
- [Quick Start](#quick-start)
- [Score Format Guide](#score-format-guide)
- [MIDI Conversion](#midi-conversion)
- [Changelog](#changelog)

## Quick Start
1. In BetterGI's "Full-Auto Scheduler", create a new configuration group and add this script.
2. Click Run to start the script. When entering the instrument performance interface in-game, the UI overlay will automatically pop up. Use the hide button (eye icon) to temporarily hide the UI; when returning to the instrument screen from other menus, the UI automatically reappears.
3. Musical score files are saved in the `assets/score/` directory. If score files are added or modified, rerun the script to refresh the selection list.

## Score Format Guide
The script uses command-based text score files (`.gs2`), where notes and tempo commands are written in sequential lines.
Refer to example scores included in `assets/score/` for syntax details.

## MIDI Conversion
Use the conversion utility in the tools directory to import `.mid` files and automatically generate `.gs2` notation.

## Changelog
- **v1.0.0**: Initial release with floating overlay UI and GS2 parser.
