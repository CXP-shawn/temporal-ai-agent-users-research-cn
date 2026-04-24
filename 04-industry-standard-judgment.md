# 04 Temporal 是不是 AI Agent 工作流的事实标准

## 判断

**不是**。原命题所包含的"事实标准"描述与公开证据不符。可以给出如下较保守、较准确的表述:

> Temporal 是企业后端 AI/agent 场景中一个重要的 durable execution 选项,拥有真实的商业客户(具名 10+、官方宣称 90+ AI 客户),但它与 DBOS、Restate、Inngest、Hatchet、LangGraph Platform 等方案处于同一竞争层。面向开发者的主流 AI agent 库/框架(LangChain/LangGraph、LlamaIndex、AutoGen、CrewAI、OpenAI Agents SDK、Anthropic Agents、Vercel AI SDK)**绝大多数没有将 Temporal 作为依赖**。

## 判断理由

### 1. 事实标准需要使用规模 + 共识

事实标准的必要条件通常是:

- 大多数相关参与者采用;
- 生态组件(库、工具、教程、招聘市场)围绕它构建;
- 没有明显的同级别竞品。

Temporal 仅满足第一条的**部分**:有真实客户,但数量级远未覆盖"大多数主流 AI agent 工具"。第二条部分满足:围绕 Temporal 有一定数量的 SDK(Python、TypeScript、Go、Java、.NET),Temporal Cloud 也有官方模板。第三条**不满足**:DBOS / Restate / Inngest / Hatchet / LangGraph Platform 都是活跃的同级别竞品,存在明显分流。

### 2. Temporal 自己的官方材料说的是什么

- 官网首页:*Durable execution for mission-critical applications*,目标市场远超 AI agent。
- AI solutions 页:*Trusted by 90+ AI companies* —— 这是官方自述的 AI 客户规模,是营销语言,不是行业调研结果。
- Replay 2024 / 2026 大会议程:AI agent 是新增的垂类专题,而不是绝对主线;依然有大量 session 聚焦通用 durable execution、迁移案例、性能。

### 3. 开发者生态的分布

按公开资料,当前主流 AI agent 工具链的 durable 层选择大致如下(样本 = 本次调研覆盖的工具):

| 工具 / 产品 | durable 运行时 | 是否使用 Temporal |
| --- | --- | --- |
| Replit Agent | Inngest | 否 |
| Vercel AI SDK | 无强依赖(TS 库) | 否 |
| LangGraph / LangGraph Platform | LangChain 自研 checkpointer | 否 |
| LlamaIndex Workflows | 自研事件驱动 | 否 |
| AutoGen (Microsoft) | gRPC + 自研 runtime | 否 |
| CrewAI | 进程内 + CrewAI Enterprise 后端 | 否 |
| OpenAI Agents SDK | 自带轻量 session | 否(但有官方集成示例) |
| Anthropic Agents | 自带 session | 否 |
| Cursor / GitHub Copilot | 未公开 | 未公开 |
| Hebbia | Temporal | **是** |
| Abridge | Temporal | **是** |
| Emergent | Temporal Cloud | **是** |
| Gradient Labs | Temporal | **是** |
| Gorgias | Temporal | **是** |
| Retool Workflow Agents | Temporal | **是** |
| Duolingo | Temporal(含 Temporal Nexus) | **是** |
| Datastax | Temporal(Replay 2024 演讲) | **是** |

比例:样本里使用 Temporal 的是**企业后端 AI 产品**,不使用 Temporal 的是**面向开发者的通用 agent 框架/SDK 与 IDE agent 产品**。这说明 Temporal 的市场切片是企业后端 durable execution,**不是**整个 AI agent 工具生态。

### 4. 竞争态势判断

- **正向趋势**:Temporal 把 *AI agents* 当成 2024-2026 的主打垂类来投入;持续输出集成示例(OpenAI / Vercel / LangChain);Replay 大会中 AI 专题在增加。
- **反向压力**:
  - DBOS 的 Postgres-native 路线对只想要一个 Postgres 的团队很有吸引力;
  - Restate 与 Inngest 已有头部 AI 客户(如 Replit 在 Inngest);
  - LangGraph Platform 天然与 LangChain 生态绑定,转换成本极低;
  - 云厂商(AWS Step Functions、Azure Durable Functions、Google Cloud Workflows)在成熟企业账户里仍是默认 durable 选项。
- **结果**:我们观察到的是一个**多选项并存、持续竞争**的市场,不是一家独大。

## 如何严格地复述结论

- 弱版本:Temporal 是**企业后端 AI/agent 场景中的主要 durable 运行时之一**。 -> 成立。
- 中版本:Temporal 是**企业后端 AI/agent 场景中使用率最高的 durable 运行时之一**。 -> 公开数据不足以判定,只能作为 Temporal 厂商自述。
- 强版本(原命题):**所有主流 AI Agent 工具都在使用 Temporal 作为工作流运行时**。 -> **不成立**。

## 给用户的建议

1. 如果关心的是"企业后端 durable 执行",Temporal 是可以认真评估的选项之一,竞品评估请同时看 DBOS、Restate、Inngest、Hatchet。
2. 如果关心的是"开发者面向的 agent 框架",选择应基于 LangChain/LangGraph、LlamaIndex、OpenAI Agents SDK、CrewAI、AutoGen 等的生态契合度,而不是 Temporal。
3. 如果关心的是"IDE / 产品级 agent(Replit/Cursor/Copilot)",目前没有一个统一的 durable 标准;各家自研或采用 Inngest 类服务。
