# 常见坑

从各章提炼的高频翻车点；发现新坑请用「现象 → 原因 → 处理」补一条。官方论坛与 Discord 适合搜同类报错。

## 安装与版本

| 现象 | 常见原因 | 处理方向 |
|------|----------|----------|
| 能装不能稳跑 / 黑屏 | 驱动或 GPU 档位不达标 | 先跑 Compatibility Checker；对照 requirements |
| 按博客装失败 | 仍走已弃用 Launcher | 改 quick-install / workstation / container / pip |
| import 诡异、扩展错乱 | 同一 shell 混 5.1 与 6.x | 分离安装根；清 `PYTHONPATH`；单会话单版本 |
| 每次启动都像首次那么慢 | 缓存目录只读或被清掉 | 查着色器缓存路径与磁盘权限 |
| `python` 指错 | 用了系统/conda base | 使用该版本安装树自带解释器（5.1≈3.11，6.x=3.12） |

## 资产与许可

- **官方 USD / 贴图 / 安装包进 Git**：立刻移出、补 ignore；遵守 no-assets 与 License FAQ。
- **写死他人机器路径**：笔记同时保留「如何在本机定位示例」的步骤链接。
- **对外打包含 NVIDIA 资产**：先读许可，默认不要分发。

## 场景与物理

- **有模型不掉落**：缺刚体或碰撞，或没按 Play。
- **穿地 / 爆炸**：碰撞近似、单位缩放、关节限位或初始穿透。
- **改了 mesh 但控制不动**：找错 Prim，应操作 articulation root / 关节。

## Python / 扩展

- **SimulationApp 未关闭**：GPU 占用、二次启动失败。
- **热重载幻觉**：文件已存但扩展未 reload。
- **旧扩展 ID**：启用无效果 → 查重命名与迁移指南。
- **Standalone 依赖 GUI 选中状态**：路径改参数化。

## ROS2

- **topic list 空**：Domain ID / RMW 不一致，或未 Play，或 Bridge 未启用。
- **混源 source**：多发行版叠加；为 Isaac 会话准备干净终端。
- **跟错 5.1 / latest landing 页**：发行版（Humble/Jazzy）与示例分支不匹配。

## Isaac Lab / SDG

- **Lab 与 Sim 版本不兼容**：先查官方矩阵，必要时改走对照轨 6.x。
- **合成数据写爆磁盘**：限额帧数；输出在仓库外。
- **数据集进 Git**：不要。

## 官方社区

- Forums：https://forums.developer.nvidia.com/
- Discord：https://discord.com/invite/nvidiaomniverse
- 迁移：https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html
- License FAQ：https://docs.isaacsim.omniverse.nvidia.com/latest/common/license-faq.html

相关：[速查表](../速查表/index.md) · [迁移 5到6](../迁移_5到6/index.md) · [资源链接](../资源链接.md)
