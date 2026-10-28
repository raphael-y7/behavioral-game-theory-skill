# verified.md — 阶段 1.5 通过三重验证的单元总索引

> 判定明细的权威记录在四个验证报告中（本文件是索引与统计）：
> - `.cangjie/verify_A_frameworks.md`（f101–f330）
> - `.cangjie/verify_B_frameworks.md`（f401–f640）
> - `.cangjie/verify_A_principles.md`（p101–p342）
> - `.cangjie/verify_B_principles.md`（p401–p648）
> - `.cangjie/verify_A_misc.md`（案例/反例/术语三池，全部 reference）

## 统计总览

| 池 | 候选数 | verified | reference | needs_review | rejected |
|---|---|---|---|---|---|
| frameworks | 203 | 189 | 7 | 1 | 6 |
| principles | 329 | 315 | 3 | 3 | 8 |
| cases | 44 | 0 | 44 | 0 | 0 |
| counter-examples | 35 | 0 | 35 | 0 | 0 |
| glossary | 48 | 0 | 48 | 0 | 0 |
| **合计** | **659** | **504** | **137** | **4** | **14** |

（注：候选总数 659 = 框架 203 + 原则 329 + 案例 44 + 反例 35 + 术语 48）

## verified 清单（按池与组）

- **frameworks（189）**：f101–f107, f109–f115, f117–f136（A组95条，f108/f116/f330/f103/f305 除外）；f401–f428, f501–f532, f534–f535, f601–f625, f628, f632, f634–f640（B组94条，f506/f533/f534/f633/f626/f627/f629/f630/f631 除外）。完整 YAML 与 V2 演练见 verify_A/B_frameworks.md。
- **principles（315）**：p101–p342 中除 p110/p302（reference）、p214（needs_review）、p103/p111/p118/p202/p207/p223/p224（rejected）外的 176 条；p401–p648 中除 p409（reference）、p403/p408（needs_review）、p642（rejected）外的 139 条。演练数值见 verify_A/B_principles.md。
- **参考池**：cases 44 条（c01–c44）、counter-examples 35 条（x01–x35）、glossary 48 条——全部 reference（方法论规定 case/counter-example/term 默认去向，不算淘汰），个别含可执行内核者其内核由 frameworks/principles 池的正典条目承载。

## 验证中裁定并修正的重要问题（详见各 verify 文件）

1. 原书排印疑误裁定成立 4 处：δ/(1−δ)→δ/(1+δ)（p245/f228，47% 数值印证）、罢工条件句漏"不"（p253）、RD 公理第二条件 pπg<πb（p254）、菜谱泊松式缺负号 e^{−τ}（p644，e^{+τ}>1 不可能是概率）。
2. 候选侧笔误修正 2 处：无交易区 12.5→25（p255，投标函数推导）、f512 指定跟随率 51%→48%。
3. 源侧数值出入登记 4 处（不阻塞，引用时以表格为准）：p250 γ=0.68 vs 算得 0.635、p608 漏 /3、p512 期数数字正文与表7—13 不一致、p422/p429/p439 表值未逐格复核。
4. 案例池引文错误 5 处（E1–E5，详见 verify_A_misc.md）：c38/cx15 把 Chaudhuri 实验引文错挂 Cooper 名下、c29 "主持人"应为"被淘汰选手"、c04 译名补全、c03 中档奖金待核。**这些条目在进入 Bundle 前须按修正建议改写。**

## 正典化（canonical）映射（去重结果）

f108→f306；f626→f105+f106+f127；f627→f207+f204+f206；f629→f302+f306+f320；f630→f423+f427（增量"支付学习/登山法"并入 f427）；f631→f502+f510；p103→p304；p111→p301；p118→p209；p202→p114；p207→p322；p223→p119；p224→p124；p642→p511（判据补充 p502）。

> 阶段 1.6 按能力（非按原始单元）晋级：约 504 个 verified 单元将合并为约 14 个能力单元后再过晋级门。
