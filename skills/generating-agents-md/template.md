# AGENTS.md Template

Copy and fill out this template for your repository.

```markdown
# {Repo Name} - Agent Guide

## Quick Summary

<!-- 1-2 sentences: what this repo does, who consumes it -->

## Keywords

<!-- Terms that should route questions here -->
`keyword1`, `keyword2`, `keyword3`

## Questions This Repo Answers

<!-- Example questions - confirms agent found the right repo -->
- "How does [feature X] work?"
- "Where is [config Y] defined?"
- "What happens when [event Z] occurs?"

## Directory Map

| Directory | Purpose | Key Files |
|-----------|---------|-----------|
| `src/api/` | REST handlers | `routes.ts` |
| `src/services/` | Business logic | `billing.ts` |

## Key Files to Read First

1. `src/types.ts` - Core type definitions
2. `src/config/index.ts` - Configuration, feature flags
3. `README.md` - Setup, architecture overview

## Architecture Notes

<!-- High-level flow not obvious from code -->

## Related Repos

| Repo | Relationship |
|------|--------------|
| `other-repo` | Consumes our API |

## Gotchas & Tribal Knowledge

<!-- NON-OBVIOUS things - this is the most valuable section -->
- **Feature X is disabled in prod**: Due to [reason]
- **Config Y overrides Z**: When both set, Y wins
- **The "legacy" folder**: Still active despite name

## Common Mistakes

- Don't confuse `UserProfile` with `User`
- Timestamps are Unix ms, not ISO strings

## Agent Guidelines

<!-- Choose a level from behavior-levels.md and paste here -->
<!-- Level 1: Minimal | Level 2: Standard | Level 3: Strict -->
```

## Section Guidelines

| Section | Purpose | Value Source |
|---------|---------|--------------|
| Quick Summary | Route questions to correct repo | Human verification |
| Keywords | Discovery index matching | Human domain knowledge |
| Questions This Repo Answers | Confirm correct repo | Human experience |
| Directory Map | Narrow file searches | Code + human context |
| Key Files to Read First | Quick orientation | Human judgment |
| Architecture Notes | Non-obvious flows | Human knowledge |
| Related Repos | Cross-repo navigation | Human experience |
| Gotchas & Tribal Knowledge | **Highest value** | **Human only** |
| Common Mistakes | Prevent repeated errors | **Human only** |
| Agent Guidelines | Behavior guardrails | Human choice (level 1-3) |
