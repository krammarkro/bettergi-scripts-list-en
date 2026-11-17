## 1. Feature Overview

### 1. Initialization Record
- Establishes the baseline inventory for restorative food / medicine.
- Typically executed on first use or after major inventory adjustments.
- Saves current inventory counts to `history`.

### 2. Record + Consumption Calculation
- Requires a preexisting initialization record to run.
- Automatically retrieves the most recent initialization baseline.
- Calculates consumption of current inventory relative to the baseline.
- Saves inventory counts to `history`.
- Saves consumption results to `consumption`.

### 3. Record-Only (Snapshot) Mode
- Does not affect baseline initialization or consumption calculations.
- Simply records current inventory upon each execution.
- Useful for long-term archiving or manual tracking.
- Outputs to `snapshot`.

## 2. Output File Description

- Each mode outputs separate files formatted as: `YYYYMMDDHHmmss-Mode-Name-Quantity`. HP recovery dishes and revival dishes are recorded on separate lines.

## 3. Instructions

- **Record-Only Mode**: Runs and records inventory on demand.
- **Consumption Comparison Mode**: Compares the standard record against the last initialization baseline to determine consumption; if no baseline exists, it automatically creates an initialization record.

## 4. Version & Environment Requirements

- BetterGI >= v0.54
