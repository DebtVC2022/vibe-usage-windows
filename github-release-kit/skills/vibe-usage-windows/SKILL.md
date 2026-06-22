---
name: vibe-usage-windows
description: Use when working on Vibe Usage Windows, the local Windows Tauri dashboard for Codex and WorkBuddy usage. Trigger for tasks that inspect, run, test, package, release, troubleshoot, or document this app, especially Codex token parsing, WorkBuddy SQLite parsing, NSIS installer builds, GitHub release preparation, and local usage dashboard maintenance.
---

# Vibe Usage Windows

## Overview

Use this skill to maintain, package, or troubleshoot Vibe Usage Windows. The app is a local Windows desktop dashboard that reads Codex JSONL sessions and WorkBuddy SQLite usage data in read-only mode.

## Quick workflow

1. Locate the repository or ask for it if unknown. On the original machine it lives under a `vibe-usage-windows` folder with an `app` subfolder.
2. Read `references/project-map.md` for layout before changing files.
3. Read `references/commands.md` before running tests, builds, or packaging.
4. Read `references/data-sources.md` before changing parsers or investigating zero usage.
5. Keep source data read-only. Do not modify `.codex` sessions or the WorkBuddy database.
6. Run targeted verification before saying the app, parser, installer, or release package works.

## Common tasks

### Run local verification

Use PowerShell and prefer `npm.cmd`:

```powershell
cd app
npm.cmd run test
npm.cmd run build
cd src-tauri
cargo test
```

If `cargo` is not found:

```powershell
$env:PATH="$HOME\.cargo\bin;$env:PATH"
cargo --version
```

### Build the local installer

```powershell
cd app
npm.cmd run installer:local
```

Expected output:

```text
app\dist-installer\VibeUsageWindowsSetup-0.1.0.exe
```

### Troubleshoot Codex token count showing zero

Check these first:

- Configured sessions path points at `%USERPROFILE%\.codex\sessions`.
- Parser supports `payload.info.total_token_usage` and `payload.info.last_token_usage`.
- Regression test in `app\src-tauri\tests\parser_tests.rs` covers real `event_msg` token records.

Do not scan or summarize prompt/response text. Only count usage metadata.

### Prepare GitHub release

Use the release kit folder if present:

```text
github-release-kit
```

Expected release assets:

```text
release-assets\VibeUsageWindowsSetup-0.1.0.exe
vibe-usage-windows-skill.zip
release-notes-v0.1.0.md
checksums.txt
```

Do not publish `node_modules`, `app\dist`, `app\dist-installer`, `app\src-tauri\target`, or private Obsidian index files as source.

## Guardrails

- Treat Codex and WorkBuddy source data as read-only.
- Do not claim WorkBuddy credit equals token count.
- Keep release docs factual. Avoid marketing claims that cannot be verified locally.
- If editing code, add or update tests first unless the change is pure documentation or packaging metadata.
- Verify generated zip and installer paths exist before reporting completion.

## References

- `references/project-map.md`: repository layout and important files.
- `references/commands.md`: build, test, install, and release commands.
- `references/data-sources.md`: parser behavior, privacy rules, and troubleshooting cues.
