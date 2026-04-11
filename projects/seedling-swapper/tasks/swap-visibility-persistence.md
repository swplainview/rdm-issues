---
project: seedling-swapper
title: 'Fix swap visibility: active swaps invisible to non-admin after restart'
status: open
priority: medium
created: 2026-04-11
---

Active swaps appear correctly in the admin console but are not visible to non-admin users after the services are restarted.

Likely cause: swap "active" state is being held in memory (e.g. a cache, in-process flag, or missing DB write) rather than persisted to the database. On restart the in-memory state is lost, so the public query finds no active swaps even though the DB row exists.

Investigate whether the `isActive` flag (or equivalent) is written to the DB at activation time, and whether the public listing query reads from the DB or a cached/derived source.
