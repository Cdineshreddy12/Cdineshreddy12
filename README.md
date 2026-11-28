<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F172A,50:1D4ED8,100:38BDF8&height=190&section=header&text=Chinta%20Dinesh%20Reddy&fontSize=38&fontColor=FFFFFF&fontAlignY=36&desc=System%20Architect%20%40%20Zopkit%20%C2%B7%20Open%20Source%20Contributor%20%C2%B7%20Cloud%20%C2%B7%20DevOps%20%C2%B7%20AI%20Tooling&descAlignY=58&descSize=14" alt="Chinta Dinesh Reddy — Software Engineer" width="100%" />

<a href="https://github.com/Cdineshreddy12"><img src="https://img.shields.io/badge/GitHub-Cdineshreddy12-111827?style=for-the-badge&logo=github&logoColor=white" alt="GitHub profile" /></a>
<a href="https://www.linkedin.com/in/c-dinesh-reddy/"><img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn profile" /></a>
<a href="https://alumni.rguktap.com/"><img src="https://img.shields.io/badge/Live_Project-Alumni_Portal-0F766E?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Alumni Portal" /></a>

<p>
<a href="#open-source"><img src="https://img.shields.io/badge/Open_Source_Contributor-node--redis%20·%20node--postgres%20·%20Fastify-DC382D?style=for-the-badge&logo=opensourceinitiative&logoColor=white" alt="Open Source Contributor" /></a>
<a href="https://github.com/redis/node-redis/pulls?q=is%3Apr+author%3ACdineshreddy12+is%3Amerged"><img src="https://img.shields.io/badge/node--redis-5_PRs_merged-2EA043?style=for-the-badge&logo=redis&logoColor=white" alt="node-redis PRs merged" /></a>
</p>

<p><em>Building multi-tenant SaaS, reliable cloud infrastructure, distributed workflows, and AI-powered developer tools.</em></p>
</div>

## About Me

System Architect at **Zopkit**, where I design and operate a multi-tenant B2B SaaS suite — seven applications sharing one identity platform, in production for paying customers. I own the AWS platform and production deploys, lead the developer team's engineering alongside the CEO, and am moving our cross-application workflows onto Temporal.

**Open source contributor** to the infrastructure my stack runs on — **node-redis, node-postgres, and the Fastify ecosystem** — with six fixes merged upstream — five into node-redis (the official Redis client) and one into `@fastify/compress` — three more in review. One of the node-redis merges is a cluster fix the maintainer assigned to me from his own issue. The work is mostly correctness fixes in error paths and protocol-level state handling; details in [Open Source](#open-source) below. Computer Science undergraduate at RGUKT Srikakulam, class of 2027.

**Where I spend my time**

- **Multi-tenant architecture** — one identity platform (SSO, row-level isolation, per-app permissions) serving seven production applications
- **Distributed systems** — cross-application workflows on Temporal, with saga compensation and recovery designed before the happy path
- **Correctness in infrastructure** — finding where two copies of state diverge when something throws: client caches vs. servers, reply queues vs. the wire ([open source](#open-source) below)
- **Platform engineering** — AWS + Terraform + CI/CD, measured in outcomes: deploys 31% faster, CI critical path 66% shorter, images 44% smaller
- **AI-native tooling** — MCP servers with permission-aware agent authorization and revocable keys, used daily by our developer team

## Engineering Impact

<div align="center">
<table>
<tr>
<td align="center" width="33%">

<h1>31%</h1>
<strong>Faster deployments</strong><br/>
<sub>8m 22s → 5m 44s</sub>

</td>
<td align="center" width="33%">

<h1>66%</h1>
<strong>Shorter CI critical path</strong><br/>
<sub>13m 54s → 4m 41s</sub>

</td>
<td align="center" width="33%">

<h1>44%</h1>
<strong>Smaller container images</strong><br/>
<sub>405 MB → 225 MB</sub>

</td>
</tr>
</table>
</div>

## Open Source

Correctness fixes in the Node.js data layer — the libraries most Node backends stand on. **Six merged** (five into node-redis, the official Redis client; one into `@fastify/compress`, merged by Fastify's co-creator), **three in review**. One of them is a cluster fix the maintainer **assigned to me from his own issue**, and then merged. Alongside the code I review other contributors' PRs and work the issue backlog: **17 verified triage verdicts, 15 of which the maintainer closed on my word**. Every claim below links to the public thread, including the ones that did not land.

<div align="center">
  <a href="https://github.com/redis/node-redis/pulls?q=is%3Apr+author%3ACdineshreddy12"><img src="https://img.shields.io/badge/node--redis-official_client-DC382D?style=for-the-badge&logo=redis&logoColor=white" alt="node-redis" /></a>
  <a href="https://github.com/brianc/node-postgres/pull/3868"><img src="https://img.shields.io/badge/node--postgres-~30M%2Fweek-336791?style=for-the-badge&logo=postgresql&logoColor=white" alt="node-postgres" /></a>
  <a href="https://github.com/fastify/fastify-compress/pull/448"><img src="https://img.shields.io/badge/Fastify-plugins-202020?style=for-the-badge&logo=fastify&logoColor=white" alt="Fastify" /></a>
</div>

### Merged

| Project | What | Link |
| --- | --- | --- |
| **node-redis** | RESP3 client-side cache served stale cross-database reads after `SELECT` — fixed per the maintainer's design, plus an in-flight-load race found in review. | [#3641](https://github.com/redis/node-redis/pull/3641) |
| **node-redis** | Cluster slot migration routed a timed-out node's late replies to the wrong commands — the fix drops the desynced connection instead of reusing it. | [#3642](https://github.com/redis/node-redis/pull/3642) |
| **node-redis** | The empty-string key routed to a random node instead of its slot. | [#3660](https://github.com/redis/node-redis/pull/3660) |
| **node-redis** | A sentinel test flake I filed, then fixed: the teardown raced a reentrant reopen, so the assertion ran before `isOpen` flipped. | [#3650](https://github.com/redis/node-redis/issues/3650) · [#3651](https://github.com/redis/node-redis/pull/3651) |
| **node-redis** | **Assigned to me by the maintainer**, from his own issue and his design. Cluster `connect()` hung forever while one master was unreachable — one down node should cost only its own shard. `connect()` now installs the slot map without awaiting the node connects, and every wait for a connecting node is bounded by the cluster's command timeout. Five rounds of review, then *"Thanks, LGTM."* | [#3592](https://github.com/redis/node-redis/issues/3592) · [#3652](https://github.com/redis/node-redis/pull/3652) |
| **@fastify/compress** | Route options silently destroyed global config — the merge ran after default-filling, so route defaults overwrote explicit global choices. Eight other PRs had tried to close the issue since May; this is the one that landed. Merged by [@mcollina](https://github.com/mcollina). | [#448](https://github.com/fastify/fastify-compress/pull/448) |

### In review

| Project | What | Link |
| --- | --- | --- |
| **node-postgres** | Found and fixed statement-cache poisoning — a named prepared statement whose parameter fails to serialize breaks every later use of that name (SQLSTATE 26000) for the life of the connection. Found by reading the bind-error path; green on the full 12-job matrix. | [#3867](https://github.com/brianc/node-postgres/issues/3867) · [#3868](https://github.com/brianc/node-postgres/pull/3868) |
| **@fastify/compress** | ~1 in 993 binary responses ships a gzip header over an uncompressed body: the already-compressed check reads a two-byte signature that arbitrary binary data matches. Quantified by measuring the collision rate. **Approved.** | [#450](https://github.com/fastify/fastify-compress/pull/450) |
| **@fastify/rate-limit** | node-redis support with zero user setup — a shared atomic Lua counter addressed via `EVALSHA` with a one-time `NOSCRIPT` fallback. Open request since May 2024. | [#475](https://github.com/fastify/fastify-rate-limit/pull/475) |

### Review and triage

| Project | What | Link |
| --- | --- | --- |
| **node-redis** | **17 verified triage verdicts, 15 closed by the maintainer** — each reproduced against current master rather than guessed at, and thanked by name three times. | [verdicts](https://github.com/redis/node-redis/issues?q=is%3Aissue+commenter%3ACdineshreddy12) |
| **node-redis** | A fix I suggested in review shipped inside the maintainer's own PR, as its own commit. | [#3636](https://github.com/redis/node-redis/pull/3636) |
| **node-redis** | Caught a cache-coherence race in another contributor's serve-stale PR — the same race my merged #3641 fixed in `clear()`. | [#3495](https://github.com/redis/node-redis/pull/3495#pullrequestreview-5975037117) |
| **node-redis** | Reviewed a contributor's reconnect fix and flagged the overlap with my own assigned PR so the two could land in either order. | [#3656](https://github.com/redis/node-redis/pull/3656) |
| **node-postgres** | Verified review of the `pool.end()` shutdown-drain fix — confirmed it cures the hang, and caught that the drain path can open new connections after `end()`. | [#3854](https://github.com/brianc/node-postgres/pull/3854#issuecomment-7002922481) |

### Closed without merging

Kept here because the reasoning is the point. A maintainer's "no" is as informative as a merge.

| Project | What | Link |
| --- | --- | --- |
| **@fastify/compress** | Proposed warning when request decompression is left at its implicit default. Declined: the module exists to decompress, so warning about it is the wrong shape. Matteo Collina's call, and a fair one. | [#449](https://github.com/fastify/fastify-compress/pull/449) |
| **node-redis** | A fix for the client/socket event-emitter split. Closed on process, not substance: I opened it before the maintainer had agreed the approach on the issue, which their contributing guidelines require. The issue is still open. | [#3680](https://github.com/redis/node-redis/issues/3680) · [#3684](https://github.com/redis/node-redis/pull/3684) |
| **node-redis** | Pipelined `EVALSHA` reuse. Declined on design grounds: an `EVALSHA` inside `MULTI..EXEC` cannot fall back on `NOSCRIPT`, so any cache gap risks a partly-applied transaction — a trade the maintainer judged not worth the saved bytes. He was right. | [#3647](https://github.com/redis/node-redis/pull/3647) |
| **node-redis** | A client-side-cache race across `SELECT`. Real, but closed as not observed in a real application. | [#3661](https://github.com/redis/node-redis/pull/3661) |
| **nodejs/docker-node** | `npm install` fails for every non-root container user. Verified across root, UID 1002, read-only root filesystem, and yarn; closed for want of a team sponsor rather than on the code. | [#2702](https://github.com/nodejs/docker-node/pull/2702) |

<sub>The common thread: find where two copies of state can diverge when something throws — client cache vs. server, reply queue vs. wire, processed config vs. intent.</sub>

## Selected Engineering Work
<table>
<tr>
<td width="50%" valign="top">

**Multi-Tenant SaaS Platform**
Zopkit · Platform Architecture

Shared capabilities for a suite of business applications.
- Tenant-aware identity, SSO, metadata, and permissions
- Application-to-application workflows with Temporal
- Saga compensation, retries, and failure recovery
Multi-tenancy Temporal Saga SSO
</td>
<td width="50%" valign="top">

**Cloud & Platform Engineering**
Delivery · Infrastructure · Reliability
- 31% faster deployments
- 66% shorter CI critical path
- 44% smaller container images
- AWS infrastructure, Terraform drift investigation, Docker, GitHub Actions, and observability
AWS Terraform Docker CI/CD Sentry
</td>
</tr>
<tr>
<td width="50%" valign="top">

**Customizable CRM**
Configurable business workflows
- Configurable modules, fields, pipelines, dashboards, and integrations
- Leads, accounts, opportunities, and tickets
- Database query optimization and performance tuning
- Used by multiple companies, including an enterprise client with 50 employees
React Node.js Fastify PostgreSQL Drizzle ORM
</td>
<td width="50%" valign="top">

**AI-Native Bug Resolution**
Developer productivity · MCP
- MCP-based retrieval for relevant bug and code context
- AI-assisted investigation using Claude Code and Cursor
- Permission-aware tooling and revocable API keys
- Designed to reduce context switching across a multi-application codebase
MCP Claude Code Cursor LangChain Qdrant
</td>
</tr>
<tr>
<td width="50%" valign="top">

**RGUKT Alumni Portal**
University community · 30,000+ people

Built a live portal serving the RGUKT university community.

Visit the Alumni Portal →
</td>
<td width="50%" valign="top">

**Techniverse College Fest**
Event platform · Approximately 5,000 users
- Online payment flows
- QR-code-based entry
- Participant-facing event experience
</td>
</tr>
</table>

## AI-Assisted Engineering
<div align="center">

<img src="https://img.shields.io/badge/Claude_Code-AI_Coding_Assistant-D97757?style=for-the-badge&logo=anthropic&logoColor=white" alt="Claude Code" />
<img src="https://img.shields.io/badge/Cursor-AI_Editor-111827?style=for-the-badge&logo=cursor&logoColor=white" alt="Cursor" />
<img src="https://img.shields.io/badge/MCP-Tool_Integration-2563EB?style=for-the-badge" alt="Model Context Protocol" />

</div>

<table>
<tr><td><strong>Codebase understanding</strong></td><td>Trace request flows, dependencies, and service boundaries.</td></tr>
<tr><td><strong>Debugging</strong></td><td>Correlate application logs, traces, CI failures, and infrastructure changes.</td></tr>
<tr><td><strong>Implementation</strong></td><td>Assist with refactoring, test scaffolding, and repetitive engineering tasks.</td></tr>
<tr><td><strong>Context retrieval</strong></td><td>Surface relevant code and bug information through MCP-based tooling.</td></tr>
<tr><td><strong>Verification</strong></td><td>Validate changes with tests, review, staging, and production monitoring.</td></tr>
</table>

AI can accelerate engineering; evidence, testing, review, and observability establish correctness.

## Tech Stack
### Languages & Frontend
<div>
<img src="https://skillicons.dev/icons?i=html,css,js,ts,react,vite,tailwind,redux,nextjs" alt="HTML, CSS, JavaScript, TypeScript, React, Vite, Tailwind CSS, Redux, Next.js" />
</div>

### Backend & API Development
<div>
<img src="https://skillicons.dev/icons?i=nodejs,express,python,fastapi" alt="Node.js, Express, Python, FastAPI" />
</div>

<p><strong>Also:</strong> Fastify · REST APIs · OAuth 2.0 · JWT · Kinde · Mongoose · Drizzle ORM</p>

### Databases, Caching & Search
<div>
<img src="https://skillicons.dev/icons?i=mongodb,postgres,redis,elasticsearch,supabase" alt="MongoDB, PostgreSQL, Redis, Elasticsearch, Supabase" />
</div>

<p><strong>Also:</strong> Redis Streams · Qdrant · Algolia · Indexing · Query optimization · Pagination</p>

### Cloud, Infrastructure & Delivery
<div>
<img src="https://skillicons.dev/icons?i=aws,docker,terraform,kubernetes,nginx,githubactions,linux,bash,git,github" alt="AWS, Docker, Terraform, Kubernetes, Nginx, GitHub Actions, Linux, Bash, Git, GitHub" />
</div>

<p><strong>AWS services:</strong> EC2 · S3 · Route 53 · CloudFront · ALB · ACM · SES · CloudWatch · MSK/Kafka · SNS/SQS · Cognito</p>

<p><strong>Also:</strong> PM2 · Docker Compose · Multi-stage builds · CI/CD · Infrastructure as Code</p>

### Distributed Systems & Observability
<div>
<img src="https://img.shields.io/badge/Temporal-Durable_Workflows-111827?style=flat-square" alt="Temporal" />
<img src="https://img.shields.io/badge/RabbitMQ-Messaging-FF6600?style=flat-square&logo=rabbitmq&logoColor=white" alt="RabbitMQ" />
<img src="https://img.shields.io/badge/Kafka-Event_Streaming-231F20?style=flat-square&logo=apachekafka&logoColor=white" alt="Apache Kafka" />
<img src="https://img.shields.io/badge/Sentry-Observability-362D59?style=flat-square&logo=sentry&logoColor=white" alt="Sentry" />
</div>

<p>Temporal · Saga pattern · Redis Streams · RabbitMQ · Kafka · Distributed tracing · Structured logs · Production metrics</p>

### AI, LLMs & Developer Tooling
<div>
<img src="https://img.shields.io/badge/Claude_Code-AI_Development-D97757?style=flat-square" alt="Claude Code" />
<img src="https://img.shields.io/badge/Cursor-AI_Editor-111827?style=flat-square" alt="Cursor" />
<img src="https://img.shields.io/badge/MCP-Model_Context_Protocol-2563EB?style=flat-square" alt="MCP" />
<img src="https://img.shields.io/badge/LangChain-LLM_Applications-1C3C3C?style=flat-square" alt="LangChain" />
<img src="https://img.shields.io/badge/Qdrant-Vector_Search-DC244C?style=flat-square" alt="Qdrant" />
</div>

<p>Gemini API · OpenAI embeddings · Qdrant vector search · MCP servers · AI-assisted debugging and code retrieval</p>

## GitHub Activity
<div align="center">

<a href="https://github.com/Cdineshreddy12">
<img src="https://github-readme-stats.vercel.app/api?username=Cdineshreddy12&show_icons=true&hide_border=true&theme=tokyonight&rank_icon=github&include_all_commits=true" height="170" alt="Public GitHub statistics" />
</a>
<a href="https://github.com/Cdineshreddy12">
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Cdineshreddy12&layout=compact&hide_border=true&theme=tokyonight&langs_count=8" height="170" alt="Languages detected in public repositories" />
</a>


<img src="https://streak-stats.demolab.com?user=Cdineshreddy12&theme=tokyonight&hide_border=true" alt="GitHub contribution streak" width="80%" />


<img src="https://ghchart.rshah.org/409ba5/Cdineshreddy12" alt="GitHub contribution calendar" width="100%" />

</div>

**How to read these cards**
- GitHub Stats: GitHub activity the card service can retrieve; visibility, API limits, and caching can affect the result.
- Top Languages: estimates the language mix of repositories visible to the service. It is not a measure of skill or time spent coding. A notebook-heavy repository can make Jupyter Notebook appear unusually high.
- Contribution streak and calendar: reflect GitHub-recognized contributions. GitHub may take time to update activity; commits generally need the correct email and to land on a repository's default branch or gh-pages to count in the profile calendar.
- Source of truth: your GitHub profile and contribution calendar. The README does not hardcode changing counts.
## Current Focus

<div align="center">
<table>
<tr>
<td align="center" width="33%">

**Workflow Resilience**

<sub>Temporal · Saga recovery</sub>
</td>
<td align="center" width="33%">


**Cloud Reliability**

<sub>AWS · Terraform · CI/CD</sub>
</td>
<td align="center" width="33%">


**AI Developer Tools**

<sub>MCP · Context retrieval</sub>
</td>
</tr>
</table>
</div>

## Let's Connect
<div align="center">

<a href="https://www.linkedin.com/in/c-dinesh-reddy/"><img src="https://img.shields.io/badge/LinkedIn-Let's_connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
<a href="https://github.com/Cdineshreddy12"><img src="https://img.shields.io/badge/GitHub-Follow_my_work-111827?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" /></a>
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:38BDF8,50:1D4ED8,100:0F172A&height=100&section=footer" alt="" width="100%" />

</div>
