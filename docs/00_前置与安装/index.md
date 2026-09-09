# 00 前置与安装

## 学习目标

- 能对照官方需求页勾选 GPU、驱动、内存、磁盘与 OS。
- 会用 **Compatibility Checker**（或文档等价检查手段）判断本机是否适合跑 Isaac Sim。
- 分清安装通道：**zip / 工作站包**、**pip(Python)**、**Docker**；知道 **Omniverse Launcher 自 2025-10-01 起已弃用**。
- 主路径钉死 **5.1.0**，对照轨单独记 **6.0.1 / latest**；同一环境不混版本。
- 理解首次启动「着色器缓存」很慢是正常现象；记下本版本对应的 Python 小版本。

## 你将完成什么（验收清单）

- [ ] 打开 5.1.0 requirements，勾选：GPU 型号档位、驱动下限、RAM、磁盘剩余空间、OS
- [ ] 跑过 Compatibility Checker（或按官方 quick-install 完成等价自检），结果写入笔记
- [ ] 选定一种主路径安装通道并装好 **5.1.0**；能启动 GUI
- [ ] 笔记中写明：`ISAAC_SIM_VERSION=5.1.0`、安装根目录、启动命令
- [ ] 确认绑定 Python：**5.x ≈ 3.11**；若另装对照轨 6.x，则 **6.x = 3.12**，且环境变量互不覆盖
- [ ] 首次启动等到着色器编译完成；第二次启动明显变快
- [ ] 已读仓库根目录 [VERSIONS.md](../../VERSIONS.md) 与 [LICENSE-NOTES.md](../../LICENSE-NOTES.md)

## 概念讲解（自己的话）

### 为什么先做前置，而不是直接下教程场景

Isaac Sim 对 GPU 与驱动敏感。硬件/驱动不达标时，常见表现是黑屏、闪退、扩展加载失败，看起来像「教程做错了」。先把兼容性钉死，后面调试成本低一个数量级。

### Compatibility Checker

把它当成「装前体检」：对照当前文档列出的 GPU、驱动、系统组件，输出是否建议安装。体检不过就先升级驱动或换机器，而不是硬装。

### 三种常见安装通道（怎么选）

| 通道 | 适合谁 | 直观利弊 |
|------|--------|----------|
| Zip / 工作站安装 | 本机日常 GUI 开发 | 路径清晰、跟官方 workstation 文档一致；体积大，注意磁盘 |
| pip / Python 安装 | 想把仿真嵌进现有 Python 工作流 | 版本必须与文档 Python 小版本对齐；别和系统 Python 搅在一起 |
| Docker / 容器 | 服务器、复现实验、CI | 环境可重复；显示/GPU 透传要额外配置 |

没有「唯一正确」通道：主路径选一种装透，对照轨若需要再**另目录 / 另容器**安装，不要覆盖主路径。

### Launcher 已弃用

若你看到的中文博客仍写「先装 Omniverse Launcher 再装 Isaac」——那是旧流程。官方自 **2025-10-01** 起弃用 Launcher；请改走当前 **quick-install / download / workstation / container / python** 文档。

### 双轨版本钉死

- **主路径 5.1.0**：本仓库所有验收默认按它写。
- **对照 6.0.1 / latest**：只在你主动切换时使用；读迁移指南，记录 API / 物理后端 / Python 差异。
- 实践建议：不同版本用不同安装根目录；shell 里用显式路径启动，少用「全局污染式」的 `PATH` 永久覆盖。

### 首次启动与着色器缓存

第一次打开 GUI，系统会编译大量着色器，风扇狂转、界面卡住几分钟都可能正常。不要中途强杀。完成后缓存留在本机，后续启动会快很多。若每次都像「第一次」，再查磁盘权限、只读挂载或清缓存策略是否异常。

### Python 版本笔记

| Isaac Sim | 大致 Python | 备注 |
|-----------|-------------|------|
| 5.x（主路径 5.1.0） | **≈ 3.11** | 用安装自带解释器或文档指定环境 |
| 6.x（对照） | **3.12** | 不要把 5.1 的 site-packages 指到 6.x |

Standalone 脚本请用「该版本自带的 python」，而不是随手 `python3`。

## 推荐步骤（可操作，细节点官方）

1. 打开需求页，按表格自检硬件与驱动。
   - 5.1.0：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/requirements.html
   - 对照 6.0.0：https://docs.isaacsim.omniverse.nvidia.com/6.0.0/installation/requirements.html
2. 阅读快速安装总览（含 Launcher 弃用后的通道说明）：
   https://docs.isaacsim.omniverse.nvidia.com/latest/installation/quick-install.html
3. 主路径下载与安装 **5.1.0**：
   - 下载：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/download.html
   - 工作站：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/install_workstation.html
4. 若走容器或 pip，对照最新通道文档（**另环境**，勿覆盖 5.1）：
   - 容器：https://docs.isaacsim.omniverse.nvidia.com/latest/installation/install_container.html
   - Python/pip（6.0.1 对照）：https://docs.isaacsim.omniverse.nvidia.com/6.0.1/installation/install_python.html
   - 6.0.1 下载：https://docs.isaacsim.omniverse.nvidia.com/6.0.1/installation/download.html
5. 启动 GUI，完成首次着色器编译；在笔记写下版本与路径。
6. 确认 Python 小版本与启动器来自同一安装树。

## 5.1 vs 6.x 差异要点

- 安装入口与包布局随大版本调整；不要把 5.1 教程里的路径原样套到 6.x。
- Python：**5.x ≈ 3.11**，**6.x = 3.12**。
- 6.x 有独立迁移指南，对照轨必读：
  https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html
- 物理后端与扩展命名在 6.x 文档中变化更多（例如 Newton 相关叙述）；主路径验收仍以 5.1.0 为准。

## 常见坑

- **驱动过旧**：能装不能稳跑，或黑屏；先满足 requirements 再排教程问题。
- **仍按 Launcher 旧博文安装**：流程失败或装到过期组件；改看 quick-install。
- **5.1 与 6.x 环境变量互相覆盖**：同一终端里 `python` / 扩展路径指向错误版本。
- **磁盘不够**：安装体积 + 着色器缓存 + 本地资产，预留远大于「安装包标称大小」。
- **用系统 Python 硬装依赖**：版本错位后 import 成功但运行期崩溃，极难查。
- **把官方 Assets / 安装器提交进 Git**：违反本仓库 no-assets 政策与 NVIDIA 许可约束。

## 延伸阅读 / 官方对照

**5.1.0**

- 首页：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
- 需求：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/requirements.html
- 下载：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/download.html
- 工作站安装：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/installation/install_workstation.html

**latest / 6.0.x**

- latest 首页：https://docs.isaacsim.omniverse.nvidia.com/latest/
- Quick Install：https://docs.isaacsim.omniverse.nvidia.com/latest/installation/quick-install.html
- 需求 6.0.0：https://docs.isaacsim.omniverse.nvidia.com/6.0.0/installation/requirements.html
- 下载 6.0.1：https://docs.isaacsim.omniverse.nvidia.com/6.0.1/installation/download.html
- 容器：https://docs.isaacsim.omniverse.nvidia.com/latest/installation/install_container.html
- Python 安装 6.0.1：https://docs.isaacsim.omniverse.nvidia.com/6.0.1/installation/install_python.html
- 迁移：https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html
- License FAQ：https://docs.isaacsim.omniverse.nvidia.com/latest/common/license-faq.html
