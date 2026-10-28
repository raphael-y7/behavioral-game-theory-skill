<h1 align="center">行为博弈 Skill</h1>

<p align="center">中文 | <a href="README.en.md">English</a></p>

一套可直接使用的 AI skill 工具包——把科林·凯莫勒《行为博弈：对策略互动的实验研究》里的实验结论与可计算模型，蒸馏成 10 张可单独触发、也可组合调用的能力卡。

它不是原书摘要，也不是读后感，而是把书中可复用的方法论拆成可触发、可执行、可测试的 skill 模块。

## 这套 skills 能解决什么问题

- 面对一个策略互动问题（对手会怎么反应、该套哪个博弈论框架），手上只有"要理性看待"这类空话，不知道从哪个模型切入
- 想预判"第一次遇到的新规则 / 新标的"里人群的第一反应落在哪里，却只能笼统说一句"非理性"
- 反复互动中对手是在跟风还是在计算、适应有多快，缺一套可估参数、可复算的建模口径
- 几个标准 / 平台 / 叙事都有人支持，判断不了会收敛到哪一边，也分不清聚点、风险占优、路径依赖各自解释什么
- 看到回购、增发、股利、担保这类公告，判断不了它是"昂贵信号"还是虚张声势；面对多年的信用记录，也说不出它到底值多少
- 谈判、并购对价、供应商赊账额度只能凭感觉报数，缺一个能给出区间的判据；读到"实验表明……"的行为结论，也不知道能不能采信、能不能外推

## 蒸馏了什么

10 张能力卡，按"先选型、再修正假设、最后落到具体场景"的顺序组织：

- **总路由与选型**：`model-recipe-selection`（模型选型菜谱：按问题类型取模型与默认参数，是全书的总入口）
- **偏好修正**：`social-preference-measure`（社会性偏好测度与计算：独裁者 / 最后通牒 / 信任三博弈读数 + FS 规避不均等函数）
- **推理与学习**：`cognitive-hierarchy-first-round`（认知等级与首轮行为预测：CH 泊松分层 + QRE）、`ewa-learning-model`（EWA 学习建模：φ / δ / κ 更新与机制辨识三判据）
- **均衡、信号与声誉**：`coordination-selection`（协调博弈与均衡筛选：三分类 + 聚点 + 风险占优度量）、`signal-reading`（信号传递判读：可信性双属性 + 精炼阶梯，含企业融资信号）、`reputation-mechanism`（声誉机制与承诺可信度：类型先验与阈值路径）
- **市场结构与谈判**：`market-entry-dynamics`（市场进入与拥挤判断：均衡进入人数 + 方差缩小与基准组群忽视）、`bargaining-prediction`（讨价还价结果预测：外部选择三分法与"均分 ↔ 精炼"区间）
- **方法论审计**：`experiment-methodology-audit`（行为实验研究审计：五因素体检与归因排障）

## 两种打包模式：single 与 pack

同一套 10 张能力卡，按两种粒度各编译了一次。两者内容完全相同，区别只在"agent 能看到几个入口"。

| | single（单一入口） | pack（compact pack，多入口） |
|---|---|---|
| 可发现入口 | **1 个**：`behavioral-game-theory-skill` | **8 个**：1 个来源路由入口 + 7 个已晋级独立 skill |
| 10 张能力卡放在哪 | 全部在入口的 `references/capabilities/` 里，由入口按路由表按需加载 1–2 张 | 7 张卡各自独立成 skill；其余 3 张仍在 router 的 `references/` 里 |
| 触发方式 | 只有入口的 description 参与匹配，进入后靠路由表分流 | 7 个能力可被 description 直接命中，少一跳 |
| 升级维护 | 替换 1 个目录 | 替换 8 个目录 |

pack 里被晋级为独立 skill 的 7 张卡：

- `model-recipe-selection` — 模型选型菜谱（总路由）
- `social-preference-measure` — 社会性偏好测度与计算（FS/互惠）
- `cognitive-hierarchy-first-round` — 认知等级与首轮行为预测（CH/QRE）
- `ewa-learning-model` — EWA 学习建模（含机制辨识）
- `coordination-selection` — 协调博弈与均衡筛选（聚点/风险占优）
- `signal-reading` — 信号传递判读（含企业融资信号）
- `market-entry-dynamics` — 市场进入与拥挤判断

另外 3 张（`reputation-mechanism`、`bargaining-prediction`、`experiment-methodology-audit`）在 pack 里仍经 router 入口访问。

### 该装哪一种

按你的工作方式选，**只装一种**：

| 你的工作方式 | 推荐 | 原因 |
|---|---|---|
| 用 DSH / Codex / Claude Code 等有 skills 目录，希望列表干净 | single | 只占 1 个入口，能力一张不少 |
| 日常问题高度集中在"该用哪个模型 / 大家会想几步 / 谁在跟风 / 哪个标准会赢 / 公告能不能信 / 赛道挤不挤" | pack | 这 6 类正是被晋级的独立 skill，能直接命中 |
| 要分发给多个 agent 或团队，各自按需取用 | pack | 可以只装其中几个独立 skill，不必整包 |
| 只想装一次、不想维护多个目录 | single | 升级时只替换 1 个目录 |

> 两版由同一个 Bundle 编译，能力内容一致。**同时安装会重复触发**，请只装一种。

## 效果示例

### 示例 1：新股上市首日，散户报价会停在哪一步

**用户问题**

"新股明天上市，首日散户的报价大概会集中在什么位置？大家会想到第几层？"

**skill 如何判断**

- 先过 `model-recipe-selection`：这是"第一次互动 / 新环境下人们怎么选"，落分支 B（首轮行为），默认参数表随输出一并列出
- 进 `cognitive-hierarchy-first-round`：0 级对可选报价均匀随机；k 级只对"0 到 k−1 级的标准化分布"做一步最优反应；各级人数按泊松式 f(k|τ)=e^(−τ)τ^k/k! 分层，τ 默认 1.5
- 走输入契约：需要报价档位（策略集合）与每种结果下的盈亏（支付矩阵）。缺支付矩阵时先问，不得臆造数值
- 判停：如果问题变成"上市之后连着几天怎么演变"，就停止并转 `ewa-learning-model`——那张卡管第 2 期以后，这张卡只管第一期

**最终回答示例**

> 这类问题不是猜散户情绪，而是问"人群的推理停在第几步"。按 CH，0 级等于在报价档位里乱选；1 级假设别人都是 0 级、自己往前一步；2 级再往前一步。泊松参数 τ 取默认 1.5 时，0 / 1 / 2 级各占约 22.3% / 33.5% / 25.1%，三级合计约 81%——八成以上的报价落在"只想到一两步"的区间里。这个落点在书里反复被验证过：选美比赛的首轮中位数就停在第 2 步（约 22），作者亲历的一场全是博弈论老手的拍卖也只到两步。
>
> 但有两件事必须说清楚。第一，τ=1.5 是作者自己标注的"零卡路里菜谱"，是方便起步的约定值，不是实证定律；书里没有给过新股首日这个场景的任何实测参数。第二，书里也没有"报价该集中在哪个价位"的公式——CH 算的是各级最优反应，而最优反应取决于你给的报价档位和盈亏结构。把这两组数据补上，我才能算出具体的加权落点；只有现在这些信息，我只能给推理深度的分布，不给价位。

### 示例 2：大额回购公告，有多少信息含量

**用户问题**

"这家公司刚公告大额回购，管理层说股价被低估。这个公告到底说明了什么？能信吗？"

**skill 如何判断**

- 先过 `model-recipe-selection`：问题的核心是"一方的行为传递了什么私人信息"，走 `signal-reading`——不是声誉卡（那是跨期类型概率的积累与消耗），也不是协调卡（那里的宣告是协调工具）
- 双属性初检：信号必须对某些类型"承受得起"、对另一些"过于昂贵"。两属性都不成立，这个信号就是空转，直接判停
- 均衡类型识别：按成本差异判断分离 / 混同 / 半分离
- 精炼筛选：从弱到强过精炼阶梯，预测落在"弱精炼可通过的均衡集合"里——书里直觉标准的命中率是 46%–63%，神性以上大幅衰减，所以强精炼只作参考

**最终回答示例**

> 判断这个回购算不算信号，只需要回答一个问题：它对"真的被低估"的公司和"其实没被低估"的公司，代价一样吗？如果回购要真金白银、现金紧张的公司做不起，那它对高价值类型"承受得起"、对低价值类型"过于昂贵"，双属性成立，公告才有信息量。如果公司可以只宣布不执行，或者用极低成本完成，这两个属性都不成立——按卡里的判停点，它就是空转，不该被当成信号。
>
> 书里最直接的证据来自 Myers-Majluf 式的融资实验：投资者分不清好坏公司时，增发会把价值让给新股东，好公司宁可搁浅正 NPV 的项目，于是出现"坏钱驱逐好项目"的混同陷阱。那个实验的判别式本体（好类型阈值 0.80、混同阈值 0.60、分界 0.68）在验证记录里逐符号复核成立；但半分离的比例式在书里排印有误（已登记为待回查），引用具体比例前要回查原文。
>
> 还有两点边界：书里的证据是学生被试、小额现金、2–3 类型的小博弈，公司金融场景有监管、披露规则等多重制度缓冲，信号成本结构要按实际重估；书里也从未给过"回购金额达到多少才算强信号"这类阈值，这个数只能你自己按公司现金流定，并写进预案。

## 这些 skill 是怎么生成出来的

这套 skill 使用 **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** 的 RIA-TV++ 流水线生成，整个流程分六个阶段：

1. **整书理解（Adler 分析）**——用 Mortimer Adler 的分析阅读法，对全书做结构、解释、批判、应用四步拆解
2. **并行提取**——同时派多个专项提取器（框架、原则、案例、反例、术语），从原文中提取候选方法论单元
3. **三重验证筛选**——每个候选必须通过三项检验：书内至少有 2 处独立佐证（跨域）、能回答书中未明说的新问题（预测力）、不是常识（独特性）
4. **RIA++ 构造**——按 R（原文引用）/ I（用自己的话重写）/ A1（书中案例）/ A2（未来触发场景）/ E（可执行步骤）/ B（边界与盲点）六个维度结构化
5. **Zettelkasten 链接**——找出能力卡之间的依赖、对比、组合关系，生成能力索引与路由表
6. **触发与输出测试**——为入口设计触发盲测（含诱饵题：该触发时要触发，不该触发时要沉默）与代表任务的执行断言，未通过的项回炉重做

本书是方法论专著，不是投资书，这一点也影响了蒸馏：卡片的 A2 触发场景按"股票市场是最大、最持续的多人策略互动"来写，但每张卡的 B 段都保留了实验边界——学生被试、小额现金、1990 年代数据，外推到真金白银的大额决策前必须重估参数。

## 测试与验证

本仓库把生成过程的测试材料一起发布：`evals/test-prompts.json` 是包级触发用例（8 个可发现入口 + 12 条 prompt，含负例与跨技能混淆诱饵），`evals/test-results.md` 是逐项记录的执行报告，包含发现的问题与局限声明，不是只留通过记录。

- **触发盲测**：12 / 12 通过，诱饵误触发 0。盲测代理只拿到 8 个入口的 name + description 与 12 条 prompt，不给预期答案；其中 4 条负例（纯信息查询、无策略互动的日常计划等）与 2 条跨技能混淆诱饵（协调 vs 信号、进入 vs 协调）均判对
- **router 可达性**：声誉、谈判、研究审计三张未晋级的卡，盲测均被正确路由，未出现"入口命中但落不到卡"的情况
- **执行断言**：10 组代表任务、23 条机械断言全部通过（FS 效用与拒绝临界、CH 泊松分层与 QRE 概率、EWA 更新与退化检验、风险占优度量、进入均衡概率、信号分离判定、声誉阈值路径、deal-me-out 份额），容差 1e-3，可独立复算
- **已知局限**：本轮**没有跑 without_skill 基线**，因此无法声明"有 skill 优于无 skill"；能力价值目前以任务覆盖映射与断言正确性为据。这一点写在测试报告里，不做粉饰

## 仓库结构

```text
behavioral-game-theory-skill/
├── README.md                      ← 你正在看的
├── README.en.md                   ← English version
├── LICENSE                        ← MIT
├── BOOK_OVERVIEW.md               ← 整书理解（Adler 四步拆解，阶段 0 产出）
├── verified.md                    ← 三重验证的单元索引与统计
├── single/                        ← 单一入口模式
│   └── behavioral-game-theory-skill/
│       ├── SKILL.md               ← 入口：触发条件 + 路由表 + 加载规则
│       ├── BUILD_MANIFEST.json    ← 编译清单与文件哈希
│       └── references/
│           ├── overview.md        ← 整书概览
│           ├── capability-index.md  ← 完整意图与关键词索引
│           ├── cheatsheet.md      ← 决策规则速查
│           ├── glossary.md        ← 术语表
│           └── capabilities/      ← 10 张能力卡
├── pack/                          ← 多入口模式（compact pack）
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json
│   ├── behavioral-game-router/
│   │   ├── SKILL.md               ← 来源路由入口
│   │   └── references/            ← 10 张卡 + 索引，供 router 内部调用
│   ├── model-recipe-selection/
│   │   └── SKILL.md
│   ├── social-preference-measure/
│   │   └── SKILL.md
│   ├── cognitive-hierarchy-first-round/
│   │   └── SKILL.md
│   ├── ewa-learning-model/
│   │   └── SKILL.md
│   ├── coordination-selection/
│   │   └── SKILL.md
│   ├── signal-reading/
│   │   └── SKILL.md
│   └── market-entry-dynamics/
│       └── SKILL.md
└── evals/                          ← 触发用例与执行记录
    ├── test-prompts.json          ← 8 个入口 + 12 条包级用例
    └── test-results.md            ← 逐项结果与局限声明
```

## 如何使用

先把仓库克隆下来：

```bash
git clone https://github.com/raphael-y7/behavioral-game-theory-skill.git
```

### 装 single（推荐先试这个）

```bash
# macOS / Linux
cp -r behavioral-game-theory-skill/single/behavioral-game-theory-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\behavioral-game-theory-skill\single\behavioral-game-theory-skill "$env:USERPROFILE\.agents\skills\"
```

### 装 pack

只复制含 `SKILL.md` 的目录，不要把 `pack/` 下的两个 json 一起拷进 skills 目录：

```bash
# macOS / Linux
cd behavioral-game-theory-skill/pack
cp -r behavioral-game-router \
      model-recipe-selection \
      social-preference-measure \
      cognitive-hierarchy-first-round \
      ewa-learning-model \
      coordination-selection \
      signal-reading \
      market-entry-dynamics ~/.agents/skills/
```

```powershell
# Windows
$pack = ".\behavioral-game-theory-skill\pack"
$dest = "$env:USERPROFILE\.agents\skills"
@('behavioral-game-router','model-recipe-selection','social-preference-measure','cognitive-hierarchy-first-round','ewa-learning-model','coordination-selection','signal-reading','market-entry-dynamics') |
  ForEach-Object { Copy-Item -Recurse -LiteralPath (Join-Path $pack $_) -Destination $dest }
```

> `~/.agents/skills` 是 DSH 的 skill 目录；用别的 agent 时换成它自己的 skills 目录即可（例如 Claude Code 是 `~/.claude/skills`）。

### 怎么确认装好了

装完问一句"这家公司公告大额回购，这个信号的信息含量怎么判"，看 agent 是否直接进入 `signal-reading` 的双属性初检与均衡类型识别，而不是给你一段泛泛的"回购是利好"。装的是 single 时，它会先读入口再按路由表进能力卡；装的是 pack 时，对应能力会被直接命中。

## 来源

- 《行为博弈》科林·凯莫勒 著
- 全书蒸馏，共产出 10 张能力卡

## 声明

本仓库只发布蒸馏后的 skill、索引与规则速查材料，不包含原书 PDF、EPUB、OCR 文件、截图或全书转写稿。能力卡中出现的原文引用仅用于标注方法论出处和保持可审计性。

书中所有数字判据（FS 的 α/β、CH 的泊松 τ、fEWA 的 λ、进入博弈的容量与阈值、声誉的 τ^n 路径等）都是实验案例与经验归纳，原书未提供可直接套用的统计背书，使用时需按场景自行重估并声明所用口径。本仓库内容不构成投资建议。

## License

[MIT](https://opensource.org/licenses/MIT)
