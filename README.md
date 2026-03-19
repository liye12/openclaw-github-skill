# openclaw-github-skill

**An OpenClaw skill for GitHub — with a built-in `gh` CLI drop-in for restricted environments.**

[![MIT License](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)

---

## What is This?

`openclaw-github-skill` is an [OpenClaw](https://github.com/openclaw/openclaw) skill that provides GitHub interaction capabilities. It bundles a lightweight `gh-wrapper` script — a pure-bash drop-in replacement for GitHub's official `gh` CLI — so it works even when `gh` cannot be installed.

> **This project is derived from and built on top of [gh-wrapper](https://github.com/liye12/gh-wrapper).** gh-wrapper is the canonical standalone implementation; this repo packages it as an OpenClaw skill.

## Features

- **gh-wrapper** — pure-bash `gh` drop-in using only `curl` and Python3
- **OpenClaw skill** — install directly into your OpenClaw workspace
- **No binary required** — works in restricted Linux containers
- **MIT licensed** — free to use, modify, and redistribute
- **Extensible** — add new subcommands by editing the shell script

## Supported Commands

| Command | Description |
|---------|-------------|
| `gh-wrapper auth status` | Show authenticated GitHub user |
| `gh-wrapper api <path>` | Call any GitHub REST API endpoint |
| `gh-wrapper pr checks <num> --repo <owner/repo>` | Show PR check runs |
| `gh-wrapper run list --repo <owner/repo> --limit N` | List workflow runs |
| `gh-wrapper run view <id> --repo <owner/repo>` | Show workflow run details |
| `gh-wrapper issue list --repo <owner/repo> --limit N` | List repository issues |
| `gh-wrapper issue view <num> --repo <owner/repo>` | Show issue details |

## Installation

### As an OpenClaw Skill

Place the skill directory in your OpenClaw workspace skills folder:
```
skills/github/
  SKILL.md
  gh-wrapper
  LICENSE
```

### Standalone

```bash
git clone https://github.com/liye12/openclaw-github-skill.git
cd openclaw-github-skill
chmod +x gh-wrapper
```

## Setup

### 1. Obtain a GitHub Personal Access Token

Generate a PAT at **GitHub → Settings → Developer Settings → Personal Access Tokens → Generate new token (classic)**.

Required scopes: `repo`, `workflow`, `read:user`

### 2. Export Your Token

```bash
export GITHUB_TOKEN="ghp_your_token_here"
# or
export TOKEN="ghp_your_token_here"
```

### 3. Run

```bash
./gh-wrapper auth status
```

## Quick Examples

```bash
# Check auth
./gh-wrapper auth status

# View repository info
./gh-wrapper api /repos/owner/repo

# List workflow runs
./gh-wrapper run list --repo owner/repo --limit 10

# View a specific run
./gh-wrapper run view 12345678 --repo owner/repo

# List issues
./gh-wrapper issue list --repo owner/repo --limit 20

# View an issue
./gh-wrapper issue view 42 --repo owner/repo

# Any REST API call
./gh-wrapper api /search/repositories?q=openclaw+language:shell
```

## Relationship to gh-wrapper

This project is a downstream extension of [gh-wrapper](https://github.com/liye12/gh-wrapper):

- **[gh-wrapper](https://github.com/liye12/gh-wrapper)** — the standalone bash script; canonical home for the wrapper implementation
- **openclaw-github-skill** — the OpenClaw skill packaging of gh-wrapper, with SKILL.md metadata for OpenClaw integration

Both projects are MIT licensed. If gh-wrapper improves upstream, please consider contributing back to [its repo](https://github.com/liye12/gh-wrapper) as well.

## License

**MIT License** — see [LICENSE](./LICENSE).  
Copyright (c) 2026 liye12

---

*Derived from [gh-wrapper](https://github.com/liye12/gh-wrapper) by [@liye12](https://github.com/liye12).*
