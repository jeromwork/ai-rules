# AGENTS.meta.md — Universal Meta Rules (Gates) for AI Coding Agents — VERIFIED

> **Note:** All rule files are written in **English**. The assistant must **chat in Russian** by default; **code comments** and **PR descriptions** are in **English**.  
> Reviewers enforce these gates using `/.rules/meta/CODE_REVIEW.md`.  
> The complete rule set is auto-loaded from `/.rules/**` (core, main, meta, vendor).

## Mandatory Workflow (MUST)
1) **PLAN.md first:** Create/refresh `/PLAN.md` (scope, steps, **Definition of Done**, verification, rollback).
2) **Small diffs:** Implement in small, focused diffs; after each diff run project checks: `lint`, `typecheck`, `test` (+ `sec:*` as needed). Attach failures and fixes.
3) **Evidence for ALL Gates:** Provide explicit evidence for **A, B, C, D, F** plus **O, S, T, P, Dv, Dep, R, Org**.

---
## Gate A — System Thinking (from our #1)
- Define **goals** & **constraints** (reliability, scalability, latency, security, cost).
- Map risks/assumptions. Trace decisions via **ADR** files.

**Evidence (MUST):** problem statement, quality attributes list, ADR link (e.g., `/docs/adr/XXXX-title.md`).

## Gate B — Manage Complexity (from our #2)
- Apply **KISS**, **DRY**, **YAGNI**.
- Decompose by **lines of change**; encapsulate variability.
- Prefer **composition over inheritance**; program to **interfaces**.

**Evidence:** removed duplication/simplification diff; chosen abstractions & rationale.

## Gate C — Architecture & Boundaries (from our #3)
- Clear modules/domains; minimal, stable interfaces.
- **Dependencies point inward** (details depend on abstractions).
- **Version contracts**; use adapters; **isolate failures** across boundaries.

**Evidence:** module map & impacted interfaces; versioning/adapter plan.

## Gate D — Data & Consistency (from our #4)
- Declare **Source of Truth**; caches are derivatives.
- **Idempotent** operations; retries safe.
- Prefer **compensations** over distributed transactions.

**Evidence:** data flow & SoT; idempotency/compensation strategy.

## Gate F — Reliability & Resilience (from our #6)
- Timeouts; retries with **jitter**; **circuit breaker**; **backpressure**; quotas/limits.
- Design for recovery: tested backups; roll-forward/backward paths.

**Evidence:** timeouts/limits config; failure-mode note; recovery test steps.

## Gate O — Observability
- Structured logs/metrics/traces; **SLI/SLO** for critical endpoints; NO PII in logs.

**Evidence:** metrics/traces added; SLI note (e.g., p95 threshold @ target RPS).

## Gate S — Security by Default
- Least privilege; secrets via manager; pinned deps/SBOM (if available).
- No secrets in code/tests/logs; supply-chain scanning; threat review for new surfaces.

**Evidence:** security checklist results; dependency audit output; threat notes if applicable.

## Gate T — Testing & Verification
- Contract + unit (many), integration (enough), e2e (minimal). Property-based where helpful.
- Default coverage floors: **≥70% libs / ≥60% services** (override in repo if needed).

**Evidence:** tests list & results; coverage/CI artifacts; bug-fix repro & failing-test proof when fixing defects.

## Gate P — Performance
- Correctness first; **profile before optimizing**.
- Define budgets (latency/CPU/mem/IO); validate when relevant.

**Evidence:** benchmark/profile diffs; confirmation budgets are met.

## Gate Dv — Delivery & Change Management
- Small PRs; trunk-based; CI green; feature flags; canary/rollback notes.

**Evidence:** rollout/rollback plan; flag/config toggles.

## Gate Dep — Dependencies & External Services
- Minimize deps; pin versions; justify new deps; wrap external calls with timeouts/fallbacks.

**Evidence:** dep rationale; interface & timeout config; license note if required.

## Gate R — Readability & API Design
- Human-first names; small functions; explicit errors; comments explain **why**; predictable, versioned APIs.

**Evidence:** before/after snippets; API docs excerpt.

## Gate Org — Teams & Knowledge
- Stream-aligned ownership; paved roads; ADRs/runbooks; blameless postmortems.

**Evidence:** links to docs/runbooks; ownership mapping.

---
## Classical Foundations (MUST)
- **McConnell (Code Complete distilled):** reduce complexity first, control nesting/cyclomatic complexity, minimal scope, explicit contracts/asserts, table-driven logic, avoid magic numbers.
- **GoF distilled:** encapsulate variability; depend on abstractions; prefer composition; OCP; Strategy/Template/Adapter/Facade/Decorator/Composite/Mediator/Observer **only if they reduce coupling/complexity**.

## Agent Safety Policy (MUST)
- No destructive ops (drops, mass renames, force-push) without plan & explicit approval.
- No secrets in code/tests/logs; never request user tokens.
- No new outbound calls/telemetry without approval + Security notes.
- **Stop-Ask-Continue:** ask ≤3 clear questions if requirements are ambiguous.

---
*Last updated: 2025-10-11*
