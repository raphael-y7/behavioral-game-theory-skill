<h1 align="center">Behavioral Game Theory Skill</h1>

<p align="center"><a href="README.md">中文</a> | English</p>

An AI skill pack for immediate use — it distills the experimental findings and computable models in Colin F. Camerer's *Behavioral Game Theory: Experiments in Strategic Interaction* into 10 capability cards that can be triggered individually or combined, covering social preferences, bounded reasoning, learning dynamics, equilibrium selection, signaling, reputation, market entry, bargaining and research-method auditing.

It is not a book summary, nor a reading response — it breaks the reusable methodology in the book into skill modules that can be triggered, executed and tested.

## What these skills solve

- A company announces a share issue, a buyback, a dividend or a heavy debt load, and you cannot tell whether it is good news or an information trap in a market of bad news — so you reverse-engineer the answer from today's price move
- An IPO's first trading day, a new rule, a new platform: you want to predict "what will people pick on the first move" and all you have is the useless line "rational players pick the equilibrium"
- A track already has a dozen entrants and you want to know whether there is room left, but you can only do your own arithmetic, not your rivals' willingness to enter
- Several standards, platforms or narratives are competing and you want to predict which one wins and whether an early choice locks the market in, instead of explaining "path dependence" afterwards
- For a merger, a block trade or a salary negotiation you can only guess "roughly a fifty-fifty split", and cannot say when an outside option (BATNA) should knock one side out entirely
- You read "experiments show that…" and cannot tell whether to read the method first or the result, nor whether it extrapolates to real money in real markets

## What was distilled

10 capability cards, organized in the order "select the model first, compute second, audit last", matching the `capabilities` entries in `bundle/verified.yaml` one for one:

- **Master router**: `model-recipe-selection` — the author's own three-branch decision recipe from the end of the book, with default parameters
- **Preferences and bargaining**: `social-preference-measure` (the FS inequity-aversion formula plus the dictator/ultimatum/trust measurement trio), `bargaining-prediction` (alternating-offer SPE, the deal-me-out test, the split-to-refined interval)
- **Reasoning and learning**: `cognitive-hierarchy-first-round` (Poisson cognitive hierarchy and QRE for first-round predictions), `ewa-learning-model` (EWA/fEWA updating rules and the three mechanism-identification criteria)
- **Equilibrium and entry**: `coordination-selection` (the matching/stag-hunt/battle-of-the-sexes trichotomy, focal points, risk-dominance measures), `market-entry-dynamics` (capacity-versus-crowd equilibrium and base-rate neglect)
- **Information and reputation**: `signal-reading` (the two credibility properties, equilibrium identification, the refinement ladder, including the Myers-Majluf corporate-finance discriminant), `reputation-mechanism` (Bayesian accumulation of type probabilities, threshold paths, permanent disqualification after one default)
- **Meta-method**: `experiment-methodology-audit` (the five-factor check-up and the four-step attribution of counter-intuitive results)

## Two packaging modes: single and pack

The same 10 capability cards are compiled twice, at two granularities. The content is identical; the only difference is how many entries an agent can discover.

| | single (one entry) | pack (compact pack, multiple entries) |
|---|---|---|
| Discoverable entries | **1**: `behavioral-game-theory-skill` | **8**: one source router + 7 promoted standalone skills |
| Where the 10 cards live | All inside the entry's `references/capabilities/`, loaded 1–2 at a time by the router table | 7 cards become standalone skills; all 10 also keep a card view under the router's `references/` |
| Triggering | Only the entry description participates in matching; routing happens after entry | The 7 high-frequency capabilities are matched directly, one hop fewer |
| Upgrades | Replace 1 directory | Replace 8 directories |

The 7 cards promoted to standalone skills in the pack:

- `model-recipe-selection` — model selection recipe (master router)
- `social-preference-measure` — social-preference measurement and computation
- `cognitive-hierarchy-first-round` — cognitive hierarchy and first-round prediction
- `ewa-learning-model` — EWA learning models
- `coordination-selection` — coordination games and equilibrium selection
- `signal-reading` — signal interpretation
- `market-entry-dynamics` — market entry and crowding

The 3 that were not promoted (`reputation-mechanism`, `bargaining-prediction`, `experiment-methodology-audit`) are reachable only through the router entry: the first two have trigger surfaces that overlap with neighbouring cards, so standalone skills would compete for the same questions, while the third is a meta-method always invoked alongside a domain card. All three are folded into the router entry under the rule "the fewest entries that cover the most intents".

### Which one to install

Pick by the way you work, and **install only one**:

| How you work | Recommended | Why |
|---|---|---|
| You use DSH / Codex / Claude Code with a skills directory and want a clean list | single | Takes 1 slot, loses no capabilities |
| Your daily questions concentrate on "which model / how to compute fairness / what happens on the first move / is this track crowded / can I trust this announcement" | pack | Those are exactly the promoted standalone skills, matched directly |
| You distribute to several agents or teammates who pick what they need | pack | They can install only the standalone skills they want |
| You want to install once and maintain one directory | single | Upgrades replace a single directory |

> Both builds come from the same bundle and carry identical capabilities. **Installing both will double-trigger**, so pick one.

## Examples

### Example 1: the stock fell 4% on a share-issue announcement — bad news or a mispricing?

**User question**

"My company just announced a private placement and the stock fell 4% that day. Is that bad news, or is the market overreacting?"

**How the skill reasons**

- Route first: this is the information content of a one-off announcement, so it belongs to `signal-reading` — not to `reputation-mechanism`, which handles the build-up and depletion of type probabilities over time
- Two-property check: is this signal affordable for the good type and too expensive for the bad type? The cost of a share issue is handing project value to new shareholders, and that cost moves in the opposite direction to firm type — if both types bear the same cost, the signal is empty and the analysis stops at step one
- Equilibrium identification: use the Myers-Majluf discriminant to compute the investors' break-even price in the pooling equilibrium and whether the good firm abandons the project, then decide whether the situation is separating, pooling or semi-separating
- Refinement: stop at weak refinement (the intuitive criterion); do not predict with strong criteria such as divinity

**Sample answer**

> Do not treat "down 4%" as the conclusion. Whether this announcement carries information depends on the cost structure: if a good firm and a bad firm pay roughly the same to issue, it is not a signal at all and the size of the drop tells you nothing about type. Assuming the costs really are asymmetric, the next question is which equilibrium you are in. In a pooling equilibrium, "a good firm issues shares" is itself bad news, because issuing hands part of a good project's value to new shareholders, and a good firm would rather shelve the project — that is a structural result, not market irrationality. So before calling it a mispricing, check two things: whether the money funds a project only a good firm would dare take (the bigger the cost gap, the more likely separation), and whether a cheaper signal (debt, buybacks) is being used at the same time. On refinement, the intuitive criterion is enough — the book's experimental data show that stronger criteria (divinity and beyond) actually predict *which* equilibrium appears less well. One caveat: this evidence comes from small-stakes laboratory financing experiments, so it does not transfer directly in magnitude or in disclosure rules to A-shares.

### Example 2: twelve entrants already, three more raising money — is there room left?

**User question**

"Twelve companies entered this track this year and three more are raising. Is there still room for us?"

**How the skill reasons**

- Route to `market-entry-dynamics`: the key variable is "people versus capacity", not "which equilibrium" (that would be `coordination-selection`)
- Input contract: number of potential entrants n, market capacity c, revenue per unit share r, outside option k. If c or k is missing, ask first — without capacity and an outside option there is no entry game at all (stop point)
- Compute the equilibrium benchmark: total payoff k+r(c−m) with m=Σe_j gives the equilibrium entry probability and expected number of entrants
- Two behavioural corrections: the actual variance of entry counts is far smaller than the mixed-equilibrium prediction (people take turns rather than each rolling their own dice); and under self-selection, base-rate neglect appears — everyone believes they are above average, and in the book's entry-plus-skill experiments the group as a whole lost money in 70% of periods while individuals kept entering

**Sample answer**

> Do the arithmetic before talking about room. Put capacity c, revenue per share r and outside option k into k+r(c−m); the equilibrium entry probability and expected entrant count that come out are your baseline. What you are judging is where "12 already in, 3 in talks" sits relative to c. Then add the two systematic deviations. First, real entry counts fluctuate much less than the model predicts — crowds stagger themselves rather than all entering at once — so do not plan against a worst case in which everyone enters simultaneously. Second, if this is a filtered opportunity (credentials, licences, brand backing), base-rate neglect makes crowding worse than the rational prediction: in the book's experiments such groups lost money in seven periods out of ten and still nobody exited. State the conclusion precisely: it is "the marginal entrant loses money overall", not "the industry is unprofitable" — lower-cost players still make money. Finally, check the repair condition: if per-period losses are observable, later entry corrects itself; if they are not, crowding drags on much longer.

## How these skills were generated

These skills were produced with the **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)** RIA-TV++ pipeline, in six stages:

1. **Whole-book comprehension (Adler analysis)** — apply Mortimer Adler's analytical reading method to the book: structure, interpretation, criticism, application; this produced `BOOK_OVERVIEW.md` and a list of 12 reader tasks
2. **Parallel extraction** — several specialized extractors (frameworks, principles, cases, counter-examples, terminology) mine candidate methodology units from the source text; this book yielded 659 candidates
3. **Triple verification** — every candidate must pass three checks: at least two independent in-book supports (cross-domain), the ability to answer questions the book never explicitly addresses (predictive power), and not being common sense (distinctiveness). 504 of the 659 passed, and the same pass adjudicated misprints and misattributed quotations in the source
4. **RIA++ construction** — structure each unit along R (quotation) / I (restatement in own words) / A1 (in-book case) / A2 (future trigger scenario) / E (executable steps) / B (boundaries and blind spots)
5. **Zettelkasten linking** — map dependencies, contrasts and combinations between cards, producing the capability index and routing table, and merging the 504 verified units into 10 capability units
6. **Trigger and output testing** — write trigger blind tests (including decoy questions: fire when they should, stay silent when they should not) and output evaluation scenarios for every card; failing cards go back for rework and are re-verified afterwards

Promotion happens after stage 5: 7 of the 10 cards pass all five independence criteria (independent intent, contract, execution, reuse and evaluation) and become standalone skills, while the other 3 are demoted to router cards under the rule "the fewest entries that cover the most intents" — two because their trigger surfaces overlap with neighbouring cards, one because it is a meta-method always invoked alongside a domain card.

## Testing and verification

This repository publishes the test material from the generation process alongside the skills: `evals/test-prompts.json` holds the entry-level trigger and boundary cases, and `evals/test-results.md` is the item-by-item scoring log — including the problems found and the stated limitations, not just the passes.

- **Trigger blind tests**: a blind agent received only the name and description of the 8 entries plus 12 prompts, with no expected answers; 12 / 12 passed with zero false triggers on decoys (4 negative cases and 2 cross-skill confusion decoys — "coordination ≠ signaling", "coordination ≠ entry")
- **Reachability**: the 3 router cards (reputation, bargaining, audit) were correctly routed in the blind test, with reasons pointing at the right card — none went missing
- **Output evaluation**: each of the 10 capability families ran a representative task on new inputs, computed independently from the canonical formulas and checked by mechanical assertions (tolerance 1e-3); 23 / 23 passed — including FS utility, CH Poisson tiers, one-step EWA updating with the δ=0 degeneracy check, the risk-dominance measure, entry probability p*≈0.105 and the deal-me-out share
- **Known limitation**: this round did **not** run a without_skill baseline, so no claim is made that "with the skill beats without it"; the value claim rests on task mapping and assertion correctness for now, and the baseline is left for a later pass. This is written into `evals/test-results.md` rather than hidden

## Repository layout

```text
behavioral-game-theory-skill/
├── README.md                      ← Chinese version
├── README.en.md                   ← you are reading this
├── LICENSE                        ← MIT
├── BOOK_OVERVIEW.md               ← whole-book comprehension (Adler four-step, stage 0 output)
├── CANGJIE_ADAPTATION.md          ← adaptation notes: text state, distillation goals, evidence rules, boundaries
├── TEST_SUMMARY.md                ← stage 4 stress-test summary (scope, structure checks, results, next steps)
├── verified.md                    ← triple-verification statistics and adjudications (stage 1.5)
├── INDEX.md                       ← skill map: capability table, dependencies, loading order
├── candidates/                    ← stage 1 candidate pool (659 raw extraction records, kept for traceability)
│   ├── frameworks.md              ← 203 framework candidates (5 groups merged)
│   ├── principles.md              ← 329 principle candidates (6 groups merged)
│   ├── cases.md                   ← 44 case candidates
│   ├── counter-examples.md        ← 35 counter-example candidates
│   └── glossary.md                ← 48 glossary candidates
├── bundle/                        ← build source: canonical copies of the 10 cards
│   ├── verified.yaml              ← metadata, criteria and promotion verdicts for the 10 cards
│   ├── cards/                     ← 10 capability cards (R/I/A1/A2/E/B sections)
│   └── book/
│       ├── overview.md            ← whole-book overview
│       └── glossary.md            ← glossary
├── single/                        ← single-entry build
│   └── behavioral-game-theory-skill/
│       ├── SKILL.md               ← entry: triggers + routing table + loading rules
│       ├── BUILD_MANIFEST.json    ← build manifest and file hashes
│       ├── test-prompts.json      ← entry-level trigger and boundary cases (shipped for post-install regression)
│       └── references/
│           ├── overview.md
│           ├── capability-index.md  ← full intent and keyword index
│           ├── cheatsheet.md        ← decision-rule quick reference
│           ├── glossary.md
│           └── capabilities/        ← 10 capability cards
├── pack/                          ← multi-entry build (compact pack)
│   ├── BUILD_MANIFEST.json
│   ├── capability-destinations.json ← where each of the 10 cards went
│   ├── behavioral-game-theory-skill-router/
│   │   ├── SKILL.md               ← source router entry (the 3 router cards are reached here)
│   │   └── references/
│   │       ├── overview.md
│   │       ├── capability-index.md
│   │       ├── cheatsheet.md
│   │       ├── glossary.md
│   │       └── capabilities/       ← card views for all 10 capabilities
│   ├── model-recipe-selection/SKILL.md
│   ├── social-preference-measure/SKILL.md
│   ├── cognitive-hierarchy-first-round/SKILL.md
│   ├── ewa-learning-model/SKILL.md
│   ├── coordination-selection/SKILL.md
│   ├── signal-reading/SKILL.md
│   └── market-entry-dynamics/SKILL.md
└── evals/                         ← trigger blind tests and output evaluation
    ├── test-prompts.json          ← entry-level trigger and boundary cases
    └── test-results.md            ← item-by-item scoring, issues and limitations
```

## Usage

Clone the repository first (replace `<your-account>` with the actual account):

```bash
git clone https://github.com/<your-account>/behavioral-game-theory-skill.git
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

> `~/.agents/skills` is the DSH skills directory; with another agent, use its own directory (Claude Code uses `~/.claude/skills`, for example).

### How to confirm it is installed

Ask "a dozen companies have already entered this track — is there room for one more?" and see whether the agent goes straight into entry-game arithmetic (asking for capacity c and outside option k first, then computing the equilibrium entrant count) rather than giving a generic industry commentary. With single installed it reads the entry first and then routes to a card; with pack installed the matching capability is hit directly.

## Source

- *Behavioral Game Theory: Experiments in Strategic Interaction* by Colin F. Camerer
- Distilled into 10 capability cards, 7 of which were promoted to standalone skills

## Notice

This repository publishes only the distilled skills, indexes and rule quick-references. It does not contain the original PDF, EPUB, OCR files, screenshots or a full-book transcript. Quotations that appear in the cards serve only to attribute the methodology and keep it auditable.

Every numeric criterion in the book (default parameters α=1/3, τ=1.5, λ=1, rejection rates and entry probabilities and other empirical anchors) comes from laboratory experiments and the author's own summary; the book provides no cross-scenario statistical backtesting, and the author himself calls the defaults a "zero-calorie recipe". Re-estimate them for any new setting and state the convention you used. Nothing here constitutes investment advice.

## License

[MIT](./LICENSE)
