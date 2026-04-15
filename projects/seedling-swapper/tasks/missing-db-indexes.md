---
project: seedling-swapper
title: Add missing database indexes on frequently queried columns
status: open
priority: medium
created: 2026-04-14
---

Fixes GitHub issue #4 (priority: high).

Several columns used in WHERE clauses have no indexes, causing full table scans.

**Missing indexes** (`packages/backend/prisma/schema.prisma`):

| Table | Column(s) | Used in |
|-------|-----------|---------|
| `Listing` | `userId`, `swapId` | listing.ts, user.ts |
| `Claim` | `userId`, `listingId` | claim.ts, listing.ts, swap.ts |
| `Notification` | `userId` | notification.ts |
| `Follow` | `followeeId` | listing.ts |
| `PlantCache` | `commonName` | plant.ts (ILIKE search) |

**Fix**
Add `@@index` directives in the Prisma schema for each of the above, then run `prisma migrate dev`. For `PlantCache.commonName`, consider a GIN trigram index (`pg_trgm`) for efficient ILIKE queries.

Note: the GIN index for `PlantCache.commonName` also addresses GitHub issue #11.
