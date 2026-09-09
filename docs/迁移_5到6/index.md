# 迁移：5.1 → 6.x

## 学习目标

- 能对照官方 **Isaac Sim 6.0 Migration** 索引，梳理自己的脚本 / 扩展 / 笔记要改哪里。
- 掌握一张**对照表**：API / 命名空间、shim 移除、工作流入口、Python 版本。
- 坚持「单会话单版本」：用干净的 6.0.1（或 latest）环境验证，而不是在 5.1 上 `export` 混搭。

## 你将完成什么（验收清单）

- [ ] 读完官方迁移索引并产出提纲：
      https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html
- [ ] 填写本章对照表中「我的项目」列（至少 5 条实际条目）
- [ ] 在干净 6.x 环境用 3.12 解释器跑通一条最小 standalone
- [ ] 确认未再依赖已宣布移除的兼容 shim
- [ ] 更新本仓库笔记链接：主路径仍写 5.1；对照轨单独成段

## 概念讲解（自己的话）

### 迁移不是「只改 import」

大版本通常同时动：

- Python 小版本与二进制扩展；
- 包命名空间（`omni.isaac.*` → `isaacsim.*` 等趋势）；
- 扩展 ID 与默认启用列表；
- 工作流文档结构（GUI / Extension / Standalone）；
- 物理后端与默认参数叙述；
- 临时 **shim**（旧名映射到新实现）的生命周期。

把 shim 当长期 API 用，会在某次小版本更新后突然集体报错。

### 官方页是唯一权威

第三方博客的「5→6 速迁」容易过期。流程应是：官方 migration 索引 → 你的对照表 → 干净环境试跑 → 再改主文档。

## 对照表（模板）

| 主题 | 5.1.0（主路径） | 6.0.x / latest（对照） | 我的项目备注 |
|------|-----------------|------------------------|--------------|
| Python | ≈ **3.11** | **3.12** | |
| 命名空间趋势 | 常见 `omni.isaac.*` | 文档与示例更多 `isaacsim.*` | |
| Standalone 入口文档 | 5.1 文档树 scripting | [manual_standalone_python](https://docs.isaacsim.omniverse.nvidia.com/6.0.1/python_scripting/manual_standalone_python.html) | |
| 工作流说明 | 分散在教程中 | [workflows](https://docs.isaacsim.omniverse.nvidia.com/6.0.0/introduction/workflows.html) 更集中 | |
| ROS2 | [5.1 landing](https://docs.isaacsim.omniverse.nvidia.com/5.1.0/ros2_tutorials/ros2_landing_page.html) | [latest landing](https://docs.isaacsim.omniverse.nvidia.com/latest/ros2_tutorials/ros2_landing_page.html)；关注 Humble/Jazzy | |
| 扩展 ID | 旧笔记可能过时 | 查迁移页 + [历史重命名](https://docs.isaacsim.omniverse.nvidia.com/4.5.0/overview/extensions_renaming.html) | |
| Shim / 兼容层 | 部分旧 API 仍可用 | **计划移除**；改为新 API | |
| 物理后端叙述 | 多 PhysX | 更多后端/Newton 相关说明 | |
| Lab 兼容 | 查旧 tag | 常对齐较新 Sim；见 Lab 文档矩阵 | |
| 安装通道 | zip/workstation 等 | 同左，但路径与包布局可能变；Launcher 已弃用 | |

## 推荐步骤（链官方）

1. 打开迁移总索引，按左侧目录逐节记「是否命中我的代码」：
   https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html
2. 精读 standalone 与 workflows 对照页：
   https://docs.isaacsim.omniverse.nvidia.com/6.0.1/python_scripting/manual_standalone_python.html
   https://docs.isaacsim.omniverse.nvidia.com/6.0.0/introduction/workflows.html
3. 机器人脚本与装配：
   https://docs.isaacsim.omniverse.nvidia.com/latest/python_scripting/robots_simulation.html
   https://docs.isaacsim.omniverse.nvidia.com/6.0.1/robot_setup_tutorials/index.html
4. ROS2 双边 landing 对照：
   https://docs.isaacsim.omniverse.nvidia.com/5.1.0/ros2_tutorials/ros2_landing_page.html
   https://docs.isaacsim.omniverse.nvidia.com/latest/ros2_tutorials/ros2_landing_page.html
5. 在**新目录**安装 6.0.1，验证一条脚本；把 diff 记回上表。
6. 回到仓库 [VERSIONS.md](../../VERSIONS.md) 核对钉死策略。

## 5.1 vs 6.x 差异要点

（本章即差异本身——执行时以官方 migration 正文为准，下表仅作记忆锚点。）

- 解释器与包布局绑定大版本；禁止混 `PYTHONPATH`。
- API 重命名后删除 shim = 硬失败；尽早改调用点。
- 文档信息架构调整：许多「以前藏在别处」的内容在 6.x 有独立 URL。

## 常见坑

- **只全局替换包名**：生命周期 / 异步 API 未改，运行中期崩溃。
- **继续依赖 shim**：CI 在新镜像上集体红。
- **Launcher 旧路径写进脚本**：2025-10-01 后安装方式已变。
- **扩展静默未加载**：ID 变更但启动脚本仍写旧名。
- **对照轨验证完又污染主路径**：用容器或完全分离的安装根。

## 延伸阅读链接

- 迁移索引：https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html
- 5.1.0：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
- latest：https://docs.isaacsim.omniverse.nvidia.com/latest/
- Standalone 6.0.1：https://docs.isaacsim.omniverse.nvidia.com/6.0.1/python_scripting/manual_standalone_python.html
- Workflows：https://docs.isaacsim.omniverse.nvidia.com/6.0.0/introduction/workflows.html
- 扩展重命名背景：https://docs.isaacsim.omniverse.nvidia.com/4.5.0/overview/extensions_renaming.html

返回：[导读](../index.md) · [常见坑](../常见坑/index.md) · [速查表](../速查表/index.md)
