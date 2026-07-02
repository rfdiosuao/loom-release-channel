# LOOM 2.1.40 rc6 - Command Brain

## 更新
- 新增 LOOM Command Brain CLI/MCP 能力目录，便于 Codex / Claude Code 判断何时调用 LOOM。
- 新增手机 ADB doctor / repair 入口，保留 admin 权限边界。
- 保留 rc5 的 NewAPI 专用 Launcher token 选择修复，避免 Codex / Claude Code 被 agnes-only 默认 key 误配。

## 发布产物
- 在线包：LOOM-Online-v2.1.40-20260702-rc6-command-brain.zip
- 在线安装器：LOOM-Online-Setup-v2.1.40-20260702-rc6-command-brain.exe

## 校验
- 在线包 SHA256：D1D796C126E4D221A8F4C7EF6040ADAFC300F7730605BFBBA3955CEA421EAC64
- 安装器 SHA256：480ACC36DE57B55B083D15FFE2CD6D139C555EB6BEAB432F1601069116F0E5D2
- 发布前验证：git diff --check、Python 合同测试、npm build、verify-release、portable smoke 已通过。

## 回滚
- 回滚 LATEST_RC.txt 与 c/release-manifest.json 到 2.1.40-rc.20260702.5，NewAPI 首页安装按钮指回 rc5 安装器。
