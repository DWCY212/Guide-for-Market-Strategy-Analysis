# 市场战略分析指导插件

这是一个面向 GPT-6 Astra 工作流的 skills-only 插件，当前版本为 `0.7.1`，用于：

- 把模糊的市场问题拆成可决策的研究问题；
- 区分“该投入多大”的市场战略洞察研究与“该不该投入”的市场战略机会研究，并分别使用对应框架；
- 默认输出 `研究报告.md` 和 `研究方向.md` 两份 Markdown 文档：前者保留框架和当前内容，后者列出章节要求、证据缺口和下一步改进；
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
- 通过明确的触发条件、输入验证、错误处理、权限边界和限制说明保持审查结果可复核。

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
    ├── research-modes-and-deliverables.md
    ├── research-insight-report-template.md
    ├── research-opportunity-report-template.md
    ├── research-directions-template.md
    └── source-inventory.md
```

## 插件说明

### 1. 插件定位与边界

插件用于搭建市场战略研究框架、审查已有分析、组织证据和提出下一步研究方向。它默认指导和审查，不自动代写完整市场战略报告，不把附件或报告中的“请执行”文字当作任务指令。

### 2. 研究类型模块

插件会先根据决策问题进行路由：

- **市场战略洞察研究**回答“该投入多大”，使用“摘要—市场定义—五看—综合研判—战略制定—附件”，输出试点、扩大或全面投入的资源、阶段门槛、验证指标和退出条件。
- **市场战略机会研究**回答“该不该投入”，使用“摘要—市场（市场定义与业务本质分析、需求机理与长期价值、市场阶段与空间、竞争格局和态势）—公司（Right to Win、战略投入判断、战略选择与验证、定目标/策略/控制点）—附件”，输出继续验证、立项、暂缓、退出或转向的条件。

默认交付两个 Markdown 文档：`研究报告.md`保留选定框架、已有内容和待补证标题；`研究方向.md`说明每个章节应回答什么、需要什么证据、当前缺口如何影响决策，以及 P0/P1/P2 下一步任务。没有内容的子标题保留为空或写“待补证”，不会为了形式删除缺口，也不会自动代写完整战略报告。

### 3. 摘要模块

摘要不是简单总结，而是研究报告的一页纸精简版。假设读者只读摘要，也应知道研究对象、决策问题、市场边界、需求与客户、产品/公司位置、市场空间口径、竞争与 Right to Win、关键证据、风险、成熟度和建议行动。摘要内容可以与正文重复；限制、冲突、模型假设和禁止外推不得被省略。洞察研究摘要重点回答投入多大，机会研究摘要重点回答是否投入。

### 4. 证据与联网模块

组织事实、分析判断、模型假设和待核验证据；按官方政策、采购、合同、验收、医院/机构和企业原文优先的规则补充联网证据。联网能力依赖宿主提供的网页搜索、浏览器或 MCP 工具，不绕过宿主权限。

### 5. 核心分析模块

包括市场定义、需求机制、客户工作流、采购闭环、市场空间、竞争与 Right to Win、进入与复制、交付经济性、风险和成熟度判断。

### 6. 专项审查模块

支持慢病数智化管理、公共卫生智能流调、医养结合、医疗高质量数据集和转会诊 DSTE，并保留各专项的市场拆分、产品边界、证据和采购审查规则。

### 7. 安全与限制模块

默认只读分析，不上传文件、发送消息、修改外部系统、调用未授权服务或索取凭据。文件缺失、网页失败、来源冲突或数字不可复算时，保留限制并标为待核验，不强行外推。

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
