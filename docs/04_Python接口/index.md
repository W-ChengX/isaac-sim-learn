# 04 Python 接口

## 学习目标

- 分清三种入口里 Python 的位置：**GUI 内脚本 / Extension**、**Standalone（SimulationApp）**。
- 能用**该版本自带解释器**跑通最小 standalone 骨架（空场景或官方 hello 类示例）。
- 记住双轨差异：**5.1 ≈ Python 3.11**、包名常落在 `omni.isaac.*`；**6.x ≈ Python 3.12**、更多文档与示例走向 `isaacsim.*`。
- 脚本**不**捆绑官方 USD；资产路径用本机文字配置。

## 你将完成什么（验收清单）

- [ ] 定位并使用 5.1.0 安装树内的 Python（而非随意系统 `python3`）
- [ ] 跑通一条 standalone：创建 `SimulationApp` → 步进若干帧 → **干净关闭**
- [ ] 笔记写明：解释器路径、`ISAAC_SIM_VERSION`、头显/无头模式
- [ ] 对照打开 6.0.1 standalone 手册，列出自己脚本里可能要改的 import
- [ ] 退出码 0；无「进程残留占用 GPU」的习惯性强杀

## 概念讲解（自己的话）

### SimulationApp 生命周期

Standalone 的第一件事通常是拉起 Kit 运行时：配置是否显示 GUI、分辨率、额外扩展等，然后你才 import 依赖 Stage 的模块。结束时要按文档关闭应用，否则容易留下僵尸进程或锁住 GPU。

直觉顺序：

1. 创建 `SimulationApp`（或文档等价入口）
2. 导入场景操作 / 机器人相关模块
3. 打开 Stage 或创建简单 Prim
4. 循环 `world.step` / 应用 update（以你版本文档为准）
5. 关闭 SimulationApp

### 为何「用错 Python」灾难巨大

Isaac 自带一堆编译扩展。系统 Python 即使 `import` 碰巧成功，也常在进入仿真循环时崩溃。原则：**启动器、解释器、site-packages 来自同一安装树**。

### 与 GUI / Extension 脚本的差别

| 模式 | 谁创建应用 | 典型用途 |
|------|------------|----------|
| GUI + Script Editor | 你已打开的 Isaac | 快速试 API、点选后改属性 |
| Extension | 应用已运行，扩展管理加载 | 工具面板、长期功能 |
| Standalone | 脚本自己 `SimulationApp` | 批跑、CI、无头数据生成 |

同一套 Stage/Prim 概念通用；差别是生命周期归属。工作流总览：
https://docs.isaacsim.omniverse.nvidia.com/6.0.0/introduction/workflows.html

### 机器人相关脚本

有了 Stage 直觉后，再看「用 Python 加载/控制机器人」的专题页（对照轨）：
https://docs.isaacsim.omniverse.nvidia.com/latest/python_scripting/robots_simulation.html

### 中英术语（本节）

| 中文 | English |
|------|---------|
| 独立脚本 | Standalone |
| 仿真应用入口 | SimulationApp |
| 无头模式 | Headless |
| 命名空间迁移 | Namespace migration |

## 推荐步骤（链官方）

1. 读完 [03 USD与Omniverse](../03_USD与Omniverse/index.md)，准备好一个 Prim 路径字符串。
2. 主路径从 5.1.0 文档目录进入 Python / scripting 章节：
   https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
3. 对照精读 standalone 手册（6.0.1 页对结构很清晰，概念可映射回 5.1）：
   https://docs.isaacsim.omniverse.nvidia.com/6.0.1/python_scripting/manual_standalone_python.html
4. 按官方示例跑空世界 / hello；把启动命令写进 [速查表](../速查表/index.md)。
5. 浏览机器人仿真脚本页，标出「下一章扩展 / ROS2 之前先掌握的 API」：
   https://docs.isaacsim.omniverse.nvidia.com/latest/python_scripting/robots_simulation.html
6. 打开迁移指南，搜索与 Python / 命名空间相关条目：
   https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html

## 5.1 vs 6.x 差异要点

| 项 | 5.1.0（主路径） | 6.x（对照） |
|----|-----------------|-------------|
| Python | ≈ **3.11** | **3.12** |
| 包名趋势 | 常见 `omni.isaac.*` | 文档更多 `isaacsim.*` |
| 手册入口 | 跟 5.1 文档树 | standalone 专页更醒目 |
| Shim | 旧代码可能仍能跑一阵 | 过渡层会移除，勿长期依赖 |

不要在同一 shell 里把两种版本的 `PYTHONPATH` 拼在一起。

## 常见坑

- **系统 Python / conda base 硬跑**：import 成功、步进崩溃。
- **忘记关闭 SimulationApp**：二次启动报 GPU/端口占用。
- **混版本 site-packages**：症状像随机 `ModuleNotFoundError` 或 ABI 错误。
- **在 Standalone 里假设 GUI 选中状态**：没有「当前选中 Prim」，路径必须写死或参数化。
- **把官方示例 USD 拷进仓库**：违反 no-assets；改用本机路径配置。

## 延伸阅读链接

- 5.1.0：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
- Standalone 6.0.1：https://docs.isaacsim.omniverse.nvidia.com/6.0.1/python_scripting/manual_standalone_python.html
- Robots simulation：https://docs.isaacsim.omniverse.nvidia.com/latest/python_scripting/robots_simulation.html
- Workflows：https://docs.isaacsim.omniverse.nvidia.com/6.0.0/introduction/workflows.html
- 迁移：https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html

上一章：[03 USD与Omniverse](../03_USD与Omniverse/index.md) · 下一章：[05 扩展开发](../05_扩展开发/index.md)
