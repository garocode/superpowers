# Interview Questions for AGENTS.md

**Ask the human these questions to gather knowledge that can't be derived from code.**

## Quick Summary
- "In one sentence, what does this repo do?"
- "Who or what consumes this repo's output?"

## Keywords
- "What terms would someone use when asking about this repo?"
- "What problem domains does this cover?"

## Questions This Repo Answers
- "What are the top 5 questions you get asked about this codebase?"
- "What questions do new team members typically ask?"

## Directory Map
- "Which directories are most important to understand?"
- "Are there any directories that look important but aren't?"
- "Any directories with misleading names?"

## Key Files to Read First
- "If someone had 10 minutes to understand this codebase, what files should they read?"
- "What file gives the best 'birds eye view'?"

## Architecture Notes
- "What's the request/data flow that isn't obvious from the code?"
- "Are there any architectural decisions that would surprise someone?"

## Related Repos
- "What other repos does this interact with?"
- "Where do cross-repo bugs typically occur?"

## Gotchas & Tribal Knowledge (MOST IMPORTANT)
- "What's something that trips up every new person?"
- "What behavior isn't obvious from reading the code?"
- "Are there any features that are disabled/deprecated but still in the code?"
- "What naming inconsistencies exist (old names in comments, renamed concepts)?"
- "What environment differences exist between dev/staging/prod?"
- "What 'looks wrong but is intentional'?"
- "What would you warn someone about before they touch this code?"

## Common Mistakes
- "What mistakes do people commonly make in this codebase?"
- "What types/concepts are commonly confused?"
- "What assumptions do people make that turn out to be wrong?"

---

## Auto-Generate vs Ask

| Section | Auto-Generate | Ask Human |
|---------|---------------|-----------|
| Quick Summary | Draft from README | Verify accuracy |
| Keywords | Suggest from code | Add domain terms |
| Questions This Repo Answers | No | Yes |
| Directory Map | Generate structure | Ask about dead dirs |
| Key Files to Read First | Suggest entry points | Confirm priority |
| Architecture Notes | Diagram from code | Non-obvious flows |
| Related Repos | Find from imports | Runtime relationships |
| Gotchas & Tribal Knowledge | **Never** | **Always ask** |
| Common Mistakes | **Never** | **Always ask** |

**Rule**: If a section could be derived from reading code, it has low value. Prioritize interview time on Gotchas and Common Mistakes.
