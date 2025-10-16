---
title: Laravel Scripts / Commands
scope:
  - include: ["app/**/*.php","routes/**/*.php","database/**/*.php","config/**/*.php","tests/**/*.php"]
  - exclude: ["frontend/**","src/**"]
priority: high
tags: ["laravel","backend","scripts"]
applies: auto
version: 1.0
last_review: 2025-10-11
---

# Scripts / Commands (via scripts.json or Makefile)

- **lint** → `vendor/bin/pint --test`  
- **typecheck** → `vendor/bin/phpstan analyse --no-progress --memory-limit=1G`  
- **test** → `php artisan test --parallel --coverage-clover=storage/coverage.xml`  
- **sec:deps** → `composer audit --format=json`  
- **sec:sast** → `vendor/bin/phpstan analyse` (strict profile)  
- **bench** → `vendor/bin/phpbench run --report=aggregate` (when necessary)

> Align local tooling to these commands or add mapping targets that run the equivalents.
