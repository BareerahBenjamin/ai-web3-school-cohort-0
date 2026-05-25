# Web3 工具调用（Web3 Tool Use）

> 把 RPC、合约读、交易草稿、钱包确认等封装为 Agent 可调用的工具；难点在权限、模拟与审计，而非「能调用」。

## 解释

Web3 Tool Use 是 [[concepts/tool-use]] 在链上的特化：工具可能包括 `eth_call`、事件查询、ABI 编码、`eth_sendRawTransaction`（通常应禁用或走人审）、模拟器接口等。每个工具须声明链 ID、只读/写、是否产生链上副作用，并在调用前后记录参数与返回 hash。

应与 [[concepts/chain-aware-context]] 配合，避免模型在错误链或过期状态下构建 tx。

## 例子

- **`simulate_transaction`**：返回 revert 原因与余额变化，不广播。
- **`read_contract`**：只读 `balanceOf`，无 gas 消耗。
- **禁止裸 `send_transaction`**：仅 `propose_transaction` 供钱包确认。

## 误区

- **「接上 RPC 工具就已是链上 Agent」**：无模拟与限权仍是玩具。
- **「模型生成的 calldata 可直接发」**：必须 decode + 规则 + 人审。
- **「公共 RPC 足够生产」**：需速率、隐私与故障切换策略。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 只读分析 + 草稿 + 模拟 | 服务器持主钥自动广播 |
| 与 MCP、Agent Wallet 联用 | 无 chainId 检查的工具 |

## 参见

- [[concepts/agent]]
- [[concepts/mcp]]
- [[concepts/chain-aware-context]]
- [[concepts/agent-wallet]]

## 来源摘要

- [[sources/handbook__bridge__web3-tool-use]]
