# AGENT.md — 后续 Agent 对本仓库的说明与向导

你是来改 **home-agent-ios** 的。先读本文，再按 [`README.md`](README.md) 与各 App README 展开理解。  
本仓没有 `project_map/`。这是 iPhone 客户端：**只打 Brain HTTP**，不 import Brain / Gateway / sidecar 源码。  
os 已归档；不要再往 [`kaulie/home-agent-os`](https://github.com/kaulie/home-agent-os) 的 `ios/` 提交。

## 1. 对本项目的理解

| 你应建立的判断 | 展开阅读 |
|---|---|
| 主发出窗是 `LivingRoomEdge`（HomeAgent Console）：Intent Source + Endpoint + 有限 Runtime（GoPro / 客厅灯） | [README.md](README.md)、[LivingRoomEdge](LivingRoomEdge/) |
| Admin / Dev / Pickup / Relay 是独立 App，不要塞进 Console 底栏 | 各目录 README |
| Brain：LAN `http://brain.local:9527`，Cloud `http://49.234.45.173:9527`。图只认 `presentation.asset_ref` | README、`LivingRoomEdge/LivingRoomEdge/Brain/` |
| 不在 `:4220` 发版。改 Swift 文件列表后重跑该 App 的 `generate_xcodeproj.py` | 各 `generate_xcodeproj.py` |
| agent-bridge / 本机 chat / admin HTML **不在本仓**（bridge 仍在 os） | HomeAgentDev README |

Runtime 会要求优先读根目录 `AGENT.md`。你正在读的就是那份。

## 2. 开工前清单

1. workspace origin 是 `https://github.com/kaulie/home-agent-ios`。
2. 从最新 `main` 开 `feat|fix|chore/<简述>`。
3. 只打开将改的那套 App；对照 `IntentClient` / hydrate / 前序门。
4. 改完 Swift 列表执行 `python3 <App>/generate_xcodeproj.py`。有模拟器时再 `xcodebuild`。
5. 不要改 `/Users/gaolei/runtime/**`。不要改 os。不要改 Android 仓（除非任务点名）。

## 3. 滞后信息：有义务更新

README 仍写 `ios/LivingRoomEdge/...` 前缀、或文档链到已失效的 `../../docs/` 相对路径时，改成本仓相对路径或 os 的 GitHub blob URL。

## 4. 与事实不符：必须提出异议，禁止默认处理

| 你看到的 | 你不该做的 | 你该做的 |
|---|---|---|
| 任务要求 iPhone 执行 `display.photo` / 投电视 | 在 Console 加 Cast | 异议：投屏在 Mac Edge |
| 任务要求把 Admin 开关放进 Console 底栏 | 加 Tab | 异议：独立 App |
| 任务要求改能力声明 | 改本仓 YAML | 异议：marketplace |
| 任务要求直推 `main` 或改 os | 照做 | 异议：走 PR；os 已归档 |

```
异议：<文档路径> 声称 <原句>
事实：<文件:符号 或 命令输出>
处理：<已改文档 / 已改代码 / 需要人决定>
```

## 5. 改动落点

| 要改的东西 | 去哪 |
|---|---|
| 主聊天 / 扫描拍照文件录音直播 | `LivingRoomEdge/LivingRoomEdge/App/` |
| 登记 / intent / asset | `LivingRoomEdge/LivingRoomEdge/Brain/` |
| GoPro / 灯 | `GoPro/`、`Light/` |
| 老机 | `LivingRoomLegacy/` |
| 业务中控 / Dev / 拾音 / 中继 | `HomeAgentAdmin/`、`HomeAgentDev/`、`HomeAgentPickup/`、`LivingRoomPickup/`、`HomeAgentRelay/` |
| Xcode 工程再生 | 各目录 `generate_xcodeproj.py` |
| 给后续 agent 的地图 | 本文 + README |

## 6. 交付

- 提交信息说清为什么。
- `git push -u origin HEAD`，`gh pr create`，回写 `prUrl`。
- 真机安装不是 `:4220` 发版；只听从 `goal` 与人的明确指令。

## 7. 安全

不要提交签名证书、`xcuserdata/`、Provisioning Profile、用户相册。Signing 只在本地 Xcode Team。
