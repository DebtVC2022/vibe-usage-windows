# Source publishing checklist

Use this if you publish the source code, not just the installer.

## Include

- `README.md`
- `app/package.json`
- `app/package-lock.json`
- `app/index.html`
- `app/vite.config.ts`
- `app/tsconfig.json`
- `app/tsconfig.node.json`
- `app/src/`
- `app/src-tauri/Cargo.toml`
- `app/src-tauri/Cargo.lock`
- `app/src-tauri/build.rs`
- `app/src-tauri/tauri.conf.json`
- `app/src-tauri/capabilities/`
- `app/src-tauri/icons/`
- `app/src-tauri/src/`
- `app/src-tauri/tests/`
- `app/installer/`
- `app/scripts/`

## Exclude

- `app/node_modules/`
- `app/dist/`
- `app/dist-installer/`
- `app/src-tauri/target/`
- generated zip files
- generated installer files
- `docs/superpowers/` unless scrubbed for public release
- personal Obsidian index files unless you intentionally want them public

## Before publishing

Run:

```powershell
cd app
npm.cmd run test
npm.cmd run build
cd src-tauri
cargo test
```

Then build release assets:

```powershell
cd ..
npm.cmd run installer:local
```
