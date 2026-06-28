# LOOM v2.1.19 rc1

Channel: rc
Package: LOOM-Online-v2.1.19-20260628-rc1.zip
Online SHA256: D10CC33B37876E10B1A198A749517F758AF3B44B8C6089EED991A7364B103D45

Contents:
- Online launcher package with LOOM.exe and LOOMFiles shell.
- Runtime layers: node, openclaw-deps, python-runtime.
- Heavy runtime layers are downloaded through rc/release-manifest.json on first run.
- No real account, password, API key, private key, or phone token is bundled.

Known limits:
- This is rc for first external machine testing; stable channel is not promoted yet.
- First run requires network access to GitHub raw layer URLs.
- Phone control still requires a paired phone endpoint and token supplied by the tester.

Rollback:
- Delete the extracted LOOM-Online-v2.1.19-20260628-rc1 folder.
- Use LOOM-Portable-v2.1.19-20260628-rc1.zip for offline fallback.
- Revert this release-channel commit or restore the previous rc/release-manifest.json if layer download fails.

Local evidence:
- verify-release passed for portable directory and zip.
- verify-portable-smoke passed for portable directory.
- verify-installer-manifest passed for root installer manifest.
- Online package shape check passed: no node/node_modules/python-runtime/OpenClawFiles/python tests in package.
