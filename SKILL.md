---
name: long-running-work
description: Best practices for long-running automated tasks. Suitable for cron jobs, sub-agent tasks, and multi-step complex tasks. Load this skill when executing time-consuming tasks, delegating to sub-agents, or handling complex work.
---

# Long-Running Work - Best Practices

## Core Principles

### 1. Before Starting - Define Goals

- **Read project docs**: PROJECT.md + PLAN.md
- **Define acceptance criteria**: What does "done" look like?
- **Plan steps**: Break into small, verifiable steps
- **Set checkpoints**: Use checkpoint mode for complex tasks

### 2. During Execution - Maintain State

- **Save regularly**: Save progress after each key step
- **Verify results**: Verify immediately after each step, not at the end
- **Log decisions**: Write key decisions/discoveries to Diaries/YYYY-MM-DD.md
- **Handle errors**: API 429 → wait and retry; timeout → increase timeout

### 3. After Completion - Cleanup & Report

- **Verify final results**: Don't assume success, actually check
- **Update docs**:
  - PROJECT.md - project status
  - PLAN.md - checkpoint completion
  - MEMORY.md - key learnings
- **Send report**: Concise Telegram message

## Sub-agent Management

When delegating tasks:

### Task Description Template

```
## Task Goal
[What exactly to complete]

## Acceptance Criteria
1. [Verifiable criteria 1]
2. [Verifiable criteria 2]

## Execution Steps
1. [Step 1]
2. [Step 2]

## Notes
- [Special requirements or constraints]
```

### Result Review

- Check git diff
- Verify test results
- Confirm docs updated
- If issues, have sub-agent fix until satisfied

## Checkpoint Mode Example

```bash
# Save after each key step
python3 checkpoint_manager.py save fetch "done"
python3 checkpoint_manager.py save analyze "done"
python3 checkpoint_manager.py save html "done"
python3 checkpoint_manager.py save deploy "done"

# Clear after completion
python3 checkpoint_manager.py clear
```

## Common Error Handling

| Error | Handling |
|-------|----------|
| API 429 | Wait 30s, retry up to 3 times |
| Timeout | Increase timeoutSeconds |
| Verification failed | Fix and redeploy, verify again |
| Push failed | Check Telegram config |

## Verification Checklist

After completing any task, must verify:

- [ ] Code/deployment actually works (not just "think" it works)
- [ ] Relevant docs updated
- [ ] Git committed
- [ ] Telegram report sent
- [ ] Diary written
