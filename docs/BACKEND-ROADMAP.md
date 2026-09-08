# EduCore — Backend Roadmap

## Goal

Build EduCore's backend progressively from a clean modular monolith into a production-style distributed system.

## Backend Stack

- Node.js
- TypeScript
- Express
- PostgreSQL
- MongoDB where justified
- Redis
- RabbitMQ
- Socket.IO
- Docker
- PM2
- Nginx
- Keycloak
- KrakenD (optional)
- AWS
- GitHub Actions
- ECS
- Kubernetes (later)

## Phase 1 — Backend Foundation

Learn and implement:
- Node.js fundamentals
- TypeScript fundamentals
- Express
- project structure
- `app.ts` vs `server.ts`
- environment configuration
- API versioning
- middleware
- controllers/services/repositories
- standard API responses
- centralized error handling
- 404 handling
- Joi/request validation
- structured logging
- PostgreSQL connectivity
- graceful shutdown
- API testing
- Git workflow

Initial API:
`GET /api/v1/health`

Done when the backend starts, connects to PostgreSQL, exposes the health API, validates requests, handles errors centrally, logs requests, and shuts down cleanly.

## Phase 2 — PostgreSQL & Database Design

Learn:
- SQL
- relational modeling
- primary/foreign keys
- relationships
- constraints
- indexes
- normalization
- joins
- transactions
- pagination/filtering/sorting

Initial domains:
- institutions
- users
- roles
- permissions
- students
- teachers
- parents
- academic_years
- classes
- sections
- subjects
- attendance
- exams
- marks
- fees

Multi-institution rule:
Use `institution_id` to scope business data where appropriate.

## Phase 3 — Authentication

Implement:
- registration
- login
- logout
- logout all sessions
- access token
- refresh token
- refresh endpoint
- current-user endpoint
- password hashing
- refresh-token rotation
- session revocation

Security:
- short-lived access token
- secure refresh-token handling
- HttpOnly/Secure/SameSite cookies where applicable
- rate limiting

## Phase 4 — RBAC

Implement:
- users
- roles
- permissions
- user_roles
- role_permissions
- authorization middleware

Permission format:
`resource:action`

Examples:
- `students:create`
- `students:read`
- `attendance:create`
- `marks:create`
- `fees:read`

## Phase 5 — Core School Modules

Build:
- institution
- academic year
- classes
- sections
- subjects
- students
- teachers
- parents
- attendance
- exams
- marks
- fees

Build each feature as:
API contract → backend implementation → tests → frontend integration.

## Phase 6 — Redis

Learn and implement:
- caching
- TTL
- session/refresh-token storage
- rate limiting
- cache invalidation
- pub/sub basics

## Phase 7 — Microservices

Start with:
- Auth Service
- Student Service
- Academic Service

Later:
- Notification Service
- Audit Service
- Fee Service

Rule:
Each service owns its data. No direct cross-service database queries.

## Phase 8 — Service-to-Service Communication

Learn:
- synchronous HTTP
- service authentication
- timeouts
- retries
- idempotency
- circuit-breaker concepts
- failure handling

## Phase 9 — RabbitMQ

Learn:
- producer
- consumer
- queue
- exchange
- routing key
- acknowledgements
- retry
- dead-letter queues

Example:
`StudentCreated` → Notification Service + Audit Service

## Phase 10 — Socket.IO

Implement:
- authenticated sockets
- rooms
- events
- broadcasting
- targeted notifications

Rooms can include:
- `user:{id}`
- `institution:{id}`
- `class:{id}`

Use the Redis adapter when multiple Node processes need to share realtime events.

## Phase 11 — MongoDB

Use where document storage is justified.

Candidates:
- Notification Service
- Audit Service

Learn:
- documents
- collections
- indexes
- aggregation
- schema design
- TTL indexes

## Phase 12 — Docker

Containerize:
- frontend
- backend/services
- PostgreSQL
- MongoDB
- Redis
- RabbitMQ
- Nginx

Use Docker Compose for local development.

## Phase 13 — PM2 + Nginx + Load Balancing

Learn:
- PM2
- cluster mode
- graceful restart
- Nginx reverse proxy
- load balancing
- health checks

Understand:
PM2 process scaling is different from infrastructure-level load balancing.

## Phase 14 — Keycloak

Introduce after custom authentication concepts are understood.

Learn:
- OAuth2
- OpenID Connect
- realms
- clients
- roles
- groups
- SSO
- token validation

## Phase 15 — KrakenD (Optional)

Learn:
- API gateway
- routing
- authentication integration
- aggregation
- rate limiting
- caching
- service abstraction

## Phase 16 — AWS

Learn:
- IAM
- VPC
- EC2
- RDS
- S3
- ECR
- ECS
- ALB
- ElastiCache
- CloudWatch

Target direction:
Route53 → ALB → ECS → services

## Phase 17 — CI/CD

Implement:
- lint
- typecheck
- tests
- build
- Docker build
- ECR push
- ECS deployment
- secrets/environment management
- rollback

## Phase 18 — Monitoring & Reliability

Implement:
- health checks
- readiness checks
- structured logs
- metrics
- latency monitoring
- error-rate monitoring
- resource monitoring
- database/Redis health
- alerts

Later:
- Prometheus
- Grafana
- OpenTelemetry

## Phase 19 — Kubernetes

Only after Docker and AWS/ECS fundamentals.

Learn:
- Pod
- Deployment
- Service
- Ingress
- ConfigMap
- Secret
- ReplicaSet
- HPA
- Namespace

## Backend Completion Rule

Do not mark a phase complete just because the code works.

A phase is complete when:
1. The concepts are understood.
2. The feature is implemented.
3. Success and failure cases are tested.
4. The architectural reason is understood.
5. Important decisions are documented.
