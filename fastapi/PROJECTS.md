# FastAPI Projects

**Stack you should standardize on:**

- FastAPI
- PostgreSQL
- Redis
- SQLAlchemy / SQLModel
- Alembic
- pytest
- Docker

---

Here are some great Backend-only FastAPI projects to build:

`Advanced Projects:`

1. [Distributed Task Queue (Mini Celery)](#distributed-task-queue-mini-celery)

2. [Auth Service (Production-Grade)](#auth-service-production-grade)

3. [Rate Limiter + API Gateway](#rate-limiter--api-gateway)

4. [Event-Driven Notification System](#event-driven-notification-system)

5. [Search Service (Like a Mini Elastic)](#search-service-like-a-mini-elastic)

6. [File Upload & Processing Service](#file-upload--processing-service)

7. [Metrics & Monitoring Service](#metrics--monitoring-service)

8. [Versioned Public API (Enterprise Style)](#versioned-public-api-enterprise-style)

9. [Webhook Delivery Platform](#webhook-delivery-platform)

10. [Multi-Tenant SaaS Backend](#multi-tenant-saas-backend)

---

`Beginner-friendly Projects:`

1. [URL Shortener](#url-shortener)

2. [Simple Auth Service](#simple-auth-service)

3. [Notes / CRUD API](#notes--crud-api)

4. [File Upload API](#file-upload-api)

5. [Rate-Limited Public API](#rate-limited-public-api)

6. [Background Job API](#background-job-api)

7. [Webhook Receiver Service](#webhook-receiver-service)

8. [Log Aggregation API](#log-aggregation-api-mini)

9. [Health & Status Service](#health--status-service)

10. [API for External Data Fetching](#api-for-external-data-fetching)

---

### Step Wise Backend Projects

| Steps | Description |
| :---: | :--- |
| 0 | [Core Backend Foundations](#step-0--core-backend-foundations) |
| 1 | [FastAPI Basics (API Correctness)](#step-1--fastapi-basics-api-correctness) |
| 2 | [Database & ORM (Data Integrity)](#step-2--database--orm-data-integrity) |
| 3 | [Authentication & Authorization (Security)](#step-3--authentication--authorization-security) |
| 4 | [Async & Background Work (Real Workloads)](#step-4--async--background-work-real-workloads) |
| 5 | [Caching & Performance (Scalability)](#step-5--caching--performance-scalability) |
| 6 | [File & Media Handling](#step-6--file--media-handling) |
| 7 | [Event-driven Design (Decoupling)](#step-7--event-driven-design-decoupling) |
| 8 | [Observability & Reliability](#step-8--observability--reliability) |
| 9 | [API Design at Scale (Enterprise Backend)](#step-9--api-design-at-scale-enterprise-backend) |
| 10 | [System Design Capstone](#step-10--system-design-capstone) |

---

### Distributed Task Queue (Mini Celery)

What you build
- Task producer API
- Worker service
- Retry, backoff, task states

Tech focus
- FastAPI
- Redis / RabbitMQ
- Background workers
- Idempotency

Why it matters
- Shows you understand async systems and job orchestration.

---

### Auth Service (Production-Grade)

What you build
- JWT + refresh tokens
- OAuth2 login (Google/GitHub)
- Role-based access control
- Token revocation

Tech focus
- OAuth2
- JWT internals
- Security best practices
- FastAPI dependencies

Why it matters
- Every real backend needs this.

---

### Rate Limiter + API Gateway

What you build
- Per-IP / per-user limits
- Sliding window / token bucket
- Request forwarding
- API keys

Tech focus
- Redis
- Middleware
- Reverse proxy logic
- High-throughput handling

Why it matters
- Backend infra + scalability signal.

---

### Event-Driven Notification System

What you build
- Publish events (user_signup, order_created)
- Subscribers (email, webhook, logs)
- Async processing

Tech focus
- Message queues
- Async FastAPI
- Event schemas

Why it matters
- Demonstrates decoupled system design.

---

### Search Service (Like a Mini Elastic)

What you build
- Index documents
- Full-text search
- Filters + ranking
- Pagination

Tech focus
- PostgreSQL full-text search or OpenSearch
- Query optimization
- Performance tuning

Why it matters
- Real-world backend data engineering.

---

### File Upload & Processing Service

What you build
- Multipart uploads
- Virus scan / validation
- Async processing (resize, compress)
- Cloud storage integration

Tech focus
- Streaming uploads
- Background tasks
- S3-compatible APIs

Why it matters
- Shows production readiness.

---

### Metrics & Monitoring Service

What you build
- Request metrics
- Custom counters
- Health checks
- Prometheus-style endpoints

Tech focus
- Observability
- Middleware
- System introspection

Why it matters
- Most engineers ignore this — you shouldn’t.

---

### Versioned Public API (Enterprise Style)

What you build

- `/v1`, `/v2` APIs
- Deprecation handling
- Schema evolution
- Backward compatibility

Tech focus
- API design
- OpenAPI mastery
- Dependency injection

Why it matters
- Senior-level backend thinking.

---

### Webhook Delivery Platform

What you build
- Register webhooks
- Retry on failure
- Signature verification
- Delivery logs

Tech focus
- Security
- Reliability
- Async retries

Why it matters
- Stripe-like backend patterns.

---

### Multi-Tenant SaaS Backend

What you build
- Tenant isolation
- Per-tenant rate limits
- Billing hooks
- Access policies

Tech focus
- DB design
- Authorization layers
- SaaS architecture

Why it matters
- Huge resume signal.

---

### URL Shortener

What you build
- Create short URLs
- Redirect service
- Expiry support
- Click count

You learn
- REST design
- Database modeling
- Indexing
- HTTP redirects

Stretch
- Rate limiting
- Custom aliases

---

### Simple Auth Service

What you build
- User signup/login
- Password hashing
- JWT access tokens

You learn
- Security basics
- FastAPI dependencies
- Auth flows

Stretch
- Refresh tokens
- Logout token blacklist

---

### Notes / CRUD API

What you build
- CRUD endpoints
- Pagination
- Sorting & filtering
- Ownership checks

You learn
- ORM usage
- Query optimization
- API correctness
  
Stretch
- Soft deletes
- Audit timestamps

---

### File Upload API

What you build
- Upload files
- Validate type & size
- Store locally or S3
- Download endpoint

You learn
- Streaming uploads
- Background tasks
- Storage abstractions

Stretch
- Async processing
- File metadata DB

---

### Rate-Limited Public API

What you build
- Public endpoint
- Per-IP rate limiting
- API key authentication

You learn
- Middleware
- Redis basics
- Defensive backend design

Stretch
- Sliding window limiter

---

### Background Job API

What you build
- Submit long-running job
- Poll job status
- Job retries

You learn
- Async vs sync
- Task queues
- Idempotency

Stretch
- Redis queue
- Worker process

---

### Webhook Receiver Service

What you build
- Receive webhooks
- Verify signatures
- Store payloads
- Retry failed processing

You learn
- Security
- Request validation
- Event handling

Stretch
- Replay events

---

### Log Aggregation API (Mini)

What you build
- Accept logs
- Store them
- Query by time/level

You learn
- Schema design
- Indexing
- Filtering large datasets

Stretch
- Pagination + cursor

---

### Health & Status Service

What you build
- `/health`
- `/ready`
- Dependency checks
- Uptime stats

You learn
- Observability mindset
- Production readiness

Stretch
- Prometheus metrics

---

### API for External Data Fetching

What you build
- Fetch data from public APIs
- Cache responses
- Expose normalized endpoints

You learn
- Async HTTP clients
- Caching
- Data normalization

Stretch
- TTL cache with Redis

---

### STEP 0 — Core Backend Foundations

Topics:
- HTTP (methods, status codes, headers)
- REST principles
- JSON, serialization
- Basic SQL (SELECT, JOIN, INDEX)
- Git (branching, PR mindset)

Mini Project:
- Pure Python REST simulator
    - In-memory CRUD
    - Manual request/response handling
    - No framework

Goal: understand what FastAPI abstracts away.

---

### STEP 1 — FastAPI Basics (API correctness)

Topics:
- FastAPI routing
- Pydantic models
- Request vs response models
- Status codes & errors
- Dependency Injection (basic)

Project 1: Notes / Todo API
- CRUD notes
- Pagination
- Validation
- Proper HTTP codes

You must learn:
- Clean endpoint design
- Data validation discipline

---

### STEP 2 — Database & ORM (Data Integrity)

Topics:
- SQLAlchemy / SQLModel
- Migrations (Alembic)
- Transactions
- Indexes
- N+1 problem

Project 2: User-owned Notes API
- Users table
- Notes linked to users
- Ownership checks
- Soft deletes

You must learn:
- Schema design
- Query optimization
- Data consistency

---

### STEP 3 — Authentication & Authorization (Security)

Topics:
- Password hashing
- JWT
- OAuth2 flow
- Role-based access
- Dependency-based auth

Project 3: Auth Service
- Signup / login
- JWT access tokens
- Role-based endpoints (admin/user)

You must learn:
- Security boundaries
- Token lifecycle
- Attack surfaces

---

### STEP 4 — Async & Background Work (Real Workloads)

Topics:
- Async vs sync
- BackgroundTasks
- Idempotency
- Long-running jobs

Project 4: Background Job API
- Submit job
- Poll job status
- Retry failed jobs

You must learn:
- Non-blocking systems
- Job lifecycle design

---

### STEP 5 — Caching & Performance (Scalability)

Topics:
- Redis
- Cache invalidation
- Rate limiting
- Response caching

Project 5: Rate-limited Public API
- API keys
- Per-IP rate limiting
- Redis-backed counters

You must learn:
- Performance thinking
- Defensive backend design

---

### STEP 6 — File & Media Handling

Topics:
- Streaming uploads
- Multipart forms
- Async processing
- Storage abstraction

Project 6: File Upload Service
- Upload files
- Validate type & size
- Background processing
- Download endpoints

You must learn:
- Resource management
- Async IO patterns

---

### STEP 7 — Event-driven Design (Decoupling)

Topics:
- Events vs requests
- Message queues
- At-least-once delivery
- Event schemas

Project 7: Event Notification System
- Emit events
- Subscribers (email/log/webhook)
- Async consumers

You must learn:
- System decoupling
- Reliability patterns

---

### STEP 8 — Observability & Reliability

Topics:
- Logging
- Metrics
- Health checks
- Graceful shutdown

Project 8: Monitoring Service
- `/health`, `/ready`
- Custom metrics
- Structured logs

You must learn:
- Production readiness
- Debuggability

---

### STEP 9 — API Design at Scale (Enterprise Backend)

Topics:
- API versioning
- Backward compatibility
- Deprecation strategies
- Schema evolution

Project 9: Versioned Public API
- `/v1`, `/v2`
- Breaking changes handled cleanly
- OpenAPI mastery

You must learn:
- Long-term API thinking

---

### STEP 10 — System Design Capstone

Topics:
- Multi-tenancy
- Authorization layers
- Horizontal scaling
- Failure handling

Project 10 (Capstone): Multi-Tenant SaaS Backend
- Tenant isolation
- Per-tenant limits
- Billing hooks
- Audit logs

You must learn:
- Architecture decisions
- Trade-offs
- Real-world complexity