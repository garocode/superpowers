# Backend Developer Skills Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:writing-skills to create each skill following TDD for documentation.

**Goal:** Add missing skills that backend developers need for common high-risk tasks.

**Architecture:** Each skill follows the standard structure (SKILL.md + supporting files). Priority order based on risk and frequency of use.

**Approach:** Create skills in priority order. Each skill requires: baseline testing (RED), minimal skill (GREEN), loophole closure (REFACTOR).

---

## Priority Order

| Priority | Skill | Why |
|----------|-------|-----|
| 1 | database-migrations | High-risk, easy to mess up, hard to rollback |
| 2 | api-design | Core backend skill, many subtle decisions |
| 3 | safe-refactoring | Common need, often done poorly by agents |
| 4 | error-handling-patterns | Affects reliability, often inconsistent |
| 5 | dependency-management | Security implications, breaking changes |
| 6 | performance-profiling | Needed but agents often guess instead of measure |

---

## Task 1: database-migrations

**Files:**
- Create: `skills/database-migrations/SKILL.md`
- Create: `skills/database-migrations/checklist.md` (if needed)

**Scope:** Schema changes, data migrations, rollback strategies, zero-downtime migrations.

**Step 1: Research existing patterns**
- Look for migration patterns in popular frameworks (Prisma, Knex, Django, Rails)
- Identify common failure modes

**Step 2: Draft interview questions**
- "What's your migration strategy? (up/down, forward-only)"
- "How do you handle data migrations vs schema migrations?"
- "What's your rollback process?"
- "Any migrations that went wrong? What happened?"

**Step 3: Write baseline pressure scenarios**
- Agent asked to "add a column to users table"
- Agent asked to "rename a field" (breaks existing queries)
- Agent asked to "migrate data from old format to new"

**Step 4: Run baseline WITHOUT skill**
- Document agent's natural behavior
- Capture rationalizations for skipping safety steps

**Step 5: Write minimal SKILL.md**
- Address specific failures from baseline
- Include: pre-migration checklist, rollback requirements, testing approach

**Step 6: Test WITH skill, close loopholes**

**Step 7: Commit**
```bash
git add skills/database-migrations/
git commit -m "feat(skills): add database-migrations skill"
```

---

## Task 2: api-design

**Files:**
- Create: `skills/api-design/SKILL.md`
- Create: `skills/api-design/patterns.md` (REST/GraphQL patterns reference)

**Scope:** Endpoint design, versioning, error responses, pagination, rate limiting considerations.

**Step 1: Research**
- REST best practices, HTTP semantics
- Error response formats (RFC 7807, custom)
- Versioning strategies (URL, header, content-type)

**Step 2: Draft interview questions**
- "What's your API style? (REST, GraphQL, RPC)"
- "How do you version APIs?"
- "What's your error response format?"
- "Any API design decisions you regret?"

**Step 3: Write baseline pressure scenarios**
- Agent asked to "add an endpoint for user settings"
- Agent asked to "handle errors properly"
- Agent asked to "add pagination to list endpoint"

**Step 4: Run baseline, document failures**

**Step 5: Write minimal SKILL.md**

**Step 6: Test, close loopholes**

**Step 7: Commit**
```bash
git add skills/api-design/
git commit -m "feat(skills): add api-design skill"
```

---

## Task 3: safe-refactoring

**Files:**
- Create: `skills/safe-refactoring/SKILL.md`
- Create: `skills/safe-refactoring/strategies.md` (strangler fig, parallel run, etc.)

**Scope:** Incremental modernization, strangler fig pattern, feature flags for refactors, measuring before/after.

**Step 1: Research**
- Martin Fowler's refactoring patterns
- Strangler fig pattern
- Branch by abstraction
- Parallel run technique

**Step 2: Draft interview questions**
- "What's the riskiest part of your codebase to change?"
- "How do you verify refactors didn't break anything?"
- "Any refactors that went badly? What happened?"

**Step 3: Write baseline pressure scenarios**
- Agent asked to "modernize this old module"
- Agent asked to "refactor to use new pattern"
- Agent asked to "clean up this mess" (wide scope)

**Step 4: Run baseline, document failures**
- Expect: agent does big-bang refactor, breaks things

**Step 5: Write minimal SKILL.md**
- Focus on incremental strategies
- Verification requirements
- Scope limiting

**Step 6: Test, close loopholes**

**Step 7: Commit**
```bash
git add skills/safe-refactoring/
git commit -m "feat(skills): add safe-refactoring skill"
```

---

## Task 4: error-handling-patterns

**Files:**
- Create: `skills/error-handling-patterns/SKILL.md`

**Scope:** Structured errors, retry strategies, graceful degradation, error boundaries.

**Step 1: Research**
- Error handling patterns by language
- Retry with backoff patterns
- Circuit breaker pattern
- Error categorization (retryable vs fatal)

**Step 2: Draft interview questions**
- "How do you categorize errors in this codebase?"
- "What's your retry strategy?"
- "How do you handle partial failures?"

**Step 3: Baseline scenarios**
- Agent asked to "handle the error case"
- Agent asked to "add retry logic"
- Agent asked to "make this more resilient"

**Step 4-7: Standard TDD cycle**

**Commit:**
```bash
git add skills/error-handling-patterns/
git commit -m "feat(skills): add error-handling-patterns skill"
```

---

## Task 5: dependency-management

**Files:**
- Create: `skills/dependency-management/SKILL.md`

**Scope:** Upgrading safely, security audits, lock files, breaking change detection.

**Step 1: Research**
- Semantic versioning implications
- Security audit tools (npm audit, Snyk, Dependabot)
- Upgrade strategies (one at a time vs batch)

**Step 2: Draft interview questions**
- "How often do you upgrade dependencies?"
- "Any dependency upgrades that broke things?"
- "How do you handle security vulnerabilities?"

**Step 3: Baseline scenarios**
- Agent asked to "upgrade all dependencies"
- Agent asked to "fix this security vulnerability"
- Agent asked to "add this new library"

**Step 4-7: Standard TDD cycle**

**Commit:**
```bash
git add skills/dependency-management/
git commit -m "feat(skills): add dependency-management skill"
```

---

## Task 6: performance-profiling

**Files:**
- Create: `skills/performance-profiling/SKILL.md`

**Scope:** Measure before optimizing, profiling tools, identifying bottlenecks, caching strategies.

**Step 1: Research**
- Profiling tools by language/runtime
- Common bottleneck patterns
- "Measure, don't guess" principle

**Step 2: Draft interview questions**
- "What are the known slow parts of this system?"
- "How do you measure performance?"
- "Any performance fixes that didn't help or made things worse?"

**Step 3: Baseline scenarios**
- Agent asked to "make this faster"
- Agent asked to "optimize the database queries"
- Agent asked to "add caching"

**Step 4-7: Standard TDD cycle**

**Commit:**
```bash
git add skills/performance-profiling/
git commit -m "feat(skills): add performance-profiling skill"
```

---

## Completion Checklist

After all skills created:
- [ ] Each skill tested with pressure scenarios
- [ ] Each skill follows writing-skills template
- [ ] Word counts within guidelines (SKILL.md < 500 words)
- [ ] All committed and pushed
- [ ] Consider which should be "getting-started" skills
