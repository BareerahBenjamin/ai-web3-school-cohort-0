# 智能账户（Smart Account）

> 链上带规则的账户合约，承载权限、恢复、模块与 Agent 自动化边界。

## 解释

Smart Account 把「谁能操作、能调用哪些合约、花多少、何时失效」写在链上逻辑里，而非全部押在单一 EOA 私钥。可挂载 Guard、Session、多签、恢复等模块。Agent Wallet 的产品问题常归结为：授权是否被拆成**可检查、可撤销**的合约规则。

## 例子

- **限额模块**：每日 USDC 流出上限 100，超出需 owner 额外签名。
- **合约 allowlist**：仅可与 DEX Router、特定 NFT 市场交互。
- **紧急暂停**：owner 一键 revoke 所有 session key。

## 误区

- **「Smart Account 一定比 EOA 安全」**：错误模块配置同样危险。
- **「部署一次规则永久有效」**：协议升级须更新 Policy。
- **「Agent = Smart Account owner」**：owner 应是人或明确的多签，不是模型。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 可编程 Agent 权限 | 存放明文私钥在链上 |
| 与模拟、审计日志配合 | 无监控的开放 call 权限 |

## 参见

- [[concepts/agent-wallet]]
- [[concepts/account-abstraction]]
- [[concepts/session-key]]

## 来源摘要

- [[sources/handbook__bridge__agent-wallet]]
