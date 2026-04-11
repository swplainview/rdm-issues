---
project: seedling-swapper
title: Docker Compose setup
status: done
priority: medium
created: 2026-04-11
tags:
- phase-1-foundation
- v1
completed: 2026-04-11
---

docker-compose.yml with three services: postgres (official image), backend (Node app), frontend (nginx serving built React app). Mount volume for photo storage. Environment variable configuration via .env.
