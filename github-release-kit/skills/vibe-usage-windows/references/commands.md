# Commands

Use PowerShell on Windows. Prefer `npm.cmd` because `npm.ps1` can be blocked by execution policy.

## Frontend

```powershell
cd app
npm.cmd install
npm.cmd run test
npm.cmd run build
npm.cmd run tauri dev
```

## Rust backend

```powershell
cd app\src-tauri
cargo test
cargo fmt -- --check
```

If Cargo is not on PATH:

```powershell
$env:PATH="$HOME\.cargo\bin;$env:PATH"
cargo --version
```

## Local installer

Install NSIS:

```powershell
winget install --id NSIS.NSIS -e
```

Build installer:

```powershell
cd app
npm.cmd run installer:local
```

Expected output:

```text
app\dist-installer\VibeUsageWindowsSetup-0.1.0.exe
```

Silent install for local verification:

```powershell
Start-Process -FilePath "app\dist-installer\VibeUsageWindowsSetup-0.1.0.exe" -ArgumentList "/S" -Wait
```

Installed app path:

```text
%LOCALAPPDATA%\Programs\Vibe Usage Windows\vibe-usage-windows.exe
```

## Release package

From the project root, copy the installer into the release kit:

```powershell
Copy-Item -LiteralPath "app\dist-installer\VibeUsageWindowsSetup-0.1.0.exe" -Destination "github-release-kit\release-assets\VibeUsageWindowsSetup-0.1.0.exe" -Force
```

Zip the skill folder:

```powershell
Compress-Archive -LiteralPath "github-release-kit\skills\vibe-usage-windows" -DestinationPath "github-release-kit\vibe-usage-windows-skill.zip" -Force
```

Generate checksums:

```powershell
Get-FileHash "github-release-kit\release-assets\VibeUsageWindowsSetup-0.1.0.exe","github-release-kit\vibe-usage-windows-skill.zip" -Algorithm SHA256
```
