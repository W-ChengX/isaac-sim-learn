# 版本对照（5.1.0 vs 6.0.1）

主路径：**Isaac Sim 5.1.0**。对照轨：**6.0.1 / latest**。

## 速览

| 项 | 5.1.0（主） | 6.0.1 / latest（对照） |
|----|-------------|------------------------|
| Python | **3.11** | **3.12** |
| 包/命名空间 | 大量 `omni.isaac.*` | 迁移为 **`isaacsim.*`** |
| Launcher | 历史路径仍见文档 | **2025-10-01 起 Launcher 弃用**，改用新安装方式 |
| 文档入口 | [5.1.0 文档](https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html) | [latest](https://docs.isaacsim.omniverse.nvidia.com/latest/) |
| 下载 | [5.1.0 download](https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/download.html) | [6.0.1 download](https://docs.isaacsim.omniverse.nvidia.com/6.0.1/installation/download.html) / [quick-install](https://docs.isaacsim.omniverse.nvidia.com/latest/installation/quick-install.html) |

## 命名空间：`omni.isaac` → `isaacsim`

- 5.x 教程与旧脚本常见 `import omni.isaac...`。
- 6.x 以 `isaacsim` 为主；对照时务必看迁移指南，勿盲目全局替换。
- 迁移： [Isaac Sim 6.0 Migration](https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html)

## Launcher 弃用（2025-10-01）

Omniverse Launcher 已弃用。新环境请按 **latest / 6.0.1** 安装页操作；主路径若仍用 5.1.0，以 5.1.0 安装文档为准，并记录你的实际安装方式。

## 禁止混版本

- 同一机器可并存多版本安装目录，但**一个 venv / 一个终端会话只绑一个版本**。
- 不要把 5.1 的扩展、Python 包、`ISAAC_*` 路径指到 6.x（反之亦然）。
- CI / 笔记中写清：`ISAAC_SIM_VERSION=5.1.0`（或 6.0.1）。

## 本章相关链接

- 需求：[5.1.0 requirements](https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/requirements.html)
- 快速安装（latest）：[quick-install](https://docs.isaacsim.omniverse.nvidia.com/latest/installation/quick-install.html)
