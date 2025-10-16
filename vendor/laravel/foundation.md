---
title: Laravel Project Rules
scope:
  - include: ["app/**/*.php","routes/**/*.php","database/**/*.php","config/**/*.php","tests/**/*.php"]
  - exclude: ["frontend/**","src/**"]
priority: high
tags: ["laravel","backend"]
applies: auto
version: 1.1
last_review: 2025-10-11
---

# Layers
Controllers → Form Requests → Services/Actions → Policies → Models.

# Coding
- No business logic in controllers/models.
- Validation via Form Requests.
- Follow PSR-12; type declarations everywhere possible.

# PRs
- Use the global PR template (English). Link to knowledge updates.

# Guardrails
- **Validation:** use **Form Requests** only.
- **Responses:** use **API Resources/DTO**; never return Eloquent models directly.
- **API versioning:** all public endpoints under `/api/v1/**`. Breaking changes → new version/adapter.
- **Idempotency:** for `POST/PUT` require `Idempotency-Key: <uuid>`; the server stores the key/result for a TTL and returns the same response on retries.
- **Rate limiting:** configure `RateLimiter` at least on write/auth routes.
- **Performance:** avoid **N+1** (eager loading/scopes); profile hot paths (bench/Blackfire/Xdebug) and attach evidence.
- **Observability:** structured logs + metrics (RPS, p50/p95 latency, error rate) + trace spans; **never** log PII.
- **Migrations:** all changes via **migrations**; data fixes via migrations/commands with rollback.
- **Configuration:** `APP_DEBUG=false` outside dev; secrets only via env/secret manager.

# SECURITY.md — Laravel 11 + JWT

> Scope: REST API on Laravel 11 secured with stateless JWT (Bearer). This file defines minimum security baselines.

## Input Validation & Responses
- Validate **all** requests via **Form Requests** (authorize + rules).
- Serialize responses via **API Resources/DTOs** only; never return raw models.

## Rate Limiting & Idempotency
- Apply **RateLimiter** to auth-sensitive and write endpoints.
- Enforce **Idempotency-Key** (header) for non-GET writes; deduplicate via a server-side store (key → prior response/status with TTL).

## Dependencies & Static Analysis
- Run **`composer audit`** in CI; fail on vulnerabilities at or above the agreed severity.
- Enforce **Larastan/PHPStan** with strict levels (e.g., 8/9) in CI.

## Secrets & PII
- **No secrets or PII** in source code or logs.
- Redact PII in errors/logs; log only what’s necessary for operations.

## Runtime Configuration
- **`APP_DEBUG=false`** in all non-dev environments.
- Use env files/secret manager for credentials/keys; never commit `.env`.

## Logging & Observability (minimum)
- Structured logs with correlation/request IDs.
- Do **not** log JWTs, secrets, or full payloads; summarize or hash when needed.

## Token Lifecycle & Revocation
- Store `jti` (or token hash) on issue; **blocklist** on revoke/rotate.
- On key rotation or suspected breach: revoke all active tokens for the subject.

## CI Requirements (must pass on every PR)
- `composer audit` (no high/critical vulnerabilities)  
- Larastan/PHPStan strict level  
- Tests (unit/integration) for auth, rate limit, and idempotency paths

---

**Non-negotiables:** never output secrets or raw `.env` values.



