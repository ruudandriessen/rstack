---
name: babysit
description: Watch a pull request until it merges or closes. Keep CI green and the branch up to date with its base, fix agreed review findings, and surface only feedback that needs the user's judgment. Use when the user says "babysit" or another skill, such as yeet, hands off a PR to watch.
license: MIT
compatibility: "Requires Git, an authenticated GitHub CLI, and repository push access."
---

# Babysit

Watch a pull request, keep it green and up to date with its base, and work through review comments until the user is satisfied. Fix findings you agree with right away and bring the user only what needs their judgment.

## Pick the PR

Use the PR the user names, or the open PR for the current branch. If there is none, ask which PR to watch. Check out its head branch and confirm you can push to it. If GitHub access is missing, report what access is needed.

## Handle feedback

Treat the authenticated GitHub account as the user's unless they name another. Ask only if it looks like a bot or is not the PR author. Accept feedback from other review tools only when attributable to the user.

Watch conversation comments, reviews, and inline threads, including replies and edits. While the PR is a draft, act on the user's in-scope feedback without asking them to repeat it.

Verify every other finding against the code. Fix bot and agent findings you agree with right away. Fix findings from people right away when they are clearly correct, in scope, and have one obvious fix. Surface the rest with your recommendation. Leave clearly wrong findings unresolved and say why in one line.

Read the full thread before changing code. Fix, run affected checks, push, and resolve a thread only once the pushed change addresses it. Do not post replies unless asked.

Once the PR is ready, the user's comments may be questions for other reviewers, so treat them as debatable. For debatable feedback, explain what the reviewer means, whether the code supports it, and what you recommend, then wait for the user's decision before editing, replying, or resolving.

Only message the user when you changed something, need a decision, or are blocked. Stay silent about events that needed no action.

## Commit fixes

Use Conventional Commits, `type(scope): summary`, imperative and without a trailing period. Follow the subject with Linux-style trailers only, adding `Assisted-by: Vendor:model` for models known to have contributed. Preserve authorship and existing trailers when amending.

## Keep the branch up to date

When the PR conflicts with its base or falls behind a required up-to-date base, rebase onto the latest base, resolve conflicts preserving both sides' intent, rerun affected checks, and push with `--force-with-lease`. Ask the user when a conflict needs a judgment call or others also commit to the branch.

## Keep CI green

The PR is not done while a required check fails or is pending on the latest commit. Read failing logs, reproduce locally where possible, fix the cause, push, and repeat. Rerun an apparent flake once and report it if it fails again. Report failures that also occur on the base branch or need access you lack, with evidence. Never skip, disable, or weaken a check unless the user asks.

Fix and push CI failures without waiting, whether the PR is a draft, ready, or approved. Approvals do not freeze the branch, and an approved PR with a red check is still not done. Ask first only when you are genuinely unsure what the right fix is.

## Keep the loop running

Prefer the host's PR event subscriptions over polling: subscribe to comments, reviews, checks, conflicts, and state changes, and confirm the subscription is active before reporting it. Poll with bounded waits only for events the host cannot deliver. Track processed comments, edits, and state so reconnects do not repeat work, and pick up feedback that arrived during a fix.

Recheck draft status before fixing, pushing, or resolving, and switch rules if it changed. Stop on merge, closure, or when the user asks. If listening is impossible or access fails, keep your place and explain how to resume.

Marking a PR ready does not authorize merging. Merge only when explicitly asked and the repository's requirements are met.
