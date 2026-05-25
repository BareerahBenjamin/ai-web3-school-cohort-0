# 链感知上下文（Chain-aware Context）

> 让 AI 在行动前看见正确的链、地址、合约、余额与数据来源，而非靠用户口述猜测链上状态。

## 解释

Chain-aware Context 是 [[concepts/context]] 在 Web3 的实例化：上下文中须包含可验证字段（`chain_id`、最新 block、地址 checksum、合约源码/ABI 版本、工具查询结果、模拟输出），并与不可信用户文本分区。Agent 若基于「用户说余额为 0」行动，而未查 RPC，极易构建错误或有风险的 tx。

常与 [[concepts/indexing]]、[[concepts/web3-tool-use]] 组合。

## 例子

- **多链仪表板**：上下文注入当前 UI 选中的 chain + 该链 explorer 链接规范。
- **提案分析**：拉取链上 `proposalId` 状态与 timelock 参数，再让 LLM 写摘要。
- **Stale 检测**：`fetched_at` 超过 60s 的余额强制刷新后再答。

## 误区

- **「用户粘贴的 tx hash 一定对应当前链」**：须校验 chain。
- **「RAG 里的旧治理帖 = 当前链上状态」**：讨论与状态要分开。
- **「模拟一次就够」**：mempool 与后续块可能改变结果。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 结构化链上字段进 context | 把未签名 tx 当已确认事实 |
| 标注数据新鲜度 | 用训练知识猜 gas 与 nonce |

## 参见

- [[concepts/context]]
- [[concepts/indexing]]
- [[concepts/web3-tool-use]]
- [[concepts/rag]]

## 来源摘要

- [[sources/handbook__bridge__chain-aware-context]]
