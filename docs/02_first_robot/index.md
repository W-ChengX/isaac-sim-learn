# 02 第一个机器人

## 学习目标

- 在仿真中加入一台经典机械臂（教学上常用 **Franka** / 文档中的 Basic Robot 路径）。
- 会在 Stage / 属性面板中**检查关节（joints）与 Articulation**，分清「连杆几何」和「可驱动自由度」。
- 从概念上理解向关节发送 **位置（position）** 或 **速度（velocity）** 命令——本章强调「命令语义与观察」，不要求背完整 API。
- 知道下一步应进入官方 **Robot Setup** 系列（装配、驱动、控制器等），而不是停在「拖进场景」。

## 你将完成什么（验收清单）

- [ ] 从**本机官方资产路径**加载 Franka（或文档指定的入门机器人），**不**复制进本仓库
- [ ] 在 Stage 中展开机器人层级，能指出 articulation root 与若干关节
- [ ] Play 后机器人稳定站在地面上（无持续爆炸、穿地抖动）
- [ ] 通过 GUI 控件、示例面板或官方 demo，对至少一个关节施加位置或速度类目标，并看到响应
- [ ] 笔记标明：`ISAAC_SIM_VERSION`、资产路径文字、用的是位置还是速度命令
- [ ] 已打开 Robot Setup 教程目录，标出「下一篇要读哪一节」

## 概念讲解（自己的话）

### 机器人资产 vs 控制脚本

- **资产**：USD 里的几何、关节、物理与材质；换机器复现时靠「同一版本 + 同一资产路径」。
- **控制**：在仿真跑起来之后，把目标位置/速度/力矩送给 articulation。  
本章先保证资产加载正确，再谈「发一条命令并看见关节动」。

### Articulation 是什么

可以把机械臂看成一棵**有约束的刚体树**：根固定或挂在基座上，子连杆通过关节连接。控制接口通常面向这棵树（articulation），而不是单独推某个可视 mesh。检查关节时，关注：

- 关节类型（转轴 / 滑动等）
- 限位（上下限）
- 当前驱动模式（位置、速度、力矩等，以你版本面板为准）

### 位置命令 vs 速度命令（概念）

| 命令类型 | 直观含义 | 观察要点 |
|----------|----------|----------|
| 位置（position） | 「关节角/位移到某目标」 | 是否收敛到目标、有无超调或抖振 |
| 速度（velocity） | 「按某角速度/线速度运动」 | 方向是否正确、停止命令后是否刹住 |

具体单位、符号与 API 名称以官方文档和你启用的扩展为准；先建立「发目标 → 仿真步进 → 读回状态」的闭环直觉。

### 为什么要指向 Robot Setup 系列

「拖进一个 Franka」只是起点。真实项目还要：坐标系与单位、驱动器参数、末端工具、控制器、与感知/ROS2 对接等。官方 **Robot Setup tutorials** 按主题拆好了，本章结束就应把书签打在那里：  
https://docs.isaacsim.omniverse.nvidia.com/6.0.1/robot_setup_tutorials/index.html

### 中英术语（本节）

| 中文 | English |
|------|---------|
| 关节机构 | Articulation |
| 关节 | Joint |
| 位置命令 | Position command |
| 速度命令 | Velocity command |
| 基座 / 根 | Base / Articulation root |

## 推荐步骤（可操作，细节点官方）

1. 完成 [01 第一个仿真](../01_first_sim/index.md)，确认 Play / 刚体碰撞直觉已建立。
2. 按主路径 Quickstart 中与机器人相关的部分，或对照 latest 的机器人 Quickstart，加载入门机械臂（Franka / Basic Robot）。  
   - 5.1.0：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/introduction/quickstart_isaacsim.html  
   - latest 机器人：https://docs.isaacsim.omniverse.nvidia.com/latest/introduction/quickstart_isaacsim_robot.html
3. 在 Stage 树中展开机器人，记录：根路径、关节命名、是否看到 articulation 相关属性。
4. Play，确认稳定；再通过文档推荐的 GUI / 示例方式发送**位置**或**速度**目标，观察关节运动。
5. 打开 Robot Setup 索引，选一节（例如导入与验证、或驱动相关）作为下一学习任务：  
   https://docs.isaacsim.omniverse.nvidia.com/6.0.1/robot_setup_tutorials/index.html
6. 复习三种工作流，思考同一发令在 GUI 与 Standalone 中的对应关系：  
   https://docs.isaacsim.omniverse.nvidia.com/6.0.0/introduction/workflows.html

## 5.1 vs 6.x 差异要点

- 机器人入门页在 latest 上更独立（`quickstart_isaacsim_robot`）；5.1.0 仍可能把部分内容收在总 Quickstart——**跟你的版本文档走**。
- Robot Setup 系列在 6.0.1 文档树很完整，对照轨强烈建议精读；主路径 5.1 用户同样可阅读概念，但操作截图以 5.1 界面为准。
- 扩展名、Python 命名空间在 6.x 迁移指南中有集中说明：  
  https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html

## 常见坑

- **资产路径写死且提交仓库**：换机器即失败，且可能违规分发；只记本机路径文字。
- **单位或轴向搞反**：机器人埋地、侧躺、关节「倒着转」——先查 stage 单位与基座 Xform。
- **未 Play 就判定驱动失败**：命令在仿真步进后才显现。
- **混用 5.1 与 6.x 扩展/脚本**：import 成功但运行期行为诡异。
- **只看 mesh 不看 articulation**：改错 Prim，怎么发令都不动。
- **一步想做完装配+控制器+ROS2**：拆开，按 Robot Setup 系列推进。

## 延伸阅读 / 官方对照

**5.1.0**

- 首页：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
- Quickstart：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/introduction/quickstart_isaacsim.html

**latest / 6.0.x**

- latest 首页：https://docs.isaacsim.omniverse.nvidia.com/latest/
- 机器人 Quickstart：https://docs.isaacsim.omniverse.nvidia.com/latest/introduction/quickstart_isaacsim_robot.html
- Robot Setup：https://docs.isaacsim.omniverse.nvidia.com/6.0.1/robot_setup_tutorials/index.html
- Workflows：https://docs.isaacsim.omniverse.nvidia.com/6.0.0/introduction/workflows.html
- 迁移：https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html
- License FAQ：https://docs.isaacsim.omniverse.nvidia.com/latest/common/license-faq.html

上一章：[01 第一个仿真](../01_first_sim/index.md) · 术语：[术语表](../glossary.md)
