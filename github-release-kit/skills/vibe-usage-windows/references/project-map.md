# Project map

The project is a Windows desktop app with a React frontend and Rust Tauri backend.

## Main layout

```text
app/
  package.json
  src/
    App.tsx
    api/usageApi.ts
    components/
    types/usage.ts
    utils/format.ts
  src-tauri/
    Cargo.toml
    tauri.conf.json
    src/
      aggregate.rs
      codex_parser.rs
      commands.rs
      csv_export.rs
      domain.rs
      lib.rs
      main.rs
      workbuddy_parser.rs
    tests/
      aggregate_tests.rs
      command_tests.rs
      csv_export_tests.rs
      parser_tests.rs
  installer/
    vibe-usage-windows.nsi
  scripts/
    build-local-installer.ps1
  dist-installer/
    VibeUsageWindowsSetup-0.1.0.exe
docs/
  superpowers/specs/
  superpowers/plans/
github-release-kit/
```

## Responsibilities

- `codex_parser.rs`: Recursively reads Codex JSONL sessions and extracts token snapshots.
- `workbuddy_parser.rs`: Opens WorkBuddy SQLite in read-only mode and extracts `session_usage` rows joined to `sessions`.
- `aggregate.rs`: Builds dashboard summaries, trends, rankings, and recent sessions.
- `commands.rs`: Exposes Tauri commands and default paths.
- `csv_export.rs`: Writes normalized usage records to CSV.
- `src/App.tsx`: Coordinates UI state, refresh, filters, settings, and export.

## Public release boundaries

Source repositories should include source files and tests, not generated dependencies or build output.

Keep these out of source publication:

```text
app/node_modules/
app/dist/
app/dist-installer/
app/src-tauri/target/
*.zip
*.exe
```

Installer `.exe` files belong in GitHub Releases, not source control.
