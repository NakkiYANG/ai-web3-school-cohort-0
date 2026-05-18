# Week 1 — MVP checklist (Security Audit Assistant)

## Day 1 — Scope & report format
- [ ] Target contract type: _TBD_ (ERC20 / Vault / NFT / etc.)
- [ ] Threat model: what we care about (fund loss, privilege abuse, DoS)
- [ ] Report schema:
  - Finding title
  - Severity: High / Medium / Low / Info
  - Evidence: line numbers / code quote
  - Impact
  - Recommendation / Fix

## Day 2 — Snippet set
- [ ] Add 3–5 vulnerable snippets under `experiments/snippets/`
- [ ] Add expected findings under `experiments/snippets/expected/`

## Day 3 — Baseline scanner
- [ ] Write `experiments/scanner/scan.py` (or similar)
- [ ] Output JSON findings

## Day 4 — LLM report generator
- [ ] Prompt template
- [ ] Convert findings + code into report markdown

## Day 5 — Packaging
- [ ] CLI usage
- [ ] README demo
