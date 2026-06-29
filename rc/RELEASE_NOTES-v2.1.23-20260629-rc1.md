# LOOM / 麓鸣 2.1.23 rc1

发布时间：2026-06-29 12:23:08 +08:00

## 更新内容

- 设置页新增真实更新入口，可检查并触发本地 Bridge 更新流程。
- 主题切换改为真实生效：米白、深色、跟随系统都会立即刷新界面变量。
- 语言切换改为真实生效：中文 / English 会保存到本机并即时切换设置页。
- 在线包前置检测不再把 node_modules/openclaw/openclaw.mjs 当成必需项，避免轻量在线包误报缺失。
- 启动页继续使用 logo_motion_single.html 循环矢量动画。
- 版本号统一升级到 2.1.23。

## 包

- rc/packages/LOOM-Online-v2.1.23-20260629-rc1.zip
- rc/packages/LOOM-Online-Setup-v2.1.23-20260629-rc1.exe

## SHA256

- Online ZIP: FE3069BB97DE5961774388D41171511CB4E217DA7C320C1E64567D28EA842203
- Online Setup EXE: 90D302C8417B4FBED2C8B3466F949F96ADD612986D837507CBC8ED6CABEE7A82

## 已验证

- git diff --check
- Python 单元测试与 py_compile
- npm run build
- scripts/build-portable.ps1
- scripts/build-online-portable.ps1
- scripts/build-online-exe-installer.ps1
- scripts/verify-installer-manifest.ps1
