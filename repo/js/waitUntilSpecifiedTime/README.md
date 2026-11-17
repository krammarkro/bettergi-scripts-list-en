# Wait Until Specified Time

---

## 1. Feature Description

**Waits until a specific target timestamp, rather than waiting for a fixed duration!**

The sole task of this script is to hold execution until a specified time:
- Remains in a waiting state until the target time arrives.
- Automatically finishes when the target time is reached.
- Ensures subsequent queued tasks start only after your scheduled time.

**Periodic Status Reports**
- Automatically logs remaining wait time every 5 minutes.
- Keeps you informed of script progress at all times.

---

## 2. Usage

1. Add the script to a Configuration Group.
2. Right-click the script → Edit Custom Configuration.
3. Configure your target time.

### Example Scenarios

| Current Time | Target Time | allowNextDay | Result |
|---|---|---|---|
| 03:00 | 04:00 | false | Waits 1 hour, completes at 04:00 today |
| 04:30 | 04:00 | false | Target time passed, exits immediately (skipped) |
| 04:30 | 04:00 | true | Waits until 04:00 tomorrow (~23.5 hours) |

---

## 3. Precautions / Notes

- When the target time is earlier than the current time, it can wait until the following day if enabled.
- Example:
  - Current time: 04:00
  - Target time: 03:55
  - Wait duration: 23 hours 55 minutes (03:55 the next day)

**Always set a target time; otherwise, the script will not run!**

### Changelog

### 1.6.3 (2025-10-15)
Added `allowNextDay` configuration setting (checkbox in settings) to control whether to wait until the same time "tomorrow" when the target time has already passed today.
- If you want the script to continue waiting until tomorrow when today's target time has already elapsed, enable "Wait until tomorrow if target time has passed today" in settings.
- If unchecked, the script skips immediately to prevent unintentionally blocking the Task Scheduler.
- When the target time has passed, choose between waiting until tomorrow (optional) or exiting immediately (default).
