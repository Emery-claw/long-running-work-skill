# Long-Running Work Skill - Plan

## Goal

Create a skill to maintain good workflow and working habits during long-running automated tasks.

## Skill Overview

- **Name**: `long-running-work`
- **Purpose**: Best practices for long-running automated tasks (cron jobs, sub-agents)
- **Trigger**: When executing time-consuming tasks, delegating to sub-agents, or handling complex multi-step work

## Content to Include

### 1. Pre-execution Guidelines
- [x] Check project status (PROJECT.md, PLAN.md)
- [x] Confirm task goals and acceptance criteria
- [x] Plan steps and checkpoints

### 2. Execution Guidelines
- [x] Save progress regularly (checkpoint)
- [x] Verify results after each step
- [x] Log key decisions to diary

### 3. Post-execution Guidelines
- [x] Verify final results
- [x] Update relevant docs (MEMORY.md, PROJECT.md, PLAN.md)
- [x] Report completion status

### 4. Sub-agent Management
- [x] Clear task descriptions
- [x] Define acceptance criteria
- [x] Result review process

### 5. Error Handling
- [x] API rate limiting handling
- [x] Timeout handling
- [x] Error recovery

## Reference Files

- `~/.openclaw/workspace/AGENTS.md` - Working rules
- `~/.openclaw/workspace/IDLE.md` - Idle work guide
- `~/.openclaw/workspace/HEARTBEAT.md` - Heartbeat workflow

## Execution Steps

1. Create SKILL.md ✅
2. Create references/ directory (optional)
3. Test skill trigger
4. Update HEARTBEAT.md to reference this skill ✅

## Status: Completed ✅
