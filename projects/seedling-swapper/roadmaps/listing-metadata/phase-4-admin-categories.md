---
phase: 4
title: Admin category management UI
status: done
completed: 2026-04-19
commit: a85663b03c5c36f8db2664f71329856f8a0e8597
---

## Context
Builds on phase 1 (admin API endpoints). Adds a Category Management section to the admin panel so admins can maintain the canonical category list.

## Steps
1. Write RTL tests for the category management UI before implementing
2. Add a `CategoryManagementPage` (or section within an existing admin page) with:
   - Table listing all categories with their in-use count
   - "Add category" inline form (name input + submit)
   - Rename action (inline edit or modal)
   - Delete button — disabled/greyed with tooltip when category is in use
3. Wire up to the `/admin/categories` endpoints from phase 1
4. Add route and link in `AdminNav`

## Acceptance Criteria
- [ ] Admin can view all categories with usage counts
- [ ] Admin can add a new category (duplicate name shows error)
- [ ] Admin can rename a category
- [ ] Delete is disabled when category is in use; enabled otherwise
- [ ] Admin nav includes a link to category management
- [ ] UI behaviour covered by RTL tests
