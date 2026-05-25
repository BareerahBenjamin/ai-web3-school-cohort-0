# 索引（Indexing）

> 把区块、交易、事件与合约状态整理为可快速查询的结构化数据，供产品与 Agent 使用。

## 解释

链上数据公开但不宜直接扫链：Indexing 通过 subgraph、自建 indexer、托管 API 等将 Event/logs 转为数据库视图。AI Agent 依赖索引做历史分析、持仓、治理投票记录等；须注意索引延迟、重组处理与数据源可信度。

与 [[concepts/chain-aware-context]] 配合时，应标注 `indexed_at` 与 `chain_id`。

## 例子

- **DEX 成交历史**：Indexer 聚合 Swap 事件，Agent 回答「过去 7 天成交量」。
- **NFT 持有**：按 owner 索引，避免 Agent 对每个 token 发 RPC 风暴。
- **重组告警**：检测到 reorg 时标记近期 tx 为 pending 复核。

## 误区

- **「索引 = 绝对真相」**：延迟与 bug 会发生，关键余额仍应 RPC 复核。
- **「一个 indexer 覆盖所有链」**：多链需分 schema。
- **「把索引当 RAG 文档」**：索引是结构化事实，文档 RAG 是另一层。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 聚合查询、仪表盘、研究 | 单笔高额转账的唯一依据 |
| 与实时 RPC 交叉验证 | 无监控的第三方索引盲信 |

## 参见

- [[concepts/chain-aware-context]]
- [[concepts/web3-tool-use]]

## 来源摘要

- [[sources/handbook__web3__indexing]]
