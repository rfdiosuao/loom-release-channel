# LOOM 2.1.40 rc4 - curl-based online installer fallback

## What changed

- Keeps the domestic-first release channel from rc2/rc3.
- Online installer now prefers Windows `curl.exe` for package downloads.
- Slow or stalled sources fall through to the next source instead of leaving a 0-byte or partial zip forever.
- Runtime layers still use LOOM server first, then GitHub raw, then accelerated GitHub.

## Scope

This release only changes the distribution path and installer download robustness. Application code and runtime behavior remain based on 2.1.40 rc1.

## Rollback

Restore `rc/release-manifest.json` to `2.1.40-rc.20260702.1`, `.2`, or `.3` if rc4 installer behavior needs to be withdrawn.
