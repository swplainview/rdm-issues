---
project: seedling-swapper
title: Fix N+1 queries in notification preference checks
status: open
priority: medium
created: 2026-04-14
---

Fixes GitHub issue #1 (priority: critical).

`isNotificationEnabled()` makes an individual `prisma.notificationPreference.findUnique()` call per user inside loops. With N followers/claimants, this produces N+1 database round trips.

**Locations**
- `packages/backend/src/routes/listing.ts:89-102` — NEW_LISTING notifications loop over followers
- `packages/backend/src/routes/listing.ts:208-220` — LISTING_DELETED notifications loop over claimants
- `packages/backend/src/routes/claim.ts:49-61` — CLAIM_MADE notification preference check

**Fix**
Batch-fetch all notification preferences upfront with `findMany({ where: { userId: { in: userIds } } })`, build a Map, and check from the map instead of querying per user.
