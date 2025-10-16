---
title: Task Template
priority: high
tags: ["template", "task", "workflow"]
applies: auto
version: 1.0
last_review: 2025-10-13
---

# AI Agent Rules for Task Creation
- **Task creation:** Only when completing branch work and creating PR
- **Language:** Russian for task content and retrospective
- **Always ask:** "Do you need to create a retrospective for this task?"
- **Date source:** Git history of current branch
- **Multi-day detection:** Check git log dates - if work spans multiple days, use DD-DD format
- **PR message inclusion:** Always include ready-to-copy PR message in task file

# Task: [Task Name]
**Date:** [YYYY-MM-DD]
**Type:** [feature|bug|refactor|hotfix|optimization|migration|security]
**Priority:** [high|medium|low]
**Estimated Time:** [X hours]

## 1. Task Description
**Goal:** [Clear goal statement]
**Context:** [Background and context]
**Constraints:** [Technical and business constraints]

## 2. Technical Solution
**Approach:** [High-level approach]
**Architecture:** 
- [Key architectural decisions]
- [Technology choices]
- [Integration points]
**Dependencies:** [External dependencies]

## 3. Execution Plan
- [ ] [Step 1]
- [ ] [Step 2]
- [ ] [Step 3]
- [ ] [Step 4]

## 4. Definition of Done (DoD)
- [ ] [Criteria 1]
- [ ] [Criteria 2]
- [ ] [Criteria 3]
- [ ] [Criteria 4]

## 5. Risks and Mitigations
**Risk 1:** [Description] → **Mitigation:** [Solution]
**Risk 2:** [Description] → **Mitigation:** [Solution]
**Risk 3:** [Description] → **Mitigation:** [Solution]

## 6. Rollback Plan
[Description of rollback strategy and steps]

## 7. Meta Gates Checklist
- [ ] Gate A: System Thinking - Goals & constraints defined
- [ ] Gate B: Manage Complexity - KISS, DRY, YAGNI applied
- [ ] Gate C: Architecture & Boundaries - Clear modules/interfaces
- [ ] Gate D: Data & Consistency - Source of Truth declared
- [ ] Gate F: Reliability & Resilience - Timeouts, retries, circuit breakers
- [ ] Gate O: Observability - Structured logs, metrics, traces
- [ ] Gate S: Security by Default - Least privilege, no secrets
- [ ] Gate T: Testing & Verification - Tests added, coverage met
- [ ] Gate P: Performance - Budgets defined and met
- [ ] Gate Dv: Delivery & Change Management - Small PRs, feature flags
- [ ] Gate Dep: Dependencies & External Services - Minimal deps, timeouts
- [ ] Gate R: Readability & API Design - Clear names, small functions
- [ ] Gate Org: Teams & Knowledge - Documentation updated

## 8. Implementation Log
- [Date] [Action taken]
- [Date] [Decision made]
- [Date] [Issue encountered and resolution]

## 9. PR Description

### Готовое PR сообщение

```
# [Заголовок PR]

## Краткое описание
[Краткое описание изменений]

## Область изменений
- [Изменение 1]
- [Изменение 2]
- [Изменение 3]

## Тип изменений
- [x] Новая функциональность
- [ ] Исправление ошибки
- [ ] Рефакторинг
- [ ] Оптимизация
- [ ] Миграция данных
- [ ] Безопасность

## Детали реализации
[Подробное описание реализации]

## Тестирование
- [ ] Выполнено ручное тестирование
- [ ] Добавлены/обновлены unit тесты
- [ ] Добавлены/обновлены интеграционные тесты
- [ ] Покрытие тестами: [X]%

## Безопасность
- [ ] Нет утечек секретов/PII
- [ ] Валидация входных данных
- [ ] Выполнен аудит зависимостей

## Производительность
- [ ] Выполнены бенчмарки
- [ ] Проведено профилирование
- [ ] Бюджеты соблюдены

## Документация
- [ ] Обновлен README
- [ ] Обновлена документация API
- [ ] Создан/обновлен ADR

## Метаданные
- **Автор:** [Имя]
- **Дата:** [YYYY-MM-DD]
- **Ветка:** [имя-ветки]
- **Коммитов:** [количество]
- **Связанные задачи:** [Ссылки на связанные задачи]
```

### Дополнительная информация:
**Summary:** [Brief summary of changes]

**Scope:**
- [File/component 1]
- [File/component 2]
- [File/component 3]

**Type of Changes:**
- [ ] New functionality
- [ ] Bug fix
- [ ] Refactoring
- [ ] Optimization
- [ ] Data migration
- [ ] Security

**Implementation Details:**
[Detailed description of implementation]

**Testing:**
- [ ] Manual testing performed
- [ ] Unit tests added/updated
- [ ] Integration tests added/updated
- [ ] Test coverage: [X]%

**Security:**
- [ ] No secrets/PII leaks
- [ ] Input validation
- [ ] Dependency audit performed

**Performance:**
- [ ] Benchmarks performed
- [ ] Profiling conducted
- [ ] Budgets met

**Documentation:**
- [ ] README updated
- [ ] API documentation updated
- [ ] ADR created/updated

**Metadata:**
**Author:** [Name]
**Date:** [YYYY-MM-DD]
**Branch:** [branch-name]
**Commit:** [commit-hash]
**Related Tasks:** [Links to related tasks]

## 10. Retrospective

**What was done:**
- [Achievement 1]
- [Achievement 2]
- [Achievement 3]

**What went well:**
- [Success 1]
- [Success 2]
- [Success 3]

**What could be improved:**
- [Improvement 1]
- [Improvement 2]
- [Improvement 3]

**Lessons learned:**
- [Lesson 1]
- [Lesson 2]
- [Lesson 3]

**Metrics:**
- Execution time: [X hours]
- Files created/modified: [X]
- Tests added: [X]
- Coverage: [X]%

**Links:**
- [Link to PLAN.md]
- [Link to AGENTS.md]
- [Link to related documentation]
