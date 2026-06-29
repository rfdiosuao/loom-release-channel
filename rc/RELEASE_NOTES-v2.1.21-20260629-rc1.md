# LOOM / 麓鸣 v2.1.21-20260629-rc1

## 重点修复

- 启动页切换到 LOOM 矢量动效资源 `logo_motion_vector-v1.html`，延长首屏展示并移除外层抖动式缩放。
- Agent 安装页主按钮改为“安装并启动 / 升级并启动”，安装或升级完成后会自动拉起组件。
- Windows 下启动 Agent 改为打开可见终端窗口，CLI 类 Agent 不再静默后台启动。
- 替换浏览器原生确认框为 LOOM 内置确认弹窗，修复 `tauri.localhost 显示` 的割裂体验。
- 左下角入口补实：齿轮进入系统设置，小门进入模型账号/登录注册。
- 新增系统设置页：外观 / 数据 / 关于，当前演示版固定米白主题，深色与跟随系统明确暂未开放。

## 包信息

- 在线包：`LOOM-Online-v2.1.21-20260629-rc1.zip`
- 在线安装器：`LOOM-Online-Setup-v2.1.21-20260629-rc1.exe`
- zip SHA256：`DB21B39F33CFFD0C34711728EFBA21CF1DA4C307E71C7EFC2A4D848B68986810`
- exe SHA256：`D389303911299583F2AEB9A7E9D42007678E89ACAE565DEF6B967AE6DC58D7CE`

## 已知限制

- 真实下载安装仍依赖 GitHub raw 网络可达性；现场演示建议优先走“检测 -> 安装 -> 启动状态”。
- 深色主题、复杂自动化模板、任务库、Skills、生图/生视频等继续保持暂未开放。
- release manifest 的组件层仍复用 `v2.1.19` 运行层，未在本次改动中替换 Node / Python / openclaw-deps 层。
