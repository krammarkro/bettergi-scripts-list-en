# Anti-Sleep Countdown

**Waits / counts down** on the main game screen while **preventing the computer from entering sleep mode or turning off the display**. Once the target time is reached, the script ends automatically and the Scheduler proceeds to the next task.

Ideal use case: Leaving your PC on overnight to wait until a **version update, the top of the hour, or the 04:00 daily reset** before starting daily routines, without your computer falling asleep during the wait.

> Difference from existing "Wait Until Specified Time" scripts: This script **periodically nudges the camera to keep the operating system awake**, supports a "Relative Countdown" mode, and can be stopped promptly.

---

## I. Feature Overview

- **Two Waiting Modes** (choose one):
  1. **Wait Until Specified Clock Time** (Priority): Enter `HH:mm` (e.g. `04:00`) to wait until that clock time today. If the time **has already arrived or passed today**, it defaults to **ending immediately and proceeding with subsequent tasks** (preventing accidental ~24-hour delays if launched slightly late). To wait for tomorrow instead, set "Wait until tomorrow if target time has passed" to "Yes".
  2. **Relative Countdown**: Enter minutes + seconds (takes effect when the clock time above is blank).
- **Zero Drift**: Constantly evaluated against `target_timestamp − current_timestamp`, maintaining precision across hours and day boundaries without accumulating drift.
- **Anti-Sleep Keep-Awake**: Periodically nudges the camera at set intervals (default: 60s) on the main interface—only adjusts camera angle without moving the character or opening menus—to refresh the OS idle timer and prevent sleep/screen timeout.
- **Interruptible Anytime**: Ticks every second; pressing "Stop" halts execution promptly.
- **Completion Logging & Notifications**: Logs completion details and optionally sends a notification.
- **Optional Welkin Moon Claiming**: Can automatically claim "Blessing of the Welkin Moon" rewards upon completion—preventing the post-reset daily popup from blocking the next automated task. Calls native BetterGI `genshin.blessingOfTheWelkinMoon()`, safely skipping if Welkin is not active.

---

## II. Usage Instructions

1. Add the script to your **Scheduler Configuration Group**, placed **before** the task you want to run next.
2. Right-click the script → Edit Custom Configuration:
   - To "Wait until a clock time": Enter a time like `04:00` into **Wait Until Specified Clock Time**.
   - To "Wait for a specific duration": Leave the clock time blank, and configure **Minutes / Seconds** below.
3. Run the configuration group. The script will wait in place and keep the PC awake, automatically completing when the time arrives, allowing the Scheduler to run subsequent tasks.

### Prerequisites

- Stay on the **main game screen (open world)** before starting, with the character standing still.
- The game window must be active/focused for camera nudges to register.

---

## III. Precautions / Notes

- **Time is based on local system time**. The CN server daily reset occurs at 04:00 GMT+8; ensure your PC clock is accurate.
- **Prevents system sleep and display timeout, NOT Windows Lock Screen**. If your power plan settings are very aggressive (e.g. laptop lid close, low battery forced sleep, corporate domain lockouts), simulated input may not override them. In such cases, set "Sleep" to "Never" in Windows Power Options.
- The keep-awake interval should be **shorter than your system sleep timeout** (e.g., if sleep timeout is 10 minutes, set interval < 600s). The default 60s works for almost all setups.
- This script handles waiting, keeping awake, and claiming Welkin Moon; **it does not handle login, launching the game, or passing announcements**. Ensure the game is already logged in on the main screen.
- Welkin Moon claiming is optional (disabled by default): only enable if you have an active Welkin Moon subscription and the countdown ends after the daily reset.

---

## Changelog

### 1.3
- Added strict validation for "Wait Until Specified Clock Time" (`HH:mm` format); invalid inputs like `04:00:30` fail fast with an error rather than being misinterpreted silently.
- "Wait until tomorrow" now uses `setDate(+1)` by calendar day to avoid daylight saving time (DST) transition offsets.
- Added corresponding unit tests.

### 1.2
- **Fix**: When launched after the target time had already passed today, the script previously postponed to the next day (~24h wait). It now defaults to completing immediately, with a toggle for "Wait until tomorrow if target time has passed" (default: No).
- Added unit tests covering edge cases where launch time >= target time.

### 1.1
- Added optional "Claim Blessing of the Welkin Moon upon completion" feature to prevent daily reset popups from stalling subsequent tasks.

### 1.0
- Initial release: Supports clock time / relative countdown modes, zero-drift timer, periodic anti-sleep keep-awake, prompt stop handling, and completion notifications.
