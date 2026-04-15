---
project: seedling-swapper
title: Parallelize post-mutation refreshes in ListingDetailPage
status: open
priority: medium
created: 2026-04-14
---

Fixes GitHub issue #9 (priority: medium).

At `packages/frontend/src/pages/listings/ListingDetailPage.tsx:59-77`, post-claim and post-cancel handlers make sequential independent API calls:
1. Fetch updated listing
2. Refresh listings and claims
3. Fetch listing claims

**Fix**
Combine all three refresh operations into a single `Promise.all` call.
