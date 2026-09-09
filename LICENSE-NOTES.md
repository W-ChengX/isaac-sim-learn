# 许可说明（资产与二次分发）

## 本仓库明确禁止

- **禁止**将 NVIDIA 官方 USD / 贴图 / 模型 / 示例场景二进制放入本仓库（含 Git LFS）。
- **禁止**二次分发上述官方资产（公开或私有镜像给第三方均不建议，除非你已获 NVIDIA 书面授权）。
- 允许：你自己创作的脚本、笔记、截图说明、指向官方文档的链接。

## 官方许可 FAQ（请先读）

- License FAQ：https://docs.isaacsim.omniverse.nvidia.com/latest/common/license-faq.html
- Isaac Sim Additional License：https://docs.isaacsim.omniverse.nvidia.com/latest/common/license-isaac-sim-additional.html

## 实践建议

1. 官方资源从本机 Isaac Sim 安装目录或 Nucleus / 官方渠道加载，**不要**提交到 Git。
2. `.gitignore` 已忽略 `*.usd` / `*.usda` / `*.usdc` / `*.usdz` 等。
3. 对外分享教程时，只给「打开哪个官方示例路径」的文字说明，不附资产文件。
