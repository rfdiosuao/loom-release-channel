# LOOM 2.1.38 rc1

Published: 2026-07-01T09:39:08Z

## What Changed

- Restored the locked navigation entries for Phone, Matrix Workbench, Agent Access, and Other capabilities.
- Kept installation and custom API provider configuration usable without login; gated managed model sync and runtime features behind NewAPI login.
- Fixed NewAPI email-code error handling so server business errors are not hidden behind the generic "endpoint unavailable" message.
- Synced NewAPI model configuration to Codex Desktop, Claude Code, opencode, OpenClaw, desktop config, image config, and phone config.
- Persisted LOOM-managed environment keys for Codex Desktop, Claude Code, and opencode while keeping actual keys out of config files.

## Artifacts

- Online package: `LOOM-Online-v2.1.38-20260701-rc1-account-codex-gates.zip`
- Online installer: `LOOM-Online-Setup-v2.1.38-20260701-rc1-account-codex-gates.exe`

## Verification

- Python unittest discovery: 294 tests passed.
- Frontend build: `npm run build` passed.
- Rust/Tauri check: `cargo check` passed.
- Portable build verification, online package verification, portable smoke, and secret scan passed.
