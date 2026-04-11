---
project: seedling-swapper
title: Fix swap form date/time UX
status: open
priority: medium
created: 2026-04-11
tags:
- phase-3-swap-management
- v1
- bug
---

Issues found in the swap creation form:

- Default opens time to 00:00 (midnight) and closes time to 23:59 when a date is selected
- Event date should be date-only (no time required)
- Use 24-hour clock inputs throughout (drop AM/PM)
- Always show and store timezone as Central Time — make it visible in the UI so it is unambiguous
