---
name: testing
description: Use when adding, reviewing, or improving tests, and project lacks explicit testing guidelines in CLAUDE.md or AGENTS.md
---

# Testing Strategy

## Overview

Tests verify user-visible behavior or prevent specific regressions. Not for coverage sake.

## When to Use

```dot
digraph testing_decision {
    "Adding tests?" [shape=diamond];
    "Project has testing guidelines?" [shape=diamond];
    "Use project guidelines" [shape=box];
    "Apply this skill" [shape=box];

    "Adding tests?" -> "Project has testing guidelines?" [label="yes"];
    "Project has testing guidelines?" -> "Use project guidelines" [label="yes\n(CLAUDE.md/AGENTS.md)"];
    "Project has testing guidelines?" -> "Apply this skill" [label="no"];
}
```

**Check first:** Look for testing section in CLAUDE.md or AGENTS.md. If present, follow project guidelines instead.

## Core Philosophy

See @guidelines.md for the full checklist and examples.

**Key principle:** If `tsc`/lint/static analysis already validates it, don't add a unit test just to have one.
