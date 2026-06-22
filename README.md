# Vibe Usage Windows GitHub release kit

This folder collects the files needed to publish the current Windows build and a companion Codex Skill.

## Contents

```text
README.md
release-notes-v0.1.0.md
checksums.txt
release-assets/
  VibeUsageWindowsSetup-0.1.0.exe
skills/
  vibe-usage-windows/
vibe-usage-windows-skill.zip
vibe-usage-windows-github-release-kit.zip
source-publishing/
  recommended-gitignore.txt
  upload-checklist.md
```

`checksums.txt` records the installer and Skill zip hashes. `github-release-kit-sha256.txt` records the full release-kit zip hash after packaging.

`github-release-kit-sha256.txt` is kept beside `vibe-usage-windows-github-release-kit.zip`. It is not embedded inside that zip, because adding it would change the zip hash.

## GitHub release asset

Upload this installer to GitHub Releases:

```text
release-assets\VibeUsageWindowsSetup-0.1.0.exe
```

Use this release title:

```text
Vibe Usage Windows v0.1.0
```

Use `release-notes-v0.1.0.md` as the release body.

## Codex Skill distribution

Upload this zip as a separate release asset:

```text
vibe-usage-windows-skill.zip
```

To install it locally, unzip the archive so the final folder is:

```text
%USERPROFILE%\.codex\skills\vibe-usage-windows
```

After installation, invoke it in Codex with:

```text
Use $vibe-usage-windows to troubleshoot Codex token parsing in my local dashboard.
```

## Source publishing note

If publishing the full source repository, use the root `README.md` in this project. Do not publish dependency folders, build output, local target output, or personal Obsidian indexes unless you intentionally want them public.
