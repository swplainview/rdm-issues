---
project: seedling-swapper
title: PDF label generation service
status: open
priority: medium
created: 2026-04-11
tags:
- phase-6-labels
- v1
---

Backend service using @react-pdf/renderer (or pdf-lib) to generate label PDFs. One label per claimed unit — if a user claimed 2, generate 2 labels: '1 of 2' and '2 of 2'. Each label: plant name, variety, claimer name, poster name, ordinal. Group labels into a single downloadable PDF per request.
