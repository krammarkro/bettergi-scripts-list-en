# Ineffa's Buffet Automation

Automated food consumption script for feeding characters (such as Ineffa) specific quantities of ingredients or dishes.

## Usage Modes

### 1. Fixed Quantity Mode
1. Add script to BetterGI scheduler.
2. Right-click script to modify JS custom configuration:
   - **Party Name**: Team containing Ineffa (required).
   - **Target Ingredient/Dish**: Food item to feed (defaults to Apple if unselected).
   - **Quantity**: Amount fed per cycle (default: 99).
   - **Cycle Count**: Number of feeding rounds to execute (default: 1).
   - **Mode Selection**: Choose "Fixed Quantity Mode".
3. Click Run to start.

### 2. Remaining Quantity Mode
1. Add script to BetterGI scheduler.
2. Right-click script to modify JS custom configuration:
   - **Party Name**: Team containing Ineffa (required).
   - **Target Ingredients**: Food items to feed (multiple selections supported).
   - **Mode Selection**: Choose "Remaining Quantity Mode".
   - **Target Remaining Count**: Set threshold count to keep in inventory.
3. The script feeds the character until inventory reaches your configured minimum threshold.
