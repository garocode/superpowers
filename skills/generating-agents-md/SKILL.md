---
name: generating-agents-md
description: Use when creating or updating AGENTS.md files in repositories, onboarding to a codebase that lacks agent documentation, or when repo structure has significantly changed
---

# Generating AGENTS.md

## Overview

AGENTS.md helps AI agents navigate repositories efficiently. The core principle: **capture human-only knowledge that can't be derived from reading code**.

Auto-generated documentation that restates the code is useless—agents can read code themselves. Value comes from tribal knowledge, gotchas, and context that only humans know.

## When to Use

- Creating AGENTS.md for a repo that lacks one
- Updating AGENTS.md after significant repo changes
- Onboarding to a new codebase as an agent
- Repo has docs but agents still struggle to navigate it

**Not for**: Central discovery indexes (DISCOVERY.md), project-specific CLAUDE.md files

## Template

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
```

## Interview Questions

**Ask the human these questions to gather knowledge that can't be derived from code.**

### Quick Summary
- "In one sentence, what does this repo do?"
- "Who or what consumes this repo's output?"

### Keywords
- "What terms would someone use when asking about this repo?"
- "What problem domains does this cover?"

### Questions This Repo Answers
- "What are the top 5 questions you get asked about this codebase?"
- "What questions do new team members typically ask?"

### Directory Map
- "Which directories are most important to understand?"
- "Are there any directories that look important but aren't?"
- "Any directories with misleading names?"

### Key Files to Read First
- "If someone had 10 minutes to understand this codebase, what files should they read?"
- "What file gives the best 'birds eye view'?"

### Architecture Notes
- "What's the request/data flow that isn't obvious from the code?"
- "Are there any architectural decisions that would surprise someone?"

### Related Repos
- "What other repos does this interact with?"
- "Where do cross-repo bugs typically occur?"

### Gotchas & Tribal Knowledge (MOST IMPORTANT)
- "What's something that trips up every new person?"
- "What behavior isn't obvious from reading the code?"
- "Are there any features that are disabled/deprecated but still in the code?"
- "What naming inconsistencies exist (old names in comments, renamed concepts)?"
- "What environment differences exist between dev/staging/prod?"
- "What 'looks wrong but is intentional'?"
- "What would you warn someone about before they touch this code?"

### Common Mistakes
- "What mistakes do people commonly make in this codebase?"
- "What types/concepts are commonly confused?"
- "What assumptions do people make that turn out to be wrong?"

## Auto-Generate vs Ask

| Section | Auto-Generate | Ask Human |
|---------|---------------|-----------|
| Quick Summary | Draft from README | Verify accuracy |
| Keywords | Suggest from code analysis | Add domain terms |
| Questions This Repo Answers | No | Yes - only humans know what gets asked |
| Directory Map | Generate structure | Ask about misleading names, dead dirs |
| Key Files to Read First | Suggest entry points | Confirm priority order |
| Architecture Notes | Diagram from code | Ask about non-obvious flows |
| Related Repos | Find from imports/configs | Ask about runtime relationships |
| Gotchas & Tribal Knowledge | **Never auto-generate** | **Always ask** |
| Common Mistakes | **Never auto-generate** | **Always ask** |

**Rule**: If a section could be derived from reading code, it has low value. Prioritize human interview time on Gotchas and Common Mistakes.

## Workflow

```
1. Explore codebase → draft auto-generatable sections
2. Interview human → fill knowledge-dependent sections
3. Human reviews draft → corrects inaccuracies
4. Commit AGENTS.md to repo root (or monorepo package root)
```

## Monorepo Handling

For monorepos, create AGENTS.md at the appropriate level:

- **Root AGENTS.md**: Overview, package routing, cross-package flows
- **Package AGENTS.md**: Package-specific details (optional, only if complex)

Don't duplicate—reference child AGENTS.md from root when needed.

## Common Mistakes

| Mistake | Why It's Wrong | Fix |
|---------|----------------|-----|
| Auto-generating Gotchas | Creates AI→AI feedback loop with no value | Always interview humans |
| Restating code as docs | Agents can read code; this wastes tokens | Focus on non-obvious knowledge |
| Over-documenting | Long files get skimmed/ignored | Keep under 200 lines |
| Generic examples | "How does X work?" teaches nothing | Use repo-specific examples |
| Skipping interview | Most value is in human knowledge | Always ask the questions |
| One-time creation | Docs rot; repo evolves | Update after significant changes |
