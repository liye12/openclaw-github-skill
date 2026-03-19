---
name: github
description: "OpenClaw GitHub skill — interact with GitHub using the gh CLI or the built-in gh-wrapper. Supports issues, PRs, workflow runs, and raw API queries. Falls back to gh-wrapper (bash+curl) when the gh binary is unavailable."
---

# GitHub Skill for OpenClaw

An OpenClaw skill providing GitHub interaction. Falls back to the bundled `gh-wrapper` when the official `gh` CLI is unavailable.

## Setup

Set your GitHub token before use:
```bash
export GITHUB_TOKEN="ghp_your_token_here"
```

## Supported Commands

| Command | Description |
|---------|-------------|
| `gh-wrapper auth status` | Show authenticated user |
| `gh-wrapper api <path>` | Call any GitHub REST API endpoint |
| `gh-wrapper pr checks <num> --repo <owner/repo>` | Show PR check runs |
| `gh-wrapper run list --repo <owner/repo> --limit N` | List workflow runs |
| `gh-wrapper run view <id> --repo <owner/repo>` | Show run details |
| `gh-wrapper issue list --repo <owner/repo> --limit N` | List issues |
| `gh-wrapper issue view <num> --repo <owner/repo>` | View issue |

## gh CLI (when available)

```bash
gh pr checks 55 --repo owner/repo
gh run list --repo owner/repo --limit 10
gh issue list --repo owner/repo --limit 20
gh api repos/owner/repo
```

## Environment Variables

| Variable | Description |
|----------|-------------|
| `GITHUB_TOKEN` | Your GitHub PAT (preferred) |
| `TOKEN` | Fallback token variable |

## License

MIT — see [LICENSE](./LICENSE) in the project root.
