<div align="center">

# 🎋 BambooSync

**Real-time collaboration, built around a modern Kanban workflow.**

BambooSync is a software project focused on building a collaborative Kanban platform where teams can organize work, manage tasks, and stay synchronized in real time.

[Explore the Backend](https://github.com/BambooSync/bamboo-sync-board-server)

</div>

---

## 🚀 Project

### BambooSync Board Server

[`bamboo-sync-board-server`](https://github.com/BambooSync/bamboo-sync-board-server) is the core backend of BambooSync.  
It provides the APIs, authentication, data management, and real-time communication required by the collaborative board experience.

### ✨ Main Features

- **Kanban workspace management** — create and manage boards, columns, tasks, members, task ordering, priorities, and due dates.
- **Authentication & authorization** — JWT-based authentication with board-level `OWNER`, `EDITOR`, and `VIEWER` roles.
- **Real-time collaboration** — Socket.IO rooms for live task events, online presence, cursor tracking, and typing indicators.
- **Reliable data operations** — PostgreSQL with Prisma ORM, database relationships, cascading rules, and transactional operations.
- **Redis integration** — Cache-Aside with TTL and invalidation, rate-limiting storage, and Redis Pub/Sub for multi-instance Socket.IO synchronization.
- **Scalable real-time architecture** — Redis Socket.IO Adapter enables events to remain synchronized when the backend runs across multiple instances.
- **Production-oriented networking** — Nginx acts as a reverse proxy for HTTP and WebSocket traffic.
- **Containerized environment** — Docker and Docker Compose simplify development and deployment.
- **Testing support** — Jest and Supertest are configured for unit and end-to-end testing.

---

## 🧱 Architecture

BambooSync Server follows a **Modular Monolith** architecture using NestJS.

```text
                    ┌────────────────────┐
                    │      Clients       │
                    └─────────┬──────────┘
                              │
                       HTTP / WebSocket
                              │
                    ┌─────────▼──────────┐
                    │       Nginx        │
                    │   Reverse Proxy    │
                    └─────────┬──────────┘
                              │
                ┌─────────────▼─────────────┐
                │       NestJS Server       │
                │                           │
                │  REST API   +  Socket.IO  │
                └──────┬─────────────┬──────┘
                       │             │
                 ┌─────▼─────┐ ┌────▼──────┐
                 │ PostgreSQL│ │   Redis   │
                 │  + Prisma │ │Cache/PubSub│
                 └───────────┘ └───────────┘
```

HTTP/REST is used for persistent data operations, while Socket.IO handles real-time and ephemeral collaboration events.

---

## 🛠️ Tech Stack

| Area | Technologies |
|---|---|
| Language | TypeScript |
| Backend | Node.js, NestJS |
| Database | PostgreSQL |
| ORM | Prisma ORM |
| Real-time | Socket.IO, NestJS WebSockets |
| Cache & Pub/Sub | Redis, ioredis |
| Authentication | JWT, Passport, bcrypt |
| Reverse Proxy | Nginx |
| Containerization | Docker, Docker Compose |
| Testing | Jest, Supertest |

---

## 📦 Repository

| Repository | Description |
|---|---|
| [`bamboo-sync-board-server`](https://github.com/BambooSync/bamboo-sync-board-server) | Backend server for the BambooSync real-time collaborative Kanban platform |

The repository also contains detailed technical documentation covering architecture, APIs, database design, deployment, and engineering decisions.

---

<div align="center">

### Built for real-time teamwork. 🎋

</div>
