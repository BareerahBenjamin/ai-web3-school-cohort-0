# 智能体钱包（Agent Wallet）

> 定义 Agent 可代表用户做哪些链上动作，以及额度、时间、对象与撤销条件；不是「把私钥交给 AI」。

## 解释

Agent Wallet 解决自动化与资产安全之间的张力：既要让 Agent 执行有用操作（付 API 费、提交低风险 tx、按策略 swap），又不能把**控制权交给概率系统**。第一性原理：**可验证、可限制、可撤销的行动空间**——主资产由人控制，Agent 仅持 session / policy 允许的子权限。

依赖 [[concepts/smart-account]]、[[concepts/account-abstraction]]，并与 [[concepts/web3-tool-use]]、模拟、人审联动。

## 例子

- **策略引擎**：链上模块检查「单笔 < 50 USDC 且目标在 allowlist」才执行。
- **两阶段支付**：Agent 生成托管条件，满足服务证明后再 release（见 settlement 相关 source）。
- **只草稿不广播**：Agent 只输出 UserOp 草稿，钱包 UI 模拟后用户点确认。

## 误区

- **「Agent Wallet = 热钱包私钥进服务器」**：应默认 session + 限额。
- **「用户点过一次同意就永久授权」**：须可审计、可撤销。
- **「AA 上线就无需 Guard」**：Guard/Policy 设计是产品核心。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 明确 scope 的自动化 | 主私钥、无限 approve 交给 Agent |
| 与模拟、日志、告警联用 | 无撤销入口的「黑盒自动交易」 |

## 参见

- [[concepts/wallet]]
- [[concepts/smart-account]]
- [[concepts/session-key]]
- [[concepts/web3-tool-use]]
- [[concepts/ai-security]]

## 来源摘要

- [[sources/handbook__bridge__agent-wallet]]
