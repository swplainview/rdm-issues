---
project: seedling-swapper
title: 'Fix photo upload: route receives multipart as JSON'
status: in-progress
priority: medium
created: 2026-04-11
---

Photo upload requests fail with `SyntaxError: Unexpected token '-'` because the global `express.json()` middleware is trying to parse multipart/form-data bodies on the photo upload route.

The upload route needs to be excluded from JSON body parsing (or use `multer`/`busboy` before `express.json()` runs), so that multipart form boundaries are handled by the file parser rather than the JSON parser.

Stack trace shows the error originates in `body-parser` attempting to JSON-parse a multipart boundary string like `------geckoformboundary...`.
