# OrbitDesk 下载与更新

这里是 OrbitDesk 的公开下载频道，开发仓库保持私有。

发布内容是 Mac App、JC3636W518C 圆屏固件、字体资源、更新清单及校验摘要，不包含设备配置、恢复镜像、私人媒体或开发日志。USB 开源组件的必要源码、版本与许可证附在 App 中。

## 安装

在 Releases 下载适配架构的 Mac App ZIP，解压到用户的 Applications 文件夹。首个本地验证包适用 Apple Silicon / macOS 13 及以上；Intel 包以对应发布资产为准。

打开菜单栏「软件与设备更新…」即可检查稳定版本。Mac 更新由 Sparkle 2.10.0 校验按架构提供的 Ed25519 签名 appcast 与 ZIP；后台自动检查与安装关闭。当前预览发行使用本地 ad-hoc 签名，不能等同于 Apple Developer ID 公证。

## 圆屏

只支持 ESP32-S3 / 16 MiB Flash 的 JC3636W518C，不支持 ESP32-C3 等其他板型。

旧固件第一次需要 USB 迁移双应用槽，并插好 TF 卡保存完整中文字库。App 会先读取并验证完整恢复备份，再检查 TF 空间、迁移固件，最后上传版本化字库并重启；保留网络设置与 TF 媒体。后续可选 USB 更新或同一局域网的 Wi‑Fi 更新。

Wi‑Fi 更新需在设备打开「Mac 监控」，使用当前 IP 与 PIN。设备通过 HTTPS 获取发布固件，只在校验成功后切换启动槽；新固件稳定 30 秒后确认。共享资源变化时需 USB 更新。

恢复备份含设备配置，保留在本机，不能上传到这个仓库。更新时保持供电与连接；不要强制退出正在写入的 USB 更新。

## 发布状态

当前 0.2.4 / Mac Build 19 为预览版，ARM64 发行含首次安装说明、签名 appcast，共 12 项白名单资产；尚无最新稳定版。目标圆屏已实际从旧版迁移到 0.2.2，备份、各段回读和字体校验通过，NVS 与 TF 媒体保留。Mac Build 19 已在本地安装并通过签名与窗口检查；这不是 Sparkle 在线升级验收。圆屏已接受 0.2.3 OTA 请求，但 GitHub TLS 连接超时，仍运行 0.2.2；无线完成、Sparkle 在线安装及失败/回滚仍待网络恢复后实测，Intel 未实测。Mac 的 Ed25519 签名不代表固件也执行该验签。当前 GitHub 下载路径出现 504，尚不能完成安装验收。

首次安装请同时下载同版 `OrbitDesk-macOS-FIRST-INSTALL.txt` 并核对 `SHA256SUMS`。M1 及以后使用 arm64 包，最低 macOS 13；退出旧版、解压并拖入“应用程序”，尝试打开一次，再到“系统设置 → 隐私与安全性 → 仍要打开”授权。macOS 13/14 使用此路径，15+ 不使用 Control-click 绕过。遇恶意软件、将损坏电脑或文件损坏提示应停止核对。无需清除 quarantine 或关闭全局安全保护。当前主机 macOS 27.3 arm64 实测；13/14/15 真实 OS 尚未实测，不能承诺所有 M 系列及更新系统均通过。官方说明：[Apple](https://support.apple.com/zh-cn/102445)、[macOS 15](https://developer.apple.com/news/?id=saqachfa)、[Sparkle](https://sparkle-project.org/documentation/)。
