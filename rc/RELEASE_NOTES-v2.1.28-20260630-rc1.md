# LOOM / 麓鸣 2.1.28 rc1

发布时间：2026-06-30 10:42 +08:00

## 更新内容

- 内置 api.heang.top 中转站账号闭环：邮箱验证码注册、用户名/邮箱密码登录、退出登录。
- 登录成功后同步可用模型、账号快照、余额/订阅信息，并写入麓鸣主模型与手机 Agent 配置。
- 麓鸣主模型默认 `qwen3.7-plus`，手机 Agent 默认 `agnes-2.0-flash`。
- 订阅信息使用麓鸣原生卡片展示，购买入口跳转中转站订阅页。
- 旧授权码入口保留为回滚路径。
- 账号错误提示统一为中文产品提示，不暴露原始堆栈或密钥。

## 包

- `rc/packages/LOOM-Online-v2.1.28-20260630-rc1.zip`
- `rc/packages/LOOM-Online-Setup-v2.1.28-20260630-rc1.exe`

## SHA256

- Online ZIP: `EC14DE3D3AA055C526DB2F3EDA819D50F7417BD8A09CDB5A120736482203CF00`
- Online Setup EXE: `4236EB247994563743213AB9A8D5DF6B1229AA1DAC01C27A8D8094B322786445`
- Full Portable ZIP: `E35A0CC51F12A2DA3E9C294585C5BFCE3D3CD5A866D024AB7CFF5133DE68F554`

## 已验证

- `api.heang.top` 无凭据接口探测：`/api/verification`、`/api/user/register`、`/api/user/login`、`/api/user/subscription`、`/api/user/self`、`/api/user/models`、`/v1/models`。
- `git diff --check -- openclaw_new_launcher`
- `python -m unittest discover openclaw_new_launcher/python/tests`：135 tests OK
- `python -m unittest openclaw_new_launcher.python.tests.test_routes_phone openclaw_new_launcher.python.tests.test_phone_demo_page_contract`：17 tests OK
- `python -m py_compile openclaw_new_launcher/python/bridge.py ... newapi_account_manager.py ... component_installer.py`
- `npm run build`
- `scripts/build-portable.ps1 -Version 2.1.28 -PackageName LOOM-Portable-v2.1.28-20260630-rc1`
- `scripts/build-online-portable.ps1 -SourcePortableDir release/LOOM-Portable-v2.1.28-20260630-rc1`
- `scripts/build-online-exe-installer.ps1 ... LOOM-Online-Setup-v2.1.28-20260630-rc1.exe`
- `scripts/verify-release.ps1 -Path release/LOOM-Portable-v2.1.28-20260630-rc1.zip`
- `scripts/verify-portable-smoke.ps1 -Path release/LOOM-Portable-v2.1.28-20260630-rc1`
- `scripts/verify-installer-manifest.ps1`
- 包内容检查：新包内包含 `/api/verification`、`/api/user/register`、`qwen3.7-plus`、`agnes-2.0-flash`。

## 已知限制

- 当前 `api.heang.top` 暂未发现独立的邮箱验证码登录 endpoint；本版支持邮箱验证码注册，登录使用用户名/邮箱 + 密码。
- 未执行真实邮箱验证码注册和真实支付购买；这些需要用户接收验证码或进入支付页。
- 在线安装器依赖本仓库 rc packages 路径可访问。
