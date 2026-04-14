---
name: personal-brain
type: skill
title: Personal Brain — 个人知识脑
description: 建立和管理个人知识脑的系统。核心原则：Entity Detection + Back-linking + Citation + Filing Rules。
category: personal-knowledge
version: 1.0.0
author: inspired by garrytan/gbrain
created: 2026-04-14
tags: [knowledge-management, personal-brain, entity-detection, citation, filing-rules]
status: active
---

# Personal Brain — 个人知识脑

Thin harness, fat skills. 用 markdown 文件作为知识存储载体，用结构化流程管理信息输入、检索和维护。

**核心理念：** 你的大脑应该像一个情报分析室——每个实体（人、公司、概念、叙事元素）都有档案，所有信息可溯源，所有引用有出处，新输入自动关联旧知识。

---

## 核心原则（必须遵守）

### 1. 归属规则（Primary Subject Rule）

内容的**主要主题**决定存放位置。不是格式，不是来源，不是工具。

| 错误 | 正确 | 原因 |
|------|------|------|
| 关于某人的分析 → `sources/` | → `people/` | 主要主题是人 |
| 关于公司的研究 → `sources/` | → `companies/` | 主要主题是公司 |
| 可复用的叙事框架 → `sources/` | → `concepts/` | 这是思维模型 |
| 关于某概念的讨论 → `sources/` | → `concepts/` | 主要主题是概念 |

**`sources/` 只用于：** 批量数据导入、API 原始导出、定期快照。原始材料需要喂养多个档案时才用。

### 2. 可关注度门槛（Notability Gate）

不是所有东西都值得建档案。建档前问：
- **人：** 我会再和他/她互动吗？和我的工作相关吗？
- **公司：** 和我的工作或兴趣相关吗？
- **概念：** 这是值得以后复用的思维模型吗？
- **存疑时：不要建。** 缺失的档案以后可以补，垃圾档案浪费注意力、污染搜索质量。

### 3. 反向链接铁律（Iron Law: Back-Linking）

每个提及有档案的人/公司，必须在**他们的档案页**创建反向链接指向当前页面。双向链接是图谱智力的来源。

格式（追加到 Timeline 或 See Also）：
```
- **YYYY-MM-DD** | 在 [页面标题](../path/to/page.md) 中被提及 -- 简短上下文
```

未连接提及 = 破损的知识脑。图谱即智能。

### 4. 引用要求（Citation Requirements）

每个写入档案的事实必须带内联引用 `[Source: ...]`。

三种格式：
- **直接归属：** `[Source: User, {context}, YYYY-MM-DD]`
- **外部来源：** `[Source: {provider}, YYYY-MM-DD]` 或 `[Source: {publication}, {URL}]`
- **综合：** `[Source: compiled from {sources list}]`

权威性优先级（高到低）：
1. 用户直接陈述（最高权威）
2. 综合真相（预存的知识脑综合）
3. 时间线条目（原始证据）
4. 外部来源（最低权威）

来源冲突时，注明矛盾，不静默选其一。

---

## 技能清单

| Skill | 用途 |
|-------|------|
| `brain-entity-detection` | 每条消息触发实体检测，将信号注入知识脑 |
| `brain-ingest` | 摄取会议、文章、媒体、文档到知识脑 |
| `brain-query` | 用三层搜索回答问题，附引用溯源 |
| `brain-maintain` | 知识脑健康检查：反向链接、引用审计、整理验证 |

## 目录结构约定

```
~/.hermes/brain/
├── people/           # 人物档案
├── companies/        # 公司/组织档案
├── concepts/        # 概念/框架/叙事元素档案
├── projects/        # 项目档案（副业、课程等）
├── meetings/        # 会议记录（YYYY-MM-DD-title.md）
├── media/           # 媒体内容（按类型/来源子目录）
│   ├── articles/    # 文章
│   ├── videos/      # 视频（含原始 transcript 链接）
│   ├── podcasts/    # 播客
│   └── social/      # 社交媒体
├── sources/         # 仅用于批量原始数据
└── .raw/            # 原始文件 sidecar（<100MB 文本/PDF）
```

## 工具使用

- `read_file` / `write_file` — 读写脑页
- `search_files` — 搜索脑内容
- `terminal` — 运行 gbrain 命令（如已安装）
