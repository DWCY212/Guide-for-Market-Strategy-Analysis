# OpenAI 与 GPT 6 Astra 兼容说明

本插件采用 skills-only 结构，不包含远程 MCP 服务，也不要求 API 密钥。它使用根目录 `plugin.json` 作为可移植清单，并保留 `.codex-plugin/plugin.json` 作为 Codex 兼容清单；技能固定放在 `skills/`。

GPT 6 Astra 官方模型页说明该模型支持 Responses API、文件搜索、网页搜索、skills、MCP、结构化输出和函数调用。本插件的工作流主要依赖技能指令和用户提供的研究材料，因此无需新增外部服务或写入权限。运行时仍应遵循宿主的沙箱、审批和数据访问策略。

官方参考：

- https://developers.openai.com/api/docs/models/gpt-6-astra
- https://developers.openai.com/plugins/build/plugins
- https://developers.openai.com/plugins/deploy/submission
