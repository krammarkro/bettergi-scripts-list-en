# Medicine Consumption Stats Script Guide

## 📋 1. Usage
This script should be run twice: once before and once after an overworld mob farming run (Pre-task = records initial medicine counts; Post-task = compares and calculates consumption). If notifications are enabled, consumption summaries are sent automatically.

Two setup methods are supported:
1. **Direct Script Inclusion**: Add this script to the pre-task and post-task slots of your Mob Farming All-in-One JS configuration.
2. **Configuration Group Mode**: Create two configuration groups with this script and schedule them before and after your mob farming run.

## 🛠️ 2. Environment and Tool Requirements
### Tool Requirements
BetterGI supports two automated medicine replenishment options:
- **Custom Modded BetterGI**: Allows auto-taking food/medicine during combat.
- **Mob Farming All-in-One JS (Recommended)**: Utilizes built-in recovery routines to consume food between pathing routes.

### Supported Consumables
- Sweet Madame, Mondstadt Hash Brown, Pita Pocket, Universal Peace, Matsutake Meat Rolls, and custom healing dishes configured in the NRE.
