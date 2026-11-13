# rStack

## 0.2.0

### Minor Changes

- b521a2e: Add the council skill. Say "council" to get review from Claude Opus, GPT Sol, and Grok, preferably run through Cursor, and loop until they agree.
- 81f6aea: yeet now fixes clearly correct review findings right away, including ones from bots and review agents, and asks the user only about debatable feedback.
- 790f00b: yeet now stays quiet when nothing needed action, rebases the PR onto its base when it falls behind or conflicts, and fixes AI review findings it agrees with without asking.

### Patch Changes

- 6dc5772: yeet now treats the authenticated GitHub account as the user's review account and asks only when that account looks like a bot or is not the PR author.
- afa7204: yeet no longer includes commit signing instructions.
- 19c6974: Trim the yeet skill instructions without changing its behavior.

## 0.1.0

### Minor Changes

- fb435ff: Package the unslop, no-comments, and yeet skills for installation through skills.sh. Yeet keeps the draft PR's CI green, fixing failing checks until every required check passes on the latest commit.
