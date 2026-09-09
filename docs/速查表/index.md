# 速查表

## 版本钉死

| 用途 | 值 |
|------|----|
| 主路径 Sim | **5.1.0** |
| 对照 Sim | **6.0.1 / latest** |
| 主路径 Python | **≈ 3.11** |
| 对照 Python | **3.12** |
| 命名空间趋势 | `omni.isaac.*` → `isaacsim.*` |
| ROS2（主路径常见） | Humble（以官方页为准） |
| ROS2（对照关注） | Jazzy 等（以 latest 为准） |
| Launcher | **2025-10-01 起弃用** |

## 常用绝对 URL

| 说明 | URL |
|------|-----|
| 5.1.0 首页 | https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html |
| latest | https://docs.isaacsim.omniverse.nvidia.com/latest/ |
| Workflows | https://docs.isaacsim.omniverse.nvidia.com/6.0.0/introduction/workflows.html |
| Standalone Python | https://docs.isaacsim.omniverse.nvidia.com/6.0.1/python_scripting/manual_standalone_python.html |
| Robots simulation | https://docs.isaacsim.omniverse.nvidia.com/latest/python_scripting/robots_simulation.html |
| CLI 扩展模板 | https://docs.isaacsim.omniverse.nvidia.com/latest/utilities/cli_extension_templates.html |
| VS Code 扩展模板 | https://docs.isaacsim.omniverse.nvidia.com/latest/utilities/vscode_extension_template_generator.html |
| ROS2 5.1 | https://docs.isaacsim.omniverse.nvidia.com/5.1.0/ros2_tutorials/ros2_landing_page.html |
| ROS2 latest | https://docs.isaacsim.omniverse.nvidia.com/latest/ros2_tutorials/ros2_landing_page.html |
| install_ros | https://docs.isaacsim.omniverse.nvidia.com/latest/installation/install_ros.html |
| 迁移 6.0 | https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html |
| 扩展重命名 | https://docs.isaacsim.omniverse.nvidia.com/4.5.0/overview/extensions_renaming.html |
| License FAQ | https://docs.isaacsim.omniverse.nvidia.com/latest/common/license-faq.html |
| ROS workspaces | https://github.com/isaac-sim/IsaacSim-ros_workspaces |
| Isaac Lab 代码 | https://github.com/isaac-sim/IsaacLab |
| Isaac Lab 文档 | https://isaac-sim.github.io/IsaacLab/ |

## 本地命令

```bash
# 文档预览（本仓库）
pip install mkdocs-material
mkdocs serve

# 提示：下列路径请改成你的 5.1.0 安装根
# export ISAAC_SIM_ROOT=/path/to/isaac-sim-5.1.0
# "${ISAAC_SIM_ROOT}/isaac-sim.sh"          # GUI 启动（名称以安装为准）
# "${ISAAC_SIM_ROOT}/python.sh" your_script.py   # Standalone

# ROS2 会话（示例：先 source 发行版再启动仿真；Domain 保持一致）
# export ROS_DOMAIN_ID=0
# source /opt/ros/humble/setup.bash
```

把你验证过的**真实**启动命令覆盖笔记中的占位行。

## 学习路径（中文目录）

| 目录 | 章节 |
|------|------|
| `docs/00_前置与安装/` | 安装与兼容性 |
| `docs/01_第一次仿真/` | 最小物理场景 |
| `docs/02_第一次机器人/` | 机械臂入门 |
| `docs/03_USD与Omniverse/` | Stage / Prim / Layer |
| `docs/04_Python接口/` | SimulationApp |
| `docs/05_扩展开发/` | Extension 模板 |
| `docs/06_ROS2集成/` | Bridge + 工作区 |
| `docs/07_Isaac_Lab/` | Lab 与版本矩阵 |
| `docs/08_SDG与传感器/` | 传感器与 SDG |
| `docs/迁移_5到6/` | 对照表 |
| `docs/常见坑/` | 坑位汇总 |
| `docs/术语表.md` / `docs/资源链接.md` | 查阅 |

## 禁止清单

- 不提交 `*.usd*`、安装包、大二进制、合成数据集
- 不混版本会话
- 不把 shim 当长期 API

更多链接：[资源链接](../资源链接.md) · 术语：[术语表](../术语表.md)
