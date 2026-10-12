# 部署细节

**不是** `:4220`。没有 runtime 目录，没有 `scripts/restart.sh`。

本机打开主 Console：

```bash
python3 LivingRoomEdge/generate_xcodeproj.py
open LivingRoomEdge/LivingRoomEdge.xcodeproj
```

Signing 只在本地 Xcode Team。真机安装、TestFlight、侧载都听从 `goal` 与人的明确指令，agent 不要自行对用户设备装包。

不要改 `/Users/gaolei/runtime/**`。不要改 os。
