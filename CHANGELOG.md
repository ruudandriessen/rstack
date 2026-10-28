# rStack

## 0.2.0

### Minor Changes

- 81f6aea: yeet now fixes clearly correct review findings right away, including ones from bots and review agents, and asks the user only about debatable feedback.

### Patch Changes

- 6dc5772: yeet now treats the authenticated GitHub account as the user's review account and asks only when that account looks like a bot or is not the PR author.
- afa7204: yeet no longer includes commit signing instructions.

## 0.1.0

### Minor Changes

- fb435ff: Package the unslop, no-comments, and yeet skills for installation through skills.sh. Yeet keeps the draft PR's CI green, fixing failing checks until every required check passes on the latest commit.
