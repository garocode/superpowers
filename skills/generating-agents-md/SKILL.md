---
name: generating-agents-md
description: Use when creating or updating AGENTS.md files in repositories, onboarding to a codebase that lacks agent documentation, or when repo structure has significantly changed
---

# Generating AGENTS.md

## Overview

AGENTS.md helps AI agents navigate repositories efficiently. **Core principle: capture human-only knowledge that can't be derived from reading code.**

Auto-generated docs that restate code are useless—agents can read code themselves. Value comes from tribal knowledge, gotchas, and context only humans know.

## When to Use

- Creating AGENTS.md for a repo that lacks one
- Updating after significant repo changes
- Repo has docs but agents still struggle to navigate

**Not for**: Central discovery indexes, project-specific CLAUDE.md files

## Workflow

```
1. Explore codebase → draft auto-generatable sections
2. Interview human → fill knowledge-dependent sections
3. Human reviews → corrects inaccuracies
4. Commit to repo root (or monorepo package root)
```

**Template**: See @template.md for the standardized AGENTS.md structure.

**Interview questions**: See @interview-questions.md for questions to ask humans for each section.

**Behavior levels**: See @behavior-levels.md for agent guardrail templates (Minimal/Standard/Strict).

## Key Sections

| Section | Value Source |
|---------|--------------|
| Quick Summary, Keywords | Human verification of drafts |
| Directory Map, Key Files | Code + human context |
| Gotchas & Tribal Knowledge | **Human only - highest value** |
| Common Mistakes | **Human only** |
| Agent Guidelines | Human choice (level 1-3) |

## Monorepo Handling

- **Root AGENTS.md**: Overview, package routing, cross-package flows
- **Package AGENTS.md**: Package-specific details (only if complex)

Don't duplicate—reference child AGENTS.md from root.

## Common Mistakes

| Mistake | Fix |
|---------|-----|
| Auto-generating Gotchas | Always interview humans |
| Restating code as docs | Focus on non-obvious knowledge |
| Over-documenting (200+ lines) | Keep concise, agents skim long files |
| Skipping the interview | Most value is in human knowledge |
| One-time creation | Update after significant changes |
