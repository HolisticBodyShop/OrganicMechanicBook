---
name: skill-name
description: One-line description of what this skill does. This is how Claude discovers when to use it.
---

# Skill Name

Brief description of the skill's purpose and when to use it.

## Trigger

How this skill is activated:
- Via command: `/namespace:command-name`
- Auto-discovered when user provides [specific content type]

## Prerequisites

- [ ] Required files/context
- [ ] User permissions needed

## Workflow

### Step 1: [Action Name]

Description of what happens in this step.

**Parallel operations** (if applicable):
- Task A
- Task B
- Task C

### Step 2: [Action Name]

Description of next step.

| Input | Output | Notes |
|-------|--------|-------|
| ... | ... | ... |

### Step 3: [Action Name]

Continue with remaining steps...

---

## Decision Points

| Condition | Action |
|-----------|--------|
| If X | Do Y |
| If A | Do B |

---

## Quality Checks

- [ ] Check 1
- [ ] Check 2
- [ ] Check 3

---

## Logging

Append to `.claude/usage-log.md`:
```
| /command-name | [date] | [outcome] | [notes] |
```

**Outcome codes:** `SUCCESS`, `PARTIAL`, `FAILED`

---

## Reference Files

- [File 1](path/to/file1.md) - Description
- [File 2](path/to/file2.md) - Description
