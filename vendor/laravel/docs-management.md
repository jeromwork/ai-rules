---
title: Documentation Management Rules
priority: high
tags: ["documentation", "management", "tasks"]
applies: auto
version: 1.0
last_review: 2025-01-15
scope:
  include: ["**/*.md", "docs/**", "PLAN.md"]
  exclude: ["node_modules/**", "vendor/**"]
---

# Documentation Management Rules for AI Agents

##  STRICT directories

**AI agents MUST use only directories in `docs/`:**
- `docs/tasks/YYYY/MM/` (ONLY this one is allowed)
- `docs/systems/` (for systems documentation files)
- Any other directories in not create `docs/` ❌


**Branch task requirements:**
- Must contain complete Meta Gates evidence
- Must include PR description with ready-to-copy message
- Must reference related system documentation if applicable
- Must follow standard task template structure


**Examples of allowed structures:**
```
docs/systems/
├── doctors/
│   ├── photo-import.md
│   ├── modx-integration.md
│   └── api.md
├── content/
│   ├── service-api.md
│   ├── batch-import.md
│   └── design.md
├── schedules/
│   ├── slots-system.md
│   ├── auto-reservations.md
│   └── api.md
├── pages.md                    # root-level functionality
├── auth-system.md             # root-level functionality
├── task-management.md        # root-level functionality
```

### Documentation Evolution and Maintenance
**AI agents MUST follow these rules when working with systems documentation:**

#### File Creation vs. Extension Rules
1. **Check existing files first:** Before creating new documentation, scan `docs/systems/` for existing related files
2. **Logical grouping:** Group related functionality in the same file or module directory
3. **Extend existing files:** If existing file covers similar functionality, extend it instead of creating new one
4. **Module boundaries:** Respect module boundaries when organizing documentation

#### File Extension Guidelines
**Extend existing files when:**
- New functionality belongs to the same module/component
- New API endpoints extend existing API documentation
- New design decisions relate to existing architecture
- New integrations extend existing vendor documentation within the same module

**Create new files when:**
- Functionality belongs to different module
- Completely new system/architecture is introduced
- New vendor integration is added to a different module
- New architectural component is created


#### File Organization Examples
```markdown
# Instead of creating multiple files in system group logically by files

docs/systems/{module}/photo-import.md
├── API Documentation               # All API endpoints for module
├── System Design                   # All design decisions for doctors module
├── Architecture Decisions
└── Implementation Details

# Or separate by concern if complex:
docs/systems/doctors/
├── photo-import.md         # Main system documentation
├── modx-integration.md     # MODX vendor integration
├── api.md                  # All API endpoints for doctors module
└── design.md               # All design decisions for doctors module

# Root-level functionality example:
docs/systems/
├── task-management.md      # Task management system
├── auth-system.md         # Authentication system
└── pages.md               # Pages functionality
```

#### Maintenance Rules
- **Update existing files** when adding related functionality
- **Add new sections** to existing files rather than creating new files
- **Maintain consistency** in documentation structure across modules
- **Reference related files** in documentation headers

### Rationale
These directories contain **project-specific documentation** created by developers, not AI-generated content. AI agents should focus on task management only.

## ✅ ALLOWED Operations

### Task Documentation
**AI agents CAN create/modify:**
- `docs/tasks/YYYY/MM/DD_task-type_task-name.md` files
- `PLAN.md` (root level)
- Task-related content within allowed structure
- **Branch tasks:** `docs/tasks/YYYY/MM/DD_feature_{branch-description}.md` for completed branches

### Systems Documentation Directory
**AI agents CAN create the `docs/systems/` directory and files with subdirectories:**

#### Module Documentation
- `docs/systems/{module-name}/{feature}.md` - module functionality
- `docs/systems/{module-name}/api.md` - module API
- `docs/systems/{module-name}/design.md` - module design
- `docs/systems/{module-name}/{vendor}-integration.md` - vendor integrations within module

#### Root-level Documentation
- `docs/systems/{root-feature}.md` - root-level functionality
- `docs/systems/task-management.md` - task management system
- `docs/systems/auth-system.md` - authentication system

**Examples of allowed systems documentation:**
- `docs/systems/doctors/photo-import.md` - doctor photo import
- `docs/systems/doctors/modx-integration.md` - MODX integration for doctors module
- `docs/systems/doctors/api.md` - doctors module API
- `docs/systems/content/service-api.md` - content service API
- `docs/systems/schedules/slots-system.md` - slots system
- `docs/systems/pages.md` - root-level pages functionality
- `docs/systems/task-management.md` - task management system

## 🎯 Compliance Checklist create docs during finish branch

- [ ] NO new directories created in `docs/` except `docs/tasks/YYYY/MM/` and `docs/systems/` with subdirectories
- [ ] Branch tasks created in `docs/tasks/YYYY/MM/` with proper naming
- [ ] Systems documentation organized by modules in appropriate subdirectories
- [ ] Existing systems documentation extended instead of creating new files when appropriate
- [ ] SLI metrics included from `docs/slis/` files
- [ ] Technical context referenced from module documentation
- [ ] Branch plans referenced for architectural decisions
- [ ] Systems documentation referenced for design decisions
- [ ] Templates used as reference for formatting
- [ ] Existing documentation patterns followed
- [ ] Knowledge from existing docs preserved in tasks
- [ ] Branch context included in task implementation log
- [ ] File creation vs extension rules followed

## ⚠️ Violations

**Creating forbidden directories will result in:**
- Task rejection
- Documentation cleanup required
- Compliance review needed

**Failure to integrate existing documentation will result in:**
- Incomplete task documentation
- Missing technical context
- Inconsistent project knowledge
