---
project: seedling-swapper
title: 'Fix quantity input: prevent leading zero when typing'
status: open
priority: medium
created: 2026-04-11
---

When using the quantity input field, if the user reduces the value to zero via keyboard and then types digits, the result is a leading zero (e.g. '01', '05'). The input should treat the value as a number and replace zero rather than prepend digits to it.
