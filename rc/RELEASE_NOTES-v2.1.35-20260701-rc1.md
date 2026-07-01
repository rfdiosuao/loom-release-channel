# LOOM / 麓鸣 2.1.35 rc1

发布时间：2026-07-01 15:05 +08:00

## 更新内容

- 安装页前置检测结果改为 24 小时缓存；即使检测结果包含缺项，也不会切页返回后反复自动检测。
- Codex / Claude Code / OpenClaw 模型配置面板补齐真正的自定义模型名输入。
- Claude Code 网关启动环境补齐 `ANTHROPIC_AUTH_TOKEN`，保留 `ANTHROPIC_API_KEY` 兼容。
- 版本统一升级到 2.1.35。

## 包

- `rc/packages/LOOM-Online-v2.1.35-20260701-rc1.zip`
- `rc/packages/LOOM-Online-Setup-v2.1.35-20260701-rc1.exe`

## SHA256

- Online ZIP: `4ADB84BAAA753CE35E5DCCCC9CA35F92D1C83A5F8A7B57D9EF3F71A612182BE0`
- Online Setup EXE: `C01F2D2418854088C5A9911A524849E8184846275813C905FDC27C69C59A3499`

## 已验证

- `verify-version-consistency.ps1`：2.1.35 通过
- `npm run build`：通过
- 安装页 / Wire / 组件启动环境合同测试：62 tests OK
- `build-portable.ps1`：portable verify + smoke 通过
- `build-online-portable.ps1`：通过
- `verify-release.ps1 -Online`：目录和 zip 均通过
- `verify-installer-manifest.ps1`：通过，5 个智能体组件齐全
- `verify-release-secrets.ps1`：通过，仅允许第三方库固定示例命中
- `git diff --check`：通过，仅有 CRLF 提示

## 已知限制

- 这版是 RC 测试包，等待另一台电脑进行真实在线下载和安装回归。
- 在线安装器依赖 GitHub raw 下载 `rc/packages/LOOM-Online-v2.1.35-20260701-rc1.zip`。
- 完整 portable 包体积约 345MB，未放入 release-channel 仓库。
