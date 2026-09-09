# 00 前置条件

## 学习目标

- 确认 GPU / 驱动 / OS 满足官方要求。
- 仅安装并固定 **Isaac Sim 5.1.0**（主路径）；了解 6.0.1 安装入口但不混用。
- 能独立启动 GUI，并记录安装路径与 Python 版本。

## 官方链接

**5.1.0**

- 总览：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
- 需求：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/requirements.html
- 下载：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/download.html

**latest / 6.0.1（对照，勿与主路径混装会话）**

- latest 首页：https://docs.isaacsim.omniverse.nvidia.com/latest/
- 快速安装：https://docs.isaacsim.omniverse.nvidia.com/latest/installation/quick-install.html
- 6.0.1 下载：https://docs.isaacsim.omniverse.nvidia.com/6.0.1/installation/download.html
- 产品页：https://developer.nvidia.cn/isaac/sim

## 本地验收清单

- [ ] 对照 requirements 勾选：GPU、驱动、磁盘、内存
- [ ] 安装目录可启动 Isaac Sim **5.1.0** GUI
- [ ] 终端中确认绑定 Python **3.11**（5.1.0）
- [ ] 笔记写明：`ISAAC_SIM_VERSION=5.1.0` 与安装路径
- [ ] 已读 [VERSIONS.md](../../VERSIONS.md) 与 [LICENSE-NOTES.md](../../LICENSE-NOTES.md)

## 常见坑（占位）

- TODO：驱动过旧导致黑屏 / 无法启动
- TODO：Launcher 弃用后仍按旧教程安装
- TODO：5.1 与 6.x 环境变量互相覆盖
