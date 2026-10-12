# 服务架构

```
LivingRoomEdge (Console)
        │  HTTP
        ▼
  Brain :9527
    POST /api/v1/edge-register     roles: intent_source + runtime + endpoint
    POST /api/v1/edge-heartbeat
    POST /api/v1/intent
    GET  /api/v1/intent_detail
    GET  /api/v1/assets/{id}/content?intent_id=
```

- 底栏「互动」；顶部分段「对话 | 扫描 | 拍照 | 文件 | 录音 | 直播」
- 图只认 `presentation.asset_ref`，禁止把临时 URL 当 identity
- 语音在本机转成中文后再 POST
- 本机 Runtime 边界：`camera.capture` / `light.set`（GoPro / 客厅灯）。其它 plan 步不在 iPhone 执行

源码落点（Console）：

| 东西 | 目录 |
|---|---|
| 主聊天 / 扫描拍照文件录音直播 | `LivingRoomEdge/LivingRoomEdge/App/` |
| 登记 / intent / asset | `LivingRoomEdge/LivingRoomEdge/Brain/` |
| GoPro / 灯 | `GoPro/`、`Light/`（在 LivingRoomEdge 树内） |
| 老机 | `LivingRoomLegacy/` |

每套 App 自带 `generate_xcodeproj.py`，Xcode 工程是生成物。
