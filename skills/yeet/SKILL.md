---
name: yeet
description: Commit and push the current work, open a draft PR, then babysit it until it merges or closes. Trigger on "yeet".
disable-model-invocation: true
license: MIT
compatibility: "Requires Git, an authenticated GitHub CLI, repository push access, and the rStack babysit skill."
---

# Yeet

Push the current work, open a draft PR, and hand it to the babysit skill.

## Prepare the change

Inspect the branch, base, diff, and worktree. Commit only work in scope, preserve unrelated changes, and use a feature branch when needed. Never force-push a shared default branch. Run appropriate checks and fix failures the change introduced. If GitHub access is missing, finish locally and report what access is needed.

Use Conventional Commits, `type(scope): summary`, imperative and without a trailing period. Follow the subject with Linux-style trailers only, adding `Assisted-by: Vendor:model` for models known to have contributed. Preserve authorship and existing trailers when amending.

## Open the draft

Reuse the branch's existing PR and keep its status; otherwise open a draft. The user decides when it is ready unless they ask for a different status. Match the title to the main commit subject. Keep the body short and current: the problem, the resulting behavior, and material testing limits, without checklists or boilerplate.

Send the user the link and check status.

## Babysit

Follow the babysit skill on the PR. If it is not installed, tell the user the PR is open but unwatched, and that installing babysit from `ruudandriessen/rstack` enables the rest of the workflow.
