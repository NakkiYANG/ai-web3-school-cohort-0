# NFT Contract — Minimal Threat Model (for Audit Assistant MVP)

This is a **starter checklist** for an NFT-focused audit helper.

## A. Ownership / Admin risks
- Centralization risks: `owner` can pause/mint/burn/update baseURI
- Missing `onlyOwner` or wrong access control
- Misconfigured roles (AccessControl): admin role can grant itself everything

## B. Minting / Supply
- Unlimited mint / missing max supply
- Public mint without allowlist controls (if expected)
- Incorrect payment accounting (price, refunds)

## C. Transfers / Approvals
- Non-standard transfer hooks / unexpected reverts
- Approval logic surprises; operator approvals
- ERC721Receiver handling for safe transfers

## D. Royalties / Marketplace integration
- EIP-2981 support correctness (if claimed)
- Royalty logic mismatch (declared but not enforced)

## E. Metadata / URI
- Mutable metadata (baseURI change) — communicate risk
- TokenURI logic errors / gas-heavy loops

## F. Reentrancy / External calls
- External calls in mint/withdraw paths
- Withdraw functions missing reentrancy guard

## G. Economic / Denial-of-service
- Looping over token holders (unbounded loops)
- Storage bloat / griefing vectors

## What the assistant should output
Each finding should include:
- Title
- Severity (H/M/L/Info)
- Evidence (code quote + line numbers)
- Impact (what could go wrong)
- Recommendation
