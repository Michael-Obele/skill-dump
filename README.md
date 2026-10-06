# skill-dump

A collection of agent skills for AI coding assistants (Claude Code, Cursor, GitHub Copilot, Windsurf, Zed, and more).

## Skills

| Skill | Description | Install |
|-------|-------------|---------|
| [conversion-psychology](./skills/conversion-psychology/) | Apply UX psychology principles (Smart Defaults, Goal Gradient, Reciprocity, IKEA Effect, Loss Aversion, Contrast Effect) to design high-converting UI across landing pages, onboarding, pricing, checkout, login flows, CTAs, and modals. Researches live patterns before writing code. | `npx skills add Michael-Obele/skill-dump --skill conversion-psychology` |
| [mobile-product-page-ui](./skills/mobile-product-page-ui/) | Apply proven mobile e-commerce product page UI principles drawn from real redesigns. Use when designing, reviewing, redesigning, or critiquing product detail pages, PDP screens, or mobile shopping experiences. | `npx skills add Michael-Obele/skill-dump --skill mobile-product-page-ui` |
| [naming-psychology](./skills/naming-psychology/) | Name anything — products, packages, MCP servers, features — using cognitive science: 7 principles (fluency, sound symbolism, Von Restorff, emotional encoding, Zeigarnik, serial position, cognitive load), a 35-point scorecard, plus npm/GitHub/web availability checks. Use when the user asks to name or rename something, brainstorm names, or wants naming criteria. | `npx skills add Michael-Obele/skill-dump --skill naming-psychology` |
| [polya-how-to-solve-it](./skills/polya-how-to-solve-it/) | Apply George Pólya's four-phase problem-solving framework from How to Solve It. Use for math, coding challenges, debugging, design decisions, or any non-trivial problem that needs structured thinking. | `npx skills add Michael-Obele/skill-dump --skill polya-how-to-solve-it` |
| [discretion](./skills/discretion/) | Decide and act by default; ask the user only when a decision is truly theirs and hard to reverse. When a question is needed, batch it into a low-load card with a recommended default. Built on research into decision fatigue, cognitive load, choice overload, and one-way doors. | `npx skills add Michael-Obele/skill-dump --skill discretion` |

## Usage

```bash
# Install a specific skill
npx skills add Michael-Obele/skill-dump --skill polya-how-to-solve-it

# List all skills in this repo
npx skills add Michael-Obele/skill-dump --list
```

## License

MIT
