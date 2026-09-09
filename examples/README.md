# examples/

本目录放**你本机可跑的最小脚本 / 说明**，对应主路径章节练习。仓库**不包含**任何 NVIDIA 官方 USD、贴图、模型或 Assets Pack——那些只应从本机 Isaac Sim 安装目录加载。

## 硬性约定

- **禁止**提交官方资产（`.usd` / `.usda` / `.usdc` / `.usdz`、贴图、机器人模型、安装包）。
- 需要官方示例时，在注释写本机路径：`# asset: <ISAAC_SIM>/...`。
- 默认假设 **Isaac Sim 5.1.0**；若脚本针对 6.0.1，在文件名或文件头标明。
- 根目录 `.gitignore` 已忽略常见资产后缀；不要用 `git add -f` 强行加入。

## 建议布局（与章节镜像）

```
examples/
  README.md                 # 本说明
  01_first_sim/             # 对应 docs/01_第一次仿真
  02_first_robot/           # （可选）对应 02
  04_python/                # 对应 docs/04_Python接口
  05_extension/             # （可选）
  06_ros2/                  # （可选）
```

当前仓库已提供占位：

| 目录 | 用途 |
|------|------|
| [`01_first_sim/`](01_first_sim/) | 第一次仿真：最短 GUI / 脚本笔记 |
| [`04_python/`](04_python/) | Standalone / SimulationApp 最小脚本 |

空目录靠 `.gitkeep` 保留；你往里面加 `.py` 后可删掉 `.gitkeep`。

## 下一步

1. 完成 `docs/01_第一次仿真` 与 `docs/04_Python接口` 验收。
2. 在对应子目录放入自有最小脚本（无官方 USD）。
3. 脚本头写明：`ISAAC_SIM_VERSION`、启动方式、依赖的本机资产路径（仅文字）。
