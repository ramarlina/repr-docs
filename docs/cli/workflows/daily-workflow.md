---
title: Daily Workflow
excerpt: Automatically capture your daily work with minimal friction
---

# Daily Workflow

**Goal:** Automatically capture your daily work with minimal friction.

## Approach A: Automatic Hook-Based Capture

### One-Time Setup

Install git hooks in your repositories:

```bash
repr hooks install --all
```

Now, every git commit is automatically queued (the hook runs silently, no network calls).

### Daily Routine

At end of day or week, generate stories from queued commits:

```bash
repr generate --local
```

Review what was generated:

```bash
repr stories --needs-review
```

### Interactive Review

```bash
repr review
```

**Options:**
- `[a]` Approve
- `[e]` Edit
- `[r]` Regenerate
- `[d]` Delete
- `[s]` Skip
- `[q]` Quit

## Approach B: Manual Morning Review

Quick summary of last 3 days (for standups):

```bash
repr commits --days 3
```

**Output:**
```
Commits (last 3 days) — 8 total

myproject:
  abc1234  Add user authentication flow    • 2 days ago
  def5678  Fix session timeout bug         • yesterday
  ghi9012  Implement rate limiting         • today
```

## Approach C: End-of-Day Capture

Check what you did today:

```bash
repr commits --since "this morning"
```

Generate stories from today's work:

```bash
repr generate --since "this morning" --local
```

Or generate from specific commits:

```bash
repr commits --limit 5
# Shows recent commits with SHAs

repr generate --commits abc1234,def5678,ghi9012
```

## Key Commands

| Command | Purpose |
|---------|---------|
| `repr hooks install --all` | Set up auto-capture |
| `repr generate` | Create stories from queued commits |
| `repr commits --days 3` | Quick 3-day summary |
| `repr commits --since <date>` | Commits since specific time |
| `repr review` | Interactive story review |

## Next Steps

- Set up [Weekly Reflection](weekly-reflection.md) to polish your best work
- Use different [templates](weekly-reflection.md#template-options) for various contexts

