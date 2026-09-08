# EduCore — Master Project Roadmap

EduCore is a full-stack education-management platform developed progressively from a modular monolith into a production-style distributed/cloud system.

## Documentation Structure

- `PROJECT-ROADMAP.md` — high-level project map
- `BACKEND-ROADMAP.md` — detailed backend learning and implementation phases
- `FRONTEND-ROADMAP.md` — detailed frontend learning and implementation phases
- `ARCHITECTURE.md` — system architecture and boundaries
- `DECISIONS.md` — architecture decision log

## Overall Flow

Planning
→ Backend Foundation
→ Frontend Foundation
→ Database Design
→ Authentication
→ RBAC
→ Core Features
→ Redis
→ Microservices
→ Service Communication
→ RabbitMQ
→ Socket.IO
→ MongoDB
→ Docker
→ PM2/Nginx/Load Balancing
→ Keycloak
→ KrakenD (optional)
→ AWS
→ CI/CD
→ Monitoring
→ Kubernetes

## Development Model

We will not build all backend first and all frontend afterward.

Instead:

Feature
→ API contract
→ Backend
→ Frontend
→ Integration
→ Tests
→ Documentation

This keeps frontend and backend aligned while still allowing each application to remain independently structured and deployable.

## Initial Repository

educore/
├── frontend/
├── backend/
├── docs/
└── README.md

## Current Status

Current backend phase: Phase 1 — Backend Foundation

Current frontend phase: F1 — Frontend Foundation (planning/setup can happen alongside backend Phase 1)

Current architecture: Modular monolith

Current primary database: PostgreSQL

## Main Architectural Principles

1. Start simple and evolve.
2. Do not introduce microservices prematurely.
3. Each microservice owns its data.
4. PostgreSQL is the relational source of truth.
5. MongoDB is used only where document storage is justified.
6. Redis is for caching/session/realtime-support use cases, not primary business truth.
7. RabbitMQ is for asynchronous messaging.
8. Socket.IO is for client-facing realtime communication.
9. Keycloak is introduced after authentication concepts are understood.
10. KrakenD is optional.
11. Kubernetes comes after Docker and cloud fundamentals.
