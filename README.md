<h1 align="center">行为博弈 Skill</h1>

<p align="center">中文 | <a href="README.en.md">English</a></p>

一套可直接使用的 AI skill 工具包——把科林·凯莫勒《行为博弈：对策略互动的实验研究》中的实验结论与可计算模型，蒸馏成 10 张可单独触发、也可组合调用的能力卡，覆盖社会性偏好、有限推理、学习演化、均衡筛选、信号、声誉、市场进入、讨价还价与研究方法审计。

它不是原书摘要，也不是读后感，而是把书中可复用的方法论拆成可触发、可执行、可测试的 skill 模块。

## 这套 skills 能解决什么问题

- 公司宣布增发、回购、分红或大幅举债，你说不清这是利好还是"坏消息市场里的信息陷阱"，只能跟着当天的涨跌反推
- 新股上市首日、新规则落地、新平台开服，你想判断"大家第一把会怎么选"，手上只有"理性人会选均衡解"这一句没用的结论
- 一条赛道已经挤进十几家，你想知道"现在进还有没有空间"，却只算得清自己的账、算不清别人的进入意愿
- 多个标准、平台或叙事在争，你想预判哪个会胜出、会不会被早期的一次选择锁死，而不是事后解释"路径依赖嘛"
- 并购、大宗交易、薪资谈判的落点，你只能凭"大概对半"给个数，说不出外部选择（BATNA）什么时候该让一方直接出局
- 读到"实验表明……"的研究结论，你不知道该先看方法还是先看结果，也说不清它能不能外推到真金白银的市场

## 蒸馏了什么

10 张能力卡，按"先选型、再算、最后审"的顺序组织，与 `bundle/verified.yaml` 中的 `capabilities` 逐条对应：

- **总路由**：`model-recipe-selection`（模型选型菜谱——作者本人在全书结尾给出的三分支决策框架，附默认参数）
- **偏好与谈判**：`social-preference-measure`（FS 规避不均等公式 + 独裁者/最后通牒/信任三博弈测度）、`bargaining-prediction`（轮流出价 SPE、deal-me-out 判据、均分↔精炼区间）
- **推理与学习**：`cognitive-hierarchy-first-round`（泊松认知等级 CH 与 QRE 的首轮落点预测）、`ewa-learning-model`（EWA/fEWA 更新规则与机制辨识三判据）
- **均衡与进入**：`coordination-selection`（匹配/猎鹿/性别战三分类 + 聚点 + 风险占优度量）、`market-entry-dynamics`（容量-人数均衡与基准组群忽视）
- **信息与声誉**：`signal-reading`（可信性双属性 + 均衡识别 + 精炼阶梯，含 Myers-Majluf 企业融资判别式）、`reputation-mechanism`（类型概率的贝叶斯积累、阈值路径与一次违约的永久失格）
- **元方法**：`experiment-methodology-audit`（五因素体检 + 反直觉结果四步归因）

## 两种打包模式：single 与 pack

同一套 10 张能力卡，按两种粒度各编译了一次。两者内容完全相同，区别只在"agent 能看到几个入口"。

| | single（单一入口） | pack（compact pack，多入口） |
|---|---|---|
| 可发现入口 | **1 个**：`behavioral-game-theory-skill` | **8 个**：1 个来源路由入口 + 7 个已晋级独立 skill |
| 10 张能力卡放在哪 | 全部在入口的 `references/capabilities/` 里，由入口按路由表按需加载 1–2 张 | 7 张卡各自独立成 skill；10 张卡另在 router 的 `references/` 里各留一份原文视图 |
| 触发方式 | 只有入口的 description 参与匹配，进入后靠路由表分流 | 7 个高频能力可被 description 直接命中，少一跳 |
| 升级维护 | 替换 1 个目录 | 替换 8 个目录 |

pack 里被晋级为独立 skill 的 7 张卡：

- `model-recipe-selection` — 模型选型菜谱（总路由）
- `social-preference-measure` — 社会性偏好测度与计算
- `cognitive-hierarchy-first-round` — 认知等级与首轮行为预测
- `ewa-learning-model` — EWA 学习建模
- `coordination-selection` — 协调博弈与均衡筛选
- `signal-reading` — 信号传递判读
- `market-entry-dynamics` — 市场进入与拥挤判断

没被晋级的 3 张（`reputation-mechanism`、`bargaining-prediction`、`experiment-methodology-audit`）只经 router 入口访问——前两张的触发面与相邻卡重叠，单独成 skill 会互相抢触发；第三张是元方法，调用时总伴随某张专业卡一起用。三张都按"最少入口覆盖最多意图"的原则收进路由入口。

### 该装哪一种

按你的工作方式选，**只装一种**：

| 你的工作方式 | 推荐 | 原因 |
|---|---|---|
| 用 DSH / Codex / Claude Code 等有 skills 目录，希望列表干净 | single | 只占 1 个入口，能力一张不少 |
| 日常问题高度集中在"用哪个模型 / 公平怎么算 / 首轮怎么选 / 赛道挤不挤 / 公告信不信" | pack | 这些正是被晋级的独立 skill，能直接命中 |
| 要分发给多个 agent 或团队，各自按需取用 | pack | 可以只装其中几个独立 skill，不必整包 |
| 只想装一次、不想维护多个目录 | single | 升级时只替换 1 个目录 |

> 两版由同一个 Bundle 编译，能力内容一致。**同时安装会重复触发**，请只装一种。

## 效果示例

### 示例 1：增发公告发布当天跌了 4%，是利空还是错杀

**用户问题**

"公司刚宣布定向增发，股价当天跌了 4%。这是利空，还是市场错杀？"

**skill 如何判断**

- 先分流：这是一次性公告的信息含量，归 `signal-reading`；不归 `reputation-mechanism`（后者处理跨期类型概率的积累与消耗）
- 双属性初检：这个信号对好公司"承受得起"、对差公司"过于昂贵"吗？增发的成本是"把项目价值让给新股东"，成本随公司类型反向变动——若两类公司成本无差异，这个信号就是空转，第一步就判停
- 均衡类型识别：按 Myers-Majluf 判别式算混同均衡下的投资者盈亏平衡与好公司是否放弃项目，判断当前落在分离、混同还是半分离
- 精炼筛选：只走到弱精炼（直觉标准），不拿"神性"这类强精炼准则当预测依据

**最终回答示例**

> 先别把"跌 4%"当成结论。这个公告能不能传递信息，取决于成本结构：如果好公司和差公司发这个增发的代价差不多，它就不是信号，跌多少都读不出类型。假设代价确实不对称，接下来要判它落在哪个均衡——在混同均衡里，"好公司增发"本身就是坏消息，因为发股筹资等于把好项目的价值让给新股东，好公司宁可搁浅项目；这是结构结果，不是市场非理性。所以别急着喊错杀，先看两件事：这笔钱的用途是不是只有好公司才敢投的项目（成本差异越大，分离越可能），以及有没有更便宜的信号（举债、回购）被同时使用。精炼层面只用到直觉标准就够——书里的实验数据显示，越强的精炼准则（神性及以后）对"哪个均衡会出现"的预测力反而衰减。另外提醒一句：这些证据来自小额实验室融资实验，量级和披露规则上不能直接平移到 A 股。

### 示例 2：赛道已经进来 12 家，现在进还有空间吗

**用户问题**

"这条赛道今年已经进来 12 家，还有 3 家在谈融资。我们现在进还有空间吗？"

**skill 如何判断**

- 归 `market-entry-dynamics`：关键变量是"人数 vs 容量"，不是"哪个均衡"（那是 `coordination-selection`）
- 输入契约：潜在进入者数 n、市场容量 c、单位份额收益 r、外部选择 k。缺 c 或 k 就先问——没有容量和外部选择，根本不构成进入博弈（判停点）
- 算均衡基准：用总收益 k+r(c−m)（m=Σe_j）解出均衡进入概率与期望进入人数
- 两条行为修正：进入人数的实际方差远小于混合均衡预测（人们像在"轮流"而不是各掷各的骰子）；自我选择情境下出现基准组群忽视——人人自认技高一筹，书中的进入博弈+技能实验里，70% 的期数群体整体亏损，个体却仍持续进入

**最终回答示例**

> 先把账算出来再谈空间：把容量 c、份额收益 r、外部选择 k 填进 k+r(c−m)，解出的均衡进入概率和期望人数才是基准线。你现在看到"12 家已进、3 家在谈"，要判断的是这 15 家相对于 c 处在什么位置。然后加两条系统性偏离：第一，真实进入人数的波动比模型小得多，人群会错开而不是同挤，所以别按"最坏情况人人同时进"来做预案；第二，如果这是个筛过人的机会（有门槛、有资质、有品牌背书），基准组群忽视会让拥挤比理性预测更严重——书里的实验里，这类组群七成期数整体亏损，但没人退出。结论要写准：是"边际进入者整体亏损"，不是"行业无利可图"——成本结构更低的玩家照样赚钱。最后看修复条件：如果每期亏损可观察，后续进入会自我修正；不可观察，拥挤会拖得更久。

## 这些 skill 是怎么生成出来的

这套 skill 使用 **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** 的 RIA-TV++ 流水线生成，整个流程分六个阶段：

1. **整书理解（Adler 分析）**——用 Mortimer Adler 的分析阅读法，对全书做结构、解释、批判、应用四步拆解，产出 `BOOK_OVERVIEW.md` 与 12 项读者任务清单
2. **并行提取**——同时派多个专项提取器（框架、原则、案例、反例、术语），从原文中提取候选方法论单元，本书共得 659 条候选
3. **三重验证筛选**——每个候选必须通过三项检验：书内至少有 2 处独立佐证（跨域）、能回答书中未明说的新问题（预测力）、不是常识（独特性）。659 条中 504 条通过，并同步裁定原书排印疑误与引文错挂
4. **RIA++ 构造**——按 R（原文引用）/ I（用自己的话重写）/ A1（书中案例）/ A2（未来触发场景）/ E（可执行步骤）/ B（边界与盲点）六个维度结构化
5. **Zettelkasten 链接**——找出能力卡之间的依赖、对比、组合关系，生成能力索引与路由表，并把 504 条 verified 单元合并为 10 个能力单元
6. **触发与输出测试**——为每张卡设计触发盲测题（含诱饵题：该触发时要触发，不该触发时要沉默）与输出评测场景，未通过的卡回炉重做，回炉后再做回归验证

其中"晋级"发生在阶段 5 之后：10 张卡里 7 张按五条独立判据（独立意图、独立契约、独立执行、独立复用、独立评测）晋级为独立 skill；另外 3 张按"最少入口覆盖最多意图"的原则降为 router 卡——两张因触发面与相邻卡重叠，一张因是元方法、总伴随专业卡调用。

## 测试与验证

本仓库连生成过程的测试材料一起发布：`test-results.md` 是逐项评分结果——包含发现的问题与局限声明，不是只留通过记录；触发与边界用例随 skill 一起分发，入口级套件在 `single/behavioral-game-theory-skill/test-prompts.json`，pack 侧见 `pack/behavioral-game-theory-skill-router/test-prompts.json` 与各晋级 skill 目录下的同名文件。

- **触发盲测**：只给盲测代理 8 个入口的 name+description 与 12 条 prompt，不给预期答案；结果 12 / 12 通过，诱饵误触发 0（其中 4 条负例、2 条"协调 ≠ 信号""协调 ≠ 进入"的跨技能混淆诱饵）
- **可达性**：3 张 router 卡（声誉、谈判、审计）在盲测中被正确路由，理由也指向正确的卡，没有失联
- **输出评测**：10 个能力族各执行一组新输入的代表任务，按正典公式独立计算并机械断言（容差 1e-3），23 / 23 通过——例如 FS 效用、CH 泊松分层、EWA 一步更新与 δ=0 退化检验、风险占优度量、进入概率 p*≈0.105、deal-me-out 份额
- **已知局限**：本轮**未跑** without_skill 基线对照，因此不能声称"有 skill 优于无 skill"；能力价值目前以任务映射与断言正确性为据，基线对照留待后续补齐。这一点写在 `test-results.md` 里，没有隐去

## 仓库结构

```text
behavioral-game-theory-skill/
├── README.md              ← 你正在看的
├── README.en.md           ← English version
├── LICENSE                ← MIT
├── BOOK_OVERVIEW.md       ← 阶段 0 产出：全书 Adler 分析
├── DIGEST.md              ← 阶段 5 产出：面向读者的整书精华长文
├── INDEX.md               ← 阶段 3 产出：skill 总览 + 依赖关系
├── verified.md            ← 通过三重验证的 504 个单元
├── TEST_SUMMARY.md        ← 阶段 4 产出：压力测试摘要
├── CANGJIE_ADAPTATION.md  ← 仓颉适配说明
├── GITHUB_REPO.md         ← 仓库元数据
├── test-results.md        ← 测试结果记录
├── candidates/            ← 阶段 1 产出：原始候选池
│   ├── frameworks.md      ← 框架与方法候选
│   ├── principles.md      ← 原则 / 规则 / 计算候选
│   ├── cases.md           ← 书中案例候选
│   ├── counter-examples.md← 反例与边界候选
│   └── glossary.md        ← 术语候选
├── rejected/              ← 阶段 1.5 产出：被淘汰的单元 + 原因
├── bundle/                ← 编译事实源
│   ├── verified.yaml      ← 能力元数据、判据与去向
│   ├── cards/             ← 能力卡源文件（六段结构）
│   └── book/              ← overview.md + glossary.md
├── single/                ← single 模式（1 个入口 + 全部能力卡）
│   └── behavioral-game-theory-skill/SKILL.md  ← 入口：触发 + 路由表 + 加载规则
└── pack/                  ← pack 模式（1 个路由入口 + 7 个晋级 skill）
    └── */SKILL.md         ← 8 个 skill，其中 6 个附 test-prompts.json
```

## 如何使用

把仓库克隆到本地（下面的 `<your-account>` 换成实际账号）：

```bash
git clone https://github.com/<your-account>/behavioral-game-theory-skill.git
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
cp -r behavioral-game-theory-skill-router \
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
@('behavioral-game-theory-skill-router','model-recipe-selection','social-preference-measure','cognitive-hierarchy-first-round','ewa-learning-model','coordination-selection','signal-reading','market-entry-dynamics') |
  ForEach-Object { Copy-Item -Recurse -LiteralPath (Join-Path $pack $_) -Destination $dest }
```

> `~/.agents/skills` 是 DSH 的 skill 目录；用别的 agent 时换成它自己的 skills 目录即可（例如 Claude Code 是 `~/.claude/skills`）。

### 怎么确认装好了

装完问一句"这条赛道已经进来十几家，现在进还有没有空间"，看 agent 是否直接进入进入博弈的核算（先要容量 c 与外部选择 k，再算均衡进入人数），而不是给你一段泛泛的行业分析。装的是 single 时，它会先读入口再按路由表进能力卡；装的是 pack 时，对应能力会被直接命中。

## 来源

- 《行为博弈：对策略互动的实验研究》科林·凯莫勒（Colin F. Camerer）著
- 全书蒸馏为 10 张能力卡，其中 7 张晋级为独立 skill

## 声明

本仓库只发布蒸馏后的 skill、索引与规则速查材料，不包含原书 PDF、EPUB、OCR 文件、截图或全书转写稿。能力卡中出现的原文引用仅用于标注方法论出处和保持可审计性。

书中所有数字判据（默认参数 α=1/3、τ=1.5、λ=1，拒绝率与进入概率等经验锚点）都来自实验室实验与作者归纳，原书未提供跨场景的统计回测背书；作者本人也把默认参数称为"零卡路里菜谱"。换场景使用必须重新估计并声明所用口径，本仓库内容不构成投资建议。

## License

[MIT](./LICENSE)
