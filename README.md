# Academic & Personal Brain Skills

本仓库包含两个skill集合：

1. **Academic Reasoning Skills** — 将社会科学方法论转化为AI推理框架
2. **Personal Brain Skills** — 个人知识脑管理系统

---

## Personal Brain Skills

源自 [garrytan/gbrain](https://github.com/garrytan/gbrain) 的启发。

> 核心理念：**Thin harness, fat skills.** 用 markdown 文件作为知识存储载体，用结构化流程管理信息输入、检索和维护。你的大脑应该像一个情报分析室——每个实体都有档案，所有信息可溯源，所有引用有出处。

### 核心原则

| 原则 | 说明 |
|------|------|
| **归属规则** | 内容按主要主题归档，不按格式或来源 |
| **可关注度门槛** | 不是所有东西都值得建档，垃圾档案污染搜索 |
| **反向链接铁律** | 每个实体提及必须创建双向链接，图谱即智能 |
| **引用要求** | 每个事实必须带 `[Source: ...]`，冲突时双引并存 |

### Skills 清单

| Skill | 用途 |
|-------|------|
| `personal-brain` | 核心原则、目录结构、工具说明 |
| `brain-entity-detection` | 每条消息触发实体检测，将信号注入知识脑 |
| `brain-ingest` | 摄取会议、文章、媒体、文档到知识脑 |
| `brain-query` | 用三层搜索回答问题，附引用溯源 |
| `brain-maintain` | 知识脑健康检查：反向链接、引用审计、整理验证 |

### 目录结构

```
~/.hermes/brain/
├── people/        # 人物档案
├── companies/     # 公司/组织档案
├── concepts/      # 概念/框架档案
├── projects/      # 项目档案（副业、课程等）
├── meetings/      # 会议记录
├── media/         # 媒体内容（articles/videos/podcasts/social）
└── sources/       # 仅用于批量原始数据
```

---

## Academic Reasoning Skills

将社会科学方法论转化为AI推理框架的skill集合，让AI具备结构化的定性分析能力。

> 核心洞察：学术方法论本质上是**结构化的认知压缩算法**——学者们花了几十年甚至几百年打磨出的思维框架，AI天然适合执行。不同的是，AI可以不知疲倦地、标准化地运用这些框架。

## 为什么需要这些Skills

当前AI助手在分析任务上的两大短板：

1. **定性分析能力弱** —— 给一段对话/文本，AI倾向于直接总结而非结构化分析
2. **缺乏系统推理** —— 能处理具体问题，但看不见更大的系统结构

这12个skills解决的问题：

```
统计思维类（2个）          定性分析类（5个）          系统推理类（3个）         话语分析类（2个）
─────────────────         ─────────────────         ───────────────         ───────────────
simpson-paradox  ───→    grounding-theory  ───→   leverage-points  ───→  grice-implicature
bayesian-update         thick-description         causal-loop              discourse-analysis
                        emic-etic                requisite-variety
                        field-analysis
                        frame-analysis
```

## Skills 清单

### 统计思维类

| Skill | 来源 | 核心能力 |
|-------|------|---------|
| `simpson-paradox` | 辛普森悖论（统计学） | 数据分析时自动检查分组后结论是否反转，避免错误归因 |
| `bayesian-update` | 贝叶斯更新（概率论） | 判断过程从"一锤定音"变为"渐进修正"，输出可审计的推理链条 |

### 定性分析类

| Skill | 来源 | 核心能力 |
|-------|------|---------|
| `grounding-theory` | 扎根理论（社会学） | 原始材料 → 开放编码 → 轴心编码 → 选择性编码，自下而上涌现洞察 |
| `thick-description` | 深描（人类学） | 四层递进诠释：表层 → 语境 → 结构 → 理论 |
| `emic-etic` | 主位/客位（人类学） | 先用局内人视角共情理解，再用外部分析批判评估 |
| `field-analysis` | 场域理论（社会学） | 用场域/资本/惯习三维框架解析任何社会空间 |
| `frame-analysis` | 框架理论（社会学） | 识别各方框架，找出框架冲突和转换点 |

### 系统推理类

| Skill | 来源 | 核心能力 |
|-------|------|---------|
| `leverage-points` | 杠杆点理论（系统论） | 从参数调整层到范式转换层逐级扫描，找出真正的干预点 |
| `causal-loop` | 因果回路图（系统论） | 识别增强回路和平衡回路，画出系统反馈结构 |
| `requisite-variety` | 必要多样性定律（控制论） | 检查你的方案是否足够"复杂"来应对问题的"复杂性" |

### 话语分析类

| Skill | 来源 | 核心能力 |
|-------|------|---------|
| `grice-implicature` | 会话含义理论（语言学） | 通过格莱斯四准则分析"没说出来的话"，解读言外之意 |
| `discourse-analysis` | 话语分析（语言学/哲学） | 福柯式权力-知识解码，解构任何领域的主流叙事 |

## 快速开始

### 发布到 GitHub（本地已安装者参考）

如果你在本机修改了某个skill，想发布到GitHub分享：

```bash
# 1. 安装 gh（GitHub CLI）
sudo apt install gh -y

# 2. GitHub 授权（一次性）
gh auth login

# 3. 使用 hermes publish 命令
# 注意：需要完整路径，因为 hermes 不在 PATH 里
/home/litie/.hermes/hermes-agent/venv/bin/hermes skills publish \
  /home/litie/.hermes/skills/academic-reasoning/<skill-name> \
  --to github \
  --repo litie19820816/academic-skills

# 4. 首次 publish 会弹出浏览器让你授权 GitHub
# 授权一次后后续自动带 token
```

常见问题：
- `hermes: command not found` → 使用完整路径 `/home/litie/.hermes/hermes-agent/venv/bin/hermes`
- `skill_path: Is a directory` → publish 接受的是**目录路径**，不是 `SKILL.md` 文件路径
- `GitHub authentication required` → 先运行 `gh auth login`

---

## 安装

从GitHub安装单个skill：

```bash
hermes skills install github:用户名/academic-skills/simpson-paradox
```

或安装整个集合：

```bash
hermes skills install github:用户名/academic-skills/academic-reasoning
```

### 使用方式

**方式一：手动调用**

```
用 bayesian-update 分析：[你的判断问题]
用 grounding-theory 分析：[你的原始材料]
用 leverage-points 分析：[你的复杂问题]
```

**方式二：描述任务，AI自动选择**

```
帮我分析一下最近寺庙经济为什么在年轻人中这么火
→ 自动触发 thick-description + emic-etic

分析一下新能源车行业的竞争格局
→ 自动触发 field-analysis + leverage-points

看看这份会议纪要里各方实际想表达什么
→ 自动触发 grice-implicature + frame-analysis
```

## 适用场景

| 场景 | 推荐Skill |
|------|---------|
| 分析用户反馈/访谈/评论材料 | grounding-theory |
| 评估一个判断/决策的可靠性 | bayesian-update |
| 看到一个数据结论，想验证是否可靠 | simpson-paradox |
| 面对一个复杂问题不知道从哪里切入 | leverage-points |
| 想深入理解一个文化/社会现象 | thick-description + emic-etic |
| 分析行业/组织/圈子里的权力结构 | field-analysis |
| 舆情危机中各方到底在想什么 | frame-analysis + grice-implicature |
| 解读政策文件/企业财报的潜台词 | grice-implicature + discourse-analysis |
| 分析一个系统为什么会越来越糟 | causal-loop |
| 评估你的方案是否真的能解决问题 | requisite-variety |

## 设计原则

1. **框架高于结论** —— 这些skills不直接给答案，而是强制结构化分析流程，让答案从框架中涌现
2. **方法论有出处** —— 每个skill背后都有严格的学术方法论支撑，不是拍脑袋发明
3. **可组合使用** —— 复杂问题经常需要多个skill组合，比如 `emic-etic` + `field-analysis` + `grice-implicature`
4. **对AI和人都适用** —— 这些框架不仅是AI的分析工具，也是人类思考的结构化支架

## 致谢

这12个skills的灵感来源：

- Glaser & Strauss：扎根理论（1967）
- Bourdieu：场域分析（《区隔》1979）
- Goffman：框架理论（《框架分析》1974）
- Geertz：深描（《文化的解释》1973）
- Grice：会话含义理论（1975）
- Foucault：话语分析（《知识考古学》1969）
- Meadows：杠杆点理论（《系统之美》1990）
- Ashby：必要多样性定律（1956）
- Simpson：辛普森悖论（1951）
- Bayes：贝叶斯定理（1763）

这套skill体系是用户与AI在2026年4月共同创作的成果。

## License

MIT
