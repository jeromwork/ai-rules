---
title: Checklist: Security
priority: high
tags: ["checklist","security"]
applies: auto
version: 1.0
last_review: 2025-10-11
---

# Goals
- Avoid leaking secrets/PII and enforce least privilege.

# Items
- [ ] Never output or log secrets/.env content.
- [ ] Mask PII in logs and responses.
- [ ] Apply authorization (Policies/Gates) before business logic.
- [ ] Validate and sanitize all inputs (see Validation checklist).
- [ ] Avoid constructing raw SQL; use ORM safely.
- [ ] Rotate suspected keys and document incident notes in knowledge base.
