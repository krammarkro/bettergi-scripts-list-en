# Switch Party (BgiTools Edition)

## Introduction

This script automatically switches party setups in Genshin Impact within BetterGI. It supports two loading modes:

- **Manual Input**: Manually specify party names in settings; the script directly switches to them.
- **BgiTools API Loading**: Queries the active party setup corresponding to the current UID via BgiTools HTTP API, then automatically performs the switch (requires JS HTTP permissions).

## Features

- Supports both manual input and BgiTools API party fetching
- Automatically detects active game UID and queries target party configurations
- On party switch failure, automatically teleports to a Statue of The Seven and retries
- Supports custom auth token name and value
- Comprehensive logging and error notifications

## Directory Structure

```text
SwitchParty/
├── main.js                 # Script entry point
├── manifest.json           # BetterGI manifest file
├── settings.json           # Settings UI configuration
└── README.md               # User guide and documentation
```

## Configuration

| Setting | Type | Description | Default |
| --- | --- | --- | --- |
| `loadMode` | Select | `input` (Manual) or `bgi_tools` (API) | `input` |
| `partyName` | Text | Name of target party preset when in manual mode | `Team 1` |
| `apiUrl` | Text | BgiTools HTTP endpoint URL | `http://127.0.0.1:8000/api/party` |
| `token` | Text | API authentication token if required | `""` |
