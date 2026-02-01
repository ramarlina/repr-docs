---
title: Weekly Reflection
excerpt: Review your week's work and create a polished summary
---

# Weekly Reflection

**Goal:** Review your week's work and create a polished summary.

## The Journey

### Step 1: See the Week's Overview

```bash
repr commits --days 7
```

### Step 2: Generate Stories

```bash
repr generate --local --batch-size 10
```

### Step 3: Review and Edit

```bash
repr stories
repr story view 01ARYZ6S41TSV4RRFFQ69G5FAV
repr story edit 01ARYZ6S41TSV4RRFFQ69G5FAV  # Opens in $EDITOR
```

### Step 4: Feature Best Stories

```bash
repr story feature 01ARYZ6S41TSV4RRFFQ69G5FAV
```

### Step 5: Export a Summary

```bash
repr profile export --format md --since 2026-01-01 > weekly-summary.md
```

## Template Options

### Resume/Portfolio Style (Default)

```bash
repr generate --template resume
```

Action verbs, quantified impact. Best for portfolios and resumes.

### Technical Changelog

```bash
repr generate --template changelog
```

Added/Changed/Fixed categories. Best for release notes.

### Blog/Case Study Narrative

```bash
repr generate --template narrative
```

Storytelling, problem-solving journey. Best for blog posts.

### Interview Preparation

```bash
repr generate --template interview
```

STAR format (Situation/Task/Action/Result). Best for job interviews.

See [Interview Prep](interview-prep.md) for more details.

## Template Comparison

| Template | Best For | Output Style |
|----------|----------|--------------|
| `resume` | Portfolios, resumes | Action verbs, quantified impact |
| `changelog` | Release notes | Added/Changed/Fixed categories |
| `narrative` | Blog posts | Storytelling, problem-solving journey |
| `interview` | Job interviews | STAR format |

## Next Steps

- Use [Interview Prep](interview-prep.md) workflow for job hunting
- [Publish your profile](publishing-profile.md) to repr.dev

