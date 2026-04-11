---
project: seedling-swapper
title: Enforce email validation on auth forms
status: open
priority: medium
created: 2026-04-11
tags:
- phase-2-auth
- v1
- bug
---

Tighten email validation on register and login forms:

- Reject invalid syntax (must match standard email format)
- Strip leading/trailing whitespace before validation
- Reject addresses containing spaces
- Enforce consistently on both frontend (immediate feedback) and backend (Zod schema)
