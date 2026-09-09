# 5.1 → 6.x 迁移对照

## 学习目标

- 列出从 5.1.0 到 6.0.1 / latest 的关键破坏性变更。
- 能对照官方迁移指南改自己的笔记与脚本。
- 坚持「单会话单版本」，用对照轨验证而非混装。

## 官方链接

**迁移（latest）**

- Isaac Sim 6.0 Migration：https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html

**版本锚点**

- 5.1.0：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
- latest：https://docs.isaacsim.omniverse.nvidia.com/latest/
- 6.0.1 Standalone Python：https://docs.isaacsim.omniverse.nvidia.com/6.0.1/python_scripting/manual_standalone_python.html
- 6.0.1 Robot setup：https://docs.isaacsim.omniverse.nvidia.com/6.0.1/robot_setup_tutorials/index.html

另见仓库根目录 [VERSIONS.md](../../VERSIONS.md)。

## 本地验收清单

- [ ] 读完官方 6.0 migration 索引页并做笔记提纲
- [ ] 列出本仓库脚本中需改的 import / API（占位表）
- [ ] 在干净的 6.0.1 环境试跑一条对照脚本
- [ ] 确认 Python 3.12 与 `isaacsim` 命名空间

## 常见坑（占位）

- TODO：只改包名不改生命周期 API
- TODO：Launcher 弃用后安装路径变更未更新文档
- TODO：扩展 ID 重命名导致静默未加载
