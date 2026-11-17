# Account Switch Tool Instructions

## Quick Start

### Method 1: Account Image Recognition (Recommended)

1. **Prepare Account Images**
   - **Recommended Method**: Use the script's "Screenshot Mode" to automatically capture and save account screenshots (see the Screenshot Mode section for details).
   - **Manual Method**: Place account screenshots in the `accounts/` directory.
   - Name images as `{UID}.png`, for example `284073800.png`.
   - The screenshot should clearly include identifiable features of that account on the account selection screen.

2. **Configure Script**
   - Open the BetterGI configuration panel.
   - Fill in the target account's UID.
   - Ensure "Skip search and directly enter account/password" is unchecked.

3. **Run Script**
   - The script will automatically navigate to the account selection screen.
   - Recognize and click the corresponding account image.
   - Automatically enter the game and return to the main interface.

### Method 2: Account & Password Input

1. **Configure Script**
   - Open the BetterGI configuration panel.
   - Fill in the target account's UID (used for notifications).
   - Enter your account username and password.
   - Check "Skip search and directly enter account/password".

2. **Run Script**
   - The script will automatically navigate to the account/password login screen.
   - Automatically click the agreement button and enter credentials.
   - Automatically enter the game and return to the main interface.

### Notes
- **Both methods can be used together**: Method 2 acts as a fallback for Method 1. If image recognition fails, it will automatically fall back to the account/password method.
- **Recommended Configuration**: Configure account & password as a backup to maximize switch success rate.

## Screenshot Mode

Screenshot Mode is an auxiliary feature used to automatically capture and save account images, making it easy to switch using the image recognition method later.

**Steps**:
1. **Configure Script**
   - Open the BetterGI configuration panel.
   - Enter the target account UID (prioritized for naming the screenshot).
   - Check "Screenshot Mode".

2. **Run Script**
   - The script prioritizes using the configured "Target Account UID" to name the image.
   - If left blank, it will attempt to automatically detect the current account's UID.
   - Navigates to the account selection screen.
   - Automatically captures and saves the account image.
   - Returns to the main interface and sends a success notification.

**Save Location**:
- Images are saved in the `accounts/` directory.
- File naming format: `{UID}.png`.

## Configuration Guide

Configure the following settings in the BetterGI configuration panel:

### 1. Target Account UID
- Enter the UID of the account to switch to.
- Used to match account image filenames, display notifications, and name screenshots in Screenshot Mode.

### 2. Account (Optional)
- Fallback credential when the account cannot be recognized via image.
- Recommended to fill in as a backup.

### 3. Password (Optional)
- Fallback credential when the account cannot be recognized via image.
- Recommended to fill in as a backup.

### 4. Skip Search and Directly Enter Account/Password
- **Checked**: Skips searching for account images and logs in directly with username/password.
- **Unchecked**: Prioritizes image recognition, falling back to credentials on failure.

### 5. UID Validation
- **Checked**: Checks current account UID before and after switching to verify success.
- **Unchecked**: Skips UID validation.

### 6. Stop Configuration Group on UID Verification Failure
- **Checked**: Automatically terminates the entire configuration group if UID verification fails (requires configuring Stop Shortcut Key).
- **Unchecked**: Only logs errors without interfering with subsequent tasks.
- **Stop Shortcut Key**: Enter virtual key codes in `VK_` format (e.g., `VK_F8`), matching your BetterGI global settings.

### 7. Screenshot Mode
- **Checked**: Enters screenshot mode to automatically capture and save the account image for the specified UID.
- **Unchecked**: Executes the standard account switching workflow.

## FAQ

### Q: What should I do if account image recognition fails?
A: Make sure:
1. Images are placed in the `accounts/` directory.
2. Images are named with the correct UID format (`{UID}.png`).
3. Screenshots are clear and contain distinguishable account identifiers.
4. Account credentials are configured as a fallback.

### Q: What should I do if prompted "Account image does not exist and credentials are not configured"?
A: The script checks whether the account image exists before switching. This prompt indicates:
1. `accounts/{UID}.png` does not exist or cannot be read (images might have been cleared after updating the script).
2. No account credentials have been configured as a fallback.

### Q: What happens if switching fails?
A: The script attempts to return to the main interface and sends a failure notification. If credentials were configured, it is recommended to manually check the account status.

### Q: Why do I need to enter a UID?
A: UID is used to:
1. Determine the account image filename.
2. Display account information in notifications.
3. Name saved image files in Screenshot Mode.

## Precautions

1. It is recommended to test the switching process manually once before first use.
2. Ensure the game resolution is set to 1920x1080.
3. Account screenshots should clearly capture recognizable account elements on the selection screen.
4. Passwords are not displayed while being entered; this is normal.
5. In Screenshot Mode, the target UID setting is used by default; if unset, it attempts auto-detection.
6. **Updating or resubscribing to the script may clear images in the `accounts/` directory**. Please re-add account images or configure backup credentials after updating.

## Feedback

If you encounter unexpected popups or issues that the script cannot handle:

1. **Take a full-screen screenshot**: Ensure the entire game window and popup are visible.
2. **Contact Author**: QQ 718135749.
3. **Provide info**: Briefly describe the issue and reproduction steps.

Thank you for your support!

<details>
<summary>Project Overview (Click to expand)</summary>

## Project Overview

An automated account switching script based on a finite state machine (FSM), supporting Genshin Impact account switching via image recognition or manual credential input.

### Features

- **Dual-Mode Switching**: Supports automatic image recognition and manual credential input.
- **State Machine Management**: Uses a finite state machine for reliable switching flow control.
- **Auto-Recovery**: Attempts to return to the original account upon failure.
- **Notifications**: Sends system notifications on success or failure.
- **Loop Protection**: Prevents getting stuck in infinite state loops.
- **UID Verification**: Supports pre- and post-switch UID checks for accuracy.
- **Smart Termination**: Automatically stops configuration group execution on UID mismatch.
- **Screenshot Mode**: Automatically captures and saves account images for future switches.

### Directory Structure

```
AccountSwitchStateMachine/
├── main.js                    # Main script
├── manifest.json              # Script manifest
├── settings.json              # Configuration definition
├── assets/
│   ├── states.json            # State machine configuration
│   └── RecognitionObjects/    # State recognition template images
│       ├── Paimon.png
│       ├── Menu.png
│       ├── PrepareToLogOut.png
│       ├── SwitchAccount.png
│       ├── Exit.png
│       ├── EnterGame.png
│       ├── LoginOther.png
│       ├── SelectAccount.png
│       ├── EnterAccountAndPassword.png
│       ├── Agree.png
│       ├── EnterAccount.png
│       ├── EnterPassword.png
│       ├── EnterGame2.png
│       ├── Login.png
│       └── Confirm.png
└── accounts/                  # Account screenshots directory
    └── {uid}.png              # Account screenshot named by UID
```

### Workflow

```
Start
│
├─► Screenshot Mode (if enabled)
│   ├─► Use configured UID or detect current UID
│   ├─► Navigate to account selection screen
│   ├─► Capture and save account image
│   └─► Return to main interface
│       ├─► Success → Send success notification
│       └─► Failure → Send failure notification
│
├─► Pre-checks (verify account image exists or credentials configured)
│   ├─► Image exists → Proceed
│   └─► Image missing & no credentials → Terminate and prompt
│
├─► Image Recognition Method (if skip is unchecked)
│   ├─► Preload account image
│   ├─► Switch to account selection screen
│   ├─► Find and click account image
│   └─► Transition to main interface
│       ├─► Success → Send success notification
│       └─► Failure → Fall back to credential login
│
└─► Credential Login Method
    ├─► Check credentials
    ├─► Switch to login input screen
    ├─► Click Agree button
    ├─► Enter username & password
    ├─► Click Enter Game
    └─► Transition to main interface
        ├─► Success → Send success notification
        └─► Failure → Attempt return to original account → Send failure notification
```

### State Descriptions

| State Name | Description |
|------------|-------------|
| mainUI | Main game interface (Paimon icon visible) |
| menuUI | Pause menu (ESC menu) |
| prepareToLogOut | Log out confirmation screen |
| loginScreen | Login title screen (Switch Account button) |
| exitAccount | Account logout screen |
| enterGame | Enter game / Log in to another account screen |
| selectAccount | Account selection screen |
| enterAccountAndPassword | Account & password input screen |
| noAccount | Unregistered / no account screen |

### Changelog

#### v1.2
- **New**: Pre-switch check for account image existence; terminates early with a prompt if missing without credentials configured, avoiding mid-flow errors.

#### v1.1
- **New**: Auto-terminate configuration group on UID verification failure, with configurable shortcut keys.
- **Optimization**: Refined recognition conditions for account/password input screen to fix potential false matches.

#### v1.0
- Initial release.
- State machine management implemented.
- Supports both image recognition and credential login.
- Added auto-return and notification features.

</details>