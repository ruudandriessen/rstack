---
name: yeet
description: Open a draft PR, keep its CI green and up to date with its base, and work through review comments. Fix agreed findings and surface only feedback that needs the user's judgment. Trigger on "yeet".
disable-model-invocation: true
license: MIT
compatibility: "Requires Git, an authenticated GitHub CLI, and repository push access."
---

# Yeet

Push the current work, open a draft PR, keep it green and up to date with its base, and work through review comments until the user is satisfied. Fix findings you agree with right away. Bring the user only the feedback that needs their judgment.

## Prepare the change

Inspect the branch, base, diff, and worktree. Include only work in scope and preserve unrelated changes. Use a feature branch when needed. Never force-push a shared default branch.

Run checks appropriate to the change and resolve failures it introduced. If GitHub access is missing, finish local preparation and report the specific access needed.

Use Conventional Commits with an imperative subject, `type(scope): summary`, without a trailing period.

After the subject, use Linux-style git trailers only. Add `Assisted-by: Vendor:model` for models known to have contributed; do not invent model identities. Preserve authorship and existing trailers when amending.

## Open the draft

Find the branch's existing PR before creating one. Open new PRs in draft and preserve an existing PR's status. The user decides when to mark it ready. Follow an explicit request for a different status.

Match the title to the main commit subject. Explain the problem and resulting behavior in a short body. Include material testing limits, without a checklist or boilerplate sections. Keep the description current when the scope changes.

Tell the user the draft is open and ready for their comments. Include the link and current check status, then begin watching for feedback. This notification does not mark the PR ready on GitHub.

## While the PR is a draft

Treat the authenticated GitHub account as the requesting user's review account unless the user names a different one. Ask for the account while completing the draft only when the authenticated account looks like a bot or service account, or is not the PR author. Do not assume any other collaborator is that person. Accept feedback from another review tool only when its source is attributable to the user.

Watch PR conversation comments, submitted reviews, and inline threads, including replies and edits. Act on the user's feedback within the task's scope without asking them to repeat it in chat.

For comments from other people, bots, or review agents, verify each finding against the code. Fix bot and agent findings you agree with right away. Fix findings from people right away when they are clearly correct, in scope, and have one obvious fix. Surface the rest to the user with your recommendation: trade-offs, scope changes, or findings you cannot confirm. Leave clearly wrong findings unresolved and say why in one line.

Read the full thread and inspect the code before changing it. Fix the issue, run affected checks, and push the change. Resolve a thread only after verifying that the pushed change addresses it. Leave questions, disputed findings, and blocked work unresolved and explain what needs the user's judgment. Do not post separate replies unless asked.

Tell the user what changed, including fixes made for other reviewers, and keep watching for their next comments. Repeat until they mark the PR ready, close it, or ask you to stop.

Only message the user when you changed something, need a decision, or are blocked. Stay silent about events that needed no action.

## Keep the branch up to date

When the PR conflicts with its base or falls behind a required up-to-date base, rebase onto the latest base, resolve conflicts preserving both sides' intent, rerun affected checks, and push with `--force-with-lease`. Ask the user when a conflict needs a judgment call or others also commit to the branch.

## Keep CI green

The draft is not done while a required check is failing or pending on the latest commit. Watch check runs alongside comments, and keep working on a red run even when no new feedback arrives.

When a check fails, read its logs, reproduce the failure locally where possible, fix the cause, push, and wait for the new run. Repeat until every check passes. Rerun a failure once when the logs point to a flake, such as a timeout or network error, and report it if it fails again. If the failure also occurs on the base branch, or needs secrets or permissions you lack, report it with evidence instead of working around it.

Never skip, disable, or weaken a check, test, or lint rule to make it pass unless the user asks.

## Once the PR is ready for review

Keep fixing findings by the same rules as in draft, and keep the branch rebased and CI green. Verify, push, resolve the thread, and report what you fixed.

For debatable feedback, explain it to the user in plain language. State what the reviewer means, whether the code supports the finding, and whether you recommend fixing it now, deferring it, or leaving the code as it is. Wait for the user's decision before editing, replying, or resolving those threads. This includes the requesting user's comments, which may now be questions for other reviewers rather than instructions. Follow an explicit instruction to handle a particular finding, then verify and report the result.

## Keep the loop accurate

Inspect the host's available PR event subscriptions, listeners, and wake tools first. Use an existing subscription or register one for this PR through the supported mechanism, then confirm it is active. Prefer event delivery to a polling loop. Subscribe to comments, reviews, check runs, conflicts, and PR state changes where supported; fetch the current PR and thread when an event arrives.

Poll only for events the host cannot deliver, with bounded waits while the session runs. Track the PR, comment IDs and edits, and the last processed state so reconnecting does not repeat completed work. Fetch feedback received while you were fixing the previous batch.

Recheck the PR's draft status before starting a fix and before pushing or resolving threads. If it became ready, pause pending changes for debatable feedback and present them for the user's decision. If it returns to draft, resume the draft workflow. Stop on merge or closure, or when the user asks.

After the PR is ready, explain CI failures and recommend a fix before proceeding unless the user already authorized that work.

Check the available tools and subscription status before declaring automatic listening unavailable. If neither event delivery nor continued polling is possible, explain the specific limitation and how to resume. Report a listener as active only after confirming it. On an access failure, preserve your place and report the blocker instead of silently abandoning the loop.

Marking a PR ready does not authorize merging it. Merge only when explicitly authorized and the repository's requirements are satisfied.
