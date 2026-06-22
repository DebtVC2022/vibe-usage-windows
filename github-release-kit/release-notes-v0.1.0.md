# Vibe Usage Windows v0.1.0

First local Windows release.

## What is included

- Windows desktop dashboard for local Codex and WorkBuddy usage.
- Codex JSONL parser for local session files.
- WorkBuddy SQLite parser for local usage records.
- Dashboard metrics for today, 7 days, 30 days, and all time.
- Trend chart, model ranking, project ranking, recent sessions, warnings, settings, and CSV export.
- Local NSIS installer.
- Parser fix for real Codex token records stored under `payload.info.total_token_usage` and `payload.info.last_token_usage`.

## Install

Download and run:

```text
VibeUsageWindowsSetup-0.1.0.exe
```

Default install path:

```text
%LOCALAPPDATA%\Programs\Vibe Usage Windows
```

## Default data paths

```text
%USERPROFILE%\.codex\sessions
%USERPROFILE%\.workbuddy\workbuddy.db
```

Both paths can be changed in the app settings panel.

## Notes

- Windows only.
- Source files are read-only.
- The app does not require cloud credentials.
- WorkBuddy credit fields are displayed as WorkBuddy usage, not as Codex token counts.
- The installer is unsigned, so Windows SmartScreen may show a warning.
