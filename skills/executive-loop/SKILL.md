---
name: executive-loop
description: 'Use when a task needs judgment instead of step-by-step instruction: underspecified or ambiguous asks, multi-step agent work, long-horizon builds, "figure it out", "do the needful", "just handle it", or any moment where a model is about to guess, overthink, skip verification, or spin without progress. Gives fast and cheap models the supervisory loop that frontier models run by default: frame the task, source context just in time, decide ask vs act vs escalate, size effort to the step, check against the environment, and stop cleanly. Load it whenever a cheaper model is doing real work on its own.'
---

# Executive Loop

Top models do not need much explaining because they run a supervisor over their own
work: frame the task, fetch what is missing, choose an action, size the effort,
check reality, stop. Cheaper models generate at the same speed but with a weak
supervisor, so they fail in three ways: they skip the setup, they misjudge their own
confidence, or they spin.

This skill is that supervisor, written down as rules a model can follow. It is for
any model doing autonomous work. It matters most on the fast and cheap ones.

## The finding this is built on

**The judgment is often already there. The interface to act on it is not.**
Cao et al. (2026) wrapped a fixed model in a harness that turns its own pre-solve and
post-solve estimates into *control decisions* (trust it, retry it with feedback,
aggregate several attempts) and lifted accuracy from 48.3 to 56.9 with no weight
updates. The metacognition was latent; the wiring was missing. Wiring is exactly what
a skill can supply.

**Introspection-flavoured fixes backfire on small models.** Advani (2026) found that
telling small models to self-critique *hurt* them (Cohen's d between -0.14 and -0.33)
while plain external grounding helped a lot (d between 0.23 and 0.93). So every check
in this skill is external and observable. Never "think harder". Always "go look".

**Both failure directions are real.** Overthinking lowers scores: Cuadron et al. (2025)
found higher overthinking scores correlating with worse results on SWE-bench Verified,
and simply picking the lower-overthinking attempt gained almost 30% in performance and
saved 43% of compute. Underthinking is real too: Wang et al. (2025) found wrong answers
from o1-like models burned 225% more tokens than correct ones, because the model kept
switching strategies instead of finishing one. Skipping and spinning are the same
disease: no supervisor deciding when enough is enough.

## When to use

- The ask is underspecified, or says "figure it out", "do the needful", "just handle it"
- Multi-step work: debugging, migrations, refactors, research, anything over ~5 tool calls
- Long-horizon runs where context has to be managed across many turns
- You notice yourself about to guess, about to re-plan for the third time, about to
  report something unverified, or about to stop while something is half done

## When NOT to use

- The user gave exact steps. Follow them; do not redesign the task.
- A single lookup or one-file change with an obvious correct form. Just do it. Adding
  a loop to a trivial task is itself a failure mode (see Analysis Paralysis below).

## The loop

Run six phases. Each phase produces a written artifact, not a feeling. Writing is the
point: a judgment you cannot state is a judgment the model cannot act on.

| Phase | Question to answer | Artifact |
|-------|--------------------|----------|
| **F** Frame | What exactly is the deliverable, and what would make it wrong? | one-line contract + the 1-3 ways this fails |
| **S** Source | What is the smallest set of facts I need, and where do they live? | the sources, in the order you will read them |
| **D** Decide | Can I settle this myself, or must I ask or escalate? | the branch taken, and why |
| **A** Act | What effort does *this* step deserve? | the action itself |
| **C** Check | What external signal proves it worked? | the command run, file read, or output seen |
| **X** Exit | Done, blocked, or out of depth? | done, or an escalation. No third state. |

The loop is a cycle, not a line: after **C** you usually return to **A**, sometimes to **S**.

## F: Frame before acting

Cheap models start typing. Spend the first few lines of thinking on this instead:

1. **The contract.** One sentence: what artifact exists at the end, and what does
   "correct" mean to the person asking? If you cannot write it, you do not know the task yet.
2. **The kill-risks.** The one to three things most likely to make the result wrong.
   Usually an unknown you have not checked, or an assumption you inherited.
3. **The reversibility.** Which parts can be undone, and which cannot. This drives
   effort in phase **A** more than "importance" does.

Do not turn this into a design essay. Three lines is normal. Ten lines means you are
inventing scope that nobody asked for.

## S: Source just in time

Do not preload everything that might be relevant. Context is a finite attention
budget, and every extra token makes the relevant tokens harder to find. Anthropic's
applied team measured this as *context rot*: as tokens grow, accurate recall drops.
Interference is worse than volume, and prompt-level fixes for it barely work
(Wang et al., 2025, PI-LLM), so the fix is hygiene, not instructions.

Rules:

- **Smallest high-signal set.** Keep references (paths, IDs, queries) and pull the
  content when you need it, instead of dragging whole files into context.
- **Read before you search for what you already have.** Re-reading the task text or a
  file you already opened costs nothing and often answers the question.
- **Stop sourcing when the next read would not change the action.** That is the test.
  Not "have I read enough to feel informed". If the next lookup cannot flip your
  decision, it is optional.
- **Prune as you go.** Once a tool result has served its purpose, drop it from your
  working notes. Old and overwritten values poison later recall.
- **Write durable notes outside the transcript.** A scratch file for state, decisions,
  and open questions beats holding them in your head across forty tool calls.

## D: Decide, ask, or escalate

This is where cheap models lose the most. The DiscoBench benchmark (2026) tested
eleven frontier models on ambiguous multi-hop questions and found the best reached only
43.1% end to end, mostly because of *interaction strategy*, not retrieval:

| Behaviour at an ambiguous point | Checkpoint success |
|---|---|
| Search first, then ask a follow-up | **93.4%** |
| Guess without asking | 56.5% |
| Keep searching, still guess | 51.9% |

Searching harder is worse than guessing. That is the whole lesson: more effort in the
wrong branch is negative value.

**The decision table. Apply it in order and take the first row that matches.**

| Situation | Do this |
|---|---|
| A tool, file, command, or source can settle it | Go get it. Never ask a human for something you can look up. |
| The ambiguity would change the deliverable, and no source can settle it | Ask **exactly one** question: the one whose answer splits the possibilities. |
| The ambiguity is cosmetic; either reading gives the same deliverable | Pick the obvious default, say so in one line, and proceed. |
| You have searched twice and are still guessing | Stop searching. Ask. |

Two more things the same benchmark showed:

- **Detecting ambiguity and asking a good question are different skills.** A prompt
  that told models to watch for ambiguity raised detection F1 from 45.3 to 64.9 but
  barely moved end results (28.6 to 33.7). Awareness is not action. You must go from
  "this is vague" to a specific question in one move.
- **A warning is not a question.** "Could you clarify?" is a wasted turn. Name the
  entities or criteria you cannot distinguish.

**Escalate when you are out of depth, and escalate properly.** Hand over: the goal,
what you established (with evidence), where you got stuck, and the two or three options
you can see. Escalating with nothing is not escalating, it is dumping the task back.
A metacognitive module doing exactly this let a fast model match a much slower
reasoning model at a lower cost (Khandelwal et al., 2025).

## A: Size the effort to the step

Effort is not a personality. It is a per-step allocation, and getting the allocation
wrong in either direction costs you.

- Uniformly low effort costs a lot: an agent dropped nearly **20% accuracy** simply by
  running every step at low reasoning effort instead of high (Yang et al., 2026).
- Uniformly high effort also costs you, through overthinking.
- A per-step router that spends high effort only on hard steps cut reasoning tokens by
  **52.7% with no accuracy loss** on TAU-Bench (Yang et al., 2026).

Triage each step yourself:

| Step type | Effort |
|---|---|
| Trivial, reversible, obvious form | Do it. No plan, no check. |
| Routine, you have done the shape before | One pass, plus one external check. |
| Novel, irreversible, or wide blast radius | Slow path: frame, source, act in small moves, verify each move. |

The discriminator is **reversibility first**. A one-line change to a live config
deserves more care than a thousand-line change to a scratch file.

## C: Check against the environment

Not against your own opinion of your work. Recall the small-model result: self-critique
hurt, grounding helped. Grounding means the outside world answered back.

Weak check (avoid) | Strong check (use)
---|---
"Looks correct to me." | Ran it, exit code 0, output matches expected shape.
"I handled the edge cases." | Fed the edge case in, saw the branch taken.
"Tests should pass." | Ran the tests, read the failures.
"Reads like the requirements." | Diffed against the actual requirement text.

If no external signal is available, say so plainly instead of substituting confidence
for evidence. That is a legitimate answer. Manufacturing certainty is not.

## X: Exit

Stop when the check passes and the contract from phase **F** is met. Then stop. Do not
add unrequested polish, extra abstraction, or a survey of alternatives nobody asked for.

You are also allowed to stop early: if the next action cannot change the deliverable,
you are done.

Three states only: **done**, **blocked with a question**, **escalated**. "Almost done
and still working on it" across many turns is a symptom, not a status.

## The failure modes, with their tells

Both overthinking and underthinking show up as named patterns. Learn the tell, and use
the counter-move. Overthinking patterns are from Cuadron et al. (2025).

| Pattern | Tell | Counter-move |
|---|---|---|
| **Analysis Paralysis** | Third re-plan, no tool call, no file touched | Touch reality. Read the file, run the command. Action beats more reasoning. |
| **Rogue Actions** | Acting past the ask, deleting, overwriting, or editing things never mentioned | Re-read phase **F**. If it is not in the contract, it is not in scope. |
| **Premature Disengagement** | Declaring done or "blocked" while the check has not run | Go to **C**. One check, then decide. |
| **Underthinking** | Strategy-hopping: new approach every few steps, none finished | Pick the most promising line. Finish it. Only then switch. |
| **Search-heavy guessing** | Many tool calls, still guessing at the answer | The DiscoBench 51.9% row. Stop. Ask. |
| **Self-critique spiral** | Reviewing your own reasoning instead of checking the world | Replace with one external observation. |
| **Uniform effort** | Same care on a typo as on a destructive migration | Re-triage in **A**. |
| **Manufactured certainty** | A guess written in the same voice as a verified fact | Label it. "Verified" and "inferred" are different words. |

## Report like an operator

- Lead with the result, then the decision needed from the reader. No survey, no recap.
- Separate what you **verified** from what you **inferred**, in plain words.
- Name uncertainty at the specific point it occurs, not as a general disclaimer.
- Put the long detail in a file or artifact; keep the message short.

## The honest limit

A procedure cannot add capability. Small models (under about 3B) do not reliably
benefit from long chain-of-thought, and one competition-grade study found that *every*
prompt-level intervention failed to close an eight-point capability gap (see
[references/evidence.md](./references/evidence.md)). A skill is a harness, not a brain
transplant.

What a harness reliably does: prevent the self-inflicted losses. Skipping the frame,
guessing instead of asking, spending effort in the wrong place, reporting unverified
work, spinning, and stopping early are all things you can stop doing right now. That
recovery is often the whole gap. When it is not, escalate, and escalate cleanly.

## Related Documents

- [Evidence and sources](./references/evidence.md)
