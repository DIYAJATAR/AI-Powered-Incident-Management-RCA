# AI-Powered Incident Management & Root-Cause Analysis Platform

A production-oriented incident management platform built with Java 21 and Spring Boot. Phase 1 provides incident CRUD APIs, validation, PostgreSQL persistence, health endpoints, and a clean service/repository architecture.

## Tech Stack

- Java 21
- Spring Boot
- Spring Web
- Spring Data JPA
- PostgreSQL
- Maven
- Bean Validation
- Spring Boot Actuator
- Docker Compose

## API

### Create incident

`POST /api/incidents`

```json
{
  "title": "Payment service returning 500 errors",
  "description": "Payment API started returning HTTP 500 responses.",
  "severity": "HIGH",
  "serviceName": "payment-service",
  "environment": "production"
}
```

### List incidents

`GET /api/incidents`

Optional service filter:

`GET /api/incidents?serviceName=payment-service`

### Get incident

`GET /api/incidents/{id}`

### Update status

`PATCH /api/incidents/{id}/status?value=INVESTIGATING`

Supported status values:

- OPEN
- INVESTIGATING
- RESOLVED
- CLOSED

### Delete incident

`DELETE /api/incidents/{id}`

## Run locally

1. Start PostgreSQL:

```bash
docker compose up -d
```

2. Run the application:

```bash
mvn spring-boot:run
```

3. Health check:

`GET http://localhost:8080/actuator/health`

## Configuration

Environment variables:

- `DB_URL`
- `DB_USERNAME`
- `DB_PASSWORD`
- `PORT`

## Roadmap

1. Authentication and RBAC
2. Log ingestion
3. Incident correlation
4. Redis-backed asynchronous processing
5. Java worker pools and concurrency
6. AI-assisted root-cause analysis
7. React operations dashboard
8. Docker + GitHub Actions CI/CD
9. AWS deployment
