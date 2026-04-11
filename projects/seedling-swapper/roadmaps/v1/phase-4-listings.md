---
phase: 4
title: Seedling Listings
status: done
completed: 2026-04-11
commit: 5a02013ef4494d8963e05874e14f613f3c265da0
---

CRUD for seedling listings scoped to an active swap. Fields: plant name, variety, quantity, notes, optional photo. Photo stored on local filesystem via mounted Docker volume. Plant lookup/autocomplete via Perenual API with local PostgreSQL cache.
