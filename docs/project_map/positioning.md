# 项目定位

## 一句话

home-agent-ios 是家庭 Agent 的 iPhone 客户端仓：登记 / 心跳 / 发 intent / 拉 presentation。不是 Brain，不是 Mac Edge，不是 sidecar。

仓库：[`https://github.com/kaulie/home-agent-ios`](https://github.com/kaulie/home-agent-ios)

Brain：LAN `http://brain.local:9527`，Cloud `http://49.234.45.173:9527`。

## 七套 App

| 目录 | 屏幕名 | 最低系统 | 职责 |
|---|---|---|---|
| `LivingRoomEdge` | HomeAgent Console | iOS 16 | **主发出窗**：Intent Source + Endpoint + 有限 Runtime（GoPro / 客厅灯） |
| `LivingRoomLegacy` | HomeAgent Legacy | iOS 12 | 老机文字 intent + 直播推流 |
| `HomeAgentAdmin` | HomeAgent Admin | iOS 16 | 业务运行态：节点 / 策略 / 事件 |
| `HomeAgentDev` | HomeAgent Dev | iOS 16 | Issue / Dev Task / Fleet |
| `HomeAgentPickup` | HomeAgent Pickup | iOS 16 | 手机麦 → Mac `voice.stream` |
| `LivingRoomPickup` | 拾音 | iOS 12 | 老机拾音 |
| `HomeAgentRelay` | HomeAgent Relay | iOS 16 | 热点 HTTP 中继实验 |

Console Bundle ID：`com.gaolei.livingroom.edge.iphone`。

## 它不是什么

| 不是 | 谁才是 |
|---|---|
| 规划 / 能力目录 | Brain + 集市 |
| 投电视 / `display.photo` | Gateway（Mac Edge） |
| Android | [`home-agent-android`](https://github.com/kaulie/home-agent-android) |
| agent-bridge / chat / admin 本机页 | 不在本仓；bridge 仍在 os |
| `:4220` 服务 | Brain / Gateway / 集市 |
