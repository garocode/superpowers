---
name: logging
description: Use when adding, reviewing, or improving logging in code, and project lacks explicit logging guidelines in CLAUDE.md or AGENTS.md
---

# Logging Standards

## Overview

Structured JSON logging with context for observability. Always include relevant identifiers.

## When to Use

```dot
digraph logging_decision {
    "Adding logging?" [shape=diamond];
    "Project has logging guidelines?" [shape=diamond];
    "Use project guidelines" [shape=box];
    "Apply this skill" [shape=box];

    "Adding logging?" -> "Project has logging guidelines?" [label="yes"];
    "Project has logging guidelines?" -> "Use project guidelines" [label="yes\n(CLAUDE.md/AGENTS.md)"];
    "Project has logging guidelines?" -> "Apply this skill" [label="no"];
}
```

**Check first:** Look for logging section in CLAUDE.md or AGENTS.md. If present, follow project guidelines instead.

## Core Principles

See @standards.md for context fields and patterns.

**Key principles:**
- Structured JSON logs (machine-parseable)
- Always include context identifiers
- Levels matter: debug/info/warn/error have distinct semantics
