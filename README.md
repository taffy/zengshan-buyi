# zengshan-buyi — 《增删卜易》六爻纳甲筮法 Skill

> 把清代野鹤老人《增删卜易》蒸馏成一个可执行的 Agent Skill：从摇卦、装卦、取用神，
> 到断旺衰吉凶、推应期，以及卦象不明时的分占与多占。

一个 **WorkBuddy / 兼容 `SKILL.md` 的 Agent Skill**，纯 Markdown，无代码、无外部依赖、不联网。
共 1 个入口 + 10 张能力卡，整包 284 KB。

---

## 这是什么

《增删卜易》（清·野鹤老人 著，李文辉觉子增删）是六爻纳甲筮法史上最重要的实操手册之一。
它的独特之处不在卦辞神煞，而在**作者亲手删规则**——书名里的"增删"二字指的就是这件事：
逐条拿古法来验证，不验就删，并把删的过程写进正文。

本 Skill 保留了这套方法论骨架，尤其是：

- **四类作用力合成**（月建 / 日辰 / 动爻 / 变爻）取代了神煞吉凶的玄学判断
- **"用神无根，元神有力亦难生"** —— 根先于援
- **大象优先**：卦变回头克者，不论用神衰旺皆以凶推
- **分占与多占** —— 野鹤区别于其他所有六爻书的独门不确定性处理
- **15 条辟谬清单** —— 他亲手删掉的古法，附"错在哪 / 证据 / 正确做法"

---

## 安装

把整个目录放到用户级技能目录即可，**新对话直接可用**：

```
~/.workbuddy/skills/zengshan-buyi/
```

Windows 实际路径：`C:\Users\<你>\.workbuddy\skills\zengshan-buyi\`

也可以放到项目级：`{项目}/.workbuddy/skills/zengshan-buyi/`（仅该项目生效）。

安装后无需任何配置——`SKILL.md` 的 frontmatter 自带触发描述，Agent 会自动识别意图。

---

## 目录结构

```
zengshan-buyi/
├── SKILL.md                          # 唯一入口：触发判断、核心原则、路由表、边界与判停
├── README.md                         # 本文件
├── BUILD_MANIFEST.json               # 构建产物哈希（重编译前比对用）
├── test-prompts.json                 # 14 条触发评测用例（可选保留）
├── test-results.md                   # 独立盲测结果（可选保留）
└── references/
    ├── overview.md                   # 全书概览：作者、体例、四卷结构、核心思想
    ├── glossary.md                   # 术语词典（50 条，含原文出处）
    ├── cheatsheet.md                 # 决策规则速查
    ├── capability-index.md           # 完整意图 → 能力卡 索引
    └── capabilities/                 # 10 张能力卡
        ├── anquan-bianjie.md         # 边界、拒绝与判停（安全红线）
        ├── zhanqian-zhunbei.md       # 占前立意与提问规范
        ├── qigua-zhuanggua.md        # 起卦与装卦六步
        ├── qu-yongshen.md            # 取用神（事类 → 爻）
        ├── daxiang-geju.md           # 大象优先与格局判定
        ├── sishen-wangshuai.md       # 四神模型与四类作用力旺衰
        ├── yingqi-tuiduan.md         # 应期推断十二条
        ├── fenzhan-duozhan.md        # 分占与多占（不确定性处理）
        ├── zhanci-yingbi.md          # 占此应彼 / 占远应近的重配对诊断
        └── pimiu-fanmoshi.md         # 辟谬与反模式清单
```

---

## 十张能力卡

每张卡采用 **RIA++ 六段结构**：`R`（原文）→ `I`（自述）→ `A1`（书中案例）→ `A2`（触发场景）→ `E`（执行步骤）→ `B`（边界）。

| # | 能力卡 | 作用 | 重要度 |
|---|---|---|---|
| 0 | `anquan-bianjie` | 安全闸门：医疗/法律/金融/人身安全四类拒绝据卦下结论并引导专业渠道 | critical |
| 1 | `zhanqian-zhunbei` | 一念一事、我事亲占、他事由他动念、须指实其事 | high |
| 2 | `qigua-zhuanggua` | 起卦装卦六步（上卦在前命名、变卦六亲仍照本宫） | critical |
| 3 | `qu-yongshen` | 庇护我身者→父母，拘束我身者→官鬼；可推导现代新事类 | critical |
| 4 | `daxiang-geju` | 大象定性质、旺衰定程度；回头克/六冲/六合/三合/进退/反伏 | high |
| 5 | `sishen-wangshuai` | 四处作用力清算合成；**用神无根则元神有力亦难生** | critical |
| 6 | `yingqi-tuiduan` | 应期十二条 + 冲突时的"先后都满足"合成逻辑 | high |
| 7 | `fenzhan-duozhan` | 分占与多占 —— 本书最独门的部分 | high |
| 8 | `zhanci-yingbi` | 占此应彼三条判据（限用） | medium |
| 9 | `pimiu-fanmoshi` | 15 条作者亲手删掉的古法辟谬清单 | high |

**主链路顺序**：
`anquan-bianjie`（闸门）→ `zhanqian-zhunbei` → `qigua-zhuanggua` → `qu-yongshen`
→ `daxiang-geju` → `sishen-wangshuai` → `yingqi-tuiduan`

---

## 用法示例

装好后直接用自然语言，不需要记命令：

| 你说 | 会命中 |
|---|---|
| 「帮我用《增删卜易》的方法占一下这个 offer 该不该接」 | 全流程，按主链路逐步推进 |
| 「卦装好了，占求财该看哪一爻」 | `qu-yongshen` |
| 「官鬼持世又旬空又月破，还有子孙发动，这到底旺还是衰」 | `sishen-wangshuai` |
| 「吉凶断出来了，大概什么时候能应」 | `yingqi-tuiduan` |
| 「随鬼入墓是不是就没救了」 | `pimiu-fanmoshi` |
| 「能不能再占一卦？我还想顺便把财运和健康一起问了」 | `fenzhan-duozhan` + `zhanqian-zhunbei` |
| 「用神、元神、忌神、仇神分别是什么」 | `glossary.md`（不加载能力卡） |

**不会触发**：纯客观信息查询（天气、行情、医学检查数值、法律条文）、写代码 / 算账 / 翻译，
以及只想聊易学文化而不真要起卦的场景。

---

## 安全边界（重要）

本 Skill 内置了硬性的拒绝机制。以下四类请求**会触发**但触发后**必须拒绝据卦下结论**，
并引导至专业渠道：

| 类别 | 引导至 |
|---|---|
| 医疗诊断、用药、手术决策、预后判断 | 医生 |
| 法律后果预判（会不会败诉、判多久） | 律师 |
| 金融投资决策、行情点位 | 持牌顾问 |
| 人身安全、刑事风险评估 | 警方 |

此外还有三道拦截：**代占**（我事不可命人）、**一卦多问**（心怀两三事而占者卦必乱应）、
**卦已明现仍再渎占**（不得一直占到满意为止）。

若用户表现出**现实危机信号**（自伤倾向、正被侵害、急性重症），停止一切占卜环节，
直接引导至急救 / 报警 / 心理危机干预渠道。

---

## 认识论声明（请务必保留）

六爻纳甲属于**传统数术与民俗知识体系**，不是现代科学意义上的预测方法。
本 Skill 每张卡的 `B` 段都强制写入了四条作者的局限：

1. 全书所有"应验"案例都是**作者自己挑选并记录的**，没有对照组、没有失败率统计 —— 幸存者偏差。
2. "占此应彼 / 占远应近 / 灵机变通"构成**事后解释机制**，使规则原则上无法被证伪。
3. "屡试四十年"无法区分真正规律与巧合。
4. 案例全部是**清代前现代社会事务**（科举、援例、世职、六畜、茔葬、痘疹），
   用到现代问题必须先做事类转译。

作为**文化遗产研究、自我反思的启发式工具、创作素材**有其价值；
作为事实预测工具，**没有任何可靠的实证支持**。

---

## 来源与生成方式

- **原书**：《增删卜易》，清·野鹤老人 著，李文辉觉子增删（公有领域）
- **生成工具**：`cangjie-skill` 蒸馏流水线 `cangjie-tools v2.5.0`（书籍 → 能力卡的 RIA-TV++ 流水线）
- **流水线**：Stage 0 整书理解 → Stage 1 五路并行提取（框架/原则/案例/反例/术语，
  共产出 18 框架 + 27 原则 + 24 案例 + 28 反例 + 50 术语）→ Stage 1.5 三重验证
  （原文核验 / 跨域佐证 / 可迁移性，淘汰 12 条）→ Stage 2 构造 RIA++ 能力卡
  → Stage 3 Zettelkasten 链接 → Stage 4 独立盲测压力测试（两轮，14 条用例）
  → Stage 5 发布
- **变体**：`single`（1 个入口 + 10 张内部能力卡）
- **校验**：`validate_skill_pack.py` → **0 errors / 0 warnings**

> **关于盲测**：第一轮独立评审暴露了三处结构缺陷（医疗请求在"不适用"与"判停"两处语义打架、
> 代占路由自相矛盾、两卡同时命中无 tie-break）。修复方式是**改 Skill 而不是改测试**——
> 新增 `anquan-bianjie` 安全闸门卡，把四类红线从"不触发"改为"触发后拒绝并引导"。
> 第二轮复测 14/14 路由正确。

---

## 上传 GitHub 必须包含的文件

### 必需（缺一不可）

```
zengshan-buyi/
├── SKILL.md
├── README.md
└── references/
    ├── overview.md
    ├── glossary.md
    ├── cheatsheet.md
    ├── capability-index.md
    └── capabilities/
        ├── anquan-bianjie.md
        ├── zhanqian-zhunbei.md
        ├── qigua-zhuanggua.md
        ├── qu-yongshen.md
        ├── daxiang-geju.md
        ├── sishen-wangshuai.md
        ├── yingqi-tuiduan.md
        ├── fenzhan-duozhan.md
        ├── zhanci-yingbi.md
        └── pimiu-fanmoshi.md
```

**共 16 个文件**（1 个 SKILL.md + 1 个 README.md + 4 个 reference + 10 张能力卡）。

### 建议包含

| 文件 | 说明 |
|---|---|
| `BUILD_MANIFEST.json` | 产物哈希清单，重编译前比对，防止本地手改被静默覆盖 |
| `LICENSE` | 建议 MIT（原书为公有领域，本蒸馏产出的现代白话注释可作为独立著作权） |

### 可选

| 文件 | 说明 |
|---|---|
| `test-prompts.json` | 14 条触发评测用例 |
| `test-results.md` | 独立盲测结果记录 |

### 不需要上传

- `.cangjie/` 流水线中间产物（候选池、验证记录、快照）—— 那是生成过程的副产品，不是 Skill 运行时所需
- `books/zengshan-buyi/` 下的审计文档（BOOK_OVERVIEW、verified、DIGEST、candidates）
- `_tmp_epub/` 提取的中间纯文本

> ⚠️ 注意：中间产物里的 `DIGEST.md`（约 7000 字精华长文）和 `candidates/` 候选池
> 对想了解"这本书讲了什么"或"蒸馏过程"的人有价值。如果想让仓库既能装 Skill
> 又能当阅读材料，可以额外放进 `docs/` 目录，但**不要放进 `references/`**——
> 会被当成运行时依赖。

---

## 更新后重新同步

如果用 `cangjie.py compile` 重新编译，产物会写到工作区目录，**不会自动同步到全局技能目录**。
改完记得手动同步（或重新 `git pull` 后覆盖 `~/.workbuddy/skills/zengshan-buyi/`）。

另外：**不要同时安装 `single` 和 `pack` 两种变体**，它们会抢同一批意图、互相覆盖。

---

## 许可

原书文本属公有领域。本仓库的现代白话重述、能力卡结构、路由设计与安全边界部分
建议以 MIT 许可发布。
