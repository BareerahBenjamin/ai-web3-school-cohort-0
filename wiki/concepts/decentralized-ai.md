# 去中心化 AI（Decentralized AI）

> 重新设计 AI 系统中数据、模型、算力、推理、评测与收益分配的组织方式，而非简单「把模型放到链上」。

## 解释

Decentralized AI 讨论谁拥有数据、谁运行推理、如何验证输出、如何激励贡献者与如何抗审查。链上组件可能记录承诺、支付、声誉或验证结果，但大模型推理往往仍在链下；关键是**对齐激励与可验证边界**，见 [[concepts/verifiable-ai]]。

与 [[concepts/rag]]、[[concepts/evaluation]] 结合可构建开放知识库与评测市场。

## 例子

- **推理市场**：用户为 GPU 推理付费，链上记录任务 hash 与交付证明。
- **联邦数据**：贡献者加密上传数据，模型训练在 TEE 或 ZK 流程中完成（视具体方案）。
- **开放权重治理**：社区投票是否发布新 checkpoint。

## 误区

- **「上链 = 去中心化」**：中心化运营 + 链上 NFT 仍是中心化。
- **「链上跑 70B 模型才正宗」**：工程与经济常要求链下推理 + 链上验证。
- **「代币激励可替代质量」**：无 eval 会激励垃圾贡献。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 讨论治理、激励、验证架构 | 用概念包装无验证的「AI 币」 |
| 与隐私、主权需求对齐设计 | 期望链自动保证模型诚实 |

## 参见

- [[concepts/verifiable-ai]]
- [[concepts/llm]]
- [[concepts/evaluation]]

## 来源摘要

- [[sources/handbook__bridge__decentralized-ai]]
- [[sources/part3__decentralized-ai]]
