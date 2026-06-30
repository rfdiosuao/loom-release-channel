# LOOM / 麓鸣 2.1.32 rc1

发布时间：2026-06-30 22:45 +08:00

## 更新内容

- 总览页收敛为两个主路径：安装智能体、连接手机。
- 安装页改为更像普通安装器的体验：一键安装、安装清单、更多操作、高级详情。
- 手机页改为自然流程：下载 App -> 连接手机 -> 输入任务 -> 查看结果。
- 普通用户界面隐藏 Matrix / MCP / CLI / Bridge 等工程词；开发者接入保留在设置页高级入口。
- 版本统一升级到 2.1.32。

## 包

- `rc/packages/LOOM-Online-v2.1.32-20260630-rc1-ui-stable.zip`
- `rc/packages/LOOM-Online-Setup-v2.1.32-20260630-rc1-ui-stable.exe`

## SHA256

- Online ZIP: `F3FAA9485520E389418EA654A943140222A98C7AD80EE159B863072CAA0CB4D2`
- Online Setup EXE: `C2D41E5C39EE6E0A2795D0259D321778FB6F1B478141701654904AD0CE7DBF02`

## 已验证

- `verify-version-consistency.ps1`：2.1.32 通过
- `git diff --check`：通过
- UI 合同测试：29 tests OK
- `npm run build`：通过
- `npm run tauri -- build`：通过，产出 LOOM.exe / MSI / NSIS
- `build-portable.ps1 -PackageName LOOM-Portable-v2.1.32-20260630-rc1-ui-stable -SkipBuild -NoZip`：通过
- portable release verify + smoke：通过
- `build-online-portable.ps1`：通过
- 在线包结构检查：LOOM.exe、LOOMFiles、Python bridge、dist-cache manifest、release manifest、公钥存在；node/node_modules 大层已裁剪

## 已知限制

- 这版是 rc 测试包，主要验证 UI 收敛、安装器体感和手机控制入口。
- 在线安装器依赖 GitHub raw 下载 `rc/packages/LOOM-Online-v2.1.32-20260630-rc1-ui-stable.zip`。
- 未在另一台电脑完成真实下载安装回归；等待用户进行第一轮外部机器测试。
