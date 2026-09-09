# 05 扩展开发

## 学习目标

- 理解 Extension 是 Kit 的可插拔模块：目录结构、`extension.toml`、依赖与启用开关。
- 能在 Extension Manager 中启用/禁用官方扩展，并观察 GUI 能力随之出现或消失。
- 会用官方 **CLI / VS Code 模板生成器**拉出最小扩展骨架（代码可后续迭代）。
- 知道扩展 ID 历史上有过重命名；读旧博客时先核对当前文档。

## 你将完成什么（验收清单）

- [ ] 在 Extension Manager 搜索并启用一个官方扩展，确认对应面板/菜单出现
- [ ] 禁用后功能消失（或给出符合预期的缺失提示）
- [ ] 笔记记录：扩展 ID、在安装目录中的路径文字
- [ ] 用官方模板生成器创建**空壳扩展**（放在仓库外或仅提交你自己的源码，不含官方二进制）
- [ ] 热重载一次：改打印语句 → 重载 → 日志可见（按你版本支持的方式）

## 概念讲解（自己的话）

### 扩展解决什么问题

Isaac 功能极其庞杂。把「ROS2 桥」「某传感器面板」「某示教工具」拆成扩展，可以：

- 按需启用，加快启动；
- 版本化依赖；
- 让你的工具以同样机制分发。

### 最小心智模型

```
my_extension/
  config/extension.toml   # 名称、版本、依赖、启动模块
  .../python 模块          # on_startup / on_shutdown 钩子
  （可选）文档与测试
```

应用启动时按启用列表加载；你的 UI 与命令在钩子里注册。细节以模板生成结果与官方 utilities 页为准。

### 模板入口（优先官方生成器）

不要从随机博客抄目录树。从这两页入手：

- CLI 模板：https://docs.isaacsim.omniverse.nvidia.com/latest/utilities/cli_extension_templates.html
- VS Code 生成器：https://docs.isaacsim.omniverse.nvidia.com/latest/utilities/vscode_extension_template_generator.html

### 扩展重命名的历史教训

较老文档曾集中说明扩展 ID 重命名（示例见 4.5 概述页）：
https://docs.isaacsim.omniverse.nvidia.com/4.5.0/overview/extensions_renaming.html
若启用失败且日志说找不到扩展，先查「旧 ID → 新 ID」，再怀疑自己代码。

### 中英术语（本节）

| 中文 | English |
|------|---------|
| 扩展 | Extension |
| 扩展管理器 | Extension Manager |
| 清单文件 | extension.toml |
| 热重载 | Hot reload |

## 推荐步骤（链官方）

1. 完成 [04 Python接口](../04_Python接口/index.md)，确认解释器与日志查看方式。
2. 打开 5.1.0 文档目录，浏览 Extensions 相关章节：
   https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
3. 对照 latest，用 CLI 或 VS Code 生成器创建骨架：
   https://docs.isaacsim.omniverse.nvidia.com/latest/utilities/cli_extension_templates.html
   https://docs.isaacsim.omniverse.nvidia.com/latest/utilities/vscode_extension_template_generator.html
4. 把扩展路径加入应用搜索路径（按生成器 README），启用并验证钩子日志。
5. 若遇到找不到扩展 ID，查阅重命名背景与 6.0 迁移：
   https://docs.isaacsim.omniverse.nvidia.com/4.5.0/overview/extensions_renaming.html
   https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html

## 5.1 vs 6.x 差异要点

- 模板与 utilities 页在 latest 更完整；5.1 用户可对照操作，但扩展搜索路径、菜单可能略有不同。
- 6.x 迁移常涉及扩展 ID / 依赖声明调整；启用列表不要假设跨大版本可原样复制。
- Python 小版本随主程序走（3.11 vs 3.12），扩展内依赖轮子需匹配。

## 常见坑

- **依赖版本与主程序不匹配**：扩展能看见但一用就炸。
- **以为保存即生效**：部分改动需要 reload 扩展或重启应用。
- **把扩展输出目录 / 缓存提交进 Git**：保持源码干净。
- **抄旧扩展 ID**：日志「not found」优先查重命名表。
- **在扩展里打包官方 USD**：同样违反 no-assets。

## 延伸阅读链接

- 5.1.0：https://docs.isaacsim.omniverse.nvidia.com/5.1.0/index.html
- latest：https://docs.isaacsim.omniverse.nvidia.com/latest/
- CLI 模板：https://docs.isaacsim.omniverse.nvidia.com/latest/utilities/cli_extension_templates.html
- VS Code 模板：https://docs.isaacsim.omniverse.nvidia.com/latest/utilities/vscode_extension_template_generator.html
- 扩展重命名：https://docs.isaacsim.omniverse.nvidia.com/4.5.0/overview/extensions_renaming.html
- 迁移：https://docs.isaacsim.omniverse.nvidia.com/latest/migration_guides/isaac_sim_6_0/index.html

上一章：[04 Python接口](../04_Python接口/index.md) · 下一章：[06 ROS2集成](../06_ROS2集成/index.md)
