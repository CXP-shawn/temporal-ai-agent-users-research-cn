# Temporal 在 AI Agent 基础设施中的使用情况:独立中文调研报告

本仓库是对一条营销命题的独立调研:
> "所有主流 AI Agent 工具都在使用 Temporal 作为工作流运行时。"

调研结论提前披露:**该命题不成立**。Temporal 在 AI/agent 领域拥有真实且可观的客户基础(官方披露 90+ AI 客户、Hebbia、Abridge 等已公开案例),但它**不是**行业事实标准,更不是"所有主流工具都在用"。

它与 **DBOS、Restate、Inngest、Hatchet、LangGraph Platform** 等方案处于同一竞争赛道;其中多家的创始人和典型用户正是出自 Temporal/Uber Cadence 的前同事,他们构建新系统的公开动机之一就是"对 Temporal 的某些架构选择不满意"。

## 文件清单

| 文件 | 内容 |
| --- | --- |
| [01-confirmed-users.md](./01-confirmed-users.md) | 已确认使用 Temporal 的 AI/agent 团队(一级/二级证据) |
| [02-original-claim-verification.md](./02-original-claim-verification.md) | 对"所有主流 AI Agent 工具都在用 Temporal"逐条反例 |
| [03-competitive-landscape.md](./03-competitive-landscape.md) | 竞品:DBOS / Restate / Inngest / Hatchet / LangGraph Platform |
| [04-industry-standard-judgment.md](./04-industry-standard-judgment.md) | "是否事实标准"的判断与理由 |
| [05-sources.md](./05-sources.md) | 全部引用 URL 列表 |

## 证据等级约定

- **一级证据**:Temporal 官方、客户本身的公开声明(官网、博客、文档、Replay 大会议程)
- **二级证据**:第三方媒体报道、技术博客、会议幻灯片、开源仓库 README
- **三级证据**:求职信息、侧面引用、社区讨论

每条结论都在正文中标注等级与 URL。

## 最核心的几条修正

1. **Replit Agent 使用的是 Inngest**(Inngest 官方客户页 + 案例研究),不是 Temporal。这是对原命题最直接的反证。
2. Vercel AI SDK 不依赖 Temporal 运行时;集成文档不等于 Vercel 在用 Temporal。
3. DBOS 创始团队公开把自己定位为 Temporal/Cadence 替代。
4. Temporal 在 Replay 2024 强调 AI agents,是重要玩家,但客户仅是 AI 生态一小部分。
5. 行业有多套并行 orchestration 方案,各有客户,没有事实标准。

详见 [04-industry-standard-judgment.md](./04-industry-standard-judgment.md)。
