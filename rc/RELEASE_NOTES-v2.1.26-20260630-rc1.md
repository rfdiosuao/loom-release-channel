# LOOM / 麓鸣 2.1.26 rc1

发布时间：2026-06-30 05:30 +08:00

## 更新内容

- 恢复 v1 版 LOOM 启动矢量动效入口：启动页重新加载 `logo_motion_vector-v1.html`，并通过 ready nonce 确认 iframe 动效已就绪。
- 手机控制页改为只输入手机 IP；LOOM 内部自动补 `http://IP:9527`，仍兼容粘贴完整 URL 或 `IP:端口`。
- 修复手机任务因 `runtime-context.json` 损坏而直接失败的问题；手机 Agent、截图、视频、视觉、发布脚本现在会把运行上下文当作可选缓存，优先使用启动器保存的手机配置继续执行。
- 手机连接错误文案统一为“手机 IP / 连接令牌”，减少普通用户看到 HTTP、端口和内部缓存文件的概率。

## 包

- `rc/packages/LOOM-Online-v2.1.26-20260630-rc1.zip`
- `rc/packages/LOOM-Online-Setup-v2.1.26-20260630-rc1.exe`

## SHA256

- Online ZIP: `09CB930C4084524A6A55CD192CD74B16AB10261C38108B888EF8E202B5BCC055`
- Online Setup EXE: `F67B0B16479DDCCA9A72C015AACA9D4C6ACF1738F011EC66348FBB58120D873A`
- Full Portable ZIP: `DD106F419850FCEEF1A90C25E28AD90A8E0668B8168DF92059E52CC29CCB8E9A`

## 已验证

- `python -m unittest discover openclaw_new_launcher/python/tests`：121 tests OK
- `python -m py_compile openclaw_new_launcher/python/bridge.py ... routes_phone.py ...`
- `git diff --check -- openclaw_new_launcher`
- `npm run build`
- 临时坏 `runtime-context.json` 复现：`openclaw-phone-agent.mjs history --json` 不再崩溃
- `scripts/build-portable.ps1 -Version 2.1.26 ...`
- `scripts/build-online-portable.ps1 ...`
- `scripts/build-online-exe-installer.ps1 ...`
- `scripts/verify-release.ps1 -Path release/LOOM-Portable-v2.1.26-20260630-rc1.zip`
- `scripts/verify-portable-smoke.ps1 -Path release/LOOM-Portable-v2.1.26-20260630-rc1`
- `scripts/verify-installer-manifest.ps1`
- 在线 zip 关键文件检查：`LOOM.exe`、`routes_phone.py`、`openclaw-phone-agent.mjs`、`openclaw-phone-secure.mjs`、`release-manifest.json` 均存在，未包含 `OpenClawFiles` 或 `openclaw_ui_integration`。

## 已知限制

- 手机真机连接仍依赖手机端 APKClaw 服务已启动、电脑与手机处于同一局域网、连接令牌正确。
- 2.1.26 只修复启动器侧输入、缓存容错和打包；手机端 APK 若未启动或端口被拦截，仍需在手机端处理。
