# Auto Story Loader - Instructions

## Project Purpose
Auto Story Loader is a utility for executing quest and story workflow files.

> **Important Notices**:
> 1. This project **does not upload any quest scripts that affect the base game to the script repository**.
> 2. **Commercial use is strictly prohibited**. Showing off or promoting automated quest capabilities in public venues is strictly prohibited.
> 3. Uploading any quest workflow scripts to public platforms is **discouraged**.
> 4. This tool provides only a technical framework and **does not contain any automated game story content**.
> 5. Do not discuss this tool on any official platforms (HoYoLAB, Bilibili, Weibo, etc.).
> 6. Strictly refrain from mentioning anything related to this tool in official livestreams, posts, or community channels.
> 7. The final right of interpretation of this document belongs to Hoshino (星野).

**Disclaimer**:
1. **Usage Risk**:
   - This script is an open-source educational project providing technical support for commission development only. Commercial use or actions violating game terms of service are prohibited.
2. **Limitation of Liability**:
   - This script is provided "as is", without warranties regarding compatibility, safety, or feature completeness.
   - Users bear all risks associated with use and must strictly adhere to the Genshin Impact Terms of Service. Developers assume no liability for any losses resulting from the use of this script.

Using this tool implies that you have read and agreed to the above terms.

---

## Usage and Configuration
1. Unpack quest scripts into the `process/` directory.
2. Add the script to the Scheduler.
3. Right-click the script to edit JS Custom Configuration.
4. Select "Refresh Quest List" in the settings.
5. The tool will scan all available quest scripts.
6. Select the quest you wish to execute from the updated list.

---

### Community Guidelines
> "We understand everyone's enthusiasm for tools, but scripting is a sensitive domain. Please ensure you:
> - Do not discuss technical details on any official platforms
> - Do not showcase or boast about tool effects in livestreams or videos
> - Do not provoke conflicts with official channels in any way
> 
> Keeping a low profile is essential to keeping the tool accessible!"

### Developer Community
Unpublished scripts such as **Auto Archon Quests, Auto Teleport Waypoints, and Auto Oculi** are obtained by contributing to the community. Let's build and share together.
**Join Us:**
- **Developer Group**: Please join one of the BadGI community groups below first; the developer group number can be obtained inside.
- **BadGI Community Groups**:
    - BadGI v1: `1031111214`
    - BadGI v2: `1058240958`
    - BadGI v3: `1061761684`

---

#### **We are currently recruiting the following four roles:**

**1. Video Editors & Social Media Operators**
- **Requirements**: Proficiency in social media account management, video editing, AI voice generation, etc.
- **Tasks**: Responsible for visual production and promotion of community content.

**2. Software Developers**
- **Requirements**: Developers in the following areas are welcome:
    - **C#** Specialists: Modifying and optimizing the BadGI core.
    - **JavaScript** Specialists: Iterating on and developing automation scripts.
    - **Python** Specialists: Refactoring AutoBGI in Python to build an uninterrupted `24/7` automated resin scheduling system.
    - **Frontend** Specialists: Optimizing and designing related web interfaces.
- **We also welcome**: Full-stack / AI developers proficient in multiple languages, or passionate beginners willing to learn from scratch (guidance provided).

**3. Community Management & Review Specialists**
- **Requirements**: Skilled in documentation, data organization, and communication; detail-oriented and responsible.
- **Tasks**: If you are not into programming or video editing, this role is a great fit. Responsible for onboarding reviews, task distribution, script statistics, tutorial documentation writing and maintenance—the core pillar maintaining community operations.

**4. Quest Script Contributors**
- *"I have no technical skills, but I want to use automated quest scripts. What can I do?"*
- **Solution**: We specially developed an automatic recorder software for this purpose. Simply start recording while playing quests in-game, and script files will be automatically generated.
- **Tasks & Rewards**: Community strength comes from sharing. By making a small contribution—**uploading your recorded quest files**—you gain access to **a massive library of automated quest scripts** in the community (including unpublished Auto Archon Quests, Auto Waypoints, Auto Oculi, etc.).

> **Reiterating**:
> - **Commercial use is strictly forbidden**; boasting or promoting automation in public is prohibited.
> - **Do not upload non-commission quest scripts to the script repository.**

**Let's protect a healthy community environment together! So that everyone gets a BetterGI to use!**

---

## New Framework Development Guide
### Quick Reference
- **File Location**: Still uses `process/.../.../process.json`
- **File Content**: Direct multi-line plain text can be written (no strict JSON required). Both Chinese and English colons are supported.
- **Metadata (Optional)**: Put at the beginning:
  - `Author: xxx`
  - `Description: xxx`
- **Quest Block Header**: Start a block with `"Quest Description String:"`, for example `Talk to Nahida:`
  - Matching Rules: OCR-recognized quest descriptions are cleaned (special characters removed, case-insensitive), matching blocks with similarity >= 0.90. Multiple blocks with identical descriptions are executed sequentially (an execution counter tracks which block runs next).
  - Default block (executed on no match or 13-second timeout): Block headers can be `Default:`, `No Quest Description:`, `default:`, `Timeout:`, etc.
- **Command Lines**: At least one space between command and parameter; `#` and `//` are comments:
  - `Pathing relative/path.json`
  - `KeyMouse relative/path.json`
  - `Dialogue NPC_Name` (automatically enables AutoSkip, interacts, and waits for return to main screen)
  - `Interact Target_Name` (Alt+Click without waiting for dialogue)
  - `Wait For Main Screen`
  - `Track Icon Icon_Type` (Bigmap / Question / Default Task)
  - `Key Key_Name` (e.g. `F`; when there is only one option, can act as interaction; writing twice is recommended for safety)
  - `Wait Milliseconds` (default: 5000ms)
  - `Quest Complete` (exits the workflow immediately)
  - `Pause Prompt_Text` (pauses script execution to let the user handle tricky situations; prompt text is optional and logged to console)
  - `Fight` (triggers combat at current position; can also be placed directly inside pathing files)
  - `Auto Loot On/Off` (toggles auto-pickup; on by default)
- **Legacy Format Compatibility**:
  - `F Nahida` is equivalent to `Dialogue Nahida`
  - `xxx.json` is equivalent to `Pathing xxx.json`

### Example: New Structure (Supports resuming from checkpoints, with retry mechanisms)
```
Author: Hoshino
Description: Example Workflow

Talk to Tunner:
What a Father Can Do-Dawn Winery-1.json
F Tunner

Ask Jilliana to concoct medicine:
What a Father Can Do-Dawn Winery-2.json
F Jilliana

Report back to Tunner:
What a Father Can Do-Dawn Winery-3.json
F Tunner
Quest Complete

Default:
What a Father Can Do-Dawn Winery-1.json
Auto Loot On
F Tunner
```
- Blocks with repeated quest descriptions execute from top to bottom sequentially.
- When no quest description is detected, checks once per second; runs the default block if no match after 13 seconds.

### Example: Legacy Structure (Can be used directly as `process.json` text)
```
Pippin1_Accept_Dialogue.json
F
Pippin2_Pause_Manual.json
Pause
Pippin3_Dialogue.json
F
Pippin4_Pause_Manual.json
Pause
Pippin5_Dialogue.json
F
Pippin6_Pause_Manual.json
KeyMouse keymouse_script.json // Pathing and keymouse scripts can be used together!
Pause
Pippin7_Dialogue_2min.json
F
```

### Other Notes
- The "Dialogue" command prioritizes Alt+Clicking the text area containing the NPC name to trigger interaction, then runs AutoSkip to skip story dialogue and waits until returning to the main screen.
- The "Interact" command only performs Alt+Click without waiting for dialogue.
- "Track Icon" supports Bigmap / Question / default Task icons.
- Original JSON array workflows remain fully backward-compatible.
> Once completed, package `process.json` and all sub-workflow files and submit them for review. Happy scripting!
