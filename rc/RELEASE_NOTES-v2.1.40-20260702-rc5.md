# LOOM 2.1.40 rc5 - NewAPI launcher token model config

## What Changed

- Codex / Claude Code model configuration now prefers a dedicated `LOOM Launcher` API token.
- If the default NewAPI token only exposes phone-side `agnes` models, LOOM creates or selects a better launcher token before writing Agent model config.
- Online installer remains domestic mirror first, with GitHub raw and accelerated GitHub fallback.

## Validation

- `git diff --check`
- source text and secret scans
- full Python unittest suite
- frontend production build
- portable and online package verification
- portable smoke verification

## Rollback

Restore `rc/release-manifest.json` and `LATEST_RC.txt` to `2.1.40-rc.20260702.4`, then re-publish the release channel.
