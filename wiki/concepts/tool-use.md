# Tool Use（工具调用）

> Agent 调用外部系统的能力层；从「能回答」变为「能做事」，风险随副作用等级陡增。

## 解释

Tool Use 将搜索、数据库、HTTP、代码执行、邮件、支付、链上 RPC 等封装为模型可请求的动作。每个工具应定义：输入 schema、只读/读写、副作用范围、速率限制、审计日志、是否需人审。Prompt Injection 与模型误判在**写工具**上后果远高于读工具。

设计原则：默认最小权限；写操作与不可逆操作分离；调用前后记录参数与返回。

## 例子

- **只读 `get_balance`**：Agent 分析投资组合，无签名路径。
- **草稿 `build_transaction`**：返回未签名 tx，由钱包 UI 模拟后用户确认。
- **分工具 `send_email` vs `send_email_draft`**：后者只写草稿箱，前者需人审 token。

## 误区

- **「一个 mega-tool 搞定一切」**：难以审计与限权。
- **「模型选的参数一定合法」**：必须 JSON schema + 业务 allowlist 校验。
- **「读网页工具无风险」**：恶意页面可注入指令影响后续写工具。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 明确 schema 与权限分级 | 无日志的自动写库/转账 |
| 与 MCP、eval 联调 | 把主私钥操作封装给模型 |

## 参见

- [[concepts/agent]]
- [[concepts/mcp]]
- [[concepts/web3-tool-use]]
- [[concepts/prompt-injection]]

## 来源摘要

- [[sources/handbook__ai__agent]]
