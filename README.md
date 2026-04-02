# /lets-cook

**Turn AI wishlists into battle-tested plans.**

An open [Agent Skill](https://agentskills.io) that forces your AI to research, challenge, and stress-test before planning — instead of confidently guessing.

## The problem

You ask an AI to plan a project. It gives you a confident, detailed plan. You build it. Then you discover a competitor with 1M users already did the same thing, your tech stack assumption was wrong, and nobody checked the legal risk.

The AI wasn't lying. It was confidently wrong. And you had no process to catch it.

## What /lets-cook does

Two passes. Pass 1 builds a rigorous plan. Pass 2 tries to destroy it.

**Pass 1 — Build (7 steps):**

| Step | What it forces |
|------|---------------|
| Commit | Name your assumptions before you get confident |
| Bound | Set budget, constraints, explicit no-gos |
| Research | Find 5-8 real competitors with web search |
| Decompose | Break into sub-systems with dependency graph |
| Challenge | Test 5 assumptions at 50-80% confidence |
| Gaps | Surface decision, error, and preference gaps |
| Cut & Commit | MVP scope, Go/No-Go gates, kill criteria |

**Pass 2 — Break (4 lenses):**

| Lens | What it tests |
|------|--------------|
| Adversarial | 3 biggest weaknesses with concrete fixes |
| Domain Expert | What only someone who built this would know |
| User Personas | 3 users: primary, edge case, buyer |
| Pre-mortem | 12 months later, it failed — why? |

After both passes, a **Pipeline Report** shows what was done, what changed, and what to do next.

## Results: same AI, wildly different output

We tested with Claude Haiku (cheapest model). Same question: "Plan a browser-based creature-battler game."

|  | Casual | /lets-cook |
|--|--------|-----------|
| **Cost** | $0.03 | $0.14 |
| **Competitors found** | 0 | 8 |
| **Assumptions named** | 0 | 5 |
| **Kill criteria** | 0 | 3 |
| **Personas tested** | 0 | 3 |
| **Pre-mortem** | No | Yes |
| **Legal risk caught** | No | Yes |
| **Decisions reconsidered** | 0 | 9 |

For $0.11 more, the AI caught a legal risk, discovered a competitor with 1M users, and reconsidered 9 decisions it would have gotten wrong.

## Install

### Claude Code

```bash
# Copy to your skills directory
cp -r lets-cook ~/.claude/skills/
```

### Any Agent Skills-compatible tool

Works with Claude Code, Codex, Gemini CLI, Cursor, VS Code Copilot, and [30+ other tools](https://agentskills.io) that support the Agent Skills spec.

```bash
# Clone and copy the skill folder
git clone https://github.com/gabrielvani/lets-cook-skill.git
cp -r lets-cook-skill/lets-cook ~/.claude/skills/
```

## Usage

Just tell your AI:

```
/lets-cook

Plan a real-time multiplayer quiz app
```

Or for stress-testing an existing plan:

```
/lets-cook (Pass 2 only)

Review this plan: [paste your plan]
```

### Modes

| Situation | What to run |
|-----------|-------------|
| New project idea | Full protocol (Pass 1 + Pass 2) |
| Have a plan, want to stress-test | Pass 2 only |
| Quick sketch, low stakes | Pass 1 only |
| Exploring whether to build at all | Steps 1-3 only |

## How it works

/lets-cook introduces **deliberate friction** at every point where LLMs naturally cut corners:

| Where AI skips | What /lets-cook forces |
|----------------|----------------------|
| Goes straight to solution | Must name assumptions first |
| Invents facts from training data | Must web search for real competitors |
| Presents everything as certain | Must rate confidence on assumptions |
| Never imagines failure | Must write a pre-mortem |
| Includes everything | Must cut features with explicit reasons |
| No quality gates | Must define kill criteria with metrics |

The protocol doesn't make AI smarter. It makes AI more honest about what it doesn't know.

## Empirical validation

Tested across 5 software topics x 2 models. Evaluated by 2 independent models (Opus + Codex GPT-5.3) using a 120-point rubric validated against IEEE 1058, PMBOK, CMMI, and Stanford DQ Framework.

```
Haiku without protocol:  25/120 (21%)
Opus without protocol:   45/120 (37%)
Haiku WITH /lets-cook:   95/120 (79%)

A $0.03 model with the protocol beats a $0.60 model without it.
```

## License

MIT

## Contributing

Issues and PRs welcome. If you find a new way the AI rationalizes skipping a step, open an issue — that's exactly what makes the protocol stronger.

