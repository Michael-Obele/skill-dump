---
name: polya-how-to-solve-it
description: Apply George Pólya's four-phase problem-solving framework from How to Solve It (1945). Use when tackling math problems, coding challenges, debugging, design decisions, algorithms, or any non-trivial problem that needs structured thinking. Triggers include problem solving, how to solve it, Polya method, understand the problem, devise a plan, carry out the plan, look back, heuristics, working backwards, analogy.
---

# Pólya's How to Solve It Framework

Apply this systematic yet flexible four-phase approach whenever a problem is non-trivial. Originally written for mathematics, the method generalizes to coding, debugging, system design, research, and everyday decisions.

The phases are not rigid stages. Understanding evolves. Plans change. You will often loop back. Flexibility is essential.

## The Four Phases

### 1. Understand the Problem

Do not start solving until the problem is clear.

Key questions:
- What is the unknown (what are we trying to find or achieve)?
- What are the data (what is given)?
- What is the condition (constraints, requirements, relationships)?
- Is the condition sufficient to determine the unknown? Insufficient? Redundant? Contradictory?
- Can you restate the problem in your own words?
- Can you draw a figure, diagram, or introduce suitable notation?
- Separate the various parts of the condition. Can you write them down?

Practical actions:
- Restate the goal and constraints clearly.
- Identify assumptions and missing information.
- For code/debugging: reproduce the issue, note exact error messages, inputs, expected vs actual behavior.
- For design: clarify success criteria and non-goals.

### 2. Make a Plan (Devise a Plan)

This is usually the hardest phase. The goal is to find the connection between the data and the unknown.

Core questions:
- Have you seen this problem before? Or a similar one in a slightly different form?
- Do you know a related problem? A theorem, algorithm, pattern, or technique that could be useful?
- Look at the unknown. Think of a familiar problem that has the same or a similar unknown.
- Here is a problem related to yours and solved before. Could you use it? Could you use its result? Could you use its method?
- Should you introduce some auxiliary element to make the connection clearer?
- Could you restate the problem differently?
- Go back to definitions.
- If you cannot solve the proposed problem, try to solve first some related problem. Could you imagine a more accessible related problem? A more general problem? A more special problem? An analogous problem?
- Could you solve a part of the problem? Keep only a part of the condition, drop the other part. How far is the unknown then determined? How can it vary?
- Could you derive something useful from the data? Could you think of other data appropriate to determine the unknown?
- Could you change the unknown or the data, or both if necessary, so that the new unknown and the new data are nearer to each other?
- Did you use all the data? Did you use the whole condition? Have you taken into account all essential notions involved in the problem?

Useful heuristics (strategies):
- Analogy — solve a similar problem and adapt the approach
- Generalization / Specialization — broaden or narrow the problem
- Working backwards — start from the desired result and work toward the given data
- Decomposition — break into smaller sub-problems
- Auxiliary elements — introduce helpful variables, constructions, or intermediate results
- Look for a pattern
- Draw a diagram or make a table
- Guess and check / trial and error (with reflection)
- Solve a simpler related problem first
- Use symmetry or invariance
- Consider extreme or special cases

For coding and engineering:
- Search for existing solutions, libraries, or design patterns that match the shape of the problem.
- Sketch the data flow or state machine before writing code.
- Identify the core algorithm or data structure needed.
- Consider edge cases early as part of the plan.

### 3. Carry Out the Plan

Execute the plan carefully and patiently.

Key practices:
- Check each step. Can you see clearly that the step is correct? Can you prove it is correct?
- Persist with the chosen plan long enough to give it a fair chance.
- If the plan is not working, abandon it cleanly and return to phase 2 (or even phase 1). Do not force a failing approach.
- Keep the overall outline in view while filling in details.
- For code: implement incrementally, test small pieces, verify invariants as you go.

### 4. Look Back (Review and Reflect)

After obtaining a solution, examine it.

Key questions:
- Can you check the result? Can you check the argument?
- Can you derive the result differently? Can you see it at a glance?
- Can you use the result, or the method, for some other problem?
- Is the solution reasonable? Does it satisfy all the original conditions?
- Is there a simpler or more elegant way?
- What did you learn that can transfer to future problems?

Practical actions:
- Verify correctness against the original problem statement and edge cases.
- Refactor or simplify if a cleaner path is now visible.
- Document the key insight or the general technique for later reuse.
- For code: add tests that capture the hard cases you discovered, note any remaining limitations.

## Important Mindset Notes from Pólya

- Your initial understanding of a complex problem is usually incomplete. Expect it to evolve.
- Be willing to change your point of view. Shift perspective as you learn more through trial and error.
- The divisions between the four phases are not sharp. You may move back and forth many times.
- A bright idea may appear suddenly; preparation and patient work make those moments more likely.
- Teaching or explaining the solution to someone else is one of the best ways to deepen understanding (look-back phase).

## When to Apply This Skill

- Mathematical or algorithmic problems
- Debugging sessions where the root cause is unclear
- System design or architecture decisions
- Research or open-ended investigation tasks
- Any situation where jumping straight to implementation has previously led to wasted effort

Do not force the full formal checklist on trivial problems. Use judgment. The value is in the disciplined thinking, not in mechanical ceremony.

## Source

George Pólya, *How to Solve It: A New Aspect of Mathematical Method* (Princeton University Press, 1945). The book remains in print and has been translated into many languages. Its short dictionary of heuristics is especially valuable for generating alternative approaches when stuck.
