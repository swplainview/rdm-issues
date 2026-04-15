---
project: seedling-swapper
title: Add pagination to admin user list endpoint
status: open
priority: medium
created: 2026-04-14
---

Fixes GitHub issue #7 (priority: medium).

The `/admin/users` endpoint at `packages/backend/src/routes/user.ts:50-75` returns all users with computed `_count` aggregates and no pagination.

**Fix**
Accept `page`/`limit` query params, add `take`/`skip` to the Prisma query, and return the total count in the response for client-side pagination.
