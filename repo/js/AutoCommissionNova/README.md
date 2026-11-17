# Auto Daily Commissions

## Important Notice

Currently under active development. Basic commission features in the Nod-Krai region are stable.

## Acknowledgments

This script is refactored from **Xingye**'s AutoCommission automated daily commission project. The smooth iteration and optimization of this script would not be possible without the open-source efforts and craftsmanship of the original author, as well as contributions from **Yunxian vsv**, **Huan Suwei u**, **Xiaoying Huachuan Bu Yong Jiang**, **Tatai**, **Weizhi_**, and others. Special thanks to **Maosheng** for contributions to Natlan dialogue routes and mob-clearing workflows. Respect to the original author and all contributors!

## First-Time Setup

On your first run, configure the following settings in the global configuration:

1. Enter your **Combat Team Name** and **Elemental Gathering Team Name**.
2. Select the corresponding **Combat Strategy** for your combat team.
3. Save the configuration and run the script.

*Note: The UI contains some unmentioned experimental features that have not been thoroughly tested. Normal users seeking stability should avoid enabling them.*

### Claim Encounter Points and Top Up Daily Rewards

When enabled, the script first claims available Encounter Points rewards, then reads the Daily Commission reward progress `n/4`: if `4/4`, it skips commissions entirely; if incomplete, it only completes the remaining required commissions; if progress cannot be verified, it follows the default execution flow. It is recommended to place this after Resin-spending tasks in an all-in-one run, followed by a task to claim daily rewards and dispatch expeditions at Katheryne. This option is disabled by default.

## Skip Configuration Panel on Launch

Once initial configuration is complete, you can disable the popup configuration window on startup:

1. Navigate to the **Scheduler**.
2. Select the **Configuration Group** where this script resides.
3. Right-click this script and choose **Modify JS Script Custom Configuration**.
4. Uncheck **Show configuration panel on launch**.

Subsequent runs will start execution directly without displaying the panel. You can re-enable this option whenever you need to adjust teams, combat strategies, or other settings.

## Regional Support

- **Nod-Krai**: Fully supported. Commissions here are combat/mob extermination tasks with straightforward paths, making it more stable than Mondstadt.
- **Mondstadt**: Inherited from Auto Mondstadt Commissions; slightly lower stability due to dialogue-based commissions.
- **Other Regions**:
  - Currently only includes mob extermination commissions that are still undergoing testing; dialogue commissions are not supported, and some unique mechanics remain unfinished.
  - Not recommended as your primary commission region if you require 4/4 guaranteed completions every day.
  - Testing and feedback are always welcome if you wish to try them.

It is strongly recommended to set **Nod-Krai** as your primary Daily Commission region for the most reliable automated experience.

## UID Configuration

Multi-account users should enter their account UID. Configurations are saved independently per UID.