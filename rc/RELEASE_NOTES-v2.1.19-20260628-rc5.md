# LOOM v2.1.19 20260628 rc5

## 变更

- 重建 LOOM 在线包，包含最新启动页动态 logo、米白视觉、深绿色主按钮、紧凑前置环境检测和检测动效。
- 保留 rc4 的 Codex 检测修复：支持 PATH、npm prefix、npm root、manifest externalPaths 等多路径检测，改善其他电脑检测不到 Codex 的问题。
- 一键在线安装器继续支持选择安装目录、SHA256 校验、创建快捷方式和安装后启动。
- 桌面/任务栏图标继续使用 LOOM/麓鸣图标资源。

## 测试

- `scripts/build-portable.ps1 -PackageName LOOM-Portable-v2.1.19-20260628-rc5` 通过。
- portable directory / zip release verification 通过。
- bundled Python imports smoke 通过。
- bundled Node CLI syntax smoke 通过。
- online portable shape verification 通过。

## 已知限制

- 本 rc 仍使用当前签名的第三方 agent 安装 manifest；manifest 签名私钥未在本机构建环境中暴露，因此未在本次重签组件清单。
