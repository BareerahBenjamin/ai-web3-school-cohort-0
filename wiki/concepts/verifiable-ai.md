# 可验证 AI（Verifiable AI）

> 当 AI 输出影响资产、权限、声誉或治理时，能否验证输入、模型、执行环境或至少留下可审计证据。

## 解释

Verifiable AI 不要求所有推理都在链上 ZK 证明（虽是一种路径），但要求系统能回答：用了什么输入、什么模型版本、谁运行、结果 hash 是否上链、争议如何仲裁。与 [[concepts/decentralized-ai]]、[[concepts/evaluation]]、[[concepts/ai-security]] 交叉。

链上可能只存承诺与结果摘要，完整 trace 在链下但须防篡改存储。

## 例子

- **AI Oracle**：模型评分 + 输入 hash 上链，争议期可挑战并重跑。
- **审计日志**：每次 Agent 工具调用签名存 WORM 存储，供监管抽查。
- **TEE  attestation**：推理节点出示硬件证明，链上注册允许列表。

## 误区

- **「存 IPFS hash = 可验证」**：还须定义验证程序与激励。
- **「可验证 = 用户能看懂 ZK」**：产品层可展示「已验证/待挑战」状态。
- **「一次证明覆盖终身」**：模型与权重会变，版本须绑定。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 高影响决策的审计与争议 | 用「将来说不定可验证」推迟落地 |
| 与链上结算、托管联动 | 用口头承诺替代日志 |

## 参见

- [[concepts/decentralized-ai]]
- [[concepts/evaluation]]
- [[concepts/ai-security]]

## 来源摘要

- [[sources/handbook__bridge__verifiable-ai]]
