# Auto Switch Graphics Settings & Volume

## Important Notice

- To ensure a smooth experience, please read this README completely before running the script.
- If you encounter issues after updating this JS script, please remove and re-add it across all Configuration Groups to regenerate the custom settings file matching the new Settings UI.
- If you notice the game window losing focus while running this script (i.e., operating mouse/keyboard in other windows while Genshin is obscured), go to the BetterGI main interface, click Settings in the bottom-left corner, find General Settings -> Other Settings, find "Auto Restore on Focus Loss", and toggle it on.

## Purpose

This script automatically adjusts graphics and audio settings based on user presets, eliminating tedious manual adjustments. Before starting repetitive automated tasks such as mob farming with BetterGI, you can run this script to lower graphics settings and mute audio to reduce power consumption and heat. Once tasks are complete, run it again to restore high graphics quality for regular gameplay. You can also tailor workflows to your own preferences.

## Compatibility

- **Cloud Genshin is NOT supported** due to the lack of graphics adjustment options.
- Tested and confirmed working on `1920×1080` and `2560×1440` resolutions. `3840×2160` should theoretically work as well.
- This script relies on OCR and therefore **ONLY supports Simplified Chinese in-game UI**. If you normally use another language, please submit an Issue.
- Tested to work normally under most graphics configurations. However, testing was primarily conducted on high-performance PCs; performance on older hardware or mobile devices is untested. If you run into issues, please file an Issue specifying your hardware specs and symptoms.
- **Adjusting game resolution is NOT supported** as it may crash BetterGI. You can use [Unity command-line arguments](https://docs.unity3d.com/cn/2021.1/Manual/CommandLineArguments.html) to specify window dimensions.

## Usage Instructions

Add this script to a Configuration Group, right-click the script, and select `Edit JS Script Custom Configuration` to adjust preset graphics and sound options in the pop-up dialog.

### Options Guide

- Setting labels and option names match the in-game text. If you find discrepancies, please open an Issue.
- Enabling **Fast Mode** bypasses OCR and clicks hardcoded coordinates directly, cutting execution time roughly in half compared to normal mode when non-default options are selected. Fast mode might not work properly on lower-spec machines if UI animation speeds lag. If you prioritize stability, leave Fast Mode unchecked.
- The first option for each setting is `Default`. When selected, the script will leave that option **unmodified**.
- Note: Even if you set the preset `Graphics Quality` option to something other than `Default` or `Custom`, the script will still modify individual sub-settings according to your presets. Therefore, modifying individual options away from preset defaults will result in the in-game display showing `Custom`.
- Volume settings only accept natural numbers from `0` to `10`. Set to `-1` to leave the corresponding volume unchanged. *Tip: You can also add Shell commands in the scheduler to adjust system volume directly.*
- Thank you for patiently reading this README; please remember to check the confirmation checkbox in the custom configuration.
