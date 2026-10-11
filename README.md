# Docker Notes

Simple Notes web app for a Docker Compose assignment. Java 21/Spring Boot runs in `app`, PostgreSQL 17 in `db`; pgAdmin runs in `pgadmin`. Compose connects the services. Passwords come from `.env`, and named Docker volumes persist database and pgAdmin data.

## Start

Requires Docker with Docker Compose; no local Java or PostgreSQL installation.

```bash
cp .env.example .env
```

Set `DB_PASSWORD`, `PGADMIN_EMAIL`, and `PGADMIN_PASSWORD` in `.env`, then start:

```bash
docker compose up --build
```

App: <http://localhost:8080>. pgAdmin: <http://localhost:5050> (database host `db`, database/user `notes`, password from `DB_PASSWORD`).

## API

| Method | Path | Purpose |
| --- | --- | --- |
| `GET` | `/api/notes` | List notes |
| `POST` | `/api/notes` | Create note with JSON `title` and `content` |
| `DELETE` | `/api/notes/{id}` | Delete note |

## Stop and data

`docker compose down` stops the containers and retains data. `docker compose down -v` also deletes the volumes and all stored notes and pgAdmin settings.

## Collaborators

Hannes Pernthaler, Mathias Rauter
