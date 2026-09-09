# 08 SDG 与传感器

## 学习目标

- 理解 **SDG（合成数据生成）**：在仿真里系统性改变光照、材质、姿态、背景等，批量导出图像/标注，服务感知与学习。
- 认识常用传感器在 Isaac 中的角色：RGB/Depth 相机、LiDAR 等——先打通「挂上传感器 → Play → 看到输出」。
- 能在本机跑一次**小规模** SDG 或传感器示例，并把输出目录放在仓库外。
- 建立磁盘与频率纪律：合成数据极易写爆硬盘；传感器频率需与仿真步进对齐思考。

## 你将完成什么（验收清单）

- [ ] 启用文档要求的传感器 / SDG 相关扩展
- [ ] 在视口或输出流中看到至少一种传感器数据（图像 / 点云 / 话题）
- [ ] 跑通一次小规模导出（几十帧量级即可），记录分辨率、随机化开关、输出路径
- [ ] 确认输出目录被 ignore 或不在本仓库内
- [ ] 笔记写明：主路径 5.1.0 下使用的示例名与本机路径文字

## 概念讲解（自己的话）

### 传感器不是「贴一张图」

相机、LiDAR 在仿真里通常对应一组 Prim + 渲染/扫描管线 +（可选）ROS/文件后端。验收时问三件事：

1. 传感器坐标系挂在哪个 Prim 下？
2. 数据在 Play 之后是否更新？
3. 输出到视口、磁盘还是 ROS 话题？

### SDG 在练什么

合成数据的价值在于**可控的分布**：你能系统改变域随机化参数，生成带自动标注的样本。学习阶段不要追求「一夜百万张」，先跑通管道：场景 → 随机化 → 渲染 → 写盘 → 抽查标注。

### 与 Python / 扩展的关系

批量 SDG 往往走 Standalone 或扩展工作流（见 [04](../04_Python接口/index.md)、[05](../05_扩展开发/index.md)）。GUI 适合调参目视；量产留给脚本。

### 中英术语（本节）

| 中文 | English |
|------|---------|
| 合成数据生成 | SDG |
| 域随机化 | Domain randomization |
| 深度相机 | Depth camera |
| 激光雷达 | LiDAR |

## 推荐步骤（链官方）

1. 从 5.1.0 文档目录进入 Sensors / Replicator / SDG 相关章节（名称以文档树为准）：
   https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
2. 对照 latest 查阅同名章节与更新说明：
   https://docs.isaacsim.omniverse.nvidia.com/latest/
3. 先挂一个相机传感器，Play 后确认图像更新；再考虑 LiDAR / 标注导出。
4. 小规模 SDG：限制帧数与分辨率；输出写到 `/tmp` 或仓库外数据盘。
5. 若数据要进训练，跳转 [07 Isaac Lab](../07_Isaac_Lab/index.md) 前先保证导出格式与路径约定清晰。
6. 涉及跨版本 API 时参考迁移：
   https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html

## 5.1 vs 6.x 差异要点

- 传感器扩展名、Replicator / SDG 面板入口可能调整；以你安装版本的文档树为准。
- 6.x 对工作流与命名空间的整理会影响脚本化 SDG；对照 standalone / 迁移页再改 import。
- 渲染与去噪默认参数可能变化，导致「同样曝光看起来更亮/更暗」——先排除版本差异再调参。

## 常见坑

- **磁盘被合成图塞满**：先限额帧数；监控输出目录。
- **传感器频率与仿真 dt 概念混淆**：日志里的 Hz 不一定等于你以为的实时时钟。
- **误提交 `.png` / `.npy` / 视频**：加入 ignore，必要时 `git rm --cached`。
- **只开可视化不开写后端**：以为 SDG「没跑」，其实只是没配置 sink。
- **无头模式忘挂显示相关扩展**：管道失败时对照官方 headless 说明。

## 延伸阅读链接

- 5.1.0：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
- latest：https://docs.isaacsim.omniverse.nvidia.com/latest/
- Workflows：https://docs.isaacsim.omniverse.nvidia.com/6.0.0/introduction/workflows.html
- 迁移：https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html
- License FAQ：https://docs.isaacsim.omniverse.nvidia.com/latest/common/license-faq.html

上一章：[07 Isaac Lab](../07_Isaac_Lab/index.md) · 对照：[迁移 5到6](../迁移_5到6/index.md)
