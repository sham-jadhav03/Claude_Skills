# Claude Token Reducers

> A collection of Claude skills and tools to maximize information density and minimize token usage — without sacrificing accuracy.

---

## Skills

### `/reduceToken`

A Claude skill that activates compact, high-density response mode on command.

**The problem it solves:** Every session you copy-paste a long disclaimer asking Claude to be concise. This skill replaces that entirely — one command, session-wide effect.

#### Commands

| Command | Effect |
|---|---|
| `/reduceToken` | Default mode — 300–800 token budget |
| `/reduceToken [N]` | Custom budget — e.g. `/reduceToken 500` |
| `/reduceToken study` | Study mode — 150–400 tokens, concept-first format |
| `/reduceToken off` | Deactivates, returns to default Claude style |

#### What it enforces

- No filler, no preamble, no re-stating your question
- Bullets over prose, tables over explanations, diffs over rewrites
- Code: only changed files, minimal comments
- Analysis: Decision → Reason → Implementation → Risks
- Study: Concept → How it works → When to use it → Gotcha

#### Core rule

> **Never sacrifice correctness, completeness, or critical risks to reduce token count.**
> Token reduction is a style constraint, not a quality constraint.

---

## Installation

### Option A — Claude Desktop (recommended for daily use)

Claude Desktop loads skills from a local folder it watches automatically.

**macOS / Linux**
```bash
# 1. Clone the repo
git clone https://github.com/sham-jadhav03/Claude-Token-Reducers.git

# 2. Copy the skill into Claude Desktop's skills folder
mkdir -p ~/.claude/skills
cp -r Claude-Token-Reducers/reduce-token ~/.claude/skills/
```

**Windows**
```powershell
# 1. Clone the repo
git clone https://github.com/sham-jadhav03/Claude-Token-Reducers.git

# 2. Copy the skill into Claude Desktop's skills folder
mkdir "$env:APPDATA\Claude\skills" -Force
Copy-Item -Recurse Claude-Token-Reducers\reduce-token "$env:APPDATA\Claude\skills\"
```

3. Restart Claude Desktop
4. Type `/reduceToken` in any chat — skill activates instantly

> **Tip:** To update the skill later, just `git pull` in the repo folder and restart Claude Desktop.

---

### Option B — Claude.ai (browser)

1. Go to **claude.ai → Settings → Skills → Install**
2. Upload `reduce-token/SKILL.md`
3. Type `/reduceToken` to activate

---

### Option C — Claude Code

Add to your project's `CLAUDE.md`:
```
Read .claude/skills/reduce-token/SKILL.md and apply its rules whenever the user types /reduceToken.
```
Then copy the skill:
```bash
mkdir -p .claude/skills
cp -r reduce-token .claude/skills/
```

---

### Option D — Manual (no install, any session)

Paste the raw contents of [`reduce-token/SKILL.md`](./reduce-token/SKILL.md) at the start of any chat. Works on Claude.ai, Claude Desktop, or any Claude API client.

---

## Usage examples

```
/reduceToken
Review this Python function and suggest improvements.
```

```
/reduceToken 500
Explain how Redis pub/sub works.
```

```
/reduceToken study
What is a transformer attention mechanism?
```

---

## Skills

| Skill | Command | Purpose |
|---|---|---|
| reduce-token | `/reduceToken` | Compact, dense responses — eliminates filler, enforces token budgets |
| oa | `/oa` | Deep Problem Solver — 7-phase DSA/algorithm framework, trap detection |

---

## Project structure

```
Claude-Token-Reducers/
├── README.md
├── LICENSE
├── reduce-token/
│   └── SKILL.md        ← token budget + compact mode skill
└── oa/
    └── SKILL.md        ← deep problem solver skill
```

---

## Contributing

PRs welcome. If you build a new token-reduction skill (e.g. `/reduceToken code`, `/reduceToken review`), open a PR with:
- A new folder under the root
- A `SKILL.md` following the same format
- A section added to this README

---

## License

MIT — see [LICENSE](./LICENSE)
