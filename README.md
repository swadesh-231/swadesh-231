<div align="center">

# Swadesh Chatterjee

### Full-Stack Engineer

Schema to screen — I model the data, design the contract, build the service, and ship the interface that consumes it.

<a href="https://www.swadesh.cc"><img src="https://img.shields.io/badge/Portfolio-swadesh.cc-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio" /></a>
<a href="https://www.linkedin.com/in/swadeshchatterjee/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
<a href="https://twitter.com/Swadesh072"><img src="https://img.shields.io/badge/Swadesh072-000000?style=for-the-badge&logo=x&logoColor=white" alt="X" /></a>
<a href="https://leetcode.com/u/swadesh072/"><img src="https://img.shields.io/badge/LeetCode-FFA116?style=for-the-badge&logo=leetcode&logoColor=black" alt="LeetCode" /></a>
<a href="mailto:swadeshchatterjee512@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>

<img src="https://img.shields.io/badge/Bengaluru-India-3FB950?style=flat-square" alt="Location" />
<img src="https://img.shields.io/badge/Open_to-Full--Stack_Roles-58A6FF?style=flat-square" alt="Status" />
<img src="https://img.shields.io/github/followers/swadesh-231?style=flat-square&logo=github&label=Followers&color=BC8CFF" alt="Followers" />

</div>

---

## 01 · About

<table>
<tr>
<td valign="top" width="52%">

```yaml
name:      Swadesh Chatterjee
role:      Full-Stack Engineer
frontend:  Next.js · React · TypeScript · Tailwind
backend:   Java · Spring Boot · Node/Bun · Express
data:      PostgreSQL · Redis · Prisma · Drizzle · JPA
strengths: API design · data modelling · DSA
location:  Bengaluru, India
email:     swadeshchatterjee512@gmail.com
```

One person, one coherent system, no handoff gaps. I care about the
parts that only show up under load — indexes, query plans, cache
invalidation, p99 — not just the happy path on localhost.

</td>
<td valign="top" width="48%">

```ts
const now = {
  building : "Flux — agentic app builder (SSE + Sandpack)",
  shipping : "Spring Boot 4 + Spring AI image pipeline",
  learning : "Kafka semantics · outbox · idempotency",
  grinding : "LeetCode — graphs and DP",
} as const;
```

- Streaming **SSE** pipelines, agentic workflows, LLM-backed services
- Fluent in **both** stacks — Spring Boot 3/4 + JPA **and** Bun/Express + TS
- Type safety across the wire — shared contracts, `Zod`, generated OpenAPI clients
- Ship features whole: migration, endpoint, UI, tests, dashboard

</td>
</tr>
</table>

---

## 02 · How I Build a Product

```mermaid
flowchart LR
    UI["Next.js 16 · React 19<br/>TypeScript · Tailwind · shadcn/ui"]
    UI -->|"Server Actions · TanStack Query"| API["API Layer<br/>Express / Bun · Spring Boot REST"]

    API --> AUTH["Auth and Access<br/>JWT · OAuth 2.0 · RBAC"]
    API --> SVC["Domain Services<br/>validation · business rules"]

    SVC -->|"Prisma · Drizzle · JPA"| PG[("PostgreSQL<br/>indexed · pooled")]
    SVC -->|"read-through cache"| RD[("Redis<br/>cache · rate limit")]
    SVC -->|"domain events"| K{{"Kafka / Queue<br/>outbox · retries · DLQ"}}
    SVC -->|"SSE streams"| AI["AI Layer<br/>OpenAI · Gemini · Groq"]

    K --> WRK["Async Workers"]
    WRK --> PG
    API --> OBS["Observability<br/>structured logs · metrics · traces"]

    classDef edge fill:#1F6FEB,stroke:#58A6FF,color:#fff
    classDef core fill:#238636,stroke:#3FB950,color:#fff
    classDef data fill:#8957E5,stroke:#BC8CFF,color:#fff
    class UI,API edge
    class AUTH,SVC,WRK,AI core
    class PG,RD,K,OBS data
```

<details>
<summary><b>A write request, hop by hop</b></summary>

<br/>

```mermaid
sequenceDiagram
    autonumber
    participant C as Client
    participant A as API (Bun / Spring)
    participant R as Redis
    participant D as PostgreSQL
    participant Q as Kafka
    participant W as Worker

    C->>A: POST /orders (Idempotency-Key)
    A->>R: reserve key · rate-limit bucket
    alt key already seen
        R-->>A: cached response
        A-->>C: 200 (replayed, no side effects)
    else first time
        A->>A: validate (Zod / Bean Validation)
        A->>D: BEGIN · write order + outbox row
        D-->>A: COMMIT
        A-->>C: 201 Created
        D->>Q: outbox relay publishes event
        Q->>W: consume with retry and backoff
        W->>D: project read model
        Note over Q,W: poison messages land in DLQ
    end
```

</details>

<details>
<summary><b>The rules I hold myself to</b></summary>

<br/>

| Concern | How I handle it |
| :-- | :-- |
| **Contracts** | One source of truth for types — schema-first models, `Zod`/Bean Validation at every boundary, versioned and documented endpoints |
| **Data access** | Explicit fetch plans over lazy-loading surprises, covering indexes, `EXPLAIN ANALYZE` before shipping |
| **Correctness** | Idempotency keys on writes, transactional outbox for events, optimistic locking on contended rows |
| **Frontend** | Server components by default, client state only where it earns its place, suspense boundaries and real loading/error states |
| **Resilience** | Timeouts on every hop, retries with jitter, circuit breakers, dead-letter queues |
| **Caching** | Read-through Redis with explicit TTLs and invalidation on write — never "cache and hope" |
| **Security** | Short-lived JWTs with rotation, least-privilege tokens, parameterised queries, secrets out of the repo |
| **Testing** | Testcontainers for real Postgres/Kafka in CI, integration tests over mocks that lie |
| **Observability** | Structured logs with trace IDs, RED metrics per endpoint, alerts on p99 not p50 |

</details>

---

## 03 · Stack

<table>
<tr>
<td valign="top" width="50%">

**Frontend**

<img src="https://img.shields.io/badge/Next.js_16-000000?style=flat-square&logo=nextdotjs&logoColor=white" /> <img src="https://img.shields.io/badge/React_19-20232A?style=flat-square&logo=react&logoColor=61DAFB" /> <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" /> <img src="https://img.shields.io/badge/Tailwind_v4-0F172A?style=flat-square&logo=tailwindcss&logoColor=38BDF8" /> <img src="https://img.shields.io/badge/shadcn/ui-000000?style=flat-square&logo=shadcnui&logoColor=white" /> <img src="https://img.shields.io/badge/TanStack_Query-FF4154?style=flat-square&logo=reactquery&logoColor=white" /> <img src="https://img.shields.io/badge/Zustand-433E38?style=flat-square" />

**Node Ecosystem**

<img src="https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white" /> <img src="https://img.shields.io/badge/Bun-14151A?style=flat-square&logo=bun&logoColor=FBF0DF" /> <img src="https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white" /> <img src="https://img.shields.io/badge/tRPC-2596BE?style=flat-square&logo=trpc&logoColor=white" /> <img src="https://img.shields.io/badge/Zod-3E67B1?style=flat-square&logo=zod&logoColor=white" /> <img src="https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white" />

**Data**

<img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white" /> <img src="https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white" /> <img src="https://img.shields.io/badge/MongoDB-47A248?style=flat-square&logo=mongodb&logoColor=white" /> <img src="https://img.shields.io/badge/Prisma-2D3748?style=flat-square&logo=prisma&logoColor=white" /> <img src="https://img.shields.io/badge/Drizzle-C5F74F?style=flat-square&logo=drizzle&logoColor=black" /> <img src="https://img.shields.io/badge/Hibernate_JPA-59666C?style=flat-square&logo=hibernate&logoColor=white" /> <img src="https://img.shields.io/badge/Flyway-CC0000?style=flat-square&logo=flyway&logoColor=white" />

</td>
<td valign="top" width="50%">

**Java Backend**

<img src="https://img.shields.io/badge/Java_21-ED8B00?style=flat-square&logo=openjdk&logoColor=white" /> <img src="https://img.shields.io/badge/Spring_Boot_3/4-6DB33F?style=flat-square&logo=springboot&logoColor=white" /> <img src="https://img.shields.io/badge/Spring_Security-6DB33F?style=flat-square&logo=springsecurity&logoColor=white" /> <img src="https://img.shields.io/badge/Spring_Data_JPA-6DB33F?style=flat-square&logo=spring&logoColor=white" /> <img src="https://img.shields.io/badge/Spring_AI-6DB33F?style=flat-square&logo=spring&logoColor=white" /> <img src="https://img.shields.io/badge/Resilience4j-2C3E50?style=flat-square" /> <img src="https://img.shields.io/badge/Maven-C71A36?style=flat-square&logo=apachemaven&logoColor=white" /> <img src="https://img.shields.io/badge/Gradle-02303A?style=flat-square&logo=gradle&logoColor=white" />

**APIs and Auth**

<img src="https://img.shields.io/badge/REST-025E8C?style=flat-square" /> <img src="https://img.shields.io/badge/GraphQL-E10098?style=flat-square&logo=graphql&logoColor=white" /> <img src="https://img.shields.io/badge/Kafka-231F20?style=flat-square&logo=apachekafka&logoColor=white" /> <img src="https://img.shields.io/badge/WebSockets_SSE-010101?style=flat-square&logo=socketdotio&logoColor=white" /> <img src="https://img.shields.io/badge/OpenAPI-6BA539?style=flat-square&logo=openapiinitiative&logoColor=white" /> <img src="https://img.shields.io/badge/JWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white" /> <img src="https://img.shields.io/badge/OAuth_2.0-EB5424?style=flat-square&logo=auth0&logoColor=white" /> <img src="https://img.shields.io/badge/Clerk-6C47FF?style=flat-square&logo=clerk&logoColor=white" />

**Platform and Tooling**

<img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white" /> <img src="https://img.shields.io/badge/AWS-232F3E?style=flat-square&logo=amazonwebservices&logoColor=FF9900" /> <img src="https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white" /> <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white" /> <img src="https://img.shields.io/badge/Linux-FCC624?style=flat-square&logo=linux&logoColor=black" /> <img src="https://img.shields.io/badge/Testcontainers-291A3F?style=flat-square&logo=docker&logoColor=white" /> <img src="https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white" />

</td>
</tr>
</table>

---

## 04 · Selected Work

<table>
<tr>
<td width="50%" valign="top">

### [Flux](https://github.com/swadesh-231/flux)

Agentic app builder — prompt in, running app out. Streams the build
over SSE, renders a live Sandpack preview, exports source as a zip.
Credit-metered plans and role-scoped model chains across OpenAI,
Gemini and Groq.

`Next.js 16` `React 19` `Prisma` `Neon` `Clerk` `Bun`

</td>
<td width="50%" valign="top">

### [Photo AI Studio](https://github.com/swadesh-231)

Upload, preview and transform photos — background removal and
anime/avatar styles — behind a Google Photos-style library shell,
with transformation state persisted per asset.

`Spring Boot 4` `Spring AI` `JPA` `Next.js` `ImageKit`

</td>
</tr>
<tr>
<td width="50%" valign="top">

### [Loophire](https://github.com/swadesh-231)

AI interviewer and talent marketplace — resume-driven question
generation, scored transcripts, and hand-rolled JWT + OAuth + RBAC
instead of a managed auth provider.

`Bun` `TypeScript` `Express` `React`

</td>
<td width="50%" valign="top">

### [Choco Cart](https://github.com/swadesh-231)

Full e-commerce storefront with an admin panel for catalogue,
orders and inventory — typed data access throughout, auth handled
at the edge.

`Next.js` `Drizzle ORM` `Neon` `Better Auth`

</td>
</tr>
<tr>
<td width="50%" valign="top">

### [Stays](https://github.com/swadesh-231)

Airbnb-style rental marketplace — search, availability windows,
booking and payments, with overlap-safe reservation logic and bot
protection on write paths.

`Next.js 16` `Prisma` `PostgreSQL` `Arcjet`

</td>
<td width="50%" valign="top">

### [AI CSV Lead Importer](https://github.com/swadesh-231)

Two-stage profiling and batch extraction pipeline that maps
arbitrary CSV shapes onto a fixed 15-field CRM schema — profile
first, then extract in batches with validation and retries.

`LLM` `Node.js` `TypeScript`

</td>
</tr>
</table>

<details>
<summary><b>More projects</b></summary>

<br/>

| Project | What it is | Stack |
| :-- | :-- | :-- |
| **[Ledger](https://github.com/swadesh-231)** | Expense tracker with categorised analytics over a fully typed API layer | `Bun` `TypeScript` `React` |
| **[Auth Service](https://github.com/swadesh-231)** | Production-grade email-OTP auth — rate limits, expiry, replay protection | `Spring Boot` `PostgreSQL` `Redis` |
| **[DSA Pattern Tracker](https://github.com/swadesh-231)** | Tracks problems by pattern rather than by list, with spaced revision | `Next.js` `TypeScript` `Postgres` |

</details>

---

## 05 · Problem Solving

Consistent practice on **[LeetCode](https://leetcode.com/u/swadesh072/)** — arrays, graphs, dynamic
programming and system-design fundamentals. It shows up in the work: better complexity choices,
tighter data structures, fewer accidental O(n²) loops in production code.

```mermaid
flowchart LR
    P["Problem"] --> B["Brute force<br/>establish correctness"]
    B --> I["Find the invariant<br/>what actually changes?"]
    I --> S["Pick the structure<br/>heap · map · monotonic stack · DSU"]
    S --> O["Optimise<br/>time and space bounds"]
    O --> E["Edge cases<br/>empty · duplicates · overflow"]
    E --> W["Write it clean<br/>a reviewer can follow it"]

    classDef a fill:#1F6FEB,stroke:#58A6FF,color:#fff
    classDef b fill:#238636,stroke:#3FB950,color:#fff
    classDef c fill:#8957E5,stroke:#BC8CFF,color:#fff
    class P,B a
    class I,S b
    class O,E,W c
```

---

<div align="center">

### Open to full-stack and product engineering roles

Next.js · TypeScript · React · Node/Express · Java · Spring Boot

<a href="https://www.swadesh.cc"><img src="https://img.shields.io/badge/See_my_work-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio" /></a>
<a href="https://www.linkedin.com/in/swadeshchatterjee/"><img src="https://img.shields.io/badge/Let's_talk-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
<a href="mailto:swadeshchatterjee512@gmail.com"><img src="https://img.shields.io/badge/Email_me-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>

</div>
