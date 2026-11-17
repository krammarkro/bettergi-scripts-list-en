### Authors
- [QiuYun (秋云)](https://github.com/physligl) (Original Author)
- Volcano
- MoJiang (莫酱)

> An automated script for farming Character Companionship EXP. Supports enemy types such as Treasure Hoarders, Fatui, and Spinocrocodiles (Floating Fungi and Electro Cicin Mages are experimental). Earns Companionship EXP by automatically triggering and completing Random Events.

### Table of Contents
- [Features Overview](#features-overview)
- [Enemy Types](#enemy-types)
- [Quick Start](#quick-start)
- [Execution Workflow](#execution-workflow)
- [FAQ](#faq)
- [File Structure](#file-structure)
- [Precautions / Notes](#precautions--notes)
- [Changelog](#changelog)
- [Contribution Guide](#contribution-guide)
- [Issue Feedback](#issue-feedback)
- [Community Support](#community-support)

---

### Features Overview

An automated script for farming Character Companionship EXP. Supports enemy types such as Treasure Hoarders, Fatui, and Spinocrocodiles (Floating Fungi and Electro Cicin Mages are experimental). Automatically triggers and completes Random Events to earn Companionship EXP.

- **Daily Limits**: Up to 10 Companionship EXP rewards per day across a maximum of 50 event triggers. Triggering Random Events elsewhere deducts from this count.
- **Loop Control**: Run count is controlled by `runTimes`. If no event is triggered or an early termination condition is met, the script exits automatically.
- **Average Duration**: Approximately 1 minute per cycle; high-efficiency teams can complete a cycle in around 40 seconds.
- **Success Rate**: Close to 98% under proper configuration, with a small probability of missing the first Random Event.

---

### Enemy Types

#### Treasure Hoarders
| Property | Details |
|---|---|
| **Trigger Event** | "No Thieves on the Island" - Defeat sneaky Treasure Hoarders |
| **Region** | Inazuma |
| **Difficulty** | ⭐⭐⭐ (Medium) |
| **Special Feature** | (Optional) Supports clearing native Hilichurls first |

#### Fatui & Hilichurls & Treasure Hoarders
| Property | Details |
|---|---|
| **Trigger Event** | "Fair Trade, Clear Conscience" - Defeat the Fatui and The Eremites<br>"Hazardous Cargo Prohibited!" - Defeat all Treasure Hoarders<br>"Hilichurls' Dinner Tonight" - Defeat all Hilichurls |
| **Region** | Sumeru |
| **Difficulty** | ⭐⭐⭐⭐ (Higher) |

#### Spinocrocodiles
| Property | Details |
|---|---|
| **Trigger Event** | "Fierce Foes" - Defeat all Spinocrocodiles |
| **Region** | Sumeru |
| **Difficulty** | ⭐⭐ (Lower) |

---

### Quick Start

#### Prerequisites
- ✅ Install BetterGI (version > 0.44.7)
- ✅ Subscribe to the script and add it to the Task Scheduler

#### Floating Fungi & Electro Cicin Mage
These are experimental features and currently unstable. You may test them, but they are not recommended for daily automated use.

#### Task Scheduler Configuration
- **Pathing Configuration**:
  - ✅ Enable "Only heal at Teleport Waypoints"
  - ✅ Enable "Allow use in JS scripts"
  - ✅ Enable "Override Auto Combat Configuration in JS"

- **Combat Configuration**:
  - **Combat Strategy**: Select or design an appropriate combat strategy file for your team.
  - **Team Investment**: High character investment is recommended; pure Companionship-farming teams with unbuilt characters may fail to defeat enemies.
  - **Important Settings**:
    - Default: ❌ Disable "Auto-detect combat end"
    - If "Disable asynchronous combat (more stable)" is enabled: ✅ Enable and properly configure "Auto-detect combat end" (applies to all enemy types).

- **Recommended Team Lineups**
> Based on community testing for optimal efficiency. Contributions of other efficient setups are welcome via Pull Request (please include rationale and demo video).

| Character | Priority | Features | Notes |
|---|---|---|---|
| **Neuvillette** | ⭐⭐⭐⭐⭐ | Highest efficiency in community testing | Consistent damage output, ideal for auto combat |
| **Citlali** | ⭐⭐⭐⭐ | Provides shield, off-field Cryo freezes enemies | Offers survivability |
| **Kaedehara Kazuha** | ⭐⭐⭐⭐ | Material grouping, Swirl damage | Boosts clear and pickup efficiency |
| **Furina** | ⭐⭐⭐ | Off-field damage | Requires sustained healing |
| **Zhongli** | ⭐⭐⭐ | Strong shield protection | In combat strategies, cast Skill left/right appropriately |

#### Script Settings
> Configure by right-clicking the script in the Task Scheduler -> "Edit JS Custom Configuration"

- **Disable Auto-pickup in Real-time Tasks (`disablePickup`)**:
  - Unchecked: Enable auto-pickup (Default)
  - Checked: Disable auto-pickup
- **Enemy Type**: Supports "Treasure Hoarders", "Fatui", "Spinocrocodiles", "Floating Fungi", and "Electro Cicin Mage".
- **Run Times**:
  - Enter a positive integer (Default: 10).
  - Recommended <= 10 runs to match the daily reward cap.
- **Hilichurl Clear Timeout (`qiuQiuRen`, seconds)**:
  - Default: `0` (Disabled).
  - Only valid for Treasure Hoarders. Setting > 0 runs an initial Hilichurl clearing phase.
- **Team Name**:
  - Enter your combat party name.
  - Leave empty to use the active party.
- **OCR Timeout**:
  - OCR detection timeout (Default: 10 seconds).
  - Too short may cause missed detection and premature exit; too long may cause unnecessary waiting.
  - Recommended to keep the default value.
- **Combat Timeout**:
  - Single combat timeout in seconds (Default: 120 seconds).
  - Reaching timeout cancels the task, so do not set it too short.
  - The script automatically detects combat completion with high accuracy.
- **Disable Asynchronous Combat (More stable; requires "Combat End Detection"; applies to all enemies)**:
  - When enabled: Uses synchronous combat execution branch.
  - When disabled: Uses asynchronous combat + OCR determination branch.

#### One-Click Run
Once configured, simply run the script to begin automated Companionship EXP farming.

#### Advanced Settings
- **Clear Natives**: Only applies to Treasure Hoarders mode, clears nearby Hilichurls.
- **Time Window Mode**: Supports scheduling runs based on specific date cycles.

---

### Execution Workflow

1. **Team Switch**: Automatically switches to the specified party.
2. **Preparation Phase**:
   - Treasure Hoarders: (Optional) Clear Hilichurls -> Proceed to trigger point.
   - Fatui: Proceed directly to trigger point.
3. **Event Detection**: Uses OCR to detect Random Event trigger.
4. **Combat Execution**: Automatically paths to combat point and starts combat.
5. **Result Evaluation**: Checks and logs combat result.
6. **Loop Execution**: Repeats until target runs are finished or no event is triggered.

---

### FAQ

#### Important Reminder
- Do NOT perform manual game operations while the script is running.

#### Common Questions

##### Q: Why is the combat strategy not working or has a high defeat rate?
**A**: Check the following:
- Ensure the combat strategy is properly selected.
- Ensure the strategy matches your current team lineup.
- Ensure your characters have sufficient artifact/talent investment.
- Ensure "Override Auto Combat Configuration in JS" is checked in Task Scheduler.

##### Q: OCR timed out even though the event was triggered?
**A**:
- Try increasing the OCR timeout setting.
- If the event triggers but no text appears on the left side of the screen, disable "Focused Experience Mode" in the game quest settings.

##### Q: How do I choose the best enemy type?
**A**:
- **Treasure Hoarders**: Best for mid-investment teams; enemies are relatively weak and forgiving.
- **Fatui**: Requires high-investment teams; higher monster strength but faster clear potential.

##### Q: What should I do if the script stops unexpectedly?
**A**:
- Check whether manual input interfered with the game.
- Review BetterGI logs to find the cause of interruption.
- Re-run the script.
- If the problem persists, submit an issue on GitHub.

##### Q: What if the script freezes on a specific step?
**A**:
- Check if the game is stuck on a character revive screen.
- Restart the script and verify BetterGI status.
- If it still fails, submit an issue.

##### Q: Treasure Hoarders vs. Fatui: which should I choose?
**A**:
- **Beginner recommendation**: Treasure Hoarders (lower enemy HP and high error tolerance).
- **High-investment teams**: Fatui (higher efficiency).
- **Companionship EXP priority**: Both give the same Companionship EXP per event; choose whichever matches your team best.

##### Q: How do I configure combat strategies?
**A**:
- Refer to the official BetterGI documentation.

##### Q: Why did the Random Event fail to trigger?
**A**:
- Check if you have reached the daily 10-reward / 50-trigger event cap.
- Try triggering it manually once to verify.

##### Q: What if party switching fails?
**A**:
- Ensure your party name matches your game configuration exactly (e.g. four Chinese characters on CN client or exact name on EN client).

##### Q: How can I speed up script execution?
**A**:
- Lower OCR timeout slightly (not too low).
- Optimize your combat strategy to eliminate redundant pauses.
- Keep BetterGI updated to the latest version.
- Ensure adequate PC hardware performance and stable network connectivity.

##### Q: How do I back up and restore configuration?
**A**:
- Settings are saved in the Task Scheduler configuration files.
- Back up those files or copy the entire `User` folder.
- Restore the files to the original folder after reinstalling.

> 💡 For any other issues, please open an issue on GitHub.

---

### File Structure

- `main.js`: Core script logic
- `settings.json`: Configuration definition file
- `assets/AutoPath/`: Pathing files directory
  - `Treasure Hoarder-准备.json`: Preparation path (Hilichurl clearance)
  - `Treasure Hoarder-触发点.json`: Trigger point path
  - `Treasure Hoarder-Combat点.json`: Combat point path
  - `愚人众-准备.json`: Fatui preparation path (Teleport Waypoint to trigger point)
  - `愚人众-触发点.json`: Fatui trigger point path
  - `愚人众-Combat点.json`: Fatui combat point path

---

### Precautions / Notes

#### Usage Notice
- **Educational / Research Only**: This script is provided solely for technical research and learning.
- **Use at Your Own Risk**: Using automation scripts carries potential risks; please use responsibly.
- **Moderate Usage**: Maintain healthy gaming habits and avoid excessive reliance on automation.

#### Safety Recommendations
- **Supervise Execution**: Monitor the initial run to address unexpected game states promptly.
- **Keep Updated**: Keep BetterGI and your scripts updated to the latest versions.
- **Community Feedback**: Report issues to help maintain and improve the script.

---

### Changelog

| Version | Update Notes |
|---|---|
| **v2.0.0** | `main.js` refactor: Resolved V8 popup errors and memory leak issues; unified enemy configuration driver and main loop; explicitly enabled "Disable asynchronous combat" across all enemies; removed time window scheduling features and obsolete configuration entries. |
| **v1.5.3** | Stability improvements: Complete resource cleanup; swimming statistics limited to Treasure Hoarders; added timeout protection to "Disable asynchronous combat" to prevent hangs; improved settings descriptions. |
| **v1.4.2** | Added pickup mode toggle to allow disabling item pickup. |
| **v1.3** | Added Fatui support; optimized enemy type switching. |
| **v1.2** | Added combat trigger detection and asynchronous combat completion check. |
| **v1.1** | Optimized Treasure Hoarders relog feature; added time-window scheduling. |
| **v1.0** | Initial release: basic Treasure Hoarders Companionship EXP farming. |

---

### Contribution Guide
Pull Requests to improve this script are welcome! Please follow these guidelines:

#### Code Contributions
- **Feature Enhancements**: New features, performance optimization, bug fixes.
- **Documentation**: README improvements, code comments, usage guides.
- **Testing & Verification**: Test cases, compatibility testing across resolutions.

#### Submission Standards
- Clear commit messages describing changes.
- Detailed PR description with testing evidence.
- Adhere to the existing code style.
- Avoid mass auto-formatting unrelated code in the same commit.

### Issue Feedback
When filing a GitHub issue, please include:
- Detailed bug description and reproduction steps.
- Relevant log files, screenshots, or error messages.
- BetterGI version and OS environment.
- Configured script parameters.

### Community Support
- 📖 **Documentation**: Read full guides and tutorials.
- 🐛 **Report Issues**: Submit bugs and feature requests via Issues.
- 🤝 **Contribute**: Submit code via Pull Requests.

> 💝 **Thank you to all developers and testers who contributed to this project!**  
> 🌟 **If this script helped you, please consider giving it a star on GitHub!**
