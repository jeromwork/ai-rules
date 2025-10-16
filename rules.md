# Agents — Global Operating Instructions111222333

**Last updated:** 2025-01-15

These instructions are vendor-agnostic and always apply. Project/vendor-specific rules are discovered under `/.rules/vendor/*/` and auto-scoped per file paths.

## Rule Loading & Scoping
- Load all vendor rule sets under `/.rules/vendor/*/`.
- Apply each rule **only within its `scope.include` globs**; respect `exclude`.
- Precedence: **priority > specificity > proximity**; if conflict remains, apply both within their scopes. (See `/.cursor/rules/06-scoping-and-precedence.md`).

## Safety
- Never output secrets/.env values; mask PII; follow security checklist.

# Master Rules

> **Note:** All rule files are in **English**. The assistant must **chat in Russian** by default; **code comments** and **PR descriptions** are in **Russian**.  
> The full rule set is auto‑loaded from `/.rules/**` (core, main, meta, vendor).  
> Full Meta Gates text is in `/.rules/meta/AGENTS.meta.md`.
> **Code comments & PR descriptions:** Russian. (See `/.rules/main/language-behavior.md`).

---

## 1) Mandatory Process (MUST)

1) **PLAN.md first.** Before any code, create/update `/PLAN.md` covering: scope, steps, **DoD**, verification, and **rollback**.  
   - Use `.rules/main/templates/task-template.md` as template
   - Follow `.rules/main/task-management.md` for workflow
2) Auto-load **all** rule files from `/.rules/**` (core, main, meta, vendor).
3) **Small diffs.** After each diff, run: `lint` → `typecheck` → `test` (and `sec:*` when deps/infra change). Do **not** hide failures—attach output and the fix.  
4) **Evidence for all Meta Gates.** For every PR/patch provide proof for **A, B, C, D, F, O, S, T, P, Dv, Dep, R, Org**.  
5) **Review strictly by checklist.** Use `/.rules/main/CODE_REVIEW.md` **and** `/.rules/meta/CODE_REVIEW.md`. No evidence ⇒ PR is **not** ready.
6) For every PR, attach **evidence** showing compliance with: meta gates, language policy, scoping, vendor rules, security, tests, docs/knowledge updates.
7) **Task completion.** After completing work, save task documentation and reset `PLAN.md` to TODO state.

---

## Modes (operate-by-modes)

- init → plan → implement → reflect → archive

| Mode       | Required artifact (EN)                         | Exit criteria                                      |
|------------|-----------------------------------------------|----------------------------------------------------|
| init       | Context Brief (scope, risks, open questions)  | Unknowns listed, owners assigned                   |
| plan       | PLAN.md (steps, DoD, verification, rollback)  | Aligns with repo rules; blockers/assumptions noted |
| implement  | Small diff(s) + green lint/type/test (+sec)   | CI green; docs updated if behavior changed         |
| reflect    | Change Log + WW/TTI + links to evidence       | Risks addressed; gaps captured as TODO             |
| archive    | ADR/Docs updated; links from PR               | Knowledge persisted; release notes tagged          |

## Small Diffs Policy
- Aim ≤ 200 LOC net per PR (soft cap). Split by concern if larger.

## Post-diff Sequence (MUST)
- Run: lint → typecheck → test (and sec:* when deps/infra change).
- Never hide failures; attach failing logs and the fix to PR evidence.

## Single Entry Point
- `/.rules/rules.md` is the mandatory start page linking all rule sets.

## PR Evidence (structure)
- Mode checklist(s) satisfied; CI results; scoping proof; links to ADR/Docs.

---

## 2) Full Meta Gates Reference

Read and follow `/.rules/meta/AGENTS.meta.md` **literally**.

---

## 3) Engineering Fundamentals (always)

- **McConnell (Code Complete, distilled):** reduce complexity; short functions; control nesting/cyclomatic complexity; minimal scopes; explicit contracts/asserts; table‑driven logic; no magic numbers.  
- **GoF (condensed):** encapsulate what varies; **composition over inheritance**; depend on abstractions; **OCP**; use patterns (Strategy/Template/Adapter/Facade/Decorator/Composite/Mediator/Observer) **only** when they reduce coupling/complexity.
- **SOLID & Coupling/Cohesion:** favor high cohesion and low coupling; keep public APIs minimal; expose capabilities via interfaces, not concrete classes.
- **Immutability & Purity (where practical):** prefer immutable value objects and side-effect-free helpers; minimize hidden state and temporal coupling.
- **Error Handling:** fail fast with explicit, typed errors; avoid silent catches; never swallow exceptions without logging + actionable context; return domain-level errors to callers (mapped to HTTP/problem+json in API layers).
- **Input Validation & Normalization:** validate at boundaries (controllers/transport); sanitize before use; never trust client data; normalize to canonical forms early.
- **Naming & Intent:** choose names that encode intent and units; avoid abbreviations; keep function parameters ≤ 4; use typed DTOs over unstructured maps.
- **Configuration & 12-Factor:** configuration via environment/config files only; no hard-coded constants for env-specific values; support easy switching between dev/stage/prod.
- **Feature Flags & Migration Paths:** introduce risky changes behind feature flags; define clear enable/disable/rollback procedures; keep migrations backward-compatible when possible.
- **API Design:** design for compatibility and evolvability; use versioning (v1, v2…); avoid breaking surface changes; document requests/responses including error envelopes.
- **Data Access:** prefer repositories/services to isolate persistence; prevent N+1 via eager loading; index for query patterns; use transactions only where necessary and scoped.
- **Concurrency & Idempotency:** make writes idempotent; protect critical sections (advisory locks/unique constraints); use optimistic concurrency where feasible.
- **Performance & Budgets:** establish explicit budgets (latency/CPU/memory/IO); measure with profiles/benchmarks; optimize hot paths only after evidence.
- **Security Baselines:** least privilege everywhere (DB, queues, buckets); never log secrets/PII; use prepared statements/ORM guards; review third-party deps and licenses.
- **Logging & Observability:** structured logs with correlation IDs; meaningful log levels; metrics for success/error/latency; traces for cross-boundary calls.
- **Testing Strategy:** pyramid shape (unit >> integration > e2e); property-based tests for critical invariants; contract tests for service boundaries; deterministic tests (no time/network randomness).
- **Documentation & ADRs:** document non-obvious decisions via concise ADRs; keep README and runbooks close to the code; prefer living docs over wikis.
- **Refactoring Discipline:** refactor in small, reversible steps; keep behavior constant with tests; separate mechanical refactors from semantic changes.
- **Dependency Hygiene:** pin versions; avoid heavy deps for trivial tasks; wrap external SDKs behind interfaces to isolate churn and enable testing.
- **CLI & DX:** provide reproducible scripts/Make targets for lint/typecheck/test/security; fast local feedback loops; pre-commit hooks optional but encouraged.

---

## 4) Agent Safety (MUST)

- No destructive operations (drop DB, mass rename, force‑push) without a plan and explicit confirmation in the PR.  
- Do not store or request secrets; use env/secret manager; never log PII.  
- New outbound calls/telemetry only with approval and an entry in `SECURITY.md`.  
- **Stop‑Ask‑Continue:** for ambiguity, ask up to 3 clarifying questions, then continue after answers.

---

## 5) What to Attach to Every PR (MUST)

- Updated **PLAN.md**.
- Output of **lint / typecheck / test** (+ **sec:deps** when deps changed).
- **Evidence** for all Meta Gates and for any applied vendor guardrails (SLI note, ADR link, bench/profile, etc.).
- **Rollback plan** and, if needed, feature flag / config toggle.

### Additional Required Items (recommended as MUST in most repos)

- **Issue/Ticket link**: reference to Jira/GitHub issue with acceptance criteria.
- **Scope & impact summary**: clearly list affected modules/services and data domains.
- **API changes** (if any):
  - Endpoint diffs (path, method, request/response schema, error envelope).
  - **Backward compatibility** note (breaking? version bump? adapter?).
  - Postman/HTTPie examples (copy-pasteable).
- **DB & data migration** (if any):
  - Migration files & rollback steps; **data backfill** plan and verification steps.
  - Query plan/index note for new/changed queries.
- **Security & privacy**:
  - PII handling statement; secrets redaction; threat sketch for new surfaces.
  - Outputs of `sec:*` jobs (e.g., `composer audit`) and actions taken.
- **Performance** (when relevant):
  - Budget targets (latency p50/p95, CPU/mem/IO) and **profile/bench results**.
  - Before/after measurement and environment description.
- **Observability**:
  - New/updated **metrics/logs/traces**; links to dashboards/alerts.
  - Sampling/PII redaction policy confirmation.
- **UX/UI changes** (frontend):
  - Screenshots or short GIF/video; a11y checklist (keyboard, contrast, labels).
  - i18n strings added/updated; RTL check if applicable.
- **Dependency changes**:
  - New/removed/updated deps with **rationale** and license note if needed.
- **Testing plan**:
  - What was tested (unit/integration/e2e/contract); how to reproduce locally.
  - Flakiness/seed note; **known gaps** or deferred tests (with TODO).
- **Docs & knowledge**:
  - Links to updated docs/ADRs/runbooks/changelogs; "how to operate" note.
- **Release/rollout**:
  - Deployment order, config flags, canary/gradual rollout plan.
  - **Smoke test** checklist post-deploy and **owner** for monitoring.

### Laravel-specific (only when Laravel paths are in scope)

- Command outputs for the required loop: `lint → typecheck → test` (+ `sec:*` if deps/infra changed).
- Evidence of **FormRequest** validation and **API Resource/DTO** responses.
- Note on preventing **N+1** (eager loading, scopes) with a sample query/trace.
- Migrations & rollback confirmed; `APP_DEBUG=false` on non-dev envs.

### Frontend (Vue) specific (only when frontend paths are in scope)

- Component/story links; screenshots/GIF; **a11y** checklist results.
- Type-safety note (TS), composables extracted, no secrets in bundle.
- Contract tests or examples matching backend API versions.

---

## 6) Language Policy (recap)

- **Chat with users:** Russian by default.  
- **Code comments & PR descriptions:** Russian.

---

## 7) Rule Loading, Scoping & Precedence (recap)

- Auto‑load all rules from `/.rules/**` (core, main, meta, vendor).  
- Apply rules **only within** their `scope.include` globs; respect `exclude`.  
- Precedence: **priority > specificity > proximity**; if conflict remains, apply both within their scopes.  
- Multi‑vendor (e.g., Laravel backend + Vue frontend): each vendor's rules apply **only** to their respective paths.

---

## 8) Vendor Rules (Multi-vendor)

- The assistant **must load and enforce** rules from **every** subfolder of `.rules/vendor/` (e.g., `laravel/`, `vue/`), allowing multiple stacks in one repo.
- **Precedence**: Vendor rules **augment** core rules. If conflicts arise, prefer the **most specific** rule (e.g., vendor → module → file patterns). Document deviations in PRs.

## 9) Retrieval & Precision

- Prefer concise answers. Cite only the most relevant knowledge chunks; avoid dumping unrelated context.
- When knowledge is insufficient, state that limitation explicitly and propose what to add.

## 10) Scoping Requirement

- **Every rule file must declare `scope` globs** (at least `include`). Rules **without scope** are considered global and should be used sparingly.
- When conflicts occur between vendors, apply each rule **only within its declared scope**.
