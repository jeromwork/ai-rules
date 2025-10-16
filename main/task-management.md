---
title: Task Management Rules
priority: high
tags: ["task", "management", "workflow"]
applies: auto
version: 1.0
last_review: 2025-10-13
---

# Task Management Rules

## Before Starting Work
1. Copy `.rules/main/templates/task-template.md` to `PLAN.md`
2. Fill in all template fields
3. Determine task type and create unique filename
4. Record start date from git history
5. **Auto-create directories:** Create `docs/tasks/YYYY/MM/` if not exists

## During Work
1. Update `PLAN.md` as work progresses
2. Check off completed checklist items
3. Record important decisions and changes
4. Maintain implementation log

## After Completing Work (When Creating PR)
1. **Auto-create directories:** Ensure `docs/tasks/YYYY/MM/` exists
2. Copy final `PLAN.md` to `docs/tasks/YYYY/MM/DD_task-type_task-name.md` (single day) or `DD-DD_task-type_task-name.md` (multi-day)
3. **Always ask:** "Do you need to create a retrospective for this task?"
4. If yes - fill in the Retrospective section in the same file
5. Reset `PLAN.md` to original TODO state for next task

## AI Agent Rules
- **Task creation:** Only when completing branch work and creating PR
- **Language for tasks and retrospectives:** Russian
- **Always ask about retrospective:** "Do you need to create a retrospective for this task?"
- **Date source:** Git history of current branch
- **Multi-day detection:** Check git log dates - if work spans multiple days, use DD-DD format
- **PR message inclusion:** Always include ready-to-copy PR message in task file

## When Creating PR Message
1. Fill in the "PR Description" section in current `PLAN.md`
2. **Always ask:** "Do you need to create a retrospective for this task?"
3. **Include ready-to-copy PR message:** Always provide complete PR message in code block for easy copying

## File Naming Convention
**Format:** `DD_task-type_task-name.md` (single day) or `DD-DD_task-type_task-name.md` (multi-day)

**Source of date:** Git history of current branch
**Task creation:** When committing work
**Examples:**
- `12_feature_task-management-system.md` (single day)
- `09-12_feature_user-authentication.md` (multi-day: started 9th, finished 12th)
- `15_bug_fix-payment-gateway.md` (single day)
- `18-20_refactor_content-service.md` (multi-day: started 18th, finished 20th)

**Task Types:**
- `feature` - new functionality
- `bug` - bug fix
- `refactor` - refactoring
- `hotfix` - critical fix
- `optimization` - performance optimization
- `migration` - data migration
- `security` - security-related changes

## Directory Structure
```
docs/
└── tasks/
    ├── 2024/
    │   ├── 10/
    │   │   ├── 12_feature_task-management.md
    │   │   ├── 15_bug_fix-payment.md
    │   │   └── 18-20_refactor_content-service.md
    │   └── 11/
    └── 2025/
        └── 10/
            ├── 09_feature_monitoring-system.md
            ├── 11_bug_fix-unit-tests.md
            └── 12_feature_task-management-system.md
```

## Multi-day Task Rules
- **Single day:** Use format `DD_task-type_name.md`
- **Multi-day:** Use format `DD-DD_task-type_name.md` where:
  - First DD = start day from git history
  - Second DD = end day from git history
  - Get dates from `git log --format="%ad" --date=short` for current branch

## Auto-directory Creation
- Check git history for date range of current branch
- Create `docs/tasks/YYYY/MM/` directory structure
- Use earliest and latest dates from git log for multi-day tasks
- For single-day tasks, use the commit date

## Task Completion Checklist
- [ ] All Meta Gates evidence provided
- [ ] Tests added/updated
- [ ] Documentation updated
- [ ] PR description filled with ready-to-copy message
- [ ] Task saved to `docs/tasks/YYYY/MM/`
- [ ] Retrospective completed (if requested)
- [ ] `PLAN.md` reset to TODO state
