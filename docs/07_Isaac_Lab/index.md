# 07 Isaac Lab

## 学习目标

- 说明 **Isaac Lab** 与 **Isaac Sim** 的分工：Sim 是仿真应用；Lab 是面向学习 / RL 的环境与工作流框架（独立仓库与文档）。
- 能按 Lab 官方文档完成**独立环境**安装，并跑通一个最小 env / demo。
- 建立强制习惯：查阅并记录 **Lab 版本（tag/commit）↔ Isaac Sim 版本** 兼容矩阵，避免「主路径 5.1」与「Lab 需要 6.x」硬撞。

## 你将完成什么（验收清单）

- [ ] 打开 Lab 文档与 GitHub，记下当前推荐的 Sim 版本要求：
      https://isaac-sim.github.io/IsaacLab/
      https://github.com/isaac-sim/IsaacLab
- [ ] 在**独立**环境安装 Lab（勿污染主路径 5.1 的 site-packages）
- [ ] 跑通官方最小示例；日志与数据集留在仓库外
- [ ] 笔记固定一张表：`Lab tag/commit` + `Isaac Sim version` + `Python` + `CUDA/PyTorch` 来源
- [ ] 若矩阵要求 Sim 6.x：明确这是对照轨任务，不在 5.1 会话里强行混装

## 概念讲解（自己的话）

### 为什么需要 Lab

直接在 Isaac Sim 里写 RL 循环可行，但环境定义、向量化、训练配置、管理器模式等会快速失控。Lab 把「任务环境」抽象成可配置模块，让你把精力放在奖励、观测与算法，而不是每次重搭仿真样板。

### 版本矩阵（最重要的一页笔记）

Lab 发版节奏与 Sim 不完全同步。典型翻车：

- 教程默认 Lab 新版本，而你主路径钉死 **5.1.0**；
- 强行 pip 混装导致 Sim 扩展与 PyTorch/CUDA 冲突。

**策略**：

1. 先读 Lab 文档的 Installation / Compatibility；
2. 需要 6.x 就开**对照轨**干净环境；
3. 主路径 5.1 仅跟与之兼容的 Lab 旧 tag（若仍需要），否则把 Lab 练习整体放到对照轨。

### 与本仓库的边界

- 本仓库继续 **no-assets / 无大数据集**；
- Lab 的输出、checkpoint、视频一律仓库外；
- 这里只保留概念、验收清单与官方链接。

### 中英术语（本节）

| 中文 | English |
|------|---------|
| 环境（RL） | Environment / Env |
| 向量化环境 | Vectorized env |
| 兼容矩阵 | Compatibility matrix |
| 管理器模式 | Manager-based workflow |

## 推荐步骤（链官方）

1. 确认你已能在 Sim 里加载机器人并理解 Articulation（[02](../02_第一次机器人/index.md)、[04](../04_Python接口/index.md)）。
2. 阅读 Lab 用户文档安装与快速开始：
   https://isaac-sim.github.io/IsaacLab/
3. 对照 GitHub README / release note，确认兼容的 Isaac Sim：
   https://github.com/isaac-sim/IsaacLab
4. 在独立目录创建环境并跑官方最小 demo；把命令摘要抄进 [速查表](../速查表/index.md)。
5. 回到 Sim 文档首页，确认你对照的是 5.1 还是 latest：
   https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
   https://docs.isaacsim.omniverse.nvidia.com/latest/
6. 若跨大版本，同时打开迁移指南：
   https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html

## 5.1 vs 6.x 差异要点

- Lab 新版本更常对齐 **较新的 Sim（含 6.x）**；主路径 5.1 用户必须先查矩阵再决定是否升级对照轨。
- Python **3.11 vs 3.12**、PyTorch 轮子、CUDA 驱动要与 Lab 文档一致。
- 不要假设「Lab 示例里的 import」在 5.1 的 `omni.isaac.*` 世界里原样可用。

## 常见坑

- **忽略兼容表**：装完才发现必须 Sim 6.x。
- **在同一个 conda env 塞进 Sim 与训练栈**：升级任一端即崩。
- **把大数据集 / checkpoint 提交 Git**：用 LFS 也往往不值得；保持在外。
- **文档跟错 fork/旧 commit**：以官方 IsaacLab 仓库与文档站点为准。

## 延伸阅读链接

- Lab 文档：https://isaac-sim.github.io/IsaacLab/
- Lab 代码：https://github.com/isaac-sim/IsaacLab
- Sim 5.1.0：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
- Sim latest：https://docs.isaacsim.omniverse.nvidia.com/latest/
- 迁移：https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html

上一章：[06 ROS2集成](../06_ROS2集成/index.md) · 下一章：[08 SDG与传感器](../08_SDG与传感器/index.md)
