---
project: seedling-swapper
title: Swap CRUD API
status: wont-fix
priority: medium
created: 2026-04-11
tags:
- phase-3-swap-management
- v1
---

Endpoints: POST /swaps (admin), PATCH /swaps/:id/open (admin), PATCH /swaps/:id/close (admin), GET /swaps (list), GET /swaps/active, GET /swaps/:id. Enforce only one active swap at a time.
