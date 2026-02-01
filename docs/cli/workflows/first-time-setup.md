---
title: First-Time Setup
excerpt: Get repr set up and generate your first stories from existing work
---

# First-Time Setup

**Goal:** Get repr set up and generate your first stories from existing work.

## Installation

First, install repr using your preferred method:

```bash
# Via pipx (recommended)
pipx install repr-cli

# Or via Homebrew
brew tap repr-app/tap
brew install repr
```

See the [Installation guide](../installation.md) for more options.

## The Journey

### Step 1: Initialize

Scan for repositories and set up local config:

```bash
repr init ~/code
```

**Output:**
```
Found 12 repositories
✓ myproject (143 commits) [Python]
✓ frontend-app (87 commits) [TypeScript]
...
Track these repositories? [Y/n]
```

### Step 2: Preview Your Work

See what you've been working on this week:

```bash
repr commits --days 7
```

### Step 3: Generate Stories

Generate your first stories locally:

```bash
repr generate --local
```

**Output:**
```
Generating stories (local LLM)...
myproject
  • Built OAuth2 integration with Google and GitHub providers
  • Implemented Redis caching layer for session management
Generated 2 stories
Stories saved to: ~/.repr/stories
```

### Step 4: View Stories

```bash
repr stories
repr story view <id>
```

### Step 5: (Optional) Enable Cloud Features

```bash
repr login
```

## Key Commands

| Command | Purpose |
|---------|---------|
| `repr init [path]` | First-time setup, discover repos |
| `repr commits --days 7` | Preview recent work |
| `repr generate --local` | Create stories using local LLM |
| `repr stories` | View generated stories |
| `repr login` | Enable cloud sync (optional) |

## Next Steps

- Set up [Daily Workflow](daily-workflow.md) for automatic capture
- Configure [Privacy settings](privacy-local-only.md) for local-only mode
- Learn about [templates](weekly-reflection.md#different-template-options) for different output styles

