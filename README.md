# Deploy Services

Docker Compose setup for the BIOFIN platform services.

## Services

This repository contains a single `docker-compose.yml` file which deploys:

- Auth API
- Gateway API
- Physical API
- Physical Worker
- PostgreSQL databases
- Temporal
- Temporal UI
- MinIO
- Frontend UI

---

## Requirements

- Docker
- Docker Compose

---

## Setup

Create a `.env` file in the root of the repository.

Example:

```env
# Auth DB
AUTH_POSTGRES_DB=auth_db
AUTH_POSTGRES_USER=auth_user
AUTH_POSTGRES_PASSWORD=auth_password

# Physical DB
PHYSICAL_POSTGRES_DB=physical_db
PHYSICAL_POSTGRES_USER=physical_user
PHYSICAL_POSTGRES_PASSWORD=physical_password

# Temporal DB
POSTGRES_USER=temporal_user
POSTGRES_PASSWORD=temporal_password
TEMPORAL_POSTGRES_USER=temporal_user
TEMPORAL_POSTGRES_PWD=temporal_password

# JWT
JWT_SECRET_KEY=supersecretkey

# Auth Clients
AUTH_CLIENT_ID=auth-client
AUTH_CLIENT_SECRET=auth-secret

GATEWAY_AUTH_CLIENT_ID=gateway-client
GATEWAY_AUTH_CLIENT_SECRET=gateway-secret

PHYSICAL_AUTH_CLIENT_ID=physical-client
PHYSICAL_AUTH_CLIENT_SECRET=physical-secret

# MinIO
MINIO_ROOT_USER=minio
MINIO_ROOT_PASSWORD=minio123
```

---

## Start Services

```bash
docker compose up -d
```

To rebuild images:

```bash
docker compose up -d --build
```

---

## Stop Services

```bash
docker compose down
```

To also remove volumes:

```bash
docker compose down -v
```

---

## Available Services

| Service | URL |
|---|---|
| Frontend UI | http://localhost:3000 |
| Gateway API | http://localhost:8000 |
| Auth API | http://localhost:8010 |
| Physical API | http://localhost:8020 |
| Temporal UI | http://localhost:8080 |
| MinIO API | http://localhost:9000 |
| MinIO Console | http://localhost:9001 |

---

## Volumes

Persistent Docker volumes:

- `auth_data`
- `physical_data`
- `temporal_pg_data`
- `minio_data`

---

## Notes

- Services communicate internally using Docker networking.
- Temporal is configured with PostgreSQL persistence.
- MinIO is used for document/object storage.
- Frontend communicates through the Gateway API.
