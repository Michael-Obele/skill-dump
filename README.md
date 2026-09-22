# skill-dump

A collection of agent skills for AI coding assistants (Claude Code, Cursor, GitHub Copilot, Windsurf, Zed, and more).

## Skills

| Skill | Description | Install |
|-------|-------------|---------|
| [conversion-psychology](./skills/conversion-psychology/) | Apply UX psychology principles (Smart Defaults, Goal Gradient, Reciprocity, IKEA Effect, Loss Aversion, Contrast Effect) to design high-converting UI across landing pages, onboarding, pricing, checkout, login flows, CTAs, and modals. Researches live patterns before writing code. | `npx skills add Michael-Obele/skill-dump --skill conversion-psychology` |
| [mobile-product-page-ui](./skills/mobile-product-page-ui/) | Apply proven mobile e-commerce product page UI principles drawn from real redesigns. Use when designing, reviewing, redesigning, or critiquing product detail pages, PDP screens, or mobile shopping experiences. | `npx skills add Michael-Obele/skill-dump --skill mobile-product-page-ui` |
| [polya-how-to-solve-it](./skills/polya-how-to-solve-it/) | Apply George Pólya's four-phase problem-solving framework from How to Solve It. Use for math, coding challenges, debugging, design decisions, or any non-trivial problem that needs structured thinking. | `npx skills add Michael-Obele/skill-dump --skill polya-how-to-solve-it` |

## Usage

```bash
# Install a specific skill
npx skills add Michael-Obele/skill-dump --skill polya-how-to-solve-it

# List all skills in this repo
npx skills add Michael-Obele/skill-dump --list
```

## License

MIT
