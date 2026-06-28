# LOOM v2.1.19 20260628 rc6

## 变更

- 在线安装器外壳改为经典安装向导样式：左侧深色品牌栏，右侧白色内容区，底部上一步 / 安装 / 取消按钮。
- 安装器内品牌统一为 LOOM / 麓鸣，移除 Lumi / LumiClaw 文案。
- 安装目录默认改为当前用户目录下的 `%LOCALAPPDATA%\LOOM`，保留浏览选择目录。
- 在线安装逻辑不变：下载 rc6 online zip、校验 SHA256、安装到选择目录、创建快捷方式、安装后启动。

## 测试

- `build-online-portable.ps1` 生成 rc6 online zip 并通过在线包结构校验。
- `build-online-exe-installer.ps1` 生成 rc6 one-click installer。
- 安装器二进制和生成脚本扫描未发现 `Lumi` / `LumiClaw` 残留。
- 截图验证：`artifacts/installer-ui-rc6-welcome.png`、`artifacts/installer-ui-rc6-dir-wide.png`。