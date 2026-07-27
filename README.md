<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                      ASCII HEADER                             -->
<!-- ═══════════════════════════════════════════════════════════════ -->

```
███████╗██╗   ██╗ █████╗ ██████╗    
██╔════╝██║   ██║██╔══██╗██╔══██╗    
█████╗  ██║   ██║███████║██║  ██║      
██╔══╝  ██║   ██║██╔══██║██║  ██║     
██║     ╚██████╔╝██║  ██║██████╔╝   
╚═╝      ╚═════╝ ╚═╝  ╚═╝╚═════╝   
```

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                    ANIMATED TYPING SVG                        -->
<!-- ═══════════════════════════════════════════════════════════════ -->

<div align="center">

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Sora&weight=700&size=23&duration=2600&pause=900&color=6C63FF&center=true&vCenter=true&width=720&lines=Backend+engineer+working+in+the+LLM+layer;Streaming%2C+retries%2C+cost+math%2C+agent+loops;Sylhet%2C+Bangladesh+%E2%80%94+UTC%2B6%2C+ships+on+EST%2FCET+time;Fourteen+repos%2C+every+one+of+them+runnable)](https://git.io/typing-svg)

</div>

---

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                   POSITIONING STATEMENT                       -->
<!-- ═══════════════════════════════════════════════════════════════ -->

<div align="center">

Most of what breaks in AI products isn't the model call — it's everything wrapped around it. What happens when the client closes the tab mid-stream. Whether a retry storm makes an outage worse. Whether the bill at the end of the month matches what actually got billed. That's the layer I work in.<br/>
Below: five things running in production right now, and fourteen smaller repos where I picked one failure mode and built until I understood it.

</div>

---

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--               SNAKE CONTRIBUTION GRAPH                        -->
<!-- Setup: Add .github/workflows/snake.yml to your profile repo   -->
<!-- ═══════════════════════════════════════════════════════════════ -->

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Fuad-Haque/Fuad-Haque/output/github-contribution-grid-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Fuad-Haque/Fuad-Haque/output/github-contribution-grid-snake.svg" />
  <img alt="GitHub contribution snake" src="https://raw.githubusercontent.com/Fuad-Haque/Fuad-Haque/output/github-contribution-grid-snake-dark.svg" />
</picture>

</div>

---

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                    HOW THE PIECES FIT                          -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 👾 How the Pieces Fit

A simplified version of the path a request takes across these systems. Not every live project touches every stage below — this compresses the common pattern across all of them into one flow, rather than depicting one single running app.

```
                       ┌─────────────────────────┐
                       │     Request arrives     │
                       │ (SSE, REST, or webhook) │
                       └─────────────────────────┘
                                    │
                                    ▼
┌───────────────────────────────────────────────────────────────────────┐
│                              Guard layer                              │
│ token check -> schema validation -> retry/backoff -> provider routing │
└───────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
         ┌────────────────────────────────────────────────────┐
         │                     Model call                     │
         │ OpenAI / Groq / Anthropic - swapped by one env var │
         └────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌──────────────────────────────────────────────────────────────────────┐
│                             Cost ledger                              │
│ 4-bucket accounting, checked before the call is even allowed to fire │
└──────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
      ┌───────────────────────────────────────────────────────────┐
      │                  Response streamed back                   │
      │ disconnect-aware: client drops -> upstream call stops too │
      └───────────────────────────────────────────────────────────┘
```

The **guard layer** and the **cost ledger** are the two stages most tutorials skip entirely. Nearly all of the studies below live in one of those two boxes.

---

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                      LIVE PROJECTS                            -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 🏗️ Running in Production

Five systems, each reachable right now. Each one has its own Swagger/OpenAPI docs, a `docker-compose.yml`, and a recorded walkthrough of the thing actually working.

| Project | What it does | Stack | Docs | Live |
|---------|-------------|-------|------|------|
| **Webhook Inspector** | Watches Stripe / GitHub / Shopify webhook traffic in real time, verifies HMAC signatures before anything is trusted, and can re-fire any stored event at a new target for debugging | FastAPI · Next.js · WebSocket · PostgreSQL | [/docs ↗](https://webhook-handler-production-99e2.up.railway.app/docs) | [Dashboard ↗](https://webhook-inspector-frontend.vercel.app) |
| **Semantic Search Platform** | Runs keyword and vector search side by side against the same document set, then blends them with Reciprocal Rank Fusion instead of picking one method and hoping | FastAPI · Next.js · Qdrant · PostgreSQL | [/docs ↗](https://semantic-search-frontend-j6yp.vercel.app/docs) | [App ↗](https://semantic-search-frontend-j6yp.vercel.app/search) |
| **URL Shortener API** | Ordinary on the surface — the actual point is the auth model: per-user link ownership enforced at the database layer, not just checked in a route handler | FastAPI · PostgreSQL · Railway | [/docs ↗](https://web-production-5bd50.up.railway.app/docs) | backend |
| **Task Automation API** | Background jobs that queue instantly and report real progress instead of a spinner — full state machine from queued to complete, failed, or cancelled | FastAPI · Railway | [/docs ↗](https://task-automation-api-i90w.onrender.com/docs) | backend |
| **Portfolio** | The site itself — custom design system, scroll-driven animation, a working contact endpoint on the backend rather than a static mailto link | Next.js · FastAPI · GSAP | — | [fuadhaque.com ↗](https://fuadhaque.com) |

---

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                  ENGINEERING STUDIES                           -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 🔬 Fourteen Ways Something Can Go Wrong

Each of these repos exists because I wanted to watch one specific failure mode happen on purpose, in isolation, instead of discovering it in production later. None of them are toy tutorials copied from documentation — each one deliberately breaks something and shows what the breakage looks like.

| Study | The failure mode it isolates | Stack |
|-------|-------------------------------|-------|
| **[Claude Tool-Use Loop](https://github.com/Fuad-Haque/anthropic-tool-use-loop)** | What happens between "the model asked for a function" and "the model has an answer" — the full round-trip, with a real subprocess doing real work in the middle | FastAPI · Anthropic SDK · Python |
| **[Context Window Auto-Summarisation](https://github.com/Fuad-Haque/context-window-auto-summarisation)** | Guessing at token count versus measuring it — this uses Anthropic's actual counting endpoint so the 80% trigger point is real, not estimated | FastAPI · Python · Anthropic API |
| **[Token Economics & Cost Tracking](https://github.com/Fuad-Haque/token-economics-cost-tracking)** | The four prices that get flattened into "one API call cost X" — input, output, cache write, cache read all bill differently and this keeps them separate | FastAPI · Python · SQLite · Anthropic API |
| **[Token Threshold Guard](https://github.com/Fuad-Haque/token-threshold-guard)** | Paying for a request that was always going to get rejected — this blocks it locally before the network call ever fires | FastAPI · Python · tiktoken |
| **[Structured Outputs (Groq)](https://github.com/Fuad-Haque/structured-outputs-groq)** | The gap between "asked the model for JSON" and "got JSON back" — strict schema mode closes that gap instead of parsing around it | Python · OpenAI SDK · Groq |
| **[Zod Runtime Validation — AI Ticket Triage](https://github.com/Fuad-Haque/zod-validation)** | Trusting the model's output the same way you'd trust a user's form input — this treats both as equally suspect, at three separate checkpoints | Express · Zod · Claude SDK |
| **[OpenAI Stream (FastAPI)](https://github.com/Fuad-Haque/openai-stream-fastapi)** | The client closes the tab, but the server keeps generating (and billing) anyway — this one notices and stops | FastAPI · OpenAI SDK · Groq |
| **[Anthropic SSE Streaming](https://github.com/Fuad-Haque/anthropic-sse-streaming)** | "It failed" isn't one error — a bad key, a rate limit, a dead network, and a disconnected client all need to be told apart, not lumped into one 500 | FastAPI · Anthropic SDK · asyncio |
| **[SSE Reconnect Demo](https://github.com/Fuad-Haque/sse-reconnect-demo)** | A dropped connection loses the client's place in the stream, unless the server can pick up from exactly where it left off | FastAPI · sse-starlette |
| **[Route Handlers vs Suspense Streaming](https://github.com/Fuad-Haque/rh-suspense-verify)** | Two things both called "streaming" in Next.js that don't share a single line of code — this keeps them apart on purpose so the difference is obvious | Next.js · React · TypeScript |
| **[useChat Streaming Chat](https://github.com/Fuad-Haque/usechat-straeming-chat)** | The assumption that a Vercel AI SDK frontend needs a Node backend — this hand-writes the wire protocol from Python and proves it doesn't | FastAPI · Next.js · `@ai-sdk/react` |
| **[Vercel AI SDK Streaming Patterns](https://github.com/Fuad-Haque/vercel-ai-sdk-streaming-patterns)** | Picking the wrong one of three response patterns is an easy mistake to make once — this puts all three side by side so the wrong pick is visibly wrong | Next.js · Vercel AI SDK · Zod |
| **[Provider Adapters](https://github.com/Fuad-Haque/provider-adapters)** | Locking a codebase to one LLM vendor by accident — swapping providers here is one environment variable, not a rewrite | Express · Vercel AI SDK |
| **[Tenacity Backoff & Retry Isolation](https://github.com/Fuad-Haque/tenacity-backoff-fastapi)** | Retry logic that looks correct but silently does nothing — four separate ways to misconfigure a retry, each shown breaking on its own | Python · tenacity |

Every repo above is cloneable and runs with the commands in its own README — none of them need a hidden config file or an undocumented step to get working.

---

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                  SYSTEM DESIGN READS ON                        -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 🧭 What the Pattern Across All of This Actually Is

Fourteen separate repos start to repeat themselves after a while. Here's what they keep repeating:

**Fails closed, not open.** The token guard blocks before the network call. The Zod triage rejects a bad merge before the database write. The provider adapter returns a typed `502` instead of quietly falling through to a broken response. Given the choice between "might reject something valid" and "might silently accept something broken," everything here picks the first one.

**Cost is a first-class variable, not a footnote.** Most of these repos treat "how much did that just cost" as a number you check after the fact. A few of these — the threshold guard, the four-bucket ledger — treat it as a number you check *before* deciding to make the call at all.

**A disconnect is a normal event, not an edge case.** Three separate repos exist because a client closing a tab mid-stream is treated, in a lot of code, as something that "shouldn't happen." It happens constantly. Detecting it and stopping cleanly is cheaper than pretending it won't.

**The wire format is the actual contract, not the SDK.** The useChat repo and both SSE repos exist because it's easy to treat a client library as the specification instead of reading what's actually being sent over the connection. Once you've hand-built the protocol once, every SDK afterward is legible instead of magic.

---

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                       CONTACT                                -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 📞 Reach Me

<div align="center">
  <a href="mailto:fuadhaque.dev@gmail.com">
    <img src="https://img.shields.io/badge/Email-fuadhaque.dev%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white" />
  </a>
  <a href="https://linkedin.com/in/fuadviews">
    <img src="https://img.shields.io/badge/LinkedIn-fuadviews-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" />
  </a>
  <a href="https://x.com/fuadviews">
    <img src="https://img.shields.io/badge/X-@fuadviews-000000?style=for-the-badge&logo=x&logoColor=white" />
  </a>
  <a href="https://wa.me/8801887885434">
    <img src="https://img.shields.io/badge/WhatsApp-01887885434-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" />
  </a>
  <a href="tel:+8801887885434">
    <img src="https://img.shields.io/badge/Mobile-01887885434-4CAF50?style=for-the-badge&logo=phone&logoColor=white" />
  </a>
  <a href="https://cal.com/fuad-haque/30min?user=fuad-haque&layout=mobile">
    <img src="https://img.shields.io/badge/Book_a_Call-30_Minutes-292929?style=for-the-badge&logo=calendly&logoColor=white" />
  </a>
  <a href="https://fuadhaque.com">
    <img src="https://img.shields.io/badge/Portfolio-fuadhaque.com-6C63FF?style=for-the-badge&logo=vercel&logoColor=white" />
  </a>
</div>

---

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                      TECH STACK                               -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 🛠️ Tech Stack

Grouped by how often it's in the loop, not by category — everything in the first group shows up in nearly every repo above; the second group is real production experience that comes up when the problem calls for it.

<div align="center">

### Daily Driver — in almost everything above

![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=next.js&logoColor=white)
![Anthropic SDK](https://img.shields.io/badge/Anthropic_SDK-191919?style=for-the-badge&logo=anthropic&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![Zod](https://img.shields.io/badge/Zod-3E67B1?style=for-the-badge&logo=zod&logoColor=white)

### Reached for When the Problem Needs It

![OpenAI SDK](https://img.shields.io/badge/OpenAI_SDK-412991?style=for-the-badge&logo=openai&logoColor=white)![Vercel AI SDK](https://img.shields.io/badge/Vercel_AI_SDK-000000?style=for-the-badge&logo=vercel&logoColor=white)
![Groq](https://img.shields.io/badge/Groq-F55036?style=for-the-badge&logoColor=white)
![Qdrant](https://img.shields.io/badge/Qdrant-DC244C?style=for-the-badge&logo=qdrant&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![WebSocket](https://img.shields.io/badge/WebSocket-010101?style=for-the-badge&logo=socket.io&logoColor=white)
![tiktoken](https://img.shields.io/badge/tiktoken-412991?style=for-the-badge&logo=openai&logoColor=white)
![tenacity](https://img.shields.io/badge/tenacity-3776AB?style=for-the-badge&logo=python&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=for-the-badge&logo=sqlalchemy&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)
![Neon](https://img.shields.io/badge/Neon-00E599?style=for-the-badge&logo=neon&logoColor=white)
![Upstash](https://img.shields.io/badge/Upstash-00E9A3?style=for-the-badge&logo=upstash&logoColor=white)
![React Query](https://img.shields.io/badge/React_Query-FF4154?style=for-the-badge&logo=reactquery&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![shadcn/ui](https://img.shields.io/badge/shadcn%2Fui-000000?style=for-the-badge&logo=shadcnui&logoColor=white)
![Recharts](https://img.shields.io/badge/Recharts-22B5BF?style=for-the-badge&logo=react&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=json-web-tokens&logoColor=white)
![slowapi](https://img.shields.io/badge/rate--limiting-slowapi-3C3C3D?style=for-the-badge)
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)
![Railway](https://img.shields.io/badge/Railway-0B0D0E?style=for-the-badge&logo=railway&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)
![Sentry](https://img.shields.io/badge/Sentry-362D59?style=for-the-badge&logo=sentry&logoColor=white)
![MCP](https://img.shields.io/badge/MCP-191919?style=for-the-badge&logo=anthropic&logoColor=white)
![instructor](https://img.shields.io/badge/instructor-000000?style=for-the-badge)

</div>

---

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                    GITHUB STATISTICS                          -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 🎓 Statistics

<div align="center">

<img height="165em" src="https://github-readme-stats-three-omega-56.vercel.app/api?username=Fuad-Haque&show_icons=true&hide_border=true&bg_color=0D1117&title_color=6C63FF&icon_color=00D4AA&text_color=E6E6EF&include_all_commits=true&count_private=true" />
<img height="165em" src="https://github-readme-stats-three-omega-56.vercel.app/api/top-langs/?username=Fuad-Haque&layout=compact&hide_border=true&bg_color=0D1117&title_color=6C63FF&text_color=E6E6EF&langs_count=8" />

</div>

<div align="center">

[![Activity Graph](https://github-readme-activity-graph.vercel.app/graph?username=Fuad-Haque&bg_color=0D1117&color=6C63FF&line=00D4AA&point=6C63FF&area=true&area_color=6C63FF&hide_border=true&custom_title=Commit+Activity)](https://github.com/ashutosh00710/github-readme-activity-graph)

</div>

---

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                    DEV JOKE / QUOTE                           -->
<!-- ═══════════════════════════════════════════════════════════════ -->

## 💬 One for the Road

<div align="center">

![Jokes Card](https://readme-jokes.vercel.app/api?hideBorder&bgColor=%230D1117&textColor=%23E6E6EF&qColor=%236C63FF&aColor=%2300D4AA&borderColor=%231E1E2E)

</div>

---

<!-- ═══════════════════════════════════════════════════════════════ -->
<!--                   SEARCH COMPARISON                            -->
<!-- ═══════════════════════════════════════════════════════════════ -->

<details>
<summary><b>🔍 Why the Semantic Search Platform Doesn't Just Do Keyword Matching</b></summary>

<br/>

Keyword search finds the words you typed. It cannot find the thing you meant unless you happened to type the exact right word for it. The table below is the same four queries run against a plain keyword index versus the hybrid RRF approach the live project actually uses.

| Query | Plain keyword match | Hybrid RRF (vector + keyword) |
|-------|---------------------|-------------------------------|
| `"invoice"` | Only documents containing the literal word "invoice" | Also surfaces billing, payments, receipts — anything semantically adjacent |
| `"slow response"` | Only documents with that literal phrase | Also surfaces latency, performance degradation, timeout reports |
| `"how do I cancel"` | Only documents with that exact phrasing | Also surfaces cancellation policy, refund process, account deletion flows |
| `"Python async code"` | Exact match only | Also surfaces asyncio, coroutines, `await` patterns, event loops |

The mechanism: every query runs through both a vector search (sentence-transformers embeddings, cosine similarity in Qdrant) and a keyword search (PostgreSQL full-text) at the same time. Reciprocal Rank Fusion then merges both ranked lists into one, instead of forcing a choice between the two approaches upfront.

</details>
