---
name: lets-cook
description: >
  Use when the user wants to plan a project, feature, or system before building it.
  Triggers: "lets cook", "plan this", "help me plan", "I want to build", or when
  user describes a project idea that needs structure before implementation. Also use
  when user has an existing plan and wants to stress-test it ("review this plan",
  "break this plan", "find weaknesses").
license: MIT
compatibility: Works with any agent that supports web search. No specific system requirements.
metadata:
  author: gabrielvani
  version: "3.1"
---

# /lets-cook — From Idea to Battle-Tested Plan

> LLMs naturally produce wishlists. This protocol forces plans.

Two passes. Pass 1 builds a rigorous plan with research and scope cuts. Pass 2 stress-tests it through 4 adversarial lenses until only the strong parts survive.

## When to Use

| Situation | What to Run |
|-----------|-------------|
| "I want to build X" | Full protocol (Pass 1 + Pass 2) |
| Already have a plan, want to stress-test | Pass 2 only (4-Lens Review) |
| Quick sketch, low stakes | Pass 1 only |
| Exploring whether to build at all | Steps 1-3 only (research phase) |

## When NOT to Use

- Simple bug fixes or small tasks (just do them)
- Pure research questions (use web search directly)
- Tasks with no design decisions (mechanical work)
- When the user explicitly says they don't want planning

---

## PASS 1 — BUILD THE PLAN

Execute all 7 steps. Use web search throughout — real data beats assumptions.

### STEP 1 — COMMIT

Before doing ANY planning, write down:

- **3 key assumptions** about this project — what you believe is true about the problem, the users, and the solution space. Be specific, not generic.
- **Where you might be WRONG** — what's your biggest uncertainty? What would surprise you?
- **What you expect to find** when you research the market — predictions you can check.

This anchors your thinking. You'll revisit these in Step 5.

### STEP 2 — BOUND THE APPETITE

Before decomposing anything, set the boundaries:

- **Time/effort budget**: How much is this project WORTH in engineering time? Be realistic, not optimistic.
- **Hard constraints** — 3 things that CANNOT be violated (regulatory, technical, business)
- **Explicit no-gos** — 3 things you will deliberately NOT build in v1, WHY, and WHEN to reconsider:
  - "We will NOT do ___ because ___. Reconsider when: ___"

### STEP 3 — RESEARCH THE LANDSCAPE

Find **5-8 real products/competitors** in this space using web search. For EACH:
- What was built? By whom? Succeed or fail? WHY specifically?
- What do they do well? What do they miss?
- What can we learn?

Then answer:
- **Base rate**: Of 10 projects like this one, how many typically succeed? What do the failures have in common?
- **5 conventions** everyone in this space follows. For each: what would the OPPOSITE approach look like? Pick **2-3 inversions** that could be genuine design opportunities (not traps).

### STEP 4 — DECOMPOSE INTO SUB-SYSTEMS

Break the project into **8-10 independent sub-systems**. For EACH:
- **Key decision** — the fork in the road
- **Constraints** — what limits the options
- **Dependencies** — what BLOCKS this? what does this BLOCK?

Then draw the **dependency graph**: which sub-systems must be built FIRST because others depend on them? Identify the **critical path** (longest chain). Note **parallel tracks** that can run simultaneously.

### STEP 5 — CHALLENGE YOUR ASSUMPTIONS

List **5 things that MUST be true** for this plan to work. Focus on things where your confidence is **50-80%** — NOT things you're 95% sure about (those are facts, not assumptions).

For each:
- How **fragile** is it? (very likely / could go either way / probably wrong)
- What **evidence** would tell you it's wrong?
- What would you **DO** if it's wrong? (concrete contingency, not "we'd adapt")

Then: **What is the strongest argument that this entire approach is WRONG?** Steelman it seriously. Then respond honestly — does it change anything?

### STEP 6 — FIND THE GAPS

After all the above, categorize what's STILL missing:
- **DECISION gaps**: What hasn't been decided yet? What information do you need to decide?
- **ERROR gaps**: What could go wrong that isn't addressed in the plan?
- **PREFERENCE gaps**: What depends on taste/values rather than facts? (these need stakeholder input)

### STEP 7 — FINAL PLAN: CUT, SEQUENCE, AND COMMIT

Produce the final plan:

- **Core pillars** — 3-4 non-negotiable principles that guide every decision
- **MVP scope** — what's IN and what's OUT, with reasons for each cut
- **Build sequence by INFORMATION DEPENDENCY**:
  - **FIRST**: what must we learn/validate/decide before building anything?
  - **THEN**: what depends on those answers?
  - **FINALLY**: what can proceed independently?
  - For **EACH phase**: a **Go/No-Go gate** — what must be true to proceed? If not, what's the fallback?
- **Explicit cuts**: "We chose NOT to do ___ because ___. Reconsider when: ___"
- **Success criteria**: How do we KNOW if this worked? Measurable outcomes.
- **Risk table**: Top 3 risks with trigger condition + mitigation + fallback

---

## PASS 2 — BREAK IT AND REBUILD

After Pass 1 is complete, apply all 4 review lenses:

### LENS A — ADVERSARIAL ATTACK

Find the **3 biggest weaknesses** in the plan. Cite specific claims. For each:
- What's wrong? (be precise)
- How to fix it? (concrete change, not "think more about it")

### LENS B — DOMAIN EXPERT

You are an **industry insider** who has built products in this exact space. From that perspective:
- What's **missing** that only someone who has built this would know?
- What **market reality** does the plan ignore?
- Use **web search** for current data.

### LENS C — USER PERSONAS

Test the plan against **3 different users**:
- **Persona 1**: The primary target (most common user)
- **Persona 2**: The edge case (constrained, atypical, or demanding user)
- **Persona 3**: The person who decides to PAY (may differ from the user)

For each: What fails? What's missing? What would make them choose a competitor?
Then: **What ONE change would improve the plan for all 3?**

### LENS D — PRE-MORTEM

It's **12 months from now**. This project has **FAILED**. It's dead.

- **Why did it fail?** (root cause, not symptoms)
- **3 warning signs** that were visible in the plan but ignored
- **What kill criteria** should have been added? (specific metric + deadline that triggers pivot/stop)

### SYNTHESIS — REVISED FINAL PLAN

Integrate ALL findings from 4 lenses into a revised plan:

- **What survived all 4 lenses** (keep — this is the validated core)
- **What needs to change** (with specific fixes from the lenses)
- **New elements added** by the review (insights no single lens would have found)
- **The 3 most important changes** overall (ranked by impact)
- **Revised MVP scope, timeline, and success criteria**

---

## OUTPUT — PIPELINE REPORT

After completing the protocol, close with a structured summary so the user sees exactly what happened:

### Pipeline Summary

```
## What was done

**Input:** [what the user asked to plan]
**Passes executed:** [Pass 1 only / Pass 1 + Pass 2 / Pass 2 only]

### Pass 1 Results
- **Competitors analyzed:** [N] ([names])
- **Base rate:** [X/10 succeed]
- **Sub-systems identified:** [N] with [N] on critical path
- **Assumptions challenged:** [N], weakest: [which one, confidence %]
- **Gaps found:** [N] decision / [N] error / [N] preference
- **Explicit cuts:** [list what was cut from MVP]

### Pass 2 Results (if executed)
- **Adversarial:** [N] weaknesses found, top: [summary]
- **Domain Expert:** [key missing insight]
- **Personas tested:** [names], universal fix: [what]
- **Pre-mortem cause of death:** [root cause]
- **Revisions applied:** [N] changes, top 3: [list]
```

### What Changed (delta from before /lets-cook)

List specific decisions that were DIFFERENT after running the protocol vs what would have been assumed without it. Format:

```
| Before | After | Why |
|--------|-------|-----|
| [assumption/default] | [new decision] | [evidence that changed it] |
```

### Recommended Next Steps

Based on the plan produced, suggest 1-3 concrete next actions:
- What to validate FIRST (highest-risk assumption)
- What to build FIRST (critical path start)
- What decision to make NOW (blocking gap)

---

## Empirical Validation

Tested across 5 software topics x 2 models, evaluated by 2 independent models (Opus + Codex GPT-5.3), using a 120-point evidence-based rubric validated against IEEE 1058, PMBOK, CMMI, Stanford DQ Framework.

```
Haiku Casual:    25/120 (21%)
Opus Casual:     45/120 (37%)
Pass 1 only:     78/120 (65%)
Full (Pass 1+2): 95/120 (79%)

Haiku + Protocol >> Opus without Protocol
A $0.03 model with the protocol beats a $0.60 model without it.
```

This protocol forces 7 operations LLMs skip naturally: research competitors, name assumptions, test against users, imagine failure, make scope cuts, set kill criteria, and calibrate confidence.

---

*Built through 6 sessions of empirical research. 50+ experimental conditions. 30+ blind evaluations. Discovered through multi-agent experimentation and distilled into these prompts.*
