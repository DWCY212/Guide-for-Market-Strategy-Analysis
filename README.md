# 市场战略分析指导插件

这是一个面向 GPT-6 Astra 工作流的 skills-only 插件，当前版本为 `0.6.0`，用于：

- 把模糊的市场问题拆成可决策的研究问题；
- 选择最小充分的市场战略分析框架；
- 组织事实、分析判断、模型假设和待核验证据；
- 审查现有市场分析在需求、客户、采购、市场空间、竞争、产品边界、进入路径和风险上的不足。
- 对数字口径冲突、TAM/SAM/SOM 与公司目标混用、案例归因、DSTE 闭环和战略成熟度进行专项审查。
- 对县域医共体慢病管理与城市二三级医院慢病管理进行双市场拆分审查，并检查模块级产品责任矩阵。
- 对公共卫生智能流调的采购证据、调查闭环、疾控平台协同、部署经济性和跨区域复制进行专项审查。
- 对医养结合区分服务支付市场与医侧系统采购市场，拆分 G 端监管、B 端长护险定点机构和基层家庭病床三条采购路径，并检查医侧产品边界、采购验收、价格拆分、交付经济性和复制条件。
- 对医疗高质量数据集区分数据集核心交付、平台治理、模型/应用、课题和邻近专病库，检查任务级数据生产闭环、质量验收、数据合规、项目金额去重、交付经济性和复购复制证据。
- 用“项目成立性七问”审查项目身份、问题、客户付费、产品成熟度、商业验证、时机、差异化壁垒、市场空间和团队执行能力。
- 在宿主提供网页搜索、浏览器或联网工具时，按官方/采购原文优先、证据等级和可追溯引用规则补充最新政策、采购、机构和竞品信息。

插件的默认目标是“指导和审查”，不是重新生成一份完整的市场战略分析报告。用户提供的慢病数智化管理、医养结合、医疗高质量数据集、公共卫生智能流调和转会诊 DSTE 报告仅用于提炼框架与审查维度。

## 目录

```text
plugins/market-strategy-guidance/
├── .codex-plugin/plugin.json       # Codex 兼容清单
├── plugin.json                     # Agent Plugins 可移植清单
├── skills/market-strategy-guidance/SKILL.md
└── assets/
    ├── chronic-disease-review-checklist.md
    ├── eldercare-integration-review-checklist.md
    ├── medical-dataset-review-checklist.md
    ├── project-viability-gate.md
    ├── public-health-review-checklist.md
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

## 更新已安装插件

从已配置的 GitHub marketplace 更新插件：

```text
codex plugin marketplace upgrade guide-for-market-strategy-analysis
codex plugin add market-strategy-guidance@guide-for-market-strategy-analysis
```

更新后请重启 Codex 或新建会话，让新版本技能加载。若 marketplace 尚未登记，先执行上面的“从 GitHub 安装”步骤。桌面端也可以在 Plugins 页面选择该插件并执行更新/重新安装。

## 联网检索说明

本插件的技能可以指导 Codex 在宿主提供网页搜索、浏览器或 MCP 外部数据工具时进行联网补证；插件清单本身不会绕过宿主权限，也不会自动获得网络、登录或外部服务访问权。联网研究优先使用政府、采购平台、医院/疾控机构和企业官方原文，并在输出中记录 URL、日期、地域、证据等级和未核验项。若当前会话没有联网工具，插件会明确说明限制并继续完成基于现有材料的审查。

## 参考资料边界

原始 DOCX 不复制进插件，也不会被插件自动改写。插件在实际使用时应重新核验引用的数字、政策、采购和竞品证据；搜索结果页或未打开的链接不能作为关键结论的最终证据。

## 许可证

MIT，见 [LICENSE](LICENSE)。
