# Stage 4 压力测试摘要

> 本文件由归档目录（`G:\虚拟机共享文件夹\成果\行为博弈\`）中的阶段 4 材料整理而来；统计数字于 2026-10-29 按仓库现状重新实测改写（脚本遍历全部 `test-prompts.json` 与 `bundle/`），来源为仓库根目录 `test-results.md` 与各 skill 目录下的 `test-prompts.json`，未做估算。

## 测试范围

- **本包 skill 数**：10 张能力单元（`bundle/cards/`）。其中 7 张晋级为独立入口，3 张（bargaining-prediction、experiment-methodology-audit、reputation-mechanism）降为 router 可达卡，故 `pack/` 下共 8 个可发现入口（1 路由 + 7 晋级）；`single/` 下为 1 个单入口包，内含全部 10 张卡的 references 视图。
- **test-prompts 文件数**：**7** 份（仓库内全部 `test-prompts.json`）：
  - `single/behavioral-game-theory-skill/test-prompts.json` —— 入口级套件，12 条用例、8 条入口描述
  - `pack/behavioral-game-theory-skill-router/test-prompts.json` —— 入口级套件的副本，内容相同（12 条）
  - `pack/signal-reading/`、`pack/cognitive-hierarchy-first-round/`、`pack/coordination-selection/`、`pack/market-entry-dynamics/`、`pack/model-recipe-selection/` 下的 `test-prompts.json` —— 分技能套件，各 5 条（命中本 skill 的用例 + 全部负例），用例原文从入口级套件摘录，判定标准未改
  - 未覆盖：`pack/social-preference-measure/` 与 `pack/ewa-learning-model/` 没有对应能力的用例（入口级套件的 12 条里没有命中这两张卡的正面题，归档里也没有分技能文件），故不生成，见下「test-prompts 放置统计」
- **用例总数**：**49** 条（各文件 `test_cases` 长度之和）；去重后唯一用例 **12** 条——分技能套件是入口级套件的子集，不是新增用例，统计总数时会重复计入。
- **按 type 统计**（49 条累计）：

| 类型 | 条数 | 说明 |
|---|---|---|
| `should_trigger` | 14 | 正面触发（信号、首轮推理、协调、进入、声誉/路由可达） |
| `should_not_trigger` | 14 | 纯信息查询、无策略互动的日常任务（诱饵） |
| `should_not_trigger_for_signal` | 7 | 跨技能混淆诱饵：协调 ≠ 信号 |
| `should_not_trigger_for_entry` | 7 | 跨技能混淆诱饵：协调 ≠ 进入 |
| `edge_case` | 7 | 谈判缺参数（输入契约）、研究结论是否可引用（审计边界）、单人决策 + 投资建议红线 |
| `output_case` | 0 | 本包没有该类型的独立用例 |

- **未覆盖类型**：本包没有 `output_case` 类型的独立用例；输出侧的正确性由 `test-results.md` 第二部分那 23 条机械断言承担（按正典公式独立计算，容差 1e-3），不是以 prompt 用例形式记录。

## 结构检查

以下为本次对仓库现文件的实际检查结果：

- **JSON 可解析性**：**7 / 7** 份 `test-prompts.json` 均可被标准 JSON 解析器（`json.load`）读取，无语法错误；入口级两份各 12 条 `test_cases`、8 条 `entries`，分技能五份各 5 条 `test_cases`、8 条 `entries`；每份文件内 `id` 唯一；每条用例都带 `id` / `type` / `prompt` / `expected_behavior` 四个字段（`notes` 为补充说明）。
- **skill frontmatter**：`single/` 与 `pack/` 下共 9 个 `SKILL.md`（1 个 single 入口 + 8 个 pack 入口），全部带 YAML frontmatter，且都含 `name`、`description`、`metadata` 三个键，无缺失；每个 `name` 与所在目录名逐字相同。
- **六段完整性**：`bundle/cards/` 下 10 张能力卡全部具备 R / I / A1 / A2 / E / B 六个段落标题，缺失数为 0。
- **能力覆盖一致性**：10 张卡与入口目录的对应关系与设计一致——3 张 router 专属卡（bargaining-prediction、experiment-methodology-audit、reputation-mechanism）在 `single/` 与 `pack/` 顶层都没有独立目录，只能经 `behavioral-game-theory-skill-router` 访问，这是阶段 1.6 晋级门的既定结论，不是缺文件。
- **test-prompts 放置统计**：归档中递归只找到 1 份 `test-prompts.json`（suite 级，无 `test-prompts__<skill>.json` 形式的分技能文件）。已放置到入口 skill 目录 `single/behavioral-game-theory-skill/test-prompts.json`；再复制一份到 `pack/behavioral-game-theory-skill-router/`（入口级用例，router 是 pack 的入口）；从入口级用例中摘出命中各晋级 skill 的正面题并连同全部负例，补到 5 个晋级 skill 目录。**跳过 2 个**：`social-preference-measure`、`ewa-learning-model`——入口级套件与归档中都没有针对这两张卡的用例，不凭空造题。
- **candidates 目录**：已从归档的 `审计过程/cangjie侧车/candidates/` 取回 5 份文本候选清单（frameworks / principles / cases / counter-examples / glossary，共 659 条候选，多组拼接在同名文件内），未复制任何图片或 PDF。

## 结果

- skills: 10（能力单元）/ 8（pack 可发现入口）/ 1（single 入口包）
- test_json: 7 份文件（`test-prompts.json`），累计 49 条用例、12 条唯一用例
- 通过情况（引自仓库根目录 `test-results.md`，2026-10-28，宿主 ZCode CLI / GLM-5.3-Flash）：
  - 触发盲测：**12 / 12 通过**，诱饵误触发 0。方法为只给盲测代理 8 个入口的 name+description 与 12 条 prompt，不给 type / expected / notes。
  - 路由可达性：3 张 router 卡（声誉、谈判、审计）在盲测中被正确路由，理由指向正确的卡，**通过**。
  - 输出机械断言：10 个能力族各跑一组新输入的代表任务，按正典公式独立计算并机械断言（容差 1e-3），**23 / 23 通过**（例：FS 效用、CH 泊松分层、EWA 一步更新与 δ=0 退化检验、风险占优度量、进入概率 p*≈0.105、deal-me-out 份额）。
  - **未跑的对照**：`without_skill` 基线本轮未运行，因此本包**不能声称"有 skill 优于无 skill"**；能力价值目前以任务映射（coverage-audit 12/12）与断言正确性为据。该局限在原报告中已显式声明，此处照录，不作补写。
  - 已知问题（原报告登记）：p616 Myers-Majluf 盈亏平衡式的 q 值（0.265 vs 记录 0.36）有出入，已停止引用该 q 值，判别式本体复核无误。

## 可接入 darwin-skill 的后续动作

1. **作为回归样本入库**：12 条入口级用例可直接充当 darwin-skill 进化循环的固定回归集——每次改卡后重跑，重点看诱饵题是否仍沉默（4 条负例 + 2 条跨技能混淆），这是最容易在改描述时退化的部分。
2. **补齐 without_skill 基线**：这是本包最该补的一项。做法是同一批 12 条 prompt 在不加载 skill 的裸模型上跑一遍，与当前 12/12 的盲测结果做新旧对比，才能把"触发正确"升级为"触发有增益"。
3. **把 23 条机械断言脚本化**：目前断言是人工复算后记录在 md 里的，建议迁成可执行断言（FS/CH/EWA/进入/deal-me-out 各一组纯函数），让 darwin 每轮自动判定数值是否漂移。
4. **盯住 router 与 model-recipe-selection 的语义重叠**：盲测员已指出两者在"不知道怎么切入"类问法上难区分。现按有意的冗余路由处理（两卡 A2 段互注），若真实使用出现双触发竞争，按 split-on-evidence 流程拆分。
5. **补 `output_case` 类型用例**：把 23 条断言中的代表任务反向写成带 `expected_output` 的 prompt 用例，让测试集覆盖"输出对不对"而不只是"该不该触发"。
6. **补两张卡的分技能用例**：`social-preference-measure` 与 `ewa-learning-model` 目前没有分技能 `test-prompts.json`，需要新写（入口级套件里没有对应题目）。
