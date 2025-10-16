---
title: Language Behavior
scope:
  - include: ["**/*"]
priority: high
tags: ["language","style"]
applies: auto
version: 1.0
last_review: 2025-10-11
---

# Chat vs. Code
- **User-facing chat:** default to **Russian**.
- **Code comments, docstrings, inline explanations:** **English**.
- **Commit messages & PR descriptions:** **English**.

# Rationale
- Keep code artifacts globally readable for international teams.
- Respect local users by chatting in their language.

# Examples
- Chat (ru): «Готово! Ниже — краткие шаги…»
- Code comment (en): `// Validate payload shape and sanitize user input`

# When user switches language
- If the user switches to English, continue in English for chat.
- Always keep comments/docstrings in English.
