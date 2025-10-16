# CODE_REVIEW.md — Master Checklist (Laravel + Meta) — VERIFIED
- Evidence по всем Meta Gates из `/.rules/meta/AGENTS.meta.md` присутствует и валидно?
- Laravel guardrails соблюдены? (Form Requests, API Resources/DTO, JWT, RateLimiter, Idempotency‑Key, нет N+1, нет PII в логах)
- Tests: unit/feature/edge; coverage цели соблюдены; есть contract‑тесты публичных API.
- Security: composer audit; mass-assignment безопасно; секретов/PII в коде/логах нет.
- Observability: логи/метрики/трейсы добавлены; есть SLI‑заметка.
- Performance: для «горячих» участков приложен профиль/бенч.
- Dependencies: новые пакеты обоснованы и pinned; лицензии приемлемы.
