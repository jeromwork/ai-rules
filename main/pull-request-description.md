---
title: Pull Request Description Template
scope:
  - include: [".git/**","**/*.md","**/*.php","**/*.ts","**/*.js"]
priority: high
tags: ["pr","reviews","documentation"]
applies: auto
version: 1.0
last_review: 2025-10-11
---

# PR Description — Required Sections (English)
1. **Summary** — What and why (1–3 sentences).
2. **Scope** — A bullet list of key changes.
3. **Breaking Changes** — If any, how to migrate.
4. **Testing** — How it was tested + commands.
5. **Security/PII** — Any sensitive data touched? Mitigations.
6. **Docs & Knowledge** — Links to updated docs/knowledge base.

## Example
**Summary**: Implement invoice creation endpoint and validation.  
**Scope**:
- `POST /v1/invoices` controller + form request.
- Service layer for business logic.
- Tests for happy path and validation errors.
**Testing**: `php artisan test --filter=InvoiceTest`  
**Security**: No secrets exposed. Input sanitized.  
**Docs**: Updated `/knowledge/api.md` and changelog.

# Assistant Behavior
- When asked to open a PR, generate the description using this template in **English**.
