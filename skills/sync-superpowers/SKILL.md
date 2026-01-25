---
name: sync-superpowers
description: Use when you have created or updated a skill in the superpowers fork and need to push changes and clear the Claude cache
---

# Sync Superpowers

## Overview

Push skill changes from the local superpowers fork to the remote and clear the Claude Code plugin cache so changes take effect.

**Core principle:** Push first, then clear cache. Both steps required for changes to propagate.

## Workflow

### 1. Commit Changes

```bash
cd ~/.config/opencode/superpowers
git add -A
git commit -m "feat(skills): <describe change>"
```

### 2. Push Branch

```bash
cd ~/.config/opencode/superpowers
git push origin garocode
```

**IMPORTANT:** Confirm push succeeded before proceeding. If push fails (e.g., SSH auth issues), stop here and ask user to push manually.

### 3. Clear Claude Cache (only after push succeeds)

```bash
rm -rf ~/.claude/plugins/cache/superpowers-marketplace/superpowers
```

### 4. Confirm

Report to user:
- Commit pushed to `garocode` branch
- Cache cleared
- Changes will take effect in new Claude Code sessions

## Quick Reference

| Step | Command |
|------|---------|
| Push | `cd ~/.config/opencode/superpowers && git push origin garocode` |
| Clear cache | `rm -rf ~/.claude/plugins/cache/superpowers-marketplace/superpowers` |

## Common Mistakes

### Forgetting to clear cache

- **Problem:** Claude Code continues using cached version of skills
- **Fix:** Always delete the cache directory after pushing

### Pushing to wrong branch

- **Problem:** Changes go to `main` instead of fork branch
- **Fix:** Always push to `garocode` branch explicitly
