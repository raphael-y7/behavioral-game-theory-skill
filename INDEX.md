# Skill 地图 — 行为博弈：对策略互动的实验研究

10 张能力卡的总索引：先看哪张、哪张是入口、哪几张可以独立安装、读一张之后该补读哪几张。本文件由 `bundle/verified.yaml` 生成，与其中 `capabilities` 字段一一对应。

## 能力总表

| capability_id | slug | 中文标题 | 重要度 | 去向 |
|---|---|---|---|---|
| `cap.behavioral-game-theory.model-recipe-selection` | `model-recipe-selection` | 模型选型菜谱（行为博弈论总路由） | critical | promoted → 独立 skill |
| `cap.behavioral-game-theory.social-preference-measure` | `social-preference-measure` | 社会性偏好测度与计算（FS/互惠） | high | promoted → 独立 skill |
| `cap.behavioral-game-theory.cognitive-hierarchy-first-round` | `cognitive-hierarchy-first-round` | 认知等级与首轮行为预测（CH/QRE） | high | promoted → 独立 skill |
| `cap.behavioral-game-theory.ewa-learning-model` | `ewa-learning-model` | EWA 学习建模（含机制辨识） | high | promoted → 独立 skill |
| `cap.behavioral-game-theory.coordination-selection` | `coordination-selection` | 协调博弈与均衡筛选（聚点/风险占优） | high | promoted → 独立 skill |
| `cap.behavioral-game-theory.signal-reading` | `signal-reading` | 信号传递判读（含企业融资信号） | high | promoted → 独立 skill |
| `cap.behavioral-game-theory.market-entry-dynamics` | `market-entry-dynamics` | 市场进入与拥挤判断 | high | promoted → 独立 skill |
| `cap.behavioral-game-theory.reputation-mechanism` | `reputation-mechanism` | 声誉机制与承诺可信度 | medium | router → 路由入口 |
| `cap.behavioral-game-theory.bargaining-prediction` | `bargaining-prediction` | 讨价还价结果预测 | medium | router → 路由入口 |
| `cap.behavioral-game-theory.experiment-methodology-audit` | `experiment-methodology-audit` | 行为实验研究审计 | medium | router → 路由入口 |

统计：10 张卡，7 张 promoted（在 pack 里各自成为独立 skill）、3 张 router（只经 `behavioral-game-theory-skill-router` 入口访问）。single 模式不区分去向，10 张卡全部放在入口的 `references/capabilities/` 下。

## 依赖关系

`verified.yaml` 的 `also_read` 字段记录的是"读完这张、还该补读哪几张"。关系有向，指向的是**下一跳**，不是等级高低。

| 能力卡（slug） | also_read（按顺序补读） |
|---|---|
| `model-recipe-selection` | `social-preference-measure`、`cognitive-hierarchy-first-round`、`ewa-learning-model` |
| `social-preference-measure` | `model-recipe-selection`、`bargaining-prediction` |
| `cognitive-hierarchy-first-round` | `model-recipe-selection`、`ewa-learning-model`、`coordination-selection` |
| `ewa-learning-model` | `model-recipe-selection`、`cognitive-hierarchy-first-round`、`signal-reading` |
| `coordination-selection` | `model-recipe-selection`、`market-entry-dynamics`、`cognitive-hierarchy-first-round` |
| `signal-reading` | `model-recipe-selection`、`reputation-mechanism`、`ewa-learning-model` |
| `market-entry-dynamics` | `model-recipe-selection`、`coordination-selection`、`cognitive-hierarchy-first-round` |
| `reputation-mechanism` | `signal-reading`、`model-recipe-selection` |
| `bargaining-prediction` | `social-preference-measure`、`model-recipe-selection` |
| `experiment-methodology-audit` | `model-recipe-selection`、`social-preference-measure` |

读法：

- `model-recipe-selection` 被 9 张卡同时列为补读对象，它是全图的中枢——**选型不确定时先读它**。
- 三组天然相邻、常一起用的配对：`social-preference-measure` ↔ `bargaining-prediction`（公平偏好决定谈判落点）、`signal-reading` ↔ `reputation-mechanism`（单期信号 vs 跨期类型概率）、`coordination-selection` ↔ `market-entry-dynamics`（标准之争 vs 人数对容量）。
- 三张 router 卡（声誉、谈判、审计）没有被任何独立 skill 承载，只能从路由入口进。

## 加载顺序

1. **先读入口 SKILL.md**。single 模式读 `single/behavioral-game-theory-skill/SKILL.md`；pack 模式读 `pack/behavioral-game-theory-skill-router/SKILL.md`（命中已晋级能力时直接读对应的 `pack/<slug>/SKILL.md`，不必先进 router）。
2. **按入口的路由表定位 1 张能力卡**。入口文件里有一张"用户意图 → 先读哪张卡"的表，以及 7 条常驻核心原则——概览类问题读到原则就能回答，不必加载能力卡。
3. **任务确实跨域时，最多再加载 1 张**，按上表的 `also_read` 顺序挑最相关的那张；不要一次铺开三四张。
4. 路由表和 `references/capability-index.md` 都命中不了的意图，明确告知超出本书范围，不要硬套能力卡。
