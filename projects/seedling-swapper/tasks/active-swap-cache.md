---
project: seedling-swapper
title: Cache active swap query to avoid redundant DB calls
status: open
priority: medium
created: 2026-04-14
---

Fixes GitHub issue #15 (priority: low).

The same `prisma.swap.findFirst({ where: { status: "ACTIVE" } })` query is executed in multiple route handlers (e.g., `user.ts:125-134`, `listing.ts`). Since only one swap can be active at a time and status changes are rare, this is redundant work.

**Fix**
Cache the active swap in application memory (e.g. a module-level variable with a short TTL) and invalidate it whenever swap status changes.
