# 开发流程

origin：`https://github.com/kaulie/home-agent-ios`。从最新 `origin/main` 开短命分支，PR 回 `main`。禁止直推 / force push `main`。

1. 先读 [`../../AGENT.md`](../../AGENT.md) 与本目录。
2. 只打开将改的那套 App。
3. 对照 IntentClient / hydrate / 前序门。
4. 改完 Swift 列表：`python3 <App>/generate_xcodeproj.py`。有模拟器再 `xcodebuild`。
5. 不要把 Admin 开关放进 Console 底栏。
6. 不要改能力声明 YAML（那是集市）。
7. 不要改 Android 仓，除非任务点名。

不要提交签名证书、`xcuserdata/`、Provisioning Profile、用户相册。
