# OpenCode Gotchas

## Known Issues

| Issue | Symptoms | Workaround |
|-------|----------|------------|
| Windows keybindings | Ctrl+P doesn't work | Check terminal keybinding settings, try different terminal |
| CJK character display | Chinese/Japanese/Korean text garbled | Use recommended terminals (WezTerm, Alacritty, Ghostty, Kitty) |
| Fresh install "Not Found" | `{detail: Not Found}` error | Verify API endpoint configuration, re-run `/connect` |
| `/compact` on Windows | Command doesn't function | Known issue, pending fix |
| Malware false positive | Windows Defender flags binary | Known false positive, add exception |
| Android/Termux | Wrong interpreter, non-PIE errors | Binary compatibility issue, use Docker container instead |

## Setup Tips

- Run `/init` after cloning a project to generate AGENTS.md
- Conversations are private by default; use `/share` explicitly to share
- Provider API keys must be configured before use (`/connect`)

## Provider Notes

- OpenCode Zen: Curated model list, recommended for new users
- Can switch providers without reinstalling
- Local models supported but may have reduced capabilities
