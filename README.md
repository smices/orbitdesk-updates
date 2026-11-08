# OrbitDesk 下载与更新

这里是 OrbitDesk 的公开下载频道，开发仓库保持私有。

发布内容是 Mac App、JC3636W518C 圆屏固件、字体资源、更新清单及校验摘要，不包含设备配置、恢复镜像、私人媒体或开发日志。USB 开源组件的必要源码、版本与许可证附在 App 中。

## 安装

在 Releases 下载适配架构的 Mac App ZIP，解压到用户的 Applications 文件夹。1.0.0 发行包适用 Apple Silicon / macOS 13 及以上；Intel 尚无真机验收，包以对应发布资产为准。

打开菜单栏「软件与设备更新…」即可检查稳定版本。Mac 更新由 Sparkle 2.10.0 校验按架构提供的 Ed25519 签名 appcast 与 ZIP；后台自动检查与安装关闭。当前正式发行使用本地 ad-hoc 签名，不能等同于 Apple Developer ID 公证。

## 圆屏

只支持 ESP32-S3 / 16 MiB Flash 的 JC3636W518C，不支持 ESP32-C3 等其他板型。

旧固件第一次需要 USB 迁移双应用槽，并插好 TF 卡保存完整中文字库。App 会先读取并验证完整恢复备份，再检查 TF 空间、迁移固件，最后上传版本化字库并重启；保留网络设置与 TF 媒体。后续可选 USB 更新或同一局域网的 Wi‑Fi 更新。

Wi‑Fi 更新需在设备打开「Mac 监控」，使用当前 IP 与 PIN。设备通过 HTTPS 获取发布固件，只在校验成功后切换启动槽；新固件稳定 30 秒后确认。共享资源变化时需 USB 更新。

恢复备份含设备配置，保留在本机，不能上传到这个仓库。更新时保持供电与连接；不要强制退出正在写入的 USB 更新。

## 发布状态

当前 1.0.0 / Mac Build 23 为正式版，进入 latest 稳定频道；ARM64 发行含首次安装说明及签名 appcast，共 12 项白名单资产。8 个旧预览 Release、对应标签与 90 项附件已清理，公开频道仅保留 1.0.0；历史验证记录、恢复备份与签名密钥保留。

本机 App 已使用验签后的本地发行包由 Build 22 安装至 23，公开 ZIP 一致性、深度代码签名、公钥、重启和窗口重开检查通过。本次使用本地发行包，产品菜单完整升级流程仍未验收；latest 清单和签名 feed 已通过匿名下载核对。

圆屏已通过 USB 实际运行 1.0.0：完整备份、四段写入回读、TF 字体验证及完成标记通过，启动日志确认版本 1.0.0，90.1 秒观察未见 panic。此前无线更新遇设备端 TLS 连接超时，OTA 完成及受控回滚仍未验收。

Mac 的 Ed25519 更新签名不代表固件也执行该验签；没有 Apple Developer ID 证书或 Apple 公证。私有源码未推送，云端 CI 未运行。

首次安装请同时下载同版 `OrbitDesk-macOS-FIRST-INSTALL.txt` 并核对 `SHA256SUMS`。M1 及以后使用 arm64 包，最低 macOS 13；退出旧版、解压并拖入“应用程序”，尝试打开一次，再到“系统设置 → 隐私与安全性 → 仍要打开”授权。macOS 13/14 使用此路径，15+ 不使用 Control-click 绕过。遇恶意软件、将损坏电脑或文件损坏提示应停止核对。无需清除 quarantine 或关闭全局安全保护。当前主机 macOS 27.3 arm64 的 1.0.0 原生自检及更新页渲染通过；13/14/15 真实 OS 尚未实测，不能承诺所有 M 系列及更新系统均通过。官方说明：[Apple](https://support.apple.com/zh-cn/102445)、[macOS 15](https://developer.apple.com/news/?id=saqachfa)、[Sparkle](https://sparkle-project.org/documentation/)。
