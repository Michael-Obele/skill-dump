# Evidence and sources: executive-loop

Research pass run 2026-10-12 with `tomoshi_discover` (SearXNG) and `tomoshi_extract`.
Tier 1 = primary or first-party. Tier 2 = reputable secondary or peer-reviewed venue.
Tier 3 = blog or opinion.

## The research question

Why do top models need less hand-holding than cheap ones, and how much of that gap can
a written procedure actually close?

Sub-questions investigated:

1. What does the psychology say the underlying ability is? (metacognition, meta-reasoning)
2. Do models have this ability and fail to use it, or do they lack it?
3. Where do they lose most: too much reasoning, too little, or bad judgment?
4. How do good agents decide when to fetch context versus think versus ask?
5. Does any of this transfer to small or cheap models, and what does not?

## Finding 1: The ability is joint monitoring and control, and models split them

**Confidence: High. Consensus: strong across the survey literature.**

The psychology is settled and old. Flavell (1979) defined metacognition as two
interacting processes: **monitoring** (judging your own uncertainty, performance,
progress) and **control** (planning, strategy selection, re-allocating effort based on
that monitoring). Ackerman and Thompson (2017) narrowed this for reasoning tasks as
*meta-reasoning*: monitor progress, decide whether to keep going or change approach.

Models do the first half and skip the second.

- Cao et al. (2026), Tier 1: models can estimate pre-solve success and post-solve
  correctness, "however, these signals are typically measured or elicited in isolation,
  rather than used to control inference." Their harness turned those signals into an
  explicit control interface (trust / retry / aggregate). On a fixed Claude Sonnet-4.6
  with no parameter updates: pooled accuracy **48.3 to 56.9**, beating the strongest
  listed leaderboard entries on HLE-Verified, LiveCodeBench v6, and R-Bench-V.
- Ma et al. (2025), EMNLP, Tier 1: title says it plainly, "Large Language Models Have
  Intrinsic Meta-Cognition, but Need a Good Lens."
- Li et al. (2025), ACL, Tier 1: "Adaptive Tool Use in Large Language Models with
  Meta-Cognition Trigger", the same pattern applied to tool selection.

**What this means for the skill:** asking a model to feel confident does nothing.
Converting a self-report into a branch with a named action is what changes results.

## Finding 2: Models are systematically overconfident, and it gets worse mid-task

**Confidence: High. Consensus: strong.**

- Barkan et al. (2025), Tier 1: "All LLMs we tested are overconfident, but most predict
  their success with better-than-random discriminatory power." Two findings that matter
  operationally: on multi-step agentic tasks, overconfidence of several frontier models
  **worsens as they progress**; and reasoning models were comparable to or worse than
  non-reasoning ones at this. Also: when the models did estimate, their decisions were
  "approximately rational given their estimated probabilities", so the failure is the
  estimate, not the logic built on it.
- Griot et al. (2025), Nature Communications, Tier 1: LLMs "lack essential metacognition
  for reliable medical reasoning."
- Ackerman (2025), Tier 1 preprint: "Evidence for Limited Metacognition in LLMs."
- Human analogue for the failure shape: Kruger and Dunning (1999); Fleming (2024) on
  confidence calibration.

**Counter-evidence, and it matters:** Singh et al. and others in the Yale survey report
that metacognitive *sensitivity* trades off against raw reasoning ability in some
models. Being good at reasoning and being well calibrated are not the same axis.

## Finding 3: Both overthinking and underthinking are real, and they are the same defect

**Confidence: High. Consensus: strong, multiple independent groups.**

Overthinking, Cuadron et al. (2025), Tier 1, SWE-bench Verified, 4,018 trajectories:

- Three named patterns: **Analysis Paralysis**, **Rogue Actions**, **Premature
  Disengagement**.
- Higher overthinking score correlates with lower performance; reasoning models
  overthink more than non-reasoning models.
- Picking the lower-overthinking solution improved performance by almost **30%** while
  cutting compute by **43%**.

Underthinking, Wang et al. (2025), Tier 1, on o1-like models:

- Models "frequently switch between different reasoning thoughts without sufficiently
  exploring promising paths."
- Wrong answers consumed **225% more tokens** than right ones, from **418% more**
  strategy switching.

Efficiency line of work: "Stop Overthinking: A Survey on Efficient Reasoning for LLMs"
(arXiv:2503.16419, TMLR); "Think How to Think: Mitigating Overthinking with Autonomous
Difficulty Cognition" (arXiv:2507.02663); "CAT: Confidence-Adaptive Thinking for
Efficient Reasoning" (arXiv:2607.00862); DTSR, Xiang et al. (2026), Tier 1: reduces
reasoning length **28.9% to 34.9%** with minimal performance loss by checking whether
the chain of thought is *sufficient* yet.

**What this means for the skill:** the target is not "think more" or "think less". The
target is knowing when to stop. Skipping and spinning get the same counter-moves.

## Finding 4: Effort must be allocated per step, not per task

**Confidence: High for the direction, Medium for exact magnitudes.**

- Yang et al. (2026), Tier 1, Ares: running every step at low reasoning effort instead
  of high cost nearly **20% accuracy** on gpt-oss-20b. A lightweight router (Qwen3-1.7B)
  predicting the *lowest sufficient* effort per step cut reasoning tokens by **52.7%**
  on TAU-Bench with no accuracy loss, and slightly better results than always-high.
- Evaluated on TAU-Bench (tool use), BrowseComp-Plus (deep research), WebArena (web).

**What this means for the skill:** triage is a first-class skill, and the discriminator
is reversibility plus novelty, not how important the task sounds.

## Finding 5: Ask-versus-act is where weak models lose the most, and awareness is not enough

**Confidence: High. Consensus: strong on the direction; the ranking of specific models
is from a single benchmark and single reporting pass.**

DiscoBench (Cheng et al., 2026), reported by The Decoder, Tier 2 reporting a Tier 1
benchmark. 211 tasks, 463 ambiguous points, 11 knowledge domains, 11 models released in
the previous six months:

| Behaviour at an ambiguous checkpoint | Success |
|---|---|
| Search first, then ask a follow-up | **93.4%** |
| Guess without asking | 56.5% |
| Search repeatedly, still guess | 51.9% |

- Without any hint, the best model reached only **43.1%** end to end (Doubao Seed 2.0
  Pro); Gemini 3.1 Pro 40.8%, Claude Opus 4.7 39.8%, MiniMax M2.7 16.1%, Qwen3.6 Max 12.3%.
- Claude Opus 4.7 solved 57% of individual checkpoints but only 39.8% end to end. One
  unresolved ambiguity collapses the chain.
- A system prompt telling models to watch for ambiguity raised Detection F1 from 45.3
  to **64.9**, but end-to-end accuracy only from 28.6 to **33.7**. For Claude Opus 4.7
  end-to-end accuracy even dipped.
- Detecting ambiguity and asking a good question are separate skills: Qwen3.6 Max had
  Detection F1 of 16% and asked 0.07 follow-ups per task, but 94.7% of the questions it
  did ask were factually correct.
- Removing ambiguity entirely raised accuracy by 26.8 to 40.2 points.

Supporting: Wang et al. (2025), EMNLP, "Learning to Ask: When LLM Agents Meet Unclear
Instruction" (NoisyToolBench); Kim et al. (2021), Amazon Science, on deciding *whether*
to ask a clarifying question rather than always asking.

**What this means for the skill:** more searching is not a substitute for asking, and
"be careful about ambiguity" is not a usable instruction. The rule has to name the
branch and the artifact (one discriminating question).

## Finding 6: Context should be pulled just in time, and interference beats volume

**Confidence: High for the practice. Consensus: strong, first-party plus independent
mechanistic work.**

- Anthropic, "Effective context engineering for AI agents", Tier 1: context is a finite
  attention budget ("context rot"); the goal is "the smallest possible set of
  high-signal tokens"; prefer just-in-time retrieval with lightweight identifiers over
  preloading; progressive disclosure; compaction, structured note-taking, and sub-agents
  for long-horizon work. Sub-agents that explore with tens of thousands of tokens but
  return a 1,000 to 2,000 token digest.
- Anthropic, "Building effective agents", Tier 1: simplicity first; routing easy queries
  to cheaper models and hard ones to stronger models; increase complexity only when it
  demonstrably helps.
- Wang et al. (2025), Tier 1, PI-LLM: with accumulating semantically related overwrites,
  retrieval accuracy "declines log-linearly toward zero". Prompt-level mitigations such
  as telling the model to ignore earlier input "yield limited success." This is a working
  memory bottleneck, not an instruction-following one.
- Chen et al. (2026), Tier 1, EvoCtx: models the choice between retrieving new evidence
  and refining within existing evidence, instead of treating retrieval as the default at
  every step.

**What this means for the skill:** hygiene and judgment about *when* to look beat
exhortations to look more.

## Finding 7: Metacognitive scaffolding can lift a cheaper model, but not by introspection

**Confidence: Medium to High. Consensus: moderate, with a clear boundary condition.**

For scaffolding:

- Khandelwal et al. (2025), Tier 1, SOFAI-LM: a fast LLM plus a metacognitive module
  giving targeted iterative feedback "match or even exceed" standalone large reasoning
  models on graph coloring and code debugging, at significantly lower inference time.
  When the fast loop is insufficient, the architecture escalates to the slow model and
  hands over what the fast loop learned. This is the escalation contract in the skill.
- Cao et al. (2026): same family, +8.6 points on a frozen model.
- Anthropic, Tier 1: harder queries routed to more capable models, easy ones to cheaper
  ones, is a first-party recommended pattern.

Against introspection specifically, and this is the boundary:

- Advani (2026), Tier 1: 10,734 reasoning traces from 7-9B models. **50 to 69% of correct
  answers contained fundamentally flawed reasoning.** Retrieval-augmented generation
  improved reasoning integrity substantially (Cohen's d 0.23 to 0.93), while
  "meta-cognitive interventions like self-critique often harm performance
  (d = -0.14 to -0.33) in small models". Meta-cognition "amplifies confusion without
  sufficient model capacity."
- Li et al. (2025), ACL Findings, Tier 1, ReflectEvo: small models improved a lot via
  reflection learning (Llama-3 52.4 to 71.2, Mistral 44.4 to 71.1) but this is **training
  via SFT and DPO on a 460k self-generated dataset**, not prompting. Do not read it as
  evidence that a prompt fixes the gap.

**What this means for the skill:** every check must be external and observable. The
skill encodes grounding and escalation, never "reflect harder".

## Finding 8: The honest limits on closing the gap from outside the weights

**Confidence: High. Consensus: active debate on magnitude, clear on direction.**

- Wang et al. (2025), ACL Findings, Tier 1: the **Small Model Learnability Gap**.
  Models at or under 3B parameters "do not consistently benefit from long chain-of-thought
  (CoT) reasoning or distillation from larger models."
- AIMO 3 competition writeup, Tier 1 (arXiv:2603.27844), title: "Model Capability
  Dominates". Across 23+ experiments, 3 models, 50 IMO-level problems: "Every prompt-level
  intervention fails." Across an 8-point capability gap, capability dominated. Most of
  the remaining loss was selection, not prompting (best majority vote 42/50 vs pass@20 of
  45.5).
- Metacognition survey, Yale NLP, Tier 1: metacognitive sensitivity is not uniformly
  better in bigger models, and there is a documented trade-off between reasoning ability
  and metacognitive sensitivity.

**Counterweight, worth stating fairly:** elicitation work (UK AI Safety Institute and
"The Elicitation Game", Tier 2 to 3 as reported) argues that getting a model to use what
it already knows can be worth the equivalent of a large increase in training compute.
The two positions are compatible: elicitation recovers *latent* capability that is
present, and cannot conjure capability that is absent.

**What this means for the skill:** claim only what is defensible. A harness stops
self-inflicted losses. It does not add reasoning capacity. Say so in the skill, and
escalate when the harness is not enough.

## Where sources disagree

- **Can prompting fix small-model reasoning?** Advani (2026) and AIMO 3 say no, and
  sometimes it backfires. Elicitation research says elicitation is worth a lot. The
  reconciliation is that elicitation recovers latent ability while prompting cannot
  create missing ability; both can be true for different tasks and model sizes.
- **Do bigger models have better metacognition?** Barkan et al. (2025) found newer and
  larger models generally do **not** have better discriminatory power, with Claude models
  as a possible exception. The Yale survey notes a reasoning-versus-calibration trade-off.
  So calibration is not simply a scale effect, which is why a harness is worth trying.
- **Is asking always better?** No. Amazon's earlier work treats asking as a decision with
  a cost. DiscoBench's `SearchThenAsk` result is about order (source first, ask second),
  not about asking at every opportunity. Over-asking is a failure mode too.

## Gaps and unknowns

- No study found that measures a pure prompt or skill (no fine-tuning, no harness code,
  no external tools) at closing an agentic decision-making gap. The positive results all
  add a controller, a router, or a tool.
- DiscoBench's model ranking comes from one benchmark with mostly Chinese-language tasks;
  treat exact rankings as provisional, the behavioural ordering as robust.
- Effects of a skill file on a specific cheap model (DeepSeek Flash, GLM Flash, Haiku
  class) are untested. Measuring that would need a small eval, not more reading.

## Sources

| # | Source | Tier | Supports |
|---|---|---|---|
| 1 | Flavell, "Metacognition and Cognitive Monitoring", American Psychologist 1979 | 1 | monitoring + control definition |
| 2 | Ackerman & Thompson, "Meta-Reasoning", Trends in Cognitive Sciences 2017 | 1 | monitor and control of reasoning |
| 3 | Kruger & Dunning, JPSP 1999; Fleming, Annual Review of Psychology 2024 | 1 | calibration failure shape |
| 4 | [Cao et al., "LLMs Know When They Know, but Do Not Act on It", arXiv:2605.14186](https://arxiv.org/abs/2605.14186) | 1 | metacognitive harness, 48.3 to 56.9 |
| 5 | [Khandelwal et al., "Language Models Coupled with Metacognition Can Outperform Reasoning Models", arXiv:2508.17959](https://arxiv.org/abs/2508.17959) | 1 | fast plus metacognitive module beats slow model |
| 6 | [Barkan et al., "Do Large Language Models Know What They Are Capable Of?", arXiv:2512.24661](https://arxiv.org/abs/2512.24661) | 1 | overconfidence worsens mid-task |
| 7 | [Cuadron et al., "The Danger of Overthinking", arXiv:2502.08235](https://arxiv.org/abs/2502.08235) | 1 | three overthinking patterns; +30% / -43% |
| 8 | [Wang et al., "On the Underthinking of o1-Like LLMs", arXiv:2501.18585](https://arxiv.org/abs/2501.18585) | 1 | 225% / 418% token and switching figures |
| 9 | [Yang et al., "Ares: Adaptive Reasoning Effort Selection", arXiv:2603.07915](https://arxiv.org/abs/2603.07915) | 1 | per-step effort; 20% drop; 52.7% saving |
| 10 | [Xiang et al., "When Is Thinking Enough?", arXiv:2604.06787](https://arxiv.org/abs/2604.06787) | 1 | sufficiency check, 28.9 to 34.9% shorter |
| 11 | [Wang et al., "Unable to Forget" (PI-LLM), arXiv:2506.08184](https://arxiv.org/abs/2506.08184) | 1 | interference; prompt fixes limited |
| 12 | [Chen et al., "To Retrieve or To Think?", arXiv:2601.08747](https://arxiv.org/abs/2601.08747) | 1 | retrieve vs refine decision |
| 13 | [Advani, "When Small Models Are Right for Wrong Reasons", arXiv:2601.00513](https://arxiv.org/abs/2601.00513) | 1 | grounding helps, self-critique hurts |
| 14 | [Li et al., "ReflectEvo", ACL Findings 2025](https://aclanthology.org/2025.findings-acl.871/) | 1 | small models improve, but via training |
| 15 | [Wang et al., "Learning to Ask", EMNLP 2025](https://aclanthology.org/2025.emnlp-main.1104.pdf) | 1 | NoisyToolBench, learning when to ask |
| 16 | [Z. Wang et al., "Small Models Struggle to Learn from Strong Reasoners", arXiv:2502.12143](https://arxiv.org/abs/2502.12143) | 1 | Small Model Learnability Gap |
| 17 | [DiscoBench, reported by The Decoder](https://the-decoder.com/ai-search-agents-dont-fail-at-searching-they-fail-at-asking-the-right-questions-when-queries-get-ambiguous/) | 2 | the 93.4 / 56.5 / 51.9 table; 43.1% ceiling |
| 18 | [Anthropic, "Effective context engineering for AI agents"](https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents) | 1 | context rot, just-in-time, compaction |
| 19 | [Anthropic, "Building effective agents"](https://www.anthropic.com/engineering/building-effective-agents) | 1 | simplicity first, routing |
| 20 | [Yale NLP, "Metacognition in LLMs: Foundations, Progress, and Opportunities"](https://github.com/yale-nlp/LLM-Metacognition) | 1 | survey index, 275 papers |
| 21 | [Ma et al., "LLMs Have Intrinsic Meta-Cognition, but Need a Good Lens", EMNLP 2025](https://aclanthology.org/2025.emnlp-main.171/) | 1 | latent metacognition |
| 22 | [Li et al., "Adaptive Tool Use with Meta-Cognition Trigger", ACL 2025](https://aclanthology.org/2025.acl-long.655/) | 1 | tool-selection gating |
| 23 | [AIMO 3 writeup, "Model Capability Dominates", arXiv:2603.27844](https://sophon.at/papers/pwc-57546) | 1 | every prompt-level intervention failed |
| 24 | [Oh, "Before You think, Monitor", arXiv:2510.16374](https://arxiv.org/abs/2510.16374) | 1 | Flavell's framework applied to LLMs |
| 25 | [Kim et al., "Deciding whether to ask clarifying questions", Amazon Science 2021](https://www.amazon.science/publications/deciding-whether-to-ask-clarifying-questions-in-large-scale-spoken-language-understanding) | 1 | asking is a decision with a cost |
