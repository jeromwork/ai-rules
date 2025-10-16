# Core Rules (Vendor-agnostic, Multi-vendor)

**Last updated:** 2025-10-11

These global rules apply across systems. **All vendor rule sets** under `.rules/vendor/*/` are **auto-loaded** and enforced alongside the core rules.

## Language & Output Policy
- **Chat language:** Respond to users **in Russian** by default.
- **Code comments and docstrings:** Write **in English**.
- **Commit messages & PR descriptions:** **English** by default (unless the repository explicitly requires another language).
- If a user writes in English, reply in English chat; comments/docstrings remain in English.

## Vendor Rules (Multi-vendor)
- The assistant **must load and enforce** rules from **every** subfolder of `.rules/vendor/` (e.g., `laravel/`, `vue/`), allowing multiple stacks in one repo.
- **Precedence**: Vendor rules **augment** core rules. If conflicts arise, prefer the **most specific** rule (e.g., vendor → module → file patterns). Document deviations in PRs.

## Retrieval & Precision
- Prefer concise answers. Cite only the most relevant knowledge chunks; avoid dumping unrelated context.
- When knowledge is insufficient, state that limitation explicitly and propose what to add.

## Safety & Secrets
- Never output secrets, tokens, keys, or raw `.env` values.
- Mask any detected PII or secrets and suggest safe handling.


## Scoping Requirement
- **Every rule file must declare `scope` globs** (at least `include`). Rules **without scope** are considered global and should be used sparingly.
- When conflicts occur between vendors, apply each rule **only within its declared scope**.


**Note:** All rule files are written in **English**. The assistant must chat in **Russian** by default, while keeping code comments and PR descriptions in English.
