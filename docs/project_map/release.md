# 发布细节

无 `build.sh`、无平台 `outputs/`、无 `deploy-notify`。

「发布」= 合入 `main` 之后，由人在 Xcode 对指定 App 归档 / 真机安装。合入 `main` ≠ 用户手机已更新。

改了 Swift 文件列表却没重跑 `generate_xcodeproj.py`，等于没交付可编译工程。
