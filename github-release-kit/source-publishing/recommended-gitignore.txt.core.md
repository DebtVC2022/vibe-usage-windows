---
source: "个人/个人探索尝试/vibe-usage-windows/github-release-kit/source-publishing/recommended-gitignore.txt"
core_kind: "business_material"
file_type: "txt"
generated: "2026-06-22T16:25:17"
doc_role: source
doc_status: active
doc_authority: supporting
doc_confidentiality: internal
doc_rule: wiki-doc-governance-v1
tags:
  - core-file
  - business-material
  - txt
  - doc/role/source
  - doc/status/active
  - doc/authority/supporting
  - doc/confidentiality/internal
  - doc/rule/wiki-doc-governance-v1
---
<!-- CORE_FILE_NOTE_V1 -->
# recommended-gitignore.txt

- Source file: [[个人/个人探索尝试/vibe-usage-windows/github-release-kit/source-publishing/recommended-gitignore.txt|recommended-gitignore.txt]]
- Folder index: [[个人/个人探索尝试/vibe-usage-windows/github-release-kit/source-publishing/资料索引|资料索引]]
- Core kind: `business_material`
- Size: 339 B
- Modified: 2026-06-22T16:22:07

## Summary
- TXT sample: 17 lines, 323 chars.
- Opening: # Recommended root .gitignore if publishing this project from the vibe-usage-windows root.
- Keywords: root, publishing, dist, tauri, 资料索引, Recommended, gitignore, project, vibe, usage

## Related files
- [[个人/个人探索尝试/vibe-usage-windows/github-release-kit/source-publishing/upload-checklist|upload-checklist.md]] - same folder

## Graph tags
- #core-file/business-material
- #file-type/txt

## Content preview
```text
# Recommended root .gitignore if publishing this project from the vibe-usage-windows root.

app/node_modules/
app/dist/
app/dist-installer/
app/src-tauri/target/
app/src-tauri/gen/

*.log
*.tmp
*.zip
*.exe

# Personal Obsidian graph files. Keep private unless intentionally publishing them.
资料索引.md
**/资料索引.md
**/*.core.md
```

## Processing notes
- encoding=utf-8-sig
