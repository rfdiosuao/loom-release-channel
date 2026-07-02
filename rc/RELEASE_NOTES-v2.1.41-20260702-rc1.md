# LOOM v2.1.41 rc1 - model-login-fix

Date: 2026-07-02

## Changes
- Enabled NewAPI bridge email-code login endpoints and friendlier login errors.
- Fixed managed model selection so text/image/video models do not overwrite each other.
- Split image and video generation loading state so one task does not block the other.
- Added phone App download entry to the matrix workbench and Skill path copy to Agent access.
- Built the online setup with Gitee split-package channel first, then api.heang.top / GitHub fallback.

## Artifacts
- Installer: LOOM-Online-Setup-v2.1.41-20260702-rc1-model-login-fix.exe
- Online package: LOOM-Online-v2.1.41-20260702-rc1-model-login-fix.zip
- Version: 2.1.41-rc.20260702.1

## Rollback
Restore c/release-manifest.json and LATEST_RC.txt to 2.1.40-rc.20260702.7, then republish the release channel and NewAPI homepage download link.