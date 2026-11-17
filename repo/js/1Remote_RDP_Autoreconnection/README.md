# 📋 Log Monitor and Auto-Reconnection Script Guide

**Author: Huoshan**

## 📌 Feature Overview
This script monitors 1Remote's log files in real-time. When a remote connection disconnection is detected (warning `OnRdpClientDisconnected` appears in the log), it automatically executes a reconnection operation to ensure stability of the remote connection.

### ⚡⚡⚡❗ Important Note: This is NOT a BetterGI JS script ❗⚡⚡⚡
### ⚡⚡⚡❗ DO NOT run blindly without reading this guide  ❗⚡⚡⚡
### ⚡⚡⚡❗ Reminder: This is an external Python script    ❗⚡⚡⚡


## 🚀 Environment Requirements
- **OS**: Windows (depends on Windows-specific keyboard shortcuts)
- **Python version**: Python 3.6 or higher  
  (Check method: press `Win+R`, type `cmd`, and run `python --version`)


## 🔧 Installing Dependencies (Important)
1. **Open Command Prompt (CMD) as Administrator**:
   - Method 1: Press `Win + R`, type `cmd`, hold `Ctrl + Shift` and click "OK"
   - Method 2: Search for "Command Prompt" in Start Menu, right-click and choose "Run as Administrator"

2. **Run Installation Command**:  
   Enter the following command in administrator CMD and press Enter:
   ```
   pip install pyautogui watchdog
   ```


## 📂 File Description
| Filename             | Description                                                              |
|----------------------|--------------------------------------------------------------------------|
| `log_monitor.py`     | Core monitoring script; watches log files for disconnect events to trigger reconnect |
| `autoreconnection.py`| Reconnect script; executes auto-reconnect via simulated hotkeys (Win+D, Alt+M, etc.) |
| `config.json`        | Configuration file storing the directory where 1Remote logs are located  |
| `监控Exception / Error.txt`       | Operation log recording error info and reconnect states for troubleshooting |


## 🔍 First-Time Setup
1. Ensure Python 3.6+ and dependencies are installed.
2. Double-click `log_monitor.py` or run in CMD:
   ```
   python log_monitor.py
   ```
3. First launch prompts for the log directory path:
   - Log files are named in the format `1Remote.log_YYYYMMDD.md`
   - Enter the full path of the folder containing 1Remote logs (e.g. `.logs` directory path)

## ⚙️ Configuration Reference
You can manually edit `config.json` to change the log folder path:
```json
{
  "log_dir": "C:\\path\\to\\1Remote\\.logs"
}
```
