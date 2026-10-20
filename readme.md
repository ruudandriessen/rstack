# rStack

[![skills.sh](https://img.shields.io/badge/skills.sh-rStack-black)](https://skills.sh/ruudandriessen/rstack)

Minimal, opinionated skills for AI agents.

> Work in progress. I'm continuing to iterate on the skills and workflows.

rStack aims to give agents more of the work between discovering a problem and merging its fix. Don't spend an afternoon solving something the agent could figure out in minutes. Give it the problem first. If it gets stuck, put on your thinking hat. Until then, spare yourself the hat hair. Let it investigate, implement, test, and follow the PR through review. This follows the approach in [Theo's walkthrough](https://youtu.be/D8PikZ1KhUo?t=2170).

The agent opens a draft PR, listens for your comments, checks its fixes, and resolves addressed threads. Once you mark the PR ready, it explains new feedback and waits for your decision. It uses the host's PR listeners when available and merges only with your authorization.

## Skills

| Skill | What it does |
| --- | --- |
| [unslop](skills/unslop/SKILL.md) | Cut filler and template language from prose. |
| [no-comments](skills/no-comments/SKILL.md) | Remove redundant comments and flag unclear code. |
| [yeet](skills/yeet/SKILL.md) | Open a draft PR, fix clear review findings, and surface debatable ones. |

## Install

```bash
bunx --bun skills add ruudandriessen/rstack
```

Or use `npx skills add ruudandriessen/rstack`. Choose the skills and agent when prompted. Add `--global` to install across projects, or `--skill unslop` to pick one skill.

[Philosophy](philosophy.md) · [Contributing](CONTRIBUTING.md) · [Releases](docs/releases.md) · [MIT license](LICENSE) · [Third-party notices](THIRD_PARTY_NOTICES.md)
