# 智能体（Agent）

> 围绕目标持续调用工具、读取状态、调整步骤的 AI 系统；关键是**被约束的执行循环**，不是「更像人」。

## 解释

Agent 在 LLM 之上增加 **Tool Use**、**Planning**、**State** 与（可选）**Reflection**：从「生成一段文字」变为「多步完成任务」。一旦能写库、发请求、触发签名，错误就从答错变成做错，因此必须明确：工具权限、外置可审计状态、停止条件（达标、超预算、风险越界、用户拒绝）。

分工原则：**模型提出候选行动，系统限制行动空间，用户批准高风险边界。** 计划是候选路线，不是授权；每一步应暴露所需工具、读写属性、是否需人审。

## 例子

- **DAO 提案分析**：计划拆为读提案 → 检索历史讨论 → 输出风险清单；涉及投票交易则停在人审。
- **只读链上助手**：工具 allowlist 仅 `eth_call`、索引查询；任何 `sendTransaction` 草稿只展示不提交。
- **可恢复任务**：state 存 `{step, tool_results, pending_approval}`，服务重启后可续跑而非只靠 prompt 历史。

## 误区

- **「接上 LangChain 就是 Agent」**：框架不替代权限、日志与 eval。
- **「Agent 应该完全自主」**：生产环境需要 human-in-the-loop 与 kill switch。
- **「状态只放 prompt 里」**：无法审计、无法回答「为何调用了该工具」。
- **「工具越多越好」**：每多一个写接口，攻击面就扩大一层。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 多步研究、编排、草稿生成 | 无 allowlist 的自动主资产操作 |
| 明确只读/只写工具分级 | 把主私钥交给模型 |
| 与 MCP、Web3 工具、eval 联用 | 无停止条件与预算的开放循环 |

## 参见

- [[concepts/llm]]
- [[concepts/tool-use]]
- [[concepts/planning]]
- [[concepts/mcp]]
- [[concepts/web3-tool-use]]
- [[concepts/agent-wallet]]

## 来源摘要

- [[sources/handbook__ai__agent]]
- [[sources/part3__ai-agents]]
