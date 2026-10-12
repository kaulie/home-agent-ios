# project_map — home-agent-ios 项目地图

本目录按**运行事实**说明本仓库，不是概念词典。

| 文档 | 维度 |
|---|---|
| [positioning.md](positioning.md) | iPhone 客户端：只打 Brain HTTP |
| [architecture.md](architecture.md) | 七套 App、Intent / Asset |
| [tech-stack.md](tech-stack.md) | Swift / Xcode 生成脚本 |
| [deployment.md](deployment.md) | 真机 / Xcode，**不走 :4220** |
| [release.md](release.md) | 无 `build.sh` |
| [development.md](development.md) | 改 Swift 列表后重跑 generate |

根目录 [`AGENT.md`](../../AGENT.md) 是后续 agent 的入口。各 App 细节在各自目录 README。

## 本轮已核对的异议（2026-10-12）

1. **不在 `:4220` 发版。** 真机安装不是平台 deploy。
2. **只打 Brain HTTP。** 不 import Brain / Gateway / sidecar 源码。
3. **主发出窗是 `LivingRoomEdge`（HomeAgent Console）。** 不要把 Admin / Dev 塞进 Console 底栏。
4. **投屏 / `display.photo` 在 Mac Edge**，不在 iPhone Console。
5. **agent-bridge / 本机 chat / admin HTML 不在本仓**（bridge 仍在归档 os）。
6. **README 路径已是仓根相对路径**（不再是 os 的 `ios/LivingRoomEdge/...`）。文档不要链到已失效的 `../../docs/`。
7. **改完 Swift 文件列表必须重跑该 App 的 `generate_xcodeproj.py`。**

后续 agent 若发现上述条目被新代码推翻，删除或改写。
