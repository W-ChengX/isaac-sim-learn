# 导读 / 学习路径

本站是 **Isaac Sim** 中文自学笔记：主版本 **5.1.0**，对照 **6.0.1 / latest**。写清「你要会什么、怎么验收、容易踩什么坑」，步骤细节以官方文档为准（每章附绝对 URL）。**不内嵌官方资产。**

## 本站怎么分区

| 分区 | 内容 | 怎么用 |
|------|------|--------|
| **主路径** | 00–08 | **按序学**：安装 → 第一次仿真 → 机器人 → USD → Python → 扩展 → ROS2 → Lab → SDG |
| **对照与升级** | [迁移 5到6](迁移_5到6/index.md) | **不默认当第 10 步**；你已在 5.1 跑通、准备碰 6.x 时再读 |
| **参考** | [术语表](术语表.md) · [常见坑](常见坑/index.md) · [速查表](速查表/index.md) · [资源链接](资源链接.md) | 随时查，不占学习顺序 |
| **元信息** | [VERSIONS](VERSIONS.md) · [LICENSE-NOTES](LICENSE-NOTES.md) · [写作规范](写作规范.md) | 版本钉死、许可与笔记写法 |

## 怎么用本站

1. 硬件与安装先过 [00 前置与安装](00_前置与安装/index.md)，再动手开场景。
2. 每章按固定结构阅读：学习目标 → 验收清单 → 概念 → 推荐步骤 → 版本差异 → 常见坑。
3. 术语不确定时查 [术语表](术语表.md)；官方入口汇总见 [资源链接](资源链接.md)。
4. 本地预览：`pip install mkdocs-material && mkdocs serve`。

## 建议学习路径（主路径 00–08）

| 顺序 | 章节 | 你将得到什么 |
|------|------|----------------|
| 1 | [00 前置与安装](00_前置与安装/index.md) | 硬件勾选、Compatibility Checker、安装通道、版本钉死、首次启动 |
| 2 | [01 第一次仿真](01_第一次仿真/index.md) | 简单场景、刚体碰撞、Play、三种工作流意识 |
| 3 | [02 第一次机器人](02_第一次机器人/index.md) | 加载 Franka 类机械臂、看关节、理解位姿/速度命令 |
| 4 | [03 USD与Omniverse](03_USD与Omniverse/index.md) | Stage / Prim / Layer / 引用与组合 |
| 5 | [04 Python接口](04_Python接口/index.md) | Standalone / SimulationApp 脚本化 |
| 6 | [05 扩展开发](05_扩展开发/index.md) | 扩展启用、模板与目录结构 |
| 7 | [06 ROS2集成](06_ROS2集成/index.md) | ROS2 bridge、Humble/Jazzy、官方工作区 |
| 8 | [07 Isaac Lab](07_Isaac_Lab/index.md) | 学习 / RL 框架入口与版本矩阵 |
| 9 | [08 SDG与传感器](08_SDG与传感器/index.md) | 合成数据与传感器 |

## 对照轨何时读

- 主路径验收仍按 **5.1.0**；不必为了「学完」硬读迁移章。
- 当你已经在 5.1 跑通关键章节，并准备安装 / 试用 **6.0.1 / latest** 时，再打开 [迁移 5到6](迁移_5到6/index.md)。
- 对照时用干净环境，禁止与 5.1 混 `PATH` / `PYTHONPATH`。
- 官方迁移总览：https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html

## 双轨提醒

- 写笔记时同时记下：**5.1.0 步骤** 与 **6.x 差异**（例如 Python 约 3.11 vs 3.12、命名空间迁移线索）。
- 版本权威页：[VERSIONS.md](VERSIONS.md)；许可与资产边界：[LICENSE-NOTES.md](LICENSE-NOTES.md)。

## 官方对照（总入口）

- **5.1.0**：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
- **latest**：https://docs.isaacsim.omniverse.nvidia.com/latest/
