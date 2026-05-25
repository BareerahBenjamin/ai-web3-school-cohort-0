# 评估（Evaluation）

> 用可重复样本与指标把「感觉变好了」变成可验证改进；没有 eval，prompt/RAG/Agent 改动迟早引发回归。

## 解释

Evaluation 面向**整条任务链路**（而不只是模型榜单分）：固定输入 → 调用系统 → 按规则或 judge 打分 → 存档版本与日志。核心组件包括 **Harness**（跑批框架）、**Golden Set**（高质量样本集）、**Regression**（防旧 bug 复发）、可选 **LLM-as-Judge**（开放题质量）。

原则：**不能被重复测量的行为，就不能被稳定改进。** 每修一个重要生产 bug，应考虑加入 regression set。Judge 模型有偏，高风险场景须保留人工抽检。

## 例子

- **RAG 引用率**：50 条 golden 问句，指标 = 答案是否含正确 doc_id + 人工抽检 10%。
- **Agent 工具调用**：期望 `tools_called` 序列与参数；误调 `transfer` 即判失败。
- **Prompt 回归**：改 system prompt 后全量跑 golden set，对比「拒答率、schema 合法率、关键字段 F1」。

## 误区

- **「试几个例子就算 eval」**：样本太少会把运气当改进。
- **「只看 BLEU/相似度」**：开放任务更关心任务完成度与风险行为。
- **「Judge 输出即真理」**：须与规则评分、人工校准结合。
- **「eval 只做一次」**：模型、检索库、协议文档都在变，eval 要进 CI。

## 使用边界

| 适合 | 不适合 |
|------|--------|
| 迭代 prompt、RAG、Agent 策略 | 替代链上模拟与形式化验证 |
| 30–100 条高质 golden 起步 | 用公开榜单分数代替产品场景 |
| 高风险样本 + 人工抽检 | 仅测「回答是否礼貌」 |

## 参见

- [[concepts/llm]]
- [[concepts/prompt]]
- [[concepts/rag]]
- [[concepts/agent]]
- [[concepts/hallucination]]

## 来源摘要

- [[sources/handbook__ai__evaluation]]
