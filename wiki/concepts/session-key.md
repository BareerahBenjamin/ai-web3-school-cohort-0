# Session Key（会话密钥）

> 限时、限额、限合约的临时授权，常用于 Agent 在可控范围内自动签名。

## 解释

Session Key 让 Smart Account 在一段时间内接受特定子密钥签名的操作，而无需每次动用主密钥。策略可约束：目标合约、方法 selector、单笔/累计额度、过期时间。用户应能查看活跃 session、历史操作并一键撤销。

## 例子

- **游戏内微支付**：24h 内仅可向游戏合约支付 < 1 ETH。
- **交易机器人**：仅 `swap` on 指定 Router，禁止 `approve` 无限额度。
- **撤销**：用户发现 Agent 异常，revoke session 后立即失效（已确认 tx 除外）。

## 误区

- **「Session = 永久 API Key」**：必须有过期与 scope。
- **「给了 Session 就不用模拟」**：每次 UserOp 仍应模拟。
- **「一个 Session 管所有链」**：策略按 chainId 分开。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 低频、可预测自动化 | 主资产无上限授权 |
| 与用户可见的权限面板配合 | 模型自行生成 session 参数且无校验 |

## 参见

- [[concepts/agent-wallet]]
- [[concepts/smart-account]]
- [[concepts/account-abstraction]]

## 来源摘要

- [[sources/handbook__bridge__agent-wallet]]
