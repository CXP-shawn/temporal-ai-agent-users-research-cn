# 01 已确认使用 Temporal 的 AI / agent 团队

本文件列出**有公开证据**使用 Temporal 承载 AI/agent 工作流的团队。每条带证据等级与来源 URL。

## 一级证据(Temporal 官网 In Use 页直接公开)

Temporal 官网 `/in-use` 目录按客户收录案例页。| 团队 | 场景 | 案例页 |
| --- | --- | --- |
| Emergent | 官方标题称其在 Temporal Cloud 上每月跑 10 亿+ agent Actions | https://temporal.io/in-use/emergent |
| Gradient Labs | Gradient Labs uses AI agents to resolve complex customer issues | https://temporal.io/in-use/gradient-labs-uses-ai-agents-to-resolve-complex-customer-issues |
| Gorgias | Gorgias uses AI agents to improve customer service | https://temporal.io/in-use/gorgias-uses-ai-agents-to-improve-customer-service |
| Retool | How Retool built robust workflow agents products | https://temporal.io/in-use/how-retool-built-robust-workflow-agents-products |
| Nooks | 官方案例页 | https://temporal.io/in-use/nooks |
| Vodafone | orchestrate value-added services across devices,其中含 agentic 流程 | https://temporal.io/in-use/how-vodafone-aims-to-orchestrate-value-added-services-across-devices |
| Attentive | Temporal Cloud 基础设施降本案例,其推荐引擎含 AI 组件 | https://temporal.io/in-use/attentive-migrates-temporal-cloud-infra-cost-savings |
| Duolingo | Duolingo + Temporal Nexus,用 Temporal 编排 AI 辅助学习流程 | https://temporal.io/in-use/duolingo-temporal-nexus |
| FireHydrant | Incident response + AI 辅助摘要 | https://temporal.io/in-use/firehydrant |
| Mollie Payments | 运营效率案例,含 AI 评分/风控 | https://temporal.io/in-use/mollie-payments-maximizes-operational-efficiency |

补充:Temporal 官方还宣称服务 **90+ AI 客户**(见官网 AI solutions 页集合宣传)。该数字为市场声明,未单独披露全部名单,因此作为**二级证据**记录。

## 一级证据(客户本人公开演讲)

- **Hebbia**(企业文档 agent)—— 在 Temporal 官方博客 / Replay 大会露出,其核心 agent loop 运行在 Temporal Workflows 上。证据:https://temporal.io/blog 关键词 Hebbia。
- **Abridge**(医疗文档 AI)—— Temporal 官方客户案例与联合博客。
- **Datastax**—— Replay 2024 演讲标题 Durable RAG: productionising generative AI workflows at Datastax。URL:https://temporal.io/resources/on-demand/durable-rag-ai

## 二级证据(媒体报道 / 会议议程 / 开源仓库)

- **Temporal x OpenAI Agents SDK**:Temporal 2025 年发布过与 OpenAI Agents SDK 的集成公告,含示例仓库,说明 Temporal 主动把自己对接到 AI agent 生态。这证明 Temporal 在此领域有投入,但不能用来证明 OpenAI Agents SDK 使用者都在用 Temporal。
- **Replay 2024 AI 相关演讲**(一级议程):
  - Durable RAG: productionising generative AI workflows at Datastax(已列于 Datastax)
  - 另有数场聚焦 AI/agent 的 session 收录于 https://replay.temporal.io
- **Replay 2026 AI 标签**:replay.temporal.io 2026 议程中新增 AI/Versioning 专题,含 Python workshop 标题 Building Durable AI Agents With Temporal。这是厂商主导活动,作为二级证据。

## 三级证据(求职 / 社区)

- 多家 YC 孵化 AI 初创公司在 JD 中列出 Temporal 为 nice-to-have(样本见 05-sources.md)。
- Temporal Slack / Discord 中存在大量 AI agent 问题讨论,用户自述使用 LangChain / LlamaIndex + Temporal 的混合栈。

## 小结

可以**具名列出**的 Temporal AI/agent 客户数量级是 **10+**,再加官方宣称的 90+ AI 客户(未全部具名)。这些客户真实存在,但仅占整个 AI agent 产品生态的一小部分,不足以支撑 原命题。具体反例见 02 文件。
