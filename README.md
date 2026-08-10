<div align="center">

<h1>
  Swadesh Chatterjee
  <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="26px" alt="wave" />
</h1>

<p><b>Full-Stack Engineer</b> · Next.js &amp; TypeScript on the front, Java/Spring Boot and Node/Bun on the back</p>

<a href="https://github.com/swadesh-231">
  <img
    src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=21&duration=3200&pause=700&color=58A6FF&center=true&vCenter=true&width=720&lines=Full-Stack+Engineer+%E2%80%A2+Next.js+%2B+TypeScript+%2B+React;Java+%C2%B7+Spring+Boot+%C2%B7+Node%2FBun+%C2%B7+Express;PostgreSQL+%C2%B7+Redis+%C2%B7+Kafka+%C2%B7+Typed+APIs+end+to+end;Problem+Solving+%E2%80%A2+DSA+%E2%80%A2+Systems+Thinking"
    alt="typing-banner"
  />
</a>

<br/><br/>

<a href="https://www.swadesh.cc"><img src="https://img.shields.io/badge/Portfolio-swadesh.cc-111111?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio" /></a>
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

### About

```yaml
name:      Swadesh Chatterjee
role:      Full-Stack Engineer
frontend:  Next.js · React · TypeScript · Tailwind · shadcn/ui
backend:   Java · Spring Boot · Node/Bun · Express
data:      PostgreSQL · Redis · Prisma · Drizzle · JPA
strengths: API design · Data modelling · DSA & problem solving
location:  Bengaluru, India
email:     swadeshchatterjee512@gmail.com
```

**What I actually do:** own features end to end — model the data,
design the API contract, build the service, then ship the interface
that consumes it. One person, one coherent system, no handoff gaps.

- Building AI-driven products: streaming SSE pipelines, agentic workflows, LLM-backed services
- Comfortable in both ecosystems — **Spring Boot 3/4 + JPA** and **Bun/Express + TypeScript**
- Type safety across the wire: shared contracts, `Zod` validation, generated OpenAPI clients
- Care deeply about **indexes, query plans, caching and p99** — not just "it works locally"
- Sharpening **DSA on LeetCode**: optimal complexity, clean and readable solutions

</td>
<td valign="top" width="44%">

<img src="https://github-profile-summary-cards.vercel.app/api/cards/profile-details?username=swadesh-231&theme=tokyonight" alt="profile-details" />

</td>
</tr>
</table>

---

### How I Build a Product

```mermaid
flowchart LR
    UI["Next.js 16 · React 19<br/>TypeScript · Tailwind · shadcn/ui"]
    UI -->|"Server Actions · TanStack Query"| API["API Layer<br/>Express / Bun · Spring Boot REST"]

    API --> AUTH["Auth &amp; Access<br/>JWT · OAuth · RBAC"]
    API --> SVC["Domain Services<br/>validation · business rules"]

    SVC -->|"Prisma · Drizzle · JPA"| PG[("PostgreSQL<br/>indexed · pooled")]
    SVC -->|"read-through cache"| RD[("Redis<br/>cache · rate limit")]
    SVC -->|"domain events"| K{{"Kafka / Queue<br/>outbox · retries · DLQ"}}
    SVC -->|"SSE streams"| AI["AI Layer<br/>OpenAI · Gemini · Groq"]

    K --> WRK["Async Workers"]
    WRK --> PG
    API --> OBS["Observability<br/>structured logs · metrics · traces"]

    classDef edge fill:#1f6feb,stroke:#58a6ff,color:#fff
    classDef core fill:#238636,stroke:#3fb950,color:#fff
    classDef data fill:#8957e5,stroke:#bc8cff,color:#fff
    class UI,API edge
    class AUTH,SVC,WRK,AI core
    class PG,RD,K,OBS data
```

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
| **Accessibility & UX** | Keyboard paths, focus management, semantic markup, no layout shift on data load |
| **Testing** | Testcontainers for real Postgres/Kafka in CI, integration tests over mocks that lie |
| **Observability** | Structured logs with trace IDs, RED metrics per endpoint, alerts on p99 not p50 |

</details>

---

### Stack

<table>
<tr>
<td valign="top" width="50%">

#### Frontend
<img src="https://skillicons.dev/icons?i=nextjs,react,ts,tailwind&perline=4" alt="frontend" />

`Next.js 16` `React 19` `TypeScript` `Tailwind v4`
`shadcn/ui` `TanStack Query` `Framer Motion` `Zustand`

#### Node Ecosystem
<img src="https://skillicons.dev/icons?i=nodejs,bun,express,vite&perline=4" alt="node" />

`Node.js` `Bun` `Express` `tRPC` `Zod` `Vite`

#### Data
<img src="https://skillicons.dev/icons?i=postgres,redis,mongodb,mysql&perline=4" alt="data" />

`PostgreSQL (Neon)` `Redis` `MongoDB`
`Prisma` `Drizzle ORM` `Flyway` `JPA / Hibernate`

</td>
<td valign="top" width="50%">

#### Java Backend
<img src="https://skillicons.dev/icons?i=java,spring,graphql,kafka&perline=4" alt="java-backend" />

`Java 21` `Spring Boot 3/4` `Spring Security` `Spring Data JPA`
`Spring AI` `MapStruct` `Resilience4j` `Maven / Gradle`

#### APIs &amp; Auth
<img src="https://skillicons.dev/icons?i=nginx,rabbitmq,postman,firebase&perline=4" alt="apis" />

`REST` `GraphQL` `WebSockets` `SSE` `OpenAPI`
`JWT` `OAuth 2.0` `RBAC` `Clerk` `Better Auth`

#### Platform &amp; Tooling
<img src="https://skillicons.dev/icons?i=docker,aws,linux,git,githubactions,vercel&perline=6" alt="platform" />

`Docker` `AWS` `Vercel` `GitHub Actions` `Testcontainers` `Prometheus`

</td>
</tr>
</table>

---

### Featured Work

| Project | What it is | Stack |
| :-- | :-- | :-- |
| **[Flux](https://github.com/swadesh-231/flux)** | Agentic app builder — prompt in, running app out. Streams the build over SSE, renders a live Sandpack preview, exports source as a zip. Credit-metered plans, role-scoped model chains across OpenAI/Gemini/Groq. | `Next.js 16` `React 19` `Prisma` `Neon` `Clerk` `Bun` |
| **[Photo AI Studio](https://github.com/swadesh-231)** | Upload, preview and transform photos — background removal and anime/avatar styles — behind a Google Photos-style library shell. | `Spring Boot 4` `Spring AI` `JPA` `Next.js` `ImageKit` |
| **[Loophire](https://github.com/swadesh-231)** | AI interviewer and talent marketplace — resume-driven question generation, hand-rolled JWT + OAuth + RBAC instead of a managed provider. | `Bun` `TypeScript` `Express` `React` |
| **[Choco Cart](https://github.com/swadesh-231)** | Full e-commerce storefront with an admin panel for catalogue, orders and inventory. | `Next.js` `Drizzle ORM` `Neon` `Better Auth` |
| **[Stays](https://github.com/swadesh-231)** | Airbnb-style rental marketplace — search, availability, booking and payments. | `Next.js 16` `Prisma` `Postgres` `Arcjet` |
| **[AI CSV Lead Importer](https://github.com/swadesh-231)** | Two-stage profiling and batch extraction pipeline mapping arbitrary CSVs onto a fixed 15-field CRM schema. | `LLM` `Node` `TypeScript` |
| **[Ledger](https://github.com/swadesh-231)** | Expense tracker with categorised analytics over a fully typed API layer. | `Bun` `TypeScript` `React` |

> Replace the placeholder links with the real repo URLs — the table structure is ready.

---

### Problem Solving

Consistent practice on **[LeetCode](https://leetcode.com/u/swadesh072/)** — arrays, graphs, dynamic
programming and system-design fundamentals. The habit shows up in the work: better complexity
choices, tighter data structures, and fewer accidental O(n²) loops in production code.

<p align="center">
  <img src="https://leetcard.jacoblin.cool/swadesh072?theme=nord&font=Fira%20Code&ext=heatmap" alt="leetcode-stats" />
</p>

---

### GitHub Metrics

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

---

<div align="center">

### Open to full-stack &amp; product engineering roles

**Next.js · TypeScript · React · Node/Express · Java · Spring Boot**

<a href="https://www.swadesh.cc"><img src="https://img.shields.io/badge/-See%20my%20work-111111?style=for-the-badge&logo=vercel&logoColor=white" alt="Portfolio" /></a>&nbsp;
<a href="https://www.linkedin.com/in/swadeshchatterjee/"><img src="https://img.shields.io/badge/-Let's%20talk-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>&nbsp;
<a href="mailto:swadeshchatterjee512@gmail.com"><img src="https://img.shields.io/badge/-Email%20me-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>

<br/><br/>

<i>From <a href="https://github.com/swadesh-231">swadesh-231</a> — thanks for stopping by.</i>

</div>
