# 04 Python API

## 学习目标

- 运行 standalone Python 脚本启动 / 控制仿真。
- 分清 5.1（`omni.isaac` / Py3.11）与 6.x（`isaacsim` / Py3.12）。
- 写出最小可复现脚本骨架（不含官方 USD）。

## 官方链接

**5.1.0**

- 文档首页（Python / scripting 从目录进入）：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html

**6.0.1 / latest（对照）**

- Standalone Python：https://docs.isaacsim.omniverse.nvidia.com/6.0.1/python_scripting/manual_standalone_python.html
- 迁移指南：https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html
- 源码：https://github.com/isaac-sim/IsaacSim

## 本地验收清单

- [ ] 用官方推荐入口跑通 hello / empty-world 类脚本
- [ ] `import` 与版本一致（5.1 勿强行用 6.x 包名）
- [ ] 脚本仅引用本机资产路径或空场景
- [ ] 退出码为 0，无未捕获异常

## 常见坑（占位）

- TODO：用系统 Python 而非 Isaac 自带解释器
- TODO：异步 / SimulationApp 生命周期错误
- TODO：混版本 site-packages
