# LOOM v2.1.19 rc3

Channel: rc
Package: LOOM-Online-v2.1.19-20260628-rc3.zip
Online SHA256: F3E4F4013C9272B197F8CFA6FBFA2ED3DF92216E80BE0132813E627A248FBD9C
One-click installer: LOOM-Online-Setup-v2.1.19-20260628-rc3.exe
Installer SHA256: 953D051EDD791284096E9A58A1348AB8422693FED09EE3B15B715E2581E27629

Fix:
- Includes LOOMFiles/_up_/python-runtime in the online package so the Python Bridge starts with the bundled runtime.
- Prevents the launcher from falling back to a random system Python when the packaged Bridge is used.
- Fixes the rc2 failure: `ImportError: DLL load failed while importing _rust` from `cryptography`.

Contents:
- Online launcher package with LOOM.exe and LOOMFiles shell.
- Bundled Python Bridge runtime.
- Node.js and LOOM runtime dependencies still download through rc/release-manifest.json on first run.
- Current LOOM/Luming app icon, taskbar icon, splash animation, top-left brand, and theme logo are retained.
- One-click online installer downloads the rc3 zip, verifies SHA256, installs into the current user's profile, creates shortcuts, and starts LOOM.
- No real account, password, API key, private key, or phone token is bundled.

Known limits:
- This is rc for first external machine testing; stable channel is not promoted yet.
- First run still requires network access to GitHub raw layer URLs for Node.js and node_modules.
- Phone control still requires a paired phone endpoint and token supplied by the tester.

Rollback:
- Delete the extracted LOOM-Online-v2.1.19-20260628-rc3 folder.
- rc2 is superseded because it can fail on machines without a compatible Python/cryptography runtime.
- Restore the previous release-channel commit if rc3 needs to be withdrawn.

Local evidence:
- LOOM-Portable-v2.1.19-20260628-rc3.zip passed verify-release and smoke checks.
- LOOM-Online-v2.1.19-20260628-rc3.zip passed online shape checks and installer manifest validation.
- Direct Bridge smoke passed with bundled Python: `BRIDGE_PORT=18793`.
- Cached distribution manifest inside the online package contains only mirrors/layers, not stale package metadata.
- One-click installer smoke passed with `/silent /install-dir ... /no-launch /no-shortcuts`; installed Bridge smoke returned `BRIDGE_PORT=18793`.
