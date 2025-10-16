---
title: Vue Project Rules
scope:
  - include: ["frontend/**/*.vue","frontend/**/*.ts","frontend/**/*.js","src/**/*.vue","src/**/*.ts","src/**/*.js"]
  - exclude: ["app/**","routes/**","database/**"]
priority: high
tags: ["vue","frontend"]
applies: auto
version: 1.1
last_review: 2025-10-11
---

# Guidelines
- Use single-file components with `<script setup>`.
- Keep components small; extract composables into `useFoo.ts`.
- Enforce type safety with TypeScript where possible.
- Avoid leaking secrets into client bundles.

# PR Notes
- Frontend changes must include screenshots or Storybook references where applicable.
