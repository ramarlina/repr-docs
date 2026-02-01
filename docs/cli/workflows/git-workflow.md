---
title: Git Workflow
excerpt: Streamlined git workflow with AI-generated messages
---

# Git Workflow

repr provides a complete git workflow with AI-generated commit messages, branch names, and PR descriptions.

## The Flow

```bash
repr changes    # See what changed
repr add .py    # Stage files
repr branch     # Create feature branch (AI names it)
repr commit     # Commit (AI writes message)
repr push       # Push to remote
repr pr         # Create PR (AI writes description)
```

## Step by Step

### 1. Review Changes

```bash
repr changes
```

Shows three states:
- **Unstaged**: Modified files not yet staged (with diff preview)
- **Staged**: Changes ready to commit
- **Unpushed**: Commits not yet pushed

Use `--explain` for AI-powered change summaries:
```bash
repr changes --explain
```

### 2. Stage Files

```bash
repr add <pattern>
```

Stage files matching a pattern:
```bash
repr add .py          # Stage Python files
repr add components   # Stage files with "components" in path
repr add .            # Stage everything
```

### 3. Create Branch

```bash
repr branch
```

AI generates a descriptive branch name from your staged changes:
```
Branch: refactor/update-representations
✓ Created and switched to refactor/update-representations
```

Or specify your own:
```bash
repr branch feat/my-feature
```

### 4. Commit

```bash
repr commit
```

AI analyzes your staged changes and generates a conventional commit message:
```
Message: refactor: improve representation and documentation in code
✓ Committed
  162d186
```

Override with your own message:
```bash
repr commit -m "fix: resolve edge case in parser"
```

### 5. Push

```bash
repr push
```

Pushes to remote, setting upstream if needed.

### 6. Create PR

```bash
repr pr
```

AI generates title and description from your commits:
```
PR for 2 commits
  162d186 refactor: improve representation and documentation in code
  6a4693f feat: update CLI options and dashboard template

Title: refactor: improve code representation and documentation

✓ PR created
  https://github.com/repo/pull/12
```

Options:
```bash
repr pr --draft        # Create as draft
repr pr -t "My title"  # Custom title
```

## Caching

repr caches AI-generated content (branch names, commit messages) so you can preview before using. Use `--regenerate` or `-r` to get a fresh suggestion:

```bash
repr branch -r    # New branch name
repr commit -r    # New commit message
repr pr -r        # New PR title/body
```

## Requirements

- **Git repository**: Must be in a git repo
- **GitHub CLI**: `repr pr` requires `gh` to be installed (`brew install gh`)
- **LLM configured**: AI features need a configured LLM (local or cloud)
