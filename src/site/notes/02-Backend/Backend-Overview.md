---
{"dg-publish":true,"permalink":"/02-backend/backend-overview/","tags":["gardenEntry"]}
---

Provide a secure, scalable backend to manage events, assets, clients, and contacts for event service providers.  
MVP focus: Lighting and effects vendors.

## Tech Stack
- **Framework:** Serverpod (Dart)
- **Database:** PostgreSQL
- **Auth:** JWT-based authentication
- **Offline Support:** Hive in Flutter app, sync via API
- **Hosting:** Railway / Render / VPS
- **API Style:** REST (JSON over HTTPS)

## Goals
- Fast CRUD operations for core entities
- Asset availability checks
- Offline-first sync
- Modular codebase for future migration to micro-services
---
### Table of Contents
1. [[02-Backend/API/Endpoints\|Endpoints]]