<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F172A,50:1D4ED8,100:38BDF8&height=190&section=header&text=Chinta%20Dinesh%20Reddy&fontSize=38&fontColor=FFFFFF&fontAlignY=36&desc=Software%20Engineering%20%7C%20Platform%20Architecture%20%7C%20AI%20Tooling&descAlignY=59&descSize=15" alt="Chinta Dinesh Reddy — Software Engineer" width="100%" />

<a href="https://github.com/Cdineshreddy12"><img src="https://img.shields.io/badge/GitHub-Cdineshreddy12-111827?style=for-the-badge&logo=github&logoColor=white" alt="GitHub profile" /></a>
<a href="https://www.linkedin.com/in/c-dinesh-reddy/"><img src="https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn profile" /></a>
<a href="https://alumni.rguktap.com/"><img src="https://img.shields.io/badge/Live_Project-Alumni_Portal-0F766E?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Alumni Portal" /></a>
Building multi-tenant SaaS, reliable cloud infrastructure, distributed workflows, and AI-powered developer tools.
</div>

👋 About Me
I'm a Computer Science student at RGUKT Srikakulam and System Architect at Zopkit. I work across product engineering, multi-tenant SaaS architecture, platform engineering, distributed workflows, database performance, observability, and AI-native developer tooling.
<table>
<tr>
<td width="50%" valign="top">


🏗️ SaaS Architecture

Multi-tenancy · Shared identity · SSO · Permissions

🔄 Distributed Systems

Temporal · Saga compensation · Retries · Recovery
</td>
<td width="50%" valign="top">


☁️ Platform Engineering

AWS · Terraform · Docker · CI/CD

🧠 AI & Data Engineering

MCP · Context retrieval · Query optimization
</td>
</tr>
</table>

📊 Engineering Impact
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

🔓 Open Source

Correctness fixes across the Node.js data layer — the libraries most Node backends stand on. All PRs currently in review (Nov 2026); every claim links to the public thread.

<table>
<tr>
<td width="50%" valign="top">

🐘 node-postgres · ~30M downloads/week

**Found and fixed a statement-cache poisoning bug** — a named prepared statement whose parameter fails to serialize leaves client and server permanently disagreeing, so every later use of that name fails with SQLSTATE 26000 for the life of the connection. Discovered by reading the bind-error path, not from a report.
- [Issue #3867](https://github.com/brianc/node-postgres/issues/3867) · [PR #3868](https://github.com/brianc/node-postgres/pull/3868) — regression-tested, green on the 12-job CI matrix
- Also: [verified review](https://github.com/brianc/node-postgres/pull/3854#issuecomment-7002922481) of the `pool.end()` shutdown-drain fix — confirmed it cures the hang, caught that it can open new connections after `end()`
</td>
<td width="50%" valign="top">

🟥 node-redis · official Redis client

**Two correctness fixes in one day**, both on maintainer-confirmed issues:
- [PR #3641](https://github.com/redis/node-redis/pull/3641) — RESP3 client-side cache served stale cross-database reads after `SELECT`; also fixed an in-flight-load race found in review (a load racing the cache clear could re-insert stale data)
- [PR #3642](https://github.com/redis/node-redis/pull/3642) — during cluster slot migration, a timed-out node's late replies resolved the *wrong commands* (RESP has no request IDs); the fix drops the desynced connection instead of reusing it
</td>
</tr>
<tr>
<td width="50%" valign="top">

⚡ @fastify/rate-limit · ~1M downloads/week

**Added node-redis support** — requested since May 2024. Shares the plugin's atomic Lua counter, addressed via locally computed SHA1 + `EVALSHA` with a one-time `NOSCRIPT` fallback, so there's zero setup for users and no new dependency. Designed around each review objection that stalled the previous attempt.
- [PR #475](https://github.com/fastify/fastify-rate-limit/pull/475) — verified with two servers enforcing one shared limit; 100% branch coverage
</td>
<td width="50%" valign="top">

🗜️ @fastify/compress · ~700K downloads/week

**Fixed route options silently destroying global config** — options were merged after default-filling, so route defaults overwrote explicit global choices. Moved the merge before processing: raw over raw, processed once.
- [PR #448](https://github.com/fastify/fastify-compress/pull/448) — regression tests written first, proven failing on main

<sub>The common thread across all of these: find where two copies of state can diverge when something throws — client cache vs. server, reply queue vs. wire, processed config vs. intent.</sub>
</td>
</tr>
</table>

🚀 Selected Engineering Work
<table>
<tr>
<td width="50%" valign="top">

🏗️ Multi-Tenant SaaS Platform
Zopkit · Platform Architecture

Shared capabilities for a suite of business applications.
- Tenant-aware identity, SSO, metadata, and permissions
- Application-to-application workflows with Temporal
- Saga compensation, retries, and failure recovery
Multi-tenancy Temporal Saga SSO
</td>
<td width="50%" valign="top">

⚡ Cloud & Platform Engineering
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

🎯 Customizable CRM
Configurable business workflows
- Configurable modules, fields, pipelines, dashboards, and integrations
- Leads, accounts, opportunities, and tickets
- Database query optimization and performance tuning
- Used by multiple companies, including an enterprise client with 50 employees
React Node.js Fastify PostgreSQL Drizzle ORM
</td>
<td width="50%" valign="top">

🤖 AI-Native Bug Resolution
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

🎓 RGUKT Alumni Portal
University community · 30,000+ people

Built a live portal serving the RGUKT university community.

Visit the Alumni Portal →
</td>
<td width="50%" valign="top">

🎪 Techniverse College Fest
Event platform · Approximately 5,000 users
- Online payment flows
- QR-code-based entry
- Participant-facing event experience
</td>
</tr>
</table>

🧠 AI-Assisted Engineering
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

🧰 Tech Stack
Languages & Frontend
<div>
<img src="https://skillicons.dev/icons?i=html,css,js,ts,react,vite,tailwind,redux,nextjs" alt="HTML, CSS, JavaScript, TypeScript, React, Vite, Tailwind CSS, Redux, Next.js" />
</div>

Backend & API Development
<div>
<img src="https://skillicons.dev/icons?i=nodejs,express,python,fastapi" alt="Node.js, Express, Python, FastAPI" />
</div>

<p><strong>Also:</strong> Fastify · REST APIs · OAuth 2.0 · JWT · Kinde · Mongoose · Drizzle ORM</p>

Databases, Caching & Search
<div>
<img src="https://skillicons.dev/icons?i=mongodb,postgres,redis,elasticsearch,supabase" alt="MongoDB, PostgreSQL, Redis, Elasticsearch, Supabase" />
</div>

<p><strong>Also:</strong> Redis Streams · Qdrant · Algolia · Indexing · Query optimization · Pagination</p>

Cloud, Infrastructure & Delivery
<div>
<img src="https://skillicons.dev/icons?i=aws,docker,terraform,kubernetes,nginx,githubactions,linux,bash,git,github" alt="AWS, Docker, Terraform, Kubernetes, Nginx, GitHub Actions, Linux, Bash, Git, GitHub" />
</div>

<p><strong>AWS services:</strong> EC2 · S3 · Route 53 · CloudFront · ALB · ACM · SES · CloudWatch · MSK/Kafka · SNS/SQS · Cognito</p>

<p><strong>Also:</strong> PM2 · Docker Compose · Multi-stage builds · CI/CD · Infrastructure as Code</p>

Distributed Systems & Observability
<div>
<img src="https://img.shields.io/badge/Temporal-Durable_Workflows-111827?style=flat-square" alt="Temporal" />
<img src="https://img.shields.io/badge/RabbitMQ-Messaging-FF6600?style=flat-square&logo=rabbitmq&logoColor=white" alt="RabbitMQ" />
<img src="https://img.shields.io/badge/Kafka-Event_Streaming-231F20?style=flat-square&logo=apachekafka&logoColor=white" alt="Apache Kafka" />
<img src="https://img.shields.io/badge/Sentry-Observability-362D59?style=flat-square&logo=sentry&logoColor=white" alt="Sentry" />
</div>

<p>Temporal · Saga pattern · Redis Streams · RabbitMQ · Kafka · Distributed tracing · Structured logs · Production metrics</p>

AI, LLMs & Developer Tooling
<div>
<img src="https://img.shields.io/badge/Claude_Code-AI_Development-D97757?style=flat-square" alt="Claude Code" />
<img src="https://img.shields.io/badge/Cursor-AI_Editor-111827?style=flat-square" alt="Cursor" />
<img src="https://img.shields.io/badge/MCP-Model_Context_Protocol-2563EB?style=flat-square" alt="MCP" />
<img src="https://img.shields.io/badge/LangChain-LLM_Applications-1C3C3C?style=flat-square" alt="LangChain" />
<img src="https://img.shields.io/badge/Qdrant-Vector_Search-DC244C?style=flat-square" alt="Qdrant" />
</div>

<p>Gemini API · OpenAI embeddings · Qdrant vector search · MCP servers · AI-assisted debugging and code retrieval</p>

📈 GitHub Activity
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

How to read these cards
- GitHub Stats: GitHub activity the card service can retrieve; visibility, API limits, and caching can affect the result.
- Top Languages: estimates the language mix of repositories visible to the service. It is not a measure of skill or time spent coding. A notebook-heavy repository can make Jupyter Notebook appear unusually high.
- Contribution streak and calendar: reflect GitHub-recognized contributions. GitHub may take time to update activity; commits generally need the correct email and to land on a repository's default branch or gh-pages to count in the profile calendar.
- Source of truth: your GitHub profile and contribution calendar. The README does not hardcode changing counts.
🎯 Current Focus
<table>
<tr>
<td align="center" width="33%">

🔄 Workflow Resilience

<sub>Temporal · Saga recovery</sub>
</td>
<td align="center" width="33%">


☁️ Cloud Reliability

<sub>AWS · Terraform · CI/CD</sub>
</td>
<td align="center" width="33%">


🧠 AI Developer Tools

<sub>MCP · Context retrieval</sub>
</td>
</tr>
</table>

🤝 Let's Connect
<div align="center">

<a href="https://www.linkedin.com/in/c-dinesh-reddy/"><img src="https://img.shields.io/badge/LinkedIn-Let's_connect-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
<a href="https://github.com/Cdineshreddy12"><img src="https://img.shields.io/badge/GitHub-Follow_my_work-111827?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" /></a>
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:38BDF8,50:1D4ED8,100:0F172A&height=100&section=footer" alt="" width="100%" />

</div>
