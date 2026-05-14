# Cloud Architecture Overview

This document provides a simple architecture view of the TODO monorepo and shows the runtime interaction for creating a task.

## System Context

```mermaid
flowchart LR
    user[User]
    browser[React Frontend\npackages/frontend]
    api[Express API\npackages/backend]
    store[(In-Memory SQLite Store)]

    user -->|Uses in browser| browser
    browser -->|HTTP JSON requests| api
    api -->|SQL queries and writes| store
```

## Sequence: Create a TODO

```mermaid
sequenceDiagram
    actor User
    participant Frontend as React Frontend
    participant API as Express API
    participant Store as In-Memory SQLite Store

    User->>Frontend: Enter title, description, and due date
    User->>Frontend: Submit create task form
    Frontend->>API: POST /api/tasks\nJSON task payload
    API->>API: Validate title is present
    API->>Store: INSERT task row
    Store-->>API: Return inserted row id
    API->>Store: SELECT created task by id
    Store-->>API: Return created task record
    API-->>Frontend: 201 Created with task JSON
    Frontend->>Frontend: Increment refresh key
    Frontend->>API: GET /api/tasks
    API->>Store: SELECT tasks ordered by due date
    Store-->>API: Return task list
    API-->>Frontend: 200 OK with updated tasks
    Frontend-->>User: Render updated TODO list
```