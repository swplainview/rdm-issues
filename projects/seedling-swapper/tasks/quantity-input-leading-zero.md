---
project: seedling-swapper
title: 'Fix quantity input: prevent leading zero when typing'
status: done
priority: medium
created: 2026-04-11
completed: 2026-04-11
commit: 2767157f146b42dffd5ada0c3377d949bb1ef6c8
---

When using the quantity input field, if the user reduces the value to zero via keyboard and then types digits, the result is a leading zero (e.g. '01', '05'). The input should treat the value as a number and replace zero rather than prepend digits to it.
