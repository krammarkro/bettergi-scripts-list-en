## Workflow

If a dedicated strategy exists for a given TCG opponent, the script automatically imports the deck using the corresponding deck share code and executes that strategy.

If no dedicated strategy exists, or if the share code requires Character Cards you have not yet unlocked:

- If `Auto Try Alternate Strategies` is enabled:
  - If `Select Strategies Based on Cloud Statistics` is enabled, it selects alternate strategies based on cloud stats.
  - If disabled, it cycles through alternate strategies in descending order of success rate based on local execution history.
- Otherwise, it falls back to the highly versatile "Raiden Shogun - Collei - Keqing" strategy.

## Script Configuration

| Option | Description |
| --- | --- |
| Default Deck | The in-game deck name containing your "Raiden Shogun - Collei - Keqing" team |
| Temporary Deck | The deck slot name used to import shared deck codes |
| Auto Try Alternate Strategies | Automatically try alternate strategies (numbered files in the `DeckStrategies` folder) upon match defeat |
| Select Strategies Based on Cloud Statistics | Under `Auto Try Alternate Strategies`, determines whether to prioritize strategies using cloud win rate and duration data.<br>Requires enabling `JS HTTP` permission in the script's `General Configuration`.<br>Enabling this will also report match outcomes and durations back to the cloud. |
| Minimum Win Rate Threshold for Alternate Strategies | When using local strategies, skips alternate strategies with recorded win rates below this threshold |
| Password | Any value |

**Important Deck Notes**:
1. Neither deck name may be left blank, and the two names must be distinct.
2. Both decks must be on the first page of your in-game deck list.

## Data Reported When Cloud Statistics are Enabled

This option is disabled by default.

When enabled, the script reports the opponent name, strategy name, win/loss outcome, and match duration to the cloud upon match completion. Your UID, character name, and personal game information are never uploaded.

See the implementation in `reportEffiency` within `effiency.js`.

**Regarding Initial Cloud Data**:  
As of this script's release, the initial dataset comprises 220 matches across 54 characters from the author's accounts (challenging opponents cycle through multiple strategies, hence match counts exceed character counts). While early records lacked duration tracking, their win rates serve as valuable decision-making heuristics.

## Adding Dedicated Strategies for Specific Characters

Authoring a strategy is straightforward: as long as you can win an encounter without relying on specific Action Card effects (Action Cards can be tuned for Omni elements), a strategy can be easily created.

Refer to `_StrategyTemplate.txt` under the script's `DeckStrategies` folder. After writing a strategy, rename the text file to match the target challenge opponent (e.g. `Lan`).

Contributions of strategies that improve win rates or speed are welcome!

## Adding or Removing Alternate Strategies

The script automatically identifies `.txt` files starting with a number and dot in the `DeckStrategies` directory as alternate strategies (e.g., `1.MonaSucroseJean.txt`).

When alternate strategies are enabled, failed matches trigger attempts in ascending numerical order.

To add new alternates, format your strategy according to `_StrategyTemplate.txt` and name it starting with a number followed by `.`.

To reduce retry counts, simply remove unwanted alternate strategy `.txt` files.
