---
project: seedling-swapper
title: Move swap history stat aggregation to database layer
status: done
priority: medium
created: 2026-04-14
completed: 2026-04-14
commit: a10f16b65fccd4e42d62e579751972205eaec5e0
---

Fixes GitHub issue #5 (priority: high).

At `packages/backend/src/routes/swap.ts:93-107` (and duplicated at `180-200`), swap statistics (participant count, listing count, total/claimed quantity) are computed in JavaScript with nested array iterations — O(n*m) where n=listings and m=claims per listing.

**Fix**
Push aggregation to the database using Prisma `_count`, `_sum`, or raw SQL `COUNT(DISTINCT)`. This reduces data transfer and lets PostgreSQL handle what it's optimized for. Remove the duplicated logic at lines 180-200.
