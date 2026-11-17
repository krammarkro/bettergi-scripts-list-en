# Genshin Lyre - AutoYuanQin

## 📑 Table of Contents

- [Disclaimer](#disclaimer)
  - [Non-Human Performance Disclaimer](#non-human-performance-disclaimer)
  - [Competition Prohibition Clause](#competition-prohibition-clause)
  - [Anti-Cheat Mechanism Notice](#anti-cheat-mechanism-notice)
- [Playing Music](#playing-music)
- [How to Add New Scores (Playing Custom Scores)](#how-to-add-new-scores-playing-custom-scores)
- [How to Upload Scores to Repository](#how-to-upload-scores-to-repository)
  - [1. Upload via Script Author](#1-upload-via-script-author)
  - [2. Self-Upload via GitHub (Recommended)](#2-self-upload-via-github-recommended)
- [MIDI Score Converter](#midi-score-converter)
- [Musical Staff Maker](#musical-staff-maker)
- [Numbered Notation Maker](#numbered-notation-maker)
- [Keyboard Notation Converter](#keyboard-notation-converter)
- [Score Creation FAQ](#score-creation-faq)
- [Score File Directory](#score-file-directory)
- [File Structure](#file-structure)
  - [Field Descriptions](#field-descriptions)
  - [Text Formatting](#text-formatting)
  - [Code Beautification](#code-beautification)
- [Notes Parsing Rules](#notes-parsing-rules)
  - [Note Syntax](#note-syntax)
- [Changelog](#changelog)

---

## Disclaimer

<details>
<summary>Click to expand</summary>

### Non-Human Performance Disclaimer

This tool emulates keyboard input to achieve automated instrument performance and is not real-time human playing. Users must not use this tool to impersonate human performers, nor mislead others into believing performances are played manually, to avoid negative community impact or infringing upon the rights of others.

### Competition Prohibition Clause

This tool is strictly prohibited for use in any form of Genshin Impact musical competitions, competitive events, or official performance evaluations. If a user violates this clause by participating in such events, all consequences (including but not limited to disqualification, account suspension, and legal liabilities) will be borne solely by the user.

### Anti-Cheat Mechanism Notice

This tool includes a built-in anti-cheat mechanism designed to prevent users from participating in any musical competitions, tournaments, or official showcases. The script periodically inputs harmless unrelated keys as a signature watermark.

</details>

---

## Playing Music

1. In the **Scheduler**, create a **New Configuration Group** or select an existing one, then add *AutoYuanQin* to it.
2. Right-click the AutoYuanQin script, select **Modify JS Custom Configuration**, and configure the parameters as desired.
3. If the **In-Game Control Panel** is enabled in JS settings (ensure the game runs in **Borderless Windowed Mode**, not Fullscreen), clicking run will bring up an HTML overlay interface. Select a song in the interface and click **Start Playing**. If the control panel is disabled, the script plays the selected song directly upon execution.
4. When playing via the in-game control panel, the script **does not exit automatically** upon finishing a song, allowing you to select and play subsequent pieces. During playback, the panel minimizes to the bottom-right corner and **cannot be focused by the mouse pointer**. It restores automatically after playback completes.
5. Pressing the configured shortcut key (default `F8`) pauses playback; pressing it again resumes from the current position. This pauses script execution only, not the game itself. If the shortcut clashes with other bindings, click the shortcut input box in the in-game control panel and press a new key or key combination (such as `Ctrl+Shift+P`).

> **Tips:**
> - The score authoring tools located under `AutoYuanQin/assets/tutorial_file` (`五线谱制谱器.html` / Musical Staff Maker, `简谱制谱器.html` / Numbered Notation Maker) are suitable for users with musical staff or numbered notation background. They generate the most precise scores, though manual input requires time and effort.
> - For a faster solution, use `AutoYuanQin/assets/tutorial_file/MIDI制谱器.html` (MIDI Converter) to automatically convert MIDI files into *AutoYuanQin* format. Scores converted this way may have minor timing imperfections; using MIDIs with 2 or fewer channels is recommended, but generation takes very little time.
> - The sections below describe the `.json` score file structure, field definitions, and content formatting requirements in detail.
> - **Placing and Updating Score Files:**
>   - If the in-game control panel is **not enabled**, place your JSON score files into `AutoYuanQin/assets/score_file`. Running the script once will automatically update `settings.json` and exit.
>   - If the in-game control panel **is enabled**, you can refresh the score list in real time directly from the panel without restarting the script.
> - Contributions of custom sheet music to the repository are always welcome!

**Note:** If you have an exceptionally large library of local scores, selecting tracks in the JS settings dropdown menu may cause UI lag. In such cases, using the in-game control panel is recommended, as it supports keyword search and instrument filtering for much smoother navigation.

---

## How to Add New Scores (Playing Custom Scores)

1. Open `MIDI制谱器.html` (MIDI Converter), `五线谱制谱器.html` (Staff Maker), or `简谱制谱器.html` (Numbered Notation Maker) under `AutoYuanQin/assets/tutorial_file` in a browser to generate a score JSON file, or write keyboard notation by hand (refer to keyboard score files like Canon with `type: "keyboard"`).
2. Ensure the `name` field in the JSON file matches the song name, and the JSON filename matches `name`.
3. Move the JSON file into the `AutoYuanQin/assets/score_file` directory.
4. Run the JS script once in the configuration group (ensure Genshin Impact is open and the bottom-left log confirms successful update).
   - Why run once: A successful run standardizes the formatting of all newly added score files under `AutoYuanQin/assets/score_file` and updates `settings.json` so the script can read them properly.

---

## How to Upload Scores to Repository

### 1. Upload via Script Author

- Place your JSON score into `AutoYuanQin/assets/score_file` (the filename will adapt automatically). After verifying playback, save the generated JSON file (e.g. formatted as `Twinkle Star - GziIvkDP.json`).
- Contact the author (**TeyvatFishing玳师**) to update the JS script.
- Join BetterGI v7 Group (Group ID: 1029539994) to request the admin update the repository.
- Alternatively, email `hijiwos@hotmail.com` with score details. Scores will be merged into the repo periodically (email submissions may experience slight delays).

### 2. Self-Upload via GitHub (Recommended)

1. Register a GitHub account and submit a PR to the [Script Repository](https://github.com/babalae/bettergi-scripts-list) following the [PR Tutorial](https://www.bettergi.com/dev/pr.html#fork-%E5%A4%8D%E5%88%B6).
2. Before uploading, verify that the following files are updated properly:
   - `manifest.json`: Increment the last digit of `version`.
   - `assets/score_file`: Score file added and verified working in-game.
   - `settings.json`: Run the script once after adding the score to `score_file` to update `settings.json` automatically.
   - `README.md`: Append your update notes under the Changelog section below following historical formatting.
3. Ensure the `author` field in each score contains your creator name, and update the `authors` list in `manifest.json`.

---

## MIDI Score Converter

1. The converter is located at `AutoYuanQin/assets/tutorial_file/MIDI制谱器.html`. Open it in any modern browser.
2. Click **Select File**, select the MIDI file you wish to convert, and conversion will start automatically.
3. Once converted, click **Export Json** and move the downloaded file to `AutoYuanQin/assets/score_file`.
4. **Do not manually modify fields in the JSON file unless you are familiar with its data structure.**

---

## Musical Staff Maker

1. Located at `AutoYuanQin/assets/tutorial_file/五线谱制谱器.html`. Open in a browser.
2. Musical sheet-reading knowledge is required; otherwise, using the [MIDI Converter](#midi-score-converter) is recommended.
3. Steps:
   - **Select Register**: Choose between 3 registers (Left / Middle / Right), each consisting of a red/blue pair of uppercase characters covering 21 keys total.
   - **Select Notes**: Click corresponding uppercase letters or `@` on the top-left image; click multiple notes to build chords.
   - **Complete Notes**: Select specific note durations in the bottom two rows. Once chosen, click **Confirm (Complete Note)** or press `Enter` while mouse focus is outside the score text box.
   - **Add Barline**: When all notes in the current measure are entered, click **Add Measure**.
   - **Line Break**: When notes on the current system are entered, click **Line Break**.
   - **Delete Notes**: If a note is incorrect, manually delete the entire note and ensure the end of the top-right code box ends with `]`, `|`, or the beginning of a line.
     > Example: `A[16]B[32]`. If you meant `B[16]` but typed a thirty-second note, delete the entire `B[32]` to leave `A[16]`, then re-enter `B`.
4. Fill in metadata (Song Name and Transcriber are required, along with BPM and Time Signature).
5. **Export Score**: Click **Export Score JSON**. Ensure filename is `SongName.json`.
6. **Import Score**: If interrupted, click **Load Score JSON** to resume editing previously exported files.

> **Note:** Keypress mode defaults to "press and immediate release". If using "press/release" sustained mode, ensure each note is released properly (unreleased keys will not sound when pressed again). This mode requires rests to control intervals between press and release.

---

## Numbered Notation Maker

1. Located at `AutoYuanQin/assets/tutorial_file/简谱制谱器.html`. Open in a browser.
2. Basic numbered musical notation reading skills required; otherwise use the [MIDI Converter](#midi-score-converter).
3. Usage is similar to the Musical Staff Maker; refer to in-tool instructions for details.

---

## Keyboard Notation Converter

1. Located at `AutoYuanQin/assets/tutorial_file/键盘谱转换器.html`. Open in a browser.
2. If you possess a MIDI file, use the MIDI converter; if you only have text keyboard notation, this converter is recommended.
3. Follow the instructions within the HTML page. If BPM is unknown, calibrate it using estimated performance durations in the validation panel.
4. **Do not manually modify JSON parameters without understanding the file structure.**

---

## Score Creation FAQ

- `/assets/tutorial_file/五线谱注解.png` details the 3 sets of keyboard layouts corresponding to treble and bass clefs (adjacent red and blue letters form an octave set across 3 octaves).
- If confused, refer to `/assets/tutorial_file/example.json`, which contains examples of most musical notation structures supported by this script.

---

## Score File Directory

All score files must be placed under `AutoYuanQin/assets/score_file`.

---

## File Structure

A standard `.json` score file structure (Staff Maker / Numbered Notation Maker format):

```json
{
  "name": "",
  "author": "",
  "instrument": "",
  "description": "",
  "type": "",
  "bpm": "",
  "time_signature": "",
  "composer": "",
  "arranger": "",
  "notes": ""
}
```

> **Note:** In the snippet above, only the values inside double quotes should be modified. Refer to `/assets/tutorial_file/example.json` for specific score formatting.

### Field Descriptions

| Field | Required | Description |
|---|---|---|
| `name` | **Required** | Song title |
| `author` | Optional | Transcriber / Score creator |
| `instrument` | Optional | Recommended instrument |
| `description` | Optional | Description notes |
| `type` | **Required** | Parsing engine: `yuanqin` (default, staff maker format), `midi` (MIDI format), `keyboard` (text keyboard format) |
| `bpm` | **Required** | Beats Per Minute |
| `time_signature` | **Required** for `yuanqin` | Time signature, e.g. `3/4` (quarter note receives one beat, three beats per measure; beat units must be powers of 2) |
| `composer` | Optional | Song composer |
| `arranger` | Optional | Musical arranger |
| `notes` | **Required** | Score content string; see parsing rules below |

### Text Formatting

- A complete `.json` score file snippet (showing a few measures):
- End each measure with `|` followed by a newline.
- End each system/line with `|` followed by two newlines.
- Do not append `|` or newlines at the very end of the score.

Example:
```json
{
  "name": "Sample Score",
  "author": "Transcriber A",
  "bpm": "120",
  "description": "Estimated duration: xxxxx, sheet source: xxx.xxxx.xxx",
  "time_signature": "4/4",
  "composer": "Composer B",
  "arranger": "Arranger C",
  "notes": "A[4](ASD)[8]Y[8-#]F[8-#](DFG)[8]R[4-*]T[8]|/n@[4](DFG)[8](CVB)[8]D[4]A[4]|/n/nA[4](ASD)[8]Y[8-#]F[8-#](DFG)[8]R[4]T[4]|/n@[4](DFG)[8](CVB)[8]D[4]A[4]"
}
```

### Code Beautification

The `notes` value in score JSON is parsed as a string where **newlines are ignored** by the engine. You can format the score with line breaks in text editors for visual clarity without affecting playback timing.

---

## Notes Parsing Rules

The `notes` field contains musical data and **must use uppercase letters**. Score content is written as a string separated into measures by `|`. Measure parsing syntax:

### `A[4]`
Press key A, treated as a quarter note.
<div align="center">
  <img src="assets/tutorial_file/四分音符示例.png"/>
  <p>Quarter note example</p>
</div>

### `F[16-#]D[16-#]S[16-#]`
Represents an **ornament / appoggiatura (grace note)**.
<div align="center">
  <img src="assets/tutorial_file/装饰音·倚音示例.png"/>
  <p>Appoggiatura example</p>
</div>
The duration of each grace note is fixed at 1/16th of the standard beat note (for 3/4, standard beat is a quarter note). The `16` carries no variable mathematical weight but must be preserved.

### `Z[4-8.3]C[4-8.3]B[4-8.$]`
Represents a **triplet** (sextuplets use `6` instead of `3`; other tuplets such as quintuplets should also use `3` or `6`). Chords within tuplets are supported.
<div align="center">
  <img src="assets/tutorial_file/三连音示例.png"/>
  <p>Triplet example</p>
</div>

- `Z[4-8.3]`: `4` denotes total tuplet duration equals a quarter note, `8` denotes visual notation displays an eighth note, `3` designates tuplet group.
- `C[4-8.3]`: Same as above.
- `B[4-8.$]`: `$` marks the final note of the tuplet group.

### `D[4-16.3]G[4-16.3]H[4-16.3]W[4-16.3]R[4-16.$]`
Represents a **quintuplet** (and similarly for N-tuplets).
<div align="center">
  <img src="assets/tutorial_file/五连音示例.png"/>
  <p>Quintuplet example</p>
</div>

### `(BG)[4-4.3]/(VF/)[4-8.$]`
Represents a **tuplet tie/slur** (similar to standard tuplets, but allows mixing different note values under the tie).
<div align="center">
  <img src="assets/tutorial_file/三连音连音线示例.png"/>
  <p>Tuplet tie example</p>
</div>

- `(BG)[4-4.3]`: First `4` is total duration (quarter note), second `4` is note value (quarter note), `3` marks tuplet.
- `(VF)[4-8.$]`: `4` is total duration, `8` is eighth note, `$` marks tuplet termination.

### Sextuplet Tie with Rests Example
```
@[2-8.3]/(AF/)[2-16.3]N[2-16.3]/(AF/)[2-16.3]N[2-16.3]/(AF/)[2-16.3]N[2-16.3]/(AF/)[2-16.3]N[2-16.3]/(AF/)[2-16.$]
```
Represents a sextuplet tie containing 1 eighth rest and 10 sixteenth notes.
<div align="center">
  <img src="assets/tutorial_file/六连音连音线示例.png"/>
  <p>Sextuplet tie example</p>
</div>

### `@[4]`
Represents a **rest**.
<div align="center">
  <img src="assets/tutorial_file/四分休止符示例.png"/>
  <p>Quarter rest example</p>
</div>
The number in brackets designates rest duration (`[4]` is a quarter rest).

### `(SH)[4-*]`
Represents a **dotted quarter note chord**.
<div align="center">
  <img src="assets/tutorial_file/附点四分音符示例.png"/>
  <p>Dotted quarter note example</p>
</div>
Presses keys S and H simultaneously as a dotted quarter note.

---

## Note Syntax

Inside brackets `[]`, the prefix before `-` represents base note value, while suffixes after `-` distinguish special notes:

- `[4]` — Quarter note
- `[16]` — Sixteenth note
- `[#]` — Grace note (usually written as `[16-#]`)
- `[-n.3]` — Tuplet (last note must end with `.$`)
- `[-n.$]` — Tuplet end

Examples:
- `[16-#]`: Sixteenth grace note.
- `A[4-8.3]S[4-8.3]D[4-8.$]`: Quarter-note triplet.

---

## Changelog

Changelog begins from version 3.0. Refer to Git history for prior versions.

<details>
<summary>Click to expand</summary>

- ver 3.8.4
  1. Added 3 tracks: "My Dearest (Animenz)", "Dare Return to Cloud Abode", "Next Daybreak".

- ver 3.8.3
  1. Added 10 tracks: "Courage" (Windsong Lyre), "My Deskmate (Melody + Accompaniment)" (Windsong Lyre), "Grandma's Penghu Bay" (Windsong Lyre), "Time Boils Rain" (Harmonic Reed Pipe), "Dream Under the Stars" (Windsong Lyre), "Mariage d'Amour" (Harmonic Reed Pipe), "Cherry Blossoms Grass" (Windsong Lyre), "Know Me" (Windsong Lyre), "Mermaid (MIDI Melody + Accompaniment)" (Windsong Lyre).
  2. Added 1 track: "Mermaid_Vodyanitsa" (Nightwind Horn).

- ver 3.8.2
  1. Added Keyboard Notation Converter with validation and playback duration estimation for BPM calibration.

- ver 3.8.1
  1. Added 5 tracks: "Boat Song of the Deep Valley III", "Strings, O Strings", "Burning Candle", "Primary Colors (Excerpt)", "Odette, Come Build a Snowman with Me".

- ver 3.8.0
  1. Clicking bottom-right opens in-game panel after pausing automated playback via shortcut.
  2. Removed redundant UI elements.

- ver 3.7.12
  1. Added 6 tracks: "Bound by Love" (Harmonic Reed Pipe), "Mermaid" (Harmonic Reed Pipe), "Insomnia" (Harmonic Reed Pipe), "If I Could Save One Heart from Breaking" (Harmonic Reed Pipe), "Frostmoon Combat Theme" (Windsong Lyre), "Canon" (Windsong Lyre).

- ver 3.7.11
  1. Added 9 tracks: "Sports March", "Moon Halo", "Rubia", "True", "Crisp Early Roast", "Parting Poem of the Breeze", "Sing of the Motherland", "Vesper Bell Song", "Nocturnal Crown (No Prelude)".

- ver 3.7.10
  1. Added 2 tracks: "Spring Festival Overture" (Harmonic Reed Pipe), "Blue and White Porcelain" (Harmonic Reed Pipe).

- ver 3.7.9
  1. Added 2 tracks: "Haruhikage" (Windsong Lyre), "Promise Under the Cherry Tree" (Windsong Lyre).

- ver 3.7.8
  1. Added 1 track: "Unbreakable Union" (Nightwind Horn).

- ver 3.7.7
  1. Added 4 tracks: "Always with Me" (Windsong Lyre), "China-E" (Harmonic Reed Pipe), "Floating Light" (Harmonic Reed Pipe), "Grain in Ear" (Windsong Lyre).

- ver 3.7.6
  1. Added 18 tracks: "Despacito", "Former Ripples", "Resting the World Easy", "Teyvat Folk Song", "Joyful Stroll", "The Truth That You Leave", "Reverse Flow", "New Moon Lullaby I: Sleep with the Moon", "Fragments of Hope", "Old Boy", "Rain Love", "Remembering Master Zhang", "Kokoronashi", "Golden Hour", "Inviting Joy (Furina Demo Climax)", "Farewell Letter", "Subway to Spring", "Sorush's Song".
  2. Added metadata including score sources, arrangement type, tempo, and expected duration.

- ver 3.7.5
  1. Added 6 tracks: "Cry For Me" (Windsong Lyre), "Luv Letter" (Harmonic Reed Pipe), "Tori no Uta" (Harmonic Reed Pipe), "溯" (Harmonic Reed Pipe), "Burying Flowers" (Harmonic Reed Pipe), "Flower Dance" (Harmonic Reed Pipe).

- ver 3.7.4
  1. Added playback pause feature: press `F8` during playback to pause or resume without pausing the game.
  2. Pausing releases currently held keys; resuming restores sustained notes and freezes playback timers to preserve rhythm.
  3. Pause/resume shortcut changed to interactive keypress recorder, supporting multi-key combinations with `Ctrl`, `Alt`, and `Shift`.
  4. Bare `A`–`Z` letters are rejected to prevent accidental pause triggers during song playback.

- ver 3.7.3
  1. Added 6 tracks: "Early Wisdom" (Windsong Lyre), "If You Suddenly Think of Me" (Windsong Lyre), "It Rained That Day" (Harmonic Reed Pipe), "Handwritten Past" (Windsong Lyre), "Sunny Day" (Windsong Lyre), "The Truth That You Leave" (Harmonic Reed Pipe).

- ver 3.7.2
  1. Switched to 8-character hash generation from notes content.
  2. Updated README documentation regarding adding scores.
  3. When auto-swapping instruments triggers the co-op ensemble popup, the script now automatically selects "Solo Performance".
  4. Added pre-performance validation: skips playback if not currently on an instrument screen.
  5. Added track: "Teyvat Folk Song" (Windsong Lyre, Author: Klopa).

- ver 3.7.1
  1. Added 2 tracks: "Call of Silence" (Harmonic Reed Pipe), "La Vaguelette - Modified" (Harmonic Reed Pipe).

- ver 3.7.0
  1. Added 7 tracks: "Lemon" (Windsong Lyre), "Sparkle" (Harmonic Reed Pipe), "New Moon Lullaby I: Sleep with the Moon" (Windsong Lyre), "Affection Touching Across Time" (Windsong Lyre), "Court of the Silver Moon (Blue Flower)" (Windsong Lyre), "Court of the Silver Moon" (Windsong Lyre), "Natlan Natlan" (Harmonic Reed Pipe).
  2. Fixed crash when in-game panel was disabled.
  3. Converted legacy MIDI scores to modern format using tick conversions.
  4. Adapted auto-instrument switching for Millennial Domains.
  5. Updated song naming from `000X.Title` to `Title-8Hash`.
  6. Displayed expected playback duration on the in-game control panel.
  7. Preserved selected song settings when opening the in-game panel.

- ver 3.6.2
  1. Added user control toggle for in-game control panel; song selection in JS settings is disabled while the panel is active.
  2. The script does not terminate after playing via the in-game panel, allowing continuous song queuing. Panel minimizes to bottom-right during playback without capturing cursor focus.
  3. Added developer feature: subtle rhythm jitter to simulate human variance.
  4. Refactored formatting and table of contents in README.

- ver 3.6.1
  1. Added 3 tracks: "Nod-Krai" (Harmonic Reed Pipe), "Eulogy of Eternal Night" (Harmonic Reed Pipe), "Coastal Town" (Harmonic Reed Pipe).

- ver 3.6.0
  1. Introduced HTML overlay interface.
  2. Moved song selection feature from JS settings to the HTML overlay.

- ver 3.5.12
  1. Updated 2 tracks: "Bright Smile" (Windsong Lyre), "Flying Squirrel March" (Harmonic Reed Pipe).

- ver 3.5.11
  1. Updated 4 tracks: "Your Name" (Harmonic Reed Pipe), "Moonglare Hymn" (Harmonic Reed Pipe), "Let the Wind Tell You" (Harmonic Reed Pipe), "Uchiage Hanabi" (Harmonic Reed Pipe).

- ver 3.5.10
  1. Updated 3 tracks: "Hello, World" (Windsong Lyre), "La Vaguelette" (Windsong Lyre), "I Haven't Forgotten" (Windsong Lyre).

- ver 3.5.9
  1. Updated track: "Merry Christmas, Mr. Lawrence" (Harmonic Reed Pipe).

- ver 3.5.8
  1. Added hover effects to note sections in staff and numbered notation makers.

- ver 3.5.7
  1. Updated track: "Love Message" (Harmonic Reed Pipe).

- ver 3.5.6
  1. Updated track: "My Northeast Hometown" (Harmonic Reed Pipe).

- ver 3.5.5
  1. Fixed bug where compensation delay was triggered on every note in single-note playback.
  2. Displayed actual elapsed performance duration in developer mode.

- ver 3.5.4
  1. Fixed logic issue where adjacent identical notes with press/release compensation failed on new MIDI formats.
  2. Fixed MIDI converter bug where identical consecutive keystrokes were not merged properly.
  3. Resolved rhythm slowdown caused by fixed delays (implemented 30ms buffer with auto-compensation).
  4. Fixed crash caused by incorrect final note duration calculation.

- ver 3.5.3
  1. Added press/release functionality to staff and numbered notation makers.
  2. Eliminated swallowed notes using extended fixed intervals.

- ver 3.5.2
  1. Added staccato recognition to MIDI converter.

- ver 3.5.1
  1. Added track: "Step Back" (Harmonic Reed Pipe).

- ver 3.5.0
  1. Added dynamic BPM tempo marker support across staff, numbered notation, and MIDI converters.
  2. Adapted playback engine to dynamic BPM shifts.
  3. Optimized core logic.

- ver 3.4.2
  1. Enhanced playback fluency for MIDI scores.

- ver 3.4.1
  1. Updated 6 tracks: "Keywords", "Dimples", "Heart Wall", "Love and Sorrow", "Red High Heels", "Mainly".
  2. Updated score upload instructions.

- ver 3.4.0
  1. Optimized exported score format in MIDI converter.
  2. Standardized local MIDI score formats.
  3. Fixed dropped notes bug in MIDI playback.
  4. Supported sustained note holds in staff and numbered notation converters.

- ver 3.3.4
  1. Updated 10 tracks: "Love You", "As You Wish", "Red High Heels", "So Many People in This World", "Way Home - 5th Anniversary", "Reverse Clock", "Greatest Works", "Orange Jasmine", "Flower Sea", "Dandelion's Promise".

- ver 3.3.3
  1. Updated 2 tracks: "Onomatopoeia Glasses" (Windsong Lyre), "Letter" (Windsong Lyre).

- ver 3.3.2
  1. Added automatic instrument swapping before performance (optional).
  2. Enabled BPM playback speed adjustment for MIDI scores.
  3. Supported multi-channel merging in MIDI converter.
  4. Simplified MIDI JSON format.
  5. Updated existing score formats.
  6. Hid note debug info during MIDI playback.
  7. Updated 3 tracks: "Sis Puella Magica", "Starlit Journey", "Life is Inexhaustible".

- ver 3.3.1
  1. Added automatic renaming: files dropped into `score_file` no longer require the `000X.` prefix.

- ver 3.3.0
  1. Updated MIDI converter with channel selection, preview audition, octave correction, instrument choice, and JSON download.
  2. Added Numbered Notation Maker.

- ver 3.2.5
  1. Updated 2 tracks: "Can We", "The Only One".

- ver 3.2.4
  1. Fixed instrument naming bug in staff maker export.
  2. Updated track: "Adore You".

- ver 3.2.3
  1. Updated staff maker with instrument selection.
  2. Updated track: "DAMIDAMI".

- ver 3.2.2
  1. Updated 2 tracks: "Boulder Crushing Chest", "ClockParadox_Drop2".

- ver 3.2.1
  1. Updated 2 tracks: "Dandelion's Promise", "Maple".

- ver 3.2.0
  1. Fixed bug where tuplets were skipped in staff notation playback.
  2. Added tracks: "Bad Apple!!", "Winter With You", "Nod-Krai".

- ver 3.1.2
  1. Fixed octave pitch error in third octave on staff maker.
  2. Adjusted sample image sizes.
  3. Allowed `Enter` key to trigger note confirmation.

- ver 3.1.1
  1. Fixed automatic lookup of `music_queue`.
  2. Improved README documentation.
  3. Added debug options in settings for playback diagnostics.
  4. Added new scores.

- ver 3.1.0
  1. Added string-based keystroke sequence parsing functions.
  2. Added keystroke serialization execution functions.
  3. Moved score authoring tools to `./tools` folder.
  4. Renamed staff software directory to `StaffMaker`.
  5. Updated manifest name to "Genshin Lyre - Music Conversion & Auto Play".
  6. Refactored `settings.json` for clarity.

</details>
