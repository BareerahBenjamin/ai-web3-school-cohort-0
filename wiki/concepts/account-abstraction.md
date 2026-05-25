# 账户抽象（Account Abstraction）

> 让账户用可编程规则表达验证、gas 支付与权限，而不限于「单一私钥签一切」。

## 解释

Account Abstraction（AA）把账户从固定 EOA 模式解放：可用合约定义谁可发起操作、如何验签、是否用 Paymaster 代付 gas、如何挂载 Session Key 等。对 Agent Wallet 而言，AA 是承载**可检查规则**的基础设施，使「允许 Agent 自动做 X」变成链上可验证策略，而非口头信任。

常见实现路径包括 ERC-4337（UserOperation + Bundler）等。

## 例子

- **Session 自动化**：Smart Account 仅接受带 session 签名的 `transfer`，且单笔 < 10 USDC。
- **社交恢复**：owner 丢设备时通过 guardian 轮换，无需把恢复权给 Agent。
- **Gas 抽象**：Paymaster 为特定 Agent 操作补贴 gas，仍受 Policy 约束。

## 误区

- **「AA = 更花哨的钱包 UI」**：核心是链上规则，不是皮肤。
- **「上了 AA 就无需人审」**：策略写错同样会自动化损失。
- **「所有链 AA 体验一致」**：Bundler、入口合约因链而异。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| Agent 限额、限时、限合约 | 用 AA 绕过用户知情同意 |
| 与 [[concepts/agent-wallet]] 联设计 | 期望 AA 自动防 Prompt Injection |

## 参见

- [[concepts/erc-4337]]
- [[concepts/smart-account]]
- [[concepts/session-key]]
- [[concepts/agent-wallet]]

## 来源摘要

- [[sources/handbook__web3__account-abstraction]]
