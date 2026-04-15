---
project: seedling-swapper
title: Paginate unbounded swap history query
status: done
priority: medium
created: 2026-04-14
completed: 2026-04-14
commit: e4df2f4fc8bb70f3b8388a8a06a32cade5cfa009
---

Fixes GitHub issue #2 (priority: critical).

The `/swaps/history` endpoint at `packages/backend/src/routes/swap.ts:77-126` loads ALL closed swaps with ALL their listings and ALL their claims with no pagination. A swap with 500 listings × 10 claims each = 5,000 claim records per swap.

**Fix**
Add `take`/`skip` pagination parameters to the `findMany()` call and accept `page`/`limit` query params from the client.
