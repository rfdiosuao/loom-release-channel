# LOOM 2.1.19 RC7

Published: 2026-06-29

## What Changed

- Startup splash now loads the LOOM/麓鸣 `logo_motion_single.html` motion asset directly.
- Removed the forced splash loop parameter so the animation no longer restarts mid-motion.
- The online installer directory page now clearly separates the install location from the temporary download cache.
- The rc manifest now points to the rc7 online package and one-click online setup exe.

## Packages

- Online package: `rc/packages/LOOM-Online-v2.1.19-20260629-rc7.zip`
- Online package SHA256: `595444602045D762A7546413977C50154A0339526EA904110C187C5485A528A6`
- One-click installer: `rc/packages/LOOM-Online-Setup-v2.1.19-20260629-rc7.exe`
- One-click installer SHA256: `068E00BD3FD1ECDA7DFF4040E59190C86ED134F20EC5DB438605253D17F3F6A4`

## Verification

- `npm run build` passed in `openclaw_new_launcher`.
- `scripts/build-portable.ps1` passed for `LOOM-Portable-v2.1.19-20260629-rc7`.
- `scripts/build-online-portable.ps1` passed for `LOOM-Online-v2.1.19-20260629-rc7`.
- `scripts/build-online-exe-installer.ps1` passed for `LOOM-Online-Setup-v2.1.19-20260629-rc7.exe`.
- Installer directory-page screenshot captured at `D:\Axiangmu\AUSTART\artifacts\installer-ui-rc7-dir-temp-cache.png`.
