# Teyvat Notepad

Resource auditing and tracking script for BetterGI in Genshin Impact. Running it once automatically tallies your Wish resources, Mora, Character EXP materials, and Artifact EXP, saving records per account.

## Audited Resources

- **Wish Resources**
  - Primogems
  - Intertwined Fates
  - Total Wish resource value in Primogem equivalent
  - Available Wish count
- **Mora**
- **Character EXP Materials**
  - Wanderer's Advice count
  - Adventurer's Experience count
  - Hero's Wit count
  - Total Character EXP value
- **Artifact EXP**
  - Sanctifying Unction (small bottle) count
  - Sanctifying Essence (large bottle) count
  - Total Artifact EXP

Total Artifact EXP accounts for decomposable 1-4 star artifacts, EXP bottles, and stored EXP.

## Configuration Guide

| Setting | Description |
| --- | --- |
| `enable_wish_stats` | Toggle Wish resource audit |
| `enable_mora_stats` | Toggle Mora audit |
| `enable_exp_stats` | Toggle Character EXP material audit |
| `enable_artifact_stats` | Toggle Artifact EXP audit |
| `save_history` | Save records per account in `local/history.json` |
