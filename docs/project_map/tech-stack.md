# 技术栈

| 项 | 事实 |
|---|---|
| 语言 | Swift |
| IDE | Xcode（工程由 Python 脚本生成，不手改 pbxproj 当源） |
| 工程生成 | 各 App 目录 `generate_xcodeproj.py` |
| 系统 | Console / Admin / Dev / Pickup / Relay：iOS 16；Legacy / 老机拾音：iOS 12 |
| 网络 | 本机 URLSession → Brain HTTP |
| 权限 | Console 真机需麦克风 + 语音识别 |

无 CocoaPods 作为一等路径（以各工程生成为准）。无 `build.sh`。无 Docker。无 HomeAgent 服务端源码。
