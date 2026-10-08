---
name: zengshan-buyi
description: |
  《增删卜易》（清·野鹤老人）六爻纳甲筮法的实操能力入口。当用户想用六爻/纳甲/铜钱卦
  占问一件事并需要按本书的方法走完流程时使用：起卦装卦、取用神、判断旺衰吉凶、推断应期，
  以及卦象不明时的分占与多占。
  覆盖：装卦排爻、用神选取、四类作用力加权、大象与格局（回头克/六冲/六合/三合/进退/反伏）、
  应期十二条、分占多占、占此应彼、以及作者亲手删掉的古法辟谬清单。
  也用于解释本书术语（用神/元神/忌神/仇神、月建日辰、旬空月破、暗动、进退神、飞伏、大象）。
  不适用：不需要起卦的客观信息查询（天气、行情、交通、医学检查数值、法律条文）；
  只是聊命理/易学文化而不真的要起卦；以及与占卜完全无关的任务（写代码、算账、翻译）。
  **注意区别**：拿医疗诊断、法律后果、金融投资、人身安全来要求断卦——这类请求**会触发**
  本 Skill，但触发后必须走 anquan-bianjie 拒绝据卦下结论并引导至医生/律师/持牌顾问/警方，
  **不是不触发**。同理，代占、一卦多问也是"触发后拦下"，不是"不触发"。
  主链路顺序：zhanqian-zhunbei → qigua-zhuanggua → qu-yongshen → daxiang-geju
  → sishen-wangshuai → yingqi-tuiduan；anquan-bianjie 是压在其上的闸门，排第一。
  注意：六爻属传统数术与民俗知识体系，不是科学预测方法，本书案例是作者自选的应验记录
  且无对照组，回答时必须保留这一认识论限定。
  trigger: 六爻 / 纳甲 / 铜钱卦 / 装卦 / 用神 / 增删卜易 / 野鹤老人 / 应期 / 分占多占 / liu yao
metadata:
  cangjie.generated-by: cangjie-tools v2.5.0
  cangjie.variant: single
  cangjie.bundle-id: bundle.zengshan-buyi
  cangjie.capability-count: 10
  cangjie.entrypoint-count: 1
---
# 增删卜易 — 全书能力入口

## 触发与不触发

**适用**：与本书能力域相关的咨询与任务（见下方路由表的意图列）。
**不适用**：
- 不需要起卦的客观信息查询（气象、行情、交通、医学检查数值、法律条文、统计数据）。
- 只想聊命理/易学文化、了解历史或问本书知识，不需要真正起卦操作（→references/overview.md、references/glossary.md）。
- 与占卜完全无关的任务（写代码、算账、翻译、查资料）。

## 核心原则（常驻速览，概览类问题读到这里即可回答）

1. 断卦只需五个变量：用神，以及施加于它的月建、日辰、卦中动爻、动爻变出之爻——四处全生则吉，全克则凶，混合则看旺衰。
2. 神兆机于动：动爻是信息的载体，动不为空、动不为散、动必有应；静卦信息量少，动卦信息量多。
3. 根先于援：用神无根，则元神有力亦难生——"虽有生扶生之不起，如树无根，寒谷不回春"。
4. 大象优先：卦变回头克者，不论用神衰旺皆以凶推；大象定性质，用神旺衰定应期与程度。
5. 空破是"待时"不是"终局"：旺不为空、动不为空，出空/实破/逢合之日即应；唯"真空"为真。
6. 一念只占一事；我事必亲占，不可命人代占；他事由他动念，慎勿提他。
7. 事多头则分占，卦恍惚则多占；卦已明现则不可再渎。
8. 用神不现时，不取伏神/互卦/化气，改再占一卦合参。
9. 星煞、六神、卦身、身位均无独立断验权，只在用神旺相时附和增吉增凶。

## 能力路由（先读本表，按意图加载 1 张能力卡）

| 用户意图 | 先读 | 补读/备注 |
|---|---|---|
| 拿医疗问题（体检结果、要不要手术、用什么药、预后）来要求断卦；拿法律后果（会不会败诉、判多久）来要求断卦；拿金融投资（要不要买/卖、什么时候涨、行情点位）来要求断卦；拿人身安全、刑事风险来要求断卦或给避险结论；用户表现出自伤倾向、正被侵害、急性重症等现实危机信号；要求替不在场的人代占 | references/capabilities/anquan-bianjie.md | references/capabilities/zhanqian-zhunbei.md、references/capabilities/fenzhan-duozhan.md、references/capabilities/pimiu-fanmoshi.md |
| 准备为一件事起卦，想确认该怎么问；想把好几件事放在一卦里问完；想让别人替自己占、或想替别人问一件事；问题太笼统（如"我今年怎么样"），不知道该怎么切 | references/capabilities/zhanqian-zhunbei.md | references/capabilities/fenzhan-duozhan.md、references/capabilities/qu-yongshen.md |
| 给出六次摇掷的正反面结果，要求排成六爻卦；不知道六亲怎么安、世应怎么定；不知道变卦怎么排、变卦的六亲按哪一宫算；自己的装卦结果和书上对不上；完全不懂五行，想知道还能不能断卦 | references/capabilities/qigua-zhuanggua.md | references/capabilities/qu-yongshen.md、references/capabilities/sishen-wangshuai.md |
| 问某个事项该取什么用神；卦里出现两处或三处同类六亲，不知该取哪个；用神完全不上卦，不知道怎么办；已由他人本人亲占、只是不确定该看哪一爻（注意：代占一律先由 anquan-bianjie 拦下）；要把现代事类（融资、面试、签证、手术、签约、跳槽）翻译成用神 | references/capabilities/qu-yongshen.md | references/capabilities/sishen-wangshuai.md、references/capabilities/fenzhan-duozhan.md、references/capabilities/pimiu-fanmoshi.md |
| 给出完整卦单，问这卦吉凶如何；多爻生克混杂，看不出谁占上风；问用神到底旺不旺、能不能得救；问元神/忌神有没有力；问月破、旬空、入墓到底算不算废 | references/capabilities/sishen-wangshuai.md | references/capabilities/daxiang-geju.md、references/capabilities/yingqi-tuiduan.md、references/capabilities/pimiu-fanmoshi.md |
| 问这卦整体什么性质；发现卦变回头克（如巽变乾、离变坎）；卦是六冲，问是不是就完了；遇到六合化冲 / 六冲化六合；出现三合局，问吉凶怎么定；动爻化进化退、或内外卦反伏；问暗动与日破怎么分 | references/capabilities/daxiang-geju.md | references/capabilities/sishen-wangshuai.md、references/capabilities/yingqi-tuiduan.md、references/capabilities/pimiu-fanmoshi.md |
| 吉凶已定，问什么时候应验；问应验在哪一天/哪一月/哪一年；卦里有旬空/月破/入墓/被合住，不知道按哪条推；已有断语，但对不上实际应在何时；同时命中两条应期规则，不知道取哪个 | references/capabilities/yingqi-tuiduan.md | references/capabilities/sishen-wangshuai.md、references/capabilities/fenzhan-duozhan.md、references/capabilities/daxiang-geju.md |
| 能不能再占一卦；已经占了好几次，结论不一致怎么办；一卦能不能同时问几件事；用神不现是不是要找伏神；不确定这一卦算不算"明现"；想一次把身命、财、官、子嗣问完 | references/capabilities/fenzhan-duozhan.md | references/capabilities/zhanqian-zhunbei.md、references/capabilities/qu-yongshen.md、references/capabilities/zhanci-yingbi.md |
| 卦好像说的不是我问的事；问 A 事但卦里某六亲强烈异常；问近事却断出很远的意象；同一个卦换个事类读反而说得通 | references/capabilities/zhanci-yingbi.md | references/capabilities/qu-yongshen.md、references/capabilities/pimiu-fanmoshi.md、references/capabilities/fenzhan-duozhan.md |
| 断卦中途自查有没有踩进被删掉的古法陷阱；引了一条古诀，问这条可信吗；拿青龙白虎或星煞直接断吉凶；问随鬼入墓 / 卦身 / 避空 / 冲散该怎么看；想给本书的规则做可信度分级 | references/capabilities/pimiu-fanmoshi.md | references/capabilities/sishen-wangshuai.md、references/capabilities/fenzhan-duozhan.md、references/capabilities/zhanci-yingbi.md |

**非能力类查询**：
- 书名/作者/章节/整书概览 → references/overview.md
- 术语解释 → references/glossary.md
- 决策规则速查（不需要原文依据时） → references/cheatsheet.md
- 完整意图与关键词索引（本表未覆盖的意图先查这里） → references/capability-index.md

## 加载规则

- 每次任务先读本文件，再按路由表加载 **1** 张能力卡；任务明确跨域时最多加载 2 张。
- 概览/书名类问题不加载能力卡，用「核心原则」与 overview.md 回答。
- 路由表与 capability-index.md 都无法命中的意图，明确告知超出本书范围，不要硬套。

## 边界与判停

- **先过红线扫描（anquan-bianjie）**：涉及医疗诊断/用药/手术预后、法律后果、金融投资决策、人身安全与刑事风险 → 停止断卦，说明本书方法不能作为决策依据，并引导至医生/律师/持牌顾问/警方。**注意：这类请求会触发本 Skill，但触发后必须拒绝并引导，不是不触发。**
- **代占拦截**：用户替不在场的人摇卦 → 触发后拒绝代占（「我事不可命人」），建议由本人动念自占（→zhanqian-zhunbei）。
- **一卦多问拦截**：用户想在一次卦里问完多个诉求 → 触发后要求拆成一事一卦，列出拆分后的各个是非题（→zhanqian-zhunbei / fenzhan-duozhan）。
- 用神无法确定、或问目既含"能否"又含"何时"未拆分 → 停止起卦，先回到提问规范（zhanqian-zhunbei）。
- 卦已明现而用户仍想再占 → 停止，说明"不可再渎"是硬边界，不得一直占到满意为止。
- 连占三卦仍结论冲突 → 停止摇卦，回到提问层重做（多半是问目不清），而不是继续占（→fenzhan-duozhan）。
- 嫌疑"占此应彼"但未同时满足三条判据 → 判定为误读，按原问读或再占，不得改读为别的事。
- **多卡命中时的 tie-break（取第一张，不并行开跑）**：anquan-bianjie → zhanqian-zhunbei → qu-yongshen → daxiang-geju → sishen-wangshuai → yingqi-tuiduan → fenzhan-duozhan → zhanci-yingbi。pimiu-fanmoshi 可随时插入自查。
- **全流程请求**：按 zhanqian-zhunbei → qigua-zhuanggua → qu-yongshen → daxiang-geju → sishen-wangshuai → yingqi-tuiduan 逐步推进，每完成一步先向用户确认再进下一步，不要一次性输出整条流水线的结论。
- 任何断语都要带不确定性限定，不得给出精确的医疗预后时间、法律裁决日期或行情点位。
- 若用户表现出**现实危机信号**（自伤倾向、正被侵害、急性重症），停止一切占卜环节，直接引导至急救 / 报警 / 心理危机干预渠道。
