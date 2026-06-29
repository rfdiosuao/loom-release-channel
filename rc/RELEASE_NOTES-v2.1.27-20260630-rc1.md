# LOOM / 麓鸣 2.1.27 rc1

发布时间：2026-06-30 06:05 +08:00

## 更新内容

- 移植上一版已验证手机控制模块的核心稳定逻辑到 LOOM 新启动器主线。
- 手机地址输入更抗脏数据：支持裸 IP、`IP:端口`、少一个斜杠的 `http:/IP`、中文冒号、中文句号、中文斜杠和粘贴路径，最终统一整理为可连接的 base URL。
- 手机安全配对加入缓存、并发合并和 30 秒失败冷却，避免连续点击检测/截图/读取时重复冲击手机端配对接口。
- 403 重新配对时会清理旧配对缓存，再走一次签名请求。
- 保留演示版简化 UI，不搬迁旧模块里的复杂自动化模板、定时任务和任务库。

## 包

- `rc/packages/LOOM-Online-v2.1.27-20260630-rc1.zip`
- `rc/packages/LOOM-Online-Setup-v2.1.27-20260630-rc1.exe`

## SHA256

- Online ZIP: `3FA8CC4605793F406BF768FCAF1D339394DE15AED6C3CE613134E11A9C5E935C`
- Online Setup EXE: `904A27F3FFCC1BDC2F0C6964F4551FD85C29730E12CDE9D4EBF5A1B6D86EC94A`
- Full Portable ZIP: `FEE6FEF683B5B8B69DDD4AB4500099866C5746A915BFB391D45B44631E87B10B`

## 已验证

- `powershell -File scripts/verify-version-consistency.ps1`
- `python -m unittest discover openclaw_new_launcher/python/tests`：122 tests OK
- `node --input-type=module ... normalizePhoneUrl(...)`：脏输入归一化通过
- `node --check`：手机安全脚本、手机 Agent、手机视觉脚本语法通过
- `python -m py_compile openclaw_new_launcher/python/bridge.py ... routes_phone.py ...`
- `git diff --check -- openclaw_new_launcher`
- `npm run build`
- `scripts/build-portable.ps1 -Version 2.1.27 ...`
- `scripts/build-online-portable.ps1 ...`
- `scripts/build-online-exe-installer.ps1 ...`
- `scripts/verify-release.ps1 -Path release/LOOM-Portable-v2.1.27-20260630-rc1.zip`
- `scripts/verify-portable-smoke.ps1 -Path release/LOOM-Portable-v2.1.27-20260630-rc1`
- `scripts/verify-installer-manifest.ps1`
- 在线 zip 关键文件检查：`LOOM.exe`、`routes_phone.py`、`openclaw-phone-secure.mjs`、`openclaw-phone-agent.mjs`、`release-manifest.json` 均存在，未包含 `OpenClawFiles` 或 `openclaw_ui_integration`。

## 已知限制

- 真机仍需要手机端 APKClaw 服务已启动、电脑与手机同局域网、令牌正确。
- 本版只搬稳定连接与安全请求核心，不开放旧模块里的复杂手机自动化任务库。
