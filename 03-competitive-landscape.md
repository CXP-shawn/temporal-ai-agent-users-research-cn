# 03 竞品:Temporal 在 durable agent orchestration 的竞争格局

如果原命题成立,应当看不到与 Temporal 并行竞争的、拥有真实商业客户的同层级产品。事实恰恰相反:**durable execution for AI agents** 是一个多玩家赛道,至少包括 DBOS / Restate / Inngest / Hatchet / LangGraph Platform。下面逐个给出证据。

## 3.1 DBOS

- 定位:**Postgres-native durable execution**,不需要单独的 workflow 服务器。
- 创始团队:Qian Li(前 Databricks / OSDI 论文作者)、Peter Kraft、Mike Stonebraker(Turing Award;Postgres 共同创始人),Matei Zaharia(Spark 共同创造者,Databricks CTO)为科学顾问。
- 核心对比卖点(官网 https://www.dbos.dev):
  - *No separate workflow server* —— 显式与 Temporal 对比;
  - *Workflows are just Postgres rows* —— 用 Postgres 的 ACID 来实现 durability;
  - 使用场景包含 AI agents(官网首页第一块 banner 就是 *Durable AI Agents*)。
- 证据等级:一级(厂商官网、创始人公开文章)。URL:https://www.dbos.dev / https://dbos.dev/blog

## 3.2 Restate

- 定位:开源 durable execution runtime,强调 suspend/resume 语义。
- 创始人:Stephan Ewen(前 Apache Flink PMC),团队含多位流处理与分布式系统资深工程师。
- 核心对比卖点(https://restate.dev):
  - 单二进制、低延迟(强调与 Temporal 相比更轻的部署)。
  - 官网 AI 板块含 agent use case(durable AI workflows)。
- 证据等级:一级(厂商官网)。
## 3.3 Inngest

- 定位:durable event-driven workflows,SaaS + 开源。
- 典型 AI agent 客户:**Replit**(客户页 https://www.inngest.com/customers,案例 https://www.inngest.com/customers/replit)、Soci、Otterly 等。
- Inngest 的定位明确指向 AI 工作流:官网顶部 banner 多次出现 *Background jobs and AI workflows*。
- 证据等级:一级(厂商官网、客户页)。

## 3.4 Hatchet

- 定位:Postgres-backed task queue + workflow,在 YC 孵化,类似 Temporal 但更轻量。
- GitHub:https://github.com/hatchet-dev/hatchet
- 强调 Python-first 与 agent use case,文档中含 *durable AI agents* 示例。
- 证据等级:二级(开源仓库 README、官网)。

## 3.5 LangGraph Platform

- 定位:LangChain 自研的 managed durable agent orchestration。
- URL:https://www.langchain.com/langgraph
- 核心差异:与 LangGraph OSS 同生态,天然与 LangChain 栈集成。底层的 checkpointer / persistence 为 LangChain 自研,不使用 Temporal。
- 这是最直接的 Temporal 对标竞品,因为它与 LangChain 生态深度绑定,转换成本极低。
- 证据等级:一级(厂商官网)。
## 3.6 其它邻近方案

- **AWS Step Functions / Azure Durable Functions / Google Cloud Workflows**:云厂商提供的托管 durable 执行,通常不会出现在 AI agent 讨论中,但在企业内部被大量用于 AI 流程。
- **Prefect、Dagster**:数据工程导向的 workflow,偶有团队用来承载 batch AI pipeline,但不覆盖实时 agent loop。
- **Airflow**:同上,更侧重 ETL。
- **Celery + Redis / RQ**:仍是很多小团队跑 agent job 的默认栈,不提供 durable 状态。

## 3.7 人员流动

- DBOS 创始团队含有 Temporal / Cadence 学术圈背景与数据库圈背景,明确把自己定位为 Temporal 的替代。
- Restate 团队来自 Apache Flink 社区,把 durable execution 看作 stream processing 的继承者,与 Temporal 同台竞争。
- Inngest 团队来自 Datadog / Clerk 等出身,把 durable workflow 定位为 developer platform 能力,和 Temporal 在同一商业赛道。

这些人员动向本身说明,Temporal 的存在并非无对手,恰恰引发了同赛道的多家公司出现。

## 3.8 Temporal 自身对此的回应

- Temporal 近一年在博客与 Replay 大会中密集强调 AI agent 场景(Replay 2024 / Replay 2026 议程都有 AI 专题,见 05 文件 URL 清单);
- Temporal 也主动发布与 OpenAI Agents SDK、Vercel AI SDK、LangChain 的集成示例,这说明 Temporal 把自己定位为**工具生态里的选项之一**,而不是**所有工具的底层**。

结论:AI agent orchestration 是一个**多玩家、在加速竞争**的赛道,Temporal 是重要玩家但不是唯一,更不是事实标准。
