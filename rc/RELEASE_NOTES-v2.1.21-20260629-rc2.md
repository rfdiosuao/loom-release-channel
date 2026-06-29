# LOOM 2.1.21 rc2

2026-06-29

## 修复

- 修复在线安装器安装到 D 盘或其他非系统盘时，目录移动可能报“源路径和目标路径必须具有相同的根”的问题。
- 修复在线包首次启动下载 Node/Python/运行时层后，跨盘 `rename` 可能失败的问题；现在会自动回退为复制后删除源目录。

## 验证

- `build-portable.ps1 -NoZip` 已重新生成并验证 portable 目录。
- `build-online-portable.ps1` 已生成 rc2 在线包。
- `build-online-exe-installer.ps1` 已生成 rc2 一键在线安装器。
