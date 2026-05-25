# 检索增强生成（RAG）

> 从知识库取回、筛选、引用外部证据再交给模型生成的链路；目标是可验证的回答，而非「接一个向量库」。

## 解释

RAG 解决训练知识过期与 context 放不下的问题：用户提问 → **Retriever** 取候选 chunk →（可选）**Rerank** → 带 citation 的生成。可靠性取决于**证据链**三层：怎么切文档（Chunking）、怎么检索（含 metadata 过滤）、生成时能否拒答与引用原文。

向量相似 ≠ 答案正确：旧版 SDK、第三方博客可能与问题语义相近却错误。Vector DB 应存来源、版本、链、更新时间、可信等级；检索失败时系统应说「不确定」，而不是让模型补全。

在 AI × Web3 中，RAG 常用于协议文档、合约 ABI 说明、治理材料；**不替代**链上模拟与权限检查。

## 例子

- **协议 FAQ**：按 API 小节切块，检索时过滤 `version=2.x`，答案附文档段落链接。
- **混合检索**：向量 + 关键词找「EIP-4337 UserOperation」，再用 rerank 把官方 spec 排在博客前。
- **拒答**：无 chunk 分数超过阈值时返回「知识库无覆盖」，禁止编造接口参数。

## 误区

- **「有向量库就是 RAG」**：无 citation、无 freshness 只是把幻觉搬到检索层。
- **「chunk 越小越好」**：过小断语义；过大噪声多、费 token。
- **「检索 Top-1 就够」**：单段常缺限制条件；应 Top-k + rerank + 多源交叉。
- **「RAG 可以替代链上查询」**：余额、nonce、授权状态必须实时查链或索引。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 文档型、历史型、长文本知识 | 实时链上状态、私钥、单次授权结果 |
| 带出处与版本的产品问答 | 无 metadata、无拒答策略的 Demo |
| 与 eval 监控引用准确率 | 高风险执行的最终依据 |

## 参见

- [[concepts/embedding]]
- [[concepts/context]]
- [[concepts/llm]]
- [[concepts/evaluation]]
- [[concepts/hallucination]]

## 来源摘要

- [[sources/handbook__ai__rag]]
