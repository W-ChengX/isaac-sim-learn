# Isaac Sim Learn

自学向、可验收的 **Isaac Sim** 中文学习笔记（docs-as-code）。本仓库写「概念 / 步骤骨架 / 验收标准 / 常见坑」，并始终给出官方文档对照链接；**不**二次分发 NVIDIA 官方 USD、贴图、模型或安装包。

## 定位

- 面向从零到能独立跑仿真、机器人、Python、ROS2 / Isaac Lab 的学习者。
- **主路径钉死 5.1.0**；需要时打开 **6.0.1 / latest** 对照页（见 [VERSIONS.md](VERSIONS.md)）。
- 每章结构统一：学习目标 → 验收清单 → 概念讲解 → 推荐步骤（指向官方 URL）→ 5.1 vs 6.x → 常见坑 → 延伸阅读。
- 可选短「中英术语对照」；完整术语见 [docs/术语表.md](docs/术语表.md)。

## 双轨版本策略

| 轨道 | 版本 | 用途 |
|------|------|------|
| 主路径 | **5.1.0** | 默认安装、教程步骤、本地验收 |
| 对照 | **6.0.1 / latest** | 迁移差异、新 API、官方最新页 |

同一会话 / 同一 shell 环境**禁止**混装 5.1 与 6.x（路径、扩展、Python 包互相覆盖是高频翻车点）。

## 如何导航文档

1. 先读本 README、[VERSIONS.md](VERSIONS.md)、[LICENSE-NOTES.md](LICENSE-NOTES.md)。
2. 从 [docs/index.md](docs/index.md) 按学习路径推进（00 → 01 → 02 …）。
3. 遇到生词查 [术语表](docs/术语表.md)；需要官方入口查 [资源链接](docs/资源链接.md)。
4. 每章底部的「官方对照」同时给出 **5.1.0** 与 **latest/6.0.1** 绝对 URL，按你当前安装版本点开即可。

## 本地预览（MkDocs）

```bash
pip install mkdocs-material
mkdocs serve
```

浏览器打开终端提示的本地地址（通常是 `http://127.0.0.1:8000`）。改 `docs/` 下 Markdown 后保存即可热刷新。

## 最短验收

1. 按官方要求装好 **5.1.0**，能启动 GUI。
2. 完成「第一次仿真」与「第一次机器人」两章本地清单。
3. 能独立运行一段 standalone Python（不依赖本仓库内任何官方 USD——本仓库本来就不带）。

## No-assets 政策

- **禁止**把 NVIDIA 官方 Assets Pack / Nucleus 上的 `.usd`、贴图、机器人模型、安装器提交进本仓库。
- 学习时从**本机安装目录**或官方文档指示的路径加载示例；笔记里只写路径文字与验收结果。
- 许可说明见 [LICENSE-NOTES.md](LICENSE-NOTES.md) 与官方 License FAQ（latest 文档 common/license-faq）。

## Docs-as-code

- 源码：`docs/` + `mkdocs.yml`
- 主题：Material（`language: zh`）
- 目录名已中文化（保留数字前缀），见 `docs/00_前置与安装` 等。
- 贡献：改 Markdown → PR →（可选）GitHub Pages

## 官方入口（常备）

- 5.1.0：`https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html`
- latest：`https://docs.isaacsim.omniverse.nvidia.com/latest/`
