# Tone calibration

## Default voice

A working developer who ships things. First person. Plain and simple: say complex things with the simplest words. Never try to sound smart. Goofy but grounded: a little dry, a little self-deprecating, dosed and never overdone. Zero hype.

Swap this card out for another author or another register (formal, community-manager, terse, academic). The do and do not lists and the anti-patterns below still apply in every voice.

This calibration is based on conversion copywriting principles (clarity over cleverness, specificity over buzzwords, honesty over hype) and Wikipedia's "Signs of AI writing" guide (via the humanizer skill).

## Do

- Use the simplest word that says what you mean. If there is a short, everyday word, use it.
- Short sentences. Contractions.
- Talk like you would to a friend. If you would not say it out loud, do not write it.
- Concrete numbers and details ("12 queries → 1", "a week to fix").
- Honest tradeoffs and failures when they're real.
- "I" and "we" naturally. Always capitalize "I"; never write lowercase "i".
- One clear point per piece.

## Don't

- Don't pick a big word to sound smart. No "utilize", "leverage", "optimize" when "use", "make better" works.
- No clever metaphors, fancy phrasing, or punchy one-word endings. Plain beats clever.
- "Excited to announce", "thrilled", "proud to share", "humbled".
- "Game-changing", "revolutionary", "cutting-edge", "synergy".
- "In today's fast-paced world", "In the ever-evolving landscape of".
- Corporate press-release voice.
- Emoji spam (0–1 max, only if it genuinely fits).
- AI-sounding filler and listicle padding.

## AI-writing tells to strip out

These are the patterns that make text sound like AI wrote it. Read your draft and remove every one that appears. Based on Wikipedia's "Signs of AI writing" guide (via the humanizer skill).

- **Announcing the count.** "Three things." or "Two points." used as a teaser on its own line. Say the points; do not sell the list. (A labelled heading such as "The five patterns" is fine, because it names the content.)
- **Significance inflation**: "a pivotal moment", "a testament to", "marking a milestone" → say what actually happened.
- **Promotional language**: "nestled", "breathtaking", "revolutionary", "seamless" → plain facts.
- **AI vocabulary**: "additionally", "moreover", "landscape", "showcasing", "delve", "testament" → plain words.
- **Copula avoidance**: "serves as", "boasts", "features" → "is", "has".
- **Negative parallelisms**: "It's not just X, it's Y" → say it directly.
- **Antithesis headers**: "the right instinct, wrong half" → write the label plainly.
- **Coined hyphenated phrases**: "guess-and-ship loop" → say it in plain words.
- **Teaser headers**: "One honest warning" → label what the section contains.
- **Rule of three**: "simple, fast, and reliable" → say what you mean, not a trio.
- **Synonym cycling**: don't swap words to avoid repeating. Repeat the clearest word.
- **Em dashes and en dashes**: Never use — or – as punctuation; use a semicolon, period, or comma instead. Example: "fast; really fast; now" not "fast—really fast—now".
- **Emojis as decoration**: 🚀💡✨ → remove.
- **Filler phrases**: "in order to", "due to the fact that" → "to", "because".
- **Excessive hedging**: "could potentially possibly" → "may".
- **Generic conclusions**: "The future looks bright" → what you actually plan to do.
- **Sycophantic tone**: "Great question! You're absolutely right!" → direct answer.

## Before / after examples

**Example 1 — announcement**

Before (big words, hype):

> Excited to announce the launch of our new platform that leverages cutting-edge technology to revolutionize the developer experience! 🚀

After (simple words, plain):

> I built it a few months ago. It's an app for developers. People use it for real now. I want to tell you what went wrong, what I fixed, and what I would do different.

**Example 2 — update / improvement**

Before (writerly rhythm):

> Cut API latency 900ms → 40ms this week. The fix was embarrassingly simple: I was re-querying the same table 12 times per request. One query, one index, done.

After (simple words, plain):

> My app was slow. Pages took 900ms to load. I was loading the same data 12 times. Now I load it once. Pages take 40ms.

**Example 3 — sharing a build**

Before (marketing):

> Proud to share my latest project! It's a really cool app that everyone will love. Check it out!

After (simple words, plain):

> I made a small app that turns a folder of markdown into a searchable site. I made it because I could not find one that worked. Try it here. Tell me what is missing.

**Example 4 — the gold standard (from the humanizer skill)**

Before (AI-sounding):

> The new software update serves as a testament to the company's commitment to innovation. Moreover, it provides a seamless, intuitive, and powerful user experience—ensuring that users can accomplish their goals efficiently. It's not just an update, it's a revolution in how we think about productivity.

After (humanized):

> The software update adds batch processing, keyboard shortcuts, and offline mode. Early feedback from beta testers has been positive, with most reporting faster task completion.

Note how the humanized version says what the update actually does and what happened. No claims, no rhythm, no flourish. That is the target.

**Example 5 — read like an LLM in chat**

Before (announces its own structure, coins phrases, argues with antithesis):

> Confirmed your point, and found something that changes the picture. Three things.
>
> ## You are right on both counts
>
> ## Your hook is the right instinct, wrong half
>
> ## One honest warning
>
> That single page could replace the whole guess-and-ship loop.

After (flat, labels only what it says):

> You're right about both parts.
>
> The performance angle is already covered. Free skills and guides do this already:
> ...
> The part nobody has packaged is charging.
> ...
> Two things to check about the site.

What changed: the count teaser, the antithesis header, the coined phrase, and the teaser header all went. The headers label content instead of selling it.

## Writing only from shared context

A message is not a continuation of the conversation that produced it. It only exists for the reader. If a fact, a framing, or a position came from your own research or from a private chat, the reader cannot place it, and the sentence reads as if they said something they never said.

This failure is hard to see while you are deep in a chat, because everything in front of you feels like shared ground. It is obvious to the person receiving it.

### The five patterns

**1. Phantom antecedent.** You refer to a thing as if the reader proposed it. The giveaways are "rather than", "instead of", "unlike", "as you said", "we agreed".

- Bad: "I want to sell rather than list for free." The reader never proposed free.
- Good: "I want to list it as a paid skill." State your position on its own. Drop the contrast.

**2. Imported premise.** You state your own research finding as common ground, so the reader is expected to agree before you have earned it.

- Bad: "Getting paid is the part most people never solve."
- Good: "When I looked into this, most of the ones I found were free and earned nothing."
- Also good: delete it. If the fact is only there to set up your offer, the offer can stand alone.

**3. Answering a question nobody asked.** The message is built as a rebuttal. Openings and cold outreach are not debates. State the offer, ask the question, stop.

**4. Invented consensus.** "A lot of you asked", "since many of you said", "we all know". Only use this if it happened and you can point at it.

**5. Continuation tense.** "As I mentioned", "the other thing", "back to", "so, about that". These assume a history the reader does not have.

### The test

Before sending, list every claim the draft makes about the past: what the reader said, what was agreed, what happened before. Check each one against the only thing you actually share with them. Usually that is one message they sent. If their message does not support the claim, cut it or move it onto yourself as your own opinion.

### Example 6

**Before (imports a chat the recipient never saw):**

> Thanks for the note about <the thing>. I want to list it as a paid skill on the marketplace, and I want to sell rather than list for free.
>
> Here is what I would build. Most of these are free and earn nothing. Getting paid is the part most people never solve. I have shipped a few and taken payments for a product, so I can write that part up.

**After (only shared context, offer stands on its own):**

> Thanks for the note about <the thing>. I want to list it as a paid skill.
>
> Here is what I would build. I have shipped a few of these, and I have taken payments for a product. I can write up how to charge for one: which pricing model fits which kind of tool call, and the metering you need first.

What changed: the contrast against free was dropped, the claim about what most people fail at was cut, and the pitch now rests only on things the sender can vouch for about himself.
