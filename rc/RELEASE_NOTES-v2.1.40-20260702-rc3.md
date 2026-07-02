# LOOM 2.1.40 rc3 - domestic mirror channel timeout fix

## What changed

- Keeps the domestic-first release channel from rc2.
- Rebuilt the one-click online installer with per-channel download timeout, so a stalled source can fall through instead of hanging forever.
- Runtime layers still use LOOM server first, then GitHub raw, then accelerated GitHub.

## Scope

This release only changes the distribution path and installer download robustness. Application code and runtime behavior remain based on 2.1.40 rc1.

## Rollback

Restore `rc/release-manifest.json` to `2.1.40-rc.20260702.1` or `2.1.40-rc.20260702.2` if rc3 installer behavior needs to be withdrawn.
