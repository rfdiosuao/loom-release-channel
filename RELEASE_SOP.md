# LOOM / 麓鸣发布 SOP

这份 SOP 用于以后发布 LOOM 在线安装包与 release channel。默认发布链路是：

`AUSTART 构建包` -> `loom-release-channel 更新 manifest` -> `api.heang.top 国内镜像` -> `GitHub raw / 加速链接兜底` -> `NewAPI 首页下载入口`。

## 1. 发布前冻结

1. 确认主线只取 `D:\Axiangmu\AUSTART\openclaw_new_launcher` 和 `D:\Axiangmu\AUSTART\scripts` 的发布链路。
2. 不把 `openclaw_ui_integration` 当作发布入口。
3. 检查工作区：

```powershell
cd D:\Axiangmu\AUSTART
git status --short --branch
git diff --stat
git diff --check
```

4. 版本命名：

```text
应用版本：2.1.x
RC manifest：2.1.x-rc.YYYYMMDD.N
包名：LOOM-Online-v2.1.x-YYYYMMDD-rcN-<short-note>
安装器：LOOM-Online-Setup-v2.1.x-YYYYMMDD-rcN-<short-note>.exe
```

## 2. 本地构建

先在 `D:\Axiangmu\AUSTART` 构建可运行包，再生成在线包与安装器。

```powershell
cd D:\Axiangmu\AUSTART

# 按当前项目实际构建脚本生成完整 portable 包。
powershell -ExecutionPolicy Bypass -File scripts\build-portable.ps1

# 用 release-channel manifest 生成在线 portable 包。
$packageName = "LOOM-Online-v2.1.x-YYYYMMDD-rcN-note"
$manifestPath = "D:\Axiangmu\loom-release-channel\rc\release-manifest.json"
powershell -ExecutionPolicy Bypass -File scripts\build-online-portable.ps1 `
  -SourcePortableDir "D:\Axiangmu\AUSTART\release\LOOM-Portable-v2.1.x-YYYYMMDD" `
  -PackageName $packageName `
  -DistributionManifestPath $manifestPath
```

生成 zip 后计算 SHA256：

```powershell
Get-FileHash -Algorithm SHA256 "D:\Axiangmu\AUSTART\release\$packageName.zip"
```

## 3. 生成一键安装 EXE

在线安装器必须优先国内源，再走 GitHub raw，最后走加速链接。

```powershell
cd D:\Axiangmu\AUSTART

$version = "2.1.x"
$packageName = "LOOM-Online-v2.1.x-YYYYMMDD-rcN-note"
$zipSha256 = "<ZIP_SHA256>"
$serverZip = "https://api.heang.top/downloads/loom/rc/packages/$packageName.zip"
$rawZip = "https://raw.githubusercontent.com/rfdiosuao/loom-release-channel/main/rc/packages/$packageName.zip"
$fastZip = "https://ghfast.top/$rawZip"

powershell -ExecutionPolicy Bypass -File scripts\build-online-exe-installer.ps1 `
  -PackageUrl $serverZip `
  -PackageFallbackUrls @($rawZip, $fastZip) `
  -PackageSha256 $zipSha256 `
  -PackageRootName $packageName `
  -Version $version `
  -OutputPath "D:\Axiangmu\AUSTART\release\LOOM-Online-Setup-v$version-YYYYMMDD-rcN-note.exe"
```

安装器生成后记录：

```powershell
Get-FileHash -Algorithm SHA256 "D:\Axiangmu\AUSTART\release\LOOM-Online-Setup-v$version-YYYYMMDD-rcN-note.exe"
```

## 4. 更新 release-channel

在 `D:\Axiangmu\loom-release-channel` 更新：

```text
LATEST_RC.txt
rc/release-manifest.json
rc/packages/<online zip>
rc/packages/<installer exe>
rc/packages/*.sha256.txt
versions/<version>.json
```

`rc/release-manifest.json` 必须包含：

```text
launcherPackage.url = https://api.heang.top/downloads/loom/rc/packages/<zip>
launcherPackage.fallbackUrls = GitHub raw + ghfast
installerPackage.url = https://api.heang.top/downloads/loom/rc/packages/<exe>
installerPackage.fallbackUrls = GitHub raw + ghfast
mirrors[0] = https://api.heang.top/downloads/loom/rc/layers/v2.1.19/
```

测试期如果需要把 zip/exe 放进 GitHub 仓库，因 `.gitignore` 会排除二进制，需要显式 `git add -f`。正式期建议迁移到 GitHub Release / Gitee Release / OSS，只在仓库保留 manifest。

## 5. 上传国内镜像

把 release-channel 公共文件同步到两台服务器：

```text
火山云前置：root@118.145.98.220:/var/www/loom-release-channel
NewAPI 后端：root@160.202.254.29:20037:/var/www/loom-release-channel
```

推荐打一个临时 tar 包上传，再在服务器解压覆盖：

```powershell
cd D:\Axiangmu\loom-release-channel
tar -czf $env:TEMP\loom-release-channel.tgz channels.json LATEST_RC.txt README.md rc stable versions
scp -i C:\Users\Administrator\Desktop\heang_server $env:TEMP\loom-release-channel.tgz root@118.145.98.220:/tmp/
scp -i C:\Users\Administrator\Desktop\heang_server -P 20037 $env:TEMP\loom-release-channel.tgz root@160.202.254.29:/tmp/
```

服务器执行：

```bash
mkdir -p /var/www/loom-release-channel
tar -xzf /tmp/loom-release-channel.tgz -C /var/www/loom-release-channel
chown -R www-data:www-data /var/www/loom-release-channel
```

Nginx 应保持：

```text
https://api.heang.top/downloads/loom/ -> /var/www/loom-release-channel/
```

## 6. 更新 NewAPI 首页安装按钮

每次换安装器文件名后，同时更新两个入口：

1. NewAPI 数据库：

```text
/mnt/data/new-api/one-api.db
options.HomePageContent
```

2. 静态首页：

```text
root@118.145.98.220:/var/www/api.heang.top/homepage.html
```

按钮目标统一指向：

```text
https://api.heang.top/downloads/loom/rc/packages/<installer exe>
```

修改数据库前必须先备份：

```bash
mkdir -p /mnt/data/backups/new-api/homepage-loom-installer-$(date +%Y%m%d-%H%M%S)
cp /mnt/data/new-api/one-api.db /mnt/data/backups/new-api/homepage-loom-installer-$(date +%Y%m%d-%H%M%S)/one-api.before.db
```

修改 `HomePageContent` 后重启 NewAPI 容器让配置刷新：

```bash
docker restart new-api
curl -fsS http://127.0.0.1:3006/api/status >/dev/null
```

## 7. GitHub 发布

```powershell
cd D:\Axiangmu\loom-release-channel
git status --short --branch
git add channels.json LATEST_RC.txt README.md RELEASE_SOP.md rc stable versions
git add -f rc\packages\<zip> rc\packages\<exe> rc\packages\*.sha256.txt
git commit -m "Publish LOOM rcN <short-note>"
git push origin main
```

推送后确认：

```powershell
Invoke-WebRequest -UseBasicParsing https://raw.githubusercontent.com/rfdiosuao/loom-release-channel/main/rc/release-manifest.json
```

## 8. 发布验证

每次发版必须记录这些证据：

```powershell
# manifest
Invoke-WebRequest -UseBasicParsing https://api.heang.top/downloads/loom/rc/release-manifest.json

# 安装器
Invoke-WebRequest -Method Head -UseBasicParsing https://api.heang.top/downloads/loom/rc/packages/<installer exe>

# 在线包
Invoke-WebRequest -Method Head -UseBasicParsing https://api.heang.top/downloads/loom/rc/packages/<zip>

# NewAPI 首页
Invoke-WebRequest -UseBasicParsing https://api.heang.top/homepage.html | Select-String "下载 LOOM 安装器"

# NewAPI 服务
Invoke-WebRequest -UseBasicParsing https://api.heang.top/api/status
```

安装器 smoke 使用临时目录，不能污染真实安装目录：

```powershell
$tmp = Join-Path $env:TEMP ("loom-install-smoke-" + [guid]::NewGuid())
& "D:\Axiangmu\AUSTART\release\<installer exe>" /S /D=$tmp
Test-Path (Join-Path $tmp "LOOM.exe")
```

## 9. 回滚

1. 保留上一版 `rc/release-manifest.json` 和包文件，不要删除。
2. 如新包故障，先把服务器 `/var/www/loom-release-channel/rc/release-manifest.json` 回滚到上一版。
3. 再把 GitHub `rc/release-manifest.json` 回滚并推送。
4. NewAPI 首页按钮改回上一版 installer URL。
5. 记录故障原因、回滚时间、回滚后的验证截图/日志。

## 10. 安全规则

1. 不提交真实账号、密码、API Key、Token、私钥、服务器密钥。
2. 不把运行日志、审计日志、缓存、用户数据打进包。
3. manifest 只放公开下载信息、公开 sha256、公开镜像地址。
4. 发布脚本和 SOP 可以入库，服务器私钥和生产凭据绝对不能入库。
