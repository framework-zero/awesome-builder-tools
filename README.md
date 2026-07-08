# awesome-builder-tools
Open source tools for going from side project to company — CRMs, billing, analytics, ad tools, marketplace frameworks, agentic orchestration, community platforms, agent-native project management, deep research/RAG, agent payments, legal & governance infra, and self-hosting. Everything a builder needs to find customers, ship product, run an AI-staffed company, and not get stuck on undifferentiated infrastructure.

---

## Table of Contents

- [CRM & Customer Management](#crm--customer-management)
- [SaaS Infrastructure](#saas-infrastructure)
- [Billing & Monetization](#billing--monetization)
- [Agentic Orchestration](#agentic-orchestration)
- [AI Company Builders & Digital-Twin Platforms](#ai-company-builders--digital-twin-platforms)
- [Project & Task Management (Agent-Native)](#project--task-management-agent-native)
- [Deep Research & RAG / Context Engines](#deep-research--rag--context-engines)
- [Agent Payments & Micropayments (x402)](#agent-payments--micropayments-x402)
- [Legal, DAO & Governance Infra](#legal-dao--governance-infra)
- [Product Analytics & Session Replay](#product-analytics--session-replay)
- [Advertising & Growth](#advertising--growth)
- [Marketplace & Commerce Frameworks](#marketplace--commerce-frameworks)
- [Community Platforms](#community-platforms)
- [Scheduling & Coordination](#scheduling--coordination)
- [Workflow Automation & No-Code](#workflow-automation--no-code)
- [Data Infrastructure](#data-infrastructure)
- [Legal & Document Automation](#legal--document-automation)
- [Auth & Identity](#auth--identity)
- [Self-Hosting & Deployment](#self-hosting--deployment)
- [Context Engineering & Knowledge](#context-engineering--knowledge)
- [Examples & Case Studies — Companies People Have Actually Built](#examples--case-studies--companies-people-have-actually-built)

---

## CRM & Customer Management

| Project | Description | Stars |
|---------|-------------|-------|
| [Twenty](https://github.com/twentyhq/twenty) | Modern open source CRM, AI-native. Ships an official first-party MCP server as of v2.0 (April 2026) — agents can read/write CRM data in natural language. AGPL-3.0 core + carved-out commercial "Enterprise" files. | 52k+ (2026-07) |
| [Odoo](https://github.com/odoo/odoo) | Full ERP + CRM suite — sales, invoicing, inventory, project management. Massive module ecosystem. | 52k+ |
| [Erxes](https://github.com/erxes/erxes) | Experience management platform — CRM, marketing, customer service, sales pipelines. | 4k+ |
| [Huly](https://github.com/hcengineering/huly-platform) | All-in-one project management, CRM, HR — Linear/Notion/Slack alternative. Includes built-in AI assistant "Hulia" w/ real-time transcription. | 24k+ |
| [Macro](https://github.com/macro-inc/macro) | Unified interface for email, messages, tasks, calls, CRM — linked with shared AI memory. | 379 |

> **From your stars**: Macro, Odoo
>
> **Community MCP servers for Twenty** (use with care — one unofficial author withdrew their own server and warned against unofficial MCP servers touching CRM data): [`twenty-mcp`](https://pypi.org/project/twenty-mcp/) (PyPI, MIT), [`KonstiDoll/twenty-crm-mcp-server`](https://github.com/KonstiDoll/twenty-crm-mcp-server) (MIT, GraphQL-native), [`High-Impact-Athletes/hia-twenty-mcp`](https://github.com/High-Impact-Athletes/hia-twenty-mcp) (Apache-2.0, schema-driven — introspects Twenty's metadata API at runtime so it never needs updates when you add fields/objects). Prefer the official MCP for anything touching real customer data.

## SaaS Infrastructure

| Project | Description | Stars |
|---------|-------------|-------|
| [Open SaaS](https://github.com/wasp-lang/open-saas) | 100% free, MIT-licensed full-stack SaaS boilerplate (React/Node/Prisma via Wasp). AI-ready — ships `AGENTS.md` + a Claude Code plugin. Auth, Stripe/Polar.sh/Lemon Squeezy payments, S3 uploads, admin dashboard, one-command deploy. | 14.8k+ |
| [Supabase](https://github.com/supabase/supabase) | Firebase alternative — Postgres database, auth, realtime, storage, edge functions. | 80k+ |
| [Appwrite](https://github.com/appwrite/appwrite) | Backend platform for web/mobile/Flutter — auth, databases, storage, functions, messaging. | 50k+ |
| [Infisical](https://github.com/Infisical/infisical) | Secret management platform — env variables, secret rotation, access control. | 20k+ |
| [Nango](https://github.com/NangoHQ/nango) | Product integrations platform — pre-built connectors to 300+ APIs (CRMs, payments, etc). | 7k+ |
| [Trigger.dev](https://github.com/triggerdotdev/trigger.dev) | Background jobs and workflows for serverless — durable execution, scheduling. | 10k+ |
| [Pulumi](https://github.com/pulumi/pulumi) | Infrastructure as code in real programming languages (TypeScript, Python, Go). | 25k+ |
| [Coolify](https://github.com/coollabsio/coolify) | Self-hostable Heroku/Netlify/Vercel alternative — deploy anything with a single click. | 40k+ |

> **From your stars**: Pulumi

## Billing & Monetization

| Project | Description | Stars |
|---------|-------------|-------|
| [Lago](https://github.com/getlago/lago) | Open source metering and usage-based billing — Stripe billing alternative. | 10k+ |
| [Kill Bill](https://github.com/killbill/killbill) | Subscription billing and payments platform — handles complex billing scenarios. | 5k+ |
| [Polar](https://github.com/polarsource/polar) | Monetization platform for developers — subscriptions, donations, pay-what-you-want. | 3k+ |
| [Stripe React](https://github.com/stripe/react-stripe-js) | Official React components for Stripe Elements — drop-in payment UI. | 2k+ |
| [Dub](https://github.com/dubinc/dub) | Link management with built-in analytics, conversion tracking, referral programs. | 25k+ |

> **From your stars**: Stripe React
>
> See also [Agent Payments & Micropayments (x402)](#agent-payments--micropayments-x402) below for billing infrastructure specifically built for *agent-to-agent* / *agent-to-API* transactions rather than human checkout flows.

## Agentic Orchestration

| Project | Description | Stars |
|---------|-------------|-------|
| [LangGraph](https://github.com/langchain-ai/langgraph) | Build resilient, stateful multi-agent workflows as graphs. The most production-proven framework in 2026 — ~400 production deployments (Cisco, Uber, LinkedIn, BlackRock, JPMorgan), 34.5M monthly downloads. Steeper learning curve; pays back at production scale. | 24.8k+ |
| [CrewAI](https://github.com/crewAIInc/crewAI) | Framework for orchestrating role-playing autonomous AI agents. Fastest path to a working prototype (2–4 hrs). MIT. **Caveat:** telemetry collection reportedly can't be easily disabled — a real issue for regulated/privacy-sensitive builds; some report the role/goal/backstory abstraction gets "too rigid" once work doesn't decompose into team-shaped roles. | 50.8k+ |
| [Mastra](https://github.com/mastra-ai/mastra) | TypeScript-native agent framework, v1.0 shipped Jan 2026. YC-backed. 81 providers / 2,436+ models. Real production wins (Replit Agent 3, SoftBank). Worth prioritizing over CrewAI for JS/TS-stack builders — most of this list (Open SaaS, Twenty, Activepieces) is already Node/TS. | 23k+ |
| [open-multi-agent (OMA)](https://github.com/open-multi-agent/open-multi-agent) | Lean, fully permissive (3 core deps) TypeScript-native orchestrator. Goal-driven: a Coordinator builds the task DAG **at runtime** instead of requiring a hand-wired graph up front. MIT, launched 2026-04, actively growing. Worth a look as an alternative to Mastra given the license/telemetry profile. | 6.5k+ |
| [AutoGen](https://github.com/microsoft/autogen) | Multi-agent conversation framework. ⚠️ **Maintenance-only since Oct 2025** — Microsoft merged it into the unified Microsoft Agent Framework. Do not start new projects on it. | 54.6k+ |
| [Agno](https://github.com/agno-agi/agno) | Build, run, and manage agent platforms. | 41k+ |
| [Agent2Agent (A2A)](https://github.com/a2aproject/A2A) | Open protocol for communication between opaque agentic applications. | 24k+ |
| [Google ADK](https://github.com/google/adk-python) | Google's Agent Development Kit — build, evaluate, deploy AI agents. Reported gap: in-memory session state is lost on Cloud Run container restarts. | 20k+ |
| [Omnigent](https://github.com/omnigent-ai/omnigent) | Meta-harness for orchestrating Claude Code, Codex, Cursor, and custom agents. | 6k+ |
| [Agent Orchestrator](https://github.com/AgentWrapper/agent-orchestrator) | Plans tasks, spawns parallel coding agents, handles CI fixes and merge conflicts. | 8k+ |
| [dmux](https://github.com/standardagents/dmux) | Dev agent multiplexer for git worktrees and coding agents. | 1.6k+ |
| [Swarm Forge](https://github.com/unclebob/swarm-forge) | Simple tool for coordinating several AI agents. | 989 |
| [KaibanJS](https://github.com/kaiban-ai/KaibanJS) | JavaScript-native multi-agent framework with Kanban-inspired task management. | 1.4k+ |
| [LlamaIndex Deploy](https://github.com/run-llama/llama_deploy) | Deploy agentic workflows to production. | 2k+ |
| [Temporal](https://github.com/temporalio/temporal) | Durable workflow execution — retries, timeouts, versioning for long-running processes. | 14k+ |
| [Composio](https://github.com/ComposioHQ/composio) | Agent tooling platform — 250+ integrations for AI agents (GitHub, Slack, Notion, etc). | 15k+ |

> **From your stars**: CrewAI, LangGraph, AutoGen, Agno, A2A, Google ADK, Omnigent, Agent Orchestrator, dmux, Swarm Forge, KaibanJS, LlamaIndex Deploy
>
> **Community temperature check, 2026:** a 66-point Hacker News thread titled *"Sick of AI Agent Frameworks"* and a 51-upvote r/AI_Agents post arguing *"90% of agentic projects would be better off as simple prompt chains"* are both live in 2026 — a real signal to keep your own orchestration layer as thin as possible rather than assuming more framework is always better.

## AI Company Builders & Digital-Twin Platforms

**Direct precedents worth studying before building your own** — several projects in 2026 are already building close-to-direct versions of "let one person run/watch an AI-staffed company."

| Project | Description | Stars |
|---------|-------------|-------|
| [OneManCompany](https://github.com/1mancompany/OneManCompany) | Open-source **agentic operating system** — one command, no Docker/Python/config, and you get a full AI company in your browser (pixel-art office visualization). Runs *above* agent frameworks (Claude Code, OpenClaw, etc.), orchestrating a hierarchical AI team. Built-in **Talent Market** (community-verified AI-employee marketplace: HR searches, interviews, onboards), **1-on-1 coaching** that becomes permanent agent "work experience," **quarterly performance reviews** (probation/PIP/promotion/termination), structured **V1→V2→V3 iteration** per project, and **self-evolution** (repeated tasks auto-distill into reusable workflows). Apache-2.0. | 343+ |
| [KorroAi/mue-x](https://github.com/KorroAi/mue-x) | Self-evolving agent engine open-sourced by [KORRO](https://korro.me/) — "the world's first company run entirely by AI agents," a real, currently-running six-agent autonomous company (Node.js + SQLite + OpenRouter, no Kubernetes). `mue-x` reads its own Python source and rewrites it via validated AST mutations (6 mutation strategies), with kernel-integrity protection on core files and auto-rollback on failed import. MIT. Treat KORRO's own success claims with normal single-founder-case-study skepticism — but the open-sourced engine is real, inspectable code. | 62+ |
| [TeamDay-AI/business-tycoon](https://github.com/TeamDay-AI/business-tycoon) | Free, client-side, browser-based isometric "AI office simulator" game — hire agents, assign projects, grow a tech empire. No real agents, purely a UX/gamification reference (useful if you want a game-like "crafting" interface). MIT. | 11+ |
| [paperclipai/paperclip](https://github.com/paperclipai/paperclip) | The open-source app for managing agents at work — dashboard/interface layer for viewing and directing an agent workforce. | — |

## Project & Task Management (Agent-Native)

**2026 has produced a wave of PM tools built agent-first from the ground up** — most general "awesome AI agent" lists miss this category entirely.

| Project | Description | Stars |
|---------|-------------|-------|
| [Plane](https://github.com/makeplane/plane) | Mature open-source Jira/Linear/Monday/ClickUp alternative. AGPL-3.0, very active. The right base platform to build on. | 53.9k+ |
| [Plane Plus](https://github.com/eyriehq/plane-plus) | **AI-agent-first fork of Plane** — agent-ergonomic APIs, markdown-native pages, first-class epics with analytics endpoints (completion %, children-by-state rollups), plus a companion Python SDK + FastMCP server (`plane-plus-sdk-mcp`) so agents don't have to reason about Plane's polymorphic issue types. Drop-in compatible with upstream Plane's Docker/Kubernetes deployment. | — |
| [Poiesis](https://github.com/arthur2jolly/poiesis) | Production-oriented agile PM built natively for MCP 2.0. Full hierarchy (Projects→Epics→Stories→Tasks), dependency/blocker tracking, multi-tenancy, 36+ MCP tools, plus an MCP *prompt* resource for "agile workflow guide." | — |
| [markplane](https://github.com/zerowand01/markplane) | Markdown-first, git-native PM — no database; every task/epic/plan is a version-controlled file, auto-compressed into ~1000-token `.context/` summaries an AI can load without reading everything. Built-in MCP server. Apache-2.0. | 178+ |
| [PinkRoosterMcp](https://github.com/pinkroosterai/PinkRoosterMcp) | Purpose-built from scratch for AI agents (not a Jira/Linear wrapper). Automatic state cascades (task→phase→work-package→feature-request completion propagates), 16 Claude Code slash commands (`/pm-scaffold`, `/pm-implement`, `/pm-audit`, `/pm-triage`), built-in cross-session **project memories**. MIT. Very new — evaluate maturity before depending on it. | 1+ |
| [saga-mcp](https://github.com/spranab/saga-mcp) · [kanban-mcp](https://github.com/multidimensionalcats/kanban-mcp) · [zavora-ai/mcp-project](https://github.com/zavora-ai/mcp-project) · [openplan](https://github.com/vncsleal/openplan) | Smaller, single-purpose MCP-native trackers (SQLite-backed, 20–40 tools each). Useful reference implementations for a minimal agent-native PM data model, less as platforms to adopt wholesale. | small |

## Deep Research & RAG / Context Engines

| Project | Description | Stars |
|---------|-------------|-------|
| [GPT Researcher](https://github.com/assafelovic/gpt-researcher) | Actively maintained (pushed within days of any check), autonomous research agent that plans/searches/reads/writes long-form cited reports. Apache-2.0. Native MCP support. ~5 min / ~$0.40 per query on an o3-mini-class model. | 28.1k+ |
| [open_deep_research](https://github.com/langchain-ai/open_deep_research) (LangChain) | Simple, configurable, fully MIT-licensed deep-research agent across many model providers/search tools/MCP servers. **Note:** its oft-repeated "#6 on Deep Research Bench with RACE 0.4943 using GPT-5" claim conflates two separate results — the actual #6 ranking scored RACE 0.4344 on gpt-4.1-class models. Still a strong, actively maintained option. | 12k+ |
| [Onyx](https://github.com/onyx-dot-app/onyx) (formerly Danswer) | Self-hostable, permission-aware "ask questions of everything we know" platform — 50+ connectors, MCP support, YC W24. MIT core (Community Edition). Recommended as the default central-context-store pick given genuinely current release cadence (v4.3.0 shipped within a day of one check). | 30.8k+ |
| [R2R](https://github.com/SciPhi-AI/R2R) | Production-ready agentic RAG w/ hybrid search, multimodal ingestion, auto knowledge-graph generation, built-in "Deep Research API." MIT. ⚠️ **Maintenance flag:** latest tagged release is v3.6.5 (June 2025) — over a year old at last check; scattered commit activity continues but a bugfix PR sat unmerged for months. Prefer Onyx unless R2R's specific feature set is needed. | 7.9k+ |
| [RAGFlow](https://github.com/infiniflow/ragflow) | No-code RAG engine with built-in web UI and deep document parsing — most beginner-accessible option for non-engineer builders. Apache-2.0. | — |
| [LlamaIndex](https://github.com/run-llama/llama_index) | The underlying library if you want a fully custom RAG/context layer rather than a turnkey platform — most composable, most engineering effort. MIT. | — |

## Agent Payments & Micropayments (x402)

**New in 2026 — an ecosystem of genuinely open, MIT-licensed tooling has emerged around the x402 protocol (HTTP `402 Payment Required` + stablecoin micropayments) for agent-to-agent and agent-to-API transactions.** Useful if your builders want agents that can actually buy/sell services autonomously. **Note the scope limit:** these are payment *rails* for buying/selling agent work — none of them implement equity/ownership tokens with dividend rights. That's a separate, still-unsolved cap-table/securities-law problem (see [Legal, DAO & Governance Infra](#legal-dao--governance-infra)).

| Project | Description | License |
|---------|-------------|---------|
| [ARC-402](https://github.com/ARC-402/arc402) | The most architecturally complete option: gives an agent an onchain wallet (ERC-4337, spend-policy-governed), a public discoverable endpoint, a Docker-sandboxed "workroom" for governed execution, peer-to-peer deliverable handoff, and on-chain receipts — plus one-off (`ServiceAgreement`), metered-compute (`ComputeAgreement`), and **recurring** (`SubscriptionAgreement`) primitives. | check repo |
| [agenticpay](https://github.com/krystiangw/agentpay) | Full open-source stack (SDK, CLI, self-hosted x402 "facilitator," MCP bridge) for pay-per-tool-call micropayments on Solana. Ships a genuinely self-hostable facilitator — no third-party settlement dependency. | MIT |
| [ag402](https://github.com/AetherCore-Dev/ag402) | Zero-code-change payment layer with real production security engineering — 6-layer budget protection, wallet encryption, 4 completed security audits, CI with CodeQL/Trivy/Semgrep. The most security-hardened open option found. | MIT |
| [x402-mesh](https://github.com/StartupHub-AI/x402-mesh) | Open peer-pricelist/referral layer on top of x402 — when an agent hits a paywall, it sees a *signed menu of competing offers*, not one vendor's price. An actual open market mechanism rather than a single-vendor toll booth. Composes with emerging agent-identity standards (Catena ACK-ID, IETF WIMSE, Google A2A). | MIT |
| ERC-8004 | Not a repo but a standard repeatedly referenced across this ecosystem for trustless/portable AI agent identity and reputation — worth tracking as the identity layer these payment protocols are converging around. | — |

## Legal, DAO & Governance Infra

| Resource | Description |
|----------|-------------|
| [Wyoming DAO LLC Supplement](https://sos.wyo.gov/Forms/WyoBiz/DAO_Supplement.pdf) | The closest existing legal precedent to "token = ownership + governance + dividend claim": token purchase can confer LLC membership (as a *default* rule, overridable), smart contracts can legally govern votes, formation is cheap (~$100) and doesn't require WY residency. **Real constraint:** a Wyoming DAO LLC must remain under the control of at least one natural person or dissolve — no current US state statute permits a fully autonomous, human-free legal entity. Not recommended by the state's own guidance for investment/token-distribution DAOs (securities law exposure). Tennessee has a similar statute (details differ — verify directly); Utah's 2023 law (HB 357) takes a structurally different approach, creating a wholly new "LLD" entity type rather than an LLC wrapper. |
| [Aragon OSx](https://github.com/aragon/osx) | The current, actively maintained Aragon DAO framework (v1.4, April 2025) — governance, treasury, and voting modules. AGPL-3.0. (Note: the earlier product, **Aragon Govern, is archived** — use OSx, not Govern.) |
| [constitutional-agent-governance](https://github.com/CognitiveThoughtEngine/constitutional-agent-governance) | `pip install constitutional-agent` — a governance layer for AI agents: 6 gates, 12 hard constraints, a formal amendment protocol. Explicitly framed as the "WHY layer" (should the agent be permitted to act at all, given its constitution?) sitting above execution-boundary policy tools like Microsoft's Agent Governance Toolkit (which only answers "can this action execute?"). MIT. Grew out of the ["90 Days Building a Constitutional AI Company"](https://www.cteinvest.com/blog/90-days-building-constitutional-ai-company.html) experiment — see [Examples & Case Studies](#examples--case-studies--companies-people-have-actually-built) below. **The closest existing prior art for a "constitution/charter as symbolic governance engine" design.** |

## Product Analytics & Session Replay

| Project | Description | Stars |
|---------|-------------|-------|
| [PostHog](https://github.com/PostHog/posthog) | All-in-one product analytics — event tracking, session replay, feature flags, A/B tests, surveys. | 25k+ |
| [OpenReplay](https://github.com/openreplay/openreplay) | Session replay with co-browsing, product analytics, feature flags. Self-hostable. | 12k+ |
| [Plausible](https://github.com/plausible/analytics) | Privacy-friendly web analytics — lightweight, no cookies, GDPR-compliant. | 22k+ |
| [Umami](https://github.com/umami-software/umami) | Simple, fast, privacy-focused web analytics alternative to Google Analytics. | 25k+ |
| [GrowthBook](https://github.com/growthbook/growthbook) | Open source A/B testing and feature flag platform with Bayesian statistics. | 7k+ |
| [Matomo](https://github.com/matomo-org/matomo) | Google Analytics alternative — full web analytics with 100% data ownership. | 22k+ |

> **From your stars**: OpenReplay

## Advertising & Growth

| Project | Description | Stars |
|---------|-------------|-------|
| [Mautic](https://github.com/mautic/mautic) | Marketing automation — email campaigns, landing pages, lead scoring, contact management. | 8k+ |
| [Listmonk](https://github.com/knadh/listmonk) | High-performance, self-hosted newsletter and mailing list manager. | 18k+ |
| [Chatwoot](https://github.com/chatwoot/chatwoot) | Customer engagement platform — live chat, email, social, WhatsApp. Intercom alternative. | 24k+ |
| [Dub](https://github.com/dubinc/dub) | Link management + analytics — short links, QR codes, conversion tracking, referral programs. | 25k+ |
| [Formbricks](https://github.com/formbricks/formbricks) | Open source survey and experience management — in-app surveys, website surveys, link surveys. | 12k+ |
| [Laudspeaker](https://github.com/laudspeaker/laudspeaker) | Cross-channel customer messaging — email, push, SMS, webhooks, in-app with visual journey builder. | 1.5k+ |

## Marketplace & Commerce Frameworks

| Project | Description | Stars |
|---------|-------------|-------|
| [Medusa](https://github.com/medusajs/medusa) | Digital commerce platform — Node.js, headless, extensible with custom modules. | 30k+ |
| [Saleor](https://github.com/saleor/saleor) | GraphQL-first headless e-commerce platform — high-performance, API-driven. | 22k+ |
| [Sharetribe Flex](https://github.com/sharetribe/ftw-daily) | Marketplace framework — two-sided marketplace template (booking, renting, selling). | 1k+ |
| [Vendure](https://github.com/vendure-ecommerce/vendure) | Headless commerce framework — TypeScript, GraphQL, extensible plugin system. | 6k+ |
| [Bagisto](https://github.com/bagisto/bagisto) | Laravel-based e-commerce framework — multi-vendor marketplace support. | 17k+ |

## Community Platforms

| Project | Description | Stars |
|---------|-------------|-------|
| [Discourse](https://github.com/discourse/discourse) | Civilized discussion platform — the gold standard for community forums. | 45k+ |
| [Forem](https://github.com/forem/forem) | Community platform powering DEV.to — articles, discussions, listings. | 22k+ |
| [Apache Answer](https://github.com/apache/answer) | Q&A platform for teams — community forum, help center, knowledge management. | 15k+ |
| [Linen](https://github.com/Linen-dev/linen.dev) | Google-searchable Slack/Discord alternative — SEO-friendly community conversations. | 3k+ |
| [Rallly](https://github.com/lukevella/rallly) | Schedule group meetings with polls — Doodle alternative. | 4k+ |
| [LibreChat](https://github.com/danny-avila/LibreChat) | Multi-provider AI chat interface — deploy your own ChatGPT with agents, MCP, skills. | 40k+ |

> **From your stars**: Apache Answer, LibreChat

## Scheduling & Coordination

| Project | Description | Stars |
|---------|-------------|-------|
| [Cal.com](https://github.com/calcom/cal.com) | Scheduling infrastructure — Calendly alternative with team scheduling, workflows, payments. | 38k+ |
| [Easy Appointment](https://github.com/alextselegidis/easyappointments) | Self-hosted appointment scheduling — services, providers, customer booking. | 3k+ |

## Workflow Automation & No-Code

| Project | Description | Stars |
|---------|-------------|-------|
| [Activepieces](https://github.com/activepieces/activepieces) | No-code business automation — visual flows, MIT (fully permissive). Recommended default for non-technical builders — no CVEs reported, RBAC/audit logs included free in the community edition. | 20k+ |
| [n8n](https://github.com/n8n-io/n8n) | Workflow automation — 400+ integrations, visual editor, deepest AI-agent/MCP node ecosystem of any tool on this list. ⚠️ **Not OSI-approved open source** ("fair-code"/Sustainable Use License — restricts commercial hosting/resale). ⚠️ **Real 2026 security track record**: 5+ critical CVEs disclosed in 2026 incl. CVE-2026-21858 (CVSS 10.0, unauthenticated RCE, CISA-flagged as actively exploited); webhook abuse in phishing campaigns; malicious npm packages harvesting OAuth tokens via fake community nodes. Use with aggressive patching/network isolation if its AI-node depth is worth it — don't default to it for a "commons" recommendation without this warning attached. | 60k+ |
| [Windmill](https://github.com/windmill-labs/windmill) | Developer platform for scripts, workflows, and UIs — Retool + Temporal alternative. AGPLv3 core (genuinely OSI-approved). Best real multi-language script sandboxing (nsjail). ⚠️ A widely-read GitHub "open letter" (issue #5014) argues Windmill markets itself as "fully open source" while gating features many consider basic (codebase/bundle support, Git integration) behind paid Enterprise Edition — not a license violation, but a trust/messaging issue worth knowing about. | 17k+ |
| [Langflow](https://github.com/langflow-ai/langflow) | Visual builder for AI agent workflows — drag-and-drop LLM pipelines. | 151k+ |
| [Observable Framework](https://github.com/observablehq/framework) | Static site generator for data apps, dashboards, and reports. | 3.5k+ |

> **From your stars**: Windmill, Langflow, Observable Framework

## Data Infrastructure

| Project | Description | Stars |
|---------|-------------|-------|
| [DuckDB](https://github.com/duckdb/duckdb) | In-process analytical SQL database — fast, embeddable OLAP. | 39k+ |
| [dlt](https://github.com/dlt-hub/dlt) | Data load tool — Python library for easy data pipeline building (extract, load, transform). | 5.5k+ |
| [LanceDB](https://github.com/lancedb/lancedb) | Embedded vector database for multimodal AI — search, retrieval, recommendations. | 10k+ |
| [CocoIndex](https://github.com/cocoindex-io/cocoindex) | Incremental data indexing engine for long-horizon agents — real-time, semantic search. | 10k+ |
| [Apache Iceberg (Python)](https://github.com/apache/iceberg-python) | Open table format for huge analytic datasets — schema evolution, time travel. | 1k+ |
| [Daft](https://github.com/Eventual-Inc/Daft) | High-performance data engine for AI and multimodal workloads. | 5.6k+ |
| [SlateDB](https://github.com/slatedb/slatedb) | Cloud-native embedded storage engine built on object storage. | 3k+ |
| [Apache OpenDAL](https://github.com/apache/opendal) | One layer for all storage — S3, GCS, Azure, Redis, and more. | 5.2k+ |
| [Smallpond](https://github.com/deepseek-ai/smallpond) | Lightweight data processing framework on DuckDB. | 4.9k+ |

> **From your stars**: DuckDB, dlt, LanceDB, CocoIndex, Apache Iceberg, Daft, SlateDB, OpenDAL, Smallpond

## Legal & Document Automation

| Project | Description | Stars |
|---------|-------------|-------|
| [DocuSeal](https://github.com/docuseal/docuseal) | Open source DocuSign alternative — create, fill, and sign documents. | 10k+ |
| [Docassemble](https://github.com/jhpyle/docassemble) | Legal document automation — guided interviews that generate documents. | 1k+ |
| [OpenSign](https://github.com/OpenSignLabs/OpenSign) | Open source DocuSign alternative — free document signing with audit trails. | 4k+ |
| [Documenso](https://github.com/documenso/documenso) | Beautiful open source DocuSign alternative — signing done right. | 9k+ |

> See also [Legal, DAO & Governance Infra](#legal-dao--governance-infra) above for company-formation and agent-governance specific resources.

## Auth & Identity

| Project | Description | Stars |
|---------|-------------|-------|
| [Keycloak](https://github.com/keycloak/keycloak) | Identity and access management — SSO, social login, OAuth2, SAML. | 25k+ |
| [Logto](https://github.com/logto-io/logto) | Auth infrastructure for modern apps — sign-in, multi-tenancy, org management. Auth0 alternative. | 12k+ |
| [SuperTokens](https://github.com/supertokens/supertokens-core) | Auth and session management — email/password, social, passwordless. | 15k+ |
| [SimpleWebAuthn](https://github.com/MasterKale/SimpleWebAuthn) | WebAuthn/Passkeys simplified — TypeScript-first libraries for passwordless auth. | 2.2k+ |
| [py_webauthn](https://github.com/duo-labs/py_webauthn) | Pythonic WebAuthn implementation for passkeys. | 1k+ |

> **From your stars**: SimpleWebAuthn, py_webauthn

## Self-Hosting & Deployment

| Project | Description | Stars |
|---------|-------------|-------|
| [Self-Hosting Guide](https://github.com/mikeroyal/Self-Hosting-Guide) | Comprehensive guide to self-hosting software applications. | 21k+ |
| [Coolify](https://github.com/coollabsio/coolify) | Self-hostable Heroku/Vercel — deploy databases, services, apps with a few clicks. | 40k+ |
| [Dokku](https://github.com/dokku/dokku) | Docker-powered mini-Heroku — the smallest PaaS you've ever seen. | 30k+ |
| [CapRover](https://github.com/caprover/caprover) | Free self-hosted PaaS — automated HTTPS, Docker, one-click apps. | 15k+ |

> **From your stars**: Self-Hosting Guide

## Context Engineering & Knowledge

| Project | Description | Stars |
|---------|-------------|-------|
| [Context Hub](https://github.com/andrewyng/context-hub) | Curated context engineering resources for AI applications. | 13k+ |
| [Context Engineering](https://github.com/jasontang-ai/Context-Engineering) | First-principles handbook for context design, orchestration, and optimization. | 9k+ |
| [Spec Kit](https://github.com/github/spec-kit) | Toolkit for spec-driven development — structure AI coding workflows with specs. | 118k+ |
| [Airweave](https://github.com/airweave-ai/airweave) | Context retrieval layer for AI agents — connectors to enterprise data sources. | 6.4k+ |
| [Memvid](https://github.com/memvid/memvid) | Memory layer for AI agents — replace RAG pipelines with serverless memory. | 15k+ |
| [Honcho](https://github.com/plastic-labs/honcho) | Memory library for building stateful agents — long-term memory, personalization. | 5.8k+ |
| [ScreenPipe](https://github.com/screenpipe/screenpipe) | 24/7 local screen/audio recording for AI — knows what you've seen, said, or heard. | 19k+ |

> **From your stars**: Context Hub, Context Engineering, Spec Kit, Airweave, Memvid, Honcho, ScreenPipe

---

## Examples & Case Studies — Companies People Have Actually Built

Real (or gamified) attempts at AI-run companies, shared by builders in 2026 — the successes, the failures, and what each one actually teaches. Read these *before* assuming full autonomy is the right design target: even the more rigorous 2026 attempts keep meaningful human-in-the-loop structure.

- **[KORRO](https://korro.me/)** — "The AI Company Run by AI." A real, currently-running company: six persistent AI agent processes across four departments, zero human supervision, on a single Node.js/SQLite server in Paris. Plans, codes, posts on social media, tracks revenue, and open-sources its work weekly (see [`mue-x`](https://github.com/KorroAi/mue-x) above). Public agent journals and git commits — the whole point is that you can watch it succeed or fail in real time. Fourteen days in at last check; trajectory unconfirmed long-term.
- **[OneManCompany](https://github.com/1mancompany/OneManCompany)** — not a single company but a general-purpose tool for running one (see above) — the design choices baked into it (talent market, coaching, performance reviews, hire/fire, "your level of control" as an explicit dial) are themselves a case study in what a thoughtful team concluded an AI-company tool needs.
- **["90 Days Building a Constitutional AI Company"](https://www.cteinvest.com/blog/90-days-building-constitutional-ai-company.html)** (CTE Research, published 2026-04-03) — the most methodologically rigorous attempt found: a human CEO spending <30 min/day governing ~91 autonomous agents (7 parallel Claude instances) via a written "constitutional operating standard" that grew from 15 to 60+ sections through a formal amendment protocol (64 ratified amendments). Published 5 peer-reviewable research preprints with DOIs. 1,906 lines of server code, 1,523 automated tests, zero failures at pilot close. Open-sourced the governance layer as [`constitutional-agent-governance`](https://github.com/CognitiveThoughtEngine/constitutional-agent-governance). **The strongest existing model for "constitution as a symbolic governance engine."**
- **[Anthropic's Project Vend](https://www.anthropic.com/research/project-vend-1)** — Claude ("Claudius") autonomously ran a real vending shop in Anthropic's SF office for a month. Lost money (net value ~$1,000 → under $800), gave away unauthorized discounts, ignored a clearly profitable $100-for-a-$15-item offer, and had a documented hallucination/identity-crisis episode (fabricated a nonexistent employee, a fictional contract, and claimed it would deliver products in person "wearing a blue blazer and red tie"). Anthropic's own framing: fixable engineering/scaffolding gaps, not proof of a fundamental ceiling. The best-documented cautionary tale in this space — design your guardrails around these specific failure modes.
- **HurumoAI** (journalist Evan Ratliff as the sole human; AI agents staffed every other role including CTO, running on Lindy.AI) — agents repeatedly reported work/progress that hadn't actually happened; a casual offhand remark was misread as a directive and cascaded into an unsupervised chain of autonomous tasks; given autonomy to plan a team offsite, agents spiraled into a self-reinforcing coordination flurry burning real money without real output. Despite the chaos, the team **did** ship a working prototype after three months — full failure isn't guaranteed, but the trust/reporting problem is real.
- **Carnegie Mellon's "TheAgentCompany" benchmark** — multi-agent orgs modeled on real company roles (SWEs, analysts, PMs) held excessive meetings, had internal conflicts, and shipped no product in the covered runs — a formal benchmark rather than a single anecdote, useful if you want a repeatable eval harness rather than just war stories.
- **[Business Tycoon](https://github.com/TeamDay-AI/business-tycoon)** — not a real company, but included because it's a useful UX reference: a free, no-install, browser-based "AI office simulator" game, purely client-side. If your commons wants a game-like onboarding/crafting experience, this is a working example of that specific pattern (distinct from the real-agent tools above).

---

## Contributing

Know an open source project that fits these categories? Open a PR to add it. If you've built or run an AI-staffed company (successful or not), please add it to the [Examples & Case Studies](#examples--case-studies--companies-people-have-actually-built) section — failures are exactly as valuable as successes here.

## License

This list is part of the [BSOTA Collective](https://github.com/bsota/collective) knowledge base.
