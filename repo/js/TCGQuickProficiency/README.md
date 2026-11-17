Have you ever spent hours playing against sluggish NPCs just to collect character card dynamic holographic skins?

Have you ever watched drawn-out card animations and lamented the waste of time?

Here it is, powered by BetterGI, rolling right up to you!

## Instructions

This script leverages Co-Op card duels to rapidly level up Genius Invokation TCG Character Card Proficiency. You need two game accounts: the account gaining proficiency (referred to below as the **Main Account**), and the account surrendering in matches (referred to below as the **Alt Account**).

[Click here to view a video demonstration](https://github.com/babalae/bettergi-scripts-list/pull/1282)

**Note: Farming proficiency via surrendering generates consecutive match records. If you are concerned about account risks from repeated surrenders, please do not use this script.**

> Before running, ensure you have set a hotkey in BetterGI's `Hotkeys` settings for `Stop Current Script`.

1. Have your Alt Account apply to join your Main Account's world in 2-player Co-Op mode.
2. **Optional**: If you have two computers, run this script on the PC logged into your Alt Account with the mode `As Helper Account: Fast Surrender`.  
   If you have only one PC, log into the Alt Account on a mobile device or tablet, manually accept duel invites from the Main Account, and forfeit quickly once the match begins.
3. On the PC logged into your Main Account, run this script. For the first run, selecting `Scan Current Account Card Proficiency` mode is recommended. Scanned data will be used to suggest characters for upcoming farming sessions.
4. On the PC logged into your Main Account, run the script in `As Main Account: Fast Proficiency Farming` mode.
5. Once proficiency for the current deck is maxed out, the script suggests the next set of characters. Manually drag-and-drop the unmaxed cards into your active deck, then simply re-run the script (it detects key game screens and automatically calculates necessary actions, avoiding redundant teleports or prompts).

## FAQ

- **What if I only have one computer?**  
  Genshin Impact does not allow running multiple client instances on a single physical PC, even across separate Windows user accounts.  
  In this case, manually operate surrenders on your Alt Account (see [Instructions](#instructions)). Since the host account requires more complex dialogue and interaction steps, using the script to automate the Main Account is recommended.  
  Alternatively, you can partner with other players in community groups who also want to farm proficiency, taking turns forfeiting for each other. [View Community Info](https://bettergi.com/community.html).

- **Can I run one standard client and one Cloud Genshin client simultaneously on one PC?**  
  BetterGI does not launch a second instance when an active instance is detected. Attempts to run dual BetterGI instances across separate Windows user accounts also encounter screen-capture conflicts.  
  Therefore, this is currently not viable (if you find a workable solution, feedback on [GitHub](https://github.com/babalae/bettergi-scripts-list/issues) is welcome; feel free to mention `@Patrick-Ze`).

- **Can it automatically swap in unmaxed characters once current characters reach max proficiency?**  
  The Genius Invokation TCG deck builder interface does not display card names as text, and bottom deck slots do not scroll with card detail pages. Swapping cards requires manual dragging and dropping. Supporting automated swapping would require comprehensive template matching across every character card in the game.  
  Consequently, this feature is not supported and is not planned for future development.
