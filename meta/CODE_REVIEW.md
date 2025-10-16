# CODE_REVIEW.md — Meta Checklist — VERIFIED

> Review in good faith, but be strict. If a **blocking** item fails, request changes.  
> Chat with the author in **Russian**, but keep review notes concise in **English**.

## 0) Pre-flight (Blocking)
- [ ] **Small PR** and focused scope (no drive-by changes).
- [ ] **PLAN.md** updated (scope, DoD, verification, rollback).
- [ ] **Evidence for all Meta Gates** (A,B,C,D,F,O,S,T,P,Dv,Dep,R,Org) is attached or linked.
- [ ] If Laravel paths changed → evidence for the **Laravel script loop** (`lint → typecheck → test` + `sec:*` when deps/infra changed).

## 1) Evidence & Traceability (Blocking)
- [ ] Evidence is **specific** (logs, artifacts, links), not claims.
- [ ] ADR or rationale exists for non-trivial decisions.
- [ ] Linked issue/ticket with acceptance criteria.

## 2) Design & Fundamentals
- [ ] Names are clear; functions small; comments explain **why**, not **what**.
- [ ] SOLID: high cohesion, low coupling; composition over inheritance.
- [ ] Contracts are explicit; input validation at boundaries.
- [ ] No “magic numbers”; configuration via env/config files (12-factor).

## 3) API & Compatibility (Blocking if public API)
- [ ] Public APIs are **versioned**; breaking changes use new version/adapter.
- [ ] Request/response schemas and error envelopes documented (copy-pasteable examples).
- [ ] Contract tests or examples exist; no silent wire format changes.

## 4) Data & Migrations (Blocking if schema/data changes)
- [ ] Migrations provided with **rollback**; data backfill has a plan and verification.
- [ ] Idempotency preserved; retries safe; unique/index constraints considered.
- [ ] Query plans acceptable; N+1 prevented (eager loading/indices).

## 5) Security & Privacy (Blocking)
- [ ] No secrets/PII in code, tests, or logs; secrets via manager only.
- [ ] Least privilege enforced (DB, queues, buckets, APIs).
- [ ] Supply-chain scans attached (`sec:*` outputs); new deps justified; licenses reviewed.
- [ ] New outbound calls/telemetry approved and **documented** (SECURITY note).

## 6) Observability
- [ ] Structured logs with correlation IDs; meaningful levels.
- [ ] Metrics for success/error/latency; traces on cross-boundary calls.
- [ ] SLI/SLO note included; **no PII** in telemetry.

## 7) Performance
- [ ] Correctness first; optimization guided by **profiles/benchmarks**.
- [ ] Budgets (latency p50/p95, CPU/mem/IO) stated and met when relevant.

## 8) Dependencies
- [ ] Added/updated/removed deps are **minimal** and justified.
- [ ] Versions pinned; transitive risks considered; license notes included if required.
- [ ] External SDKs wrapped behind interfaces (testability/isolation).

## 9) Testing (Blocking if unsafe changes)
- [ ] Tests cover happy paths and edge cases; deterministic and repeatable.
- [ ] Coverage floors respected (≥70% libs / ≥60% services, unless repo overrides).
- [ ] Contract/integration tests where boundary changes occur.
- [ ] Repro case or failing test included for bug fixes.

## 10) Docs & Knowledge
- [ ] README/runbooks/knowledge updated; “how to operate” notes added.
- [ ] ADRs for key decisions; links included in PR.

## 11) Release & Rollout (Blocking for risky changes)
- [ ] Feature flags or config toggles used where appropriate.
- [ ] Clear deployment order and **rollback** plan.
- [ ] Post-deploy **smoke test** checklist + responsible owner.

## 12) Frontend (only if FE files changed)
- [ ] Screenshots/GIF or Storybook links; i18n strings updated.
- [ ] Accessibility: keyboard nav, labels, contrast, focus states.
- [ ] No secrets in client bundles; API contracts match backend version.

## 13) Laravel-specific (only if Laravel paths in scope)
- [ ] **FormRequest** validation (not controller-inline).
- [ ] **API Resource/DTO** responses (no raw Eloquent in payload).
- [ ] **Script loop evidence**: `lint → typecheck → test` (+ `sec:*` if deps/infra changed).
- [ ] N+1 avoided (eager/scopes); migrations + rollback included; `APP_DEBUG=false` outside dev.

## 14) Multi-vendor Scoping (Always)
- [ ] Rules applied only within their **scope.include** globs; **exclude** respected.
- [ ] Coexistence (e.g., Laravel + Vue): each vendor’s rules affect only their own paths.
- [ ] If rules conflict: **priority → path specificity → proximity**; unresolved? document the divergence in PR.

---

### Blocking Conditions (Request Changes)
- Missing **PLAN.md** update or missing **evidence** for gates/required scripts.  
- Public API breaking change without versioning/adapter.  
- Schema/data changes without migrations/rollback plan.  
- Security/privacy violations (secrets/PII, missing scans).  
- Failing or missing tests for critical paths.

### Reviewer Actions
- Comment with **actionable**, **testable** suggestions.  
- Ask for **before/after** snippets and command outputs where unclear.  
- If ready: approve with a short English summary (what, why, risks, rollout).
