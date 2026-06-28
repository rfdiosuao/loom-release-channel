# LOOM v2.1.19 rc2

Channel: rc
Package: LOOM-Online-v2.1.19-20260628-rc2.zip
Online SHA256: 8FA04372F3EFBCA044B5625E65D2CCC7E9A2DA5CC573FBA615C163323B53A45A

Contents:
- Online launcher package with LOOM.exe and LOOMFiles shell.
- Rebuilt LOOM.exe from the latest Tauri output so the app icon, taskbar icon, splash animation, and top-left LOOM/Luming brand are included.
- Theme package logos for default and loom now match the LOOM/Luming app icon.
- Runtime layers remain provided through rc/release-manifest.json on first run.
- No real account, password, API key, private key, or phone token is bundled.

Known limits:
- This is rc for first external machine testing; stable channel is not promoted yet.
- First run requires network access to GitHub raw layer URLs.
- Phone control still requires a paired phone endpoint and token supplied by the tester.

Rollback:
- Delete the extracted LOOM-Online-v2.1.19-20260628-rc2 folder.
- Use LOOM-Online-v2.1.19-20260628-rc1.zip only as a previous package fallback; rc1 is known to contain an older launcher executable.
- Restore the previous rc/release-manifest.json or checkout commit 34519fd if rc2 needs to be withdrawn.

Local evidence:
- verify-release passed for LOOM-Portable-v2.1.19-20260628-rc2.zip.
- verify-installer-manifest passed for the rc2 online package payload.
- git diff --check passed in the launcher repository.
- Online package shape check passed: no node/node_modules/python-runtime heavy layers in the online zip.
- Visual evidence captured in D:\Axiangmu\AUSTART\artifacts\branding-rc2.
