---
name: naming-psychology
description: "Name anything — products, packages, MCP servers, features — using cognitive science. Use when the user asks to name something, rename something, brainstorm names, check if a name is good, or wants naming criteria."
---

# Naming Psychology — The Science of Names That Stick

A practical naming system built from cognitive science. Use it to generate, evaluate, and choose names that are memorable, pronounceable, and distinctive — whether for an npm package, an MCP server, a feature, or a company.

> **Core insight:** The best names satisfy multiple psychological principles simultaneously. A name that is fluent + distinctive + emotionally resonant + phonetically aligned will outperform one that only hits one dimension.

## When to Use

- "Name this project / package / feature / MCP server"
- "Is this a good name?" / "Which name is better?"
- "Brainstorm names for X"
- Renaming, rebranding, or choosing between candidates
- Any time a name will be typed, spoken, searched, or remembered

## When NOT to Use

- Internal-only identifiers nobody will say aloud (variable names, branch names)
- User explicitly says "just pick one, don't overthink it"

---

## The 7 Principles

### 1. Processing Fluency — "Can they say it on first sight?"

The single strongest predictor of preference. Easy-to-process names feel more trustworthy, familiar, and valuable — subconsciously.

**Study:** Alter & Oppenheimer (2006, PNAS) — three studies of real US-listed stocks (1990–2004). Shares with pronounceable ticker codes returned **13.45% vs 9.67% after their first day of trading** (NYSE, n = 665, p < .05), and a $1,000 basket of the 10 most *fluently named* companies earned $112 (11.2%) in one day — significantly beating the disfluent basket at every horizon measured. Same fundamentals, different fluency. Caveat from the paper itself: this is an **early-window** effect — the ticker difference stopped being significant beyond day 1.

**Tests:**

- **Pronounceability:** Show the name written to 5 strangers. Can 4+ say it correctly on first try? If not, it has a fluency problem.
- **Spellability:** Say the name aloud. Can they spell it correctly? `Lyft` fails (Y substitution), `Slack` passes.
- **Rhythm:** Trochaic stress (GOO-gle, AP-ple, TWIT-ter — stress on first syllable) matches English's dominant pattern and feels natural.
- **Phonological neighborhood:** Names near common words benefit from existing neural pathways. `Shopify` ← `shop`, `Spotify` ← `spot`.

**Rule:** If someone hesitates before saying your name, fluency is broken. Fix it.

### 2. Sound Symbolism — "Do the sounds match the feeling?"

Speech sounds carry inherent meaning independent of the words they form (Bouba-Kiki effect: ~95% of people map "Bouba" → round shape, "Kiki" → jagged shape — Ramachandran & Hubbard, 2001, after Köhler's 1929 takete/maluma result).

**How solid is it?** The effect replicates across cultures and writing systems — a 25-language study found it robust overall (Cwiek et al. 2022, *Philosophical Transactions of the Royal Society B*), though measurably weaker in Mandarin, Turkish, Romanian and Albanian. It has also been shown in day-old chicks (*Science*, 2024), which suggests the sound→shape mapping is not learned from language. Treat it as a real, cross-cultural prior — not a law.

| Sound family                        | Feels like                | Use for                  | Examples               |
| ----------------------------------- | ------------------------- | ------------------------ | ---------------------- |
| **Front vowels** (I, E — beet, bit) | Small, fast, sharp, light | Precision, speed, tech   | Wii, Visa, Kindle      |
| **Back vowels** (O, U — boot, boat) | Large, powerful, heavy    | Scale, authority         | Google, Roku, Volvo    |
| **Open vowels** (A — father)        | Warm, open, welcoming     | Approachability, breadth | Amazon, Asana, Zara    |
| **Plosives** (B, D, G, K, P, T)     | Energetic, decisive, bold | Impact, action           | Bold, TikTok, Stripe   |
| **Fricatives** (F, S, Sh, V, Z)     | Smooth, sophisticated     | Elegance, flow           | Visa, Zoom, Shazam     |
| **Nasals** (M, N)                   | Warm, comforting          | Care, trust              | Amazon, Noom           |
| **Liquids** (L, R)                  | Fluid, elegant            | Luxury, movement         | Rolls-Royce, Lululemon |

**Rule:** Choose consonants/vowels that match the emotional target. A "harbor" (warm, safe) should not sound like a "bolt" (sharp, fast).

### 3. Von Restorff (Isolation) Effect — "Does it stand out from neighbors?"

Items that break category conventions are remembered better. Every category has naming conventions that make brands interchangeable.

- Law firms → surnames. Banks → "first/national/trust." Tech → abstract nouns.
- Breakthroughs: `Apple` in tech (fruit, not jargon), `Liquid Death` in water (aggression in a gentle category).

**Test:** List 10 competitor names. Does yours visually/phonetically stand out, or does it blur into the list? Distinctiveness drives memorability.

**Rule:** Be distinctive without being random. `Apple` works because simplicity IS the brand. `Banana Law Firm` would just confuse people.

### 4. Emotional Encoding — "Does it make them feel something?"

Emotionally tagged memories are stored deeper and retrieved faster (amygdala + hippocampus).

| Trigger type   | Feeling                | Words                   | Works for               |
| -------------- | ---------------------- | ----------------------- | ----------------------- |
| **Aspiration** | Desire, ambition       | Triumph, Summit, Ascend | Achievement, growth     |
| **Comfort**    | Safety, warmth         | Haven, Harbor, Nest     | Healthcare, home, trust |
| **Energy**     | Excitement, action     | Spark, Bolt, Surge      | Creative, performance   |
| **Wonder**     | Curiosity, exploration | Voyage, Quest, Odyssey  | Discovery, learning     |

**Rule:** Vague emotion ("Good Solutions") creates no memory advantage. Specific emotion ("Haven," "Quilt," "Weave") creates vivid associations. The more specific, the stronger.

### 5. Zeigarnik Effect — "Does it intrigue?"

People remember incomplete tasks better than completed ones. Coined/suggestive names that create slight unfinished meaning prompt ongoing processing.

- `Google` (googol → novel but near a known word) keeps the brain "solving" it.
- `Spotify` (spot + identify) — partial connections, not a full match.
- Invented names like `Scintilo` (scintillate) or `Turmic` (dawn + tech) deliberately engage this.

**Rule:** The sweet spot is _unusual enough to be distinctive, fluent enough to be processed easily_. Pure dictionary words are clear but forgettable; pure gibberish is distinctive but unprocessable.

### 6. Serial Position Effect — "Do the first and last sounds land?"

People remember the first and last items in a sequence best. Openings grab attention; closings linger.

**Strong openings:** Hard consonants (K, B, D, G, T), sibilants (S, Sh), rare initials (Z).
`K`raft, `G`oogle, `T`esla, `S`potify, `B`ose.

**Strong closings:**

- `-a` (Tesla, Zara, Nvidia) — open, modern, international
- `-o` (Volvo, Lego, Cisco) — bold, complete
- `-er` (Twitter, Uber, Docker) — active, agent-like
- Hard stop (Slack, Bolt, Stripe) — decisive, final

**Rule:** Design the opening for attention and the closing for linger. Weak middles are forgiven; weak edges are not.

### 7. Cognitive Load — "Is it short enough to survive?"

Working memory is limited. Every extra syllable/letter costs recall.

- **1-3 syllables** optimal; each additional syllable reduces recall ~10%.
- **4-8 letters** sweet spot for visual processing.
- **Spelling predictability:** If they can't spell it after hearing it once, cognitive load is too high.

**Exceptions:** Luxury/scientific brands sometimes benefit from strategic complexity (Mercedes-Benz > Ford signals premium; Syntheon > Pill signals expertise). But random difficulty is always bad.

**Rule:** Shorter is almost always better. If you can cut a syllable without losing meaning, cut it.

---

## Cross-Cultural Check (for global / npm packages)

1. **Universal phonemes:** /m/, /n/, /p/, /b/, /t/, /d/, /k/, /s/, /a/, /i/, /u/ exist in nearly every language.
2. **Avoid language-specific sounds:** English "th," French "r," Mandarin tones, Arabic pharyngeals.
3. **Check meaning** in Mandarin, Spanish, Hindi, Arabic, Portuguese, Japanese at minimum.
4. **Test pronunciation** with native speakers of different languages — consistent pronunciation = strong global candidate.
5. **Modulation, not absence:** sound symbolism strength varies by language family (weaker bouba/kiki matches in Mandarin, Turkish, Romanian, Albanian — Cwiek et al. 2022), so a name that leans hard on sound symbolism may land differently across markets. Fluency and load checks are universal; sound-symbolism bonuses are cultural.

---

## Devtool / MCP / npm Naming — Additional Rules

Beyond the 7 principles, package/MCP names have extra constraints:

| Rule                                             | Why                                                                                                                            | Example                                                          |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------- |
| **No `sv-` prefix unless the ecosystem owns it** | `sv-` is not a recognized Svelte prefix (unlike `svelte-*`); it adds a syllable and hurts fluency                              | `weave-mcp` > `sv-weave-mcp`                                     |
| **Avoid `mcp` in the base name if possible**     | `mcp` is a transport detail, not the product; it dates the name                                                                | `haven` > `haven-mcp` (use `-mcp` only as npm suffix if needed)  |
| **Metaphor > description**                       | `Vite` (fast in French), `Prisma` (prism), `Turborepo` (turbo) — metaphors are distinctive; `svelte-component-registry` is not | `quilt` (weaving pieces together) > `svelte-registry-aggregator` |
| **Check npm + GitHub + domain**                  | A name available on npm but taken on GitHub creates confusion                                                                  | `curl -s https://registry.npmjs.org/<name>` → 404 = available    |
| **One strong word > two weak words**             | `Stripe`, `Vercel`, `Supabase` — single-word names have lower cognitive load and stronger Von Restorff                         | `haven` > `registry-haven`                                       |
| **Say it in a sentence**                         | "Add it with `npx haven`" should sound natural                                                                                 | Test: "I use \_\_\_ for Svelte components"                       |

---

## Language Inspiration — Project Preferences

This project has a deliberate language palette. Apply it when generating candidates:

> **Optional local asset:** if you keep a searchable dump of a heritage-language dictionary (e.g. `assets/<language>-dictionary.txt` produced with `pdftotext -layout`), mine it with `grep -inE "mail|letter|message|news|listen|speak|..."` **before** inventing roots — an attested word beats a made-up one. Keep already-mined reserve lists in the calling project's `naming.md`, and don't commit third-party dictionary texts to public repos.

| Preference                 | Rule                                                                                                                                                                                                                                                                  | Why                                                                                                                                                                                 |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **African → Ijaw only**    | For any African-language inspiration, use **Ijaw (Ijo)** — not Yoruba, Igbo, Hausa, or other Nigerian languages. Ijaw is the heritage language (e.g., `Aghara` = town crier).                                                                                          | Consistency, personal story, and distinctiveness — Ijaw is underrepresented in tech naming, so Von Restorff is high. Other Nigerian languages are crowded and dilute the narrative. |
| **Non-European preferred** | Beyond Ijaw, prefer **Chinese, Japanese, and other non-European** sources over European (no French, Latin, Greek, German, etc. for new names). Existing European loans like `Vite` are grandfathered, not a pattern to repeat.                                        | European tech names are wallpaper (`nova`, `luna`, `aura`). Non-European roots stand out and signal intentional curation.                                                           |
| **Fluency still vetoes**   | Any Ijaw/Chinese/Japanese candidate must still pass **Processing Fluency** (pronounceable on first sight, spellable after hearing once). If the authentic word is hard, use a **shortened or adapted form** that preserves the root and passes the 4/5 stranger test. | A beautiful meaning that nobody can say is a failed name. Adapt, don't force.                                                                                                       |
| **Provide the story**      | Every non-English candidate must ship with a one-line gloss: `word (language — meaning)`. The story IS the emotional encoding.                                                                                                                                        | `Aghara (Ijaw — town crier)` and `Souk (Arabic — marketplace)` work because the gloss is specific and vivid. A name without its story is just a sound.                              |

**How to use:** When the brief allows non-English inspiration, generate 1/3 of candidates from your heritage language, 1/3 from Chinese/Japanese, 1/3 from metaphor families. Score all on the same 7-principle scorecard — language origin does not excuse a low fluency or load score.

## Availability & Discoverability — The "Truly Free" Test

A name that scores 35/35 but is unownable is a failed name. Check **three surfaces** — npm, GitHub, and the open web — before ranking. A collision on any surface is a discoverability tax you pay forever.

### 1. npm — `curl -s https://registry.npmjs.org/<name>`

- `404` = available (ownable as base). `200` = taken — read `description` to see if it's a real package or a squat.
- Also check the `-mcp` suffix variant if you need it (`souk` vs `souk-mcp`). Prefer owning the base; `-mcp` is a transport suffix, not the product.
- Check `https://registry.npmjs.org/-/v1/search?text=<name>&size=5` for near-matches that will clutter `npm search`.

### 2. GitHub — three checks (all required)

A name can be blocked on GitHub in two different ways — check both, plus the global ranking:

- **(a) Your repo — can you create it?** `curl -s -o /dev/null -w "%{http_code}" https://github.com/<YOUR_ORG>/<name>` and `https://api.github.com/repos/<YOUR_ORG>/<name>` — `404` = you can create `YOUR_ORG/<name>`. This is **availability**.
- **(b) Any repo with that exact name — does one exist anywhere?** `curl -s "https://api.github.com/search/repositories?q=<name>+in:name&per_page=5"` — inspect `total_count` and top hits. A repo like `jiayj007/sousuo` (even at 0★) means the bare word is already a repo name somewhere. Check `https://github.com/<name>` (bare user/org) too — `200` = a user/org squats the term. This is **collision**.
- **(c) Global ranking — will you be buried?** Web-search `<name> site:github.com` (any search tool) or open `https://github.com/search?q=<name>&type=repositories` — look for dominant repos (1k+★) that will own the first page forever (e.g., `cinder` → `github.com/cinder/Cinder` 5.5k★). This is **discoverability**.
- **Verdict:** (a) must be 404 to ship. (b) at 0★/low activity is Yellow (winnable — you outrank it with stars/docs), at 1k+★ is Red (dominated). (c) dominated = veto regardless of 7-principle score.

### 3. Web — open-web search

- **Run:** search `"<name>"` with your web-search tool, 8 results — inspect the top 5. Are they the word's dictionary meaning, a dominant brand, or unrelated noise?
- **Rank signal:**
  - **Green (ownable):** Top results are dictionary/Wiktionary, weak blogs, or unrelated small projects — you can own page 1 with a good README + npm + GitHub repo.
  - **Yellow (contested):** Top results include a mid-size product or common word with many meanings — winnable but needs SEO work.
  - **Red (dominated):** Top results are a major brand, framework, or Wikipedia with strong authority — you will never outrank it. Pick a different name.
- **Also check:** `"<name> npm"` and `"<name> mcp"` to see if an npm/GitHub collision already dominates the devtool-specific search.

### Discoverability Score (add to ranking)

After the 7-principle score (/35), add a **Discoverability bonus/penalty** when ranking finalists:

| Signal                  | npm                                 | GitHub               | Web                             | Bonus                          |
| ----------------------- | ----------------------------------- | -------------------- | ------------------------------ | ------------------------------ |
| **Truly free**          | 404 base                            | No dominant repo     | Green (dictionary/weak)         | **+3** — you own the term      |
| **Ownable with suffix** | Base taken, `-mcp` 404              | No dominant repo     | Green/Yellow                    | **+1** — suffix saves you      |
| **Contested**           | 404 but near-matches clutter search | Mid-size collisions  | Yellow                          | **0** — winnable with effort   |
| **Dominated**           | Taken or major framework owns term  | Dominant repo (1k+★) | Red (brand/Wikipedia/framework) | **-3** — pick a different name |

**Rule:** Discoverability is a **veto at -3**. A dominated term is out regardless of its 7-principle score — you will never be found. Between two names with equal 7-principle scores, the higher discoverability wins.

## Evaluation Scorecard

Score each candidate 1-5 on each principle. Total out of 35.

| #   | Principle          | 1 (weak)                                            | 5 (strong)                      |
| --- | ------------------ | --------------------------------------------------- | ------------------------------- |
| 1   | Fluency            | Hesitation to pronounce/spell                       | Instant, no thought needed      |
| 2   | Sound Symbolism    | Sounds contradict the feeling                       | Sounds ARE the feeling          |
| 3   | Von Restorff       | Blurs with competitors                              | Nothing else sounds like it     |
| 4   | Emotional Encoding | No feeling, or vague                                | Specific, vivid emotion         |
| 5   | Zeigarnik          | Fully understood and forgettable, or pure gibberish | Intriguing, keeps processing    |
| 6   | Serial Position    | Weak/mushy opening or closing                       | Strong grab + strong linger     |
| 7   | Cognitive Load     | 4+ syllables, hard to spell                         | 1-2 syllables, obvious spelling |

**Interpretation:**

- **30-35:** Exceptional — ship it
- **25-29:** Strong — minor polish
- **20-24:** Usable — has a weakness to address
- **<20:** Rethink — likely has a fluency or distinctiveness problem

---

## Practical Workflow

### Generating names

1. **Define the emotional target first.** What should the name FEEL like? (Warm/safe? Fast/sharp? Crafted/curated? Expansive?)
2. **Pick a metaphor family** that matches the feeling:
   - _Gathering/curation:_ bazaar, souk, emporium, arcade, gallery, trove, pantry, depot
   - _Weaving/connecting:_ weave, loom, quilt, mosaic, tapestry
   - _Shelter/trust:_ haven, harbor, atrium, hearth
   - _Navigation/discovery:_ compass, atlas, beacon, lodestar
   - _Craft/building:_ forge, foundry, kiln, studio
3. **Generate 10-15 candidates** within the chosen family. Favor 1-2 syllables, universal phonemes, strong openings/closings.
4. **Score each** on the 7-principle scorecard. Keep the top 3-4.
5. **Check availability & discoverability (three surfaces):**
   - **npm:** `curl -s https://registry.npmjs.org/<name>` (404 = available) + `/-/v1/search?text=<name>` for near-matches
   - **GitHub:** direct probe + global search (`<name> site:github.com`)
   - **Web:** search `"<name>"` — Green/Yellow/Red per Availability & Discoverability section
     Score discoverability (+3 to -3) and apply veto at -3.
6. **Fluency test:** Show written name to 5 strangers, say it aloud to 5 others. 4+/5 must pass both.
7. **Sentence test:** "I use **_ for Svelte components" / "Add it with `npx _**`" — does it sound natural?

### Choosing between finalists

- Highest scorecard total wins, but **fluency is a veto** — a name that fails pronounceability/spellability is out regardless of other scores.
- If tied, prefer: shorter > longer, metaphor > description, single word > compound, universal phonemes > language-specific.

---

## References

- Alter & Oppenheimer (2006) — "Predicting short-term stock fluctuations by using processing fluency," *PNAS* 103(24) 9369–9372 — [doi:10.1073/pnas.0601071103](https://doi.org/10.1073/pnas.0601071103)
- Ramachandran & Hubbard (2001) — Bouba-Kiki effect refinement (after Köhler 1929)
- Cwiek et al. (2022) — "The bouba/kiki effect is robust across cultures and writing systems," *Phil. Trans. R. Soc. B* 377(1841) 20200390
- Matching sounds to shapes: evidence of the bouba-kiki effect in naïve baby chicks (2024) — [doi:10.1126/science.adq7188](https://doi.org/10.1126/science.adq7188)
- Zajonc (1968) — Mere exposure effect
- Von Restorff (1933) — Isolation effect
