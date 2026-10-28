<h1 align="center">Behavioral Game Theory Skill</h1>

<p align="center"><a href="README.md">中文</a> | English</p>

An AI skill pack for immediate use — it distills the experimental findings and computable models in Colin F. Camerer's *Behavioral Game Theory: Experiments in Strategic Interaction* into 10 capability cards that can be triggered individually or combined.

It is not a book summary, nor a reading response — it breaks the reusable methodology in the book into skill modules that can be triggered, executed and tested.

## What these skills solve

- You face a strategic-interaction problem (how will the counterparty react, which game-theory frame applies) and all you have is "stay rational" — no idea which model to start from
- You want to predict where the first reaction lands in a brand-new game, rule set or listing, but can only say "people are irrational"
- You cannot tell whether a counterparty is following the crowd or actually calculating, nor how fast they adapt, because you lack a model with estimable, recomputable parameters
- Several standards, platforms or narratives all have backers and you cannot judge which one converges, nor which of focal point, risk dominance and path dependence explains what
- You see a buyback, secondary offering, dividend or guarantee announcement and cannot tell whether it is a costly signal or cheap talk; you see a years-long credit record and cannot say what it is worth
- Deal pricing, merger consideration and supplier credit limits are quoted by gut feel with no interval to anchor on; and when you read "studies show…" you cannot judge whether to trust it or how far it extrapolates

## What was distilled

10 capability cards, organized in the order "pick the model first, correct the assumptions second, land on the concrete situation last":

- **Router and model selection**: `model-recipe-selection` (the author's recipe: which model and default parameters for which problem type — the entry point for the whole book)
- **Preference correction**: `social-preference-measure` (dictator / ultimatum / trust readings plus the FS inequity-aversion function)
- **Reasoning and learning**: `cognitive-hierarchy-first-round` (cognitive hierarchy with Poisson layering plus QRE), `ewa-learning-model` (the φ / δ / κ attraction update and three identification criteria)
- **Equilibrium, signals and reputation**: `coordination-selection` (three-way classification, focal points, risk-dominance measures), `signal-reading` (the two credibility properties and the refinement ladder, including corporate-finance signals), `reputation-mechanism` (type priors and threshold paths)
- **Market structure and bargaining**: `market-entry-dynamics` (equilibrium entry counts, variance shrinkage and base-group neglect), `bargaining-prediction` (the outside-option trichotomy and the "split ↔ refined" interval)
- **Methodology audit**: `experiment-methodology-audit` (the five-factor check-up and attribution troubleshooting)

## Two packaging modes: single and pack

The same 10 capability cards are compiled twice, at two granularities. The content is identical; the only difference is how many entries an agent can discover.

| | single (one entry) | pack (compact pack, multiple entries) |
|---|---|---|
| Discoverable entries | **1**: `behavioral-game-theory-skill` | **8**: one source router + 7 promoted standalone skills |
| Where the 10 cards live | All inside the entry's `references/capabilities/`, loaded 1–2 at a time by the routing table | 7 cards become standalone skills; the other 3 stay in the router's `references/` |
| Triggering | Only the entry description participates in matching; routing happens after entry | 7 capabilities are matched directly, one hop fewer |
| Upgrades | Replace 1 directory | Replace 8 directories |

The 7 cards promoted to standalone skills in the pack:

- `model-recipe-selection` — the model-selection recipe (main router)
- `social-preference-measure` — social preferences (FS / reciprocity)
- `cognitive-hierarchy-first-round` — cognitive hierarchy and first-round prediction (CH/QRE)
- `ewa-learning-model` — EWA learning with mechanism identification
- `coordination-selection` — coordination games and equilibrium selection (focal points / risk dominance)
- `signal-reading` — signal reading, including corporate-finance signals
- `market-entry-dynamics` — market entry and crowding

The other 3 (`reputation-mechanism`, `bargaining-prediction`, `experiment-methodology-audit`) remain reachable through the router entry in the pack.

### Which one to install

Pick by the way you work, and **install only one**:

| How you work | Recommended | Why |
|---|---|---|
| You use DSH / Codex / Claude Code with a skills directory and want a clean list | single | Takes 1 slot, loses no capabilities |
| Your daily questions concentrate on "which model / how many steps will people think / who is following the crowd / which standard wins / can I trust this announcement / is this niche crowded" | pack | Those are exactly the promoted standalone skills, matched directly |
| You distribute to several agents or teammates who pick what they need | pack | They can install only the standalone skills they want |
| You want to install once and maintain one directory | single | Upgrades replace a single directory |

> Both builds come from the same bundle and carry identical capabilities. **Installing both will double-trigger**, so pick one.

## Examples

### Example 1: a new listing's first day — at which step does the crowd stop?

**User question**

"A stock lists tomorrow. Where will retail quotes cluster on day one, and at which level will people be thinking?"

**How the skill reasons**

- First `model-recipe-selection`: this is "the first interaction / how people choose in a new environment", so it takes branch B (first-round behaviour) and carries the default parameter table into the output
- Then `cognitive-hierarchy-first-round`: level 0 randomizes uniformly over the quote options; level k best-responds one step against the normalized distribution of levels 0 to k−1; each level's share follows the Poisson form f(k|τ)=e^(−τ)τ^k/k!, with τ defaulting to 1.5
- The input contract applies: you need the quote grid (the strategy set) and the payoff of each outcome (the payoff matrix). When the payoff matrix is missing, ask first — never invent numbers
- Stop condition: if the question turns into "how does it evolve over the following days", stop and switch to `ewa-learning-model` — that card covers period 2 onward, this one only covers period 1

**Sample answer**

> This is not a question about retail sentiment; it is a question about which step the crowd stops at. Under CH, level 0 picks uniformly across the quote grid; level 1 assumes everyone else is level 0 and takes one step further; level 2 takes one more. With the default τ = 1.5, levels 0 / 1 / 2 account for roughly 22.3% / 33.5% / 25.1%, about 81% together — over four fifths of quotes fall in the "thought one or two steps" band. That landing point has been replicated repeatedly in the book: the first-round median in beauty-contest games sits at step 2 (around 22), and an auction the author personally attended, full of game-theory veterans, also stopped at two steps.
>
> Two caveats must be stated. First, τ = 1.5 is what the author himself labels a "zero-calorie recipe" — a starting convention, not an empirical law; the book never reports measured parameters for the first day of a new listing. Second, the book also gives no formula for "which price quotes should cluster at" — CH computes each level's best response, and that best response depends on the quote grid and payoff structure you supply. Give me those two inputs and I can compute the weighted landing point; with only what we have now I can give you the distribution of reasoning depth, not a price.

### Example 2: a large buyback announcement — how much information does it carry?

**User question**

"This company just announced a large buyback and management says the stock is undervalued. What does the announcement actually say? Can I believe it?"

**How the skill reasons**

- First `model-recipe-selection`: the core of the question is "what private information does one side's action convey", so it goes to `signal-reading` — not the reputation card (that is the accumulation and spending of type probabilities across periods), and not the coordination card (there an announcement is a coordinating device)
- Two-property pre-check: a signal must be "affordable" for some types and "too expensive" for others. If neither property holds, the signal is idle and the card stops there
- Equilibrium-type identification: separating / pooling / semi-separating, judged by the cost differential
- Refinement screening: run the refinement ladder from weak to strong and predict within the set of equilibria that weak refinements pass — the book reports a 46%–63% hit rate for the intuitive criterion and a sharp decay above divinity, so strong refinements are reference only

**Sample answer**

> To judge whether this buyback is a signal, you only need to answer one question: does it cost a genuinely undervalued company the same as a company that is not? If the buyback must be paid in real cash and a cash-strapped company cannot afford it, then it is affordable for the high-value type and too expensive for the low-value type, both properties hold, and the announcement carries information. If the company can announce without executing, or execute at negligible cost, neither property holds — by the card's stop condition the signal is idle and should not be treated as one.
>
> The most direct evidence in the book comes from Myers-Majluf style financing experiments: when investors cannot separate good firms from bad, issuing equity transfers value to new shareholders, so good firms would rather shelve positive-NPV projects — the "bad money drives out good projects" pooling trap. That experiment's discriminant itself (good-type threshold 0.80, pooling threshold 0.60, cut-off 0.68) was re-checked sign by sign in the verification record; but the semi-separating ratio formula is misprinted in the book (logged for re-checking), so re-check the original before quoting specific ratios.
>
> Two boundaries as well: the book's evidence comes from student subjects, small cash stakes and small 2–3 type games, while corporate finance has regulatory and disclosure buffers that change the cost structure and must be re-estimated; and the book never gives a threshold for "how large a buyback counts as a strong signal" — that number is yours to set from the company's cash flow, and it belongs in a written plan.

## How these skills were generated

These skills were produced with the **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** RIA-TV++ pipeline, in six stages:

1. **Whole-book comprehension (Adler analysis)** — apply Mortimer Adler's analytical reading method to the book: structure, interpretation, criticism, application
2. **Parallel extraction** — several specialized extractors (frameworks, principles, cases, counter-examples, terminology) mine candidate methodology units from the source text
3. **Triple verification** — every candidate must pass three checks: at least two independent in-book supports (cross-domain), the ability to answer questions the book never explicitly addresses (predictive power), and not being common sense (distinctiveness)
4. **RIA++ construction** — structure each unit along R (quotation) / I (restatement in own words) / A1 (in-book case) / A2 (future trigger scenario) / E (executable steps) / B (boundaries and blind spots)
5. **Zettelkasten linking** — map dependencies, contrasts and combinations between cards, producing the capability index and routing table
6. **Trigger and output testing** — design trigger blind tests for the entry (including decoys: fire when they should, stay silent when they should not) plus execution assertions on representative tasks; anything that fails goes back for rework

The book is a methodology monograph, not an investing book, and that shapes the distillation: the A2 trigger scenarios are written around "the stock market is the largest and most persistent multi-player strategic interaction", while every card's B section keeps the experimental boundaries — student subjects, small cash stakes, 1990s data — which must be re-estimated before being applied to large real-money decisions.

## Testing and verification

This repository publishes the test material from the generation process alongside the skills: `evals/test-prompts.json` holds the package-level trigger cases (8 discoverable entries plus 12 prompts, including negatives and cross-skill confusion decoys), and `evals/test-results.md` is the item-by-item execution report, including the problems found and the stated limitations, not just the passes.

- **Trigger blind tests**: 12 / 12 passed, zero false triggers on decoys. The blind agent received only the 8 entries' name + description and the 12 prompts, without expected answers; 4 negatives (pure information lookup, a non-strategic daily plan, etc.) and 2 cross-skill confusion decoys (coordination vs signal, entry vs coordination) were all judged correctly
- **Router reachability**: the three non-promoted cards — reputation, bargaining, methodology audit — were all routed correctly in the blind test; no case of "entry matched but card unreachable"
- **Execution assertions**: 10 representative task groups and 23 mechanical assertions all passed (FS utility and rejection threshold, CH Poisson layering and QRE probabilities, EWA updates and degenerate cases, risk-dominance measures, equilibrium entry probability, separating-equilibrium determination, reputation threshold path, deal-me-out shares), tolerance 1e-3, independently recomputable
- **Known limitation**: this round ran **no without_skill baseline**, so it cannot claim "with skill beats without skill"; capability value currently rests on task-coverage mapping and assertion correctness. That limitation is written into the test report rather than glossed over

## Repository layout

```text
behavioral-game-theory-skill/
├── README.md                      ← Chinese version
├── README.en.md                   ← you are reading this
├── LICENSE                        ← MIT
├── BOOK_OVERVIEW.md               ← whole-book comprehension (Adler four-step, stage 0 output)
├── verified.md                    ← index and statistics of the triple-verification pass
├── single/                        ← single-entry build
│   └── behavioral-game-theory-skill/
│       ├── SKILL.md               ← entry: triggers + routing table + loading rules
│       ├── BUILD_MANIFEST.json    ← build manifest and file hashes
│       └── references/
│           ├── overview.md        ← whole-book overview
│           ├── capability-index.md  ← full intent and keyword index
│           ├── cheatsheet.md      ← decision-rule quick reference
│           ├── glossary.md        ← glossary
│           └── capabilities/      ← 10 capability cards
├── pack/                          ← multi-entry build (compact pack)
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json
│   ├── behavioral-game-router/
│   │   ├── SKILL.md               ← source router entry
│   │   └── references/            ← 10 cards + indexes, called by the router
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
└── evals/                          ← trigger cases and execution records
    ├── test-prompts.json          ← 8 entries + 12 package-level cases
    └── test-results.md            ← item-by-item results and stated limitations
```

## Usage

Clone the repository first:

```bash
git clone https://github.com/raphael-y7/behavioral-game-theory-skill.git
```

### Install single (recommended first try)

```bash
# macOS / Linux
cp -r behavioral-game-theory-skill/single/behavioral-game-theory-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\behavioral-game-theory-skill\single\behavioral-game-theory-skill "$env:USERPROFILE\.agents\skills\"
```

### Install pack

Copy only the directories that contain a `SKILL.md`; do not copy the two JSON files under `pack/` into your skills directory:

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

> `~/.agents/skills` is the DSH skills directory; with another agent, use its own skills directory (for example `~/.claude/skills` for Claude Code).

### How to verify the install

Ask: "This company just announced a large buyback — how do I judge how much information the signal carries?" If the agent enters the two-property pre-check and equilibrium-type identification of `signal-reading` instead of giving generic "buybacks are bullish" commentary, the install works. With the single build it reads the entry first and then routes to a card; with the pack build the matching capability is hit directly.

## Sources

- *Behavioral Game Theory* by Colin F. Camerer
- Distilled from the whole book, producing 10 capability cards

## Notice

This repository publishes distilled skills, indexes and rule quick references only. It contains no PDF, EPUB, OCR files, screenshots or full-book transcripts of the source book. Quotations that appear in the capability cards serve solely to attribute methodology and keep the material auditable.

All numeric criteria in the book (the FS α/β values, the CH Poisson τ, the fEWA λ, entry-game capacities and thresholds, the reputation τ^n path, etc.) are experimental cases and empirical generalisations without directly transferable statistical backing; re-estimate them for your own setting and declare the convention you use. Nothing in this repository is investment advice.

## License

[MIT](https://opensource.org/licenses/MIT)
