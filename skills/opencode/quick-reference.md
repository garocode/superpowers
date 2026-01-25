# OpenCode Quick Reference

## Agent Types

| Agent | Purpose |
|-------|---------|
| Build (default) | Full access for development tasks |
| Plan | Read-only, suggests implementation, no file edits |
| `@general` | Subagent for complex searches and multistep operations |

Toggle Plan/Build mode with **Tab** key.

## Commands

| Command | Action |
|---------|--------|
| `/init` | Analyze project, generate AGENTS.md |
| `/connect` | Configure API provider credentials |
| `/share` | Generate shareable conversation link |
| `/undo` | Revert recent changes |
| `/redo` | Restore undone changes |

## File References

Use `@` for fuzzy file search in prompts (e.g., `@config` finds config files).

## Image Support

Drag-and-drop images into terminal for context.

## Installation Directories

Priority order for install location:
1. `$OPENCODE_INSTALL_DIR`
2. `$XDG_BIN_DIR`
3. `$HOME/bin`
4. `$HOME/.opencode/bin` (default)

## Terminal Requirements

Recommended: WezTerm, Alacritty, Ghostty, Kitty

Basic features may work in other terminals, but full functionality requires modern terminal emulators.
