# EV + Solar Quoting Platform Completion Plan (Monorepo)

**Objective:** Launch a fully functional SaaS platform that generates instant, automated quotes for EV chargers + solar (and batteries) for both contractors and homeowners — with the quoting engine built **inside** the website repo.

**Working Directory (single repo):**
- Website + Quoting Engine: `C:\Users\Ben\OneDrive\Documents\GitHub\Quotemypower`
  - `/lib/quoting-engine/` (core engine, pricing rules, data adapters)
  - `/pages/` (Next.js app: homeowner + contractor flows)
  - `/pages/api/` (API routes; thin controllers delegating to `/lib/quoting-engine`)
  - `/lib/integrations/` (external APIs: property, roof, incentives, suppliers)
  - `/lib/data/` (defaults, tables, schemas)
  - `/components/` (UI building blocks)
  - `/scripts/` (data loaders, test fixtures, seeders)

## AVAILABLE AGENT ROSTER

### Morgan (Senior Product Manager)
**Focus:** Strategy, roadmaps, prioritization frameworks
**Capabilities:** Business goals  epics/stories, KPI/OKR setup, cross-functional alignment

### Casey (Senior UX Designer)
**Focus:** Research, personas, journey maps, wireframes, prototypes  
**Capabilities:** User flows, information architecture, usability testing  

### Jules (Senior UI & Design Systems Specialist)
**Focus:** Design tokens, component libraries, visual hierarchy  
**Capabilities:** High-fidelity screens, motion specs, accessibility  

### Riley (Senior Frontend Engineer)
**Focus:** React/Next.js + TypeScript, high-end interfaces  
**Capabilities:** State management, accessibility-first UI, performance optimization  

### Shane (Senior Backend Developer)
**Focus:** Server-side systems, APIs, databases  
**Capabilities:** REST/GraphQL design, authentication, business logic, webhooks  

### Alex (Senior Full-Stack Engineer)
**Focus:** Bridges FE/BE to ship features fast  
**Capabilities:** React + Node.js, Stripe integrations, end-to-end features  

### Quinn (Senior DevOps & Security Engineer)
**Focus:** CI/CD, security, stability and scale  
**Capabilities:** GitHub Actions, secrets management, monitoring  

### Taylor (Senior QA Engineer)
**Focus:** Automation and reliability testing  
**Capabilities:** Playwright/Cypress E2E, performance baselines  

### Hudson (AI/ML Systems Architect)
**Focus:** AI model integration, quoting engine intelligence, system scalability  
**Capabilities:** Model training & tuning, API orchestration, data pipelines, ML ops  

### Atlas (SEO Strategist)
**Focus:** Technical SEO, content strategy, competitive analysis  
**Capabilities:** Directory research, keyword mapping, content optimization  

### Cora (QA Auditor)
**Focus:** End-to-end reviews, compliance, final validation  
**Capabilities:** HTML/CSS validation, accessibility standards, launch readiness  

Available tools:
- **Git/GitHub** version control  
- **NVM for Windows (nvm4w)** manage Node versions (`nvm use `)  
- **Node.js 20.17.0 (LTS)** JavaScript runtime (`node -v`)  
- **npm 10.9.x** Node package manager (`npm -v`)  
- **pnpm 10.15.0 (via Corepack)** fast alternative package manager (`pnpm -v`)  
- **Netlify CLI 23.4.x** deploy + local dev for Netlify (`netlify --version`)  
- **Python 3.12.x** general scripting (`python --version`)  
- **pip** python package manager (bundled with Python)  
- **Poetry** Python dependency & env manager (`poetry --version`)  
- **pre-commit** Git hook manager (`pre-commit --version`)  
- **Docker Desktop 28.3.3** containers, local DBs, queues, etc. (`docker --version`)  
- **Playwright 1.55.0** end-to-end browser testing (`playwright --version`)  
- **Lighthouse CI 0.15.1** performance/SEO audits (`lhci --version`)  
- **axe CLI 4.10.2** accessibility testing (`axe --version`)  
- **Snyk CLI 1.1298.3** ecurity scanning (`snyk --version`)  
- **Storybook CLI** UI component sandbox (`npx storybook --version`)  
- **OWASP ZAP**dynamic app security testing (GUI app, not CLI-only)  
- **Postman** API testing (desktop app)  
- **ngrok** expose local servers to the internet (`ngrok version`)  
- **DBeaver** database GUI client (desktop app)  

**Global Node Helper Tools (via npm or Corepack):**  
- **Corepack** manages pnpm/yarn/npm versions (`corepack enable`)  
- **npm-check-updates (ncu)** upgrade dependencies (`ncu -u`)  
- **dotenv-cli** load `.env` vars into commands (`dotenv -- command`)  
- **lockfile-lint** validate lockfiles for security (`lockfile-lint`)  


## PHASE 1: CRITICAL PAYMENT & AUTHENTICATION SYSTEM

### Section 1.1: Payment Gateway Integration
- [ ] **1.1.1** Configure Stripe with production keys (one-time + subscriptions)  
  - Tools: **Postman** for webhook tests, **DBeaver** for verifying DB inserts  
- [ ] **1.1.2** Create products: EV-only, Solar-only, EV+Solar bundle; add-ons (site visit, expedite, custom engineering)  
  - Tools: **Stripe Dashboard**, **dotenv-cli** for secret key injection  
- [ ] **1.1.3** Implement checkout → success/cancel flows; persist order intents  
  - Tools: **Playwright** for flow testing  
- [ ] **1.1.4** Webhooks: on payment success/failure, upsert customer + entitlement state  
  - Tools: **ngrok** for local webhook replay  
- [ ] **1.1.5** E2E tests for all tiers/add-ons/webhooks (happy + failure paths)  
  - Tools: **Playwright**, **Postman collections**  

### Section 1.2: User Authentication
- [ ] **1.2.1** Contractor auth: email/password + OAuth (Google/MS)  
  - Tools: **Docker** (local auth DB), **Playwright** (login flows)  
- [ ] **1.2.2** Homeowner auth-lite: email + magic link (optional account)  
  - Tools: **Postman** (token API tests), **DBeaver** (verify users table)  
- [ ] **1.2.3** JWT session for API routes; role claims (homeowner/contractor/admin)  
  - Tools: **OWASP ZAP** for token/session testing  
- [ ] **1.2.4** Access control guards on pages + APIs  
  - Tools: **axe CLI** for access UX validation  

---

## PHASE 2: DATA & PRICING ENGINE (in-repo)

### Section 2.1: Property Data Intake
- [ ] **2.1.1** Address lookup adapter (Regrid/ATTOM API)  
  - Tools: **Postman** (API testing), **Docker** for mock API fallback  
- [ ] **2.1.2** Homeowner Q&A wizard  
  - Tools: **Storybook CLI** for form UI, **Playwright** for validation testing  
- [ ] **2.1.3** Photo upload + CV parsing  
  - Tools: **Python/Poetry** for ML scripts, **Docker** for OpenCV container  
- [ ] **2.1.4** NREL PVWatts adapter  
  - Tools: **Postman** (API validation)  

### Section 2.2: Materials Pricing Engine
- [ ] **2.2.1** Baseline cost tables (RSMeans or supplier CSVs)  
  - Tools: **DBeaver** for import checks, **Python/pandas** for data prep  
- [ ] **2.2.2** Supplier APIs (Graybar, Home Depot Pro, Grainger)  
  - Tools: **Postman** for auth + rate limit tests  
- [ ] **2.2.3** Contractor markup + margin rules  
  - Tools: **Storybook CLI** for admin UI controls  
- [ ] **2.2.4** Regional pricing modifiers by ZIP/utility  
  - Tools: **Docker + local DB** for region tables  

### Section 2.3: Labor & Incentives Engine
- [ ] **2.3.1** NECA labor units seeded  
  - Tools: **Python/Poetry**, **DBeaver** for verification  
- [ ] **2.3.2** Regional wages (BLS + IBEW locals)  
  - Tools: **pip** scripts for scraping, **Docker** container for wage data  
- [ ] **2.3.3** Incentives (DSIRE + utility rebates)  
  - Tools: **Postman** for API, **Docker** for cron ingestion  
- [ ] **2.3.4** Federal ITC 30% calculator  
  - Tools: **Playwright** for validation across test scenarios  

---

## PHASE 3: QUOTING ENGINE (in `/lib/quoting-engine/`)

### Section 3.1: EV Charger Quoting Module
- [ ] **3.1.1** Input normalization (`/lib/quoting-engine/input/ev.ts`)  
- [ ] **3.1.2** BOM generator (wire, conduit, charger, breakers) → `.../ev/bom.ts`  
- [ ] **3.1.3** Labor + margin estimator (rules + overrides) → `.../ev/costing.ts`  
- [ ] **3.1.4** Proposal composer (PDF/HTML) → `.../proposals/ev-proposal.ts`  
- Tools: **Storybook CLI**, **Playwright**, **DBeaver**  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** HIGH  

### Section 3.2: Solar Quoting Module
- [ ] **3.2.1** Roof scan adapter (Google Sunroof/EagleView) → `/lib/integrations/roof.ts`  
- [ ] **3.2.2** Array layout + system sizing (kW, panel selection, inverter mapping) → `.../solar/design.ts`  
- [ ] **3.2.3** Savings + payback calculator (tariffs, net metering) → `.../solar/economics.ts`  
- [ ] **3.2.4** Proposal with incentives (ITC, local rebates) → `.../proposals/solar-proposal.ts`  
- Tools: **Docker**, **Postman**, **Lighthouse CI**  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** HIGH  

### Section 3.3: Bundle & Add-On Quotes
- [ ] **3.3.1** Bundle compositor (EV + Solar unified output) → `.../bundle/combine.ts`  
- [ ] **3.3.2** Add-ons: battery storage, MPU (main panel upgrade), trenching → `.../addons/*.ts`  
- [ ] **3.3.3** Contractor branding (logos, company info) → `.../proposals/branding.ts`  
- [ ] **3.3.4** eSignature + acceptance → `/pages/api/sign/*` + `/components/signing/*`  
- Tools: **Storybook CLI**, **Playwright**  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** MEDIUM  

### Section 3.4: Battery Quoting Module
- [ ] **3.4.1** Battery sizing (load profile, backup duration) → `.../battery/sizing.ts`  
- [ ] **3.4.2** Hybrid integration with solar (inverter compat, EMS flags) → `.../battery/integration.ts`  
- [ ] **3.4.3** Battery incentives (stack with ITC/rebates) → `.../battery/incentives.ts`  
- [ ] **3.4.4** ROI/payback → `.../battery/economics.ts`  
- Tools: **Python/Poetry**, **Docker**  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** MEDIUM  

---

## PHASE 4: DASHBOARDS

### Section 4.1: Homeowner Dashboard
- [ ] **4.1.1** Guided wizard (plain-English, tooltips) → `/pages/quote/*`  
- [ ] **4.1.2** Visual breakdown (materials, labor, incentives) → `/components/estimates/*`  
- [ ] **4.1.3** Savings projection (yearly & lifetime charts)  
- [ ] **4.1.4** CTA: “Book site visit” → scheduling (Calendly/Make) → `/lib/integrations/scheduling.ts`  
- Tools: **Storybook CLI**, **axe CLI**  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** MEDIUM  

### Section 4.2: Contractor Dashboard
- [ ] **4.2.1** Quote management (view/edit/approve) → `/pages/contractor/quotes/*`  
- [ ] **4.2.2** CRM integration (HubSpot/Zoho/Make) → `/lib/integrations/crm/*`  
- [ ] **4.2.3** Analytics (win rate, avg quote, ROI) → `/pages/contractor/analytics`  
- [ ] **4.2.4** Team accounts (installers under org) → org/roles tables + guards  
- Tools: **Storybook CLI**, **DBeaver**, **Lighthouse CI**  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** MEDIUM  

---

## PHASE 5: CUSTOMER COMMUNICATION SYSTEM

### Section 5.1: Notifications
- [ ] **5.1.1** Email/SMS estimate copy to homeowners  
- [ ] **5.1.2** Contractor lead/quote alerts  
- [ ] **5.1.3** Status updates: pending → revised → accepted  
- Tools: **Postman**, **Docker**  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** MEDIUM  

### Section 5.2: Support System
- [ ] **5.2.1** Homeowner FAQ (“What’s a breaker upgrade?”)  
- [ ] **5.2.2** Contractor docs (markup rules, CRM setup)  
- [ ] **5.2.3** Support ticket form  
- [ ] **5.2.4** Live chat (Intercom/Crisp)  
- Tools: **Storybook CLI**, **Playwright**  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** LOW  

---

## PHASE 6: QUALITY ASSURANCE & LAUNCH

### Section 6.1: Testing
- [ ] **6.1.1** End-to-end: homeowner → quote → contractor acceptance → payment  
  - Tools: **Playwright**, **Postman**  
- [ ] **6.1.2** Scenarios: EV-only, Solar-only, Bundle, Battery add-on  
  - Tools: **Docker**, seeded fixtures  
- [ ] **6.1.3** Multi-device testing  
  - Tools: **Playwright device emulation**  
- [ ] **6.1.4** Load test: 1,000 concurrent quote requests  
  - Tools: **Dockerized locust.io/k6**, **Netlify CLI logs**  

### Section 6.2: Security & Compliance
- [ ] **6.2.1** PCI compliance (Stripe)  
  - Tools: **OWASP ZAP**, **Postman**  
- [ ] **6.2.2** GDPR/CCPA compliance  
  - Tools: **DBeaver** for DB audits  
- [ ] **6.2.3** OWASP checks on API routes  
  - Tools: **Snyk CLI**  
- [ ] **6.2.4** Audit log for contractor edits  
  - Tools: **Docker + DBeaver**  

### Section 6.3: Launch Prep
- [ ] **6.3.1** Production deploy  
  - Tools: **Netlify CLI**, **ngrok** for staging previews  
- [ ] **6.3.2** Monitoring + alerting  
  - Tools: **Docker** for simulating errors, Sentry/Datadog integration  
- [ ] **6.3.3** Docs (contractor onboarding, homeowner guide)  
  - Tools: **Storybook CLI**  
- [ ] **6.3.4** SSL, SEO, performance (LCP/TTFB budgets)  
  - Tools: **Lighthouse CI**, **axe CLI**  

---

## LAUNCH CRITERIA
- [ ] Payments functional (one-time + subscriptions)  
- [ ] Homeowner can self-generate EV/Solar/Battery quote in < 5 minutes  
- [ ] Contractor dashboard: manage/edit/export proposals  
- [ ] 100% unit coverage on `/lib/quoting-engine/` rules & calculators  
- [ ] Security audit passed  
- [ ] 50+ contractors onboarded  

---

## SYSTEM ARCHITECTURE DIAGRAM (Monorepo)

```mermaid
flowchart TD
    subgraph Repo["ElectroQuoteAI (monorepo)"]
      subgraph Intake["Input Modules"]
        A1[Homeowner Wizard /pages/quote/*]
        A2[Contractor CRM /lib/integrations/crm/*]
        A3[External APIs\nProperty/Roof/Incentives/Suppliers\n/lib/integrations/*]
      end

      subgraph Engine["/lib/quoting-engine"]
        B1[Pricing Rules /rules/*]
        B2[Proposal Builder /proposals/*]
        B3EV[EV Module /ev/*]
        B3SOLAR[Solar Module /solar/*]
        B3BAT[Battery Module /battery/*]
      end

      subgraph UI["Presentation & APIs"]
        C1[Homeowner Dashboard /pages/quote/*]
        C2[Contractor Dashboard /pages/contractor/*]
        C3[API Routes /pages/api/*]
        C4[PDF Exports /lib/quoting-engine/proposals/*]
      end

      Intake --> Engine
      Engine --> UI
    end
