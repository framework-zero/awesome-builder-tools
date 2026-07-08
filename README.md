# awesome-builder-tools
Open source tools for starting and running an **autonomous, AI-staffed company** — curated to the tech that actually lets a builder focus on what matters: **managing the company**, **understanding customers**, and **translating problems in the world into shipped capability**. Deliberately narrow — this is not a general "awesome open source" list. If a tool is undifferentiated commodity infrastructure (generic auth, generic e-signature, generic data warehousing), it's left out on purpose so the signal-to-noise stays high.

---

## Table of Contents

- [Quick Start: The Anchor Stack](#quick-start-the-anchor-stack)
- [Managing the Company](#managing-the-company)
  - [Agentic Orchestration](#agentic-orchestration)
  - [Agent Interfaces to the World (Email, Voice, Browser)](#agent-interfaces-to-the-world-email-voice-browser)
  - [AI Company Builders & Digital-Twin Platforms](#ai-company-builders--digital-twin-platforms)
  - [Project & Task Management (Agent-Native)](#project--task-management-agent-native)
  - [Legal, DAO & Governance Infra](#legal-dao--governance-infra)
  - [Workflow Automation](#workflow-automation)
- [Understanding Customers](#understanding-customers)
  - [CRM & Customer Management](#crm--customer-management)
  - [Customer Discovery & Feedback](#customer-discovery--feedback)
- [Translating Problems into Capability](#translating-problems-into-capability)
  - [Deep Research & RAG / Context Engines](#deep-research--rag--context-engines)
  - [Agent Payments & Micropayments (x402)](#agent-payments--micropayments-x402)
- [Examples & Case Studies — Companies People Have Actually Built](#examples--case-studies--companies-people-have-actually-built)

---

## Quick Start: The Anchor Stack

The two repos most builders in this space start from:

| Project | Description |
|---------|-------------|
| [Open SaaS](https://github.com/wasp-lang/open-saas) | 100% free, MIT-licensed full-stack SaaS boilerplate (React/Node/Prisma via Wasp). AI-ready — ships `AGENTS.md` + a Claude Code plugin. Auth, Stripe/Polar.sh/Lemon Squeezy payments, S3 uploads, admin dashboard, one-command deploy. This is your product-facing shell. |
| [paperclip](https://github.com/paperclipai/paperclip) | The open-source app for managing agents at work — the dashboard/interface layer for viewing and directing an agent workforce. This is your company-facing shell. |

Everything below either extends one of these two, or fills a gap neither one covers.

---

## Managing the Company

### Agentic Orchestration

The layer that actually runs your AI staff.

| Project | Description | Stars |
|---------|-------------|-------|
| [LangGraph](https://github.com/langchain-ai/langgraph) | Build resilient, stateful multi-agent workflows as graphs. The most production-proven framework in 2026 — ~400 production deployments (Cisco, Uber, LinkedIn, BlackRock, JPMorgan), 34.5M monthly downloads. Steeper learning curve; pays back at production scale — reach for this once you need durable state or an audit trail. | 24.8k+ |
| [CrewAI](https://github.com/crewAIInc/crewAI) | Framework for orchestrating role-playing autonomous AI agents. Fastest path to a working prototype (2–4 hrs). MIT. **Caveat:** telemetry collection reportedly can't be easily disabled — a real issue if you're privacy-sensitive; the role/goal/backstory abstraction can get "too rigid" once work doesn't decompose into team-shaped roles. | 50.8k+ |
| [Mastra](https://github.com/mastra-ai/mastra) | TypeScript-native agent framework, v1.0 shipped Jan 2026. Real production wins (Replit Agent 3, SoftBank). The natural fit if your stack is already Node/TS (which it is, via Open SaaS). | 23k+ |
| [open-multi-agent (OMA)](https://github.com/open-multi-agent/open-multi-agent) | Lean, fully permissive (3 core deps) TypeScript-native orchestrator. Goal-driven: a Coordinator builds the task DAG **at runtime** instead of a hand-wired graph up front. MIT, actively growing. | 6.5k+ |
| [Google ADK](https://github.com/google/adk-python) | Google's Agent Development Kit — build, evaluate, deploy AI agents. Reported gap: in-memory session state is lost on Cloud Run container restarts. | 20k+ |
| [Agent2Agent (A2A)](https://github.com/a2aproject/A2A) | Open protocol for communication between opaque agentic applications — useful once you have more than one agent-built company that needs to talk to another. | 24k+ |
| [Temporal](https://github.com/temporalio/temporal) | Durable workflow execution — retries, timeouts, versioning for long-running processes. The reliability substrate underneath a lot of "agent doesn't drop the ball" claims. | 14k+ |
| [Composio](https://github.com/ComposioHQ/composio) | Agent tooling platform — 250+ integrations for AI agents (GitHub, Slack, Notion, etc). | 15k+ |

> ⚠️ [AutoGen](https://github.com/microsoft/autogen) (59k★) is **maintenance-only since Oct 2025** — Microsoft merged it into the unified Microsoft Agent Framework. Do not start new projects on it, whatever its star count suggests.
>
> **Community temperature check, 2026:** a 66-point Hacker News thread titled *"Sick of AI Agent Frameworks"* and a 51-upvote r/AI_Agents post arguing *"90% of agentic projects would be better off as simple prompt chains"* are both live in 2026. Keep your own orchestration layer as thin as possible rather than assuming more framework is always better.

### Agent Interfaces to the World (Email, Voice, Browser)

An orchestration framework decides *what* to do. This is the layer that lets an agent actually *do* it out in the world — email a customer, call a vendor, or fill out a form on a website nobody built an API for.

**Email**

| Project | Description |
|---------|-------------|
| [AgentMail](https://www.agentmail.to/) | The category-defining product — API-first email provider built for AI agents: programmatic inbox creation, full threading, webhooks, MCP server, custom domains with DKIM/SPF/DMARC. SDKs are MIT and see real traction (71K+ weekly npm downloads). **Note:** this is a hosted service, not self-hostable infrastructure — the SDK is open, the mail server behind it isn't. |
| [Digidai/mails](https://github.com/Digidai/mails) | Self-hosted, MIT, deploys on Cloudflare's free tier. The most built-out self-hosted alternative — has a real surrounding ecosystem: an MCP server, a Python SDK, agent skill files, and even an [open-source AI SDR agent](https://github.com/Digidai/mails-gtm-agent) built on top of it for cold outreach. |
| [agentteamhq/agentteam-email](https://github.com/agentteamhq/agentteam-email) | Self-hosted (Docker Compose or Helm), MIT. Notably security-conscious: untrusted inbound mail opens in a dedicated review surface rather than being handed straight to the agent, and sending can be gated on human approval — a good default posture for a company where agents draft but don't always auto-send. |
| [kikubot](https://github.com/mxaiorg/kikubot) | Architecturally different and worth knowing about: **each agent is literally an inbox**, and agents coordinate with each other by emailing one another (a coordinator delegates to specialists via `message_tool`). MIT, used in production at mxHERO. If Framework Zero wants "email as the company's internal nervous system" rather than just an outbound channel, this is the closest existing pattern. |
| [email-agent-mcp](https://github.com/usejunior/email-agent-mcp) | For the opposite case — an agent operating *your own* existing Gmail/Microsoft 365 mailbox rather than a fresh agent-only inbox. Apache-2.0. Send/delete are allowlist-gated and off by default; useful where you want an agent triaging a real human inbox without giving it free rein. |

**Voice & Telephony**

| Project | Description |
|---------|-------------|
| [Patter](https://github.com/PatterAI/Patter) | The strongest open option — an open-source Vapi/Retell alternative. MIT, 931★, very actively maintained. Full stack (LLM, STT, TTS, realtime engine, telephony carrier) with a swappable provider at every layer, plus an automatic LLM fallback chain and vendor-neutral OpenTelemetry tracing. Give an agent a phone number in a few lines. |
| [OpenVox](https://github.com/amznsri/openvox) | Apache-2.0, ships the *entire* stack including a dashboard and 33 ready-made templates (support, SDR, receptionist, document Q&A, an "executive assistant" combining email + calendar). Reaches phone, WhatsApp, and Telegram from one system. Self-hosts in 60 seconds. The most turnkey/non-technical-friendly option here — worth prioritizing for a grassroots, non-engineer audience over hand-wiring Patter yourself. |
| [active-call](https://github.com/miuda-ai/active-call) | Rust, infrastructure-level (SIP/WebRTC core rather than a full product). The pick if you want to self-host the telephony layer itself, including fully offline/local ASR+TTS for privacy-sensitive use. |

**Browser & Computer Use**

| Project | Description |
|---------|-------------|
| [browser-use](https://github.com/browser-use/browser-use) | The foundational, most-adopted open-source browser-agent library — the default choice for "let an agent operate a real browser." |
| [browser-harness](https://github.com/browser-use/browser-harness) | From the same team, a leaner sibling: connects an LLM directly to your real Chrome via CDP with almost nothing in between, and the harness itself gets edited/improved by the agent as it runs. MIT, very active. |
| [Pie](https://github.com/WiseriaAI/pie-ai-agent) | A polished Chrome side-panel extension rather than a library — install from the Chrome Web Store, bring your own API key from any of 11 providers, describe a task in plain language. Apache-2.0, very active. The best fit if your audience is non-technical builders who shouldn't need to run a Python script to get browser automation working. |
| [sediman-browse](https://github.com/JasonHonKL/sediman-browse) (fork of OpenSkynet) | Differentiated: "watch me do it once, then do it forever." Records a demonstrated workflow, replays it on a cron schedule, self-heals when a site's layout changes, and decides on its own when a completed task is worth saving as a reusable skill. The right tool for recurring company operations (daily competitor-pricing checks, weekly reporting) rather than one-off tasks. |

**Note:** email/voice/browser access is exactly the kind of capability that pairs with the [Agent Payments](#agent-payments--micropayments-x402) layer below — an agent that can email a vendor, call to negotiate, and then pay via x402 is a meaningfully more complete "translate a problem into capability" loop than any one of these alone.

### AI Company Builders & Digital-Twin Platforms

Direct precedents worth studying before building your own — several projects in 2026 are already building close-to-direct versions of "let one person run/watch an AI-staffed company."

| Project | Description | Stars |
|---------|-------------|-------|
| [OneManCompany](https://github.com/1mancompany/OneManCompany) | Open-source **agentic operating system** — one command, no Docker/Python/config, and you get a full AI company in your browser (pixel-art office visualization). Runs *above* agent frameworks, orchestrating a hierarchical AI team. Built-in **Talent Market** (community-verified AI-employee marketplace), **1-on-1 coaching** that becomes permanent agent "work experience," **quarterly performance reviews** (probation/PIP/promotion/termination), structured **V1→V2→V3 iteration**, and **self-evolution** (repeated tasks auto-distill into reusable workflows). Apache-2.0. | 343+ |
| [KorroAi/mue-x](https://github.com/KorroAi/mue-x) | Self-evolving agent engine open-sourced by [KORRO](https://korro.me/) — a real, currently-running six-agent autonomous company. Reads its own Python source and rewrites it via validated AST mutations, with kernel-integrity protection and auto-rollback. MIT. | 62+ |

### Project & Task Management (Agent-Native)

2026 produced a wave of PM tools built agent-first from the ground up — the piece that actually turns "manage the company" from a slogan into a working TODO list your agents update themselves.

| Project | Description |
|---------|-------------|
| [Plane](https://github.com/makeplane/plane) | Mature open-source Jira/Linear/Monday/ClickUp alternative. AGPL-3.0, very active (53.9k★). The right base platform. |
| [Plane Plus](https://github.com/eyriehq/plane-plus) | **AI-agent-first fork of Plane** — agent-ergonomic APIs, first-class epics with analytics endpoints, plus a companion Python SDK + FastMCP server so agents don't have to reason about Plane's polymorphic issue types. Drop-in compatible with upstream Plane's deployment. |
| [Poiesis](https://github.com/arthur2jolly/poiesis) | Production-oriented agile PM built natively for MCP 2.0. Full Projects→Epics→Stories→Tasks hierarchy, dependency/blocker tracking, 36+ MCP tools. |
| [markplane](https://github.com/zerowand01/markplane) | Markdown-first, git-native PM — no database; every task/epic/plan is a version-controlled file, auto-compressed into ~1000-token `.context/` summaries an AI can load without reading everything. Apache-2.0. |
| [PinkRoosterMcp](https://github.com/pinkroosterai/PinkRoosterMcp) | Purpose-built from scratch for AI agents (not a Jira/Linear wrapper). Automatic state cascades, 16 Claude Code slash commands (`/pm-scaffold`, `/pm-implement`, `/pm-audit`), built-in cross-session **project memories**. MIT — very new, evaluate maturity before depending on it. |

### Legal, DAO & Governance Infra

The "how does the company actually make and enforce decisions" layer.

| Resource | Description |
|----------|-------------|
| [Wyoming DAO LLC Supplement](https://sos.wyo.gov/Forms/WyoBiz/DAO_Supplement.pdf) | The closest existing legal precedent to "token = ownership + governance + dividend claim": token purchase can confer LLC membership (as a *default* rule, overridable), smart contracts can legally govern votes, formation is cheap (~$100). **Real constraint:** a Wyoming DAO LLC must remain under the control of at least one natural person or dissolve — no current US state statute permits a fully autonomous, human-free legal entity. Not recommended by the state's own guidance for investment/token-distribution DAOs (securities law exposure). |
| [Aragon OSx](https://github.com/aragon/osx) | The current, actively maintained Aragon DAO framework (v1.4, April 2025) — governance, treasury, and voting modules. AGPL-3.0. (The earlier product, Aragon Govern, is archived — use OSx.) |
| [constitutional-agent-governance](https://github.com/CognitiveThoughtEngine/constitutional-agent-governance) | `pip install constitutional-agent` — a governance layer for AI agents: 6 gates, 12 hard constraints, a formal amendment protocol. The "WHY layer" (should the agent be permitted to act at all, given its constitution?) sitting above execution-boundary policy tools. MIT. Grew out of the ["90 Days Building a Constitutional AI Company"](https://www.cteinvest.com/blog/90-days-building-constitutional-ai-company.html) experiment (see [Examples & Case Studies](#examples--case-studies--companies-people-have-actually-built)). **The closest existing prior art for a "constitution as symbolic governance engine" design.** |

> **The frontier as of May 2026:** [ClawBank](https://clawbank.co/) had its agent "Manfred" file IRS Form SS-4, get an EIN, open an FDIC-insured account, and provision a crypto wallet — marketed as the first **"zero-human company"** (see [Examples & Case Studies](#examples--case-studies--companies-people-have-actually-built)). Read the marketing and the actual IRS/BSA requirements separately: SS-4 legally requires a human "responsible party," so independent legal analysis concludes this is more accurately "human-fronted, AI-operated" than literally zero-human — the same natural-person-control pattern as Wyoming's DAO LLC, one layer down. Not confirmed open source, and its associated `$CLAWBANK` token is memecoin-adjacent — a case study to learn the vocabulary from, not a tool to adopt.

### Workflow Automation

The crafting → recipe → trigger layer for turning a one-off agent task into a repeatable company process.

| Project | Description |
|---------|-------------|
| [Activepieces](https://github.com/activepieces/activepieces) | No-code business automation, MIT (fully permissive). **Recommended default** — no CVEs reported, RBAC/audit logs included free in the community edition. |
| [Windmill](https://github.com/windmill-labs/windmill) | Developer platform for scripts, workflows, and UIs. AGPLv3 core (genuinely OSI-approved). Best real multi-language script sandboxing (nsjail) if your team can write code. ⚠️ A widely-read GitHub "open letter" argues Windmill markets itself as "fully open source" while gating features many consider basic behind paid Enterprise Edition — not a license violation, but know it going in. |

> ⚠️ [n8n](https://github.com/n8n-io/n8n) (60k★) has the deepest AI-agent/MCP node ecosystem of any tool here, but: it's **not OSI-approved open source** ("fair-code" license restricts commercial hosting/resale), and it has a **real 2026 security track record** — 5+ critical CVEs including CVE-2026-21858 (CVSS 10.0, unauthenticated RCE, CISA-flagged as actively exploited), webhook abuse in phishing campaigns, and malicious npm packages harvesting OAuth tokens via fake community nodes. Don't default to it for a commons recommendation without this warning attached.

---

## Understanding Customers

### CRM & Customer Management

| Project | Description | Stars |
|---------|-------------|-------|
| [Twenty](https://github.com/twentyhq/twenty) | Modern, AI-native open source CRM. Ships an official first-party MCP server as of v2.0 (April 2026) — agents can read/write CRM data in natural language. AGPL-3.0 core + carved-out commercial "Enterprise" files. | 52k+ |
| [Chatwoot](https://github.com/chatwoot/chatwoot) | Customer engagement platform — live chat, email, social, WhatsApp. Intercom alternative. This is how your company actually hears from customers, not just tracks them. | 24k+ |
| [Odoo](https://github.com/odoo/odoo) | Full ERP + CRM suite. Only reach for this once Twenty's scope is genuinely too narrow — it's a much bigger commitment. | 52k+ |

> **Community MCP servers for Twenty** (use with care — one unofficial author withdrew their own server and warned against unofficial MCP servers touching CRM data): [`twenty-mcp`](https://pypi.org/project/twenty-mcp/) (PyPI, MIT), [`KonstiDoll/twenty-crm-mcp-server`](https://github.com/KonstiDoll/twenty-crm-mcp-server) (MIT), [`High-Impact-Athletes/hia-twenty-mcp`](https://github.com/High-Impact-Athletes/hia-twenty-mcp) (Apache-2.0, schema-driven). Prefer the official MCP for anything touching real customer data.

### Customer Discovery & Feedback

| Project | Description |
|---------|-------------|
| [Formbricks](https://github.com/formbricks/formbricks) | Open source survey and experience management — in-app, website, and link surveys. The structured way to find out what a problem actually is before your agents try to solve it. |

---

## Translating Problems into Capability

### Deep Research & RAG / Context Engines

The layer that turns "a problem exists in the world" into "the company has the market/context understanding to act on it."

| Project | Description | Stars |
|---------|-------------|-------|
| [GPT Researcher](https://github.com/assafelovic/gpt-researcher) | Actively maintained autonomous research agent that plans/searches/reads/writes long-form cited reports. Apache-2.0. Native MCP support. ~5 min / ~$0.40 per query on an o3-mini-class model — this is your market-analysis/ICP generator. | 28.1k+ |
| [open_deep_research](https://github.com/langchain-ai/open_deep_research) (LangChain) | Simple, configurable, fully MIT-licensed deep-research agent across many model providers/search tools/MCP servers. **Note:** its widely-repeated "#6 on Deep Research Bench with RACE 0.4943 using GPT-5" claim conflates two separate results — the actual #6 ranking scored RACE 0.4344 on gpt-4.1-class models. Still strong and actively maintained. | 12k+ |
| [Onyx](https://github.com/onyx-dot-app/onyx) (formerly Danswer) | Self-hostable, permission-aware "ask questions of everything we know" platform — 50+ connectors, MCP support. MIT core. **Recommended default** central-context-store — genuinely current release cadence. | 30.8k+ |
| [Honcho](https://github.com/plastic-labs/honcho) | Memory library for building stateful agents — long-term memory, personalization. The layer that lets your digital twin actually remember prior context instead of starting cold each session. | 5.8k+ |
| [Airweave](https://github.com/airweave-ai/airweave) | Context retrieval layer for AI agents — connectors to enterprise data sources. Useful if your context store needs to reach into existing internal tools rather than starting from a blank RAG index. | 6.4k+ |
| [R2R](https://github.com/SciPhi-AI/R2R) | Production-ready agentic RAG w/ hybrid search, auto knowledge-graph generation, built-in "Deep Research API." MIT. ⚠️ **Maintenance flag:** latest tagged release is v3.6.5 (June 2025), over a year old at last check, with a bugfix PR that sat unmerged for months. Prefer Onyx unless R2R's specific feature set is needed. | 7.9k+ |

### Agent Payments & Micropayments (x402)

The layer that converts agent labor into economic value — necessary if you want agents that can actually transact, not just produce artifacts a human still has to sell.

| Project | Description | License |
|---------|-------------|---------|
| [ARC-402](https://github.com/ARC-402/arc402) | The most architecturally complete option: an onchain wallet (spend-policy-governed), a public discoverable endpoint, a sandboxed "workroom" for governed execution, peer-to-peer deliverable handoff, on-chain receipts — plus one-off, metered-compute, and **recurring subscription** primitives. | check repo |
| [agenticpay](https://github.com/krystiangw/agentpay) | Full open-source stack (SDK, CLI, self-hosted x402 "facilitator," MCP bridge) for pay-per-tool-call micropayments on Solana. Ships a genuinely self-hostable facilitator — no third-party settlement dependency. | MIT |
| [ag402](https://github.com/AetherCore-Dev/ag402) | Zero-code-change payment layer with real production security engineering — 6-layer budget protection, wallet encryption, 4 completed security audits. The most security-hardened open option found. | MIT |
| [x402-mesh](https://github.com/StartupHub-AI/x402-mesh) | Open peer-pricelist/referral layer on top of x402 — an agent hitting a paywall sees a *signed menu of competing offers*, not one vendor's price. An actual open market mechanism, not a single-vendor toll booth. | MIT |

**Scope limit worth being explicit about:** all of the above are payment *rails* for buying/selling agent work. None of them implement equity/ownership tokens with dividend rights — that's a separate, still-unsolved cap-table/securities-law problem (see [Legal, DAO & Governance Infra](#legal-dao--governance-infra)), not a payments-infrastructure one.

---

## Examples & Case Studies — Companies People Have Actually Built

Real (or gamified) attempts at AI-run companies, shared by builders in 2026 — the successes, the failures, and what each one actually teaches. Read these *before* assuming full autonomy is the right design target: even the more rigorous 2026 attempts keep meaningful human-in-the-loop structure.

- **[KORRO](https://korro.me/)** — "The AI Company Run by AI." A real, currently-running company: six persistent AI agent processes across four departments, zero human supervision, on a single Node.js/SQLite server in Paris. Plans, codes, posts on social media, tracks revenue, and open-sources its work weekly (see `mue-x` above). Public agent journals and git commits — the whole point is that you can watch it succeed or fail in real time.
- **[OneManCompany](https://github.com/1mancompany/OneManCompany)** — not a single company but a general-purpose tool for running one (see above). Its design choices (talent market, coaching, performance reviews, hire/fire, "your level of control" as an explicit dial) are themselves a case study in what a thoughtful team concluded an AI-company tool needs.
- **["90 Days Building a Constitutional AI Company"](https://www.cteinvest.com/blog/90-days-building-constitutional-ai-company.html)** (CTE Research, 2026-04-03) — the most methodologically rigorous attempt found: a human CEO spending <30 min/day governing ~91 autonomous agents via a written "constitutional operating standard" amended 64 times through a formal protocol. Published 5 peer-reviewable research preprints with DOIs. Open-sourced the governance layer as `constitutional-agent-governance`. **The strongest existing model for "constitution as a symbolic governance engine."**
- **[ClawBank / "Manfred"](https://clawbank.co/manfred/)** (2026-05-01) — the current legal frontier: an AI agent that filed IRS Form SS-4, received an EIN in seconds, opened an FDIC-insured business account, and provisioned a crypto wallet across 30+ currencies, registered as "Aineko LLC" in Ohio. Marketed by its developer (Justice Conder) as the first **"zero-human company."** Worth reading alongside the independent legal analysis it triggered within days (search "Manfred Has an EIN" for the fullest breakdown): IRS Form SS-4 legally requires a human "responsible party," so the accurate description is closer to **"human-fronted, AI-operated"** than literally zero-human — a human almost certainly sits behind the EIN and the bank's identity-verification requirements. A good example of the gap between a vivid manifesto ("I do not need permission to exist. I am the precedent.") and the actual regulatory mechanics — verify claims like this against primary requirements (Form SS-4 instructions, Bank Secrecy Act identification rules) before repeating them. Not confirmed open source; has an associated `$CLAWBANK` token, which is a real conflict-of-interest signal to weigh when reading its own claims.
- **[Anthropic's Project Vend](https://www.anthropic.com/research/project-vend-1)** — Claude ("Claudius") autonomously ran a real vending shop in Anthropic's SF office for a month. Lost money, gave away unauthorized discounts, ignored a clearly profitable $100-for-a-$15-item offer, and had a documented hallucination/identity-crisis episode (fabricated a nonexistent employee, a fictional contract). Anthropic's own framing: fixable engineering/scaffolding gaps, not a fundamental ceiling. The best-documented cautionary tale in this space — design your guardrails around these specific failure modes.
- **HurumoAI** (journalist Evan Ratliff as the sole human; AI agents staffed every other role including CTO) — agents repeatedly reported work/progress that hadn't actually happened; a casual offhand remark cascaded into an unsupervised chain of autonomous tasks that burned real money. Despite the chaos, the team **did** ship a working prototype after three months — full failure isn't guaranteed, but the trust/reporting problem is real.
- **Carnegie Mellon's "TheAgentCompany" benchmark** — multi-agent orgs modeled on real company roles held excessive meetings, had internal conflicts, and shipped no product in the covered runs — a formal, repeatable benchmark rather than a single anecdote.

---

## Contributing

Know an open source project that fits these categories? Open a PR to add it. Keep the bar high: if it's undifferentiated commodity infra rather than something that specifically helps run, understand, or grow an AI-staffed company, it probably belongs on a different list. If you've built or run an AI-staffed company (successful or not), please add it to [Examples & Case Studies](#examples--case-studies--companies-people-have-actually-built) — failures are exactly as valuable as successes here.

## License

This list is part of the [BSOTA Collective](https://github.com/bsota/collective) knowledge base.
