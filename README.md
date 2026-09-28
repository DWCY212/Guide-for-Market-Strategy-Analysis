# 市场战略分析指导插件

这是一个面向 GPT-6 Astra 工作流的 skills-only 插件，用于：

- 把模糊的市场问题拆成可决策的研究问题；
- 选择最小充分的市场战略分析框架；
- 组织事实、分析判断、模型假设和待核验证据；
- 审查现有市场分析在需求、客户、采购、市场空间、竞争、产品边界、进入路径和风险上的不足。

插件的默认目标是“指导和审查”，不是重新生成一份完整的市场战略分析报告。用户提供的慢病数智化管理、医养结合、医疗高质量数据集、公共卫生智能流调和转会诊 DSTE 报告仅用于提炼框架与审查维度。

## 目录

```text
plugins/market-strategy-guidance/
├── .codex-plugin/plugin.json       # Codex 兼容清单
├── plugin.json                     # Agent Plugins 可移植清单
├── skills/market-strategy-guidance/SKILL.md
└── assets/
    ├── reference-framework.md
    └── source-inventory.md
```

## 本地测试

从仓库根目录运行：

```text
python C:/Users/<user>/.codex/skills/.system/plugin-creator/scripts/validate_plugin.py plugins/market-strategy-guidance
```

本仓库的 GitHub Actions 会在推送和 Pull Request 时自动执行同一校验。

## 从 GitHub 安装

第一步，添加 GitHub marketplace：

```text
codex plugin marketplace add https://github.com/DWCY212/Guide-for-Market-Strategy-Analysis.git --sparse .agents/plugins
```

第二步，安装插件：

```text
codex plugin add market-strategy-guidance@guide-for-market-strategy-analysis
```

`marketplace add` 只登记插件来源，不会自动安装其中的插件。安装完成后，重启 Codex 或新建会话，使技能加载生效。也可以在 Codex 桌面端的 Plugins 页面找到“市场战略分析指导”并点击安装。

检查安装状态：

```text
codex plugin list
```

## 参考资料边界

原始 DOCX 不复制进插件，也不会被插件自动改写。插件在实际使用时应重新核验引用的数字、政策、采购和竞品证据；搜索结果页或未打开的链接不能作为关键结论的最终证据。

## 许可证

MIT，见 [LICENSE](LICENSE)。
