---
project: seedling-swapper
title: Add timeout and error handling to Perenual API calls
status: done
priority: medium
created: 2026-04-14
completed: 2026-04-14
commit: e4df2f4fc8bb70f3b8388a8a06a32cade5cfa009
---

Fixes GitHub issues #3 and #6 (priority: critical + high bug).

Two related problems in `packages/backend/src/services/plant.ts`:

1. **No timeout** (line 39) — if the upstream API is slow or unresponsive, the request hangs indefinitely.
2. **No error handling** (lines 38-48) — `fetch()` throws on network errors and `response.json()` throws on malformed responses, crashing the request handler with a 500.

**Fix**
Wrap the external call in try-catch and use `AbortController` with a timeout (e.g. 10s). Return an empty result on any failure with appropriate logging.
