# Architektur TicketBoard

## Komponenten

- Frontend
- API
- PostgreSQL-Datenbank
- Adminer
- Volume (Persistenz)

---

## Kommunikation

- Browser → Frontend
- Frontend → API
- API → Datenbank
- Adminer → Datenbank

---

## Architekturdiagramm

```mermaid
graph TD
    user[Browser]

    subgraph system [Docker Compose System]
        frontend[Frontend Container]
        api[API Container]
        adminer[Adminer]
        db[(PostgreSQL)]
        volume[(postgres_data Volume)]
    end

    user -->|http :3000| frontend
    user -->|http :8080| adminer

    frontend -->|http :8000| api

    api -->|DB :5432| db
    adminer -->|DB :5432| db

    db --> volume