# Learning Plan (Cohort 0)

> Track: **Frontier / project-driven**
> Project: **AI × Web3 Security Audit Assistant**
> Time budget: **~30 min/day**

## 0) North Star (what “done” means)
In 2–4 weeks, ship a small demo that:
- Takes a Solidity file (or pasted code)
- Runs a few checks (static rules + LLM reasoning)
- Produces a short **audit-style report** (findings, severity, evidence lines, suggestions)

## 1) Daily rhythm (30 min)
1. **10 min** Handbook reading (1 concept)
2. **15 min** Build (1 small commit)
3. **5 min** Log (daily note + next action)

## 2) Week 1 — MVP skeleton (recommended)
**Goal:** a minimal “audit note generator” pipeline.

Day 1 — Scope & baseline
- Define what contracts you target first (e.g., ERC20 / simple vault)
- Define output format: Finding / Severity / Evidence / Fix

Day 2 — Dataset & examples
- Collect 3–5 short vulnerable snippets (reentrancy, access control, integer issues)
- Write them into `experiments/snippets/` (no private code)

Day 3 — Rule checks (non-LLM)
- Add a small checklist-based scanner (regex is OK)
- Output findings as JSON

Day 4 — LLM reasoning layer (manual first)
- Prompt template: explain vulnerability + locate evidence + propose fix
- Produce report markdown

Day 5 — Packaging
- Wrap into a CLI script (or minimal web page)
- Add README usage + 1 demo screenshot

## 3) Knowledge modules (pull as needed)
- Web3: Smart contract basics, common vulnerabilities, security mindset
- AI: Prompting, evaluation, tool-use, guardrails (avoid hallucinated claims)
- Bridge: Chain-aware context (optional), verifiable outputs (cite evidence lines)

## 4) Next action (today)
- Create `tasks/week1-mvp.md` and start Day 1 scope.
