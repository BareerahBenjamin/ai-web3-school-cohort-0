# AI 安全（AI Security）

> 防止模型错误、恶意上下文与工具滥用变成真实资产、权限或治理事故；不止于「防止说错话」。

## 解释

AI Security 覆盖 Prompt Injection、过度代理（Excessive Agency）、敏感数据泄漏、不可信检索内容、工具参数篡改、供应链（模型/插件）风险等。在 AI × Web3 中，文本风险可迅速变为链上损失，因此须**纵深防御**：来源标注、allowlist、模拟、人审、审计日志、速率限制与 kill switch。

与 [[concepts/prompt-injection]]、[[concepts/agent-wallet]]、[[concepts/evaluation]] 紧密相关。

## 例子

- **工具隔离**：邮件 Agent 无法调用 `transfer` 工具。
- **检索沙箱**：网页内容标记 `untrusted`，不得覆盖 system 指令。
- **告警**：同一 session 5 分钟内 3 次 revert 触发暂停与通知。

## 误区

- **「安全 = 内容审核」**：链上场景要管权限与副作用。
- **「闭源模型更安全」**：供应链与集成方式同样关键。
- **「小团队不用做威胁建模」**：Agent 一上线即有攻击面。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 与开发同步的威胁建模 | 仅靠免责声明 |
| 高风险路径强制人审 | 期望 prompt 单独防注入 |

## 参见

- [[concepts/prompt-injection]]
- [[concepts/agent]]
- [[concepts/agent-wallet]]
- [[concepts/evaluation]]

## 来源摘要

- [[sources/handbook__bridge__ai-security]]
- [[sources/handbook__tracks__ai-security]]
