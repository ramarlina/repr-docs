---
title: Team Lead Review
excerpt: Review team member contributions for performance reviews or project retrospectives
---

# Team Lead / Manager Review

**Goal:** Review team member contributions for performance reviews or project retrospectives.

## The Journey

### Step 1: Track Project Repos

```bash
repr repos add ~/code/team-project-1
repr repos add ~/code/team-project-2
```

### Step 2: Generate Summaries

```bash
repr generate --repo ~/code/team-project-1 --template changelog
```

### Step 3: Filter by Date Range

```bash
repr commits --since "2025-10-01"
```

### Step 4: Export Project Summaries

```bash
repr profile export --format md --since 2025-10-01 > Q4-review.md
```

### Step 5: View Commits for Specific Period

```bash
repr commits --repo team-project-1 --since 2025-10-01
```

### Step 6: Generate Narrative for Retrospective

```bash
repr generate --repo ~/code/team-project-1 --template narrative
```

## Creating Project Changelogs

### Generate Changelog-Style Stories

```bash
repr generate --template changelog
```

### Export as Markdown

```bash
repr profile export --format md > CHANGELOG.md
```

### Or JSON for Programmatic Use

```bash
repr profile export --format json > project-data.json
```

## Use Cases

- **Performance reviews** - Quantify contributions with data
- **Project retrospectives** - Generate comprehensive summaries
- **Release notes** - Auto-generate changelogs from commits
- **Team reports** - Aggregate work across multiple repos

## Next Steps

- Learn about [Templates](weekly-reflection.md#template-options) for different output formats
- Use [Backup & Migration](backup-migration.md) to preserve project history

