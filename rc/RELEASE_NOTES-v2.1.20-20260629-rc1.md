# LOOM 2.1.20 RC1

Published: 2026-06-29

## What Changed

- Bumped launcher version to `2.1.20` for a patch release covering installer stability and UI polish.
- Improved Agent detection fallback for Codex, Claude Code, opencode, OpenClaw, and Hermes across common Windows user paths.
- Added retry behavior for transient download and install command failures.
- Added unified centered busy overlays for detection, install, sync, diagnostics, phone screenshot, and screen-reading waits.
- Documented the LOOM semantic versioning policy in the long-term architecture document.

## Packages

- Online package: `rc/packages/LOOM-Online-v2.1.20-20260629-rc1.zip`
- Online package SHA256: `5B0FE98C572623BFD8AEC17D0835245ACE2B40728C5722B4B030661D17B66655`
- One-click installer: `rc/packages/LOOM-Online-Setup-v2.1.20-20260629-rc1.exe`
- One-click installer SHA256: `02090B1DAB8B30013873427C4D61C05BC168A56BEA4D3AF1786037E2725620E5`

## Verification

- `scripts/verify-version-consistency.ps1` passed for `2.1.20`.
- Brand/mojibake scan passed for `openclaw_new_launcher/src`, `data`, and `python`.
- Python compile passed for bridge, component routes, account routes, component installer, and NewAPI account manager.
- Component installer tests passed: 31 tests.
- Component route/catalog tests passed: 11 tests.
- `npm run build` passed in `openclaw_new_launcher`.
- `scripts/build-portable.ps1` passed for `LOOM-Portable-v2.1.20-20260629-rc1`.
- `scripts/verify-release.ps1` passed for the portable zip.
- `scripts/verify-portable-smoke.ps1` passed for the extracted portable package.
- `scripts/verify-installer-manifest.ps1` passed.
- `scripts/build-online-portable.ps1` passed for `LOOM-Online-v2.1.20-20260629-rc1`.
- `scripts/build-online-exe-installer.ps1` passed for `LOOM-Online-Setup-v2.1.20-20260629-rc1.exe`.

## Notes

- Stable channel is intentionally unchanged. Promote this RC only after cross-machine smoke testing.
- Runtime layers continue to use the existing rc layer mirror until a layer change requires rebuilding them.
