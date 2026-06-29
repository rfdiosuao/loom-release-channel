# LOOM 2.1.21 rc3

2026-06-29

## 修复

- 保留 rc2 的跨盘安装修复：在线安装器安装到 D 盘或其他非系统盘时，不再依赖跨卷目录移动。
- 保留 rc2 的首次启动修复：Node/Python/运行时层从缓存进入安装目录时，跨盘失败会自动回退为复制后删除源目录。
- 新增 manifest BOM 容错：即使远端或缓存 manifest 被 Windows 工具写入 UTF-8 BOM，启动器也能正常解析。

## 验证

- `cargo test bootstrap::tests::`
- `npm run tauri -- build`
- `build-portable.ps1 -SkipBuild -NoZip`
- `build-online-portable.ps1`
- `build-online-exe-installer.ps1`
