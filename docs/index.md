# 导读 / 学习路径

本站是 **Isaac Sim** 中文自学笔记：主版本 **5.1.0**，对照 **6.0.1 / latest**。写清「你要会什么、怎么验收、容易踩什么坑」，步骤细节以官方文档为准（每章附绝对 URL）。**不内嵌官方资产。**

## 怎么用本站

1. 硬件与安装先过 [00 前置条件](00_prereqs/index.md)，再动手开场景。
2. 每章按固定结构阅读：学习目标 → 验收清单 → 概念 → 推荐步骤 → 版本差异 → 常见坑。
3. 术语不确定时查 [术语表](glossary.md)；官方入口汇总见 [资源链接](links.md)。
4. 本地预览：`pip install mkdocs-material && mkdocs serve`。

## 建议学习路径

| 顺序 | 章节 | 你将得到什么 |
|------|------|----------------|
| 1 | [00 前置条件](00_prereqs/index.md) | 硬件勾选、Compatibility Checker、安装通道、版本钉死、首次启动 |
| 2 | [01 第一个仿真](01_first_sim/index.md) | 简单场景、刚体碰撞、Play、三种工作流意识 |
| 3 | [02 第一个机器人](02_first_robot/index.md) | 加载 Franka 类机械臂、看关节、理解位姿/速度命令 |
| 4 | [03 USD 与 Omniverse](03_usd_omniverse/index.md) | Stage / Prim / 引用与组合（后续批次展开） |
| 5 | [04 Python API](04_python_api/index.md) | Standalone / SimulationApp 脚本化 |
| 6 | [05 Extensions](05_extensions/index.md) | 扩展启用与结构 |
| 7 | [06 ROS2](06_ros2/index.md) | ROS2 bridge 与工作区 |
| 8 | [07 Isaac Lab](07_isaac_lab/index.md) | 学习 / RL 框架入口 |
| 9 | [08 SDG 与传感器](08_sdg_sensors/index.md) | 合成数据与传感器 |
| 10 | [5→6 迁移](migration_5_to_6/index.md) | 对照轨必读 |
| — | [常见坑](pitfalls/index.md) · [速查表](cheatsheets/index.md) · [术语表](glossary.md) · [资源链接](links.md) | 随时查阅 |

## 双轨提醒

- 写笔记时同时记下：**5.1.0 步骤** 与 **6.x 差异**（例如 Python 约 3.11 vs 3.12、命名空间迁移线索）。
- 官方迁移总览：https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html

## 官方对照（总入口）

- **5.1.0**：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
- **latest**：https://docs.isaacsim.omniverse.nvidia.com/latest/
