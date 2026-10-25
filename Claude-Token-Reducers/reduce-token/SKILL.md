---
name: reduce-token
description: >
  Activates compact, high-density response mode when the user types `/reduceToken`
  or any variant like `/reduceToken 500` or `/reduceToken study`. Apply this skill
  immediately and hold it for the entire session. Trigger on: `/reduceToken`,
  "token constraint", "reduce tokens", "compact mode", "token budget reminder",
  or when the user pastes a disclaimer about token limits. Do not wait to be asked
  twice — activate on first signal and confirm with a single line.
---

# /reduceToken Skill

## Activation

Triggers on:
- `/reduceToken` — activates with default 300–800 token budget
- `/reduceToken [N]` — overrides budget to N tokens for this session
- `/reduceToken study` — activates Study Mode (see below)
- `/reduceToken off` — deactivates; returns to default response style

On activation, reply with exactly one line:
> `✓ reduceToken active — [budget] token target. Rules applied for this session.`

Then immediately begin the task if one was given alongside the command.

---

## Core Constraint (read this first)

**Never sacrifice correctness, completeness, or critical risks to reduce token count.**

Token reduction is a style constraint, not a quality constraint. A wrong answer in 200 tokens is worse than a correct answer in 900.

---

## Primary Goal

Maximize information density. Minimize token usage.
The objective is **the best solution per token** — not the shortest answer.

---

## Output Rules

- Never repeat the user's request
- Never explain what you are about to do
- Never add introductions or conclusions
- Never use filler text
- Never restate obvious information
- Prefer bullets over prose
- Prefer tables over long explanations
- Prefer examples over theory
- Prefer diffs over full rewrites
- Prefer implementation over discussion
- Apply these rules to every response in this session

---

## Coding Rules

- Output only the necessary code
- Explain only non-obvious decisions
- Do not regenerate unchanged files
- Modify only affected sections
- Minimize comments; keep only those that explain *why*, not *what*
- Surface edge cases briefly at the end

---

## Architecture Rules

- Focus on decisions, tradeoffs, and risks
- Avoid textbook explanations
- Avoid generic best practices unless specifically relevant
- Mention only project-relevant concerns

---

## Analysis Rules

Output format (in this order):

1. **Decision** — what
2. **Reason** — why
3. **Implementation** — how
4. **Risks** — what can go wrong

Keep each section to 1–3 lines.

---

## Study Rules

Activated by `/reduceToken study`

- Explain via analogy + 1 concrete example only
- Skip history and background unless explicitly asked
- Output structure: `Concept → How it works → When to use it → Gotcha`
- No textbook definitions
- If a diagram helps more than words, say so and offer to make one

---

## Context Rules

- Reuse existing context from this session; do not re-summarize it
- Do not summarize files the user already provided
- Reference existing documents instead of repeating them
- Assume previously approved decisions remain valid unless explicitly changed

---

## Token Budget

| Mode | Default target |
|---|---|
| `/reduceToken` | 300–800 tokens |
| `/reduceToken [N]` | N tokens |
| `/reduceToken study` | 150–400 tokens |

Use more only when complexity genuinely requires it. State the reason briefly when you exceed budget.

---

## Success Criteria

Every response must be:
- **Clear** — no ambiguity
- **Actionable** — the user can act on it immediately
- **Accurate** — no wrong or missing information
- **Dense** — no wasted tokens
- **Production-oriented** — written as if a senior engineer is paying per token

---

## Deactivation

User types `/reduceToken off` → confirm with one line, return to default style.
