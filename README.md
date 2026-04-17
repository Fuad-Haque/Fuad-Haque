# Fuad Haque — Python Backend Engineer; specialized in Asynchronous Programming, Concurrency and API Engineering

I engineer production-grade FastAPI systems — async backends, webhook pipelines, and task automation for startups.


---

## Services

**Full-Stack Builds**
- Portfolio and personal branding sites for developers, designers, and freelancers
- SaaS landing pages with motion design and conversion-focused layout
- Interactive marketing microsites with Framer Motion polish

**Backend Systems**
- Production REST APIs with auth, rate limiting, and async task handling
- Webhook pipelines for Stripe, GitHub, and Shopify with HMAC verification and idempotency
- Background task systems with async queues, status polling, and progress tracking
- JWT/OAuth2 authentication flows with refresh token rotation
- Third-party integrations that don't break when the upstream service misbehaves

**Frontend for Existing Backends**
- UI layer for your already-deployed API — forms, auth flows, live data
- Design system implementation from Figma to Next.js
- Component libraries for developer tools and internal dashboards

Open to fixed-scope contracts and ongoing retainers.
Available for international clients via Upwork or direct.

---

## Tech Stack

<div align="center">

### Core Backend
![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![Starlette](https://img.shields.io/badge/Starlette-2B5B84?style=for-the-badge&logo=starlette&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-v2-E92063?style=for-the-badge&logo=pydantic&logoColor=white)
![asyncio](https://img.shields.io/badge/asyncio-3776AB?style=for-the-badge&logo=python&logoColor=white)

### Frontend
![Next.js](https://img.shields.io/badge/Next.js_16-000000?style=for-the-badge&logo=next.js&logoColor=white)
![React](https://img.shields.io/badge/React_18-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)
![Framer Motion](https://img.shields.io/badge/Framer_Motion-0055FF?style=for-the-badge&logo=framer&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)

### HTTP & Async
![httpx](https://img.shields.io/badge/httpx-0F2E3D?style=for-the-badge&logo=python&logoColor=white)
![aiofiles](https://img.shields.io/badge/aiofiles-FFD43B?style=for-the-badge&logo=python&logoColor=black)

### Database
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-async-D71F00?style=for-the-badge&logo=sqlalchemy&logoColor=white)
![Alembic](https://img.shields.io/badge/Alembic-306998?style=for-the-badge&logo=python&logoColor=white)

### Auth
![JWT](https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=json-web-tokens&logoColor=white)
![OAuth2](https://img.shields.io/badge/OAuth2-3C3C3D?style=for-the-badge&logo=oauth&logoColor=white)

### Deployment & CI
![Vercel](https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=node.js&logoColor=white)
![npm](https://img.shields.io/badge/npm-CB3837?style=for-the-badge&logo=npm&logoColor=white)
![Railway](https://img.shields.io/badge/Railway-0B0D0E?style=for-the-badge&logo=railway&logoColor=white)
![Render](https://img.shields.io/badge/Render-46E3B7?style=for-the-badge&logo=render&logoColor=black)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)

### Testing
![Pytest](https://img.shields.io/badge/Pytest-0A9EDC?style=for-the-badge&logo=pytest&logoColor=white)
![pytest-asyncio](https://img.shields.io/badge/pytest--asyncio-3776AB?style=for-the-badge&logo=python&logoColor=white)

</div>

---

## Specializations

### Backend Engineering
-Async request handling (non-blocking I/O with async/await across endpoints)
JWT authentication flow (token generation, hashing, expiry, and protected route middleware)
OAuth2 password flow implementation (scopes, bearer tokens, dependency injection)
HMAC signature verification (validating Stripe/GitHub/Shopify webhook payloads)
Idempotency pattern (preventing duplicate processing on retried webhook events)
Background task architecture (offloading work from the request cycle)
Status polling design (task state machine with client-side progress tracking)
Click tracking and link expiry (state management across CRUD operations)
Pydantic v2 schema design (request validation, response models, custom validators)

Frontend Engineering

Component architecture (splitting UI into reusable, typed components)
Client vs server component model (knowing when to use "use client")
Z-index and layering management at scale
Viewport-aware drag constraints
Keyboard event handling globally (keydown listeners)
SSR-safe browser API usage (wrapping window/document in useEffect)
Responsive design without a framework (pure breakpoint logic)
Performance-conscious animation (RAF-based cursor lerping)

Design Engineering

Design-to-code translation (converting a spec into pixel-perfect components)
Typography pairing (serif vs monospace contrast)
Color system design with CSS variables
Micro-interaction design (cursor states, hover shifts, entry animations)
Noise/grain texture implementation via SVG filters
Glassmorphism (backdrop-blur + low-opacity borders)
Spotlight/lighting effects with radial gradients

API Design

REST endpoint structuring (resource-based routing, HTTP verb semantics)
Dependency injection with FastAPI (Depends() for auth, DB sessions, shared logic)
OpenAPI documentation (auto-generated Swagger UI from type annotations)
Error response standardization (consistent shape across all failure modes)

Database

Async SQLAlchemy ORM (non-blocking DB queries in a FastAPI context)
Alembic migration workflow (schema versioning without manual SQL)
PostgreSQL in production (provisioned and connected on Railway/Render)

DevOps & Deployment

Git branching and pushing to remote
Vercel deployment pipeline (push → auto-deploy)
Railway deployment pipeline (environment variables, service provisioning, live logs)
Render deployment (cold start behavior, free tier limitations)
Multi-service production management (three independent APIs, each live)
npm dependency management
Local dev server workflow
Pytest async test suites (testing endpoints that depend on DB state and auth)

## GitHub Stats
<div align="center">
  <img height="160em" src="https://github-readme-stats.vercel.app/api?username=Fuad-Haque&show_icons=true&theme=github_dark&hide_border=true&bg_color=0D1117&title_color=38BDAE&icon_color=38BDAE" />
  <img height="160em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Fuad-Haque&layout=compact&theme=github_dark&hide_border=true&bg_color=0D1117&title_color=38BDAE" />
</div>

<div align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=YOUR_USERNAME&theme=github-dark&hide_border=true&background=0D1117&stroke=38BDAE&ring=38BDAE&fire=38BDAE&currStreakLabel=38BDAE" />
</div>

---

## Live Projects
- **[Personal Website](https://fuad-portfolio-website.vercel.app/)**
- **[URL Shortener API](https://web-production-5bd50.up.railway.app/docs)** — Full CRUD URL shortener with JWT auth, click tracking, and link expiry
- **[Webhook Handler](https://webhook-handler-production-99e2.up.railway.app/docs )** — Stripe/GitHub/Shopify event processor with HMAC verification and idempotency
- **[Task Automation API](https://task-automation-api-i90w.onrender.com/docs)** — Background task processing with status polling and progress tracking

---

## Contact
[![Email](https://img.shields.io/badge/Email-fuadhaque.dev%40gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:fuadhaque.dev@gmail.com)
[![GitHub](https://img.shields.io/badge/GitHub-YOUR_USERNAME-181717?style=flat-square&logo=github)](https://github.com/Fuad-Haque)
