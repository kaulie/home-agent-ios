# home-agent-ios

家庭 Agent 的 iPhone 客户端仓。只打 Brain HTTP（登记 / 心跳 / intent / asset），**不知道** sidecar 源码，也不 import Brain / Gateway。

源码从冻结的 [`home-agent-os/ios`](https://github.com/kaulie/home-agent-os) 迁出；os 本身不再改这些 App。

Brain：LAN 身份 `http://brain.local:9527`，Cloud 默认 `http://49.234.45.173:9527`。

## App

| 目录 | 名称 | 最低系统 | 职责 |
|------|------|----------|------|
| [LivingRoomEdge](LivingRoomEdge/) | HomeAgent Console | iOS 16 | 主发出窗：Intent Source + Endpoint + 有限 Runtime（GoPro / 客厅灯） |
| [LivingRoomLegacy](LivingRoomLegacy/) | HomeAgent Legacy | iOS 12 | 老机文字 intent + 直播推流 |
| [HomeAgentAdmin](HomeAgentAdmin/) | HomeAgent Admin | iOS 16 | 业务运行态：节点 / 策略 / 事件 |
| [HomeAgentDev](HomeAgentDev/) | HomeAgent Dev | iOS 16 | Issue / Dev Task / Fleet |
| [HomeAgentPickup](HomeAgentPickup/) | HomeAgent Pickup | iOS 16 | 手机麦 → Mac `voice.stream` |
| [LivingRoomPickup](LivingRoomPickup/) | 拾音 | iOS 12 | 老机拾音 |
| [HomeAgentRelay](HomeAgentRelay/) | HomeAgent Relay | iOS 16 | 热点 HTTP 中继实验 |

不要把 Admin / Dev 开关塞进 Console 底栏。

## 打开主 Console

```bash
git clone https://github.com/kaulie/home-agent-ios.git
cd home-agent-ios
python3 LivingRoomEdge/generate_xcodeproj.py
open LivingRoomEdge/LivingRoomEdge.xcodeproj
```

- 主屏幕名称：`HomeAgent Console`
- Bundle ID：`com.gaolei.livingroom.edge.iphone`
- 真机需麦克风 + 语音识别权限

改完 Swift 文件列表后重新跑对应目录的 `generate_xcodeproj.py`。其它 App 打开方式见各自 README。

## Console 做什么

```text
启动 / 改 Brain URL
        │
 POST /api/v1/edge-register
   roles: intent_source + runtime + endpoint
        │
 POST /api/v1/edge-heartbeat
        │
 POST /api/v1/intent  →  GET /api/v1/intent_detail
```

- 底栏「互动」；顶部分段「对话 | 扫描 | 拍照 | 文件 | 录音 | 直播」
- 图只认 `presentation.asset_ref`，走 `GET /api/v1/assets/{id}/content?intent_id=`
- 语音在本机转成中文后再 POST

## 明确不做

- `display.photo` / 投电视（仍由 Mac Edge / Cast）
- 执行除 `camera.capture` / `light.set` 以外的 plan
- Android（另仓）、agent-bridge / chat / admin 本机页（不在本仓）
