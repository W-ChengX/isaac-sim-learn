# 06 ROS2

## 学习目标

- 打通 Isaac Sim ↔ ROS2 基础桥接（话题可见即可）。
- 使用官方 ros_workspaces，不向本仓库塞大型工作区二进制。
- 对照 5.1 与 latest 的 ROS2 landing 页。

## 官方链接

**5.1.0**

- ROS2 tutorials：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/ros2_tutorials/ros2_landing_page.html

**latest（对照）**

- ROS2 tutorials：https://docs.isaacsim.omniverse.nvidia.com/latest/ros2_tutorials/ros2_landing_page.html
- 工作区仓库：https://github.com/isaac-sim/IsaacSim-ros_workspaces

## 本地验收清单

- [ ] ROS2 发行版与文档要求一致（笔记写明）
- [ ] `ros2 topic list` 能看到 Isaac 相关话题（按官方教程）
- [ ] 仿真 Play 时有数据更新
- [ ] 工作区 clone 在仓库外，本仓仅留链接与笔记

## 常见坑（占位）

- TODO：ROS_DOMAIN_ID / DDS 不匹配
- TODO：Isaac 内嵌 ROS 与系统 ROS 混源
- TODO：版本文档跟错（5.1 vs latest）
