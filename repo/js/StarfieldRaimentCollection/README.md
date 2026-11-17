# Thousand Stars Realm - Starfield Raiment Collection

**Core Feature**: Fully automated completion of "Thousand Stars Realm - Starfield Raiment Collection" with automatic reward claiming, support for custom extra farming runs, and automatic return to Teyvat upon completion.

Powered by **OCR & Template Matching**.

## Supported Stages

By default, this script uses the designated Starfield Raiment challenge stages:
- "Roaring Target Dummy: DPS Test" (`GUID: 45694132064`)
- "Thousand Star Dummy: Total & Burst DPS" (`GUID: 24339714898`)

You can also use custom stages by enabling "Custom Realm" in the configuration and providing custom stage GUIDs.

## About Custom Realms

If current stages change or are delisted, configure custom stages as follows:

### 1. Using the Default 2-Minute Wait Template
Ensure the stage displays an Exit icon in the top-left corner upon entry (see image below):

<div align="center">
 <img src="assets/Exit.png"/>
 <p>In-stage Top-Left Exit Icon</p>
</div>

- In **JS Script Custom Configuration**, check `Custom Realm - Use 2-minute wait template (Enter GUID below)`.
- Enter the stage GUID in the `Stage GUID` field (separate multiple GUIDs with commas `,`).

### 2. Using Flexible Custom Action Sequences
- In **JS Script Custom Configuration**, **uncheck** `Custom Realm - Use 2-minute wait template`.
- Enter stage GUIDs in `Stage GUID` (comma-separated).
- Open `assets/archive.json` in the script directory and write custom action routines matching existing syntax.

Sample `archive.json`:
```json
{
  "45694132064": "sleep(41000)|keyDown(D)|sleep(700)|keyUp(D)|keyPress(F)",
  "24339714898": "sleep(61000)|keyPress(Escape)|sleep(1000)|click(978,601)|sleep(1000)"
}
```

Commands are separated by `|`:
- `sleep(1000)`: Wait duration in milliseconds.
- `keyDown(A)`: Key press down (refer to virtual key code reference).
- `keyUp(A)`: Key release.
- `keyPress(A)`: Key tap.
- `click(x,y)`: Mouse click coordinates (screen coordinates at 1920×1080).