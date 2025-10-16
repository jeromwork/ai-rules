# SECURITY.md — Laravel 11 + JWT — VERIFIED
- Валидация через Form Requests; API Resources/DTO для респонсов.
- JWT Bearer на приватных маршрутах; минимальные claims; revoke при утечке; TTL/refresh по политике.
- Rate limiting через RateLimiter; идемпотентность через заголовок Idempotency‑Key и дедуп‑хранилище.
- Composer audit; строгие уровни Larastan/PHPStan; секретов/PII в коде и логах — нет; `APP_DEBUG=false` вне dev.
