# Deep Research

面向 OpenClaw 的多来源深度研究 Skill。

这个 Skill 把模糊的研究需求收敛成有证据、有结论、有风险提示的交付物，适用于行业研究、竞品分析、趋势扫描、决策支持和深度报告。

## Hermes 适配

适用于 Hermes，前提是 Hermes 会话启用了网页搜索或网页提取能力。

- 适配方式：把仓库作为外部 Skill 目录加载，然后把工作流里的工具名映射到 Hermes 自带能力
- 推荐映射：`memory-search` -> 本地记忆或笔记检索，`multi-search-engine` -> `web_search`，`web-access` -> `web_extract` 或浏览器工具
- 能力边界：这是研究方法论和流程 Skill，不绑定 OpenClaw 私有 API，但部分工具名需要在 Hermes 中做语义映射

## 适用场景

- 用户要的不只是“搜一下”，而是要有来源支撑的研究结论
- 需要比较多个方案并给出建议
- 需要把事实、推断、未知项分开表达
- 需要形成 briefing、standard report 或 deep report

## 三个控制旋钮

1. 时间预算：`S` / `M` / `L` / `XL`
2. 深度层级：`T1` / `T2` / `T3`
3. 交付形态：`briefing` / `standard-report` / `deep-report`

## 默认工作流

1. 先做内部记忆检索，避免重复研究
2. 明确研究目标、时间范围、地域范围和输出形态
3. 混合一手来源、社区来源、对比来源
4. 关键结论逐条标记为事实、推断或待确认
5. 最终必须给出影响、风险和下一步动作

## 仓库内容

- `SKILL.md`：主研究流程
- `agents/openai.yaml`：供 Agent 直接调用的结构化入口
- `references/report-levels.md`：研究层级和交付模式
- `references/source-routing.md`：不同来源的选取策略
- `references/failure-handling.md`：中断、登录墙、信息缺口处理

## 输出质量标准

- 结论可以追溯到来源
- 明确区分事实与推断
- 至少给出一个关键权衡点
- 至少指出一个盲区或信息缺口
- 给出明确的下一步建议

## License

MIT
