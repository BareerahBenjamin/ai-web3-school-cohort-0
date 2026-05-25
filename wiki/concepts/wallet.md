# 钱包（Wallet）

> 用户管理账户、签名授权与确认风险的入口；不是简单的「Web3 登录按钮」。

## 解释

钱包连接身份（地址）、密钥材料（或智能账户控制器）、网络选择与交易签名流程。对用户而言，它是意图进入链上执行前的**最后一道确认界面**；对 Agent 而言，钱包是权限边界的载体，而非可交给模型的黑盒。

EOA 钱包由单一私钥控制；Smart Account 则可在链上表达更细规则（见 [[concepts/account-abstraction]]）。

## 例子

- **MetaMask 确认**：展示 to、value、data、模拟后的资产变化，用户拒绝异常授权。
- **只读连接**：dApp 仅需 `eth_accounts` 展示 portfolio，不请求签名。
- **多链切换**：用户显式选 L2，避免 Agent 在错误链上构建交易。

## 误区

- **「连接钱包 = 同意一切后续操作」**：每次签名仍是独立授权。
- **「钱包地址 = 实名身份」**：地址可复用、可合约化。
- **「把 Agent 绑在用户钱包上就不用管」**：须 Session Key / Policy 限权。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 人类最终确认高风险 tx | 把主私钥交给自动化 Agent |
| 清晰展示模拟结果 | 用钱包 UI 替代服务端风控 |

## 参见

- [[concepts/eoa]]
- [[concepts/agent-wallet]]
- [[concepts/smart-account]]

## 来源摘要

- [[sources/handbook__web3__wallet]]
