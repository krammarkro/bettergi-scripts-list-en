# AutoPlan - Automated Resin Schedule

**Auto Resin Schedule JS**  
This script schedules and executes resin spending by calling **BetterGI**'s built-in Auto Domain, Auto Ley Line, Auto Stygian Onslaught, and Auto Boss features.

## Features Overview

This script brings scheduling and queuing capabilities to BetterGI's automated combat modules, enabling you to:

- Configure different farming targets for different party setups
- Specify farming round counts
- Restrict runs to specific days of the week (e.g., Sunday material domains, Weekly Bosses)
- Set execution priorities (higher numbers execute first)
- Support three configuration sources: Manual text input / UID-specific profile / `bgi_tools` remote API
- Automatically check Stygian Onslaught availability status  
  ![check](assets/md/check.jpg)
- Record resin plan execution history  
  ![record](assets/md/record.jpg)

## Configuration Options

Configure settings in the script settings UI (corresponding to `settings.json`):

| Option | Type | Description | Example |
|---|---|---|---|
| **key** | input-text | Version key (required; see version table below) | `xxxx` |
| **auto_load** | multi-checkbox | Configuration load sources (multiple selection):<br>・Input: uses the `run_config` field below<br>・UID: reads `config/run_config.json` (per UID)<br>・bgi_tools: fetches from remote API | Default: `["Input", "UID"]` |
| **auto_check** | multi-checkbox | Checks to perform:<br>・Check Stygian Onslaught status<br>・Check Artifact Inventory free space | Default: `["Stygian Onslaught Check", "Artifact Space Check"]` |
| **holy_relic_threshold** | input-text | Remaining free artifact slots threshold (e.g. 100 free slots remaining at 2300/2400) | `100` |
| **run_config** | input-text | Domain schedule configuration string (used when "Input" source is active; see syntax below) | `Domain\|0,6\|9\|\|FastClear\|Pale Flame\|3\|1` |
| **loop_plan** | checkbox | Enable continuous resin plan looping | `false` |
| **retry_count** | select | Max revival retries upon party wipe | `3` |
| **bgi_tools_http_pull_json_config** | input-text | API endpoint to pull configuration from `bgi_tools` | `https://example.com/api/pull` |
| **bgi_tools_open_push** | checkbox | Push current configuration back to `bgi_tools` on completion (for sync/backup) | Checked = Enabled |
| **bgi_tools_http_push_all_json_config** | input-text | API endpoint to push domain constants | `https://example.com/api/push-all` |
| **bgi_tools_http_push_all_country_config** | input-text | API endpoint to push nation constants | `https://example.com/api/push-all` |
| **bgi_tools_http_push_all_boss_config** | input-text | API endpoint to push boss constants | `https://example.com/api/push-all` |
| **bgi_tools_token** | input-text | Authorization token for `bgi_tools` (syntax: `tokenName=tokenValue`) | `tokenName=tokenValue` |

### Schedule Configuration Syntax (`run_config` field)

```text
Type|Days(0-6)|Priority|Record|Team|TargetName|Rounds|SundaySelection|ResinOrder
```

- Separate multiple plan rules with standard commas `,`.
- Separate individual parameters within a rule with vertical pipes `|`.
- **Required**: Target/Item Name.
- Other fields can be omitted (leave empty, but preserve the `|` delimiters).

**Field Details**

| Index | Field | Required | Description | Example |
|:--:|:-----------:|:------:|:------------------------------------------------------------:|:-----------------------:|
| 1 | Type | **Required** | `Domain` / `LeyLine` / `StygianOnslaught` / `Boss` (`秘境`/`地脉`/`幽境`/`Boss`) | `Domain` |
| 2 | Days of Week | Optional | `0`=Sun, `1`=Mon, ..., `6`=Sat; slash-delimited `/`; empty = run any day | `0/3` |
| 3 | Priority | Optional | Higher numbers execute first | `9` / `5` / `1` |
| 4 | Record Run | Optional | Fill any value to track execution history | `1` |
| | | | ***Domain Type Parameters*** | |
| 5 | Team Name | Optional | Saved team name in BetterGI (used to switch teams) | `FastClear` |
| 6 | Domain / Item Name | **Required** | Exact name recognized by BetterGI Auto Domain | `Pale Flame` / `Crimson Witch of Flames` |
| 7 | Rounds | Optional | Number of runs (1 round = 1 complete domain clear) | `3` / `5` |
| 8 | Sunday / Limited | Optional | Matches BetterGI 1-3 selection values | `1` / `2` / `3` |
| 9 | Resin Priority | Optional | `Original Resin`, `Condensed Resin`, `Transient Resin`, `Fragile Resin` separated by `/` | `Condensed Resin/Original Resin` |
| | | | ***Ley Line Outcrop Type Parameters*** | |
| 5 | Team Name | Optional | Saved team name in BetterGI | `FastClear` |
| 6 | Nation | **Required** | Recognized nation (for switching regions) | `Natlan`, `Fontaine` |
| 7 | Rounds | **Required** | Number of Ley Line rounds to clear | `1` |
| 8 | Ley Line Type | **Required** | `Blossom of Revelation` / `Blossom of Wealth` (`启示之花` / `藏金之花`) | `Blossom of Revelation` |
| 9 | Companionship Team | Optional | Friendship team name | |
| 10 | Use Fragile Resin | Optional | Any value enables | |
| 11 | Use Transient Resin | Optional | Any value enables | |
| 12 | Craft Condensed Resin | Optional | Any value enables | |
| 13 | Combat Timeout | Optional | In seconds, default: 120 | `120` |
| | | | ***Stygian Onslaught Type Parameters*** | |
| 5 | Battlefield Index | Optional | (1-3) Leave empty to use BetterGI default configuration | `1` |
| 6 | Team Name | Optional | Saved team name in BetterGI | `National` |
| 7 | Use Custom Resin | Optional | Any value enables | |
| 8 | Custom Resin Order | Optional | Separated by `/` (Original Resin / Condensed Resin / Transient Resin / Fragile Resin) | `Original Resin/Condensed Resin` |
| 9 | Custom Resin Count | Optional | Separated by `/` corresponding to resin types | `1/1` |
| | | | ***Boss Type Parameters*** | |
| 5 | Boss Name | **Required** | Exact Boss name in BetterGI Auto Boss interface | `Electro Hypostasis` |
| 6 | Strategy Name | Optional | Combat strategy preset in BetterGI | `FastKill` |
| 7 | Combat Script Path | Optional | Custom combat script path overriding strategy name | `D:\scripts\boss1.txt` |
| 8 | Team Name | Optional | Team to switch to before challenging the Boss | `RaidenNational` |
| 9 | Specify Run Count | Optional | `true` or `false` (default: false, runs until resin exhausted). If true, item 10 is required. | `true` |
| 10 | Run Count | Optional | Target clears when item 9 is `true` | `3` |
| 11 | Use Transient Resin | Optional | Allow Transient Resin when Original Resin is insufficient (`true`/`false`) | `false` |
| 12 | Use Fragile Resin | Optional | Allow Fragile Resin when Original Resin is insufficient (`true`/`false`) | `false` |
| 13 | Revive Retry Count | Optional | Maximum retries to return to Statue of The Seven and retry on party wipe | `3` |
| 14 | Return to Statue Each Round | Optional | Return to Statue to heal after each clear before navigating back (`true`/`false`) | `false` |
| 15 | Reward OCR Recognition | Optional | Enable OCR to verify correct reward claim (`true`/`false`) | `false` |

**Configuration Examples**

```text
Domain|0/3|9||FastClear|Pale Flame|3|1,          # Highest priority: Run Pale Flame 3 times on Sun/Wed
Domain||5||National|Crimson Witch of Flames|5||,  # Medium priority: Run Crimson Witch 5 times daily
Domain|0|2||RaidenNat|Momiji-Dyed Court|2|2|Condensed Resin/Original Resin, # Sunday only: Use Condensed then Original Resin
LeyLine||1|1||Mondstadt|1|Blossom of Revelation|||||120, # Low priority: 1 round of Mondstadt EXP Ley Line
StygianOnslaught||1||||,                         # Stygian Onslaught: default BetterGI configuration
Boss|0/3|8||Electro Hypostasis|FastKill||RaidenNat|true|3|false|false|2|true|false, # Sun/Wed: 3 clears of Electro Hypostasis
Boss||5||Cryo Regisvine|||National|true|1|true|false|1||, # Daily: 1 clear of Cryo Regisvine, allow Transient Resin
Boss||3||Pyro Regisvine||||false||||||           # Simple setup: Farm Pyro Regisvine until resin runs out
```

### JSON Profile Syntax (`config/run_config.json`)

```json
[
  [
    "10000002",
    [
      {
        "order": 1,
        "days": [0],
        "record": false,
        "runType": "Domain",
        "autoFight": {
          "physical": [
            { "order": 0, "name": "Original Resin", "open": true },
            { "order": 1, "name": "Condensed Resin", "open": false },
            { "order": 2, "name": "Transient Resin", "open": false },
            { "order": 3, "name": "Fragile Resin", "open": false }
          ],
          "domainName": "Pale Flame",
          "partyName": "FastClear",
          "sundaySelectedValue": 1,
          "domainRoundNum": 3
        }
      },
      {
        "order": 2,
        "days": [],
        "record": true,
        "runType": "LeyLine",
        "autoLeyLineOutcrop": {
          "count": 1,
          "country": "Natlan",
          "leyLineOutcropType": "Blossom of Revelation",
          "friendshipTeam": "",
          "team": "",
          "timeout": 120,
          "isGoToSynthesizer": false,
          "useFragileResin": false,
          "useTransientResin": false
        }
      },
      {
        "order": 3,
        "days": [0, 3],
        "record": true,
        "runType": "Boss",
        "autoBoss": {
          "bossName": "Electro Hypostasis",
          "strategyName": "FastKill",
          "combatStrategyPath": "",
          "teamName": "RaidenNat",
          "specifyRunCount": true,
          "runCount": 3,
          "useTransientResin": false,
          "useFragileResin": false,
          "reviveRetryCount": 2,
          "returnToStatueAfterEachRound": true,
          "rewardRecognitionEnabled": false
        }
      }
    ]
  ]
]
```

### Visual Web Configuration Tool

If you prefer a visual web interface over editing text syntaxes, you can deploy [bettergi-scripts-tools](https://github.com/Kirito520Asuna/bettergi-scripts-tools) (v0.0.8+ recommended):

![login](assets/md/bgi-tools-login.jpg)
![init](assets/md/bgi-tools-config-ui-init.jpg)
![config](assets/md/bgi-tools-config-ui.jpg)

## Recommendations

1. For initial setup, check only "Input" source and test rules in `run_config`.
2. For advanced multi-account setups, switch to "UID" source and maintain profiles in `config/run_config.json`.
3. If hosting a personal cloud configuration service, use "bgi_tools" source with push synchronization.
4. Ensure BetterGI native **Auto Domain** functions correctly (Zhongli recognition, combat scripts, etc.) before scheduling.

## FAQ

- **Plan does not execute?**  
  → Verify version key, ensure the matching load source is checked, and verify domain/boss names match BetterGI exactly.
- **Day-of-week restrictions not working?**  
  → Confirm system time is correct and day numbers are 0-6 (0 = Sunday).

## Version Key Table

| Version | Key | `bettergi-scripts-tools` Version |
|:---:|:---:|:---:|
| 0.0.1 - 0.0.7 | `oiJbmjU2R0NniiwiZxh` | 0.0.4+ - 0.0.6+ |
| 0.0.8 - 0.0.12 | `yHlw8FHjTJAPEtpp9O+` | 0.1.3+ - 0.1.6+ |
| 0.1.3 - 0.1.5 | `2Cbayi1S2I41BlTXb/XAmw==` | 0.1.8+ - 0.1.9+ |

---

## Changelog Summary

### 0.1.5 (2026-11-12)
- Fixed missing error prompts when HTTP requests encounter exceptions.

### 0.1.4 (2026-09-06)
- Adapted to BetterGI core API updates; fixed OCR recognition issues.

### 0.1.3 (2026-08-22)
- Fixed Stygian Onslaught check; updated JSON format.

### 0.1.2 (2026-07-30)
- Separated Stygian Onslaught checks; added Artifact inventory capacity threshold check; added custom boss combat timeout.

### 0.1.0 - 0.1.1 (2026-06)
- Added Auto Boss scheduling and constant synchronization with `bgi_tools`.

### 0.0.7 - 0.0.9 (2026-04 - 2026-05)
- Replaced OCR UID with `genshin.uid()` native API; raised minimum BetterGI version to 0.61.0.

**Author**: Kirito520Asuna (云端客)
