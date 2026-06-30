# LOOM / 麓鸣 2.1.29 rc1

发布时间：2026-06-30 11:05 +08:00

## 更新内容

- 保留 2.1.28 的 api.heang.top 中转站账号闭环：邮箱验证码注册、用户名/邮箱密码登录、退出登录、订阅快照、模型同步。
- 根据当前服务器接口探测结果，UI 移除未开放的“验证码登录”主入口，只保留“密码登录”和“邮箱注册”。
- 邮箱验证码仍用于注册；后端保留验证码登录兼容路由，待服务器开放后可恢复入口。
- 麓鸣主模型默认 `qwen3.7-plus`，手机 Agent 默认 `agnes-2.0-flash`。
- 旧授权码入口继续保留为回滚路径。

## 包

- `rc/packages/LOOM-Online-v2.1.29-20260630-rc1.zip`
- `rc/packages/LOOM-Online-Setup-v2.1.29-20260630-rc1.exe`

## SHA256

- Online ZIP: `3227944633248CC60F467B1A77F6BD0CEC6F1F99E9655DA79E4D995A4154305F`
- Online Setup EXE: `42B0FAA56D99B1358C701A25CD0AF588BD72B99903085983E72FA4E0F75B592C`
- Full Portable ZIP: `BF467AAD0C5826A9733B3BE6587EF9C2EEC8EFF1378B16F6F6855B88A659FD21`

## 已验证

- `python -m unittest openclaw_new_launcher.python.tests.test_account_ui_contract openclaw_new_launcher.python.tests.test_newapi_account_manager openclaw_new_launcher.python.tests.test_routes_account openclaw_new_launcher.python.tests.test_routes_phone openclaw_new_launcher.python.tests.test_phone_demo_page_contract`：38 tests OK
- `python -m unittest discover openclaw_new_launcher/python/tests`：135 tests OK
- `npm run build`
- `git diff --check -- openclaw_new_launcher`
- `scripts/build-portable.ps1 -Version 2.1.29 -PackageName LOOM-Portable-v2.1.29-20260630-rc1`
- `scripts/build-online-portable.ps1 -SourcePortableDir release/LOOM-Portable-v2.1.29-20260630-rc1`
- `scripts/build-online-exe-installer.ps1 ... LOOM-Online-Setup-v2.1.29-20260630-rc1.exe`
- `scripts/verify-release.ps1 -Path release/LOOM-Portable-v2.1.29-20260630-rc1.zip`
- `scripts/verify-portable-smoke.ps1 -Path release/LOOM-Portable-v2.1.29-20260630-rc1`
- 前端源码与 dist 扫描：UI 不再出现“验证码登录”主入口。

## 已知限制

- 未执行真实邮箱验证码注册、真实账号登录和支付购买；这些需要用户提供验证码或测试账号。
- 当前 `api.heang.top` 探测结果显示验证码发送与注册可用，未发现独立的验证码登录 endpoint。
