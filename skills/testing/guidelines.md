# Testing Guidelines

## The Checklist

Before adding a test, answer these questions:

1. **What user-visible behavior would break without it?**
2. **What real bug would this prevent from returning?**
3. **Is there a higher-level test (integration/regression) that better captures the value?**

If you can't answer at least one clearly, don't add the test.

## Good Tests

| Example | Why Good |
|---------|----------|
| Regression test reproducing Slack reaction misattribution | Prevents specific bug from returning |
| Integration test verifying queue message posts response | Validates user-visible behavior |

## Bad Tests

| Example | Why Bad |
|---------|---------|
| Test asserting helper returns a string | Duplicates type checking |
| Test that mirrors a type guard | Already validated by `tsc` |
| Test for a constant value | No behavior, just implementation detail |
| Test duplicating a simple schema | Static analysis covers this |

## AI Feeds AI Anti-Pattern

Avoid tests that mirror:
- Types already checked by TypeScript
- Configs validated by schema
- Implementation details guaranteed by lint/static analysis

These create maintenance burden without catching real bugs.

## Documentation

When adding a test, mention in commit message:
- The behavior it covers, OR
- The bug it prevents

Example: `test: prevent reaction feedback misattribution (#123)`
