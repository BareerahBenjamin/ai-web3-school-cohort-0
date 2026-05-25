# 知识库说明

本目录不复制完整 Obsidian 库，只记录**与学习仓库的对接方式**。

## 本地知识库位置

```
G:\obsidian\Karpathy-wiki-demo
├── raw/docs/zh/          # 原始 Handbook 与课程文档（只读参考）
└── wiki/
    ├── index.md          # 总目录
    ├── log.md            # ingest 操作日志
    ├── sources/          # 各章摘要页
    ├── concepts/         # 概念交叉引用
    └── entities/         # 实体（School、Bootcamp 等）
```

## 如何使用

1. 在 Obsidian 中打开 `Karpathy-wiki-demo` 仓库。
2. 按 `wiki/知识地图.md` 中的周次阅读 `[[sources/...]]` 与 `[[concepts/...]]`。
3. 学习产出（笔记、实验、反馈）写在本 Git 仓库对应目录，并 commit。
4. 发现 Handbook 问题 → 在 `handbook-feedback/` 写反馈，并在 Obsidian 概念页补充「待验证」备注（可选）。

## 与 ai-web3-school-cohort-0 的分工

| 位置 | 放什么 |
|------|--------|
| Obsidian `wiki/` | 概念地图、摘要、双链导航 |
| GitHub 本 repo | 打卡、任务、实验代码、MVP、提交记录 |
