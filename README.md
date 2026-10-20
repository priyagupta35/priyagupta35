<div align="center">

<!-- Animated Typing Header -->
<a href="https://github.com/priyagupta35">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=24&pause=1000&color=38BDF8&center=true&vCenter=true&width=680&lines=Hi%2C+I'm+Priya+Gupta+%F0%9F%91%8B;Backend+Software+Engineer+%7C+Distributed+Systems;Java+17+%2B+Spring+Boot+3+%2B+Microservices;Python+%2B+Apache+Kafka+%2B+Redis+GEO;Architecting+Resilient+Event-Driven+Backends" alt="Typing Header" />
</a>

<p align="center">
  <b>B.Tech in Computer Science & Business Systems (CSBS)</b> • Netaji Subhash Engineering College, Kolkata<br/>
  <i>Specializing in Distributed Systems, High-Concurrency REST APIs, Event-Driven Architectures & Cloud Deployments</i>
</p>

<!-- Social & Badges Bar -->
<p align="center">
  <a href="https://www.linkedin.com/in/priya-gupta35" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
  </a>
  <a href="mailto:priyaguptaindia56@gmail.com">
    <img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" />
  </a>
  <a href="https://github.com/priyagupta35">
    <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
  </a>
  <img src="https://img.shields.io/badge/Location-Kolkata%2C%20India-blue?style=for-the-badge&logo=googlemaps&logoColor=white" alt="Location" />
</p>

</div>

---

### ⚡ Developer Snapshot

```bash
$ curl -s https://priyagupta.dev/status | jq
{
  "name": "Priya Gupta",
  "education": "B.Tech in CSBS (2023 - 2027) | CGPA: 7.33",
  "primary_languages": ["Java 17+", "Python 3.11+", "SQL"],
  "core_backend": ["Spring Boot 3", "FastAPI", "Spring Data JPA", "Spring Security 6"],
  "distributed_systems": ["Apache Kafka (KRaft)", "Redis (GEO & Cache)", "WebSockets"],
  "databases": ["PostgreSQL (Neon Serverless)", "MySQL 8.0"],
  "infrastructure": ["Docker", "Docker Compose", "Render Cloud", "AWS Foundations"],
  "open_to_work": "Full-Time SDE-1 / Backend Engineer / SDE Intern"
}
```

---

### 🛠️ Technical Arsenal

<div align="center">

| Domain | Technologies & Frameworks |
| :--- | :--- |
| **Languages** | `Java 17+` • `Python 3.11+` • `SQL (PostgreSQL, MySQL)` |
| **Backend & Microservices** | `Spring Boot 3` • `Spring MVC` • `Spring Data JPA` • `Spring Security 6` • `Hibernate ORM` • `FastAPI` • `SQLAlchemy` • `Pydantic` |
| **Messaging & Caching** | `Apache Kafka (KRaft, Consumer Groups, DLQ)` • `Redis GEO Spatial Indexing` • `Redis TTL Cache` • `WebSockets` |
| **Databases & Pooling** | `PostgreSQL (Neon Cloud)` • `MySQL 8.0` • `HikariCP Connection Pool` • `ACID Transactions` |
| **DevOps & Cloud** | `Docker` • `Docker Compose` • `Multi-Stage Builds` • `Render Platform` • `AWS Cloud Foundations` • `Maven` • `Git` • `Linux CLI` |
| **API & Observability** | `RESTful API Design` • `JWT RBAC` • `OpenAPI 3 / Swagger UI` • `Prometheus Metrics` • `Streamlit 3D Maps` • `Apache Log4j2` |

<br/>

<p align="center">
  <img src="https://skillicons.dev/icons?i=java,spring,python,fastapi,kafka,redis,postgres,mysql,docker,maven,git,postman&theme=dark" alt="Skills Grid" />
</p>

</div>

---

### 🚀 Featured Production Engineering Projects

#### 1. 📦 [LogiStream — Event-Driven Logistics & Real-Time Delivery Backend](https://github.com/priyagupta35/LogiStream)
> **Asynchronous Event-Driven Logistics Infrastructure with Apache Kafka & Redis GEO**  
> `Python 3.11` • `FastAPI` • `Apache Kafka (KRaft)` • `Redis GEO` • `PostgreSQL` • `Docker Compose` • `Streamlit 3D`

[![Repository](https://img.shields.io/badge/GitHub-LogiStream-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/priyagupta35/LogiStream)
[![Kafka](https://img.shields.io/badge/Kafka-KRaft_Partitioned-231F20?style=flat-square&logo=apachekafka&logoColor=white)](https://github.com/priyagupta35/LogiStream)
[![Redis GEO](https://img.shields.io/badge/Redis-GEO_Spatial-DC382D?style=flat-square&logo=redis&logoColor=white)](https://github.com/priyagupta35/LogiStream)
[![Docker Compose](https://img.shields.io/badge/Docker_Compose-Multi--Service-2496ED?style=flat-square&logo=docker&logoColor=white)](https://github.com/priyagupta35/LogiStream)

* **Event-Driven Lifecycle:** Publishes and streams order states (`OrderCreated`, `DriverAssigned`, `InTransit`, `OrderDelivered`) via partitioned Kafka topics keyed by `order_id`.
* **Sub-Millisecond Driver Matching:** Employs Redis `GEOSEARCH` to identify and dispatch the nearest available delivery driver in sub-milliseconds based on spatial coordinates.
* **Transactional Idempotency & Fault Tolerance:** Couples business state updates with a `processed_events` table in a single atomic DB transaction before committing Kafka consumer offsets, with automatic Dead Letter Queue (DLQ) retry routing.
* **Live Telemetry & Visuals:** Containerized via Docker Compose with Prometheus metrics export and an interactive 3D Streamlit & PyDeck operations tracking dashboard.

<details>
<summary><b>🔍 View LogiStream Architecture & Event Flow</b></summary>

```
[Client / API] ──(OrderCreated)──► [Kafka: orders.events]
                                          │
                                          ▼
                                 [Dispatch Consumer]
                                          │
                  ┌───────────────────────┴───────────────────────┐
                  ▼                                               ▼
       [Redis GEO Proximity Query]                     [PostgreSQL Transaction]
       (Find nearest available driver)                 (processed_events + DB update)
                  │                                               │
                  └───────────────────────┬───────────────────────┘
                                          ▼
                               [Commit Kafka Offset]
                                          │
                      (Success) ──────────┴──────────► (Failure / Malformed)
                          │                                     │
                          ▼                                     ▼
             [delivery.events Topic]                   [orders.dlq Topic]
```
</details>

---

#### 2. 📰 [TechPulse — Microservices Tech News Platform & AI Summarizer](https://github.com/priyagupta35/techpulse)
> **Decoupled Spring Boot Microservices Architecture with Spring AI & DeepSeek LLM**  
> `Java 17` • `Spring Boot 3` • `Spring Security 6` • `Spring AI` • `DeepSeek / Ollama` • `PostgreSQL (Neon)` • `Docker` • `Render`

[![Delivery Service Live](https://img.shields.io/badge/Delivery_Service-Live_API-00E599?style=flat-square&logo=render&logoColor=black)](https://news-delivery-service.onrender.com/api/articles)
[![Ingestion Service Health](https://img.shields.io/badge/Ingestion_Service-Health_OK-blue?style=flat-square&logo=render)](https://news-ingestion-service-3.onrender.com/api/ingestion/health)
[![Docker Multi-Container](https://img.shields.io/badge/Docker_Compose-Multi--Container-2496ED?style=flat-square&logo=docker&logoColor=white)](https://github.com/priyagupta35/techpulse-docker)

* **Microservices Separation:** Decomposed monolithic backend into two independent services to isolate scheduled data ingestion workloads from client-facing REST APIs:
  - **[News Ingestion Service](https://github.com/priyagupta35/news-ingestion-service):** Automated Spring Scheduler polling NewsAPI every 30 mins with Spring Data JPA `existsByUrl()` duplicate filtering.
  - **[News Delivery Service](https://github.com/priyagupta35/news-delivery-service):** Exposes secured REST endpoints protected by stateless Spring Security 6 JWT and role-based access control (`READER`, `CONTRIBUTOR`, `ADMIN`).
* **Automated AI Briefings:** Integrated **Spring AI** with **DeepSeek-r1:1.5b via Ollama** to generate real-time 2–3 sentence executive summaries for incoming technology articles.
* **Cloud Orchestration:** Fully containerized with multi-stage Docker builds and deployed continuously on Render with centralized Log4j2 rolling logging.

<details>
<summary><b>🔍 View TechPulse Decoupled Architecture Diagram</b></summary>

```
   [NewsAPI.org]
         │ (Automated 30-min polling via Spring Scheduler)
         ▼
   [News Ingestion Service :8081]
         │ (existsByUrl duplicate filtering)
         ▼
   [PostgreSQL Database (Neon Serverless Cloud)]
         ▲
         │ (Reads verified articles)
   [News Delivery Service :8080]
   ├── Spring Security 6 (Stateless JWT RBAC)
   ├── Spring AI + DeepSeek LLM (Summarization)
   └── Swagger UI / OpenAPI 3
         ▲
         │ (RESTful Endpoints)
   [Client Applications / Web Consumers]
```
</details>

---

#### 3. 💳 [ExpenseFlow — Personal Finance Management REST API](https://github.com/priyagupta35/ExpenseFlow)
> **Stateless Multi-Tenant Financial Analytics & Ledger Engine**  
> `Java 17` • `Spring Boot 3.3.5` • `Spring Security 6` • `JWT` • `PostgreSQL (Neon)` • `HikariCP` • `Docker` • `Render`

[![Live API](https://img.shields.io/badge/Live_API-Online-success?style=flat-square&logo=render)](https://expenseflow-1-n72u.onrender.com)
[![Swagger UI Docs](https://img.shields.io/badge/Interactive_Docs-Swagger_UI-85EA2D?style=flat-square&logo=swagger&logoColor=black)](https://expenseflow-1-n72u.onrender.com/swagger-ui/index.html)
[![Docker Multi-Stage](https://img.shields.io/badge/Docker-Multi--Stage_Build-2496ED?style=flat-square&logo=docker&logoColor=white)](https://github.com/priyagupta35/ExpenseFlow)

* **Stateless Security Architecture:** Implemented token-based authentication via JJWT with BCrypt password hashing, enforcing multi-tenant data isolation through `@AuthenticationPrincipal`.
* **Aggregations & Analytics:** Real-time financial calculations (monthly balance, category spending distributions, date-filtered ledgers) optimized via Spring Data JPA custom repository queries.
* **Connection Pool Optimization:** Configured HikariCP connection pooling parameters (`maximumPoolSize`, `idleTimeout`, `maxLifetime`) to handle serverless Neon PostgreSQL cold-start idle drops.
* **Production Observability:** Centralized exception handling via `@RestControllerAdvice` emitting standardized RFC 7807 `ProblemDetails` payloads.

---

#### 4. 🧠 [Java Data Structures & Algorithms Practice](https://github.com/priyagupta35/java-dsa-practice)
> **Problem Solving, Algorithmic Efficiency & Clean Object-Oriented Design**  
> `Java 17` • `Data Structures` • `OOP Design Patterns` • `Complexity Analysis`

* **Linear Data Structures:** Dynamic Arrays, Singly/Doubly Linked Lists, Stacks, Queues, Two Pointers, Sliding Window.
* **Non-Linear Structures:** Binary Search Trees (BST), Heaps / Priority Queues, Graph traversals (BFS & DFS).
* **Algorithmic Patterns:** Divide & Conquer, Binary Search optimizations, Recursion & Backtracking fundamentals.

---

### 📊 GitHub Activity & Telemetry

<div align="center">
  <table border="0">
    <tr>
      <td align="center">
        <img src="https://github-readme-stats.vercel.app/api?username=priyagupta35&show_icons=true&theme=tokyonight&hide_border=true&include_all_commits=true&count_private=true" alt="GitHub Stats" height="165" />
      </td>
      <td align="center">
        <img src="https://github-readme-streak-stats.herokuapp.com/?user=priyagupta35&theme=tokyonight&hide_border=true" alt="GitHub Streak" height="165" />
      </td>
    </tr>
    <tr>
      <td colspan="2" align="center">
        <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=priyagupta35&layout=compact&theme=tokyonight&hide_border=true&langs_count=6" alt="Top Languages" width="380" />
      </td>
    </tr>
  </table>
</div>

---

### 🤝 Connect & Inquire

<div align="center">

I am actively interviewing for **Software Development Engineer (SDE-1) / Backend Developer** opportunities.

[![Connect on LinkedIn](https://img.shields.io/badge/Connect%20on-LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/priya-gupta35)
[![Send an Email](https://img.shields.io/badge/Drop%20an-Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:priyaguptaindia56@gmail.com)

<br/>
<sub>Designed & engineered with precision by <b>Priya Gupta</b> • 2026</sub>

</div>
