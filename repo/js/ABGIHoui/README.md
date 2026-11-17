# ABGIHoui
## Overview
#### This script is designed to be used in conjunction with the auto-bgi software.
#### If you are unfamiliar with auto-bgi, you can search for `auto-bgi` in BetterGI's official QQ channel.
#### You can also visit [ABGI on Gitee](https://gitee.com/wangjian0327/auto-bgi/blob/ginVue/README.md) to learn more, read documentation, and join the QQ group: 215053644.

##### Supported Features (If a feature fails to trigger, please update abgi):
- `"All-in-One Run"`, [Parameter: All-in-One Run name, e.g. `Default Configuration`]
- `"Configuration Group"`, [Parameter: Configuration group name, e.g. `Mob Farming`]
- `"All-in-One Run (Close Genshin)"`, [Parameter: All-in-One Run name, e.g. `Default Configuration`]
- `"Configuration Group (Close Genshin)"`, [Parameter: Configuration group name, e.g. `Mob Farming`]
- `"Artifact EXP Online Status - Log In"`
- `"Artifact EXP Online Status - Log Out"`
- `"Artifact EXP Online Debug"`
- `"Update Specified Script"`
- `"Today's Configuration Group Execution Notification"`
- `"Close Genshin Impact and Close BetterGI"`
- `"Mute Computer Audio"`
- `"Start OBS Recording"`
- `"Stop OBS Recording"`
- `"HoYoLAB / Miyoushe Check-in"`, [Requires configuring your own account files]
- `"Run Batch Script"`, [Parameter: bat script path, e.g. `E:\ABGI\restart.bat`]
- `"Change ABGI Account Info in Co-op"`, [Parameter: `uid-name`, e.g. `1*******-PlayerName`]
- `"Change Co-op Room"`, [Parameter: room name + secret key, e.g. `RoomName-SecretKey`]
- `"Wait Time"`, [Parameter: milliseconds to wait, e.g. `5000`]
- `"Low HP Detection"`, [Parameter: enable/disable, e.g. `enable`]
- `"Start 1Remote Multi-User"`, [Parameter: `xxx-xxx`, e.g. `User-Profile`]
- `"Log Off 1Remote Multi-User"`, [Parameter: `xxx-xxx`, e.g. `User-Profile`]
- `"Custom Text Output"`, [Parameter: custom text content, e.g. `Message text`]

---

#### How It Works
- Features are triggered based on ABGI's built-in keyword recognition.
- The `"Custom Text Output"` feature must be paired with ABGI's "Log Behavior Orchestration" to configure matching rules.

---
