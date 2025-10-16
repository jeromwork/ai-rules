# Agents Index

This file indexes all rule files and serves as an entrypoint for agents.

## Rule Files
- [main/AGENTS.meta.md](.rules/main/AGENTS.meta.md)
- [main/CODE_REVIEW-1.md](.rules/main/CODE_REVIEW-1.md)
- [main/.rules/main/CODE_REVIEW.md](.rules/main/.rules/main/CODE_REVIEW.md)
- [main/CONTRIBUTING.md](.rules/main/CONTRIBUTING.md)
- [main/PLAN-1.md](.rules/main/PLAN-1.md)
- [main/PLAN.md](.rules/main/PLAN.md)
- [main/SECURITY-1.md](.rules/main/SECURITY-1.md)
- [main/SECURITY.md](.rules/main/SECURITY.md)
- [main/checklists/observability-checklist.md](.rules/main/checklists/observability-checklist.md)
- [main/checklists/security-checklist.md](.rules/main/checklists/security-checklist.md)
- [main/checklists/validation-checklist.md](.rules/main/checklists/validation-checklist.md)
- [main/language-behavior.md](.rules/main/language-behavior.md)
- [main/task-management.md](.rules/main/task-management.md)
- [vendor/laravel/docs-management.md](.rules/vendor/laravel/docs-management.md)
- [main/process/archive.md](.rules/main/process/archive.md)
- [main/process/implement.md](.rules/main/process/implement.md)
- [main/process/init.md](.rules/main/process/init.md)
- [main/process/PLAN.md](.rules/main/process/PLAN.md)
- [main/process/reflect.md](.rules/main/process/reflect.md)
- [main/pull-request-description.md](.rules/main/pull-request-description.md)
- [rules.md](.rules/rules.md)
- [vendor/laravel/foundation.md](.rules/vendor/laravel/foundation.md)

> Structure: reusable rules in `.rules/main/`, vendor-specific rules in `.rules/vendor/<name>/`.  
> Core entrypoint: `.rules/rules.md`. Cursor auto-loads **all** vendor rules via `/.cursor/rules/05-vendor-loader.md`.
