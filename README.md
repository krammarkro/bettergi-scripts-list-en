# BetterGI · Script Repository

📜 Script Repository for [BetterGI (Better Genshin Impact)](https://github.com/babalae/better-genshin-impact)

Online Script Market: [bgi.sh](https://bgi.sh) | Mirror: [https://s.bettergi.com](https://s.bettergi.com/)

[How to submit to this repository? (Pull Request Guide for Everyone)](https://bettergi.com/dev/pr.html)

## Script Submission Guide

- **Combat Strategies**: Submit to the [repo/combat](https://github.com/babalae/bettergi-scripts-list/tree/main/repo/combat) directory;
- **JS Scripts**: Submit to the [repo/js](https://github.com/babalae/bettergi-scripts-list/tree/main/repo/js) directory;
- **Map Pathing Routes**: Submit to the [repo/pathing](https://github.com/babalae/bettergi-scripts-list/tree/main/repo/pathing) directory;
- **Genius Invokation TCG Strategies**: Submit to the [repo/tcg](https://github.com/babalae/bettergi-scripts-list/tree/main/repo/tcg) directory.

## Submission Standards

Please follow these guidelines when submitting. Submissions that do not comply or where the author does not respond for an extended period (typically 1 month) will be closed.

### Combat Strategies

To create a combat strategy, please refer to the documentation on [Auto Combat](https://www.bettergi.com/feats/task/domain.html) and existing combat strategies.

#### Naming Rules

- The strategy name **should include abbreviations or names of the characters used**.
- Combat strategies that can only be used in domains and are not suitable for overworld farming should have the `-Domain` suffix.
- Avoid redundant or excessive descriptive words.

#### Comments and Attribution

- Use `//` for comments. Where necessary, explain usage conditions in comments.
- It is recommended to explain related auto-combat settings via comments, for example: `// Delay check for battle completion: Set to 0.4`.
- For author attribution, use `// Author: YourName` (or `// 作者: YourName`). Incorrect formats will prevent author recognition.

#### Important Notes

- Ensure you fully understand auto-combat mechanisms (such as battle end check triggers) and the exact behavior of each action before writing strategies.
- Strategies generated entirely by AI without testing will not be accepted.
- Perform thorough in-game testing and optimization before submitting, and provide combat duration data. If an existing strategy exists, provide comparative benchmarks.

### Map Pathing

#### File Naming

Route file name format:

```text
Number-Material-[Region]-[Subregion]-SecondarySubregion-Quantity
```

Where:

- **Number**: Default two digits (`01`, `02`); for more than 100 routes, use three digits (`001`) or `A01`. Sorting should be ordered by teleport convenience or material gathering efficiency.
- **Material Name**: Use official in-game names. For gathered items, do not use informal names; for enemies, use the names from the in-game Adventurer Handbook (F1).
- **Region**: Such as `Mondstadt`, `Liyue`, `Inazuma`, etc. Only cross-region materials need to specify this.
- **Subregion**: Such as `Minlin`, fill in according to actual needs.
- **Secondary Subregion**: Such as `Jueyun Karst`. If there is no specific subregion, use the starting waypoint area or the main route area.
- **Quantity**: Expected quantity gathered along the route (e.g. `6`, `x6`).

The file name should in principle only contain the above information, and should not add extra descriptions like "Fast Route" or "Recommended Route".

```text
✔ 01-Crystal Chunk-Liyue-Jueyun Karst-6
✔ 02-Crystal Chunk-Liyue-Dihua Marsh-8
✘ 01-Crystal Chunk-Liyue-Fast Route-Jueyun Karst-6
```

When multiple routes exist in the same secondary subregion, cardinal directions (North, South, East, West) can be added to distinguish them.

The route file name must match the `name` field in the JSON file, and documentation files must be uniformly named `README.md`.

#### Folder Structure

Routes should be placed in corresponding categories, currently including:

`Local Specialties`, `Enemies and Monsters`, `Minerals`, `Food and Alchemy`, `Mob Farming`, `Other`

Top-level directories are named after the material or category; subdirectories can be added to distinguish projects, gathering methods, or authors if necessary.

```text
repo/pathing/Minerals
├── Crystal Chunk
│   ├── 01-Crystal Chunk-Liyue-Jueyun Karst-6.json
│   └── 02-Crystal Chunk-Liyue-Dihua Marsh-8.json
└── Starsilver
    └── 01-Starsilver-Snow-Covered Path-7.json
```

When conflicts exist with existing routes:

| Situation | Handling |
| --- | --- |
| Fix or supplement original route | Submit directly to original directory |
| Same type of route but different implementation | Use `Name@Author` to establish an independent directory |
| Different gathering character, method, or goal | Use `Method@Author`, `Efficient@Author`, etc. to differentiate |

For example:

```text
Crystal Chunk
├── Claymore@AuthorA
├── Zhongli@AuthorB
└── Claymore Efficient@AuthorC
```

### JS Scripts

To create a JS script, please refer to the documentation on [Creating Scripts](https://bettergi.com/dev/js/create.html).

#### Folder Naming Rules

- The script folder name **should reflect the purpose of the script**. A brief description can be provided in [manifest.json](https://bettergi.com/dev/js/create.html#manifest-json), and detailed instructions in `README.md`.
- Script folder names should follow [UpperCamelCase / PascalCase](https://en.wikipedia.org/wiki/Camel_case) without spaces, for example:

  ```text
  repo/js
  ├── AutoLeyLineOutcrop
  ├── AutoFishing
  └── ...
  ```

- Common script structure:

  ```text
  repo/js
  └── jsName
      ├── Assets
      │   ├── Pathing
      │   │   └── xxx.json
      │   └── RecognitionObject
      │       └── xxx.png
      │
      ├── src
      │   ├── modules
      │   │   ├── recognition.js
      │   │   ├── navigation.js
      │   │   └── task.js
      │   ├── utils
      │   │   └── common.js
      │   └── constants.js
      │
      ├── main.js
      ├── manifest.json
      ├── settings.json
      └── README.md
  ```

- `Assets` is used to store resources used by the script:
  - `Pathing` stores [Map Pathing](https://bettergi.com/feats/autos/pathing-dev.html) files.
  - `RecognitionObject` stores [Template Matching / Image Recognition](https://bettergi.com/dev/js/rec.html) assets.

#### HTML Overlay Content Guidelines

When rendering HTML overlay windows for guides, prompts, or configuration, follow these rules:
- Consider memory footprint issues caused by too many DOM elements or inappropriate operations.
- Submit clean, human-readable source code.
- Must not be used for advertising, promotional content, or third-party group promotions.
- Content must not contain derogatory, insulting, or inappropriate language.

#### Additional Notes

- For complex scripts, follow standard software engineering practices.
- `README.md` should clearly explain script usage, prerequisites, and configuration.
- `main.js` should serve as the script entry point and orchestrator. Large single-file scripts with hundreds of lines without modular separation are discouraged.

## Contributors

<a href="https://next.ossinsight.io/widgets/official/compose-recent-active-contributors?repo_id=866958830&limit=30" target="_blank" style="display: block" align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://next.ossinsight.io/widgets/official/compose-recent-active-contributors/thumbnail.png?repo_id=866958830&limit=30&image_size=auto&color_scheme=dark" width="655" height="auto">
    <img alt="Active Contributors of babalae/bettergi-scripts-list - Last 28 days" src="https://next.ossinsight.io/widgets/official/compose-recent-active-contributors/thumbnail.png?repo_id=866958830&limit=30&image_size=auto&color_scheme=light" width="655" height="auto">
  </picture>
</a>

## Related Source Code

Script repository web frontend:
- [bettergi-script-web](https://github.com/zaodonganqi/bettergi-script-web)
- [bettergi-scripts-web (legacy)](https://github.com/huiyadanli/bettergi-scripts-web)

Map path tracking source code: [bettergi-map](https://github.com/huiyadanli/bettergi-map)
