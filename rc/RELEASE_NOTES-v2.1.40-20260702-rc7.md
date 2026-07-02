# LOOM 2.1.40 rc7 prerequisite fix

- 首页安装入口更新到 rc7。
- 在线 Setup 改为公开 Gitee 小分片优先下载，api.heang.top、GitHub raw 与 GitHub 加速链路作为兜底。
- 修复安装页反复检测前置环境的体感问题。
- 缺失 Git / Git Bash / Node.js / npm / Python / uv / WebView2 时进入一键补齐链路。
- npm 类智能体安装改为 LOOM 私有 prefix，减少污染用户全局环境。