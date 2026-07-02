# LOOM 2.1.40 rc2 - domestic mirror channel

## What changed

- Added a domestic HTTPS release channel under `https://api.heang.top/downloads/loom/`.
- Rebuilt the one-click online installer so the launcher package download tries:
  1. LOOM domestic server
  2. GitHub raw
  3. accelerated GitHub fallback
- Updated runtime layer mirrors in `release-manifest.json` to use the same domestic-first order.

## Scope

This release only changes the distribution path. Application code and runtime behavior remain based on 2.1.40 rc1.

## Rollback

Restore `rc/release-manifest.json` to `2.1.40-rc.20260702.1` and use the previous rc1 package files if the domestic mirror has download issues.
