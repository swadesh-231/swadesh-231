<!--
  README.md — Swadesh Chatterjee
  Backend Engineer · Java & Spring Boot · Distributed Systems
  ──────────────────────────────────────────────────────────
  Notes:
   - GitHub Stats / Top Languages use `github-profile-summary-cards`
     (separate Vercel deployment) because the public
     github-readme-stats instance has been rate-limited 2025–2026.
   - Streak Stats use streak-stats.demolab.com (Heroku version deprecated).
   - The Mermaid block below renders natively on GitHub — no external service.
   - Replace the repo links in "Featured Work" with your real repos.
-->

<div align="center">

<h1>
  Hi, I'm Swadesh Chatterjee
  <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="28px" alt="wave" />
</h1>

<a href="https://github.com/swadesh-231">
  <img
    src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3200&pause=700&color=58A6FF&center=true&vCenter=true&width=700&lines=Backend+Engineer+%E2%80%A2+Java+%26+Spring+Boot;Distributed+Systems+%E2%80%A2+Event-Driven+Architecture;PostgreSQL+Tuning+%E2%80%A2+Caching+%E2%80%A2+Sub-100ms+p99;Full-Stack+when+it+counts+%E2%80%A2+Next.js+%2B+TypeScript"
    alt="typing-banner"
  />
</a>

<br/><br/>

<a href="https://www.linkedin.com/in/swadeshchatterjee/"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
<a href="https://twitter.com/Swadesh072"><img src="https://img.shields.io/badge/@Swadesh072-000000?style=for-the-badge&logo=x&logoColor=white" alt="X" /></a>
<a href="https://leetcode.com/u/swadesh072/"><img src="https://img.shields.io/badge/LeetCode-FFA116?style=for-the-badge&logo=leetcode&logoColor=black" alt="LeetCode" /></a>
<a href="mailto:swadeshchatterjee512@gmail.com"><img src="https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
<br/>
<img src="https://img.shields.io/github/followers/swadesh-231?logo=github&style=flat-square&label=Followers&color=58A6FF" alt="followers" />
<img src="https://komarev.com/ghpvc/?username=swadesh-231&label=Profile%20Views&style=flat-square&color=0e75b6" alt="views" />

</div>

---

<table>
<tr>
<td valign="top" width="56%">

### 🧭 About

```yaml
name:      Swadesh Chatterjee
role:      Backend Engineer
primary:   Java · Spring Boot · PostgreSQL · Kafka
secondary: TypeScript · Next.js · React · Node/Bun
domains:   Distributed Systems · Microservices · API Design
location:  Bengaluru, India 🇮🇳
email:     swadeshchatterjee512@gmail.com
```

**What I actually do:** design and ship backend services that stay
correct under concurrency and fast under load — clean domain
boundaries, well-indexed schemas, idempotent APIs, and
observability baked in from day one.

- 🔭 Building **event-driven microservices** on Spring Boot + Kafka
- 🧱 Deep in **JVM concurrency**, **JPA/Hibernate internals**, and **query planning**
- ⚡ Chasing **sub-100 ms p99** through caching, connection pooling, and N+1 elimination
- 🎯 Ship full-stack when the product needs it — **Next.js 16 + TypeScript** front ends
- 🧠 Sharpening DSA on **LeetCode**: optimal complexity, readable code

</td>
<td valign="top" width="44%">

<img src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=swadesh-231&theme=tokyonight" alt="profile-details" />

</td>
</tr>
</table>

---

### 🏗️ How I Architect a Service

```mermaid
flowchart LR
    C["Next.js 16<br/>React · TypeScript"] -->|HTTPS| GW["API Gateway<br/>Spring Cloud Gateway"]
    GW -->|JWT / RBAC| AUTH["Auth Service<br/>Spring Security"]
    GW --> SVC["Domain Services<br/>Spring Boot · REST + GraphQL"]

    SVC -->|Read-through| RD[("Redis<br/>cache + rate limit")]
    SVC -->|JPA / Hibernate| PG[("PostgreSQL<br/>indexed · pooled")]
    SVC -->|Publish| K{{"Kafka<br/>domain events"}}

    K --> WRK["Async Workers<br/>outbox · retries · DLQ"]
    WRK --> PG

    SVC --> OBS["Observability<br/>Actuator · Micrometer · Prometheus"]

    classDef edge fill:#1f6feb,stroke:#58a6ff,color:#fff
    classDef core fill:#238636,stroke:#3fb950,color:#fff
    classDef data fill:#8957e5,stroke:#bc8cff,color:#fff
    class C,GW edge
    class AUTH,SVC,WRK core
    class RD,PG,K,OBS data
```

<details>
<summary><b>The rules I hold myself to</b></summary>

<br/>

| Concern | How I handle it |
| :-- | :-- |
| **Correctness** | Idempotency keys on writes, transactional outbox for event publishing, optimistic locking on contended rows |
| **Data access** | Explicit fetch plans over lazy-loading surprises; covering indexes; `EXPLAIN ANALYZE` before shipping |
| **Concurrency** | Virtual threads / bounded pools over unbounded async; no shared mutable state across requests |
| **Resilience** | Timeouts on every hop, circuit breakers, exponential backoff with jitter, dead-letter queues |
| **Caching** | Read-through Redis with explicit TTLs and invalidation on write — never "cache and hope" |
| **API design** | Versioned contracts, cursor pagination, RFC 7807 problem details, OpenAPI generated from code |
| **Testing** | Testcontainers for real Postgres/Kafka in CI — no in-memory H2 lies |
| **Observability** | Structured logs with trace IDs, RED metrics per endpoint, alerts on p99 not p50 |

</details>

---

### 🛠️ Stack

<table>
<tr>
<td valign="top" width="50%">

#### ☕ Core Backend
<img src="https://skillicons.dev/icons?i=java,spring,kotlin,go&perline=4" alt="core-backend" />

`Java 21` `Spring Boot 3` `Spring Security` `Spring Data JPA`
`Hibernate` `Spring Cloud Gateway` `Resilience4j` `Maven / Gradle`

#### 🔌 APIs & Messaging
<img src="https://skillicons.dev/icons?i=graphql,kafka,rabbitmq,nginx&perline=4" alt="apis" />

`REST` `GraphQL` `gRPC` `WebSockets` `Kafka` `RabbitMQ` `OpenAPI`

#### 🗄️ Data
<img src="https://skillicons.dev/icons?i=postgres,mysql,redis,mongodb&perline=4" alt="data" />

`PostgreSQL` `Redis` `MongoDB` `Flyway` `Prisma` `Drizzle ORM`

</td>
<td valign="top" width="50%">

#### 🌐 Frontend (when needed)
<img src="https://skillicons.dev/icons?i=nextjs,react,ts,tailwind&perline=4" alt="frontend" />

`Next.js 16` `React 19` `TypeScript` `Tailwind v4` `shadcn/ui` `TanStack Query`

#### 🟩 Node Ecosystem
<img src="https://skillicons.dev/icons?i=nodejs,bun,express,vite&perline=4" alt="node" />

`Node.js` `Bun` `Express` `Zod` `tRPC`

#### ☁️ Platform & Tooling
<img src="https://skillicons.dev/icons?i=docker,kubernetes,aws,linux,git,githubactions&perline=6" alt="platform" />

`Docker` `Kubernetes` `AWS` `GitHub Actions` `Prometheus` `Grafana` `Testcontainers`

</td>
</tr>
</table>

---

### 🚀 Featured Work

| Project | What it is | Stack |
| :-- | :-- | :-- |
| **[Loophire](https://github.com/swadesh-231)** | AI interviewer & talent marketplace — resume-driven question generation, hand-rolled JWT + OAuth + RBAC | `Bun` `TypeScript` `Express` `React` |
| **[AI CSV Lead Importer](https://github.com/swadesh-231)** | Two-stage profiling + batch extraction pipeline mapping arbitrary CSVs onto a fixed 15-field CRM schema | `LLM` `Node` `TypeScript` |
| **[Stays](https://github.com/swadesh-231)** | Airbnb-style rental marketplace with search, booking and payments | `Next.js 16` `Prisma` `Postgres` `Better Auth` |
| **[Ledger](https://github.com/swadesh-231)** | Expense tracker with categorized analytics and a typed API layer | `Bun` `TypeScript` `React` |
| **[Job Application Agent](https://github.com/swadesh-231)** | Agentic workflow that tailors and submits applications end to end | `TypeScript` `LLM` |

> Swap these links for the real repo URLs — the table structure is ready.

---

### 📊 GitHub Metrics

<p align="center">
  <img src="https://streak-stats.demolab.com?user=swadesh-231&theme=tokyonight&hide_border=true&date_format=M%20j%5B%2C%20Y%5D" alt="streak" height="180" />
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/stats?username=swadesh-231&theme=tokyonight" alt="stats" height="180" />
</p>

<p align="center">
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/most-commit-language?username=swadesh-231&theme=tokyonight" alt="top-langs" height="180" />
  <img src="https://github-profile-summary-cards.vercel.app/api/cards/productive-time?username=swadesh-231&theme=tokyonight&utcOffset=5.5" alt="productive-time" height="180" />
</p>

<p align="center">
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=swadesh-231&bg_color=1a1b27&color=70a5fd&line=bf91f3&point=38bdae&hide_border=true&area=true" alt="activity-graph" />
</p>

<p align="center">
  <img src="https://github-profile-trophy.vercel.app/?username=swadesh-231&theme=tokyonight&no-frame=true&no-bg=true&row=1&column=7&margin-w=8&margin-h=8" alt="trophies" />
</p>

---

<div align="center">

### 🤝 Open to backend & platform engineering roles

**Java · Spring Boot · Distributed Systems**

<a href="https://www.linkedin.com/in/swadeshchatterjee/"><img src="https://img.shields.io/badge/-Let's%20talk-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>&nbsp;
<a href="mailto:swadeshchatterjee512@gmail.com"><img src="https://img.shields.io/badge/-Email%20me-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>

<br/><br/>

<i>⭐ From <a href="https://github.com/swadesh-231">swadesh-231</a> — thanks for stopping by.</i>

</div>
