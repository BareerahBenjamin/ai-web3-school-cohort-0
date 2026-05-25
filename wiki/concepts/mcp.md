# 模型上下文协议（MCP）

> 标准化模型与外部工具、数据源、应用上下文之间的连接，使能力接入可描述、可复用、可管理。

## 解释

MCP（Model Context Protocol）解决的不是「模型更聪明」，而是**集成碎片化**：每个产品各自封装 API，导致工具定义、鉴权、上下文格式无法复用。MCP 提供统一方式声明资源（可读数据）、工具（可执行动作）与提示模板，让 Agent 运行时以协议发现并调用能力。

对团队意味着：工具边界、版本与权限可在 MCP Server 侧治理；模型侧主要消费结构化 tool schema。它常与 [[concepts/agent]]、[[concepts/web3-tool-use]] 配合，但不替代业务层风控与模拟。

## 例子

- **内部 runbook Server**：暴露 `search_incident`、`get_runbook` 资源，Agent 只读排障，写操作仍走工单 API + 人审。
- **多 MCP 组合**：文档 MCP + 链上只读 MCP；Orchestrator 按任务类型路由，避免一个 Server 持有过多写权限。
- **版本化 tool 定义**：`swap_quote_v2` 与 v1 并存，eval 回归确保参数 schema 变更不破坏旧样本。

## 误区

- **「上了 MCP 就安全」**：协议不自动做 allowlist、速率限制与审计。
- **「所有 API 都包成一个 MCP Tool」**：粒度过粗难以最小权限；应读写分离。
- **「MCP 替代 RAG」**：资源与检索是不同层；文档问答仍要 chunking 与 citation。
- **「客户端无需校验工具参数」**：模型生成的参数必须经过 schema 与业务规则校验。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 可复用的工具/资源接入层 | 单笔交易的最终授权逻辑 |
| 多 Agent 共享的能力目录 | 存放私钥或长期会话令牌 |
| 与标准 schema、eval 联调 | 绕过代码层直接执行高危副作用 |

## 参见

- [[concepts/agent]]
- [[concepts/tool-use]]
- [[concepts/web3-tool-use]]
- [[concepts/context]]

## 来源摘要

- [[sources/handbook__ai__mcp]]
