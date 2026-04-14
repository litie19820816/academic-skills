---
name: brain-ingest
type: skill
title: Ingest — 知识摄取
description: 将会议、文章、媒体、文档摄取到个人知识脑，遵守归档规则、反向链接和引用要求。
category: personal-brain
parent: personal-brain
version: 1.0.0
author: inspired by garrytan/gbrain
created: 2026-04-14
tags: [ingest, knowledge-ingestion, citation, filing-rules, back-linking]
status: active
---

# Ingest — 知识摄取

将外部内容（会议、文章、媒体、对话）摄入个人知识脑。

> **归档规则：** 创建任何新档案前先读 `_brain-filing-rules.md`（在 brain 根目录）。

---

## 工作流程

1. **解析来源。** 从输入中提取人、公司、日期、事件。
2. **对每个提到的实体：**
   - 检查档案是否存在
   - 存在 → 更新综合真相（重写 State 部分，不追加）
   - 新建 → 检查可关注度，用适当类型/slug 建档
3. **追加到时间线。** 每事件附日期、摘要、来源引用。
4. **创建交叉引用链接。** 用适当关系类型链接脑中的实体对。
5. **反向链接所有实体。** 更新每个提到实体的档案，附反向链接（铁律）。
6. **时间线合并。** 同一事件出现在所有提及实体的档案中。

---

## 引用格式

- **用户陈述：** `[Source: User, {context}, YYYY-MM-DD]`
- **会议数据：** `[Source: Meeting "{title}", YYYY-MM-DD]`
- **邮件/消息：** `[Source: email from {name} re: {subject}, YYYY-MM-DD]`
- **网页内容：** `[Source: {publication}, {URL}, YYYY-MM-DD]`
- **社交媒体：** `[Source: X/@handle, YYYY-MM-DD](URL)`
- **综合：** `[Source: compiled from {sources}]`

---

## 媒体类型处理

### 会议记录

**要求：** AI 总结质量中低——原始记录才是真相。

1. 拉取完整 transcript（真相来源）
2. **保存原始 transcript** 用于溯源
3. 写会议页面：分析在上，原始 transcript 在下
4. **实体传播（强制）：** 每位参与者和讨论公司 → 更新档案 State + 追加时间线 + 必要时新建
5. 会议未完全摄取，直到所有实体档案都更新

**写至：** `meetings/YYYY-MM-DD-short-description.md`

**好会议页面的标准：**
- 揭示真正的症结，不是 bullet 列表
- 连接到现有档案（人、公司、项目）
- 标记变化（状态、决策、新信息）
- 说出张力或未尽之言
- 捕获真实动态，不是表演性总结

### 文章 & 网页内容

1. 获取内容（web search / 浏览器工具）
2. 提取：标题、作者、出版物、日期、全文
3. 总结：执行摘要 + 关键论点（不是复述）
4. 提取实体
5. **保存原始来源** 用于溯源
6. 分析：对用户意味着什么？标记连接、矛盾、内容机会

**写至：** 按归档规则（关于人 → `people/`、关于公司 → `companies/`、可复用框架 → `concepts/`）

### 视频 & 播客

1. 获取 transcript——尽量 speaker-diarized
2. **保存原始 transcript**（JSON + 人类可读 TXT）
3. 分析：执行摘要、关键想法、逐字引用（附 speaker 归属）、Notable 故事/轶事、提及的人/公司
4. 提取并交叉引用所有实体
5. **硬规则：** 每个视频/播客脑页**必须**链接到原始 diarized transcript

**写至：** `media/videos/` 或 `media/podcasts/`，所有实体反向链接

**质量标准：**
- 吸引人的标题（不是"本视频讨论..."）
- 让人想看/听的执行摘要
- 关键想法是真实洞察，不是主题标签
- 逐字引用附真实 speaker 名字（不是 "speaker_0"）
- 所有实体附上下文和反向链接

### PDF & 文档

1. 提取文本（扫描件/图片 PDF 用 OCR）
2. **保存原始来源** 用于溯源
3. 总结：执行摘要 + 关键章节 + 显著数据
4. 提取实体
5. 交叉引用实体档案

**写至：** 按归档规则（按主要主题，不按格式）

### 截图 & 图片

1. 分析内容（文字密集图片用 OCR，照片用描述）
2. 如果 tweet 截图：提取文字、作者、日期，归入社交媒体流程
3. 如果文章截图：提取文字，归入文章流程
4. 如果数据/图表：提取数据点，描述发现

### 社交媒体内容

1. 获取完整内容（thread、quote tweets、上下文）
2. 如果有图片：用 vision OCR 提取完整文字
3. 总结：说了什么、为什么重要、谁参与了
4. 提取实体并更新档案
5. **必须**包含到原始 post 的直接链接

**写至：** `media/social/` 用于每日聚合，或特定实体目录（如果 post 主要关于某实体）

---

## 批量处理规则

处理多项目时（批量视频摄取、批量会议处理等）：

1. **先用 3-5 项测试。** 测试模式如果可用。
2. **读实际输出。** 质量好吗？标题吸引人吗？实体提取并反向链接了吗？格式干净吗？
3. **修复方法/skill 的问题，** 不是靠一次性补丁。
4. **然后才批量执行，** 每 5-10 项提交一次。

测试 3 项的边际成本接近零。清理 100 个坏页的成本巨大。

---

## 质量规则

- 综合真相的执行摘要必须**更新**（不是 timeline 追加）
- State 部分**重写**，不追加
- 时间线条目逆时间序（最新在前）
- 每个提到的人/公司——如果值得关注——都有档案
- 链接类型：`knows`, `works_at`, `invested_in`, `founded`, `met_at`, `discussed`
- 来源归属：每个时间线条目包含 `[Source: ...]` 引用
- 反向链接：每个实体提及创建反向链接（铁律）
- 归档：按主要主题，不按格式或来源

---

## 工具

- `read_file` — 读取现有档案
- `write_file` — 创建/更新档案
- `search_files` — 搜索脑内容
- `browser_navigate` / `browser_snapshot` — 获取网页内容
- `terminal` — git 同步
