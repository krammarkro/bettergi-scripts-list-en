# Artifact Assistant

This script runs periodically in the background. Whenever you view an individual artifact in your Inventory or on a character in Genshin Impact, text will be displayed on BetterGI's overlay window to inform you of the artifact's evaluation, suitable characters, and more.

Please run `overlay.exe` first. It continuously reads `overlay.txt` and refreshes its own window to solve the readability issues with BetterGI's native overlay window.

You can also customize the script configuration: uncheck `Output to overlay window` if you wish to disable BetterGI's overlay window messages.

Output format explanation:

``` txt
==== Complete Artifact ====
Golden Troupe: Flower of Life, 5-Star, Level +20
Total Points: 76.3, Main Stat: HP 4780
Substat 1: +0 rolls, HP +5.3%
Substat 2: +0 rolls, DEF +19
Substat 3: +4 rolls, CRIT DMG +31.1%
Substat 4: +1 roll, CRIT Rate +7.4%
Suitable: Yae Miko, Chiori, Escoffier, Furina, Fischl, Albedo
Affix Score (61.1): *CRIT Rate*, *CRIT DMG*, ATK, Elemental Mastery
----------------
```

- `==== Complete Artifact ====`: Indicates a 5-star artifact starting with 4 initial substats (or 4-star starting with 3 initial substats). May have slight calculation edge cases.
- `==== Artifact ====`: Indicates a 5-star starting with 3 initial substats (or 4-star starting with 2 initial substats). This is strictly accurate.
- `Total Points`: The sum of all substat rolls on the artifact; each roll contributes randomly from 7 to 10 points.
- `Substat`: Followed by its upgrade roll count and stat values. `Affix Score` shows total score and names of affixes relevant to suitable characters (starred with `*` if present).
- `This artifact is not very useful`: Not recommended for any current characters; can be used for Artifact Strongbox crafting or consumed as Artifact EXP fodder.
- `Suitable:`: Can serve as a best-in-slot / endgame artifact for these characters. If substat distribution is suboptimal, consider rerolling/reshaping.
- `Usable:`: A solid, usable artifact for these characters; check if the rolled stats fit your build.

Configuration instructions for `Character Overview.md`:

1. You can freely modify or add configuration entries, but you must adhere to the original syntax.
2. A numbered index must be followed by a space and character name, e.g. `108. Durin`.
3. Newline rules must be strictly followed. Do not omit newlines or parsing will fail; ensure there are two trailing newlines at the end.
4. Different variant names for a build are separated by `、`. If a character has multiple distinct builds, separate them with `;`.
5. `Artifact Main Stats:` Configures Sands of Eon, Goblet of Eonothem, and Circlet of Logos main stats. If a slot permits multiple main stats, separate them with `/`.
6. Six default templates: `HP DPS`, `ATK DPS`, `DEF DPS`, `HP Healer`, `ATK Healer`, `DEF Healer`. It is recommended not to modify these.