# Evidence behind `discretion`

Each entry gives the finding, the source, and the rule it justifies. Where a finding is contested, it says so. Prefer the primary sources when a claim matters.

## Decision fatigue

A long session of decisions degrades decision quality: people become reluctant to make trade-offs, lean on defaults and the status quo, delay or avoid deciding, and get more impulsive. Danziger, Levav & Avnaim-Pesso (2011) found parole rulings grew harsher across a decision session and reset after a break.

- Source: Tierney, "Do You Suffer From Decision Fatigue?" (NYT Magazine, 2011); Vohs & Baumeister (2008); Danziger, Levav & Avnaim-Pesso, PNAS 108(17), 2011. Overview: https://en.wikipedia.org/wiki/Decision_fatigue
- **Contested:** the underlying "ego depletion" effect failed a 23-lab replication (Hagger et al., 2016), and Dweck and colleagues found depletion mainly hits people who *believe* willpower is finite (Job, Dweck & Walton, 2010).
- **Rule:** cut *unnecessary* decisions and interruptions. Don't treat the user as fragile, and don't manufacture fatigue by dripping questions. Defaults are powerful because depleted people take them.

## Cognitive load

Working memory is tiny (Miller's ~7±2; modern estimates nearer 4, Cowan 2001). Cognitive load theory splits load into intrinsic (the task), extraneous (how it's presented), and germane (schema-building). The presenter controls extraneous load.

- Source: Sweller (1988) cognitive load theory; Miller (1956); Cowan (2001). Overview: https://en.wikipedia.org/wiki/Cognitive_load
- **Rule:** reduce extraneous load, not the decision. Clean, scannable question cards; no redundant framing; batch related asks so context is carried once.

## Choice overload (overchoice)

Choosing among many roughly equal options is demotivating and lowers satisfaction (inverted-U). Iyengar & Lepper's jam study is the classic result. But meta-analyses show the effect is conditional: it needs no prior preference, no dominant option, and low familiarity. A clearly superior option, or an expert chooser, cancels it. Overload also **reverses** when choosing for someone else.

- Sources: Iyengar & Lepper (2000); Chernev, Böckenholt & Goodman (2015); Scheibehenne, Greifeneder & Todd (2010); Polman (2012). Overview: https://en.wikipedia.org/wiki/Overchoice
- **Rule:** always give a recommended option. A dominant default means the user isn't weighing equals, so overload doesn't apply. This is why "here's my pick" beats "here are your options."

## Hick's law

Decision time grows with the number of choices (logarithmically for clean sets). Fewer options, faster and easier.

- Source: Hick (1952); Hyman (1953). Overview: https://en.wikipedia.org/wiki/Hick%27s_law
- **Rule:** ≤4 options, prefer binary/ternary.

## Satisficing vs. analysis paralysis

Simon's bounded rationality: people "satisfice" (take the first option past an acceptability threshold) rather than optimize. Maximizers seek more options and end up less happy. At the extreme, over-analysis blocks action entirely (analysis paralysis).

- Sources: Simon (1956, 1979); Schwartz et al. (2002). Overviews: https://en.wikipedia.org/wiki/Satisficing , https://en.wikipedia.org/wiki/Analysis_paralysis
- **Rule:** aim for "good enough, reversible" over "optimal." Don't force the user to optimize; let them accept a sensible default.

## Progressive and staged disclosure

Show the few core options first; disclose the rest on request. People understand a system better when you prioritize for them.

- Source: Nielsen, "Progressive Disclosure" (NN/g, 2006). https://www.nngroup.com/articles/progressive-disclosure/
- **Rule:** in a question, lead with the recommendation and the two real alternatives; keep detail behind "want the reasoning?"

## One-way vs. two-way doors

Bezos's heuristic: a two-way door is a reversible decision — make it fast. A one-way door is hard to reverse — slow down and be deliberate. Confusing the two is the expensive mistake.

- Source: Amazon, Letter to Shareholders (2015). https://www.aboutamazon.com/about-us/shareholder-letters
- **Rule:** reversibility, not size, decides whether to ask. See The Gate, check 2.

## Human–AI interaction guidelines

Guideline sets for human-AI interaction converge on: be clear about what the system can do and why it acted, support efficient correction and dismissal, and scope services conservatively when the system is unsure.

- Source: Amershi et al., "Guidelines for Human-AI Interaction," CHI 2019; Microsoft HAX Toolkit. https://www.microsoft.com/en-us/haxtoolkit/
- **Rule:** The Tell format (what changed, why, how to override) is the "make clear why it acted" guideline. Silently deciding badly is as much a failure as over-asking.

## Existing pattern in this skill set

The `grilling` skill already states the split this skill leans on: *facts are the agent's job, decisions are the user's*, and a round of questions is batched with a recommended answer for each. `discretion` generalizes that beyond an interview to everyday decisions: default to acting, and use the same "recommend + batch" shape whenever a question is genuinely needed.
