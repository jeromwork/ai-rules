---
title: Checklist: Validation
priority: high
tags: ["checklist","validation"]
applies: auto
version: 1.0
last_review: 2025-10-11
---

# Goals
- Ensure all external inputs are validated and sanitized.

# Items
- [ ] Use framework-native validators (e.g., Laravel FormRequest).
- [ ] Validate types, ranges, enums; provide localized error messages.
- [ ] Sanitize strings to prevent XSS/SQLI injection vectors.
- [ ] Centralize validation rules; avoid duplication.
- [ ] Add tests for success and common failure paths.
