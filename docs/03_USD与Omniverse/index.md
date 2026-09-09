# 03 USD 与 Omniverse

## 学习目标

- 用自己的话解释 **Stage / Prim / Attribute / Layer**，以及 Reference 与 Payload 的使用动机。
- 能在 GUI 的 Stage 树中定位目标 Prim，并在属性面板读改常见属性（Xform、可见性等）。
- 理解 Isaac Sim 场景几乎都以 **OpenUSD** 表达；Omniverse Kit 提供运行时与扩展生态。
- 明确本仓库 **不存放** 官方或大型 `.usd` 文件，只在笔记中写本机路径文字。

## 你将完成什么（验收清单）

- [ ] 打开任意入门场景，在 Stage 面板展开 `/World`，能指出至少 3 个不同类型 Prim
- [ ] 选中一个 Xform/Mesh，读出 translate/rotate/scale（或等价属性）并做一次可逆小改动
- [ ] 笔记中用自己的话区分：默认 layer 编辑 vs 引用外部资产（reference/payload）
- [ ] 确认仓库 `.gitignore` 忽略 `*.usd*`；Git 状态中无官方资产
- [ ] 能说明「组合（composition）」为何让同一机器人资产被多场景复用

## 概念讲解（自己的话）

### 为什么机器人仿真绕不开 USD

Isaac 的世界状态主要挂在一张 **Stage** 上：灯光、地面、机器人、传感器坐标系都是 Stage 里的节点。USD 不是「另一种模型格式」那么简单，它还描述**层级、引用、覆盖（opinion）与时间采样**。学会读 Stage，后面 Python / ROS2 / Lab 都是在同一套图上操作。

### Stage、Prim、Attribute

| 概念 | 直觉 |
|------|------|
| Stage | 当前打开的整张场景图 |
| Prim | 树上的一个节点，路径如 `/World/Cube` |
| Attribute | Prim 上的字段（位姿、颜色、物理标记等） |

改「场景」通常就是：找到 Prim → 改 Attribute 或关系（relationship）→（可选）保存 layer。

### Layer 与组合

多个 **Layer** 叠在一起，按强度合并出你最终看到的 Stage。常见坑是：在「错误的层」上改官方示例，导致文件变脏、难以还原。学习阶段优先：

1. 新建自己的 root layer / 匿名层做实验；
2. 对官方资产用 **reference / payload** 引用，而不是把大文件复制进 Git。

**Payload** 适合「先占位、真正需要再加载」的大资产，避免一开场景就吃满内存。

### Omniverse 在这里扮演什么

可以把 **Omniverse Kit** 想成应用壳与扩展运行时；Isaac Sim 是其上面向机器人的产品层。你在 GUI 里点的许多按钮，背后是某个 Extension 在读写 USD。因此「USD 概念」和「扩展 / Python API」是同一条能力链上的不同切口。

### 中英术语（本节）

| 中文 | English |
|------|---------|
| 舞台 | Stage |
| 图元 | Prim |
| 属性 | Attribute |
| 层 | Layer |
| 引用 / 延迟引用 | Reference / Payload |

## 推荐步骤（链官方，不抄大段）

1. 复习 [01 第一次仿真](../01_第一次仿真/index.md)，确保能 Play 简单物理场景。
2. 打开主路径文档首页，从目录进入 USD / 场景相关章节，对照 Stage 面板点选：
   https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
3. 对照轨浏览最新文档树中的场景与工作流说明：
   https://docs.isaacsim.omniverse.nvidia.com/latest/
   https://docs.isaacsim.omniverse.nvidia.com/6.0.0/introduction/workflows.html
4. 在笔记画一张简图：`Root Layer` → references → 机器人资产；标出你本机资产路径文字（不提交文件）。
5. 尝试：复制一个 Prim 路径字符串，供下一章 Python 使用。

## 5.1 vs 6.x 差异要点

- USD 核心概念稳定；变的是菜单入口、扩展 ID、以及部分辅助 API 命名。
- 6.x 迁移指南会提到命名空间与工作流整理，读 Stage 的方式不变：
  https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html
- 物理后端叙述（PhysX / Newton）增多时，先分清「USD 里有没有刚体/碰撞属性」与「哪个后端在积分」。

## 常见坑

- **把 payload 展开后的大资产存进 Git**：仓库膨胀且可能违规；只留路径文字。
- **相对路径在 GUI 与 Standalone 不一致**：笔记同时记录「启动工作目录」与「资产绝对路径」。
- **改脏官方示例层**：下次更新安装目录被覆盖或无法 diff；用自己的 layer 覆盖。
- **只改可视 mesh、不改 Xform/articulation root**：看起来动了，控制与物理却对不上。
- **混淆 Prim 路径大小写与命名空间**：脚本里路径写错会静默找不到。

## 延伸阅读链接

- 5.1.0 首页：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
- latest：https://docs.isaacsim.omniverse.nvidia.com/latest/
- Workflows：https://docs.isaacsim.omniverse.nvidia.com/6.0.0/introduction/workflows.html
- 迁移：https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html
- 术语：[术语表](../术语表.md)

上一章：[02 第一次机器人](../02_第一次机器人/index.md) · 下一章：[04 Python接口](../04_Python接口/index.md)
