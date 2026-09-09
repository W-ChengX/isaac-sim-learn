# Isaac Sim Learn

自学向、可验收的 Isaac Sim 学习笔记仓库（中文）。

## 目标

- 用最短路径跑通仿真、机器人、Python API、ROS2 / Isaac Lab 等核心能力。
- **主路径钉死 Isaac Sim 5.1.0**；需要时对照 **6.0.1 / latest**（见 [VERSIONS.md](VERSIONS.md)）。
- 文档即代码（MkDocs），不内嵌 NVIDIA 官方资产（USD / 贴图 / 模型）。

## 双轨版本策略

| 轨道 | 版本 | 用途 |
|------|------|------|
| 主路径 | **5.1.0** | 默认安装、教程步骤、验收 |
| 对照 | **6.0.1 / latest** | 迁移差异、新 API、官方最新页 |

禁止混版本（同一环境混装 / 混用扩展与 Python 包）。详见 [VERSIONS.md](VERSIONS.md)。

## 最短验收

1. 按官方要求装好 **5.1.0**，能启动 GUI。
2. 完成「第一个仿真」与「第一个机器人」两章本地清单。
3. 能独立运行一段 standalone Python（不依赖本仓库内任何官方 USD）。

## 如何开始

1. 阅读 [VERSIONS.md](VERSIONS.md) 与 [LICENSE-NOTES.md](LICENSE-NOTES.md)。
2. 打开 [docs/index.md](docs/index.md) 按学习路径推进。
3. 本地预览文档（可选）：

```bash
pip install mkdocs-material
mkdocs serve
```

4. `examples/` 仅占位说明：有本机 Isaac Sim 再跑自己的脚本；**不放官方 USD**。

## Docs-as-code

- 源码：`docs/` + `mkdocs.yml`
- 主题：Material
- 站点名：Isaac Sim Learn
- 贡献：改 Markdown → PR →（可选）GitHub Pages

## 许可与资产

本仓库**不**二次分发 NVIDIA 官方 USD / 贴图 / 模型。使用官方资源请遵守 NVIDIA 许可，见 [LICENSE-NOTES.md](LICENSE-NOTES.md)。
