# LOOM 2.1.40 rc1

Published: 2026-07-01T16:22:54Z

## What Changed

- Cached prerequisite detection after a successful check so returning to the installer page no longer forces the same scan.
- Kept installation and prerequisite repair usable without login; kept managed model sync and runtime capabilities behind NewAPI login.
- Improved Codex Desktop, Claude Code, opencode, OpenClaw, and Hermes install/config states with clearer custom provider and rollback paths.
- Updated the phone control flow around saved IP/token, model sync prompts, connection failures, and task status persistence.
- Pointed the subscription entry to the current wallet page and kept custom API key configuration available without login.
- Kept the Matrix Workbench on real backend/no-device states instead of demo-only placeholder data.

## Artifacts

- Online package: `LOOM-Online-v2.1.40-20260702-rc1-p0-stabilization.zip`
- Online installer: `LOOM-Online-Setup-v2.1.40-20260702-rc1-p0-stabilization.exe`

## Verification

- `git diff --check` passed in the source workspace before packaging.
- Related Python compile/tests passed, with 303 full Python tests passed in the last source validation run.
- Frontend build: `npm run build` passed before packaging.
- Online package verification passed.
- Release secret scan passed.
- UI smoke covered installer cache, account/model page, custom provider, fake phone IP failure state, Agent Access, Other, and Matrix Workbench no-device state.
