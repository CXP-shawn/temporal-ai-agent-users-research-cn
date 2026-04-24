# 02 对原命题的逐条核验

原命题:**所有主流 AI Agent 工具都在使用 Temporal 作为工作流运行时**。

本文件对该命题做逐条核验,结论:**该命题不成立**。命题成立需要两个条件同时满足:(a) 有一份"主流 AI Agent 工具"的清单;(b) 清单中**绝大多数**使用 Temporal。实际情况是:

- 清单本身有争议,但一般会包含 LangChain / LangGraph、LlamaIndex、AutoGen(Microsoft)、CrewAI、OpenAI Agents SDK、Anthropic Agents、Vercel AI SDK、Replit Agent、Cursor 等;
- 上述工具中,**绝大多数并不依赖 Temporal 运行时**。

## 2.1 Replit Agent —— 使用 Inngest,不是 Temporal(一级反例)

**证据等级:一级**。

- Inngest 官方客户页(https://www.inngest.com/customers)把 Replit 列为客户;
- Inngest 专门发布过 Replit 案例研究,标题含 *How Replit built their AI Agent on Inngest*;URL:https://www.inngest.com/customers/replit
- 没有任何 Temporal 官方材料把 Replit 列为客户。

结论:Replit Agent 的耐久执行运行时是 Inngest,不是 Temporal。这一条独立就足以证伪 原命题。

## 2.2 Vercel AI SDK —— 是库而不是运行时(一级反例)

**证据等级:一级**。

- Vercel AI SDK 是一个 TypeScript 库(https://github.com/vercel/ai),生成文本/调用工具/流式响应等能力由库内实现,**不需要任何外部 workflow 服务器**。
- Temporal 官方发布过 *Integrating Vercel AI SDK with Temporal* 的教程(https://temporal.io/blog 中检索得到)。该教程证明 Temporal 官方主动为 Vercel 用户提供集成示例。
- **把官方发布的集成示例等价于 "Vercel AI SDK 依赖 Temporal 运行时" 是严重误读**。同样的集成示例 Temporal 也为 LangChain、OpenAI Agents SDK 发过,不代表这些工具依赖 Temporal。
## 2.3 LangGraph / LangGraph Platform —— 自研 durable 层(一级反例)

**证据等级:一级**。

- LangGraph 是 LangChain 公司推出的 graph-based agent 编排库,其商业化产品 **LangGraph Platform** 提供 managed durable execution,**底层不使用 Temporal**,而是 LangChain 自研。
- LangChain 官方文档页面 https://langchain-ai.github.io/langgraph/ 明确说明 LangGraph Platform 提供 persistence / checkpointing / human-in-the-loop。
- 这是 Temporal 的直接竞品,不是 Temporal 的用户。

## 2.4 CrewAI —— 自管 session,不依赖 Temporal(二级反例)

**证据等级:二级**。

- CrewAI(https://github.com/crewAIInc/crewAI)是进程内 Python 框架,自己管理 agent loop,不绑定 Temporal。
- CrewAI 商业化的 CrewAI Enterprise 提供其自有的 orchestration 后端。

## 2.5 AutoGen (Microsoft) —— 自有后端(二级反例)

**证据等级:二级**。

- AutoGen(https://github.com/microsoft/autogen)由 Microsoft Research 出品,v0.4 以后重构为事件驱动架构,采用 gRPC runtime,不使用 Temporal。
- 微软内部运行时生态偏向 Durable Task Framework / Dapr Workflow,这两者才是 Azure 官方的 durable 工作流选择。
## 2.6 OpenAI Agents SDK —— 运行时开放(二级反例)

**证据等级:二级**。

- OpenAI 于 2025 年发布的 Agents SDK(https://github.com/openai/openai-agents-python)是一个 Python 工具库,自带轻量 session 与 handoff 能力,并**不强制绑定任何 workflow 服务器**。
- Temporal 官方发布过 *Temporal x OpenAI Agents SDK* 集成示例,但这只代表集成**可行**,不代表 OpenAI 或其用户必然选择 Temporal。
- OpenAI 的 Assistants API / Responses API 本身由 OpenAI 自有后端承载。

## 2.7 Anthropic Agents / Claude Agent SDK —— 运行时开放(二级反例)

**证据等级:二级**。

- Anthropic 官方 Agents Cookbook 与 Claude Agent SDK 没有任何绑定 Temporal 的说明。

## 2.8 Cursor / GitHub Copilot 等 IDE agent

**证据等级:三级**(缺乏直接披露)。

- 这些产品的后端 orchestration 未公开细节,但 Cursor/GitHub Copilot 公开演讲中讨论的技术栈以自研 + OpenAI/Anthropic API 为主,**没有任何公开材料提及 Temporal**。

## 2.9 LlamaIndex —— 自研 workflow 层(二级反例)

**证据等级:二级**。

- LlamaIndex 2024 年推出了 LlamaIndex Workflows(https://docs.llamaindex.ai/en/stable/module_guides/workflow/),是其自有事件驱动工作流,不依赖 Temporal。
## 2.10 Temporal 真正的用户在哪里

- Temporal 的 AI/agent 客户真实存在(见 01 文件),但集中在**企业后端类 agent**(客服、文档、incident response、数据管道)。
- 面向开发者的框架层(LangChain、LlamaIndex、CrewAI、AutoGen)几乎没有使用 Temporal 的。
- 面向终端用户的 agent 产品(Replit、Cursor、Vercel v0)也未使用或未依赖 Temporal。

## 结论

原命题 **所有主流 AI Agent 工具都在使用 Temporal 作为工作流运行时** 与公开证据不符,至少:

1. Replit Agent 明确使用 Inngest;
2. LangGraph Platform 是 Temporal 的**直接竞品**,自研 durable 层;
3. Vercel AI SDK / OpenAI Agents SDK / LlamaIndex 都是**可与 Temporal 集成但并不依赖 Temporal**的库。

正确的表述应当是:**Temporal 是多家企业级 AI/agent 后端采用的 durable execution 引擎之一,与 DBOS、Restate、Inngest、Hatchet、LangGraph Platform 等方案处于同一竞争层**。见 03 与 04 文件。
