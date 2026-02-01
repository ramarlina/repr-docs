---
title: Command Quick Reference
excerpt: Quick reference for all repr commands
---

# Command Reference

Quick reference for all repr commands.

## Setup & Status

```bash
repr init [path]           # First-time setup
repr status                # Overall health
repr mode                  # Execution mode
repr doctor                # Full diagnostics
repr whoami                # Current user
```

## Story Generation

```bash
repr generate --local      # Generate with local LLM
repr generate --cloud      # Generate with cloud LLM
repr generate --template X # Use template (resume/changelog/narrative/interview)
repr generate --dry-run    # Preview what would be sent
```

## Git Workflow

```bash
repr changes               # Show staged/unstaged/unpushed changes
repr changes --explain     # Use LLM to explain changes
repr changes --compact     # Compact output (no diffs)
repr add .py               # Stage files matching pattern
repr add .                 # Stage all files
repr add cli -f            # Force add ignored files
repr branch                # Create branch (AI-generated name)
repr branch feat/my-feat   # Create branch with explicit name
repr branch -r             # Regenerate branch name
repr commit                # Generate message and commit
repr commit -m "fix: typo" # Custom message
repr commit -r             # Regenerate message
repr push                  # Push commits to remote
repr pr                    # Create PR (AI-generated title/body)
repr pr -t "feat: add X"   # Custom PR title
repr pr --draft            # Create draft PR
```

## Commits

```bash
repr commits               # Recent commits
repr commits --days 7      # Last 7 days (week)
repr commits --days 3      # Last 3 days (standup)
repr commits --since "monday"  # Since specific date
repr commits --repo myproject  # Filter by repo
```

## Story Management

```bash
repr stories               # List all stories
repr story view <id>       # View story content
repr story edit <id>       # Edit in $EDITOR
repr story delete <id>     # Delete story
repr story hide <id>       # Hide from profile
repr story feature <id>    # Pin to profile top
repr review                # Interactive review
```

## Repository Management

```bash
repr repos                 # List tracked repos
repr repos add <path>      # Add repo
repr repos remove <path>   # Remove repo
repr repos pause <path>    # Pause tracking
repr repos resume <path>   # Resume tracking
```

## Hooks

```bash
repr hooks install --all   # Install in all repos
repr hooks remove --all    # Remove from all repos
repr hooks status          # Check hook status
```

## Cloud Operations

```bash
repr login                 # Sign in
repr logout                # Sign out
repr push                  # Publish stories
repr push --dry-run        # Preview push
repr sync                  # Bidirectional sync
repr pull                  # Pull from cloud
```

## LLM Configuration

```bash
repr llm configure         # Interactive setup
repr llm test              # Test connection
repr llm add <provider>    # Add BYOK provider
repr llm remove <provider> # Remove BYOK
repr llm use <mode>        # Set default (local/cloud/byok:X)
```

## Privacy

```bash
repr privacy explain       # Privacy summary
repr privacy audit         # What was sent to cloud
repr privacy lock-local    # Disable cloud
repr privacy unlock-local  # Re-enable cloud
```

## Profile & Export

```bash
repr profile               # View profile
repr profile export --format md   # Export as Markdown
repr profile export --format json # Export as JSON
repr profile link          # Get public URL
```

## Data Management

```bash
repr data                  # Storage stats
repr data backup -o FILE   # Create backup
repr data restore FILE     # Restore from backup
repr data clear-cache      # Clear cache
```

## Configuration

```bash
repr config show           # Show all config
repr config show llm.default  # Show specific key
repr config set key value  # Set value
repr config edit           # Open in $EDITOR
```

## Templates

| Template | Use Case | Output Style |
|----------|----------|--------------|
| `resume` | Portfolios, resumes | Action verbs, quantified impact |
| `changelog` | Release notes | Added/Changed/Fixed categories |
| `narrative` | Blog posts | Storytelling, problem-solving |
| `interview` | Job interviews | STAR format |

## Privacy Modes

| Mode | Command | Behavior |
|------|---------|----------|
| **Local LLM** | `repr generate --local` | Localhost only |
| **BYOK** | `repr llm add <provider>` | Direct provider calls |
| **Cloud** | `repr generate --cloud` | User-initiated network |
| **Offline** | `repr commits` / `repr stories` | Pure local ops |

## Getting Help

```bash
repr --help
repr <command> --help
```

