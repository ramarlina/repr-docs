---
title: Commands
excerpt: Complete reference for all Repr CLI commands
---

# Command Reference

### `repr analyze`
Analyze repositories and generate profiles (auto-pushed to repr.dev).

```bash
repr analyze <paths...> [OPTIONS]
```

**Options:**
- `--local, -l`: Use local LLM (Ollama) instead of cloud.
- `--model, -m NAME`: Local model to use (default: llama3.2).
- `--api-base URL`: Custom local LLM API endpoint.
- `--offline`: Stats only, no AI analysis (no push).
- `--no-cache`: Re-analyze all repositories (ignore cache).
- `--min-commits N`: Minimum commits required to include a repo (default: 10).
- `--since TEXT`: Only analyze commits after this point (SHA or date like `2026-01-01`).
- `--verbose, -V`: Show detailed logs during analysis.
- `--json`: Output progress as JSON (for machine consumption / extension).

**Examples:**
```bash
repr login                                  # Authenticate for cloud/sync
repr analyze ~/code                          # Cloud (default)
repr analyze ~/code --local --model llama3.2 # Local LLM (Ollama)
repr analyze ~/code --offline                # Stats only, no push
repr analyze ~/code --since 2026-01-01       # Only recent commits
repr analyze ~/code --json                   # JSON progress for extension
```

---

### `repr view`
View a profile in the terminal.

```bash
repr view [OPTIONS]
```

**Options:**
- `--raw, -r`: Output plain markdown (for piping).
- `--json`: Output content + metadata as JSON.
- `--profile, -p NAME`: View a specific profile by name.

**Examples:**
```bash
repr view                                # View latest profile
repr view --profile myrepo_2025-12-26    # View specific profile
repr view --raw > profile.md             # Export to file
repr view --json                         # Machine-readable output
```

---

### `repr push`
Push local profiles to repr.dev.

```bash
repr push [OPTIONS]
```

**Options:**
- `--profile, -p NAME`: Push a specific profile (default: all unsynced profiles).

**Examples:**
```bash
repr push                                # Push all unsynced profiles
repr push --profile myrepo_2025-12-26    # Push specific profile
```

---

### `repr login`
Authenticate with Repr using device code flow.

```bash
repr login
```

Opens a browser where you can sign in, then automatically completes authentication.

---

### `repr logout`
Clear authentication and logout.

```bash
repr logout
```

---

### `repr profiles`
List all saved profiles.

```bash
repr profiles [--json]
```

Shows profile names, project counts, sizes, and sync status.

---

### `repr config`
Show current configuration and API endpoints.

```bash
repr config
repr --dev config    # Show config in dev mode
repr config --json
```

---

### `repr config-set`
Configure LLM models and local API settings.

```bash
repr config-set [OPTIONS]
```

**Options:**
- `--extraction-model MODEL`: Model for extracting accomplishments (e.g., gpt-4o-mini, llama3.2).
- `--synthesis-model MODEL`: Model for synthesizing the final profile (e.g., gpt-4o, llama3.2).
- `--local-api-url URL`: Local LLM API base URL (e.g., http://localhost:11434/v1).
- `--local-api-key KEY`: Local LLM API key (e.g., 'ollama' for Ollama).
- `--clear`: Clear all LLM configuration.

**Examples:**
```bash
# Set models for cloud analysis
repr config-set --extraction-model gpt-4o-mini --synthesis-model gpt-4o

# Configure local LLM (Ollama)
repr config-set --local-api-url http://localhost:11434/v1 --local-api-key ollama
repr config-set --extraction-model llama3.2 --synthesis-model llama3.2

# Configure local LLM (LM Studio)
repr config-set --local-api-url http://localhost:1234/v1 --local-api-key lm-studio

# Clear all LLM settings
repr config-set --clear
```

---

### `repr status`
Show CLI status (auth, profiles, sync state).

```bash
repr status [--json]
```

---

### `repr whoami`
Show current user info and public profile URL.

```bash
repr whoami [--json]
```

---

---

## Git Workflow Commands

These commands streamline the git workflow with AI-generated messages.

### `repr changes`
Show file changes across git states with diff details.

```bash
repr changes [PATH] [OPTIONS]
```

**Options:**
- `--explain, -e`: Use LLM to explain changes.
- `--compact, -c`: Compact output (no diff previews).
- `--json`: Output as JSON.

**Examples:**
```bash
repr changes                # Show changes with diffs
repr changes --explain      # AI explains what changed
repr changes --compact      # Summary without diffs
```

---

### `repr add`
Stage files matching a pattern.

```bash
repr add <pattern> [OPTIONS]
```

**Options:**
- `--force, -f`: Force add ignored files.

**Examples:**
```bash
repr add cli              # Stage files containing "cli"
repr add .py              # Stage files containing ".py"
repr add .                # Stage all
repr add cli -f           # Force add ignored files
```

---

### `repr branch`
Create and switch to a new branch.

```bash
repr branch [NAME] [OPTIONS]
```

**Options:**
- `--regenerate, -r`: Regenerate branch name.

If no name is given, generates one from staged or unpushed changes using AI.

**Examples:**
```bash
repr branch                    # AI generates name
repr branch feat/my-feature    # Use explicit name
repr branch -r                 # Regenerate name
```

---

### `repr commit`
Generate commit message and commit staged changes.

```bash
repr commit [OPTIONS]
```

**Options:**
- `--message, -m TEXT`: Custom message (skip AI).
- `--regenerate, -r`: Regenerate message.
- `--yes, -y`: Skip confirmation on main/master.

**Examples:**
```bash
repr commit                    # Generate and commit
repr commit -m "fix: typo"     # Custom message
repr commit -r                 # Regenerate message
```

---

### `repr push`
Push commits to remote.

```bash
repr push
```

Sets upstream if needed on first push.

---

### `repr pr`
Create a pull request with AI-generated title and description.

```bash
repr pr [OPTIONS]
```

**Options:**
- `--title, -t TEXT`: Custom PR title.
- `--draft, -d`: Create as draft PR.
- `--regenerate, -r`: Regenerate title/body.

Requires GitHub CLI (`gh`) to be installed.

**Examples:**
```bash
repr pr                    # AI generates title/body
repr pr -t "feat: add X"   # Custom title
repr pr --draft            # Create draft PR
```

---

### `repr stories`
List commit stories (stored on repr.dev).

```bash
repr stories [OPTIONS]
```

**Options:**
- `--repo TEXT`: Filter by repository name.
- `--since TEXT`: Filter by date (e.g., `1 week ago`, `2026-01-01`).
- `--technologies TEXT`: Filter by technology (comma-separated, e.g. `React,FastAPI`).
- `--limit N`: Max stories to return (default: 50).
- `--json`: Output as JSON.

---

### `repr repos`
Manage tracked repositories.

```bash
repr repos list [--json]
repr repos add <path>
repr repos remove <path>
repr repos scan [--json]
```

---

### `repr sync`
Sync tracked repositories (analyze new commits since last sync and push updates).

```bash
repr sync [OPTIONS]
```

**Options:**
- `--repo PATH`: Sync a specific tracked repo by path.
- `--all`: Force sync (ignore last sync).
- `--background`: Run silently (for hooks/automation).
- `--json`: Output as JSON.

---

### `repr hook`
Manage git post-commit hooks for automatic syncing.

```bash
repr hook install [--repo <path> | --all]
repr hook remove  [--repo <path> | --all]
repr hook status  [--json]
```
