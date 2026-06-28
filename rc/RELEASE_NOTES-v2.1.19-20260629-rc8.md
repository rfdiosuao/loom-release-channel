# LOOM 2.1.19 RC8

Published: 2026-06-29

## What Changed

- Agent detail page now shows one green primary action by state: `安装`, `升级`, or `启动`.
- Removed the confusing legacy Agent action wording from the Agent page.
- `重新检测` is kept as a secondary action instead of competing with the main button.
- `可升级` now has an explicit green `升级` action.
- The remaining yellow/brown warning and shadow treatments were changed to muted green.

## Packages

- Online package: `rc/packages/LOOM-Online-v2.1.19-20260629-rc8.zip`
- Online package SHA256: `8FC4319D633404E8D0A66DF8A9AFE0C21BD2710FA077BDA54EE886DAF5232059`
- One-click installer: `rc/packages/LOOM-Online-Setup-v2.1.19-20260629-rc8.exe`
- One-click installer SHA256: `D646D4171DBCC5B62859D70D69566656D0F78674478EF4657BED0D37FF9A365B`

## Verification

- `npm run build` passed in `openclaw_new_launcher`.
- `scripts/build-portable.ps1` passed for `LOOM-Portable-v2.1.19-20260629-rc8`.
- `scripts/build-online-portable.ps1` passed for `LOOM-Online-v2.1.19-20260629-rc8`.
- `scripts/build-online-exe-installer.ps1` passed for `LOOM-Online-Setup-v2.1.19-20260629-rc8.exe`.
- Raw GitHub download checks returned HTTP 200 for both rc8 package URLs.
- Silent install smoke passed with custom install dir `D:\Axiangmu\AUSTART\artifacts\installer-smoke-rc8\CustomLOOM`.
- Scanned built frontend/source for removed Agent wording and old yellow color constants.
