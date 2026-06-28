# LOOM 2.1.20 RC2

Published: 2026-06-29

## What Changed

- Fixed one-click online installer failure when installing or upgrading into a D: drive target while the temporary download directory is on C:.
- Existing install directories are now backed up beside the target install directory, so Windows does not need to move folders across volumes.
- User data under `LOOMFiles/data` is still restored after an overwrite install.

## Packages

- Online package: `rc/packages/LOOM-Online-v2.1.20-20260629-rc2.zip`
- Online package SHA256: `018059BEAC8DED227353045355374BDC917510C40C7FD5240A9C19EB06C7722E`
- One-click installer: `rc/packages/LOOM-Online-Setup-v2.1.20-20260629-rc2.exe`
- One-click installer SHA256: `AAFEEFA242B26D2D497BDB4183D49CE89629FD7EFA8D887E9AE68440021F6F44`

## Verification

- Reproduced the problematic shape locally: installer temp/download path on C:, existing install target under `D:\Axiangmu\AUSTART\artifacts\installer-smoke-cross-volume-rc2\Probe`.
- Silent overwrite install returned exit code `0`.
- Verified `LOOM.exe`, `LOOMFiles/_up_/python/bridge.py`, and `LOOMFiles/data/launcher_runtime.json` after install.
- Verified a pre-existing `LOOMFiles/data/user-sentinel.txt` was preserved after overwrite install.
- Verified the installed Python bridge imports successfully.

## Notes

- Stable channel is intentionally unchanged. Use rc2 for the next cross-machine test.
