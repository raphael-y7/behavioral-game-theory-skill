---
name: behavioral-game-router
description: |
  行为博弈论能力路由入口：按问题类型（社会性偏好/首轮行为/学习演化/均衡筛选/信号/声誉/进入/谈判/研究审计）定位到对应能力卡执行；未晋级能力（声誉机制、讨价还价预测、研究审计）经此入口访问。
metadata:
  cangjie.generated-by: cangjie-tools v2.5.0
  cangjie.variant: router
  cangjie.bundle-id: bundle.behavioral-game-theory
  cangjie.capability-count: 10
  cangjie.entrypoint-count: 8
---
# 行为博弈：对策略互动的实验研究 — 来源路由入口（compact pack）

## 触发与不触发

**适用**：与本书能力域相关的咨询与任务（见下方路由表的意图列）。
**不适用**：
- 单人不涉及策略互动的普通决策与心理自助
- 已由长期市场选择充分塑造的稳态价格预测（实验室规律外推边界）
- 纯技术分析、财务报表分析与估值建模（非本书主题）
- 统计审查（样本量、功效、多重比较——原书未覆盖的方法论纪律）

## 核心原则（常驻速览，概览类问题读到这里即可回答）

1. 自利是特例：他人所得真实进入效用函数，可用 FS(α,β) 或互惠模型参数化
2. 人是"一步半的思考者"：首轮行为由泊松认知等级(τ≈1.5)主导，QRE 给理性程度定价
3. 均衡概念对动态零解释力：重复互动的演化用 EWA/fEWA 更新规则建模
4. 多重均衡的筛选有可辨识原则：三分类（匹配/猎鹿/性别战）+ 聚点 + 风险占优度量
5. 信号的价值在成本不对称；弱精炼够用，强精炼在数据面前失灵
6. 修正而非抛弃：保留策略互动框架，替换自利/无限推理/静态均衡三个假设
7. 默认参数是"零卡路里菜谱"（FS α=1/3、CH τ=1.5、fEWA λ=1），换场景必须重估

## 能力路由（先读本表，按意图加载 1 张能力卡）

| 用户意图 | 先读 | 补读/备注 |
|---|---|---|
| 选择行为博弈模型；判断用哪个博弈论框架；策略互动问题建模选型；model selection for strategic interaction | references/capabilities/model-recipe-selection.md | 已晋级为独立 Skill `model-recipe-selection`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 分析公平与互惠行为；计算社会性效用；预测对方是否拒绝要约；评估激励是否被公平感扭曲；fairness reciprocity analysis | references/capabilities/social-preference-measure.md | 已晋级为独立 Skill `social-preference-measure`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 预测首轮行为；估计市场第一反应；判断对手想几步；预测新博弈新规则下的初始选择；level-k reasoning；first-round prediction | references/capabilities/cognitive-hierarchy-first-round.md | 已晋级为独立 Skill `cognitive-hierarchy-first-round`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 建模重复互动中的行为演化；分析学习速度与适应；判断对手在跟风还是在计算；reinforcement learning modeling；EWA | references/capabilities/ewa-learning-model.md | 已晋级为独立 Skill `ewa-learning-model`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 判断哪个均衡标准会胜出；分析共识与题材形成；评估路径依赖与锁定；预判集体行动能否启动；equilibrium selection；focal point | references/capabilities/coordination-selection.md | 已晋级为独立 Skill `coordination-selection`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 解读公司公告的信息含量；判断增发回购股利信号；评估声明可信度；识别虚张声势；signaling；costly signal | references/capabilities/signal-reading.md | 已晋级为独立 Skill `signal-reading`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 判断赛道拥挤度；分析产能扩张与进入潮；评估机会剩余空间；market entry；crowding | references/capabilities/market-entry-dynamics.md | 已晋级为独立 Skill `market-entry-dynamics`（已安装时优先直接使用；本卡仅作原文与背景补充） |
| 评估管理层信用记录价值；判断承诺可信度；分析惩罚制度设计；reputation；track record | references/capabilities/reputation-mechanism.md | references/capabilities/signal-reading.md、references/capabilities/model-recipe-selection.md |
| 预测谈判落点；判断BATNA重要性；设计谈判时序；bargaining prediction；BATNA | references/capabilities/bargaining-prediction.md | references/capabilities/social-preference-measure.md、references/capabilities/model-recipe-selection.md |
| 评估行为研究可信度；审查实验证据；设计小实验验证行为假设；audit behavioral research | references/capabilities/experiment-methodology-audit.md | references/capabilities/model-recipe-selection.md、references/capabilities/social-preference-measure.md |

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

- 问题不含策略互动（对手反应不影响结果）时停止并说明
- 缺少关键结构参数（支付/容量/贴现因子/类型先验）且用户无法提供时，输出定性方向并声明缺口，不得臆造数值
- 需要逐笔投资建议时停止——本技能提供行为分析视角，不构成投资建议
