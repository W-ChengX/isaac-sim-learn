# 06 ROS2 集成

## 学习目标

- 理解 Isaac Sim 通过 **ROS2 Bridge 扩展** 与外部 ROS 2 图通信（话题 / 服务 / TF 等，以你启用的桥接为准）。
- 能按文档对齐：**Isaac 版本 ↔ Python ↔ ROS 2 发行版**（主路径常对 **Humble**；对照轨关注 **Jazzy** 等更新说明）。
- 使用官方仓库 [IsaacSim-ros_workspaces](https://github.com/isaac-sim/IsaacSim-ros_workspaces)，**clone 在本仓库之外**。
- 完成最小验收：`ros2 topic list` 能看到桥接相关话题，且 Play 时有数据刷新。

## 你将完成什么（验收清单）

- [ ] 笔记写明：Isaac **5.1.0**、内嵌/配套 Python **≈3.11**、ROS 2 发行版（如 Humble）与 `ROS_DOMAIN_ID`
- [ ] 按官方安装说明完成 ROS 侧依赖（见 install_ros）：
      https://docs.isaacsim.omniverse.nvidia.com/latest/installation/install_ros.html
- [ ] 启用 ROS2 Bridge 相关扩展；仿真 Play 后外部 `ros2 topic list` 可见预期话题
- [ ] 至少验证一条「仿真 → ROS」或「ROS → 仿真」的数据路径（传感器或简单命令）
- [ ] `IsaacSim-ros_workspaces` 位于仓库外；本仓仅保留链接与笔记

## 概念讲解（自己的话）

### Bridge 是什么

Isaac 内部是 USD + 仿真步进；ROS 2 是 DDS 上的节点图。Bridge 把两边的消息类型与时钟对齐，让你用熟悉的 `ros2` CLI / rviz / 自有节点对接仿真。它不是「把 Isaac 变成 ROS 发行版」，而是**桥**。

### 版本矩阵（务必记笔记）

| Isaac Sim | 大致 Python | ROS 2 常见组合（以官方页为准） |
|-----------|-------------|-------------------------------|
| 5.1.x（主路径） | **≈ 3.11** | 文档多围绕 **Humble** 等工作区 |
| 6.x（对照） | **≈ 3.12** | 关注 latest ROS2 页对 **Jazzy** 等的说明 |

混用「系统 Humble + 另一套 Jazzy + Isaac 内嵌环境」而不隔离，是 ROS 集成翻车头号原因。

### 官方工作区仓库

https://github.com/isaac-sim/IsaacSim-ros_workspaces
提供与文档配套的示例包与工作区布局。学习策略：

1. 按 Isaac 版本选对应分支/说明；
2. 在仓库外 colcon build；
3. 本 Git 笔记只记：分支名、source 命令、验证过的话题名。

### 中英术语（本节）

| 中文 | English |
|------|---------|
| 桥接扩展 | ROS2 Bridge |
| 工作区 | Workspace |
| 域 ID | ROS_DOMAIN_ID |
| 发行版 | Distro（Humble / Jazzy …） |

## 推荐步骤（链官方）

1. 确认 [00 前置与安装](../00_前置与安装/index.md) 与 [04 Python接口](../04_Python接口/index.md) 已通过；Bridge 依赖正确的 Isaac 运行时。
2. 阅读 ROS 安装要点：
   https://docs.isaacsim.omniverse.nvidia.com/latest/installation/install_ros.html
3. 主路径 ROS2 教程落地页：
   https://docs.isaacsim.omniverse.nvidia.com/5.1.0/ros2_tutorials/ros2_landing_page.html
4. 对照轨同步打开：
   https://docs.isaacsim.omniverse.nvidia.com/latest/ros2_tutorials/ros2_landing_page.html
5. Clone 官方工作区到仓库外，按 README 与上述 landing 页完成最小 bringup：
   https://github.com/isaac-sim/IsaacSim-ros_workspaces
6. 验收：Play → `ros2 topic list` / `echo` → 记录话题与频率到笔记。

## 5.1 vs 6.x 差异要点

- **Python 3.11 vs 3.12** 影响你如何嵌套 venv / 调用 `ros2` 与 Isaac 解释器。
- Landing 页内容随版本调整；**Humble / Jazzy** 支持矩阵以当前打开的官方页为准，勿背第三方旧表。
- 扩展 ID、桥接参数名可能变更；启用失败时先对迁移指南：
  https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html

## 常见坑

- **ROS_DOMAIN_ID / RMW 实现不一致**：两边「都没报错」但谁也看不见谁。
- **混源**：`source` 了多个 ROS 发行版或把 Isaac 环境与系统 ROS 粗暴叠加。
- **未 Play 就判定桥接坏了**：多数话题只在仿真步进后刷新。
- **跟错版本文档**：5.1 步骤套 latest 截图。
- **把整个 ros_workspace build 产物塞进本仓**：体积与许可双重灾难。

## 延伸阅读链接

- ROS2 5.1.0：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/ros2_tutorials/ros2_landing_page.html
- ROS2 latest：https://docs.isaacsim.omniverse.nvidia.com/latest/ros2_tutorials/ros2_landing_page.html
- install_ros：https://docs.isaacsim.omniverse.nvidia.com/latest/installation/install_ros.html
- 工作区：https://github.com/isaac-sim/IsaacSim-ros_workspaces
- 迁移：https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html

上一章：[05 扩展开发](../05_扩展开发/index.md) · 下一章：[07 Isaac Lab](../07_Isaac_Lab/index.md)
