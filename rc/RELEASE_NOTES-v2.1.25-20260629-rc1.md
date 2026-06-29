# LOOM / 麓鸣 2.1.25 rc1

发布时间：2026-06-29 18:00:26 +08:00

## 更新内容

- 启动页继续使用 `logo_motion_single.html` 矢量动效资源，包内 `dist` 动画哈希与源文件一致。
- 修复 Codex、Claude Code、opencode、OpenClaw、Hermes 通过启动器启动后命令行闪退的问题，交互式窗口现在保留标准输入输出。
- 总览与设置页版本同步到 `2.1.25`，总览不再把签名组件源版本误当作启动器版本展示。
- 在线安装器重新绑定 `LOOM-Online-v2.1.25-20260629-rc1.zip` 与真实 SHA256。

## 包

- `rc/packages/LOOM-Online-v2.1.25-20260629-rc1.zip`
- `rc/packages/LOOM-Online-Setup-v2.1.25-20260629-rc1.exe`

## SHA256

- Online ZIP: `CA8FB5C8C83C9B8E7F6EA8A64A20DC77E8189170F37ECC972C62C352393501EC`
- Online Setup EXE: `5FF7824216289E2B8BC629C4A4462AF618C46178004916EDAB6ABE9A4C6E66E3`

## 已验证

- `git diff --check -- openclaw_new_launcher scripts`
- `python -m py_compile ...`
- `python -m unittest discover openclaw_new_launcher/python/tests`
- `npm run build`
- `scripts/build-portable.ps1`
- `scripts/build-online-portable.ps1`
- `scripts/build-online-exe-installer.ps1`
- `scripts/verify-release.ps1`
- `scripts/verify-portable-smoke.ps1`
- `scripts/verify-installer-manifest.ps1`
