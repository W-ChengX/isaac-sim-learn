# 01 第一次仿真

## 学习目标

- 在 **5.1.0** 里跑通「看得见、能 Play」的最短物理场景（Simple Room，或地面 + 灯 + 立方体）。
- 理解 **Rigid Body（刚体）** 与 **Collider（碰撞体）** 必须成对才有「掉下去、撞得上」。
- 会用工具栏 **Play / Stop / 重置**，观察视口中的仿真推进。
- 建立三种工作流意识：**GUI**、**Extension 内脚本**、**Standalone**——本章先以 GUI 验收，不抄官方长文。

## 你将完成什么（验收清单）

- [ ] 启动 Isaac Sim **5.1.0** GUI，Stage 非空或能自行创建简单场景
- [ ] 场景中有地面（或房间）与至少一个可动物体（如 cube）
- [ ] 该物体具备刚体 + 碰撞；点击 Play 后能下落或与地面相互作用
- [ ] 能 Stop / 重置，再次 Play 行为可重复
- [ ] 口头或笔记能区分：GUI 点选、扩展里跑代码、终端 Standalone 三种入口
- [ ] **未**把任何官方 `.usd` 复制进本 Git 仓库（只写本机路径文字）

## 概念讲解（自己的话）

### 场景最小集合

一个「能演示物理」的最小舞台通常包括：

1. **参考地面或房间**：提供碰撞平面与空间感（官方常用 Simple Room 一类示例）。
2. **光照**：否则视口里物体发黑，新手容易误判「没加载成功」。
3. **动态物体**：例如立方体；仅有 mesh 还不够，还要挂上物理相关属性。

### 刚体 ≠ 碰撞体

- **Rigid Body**：告诉物理引擎「请积分我的运动」。
- **Collider**：告诉引擎「我的碰撞形状长这样」。
只有刚体、没有碰撞：可能穿地或根本不参与接触。只有碰撞、没有刚体：更像静态障碍。两者都开，Play 后才会出现下落、弹跳、堆叠等直觉现象。

### Play 在做什么

按下 Play，时间开始推进：物理步进、动画与部分传感器逻辑进入「仿真态」。Stop 停住；重置通常回到播放前的初始状态。验收时至少走一遍「Play → 观察 → Stop/重置 → 再 Play」。

### 三种工作流（先认识，后深入）

| 工作流 | 你怎么启动 | 典型用途 |
|--------|------------|----------|
| GUI | 打开 Isaac Sim 窗口，菜单/拖拽/属性面板 | 探索、摆场景、目视验收 |
| Extension | 应用已运行，在扩展或 Script Editor 里执行 | 交互工具、面板、边看边改 |
| Standalone | 终端用该版本 Python + `SimulationApp` | 批处理、无头、自动化测试 |

同一套 Stage / Prim 概念三处通用；差别在「谁创建应用生命周期」。对照阅读：
https://docs.isaacsim.omniverse.nvidia.com/6.0.0/introduction/workflows.html

### 中英术语（本节）

| 中文 | English |
|------|---------|
| 舞台 | Stage |
| 图元 | Prim |
| 刚体 | Rigid Body |
| 碰撞体 | Collider |
| 播放仿真 | Play |

## 推荐步骤（可操作，细节点官方）

> 下列是**骨架**，具体按钮名与菜单路径以你打开的官方 Quickstart 为准，勿机械背博客截图。

1. 确认 [00 前置与安装](../00_前置与安装/index.md) 已通过，主路径为 **5.1.0**。
2. 打开官方 Quickstart，按文档加载 **Simple Room**（或等价入门场景）；若文档引导手搭场景，则创建地面、灯光、立方体。
   - 5.1.0：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/introduction/quickstart_isaacsim.html
3. 选中动态物体，检查是否启用刚体与碰撞；缺失则按属性面板补齐（以 GUI 提示为准）。
4. 点击 **Play**，观察物体是否与地面发生合理接触；再 Stop / 重置并重放。
5. 在笔记中用文字记录：本机示例路径、版本号、是否首次着色器缓存已完成。
6. 抽 10 分钟浏览 workflows 页，对照三张「入口」表，不要求本章就写 Standalone。

可选对照（机器人向 quickstart，场景更复杂，不必本章做完）：
https://docs.isaacsim.omniverse.nvidia.com/latest/introduction/quickstart_isaacsim_robot.html

## 5.1 vs 6.x 差异要点

- 入门场景名称、菜单入口可能微调；**以你安装版本的文档为准**，不要混用 5.1 截图与 6.x 路径。
- 6.x 对 workflows 有更集中的说明页（见上）；主路径验收仍在 5.1.0 GUI 完成即可。
- 物理后端叙述在 6.x 更多元（PhysX / Newton 等）；本章只要求「Play 后有可重复的接触行为」。

## 常见坑

- **找不到示例**：安装根目录不同，路径会变；用官方文档中的定位方式，勿把 `.usd` 拷进仓库「图省事」。
- **有模型但不掉落**：常缺刚体或碰撞；或 Play 根本没按下。
- **穿地**：碰撞近似过粗、地面无 collider、或单位/缩放异常。
- **首次启动极慢**：着色器缓存，见第 00 章；与「场景坏了」区分。
- **误提交官方资产**：Git 里出现大型 `.usd` / 贴图 → 立刻移出并写入 ignore；遵守 no-assets。
- **扩展未启用导致面板缺失**：GUI 里找不到物理属性时，先查扩展是否被关掉，而不是重装整个软件。

## 延伸阅读 / 官方对照

**5.1.0**

- 首页：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
- Quickstart：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/introduction/quickstart_isaacsim.html

**latest / 6.0.x**

- latest 首页：https://docs.isaacsim.omniverse.nvidia.com/latest/
- 机器人 Quickstart：https://docs.isaacsim.omniverse.nvidia.com/latest/introduction/quickstart_isaacsim_robot.html
- Workflows：https://docs.isaacsim.omniverse.nvidia.com/6.0.0/introduction/workflows.html
- 迁移：https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html
- License FAQ：https://docs.isaacsim.omniverse.nvidia.com/latest/common/license-faq.html

下一章：[02 第一次机器人](../02_第一次机器人/index.md)
