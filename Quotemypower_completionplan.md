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

---

## AVAILABLE AGENT ROSTER

### Morgan (Senior Product Manager)
**Focus:** Strategy, roadmaps, prioritization frameworks  
**Capabilities:** Business goals, epics/stories, KPI/OKR setup, cross-functional alignment  

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

---

## TOOLS AVAILABLE

- **Git/GitHub** – version control  
- **NVM for Windows (nvm4w)** → manage Node versions (`nvm use …`)  
- **Node.js 20.17.0 (LTS)** → JavaScript runtime (`node -v`)  
- **npm 10.9.x** → Node package manager (`npm -v`)  
- **pnpm 10.15.0 (via Corepack)** → fast alternative package manager (`pnpm -v`)  
- **Netlify CLI 23.4.x** → deploy + local dev for Netlify (`netlify --version`)  
- **Python 3.12.x** → general scripting (`python --version`)  
- **pip** → Python package manager (bundled with Python)  
- **Poetry** → Python dependency & env manager (`poetry --version`)  
- **pre-commit** → Git hook manager (`pre-commit --version`)  
- **Docker Desktop 28.3.3** → containers, local DBs, queues, etc. (`docker --version`)  
- **Playwright 1.55.0** → end-to-end browser testing (`playwright --version`)  
- **Lighthouse CI 0.15.1** → performance/SEO audits (`lhci --version`)  
- **axe CLI 4.10.2** → accessibility testing (`axe --version`)  
- **Snyk CLI 1.1298.3** → security scanning (`snyk --version`)  
- **Storybook CLI** → UI component sandbox (`npx storybook --version`)  
- **OWASP ZAP** → dynamic app security testing (GUI app, not CLI-only)  
- **Postman** → API testing (desktop app)  
- **ngrok** → expose local servers to the internet (`ngrok version`)  
- **DBeaver** → database GUI client (desktop app)  

**Global Node Helper Tools (via npm or Corepack):**  
- **Corepack** → manages pnpm/yarn/npm versions (`corepack enable`)  
- **npm-check-updates (ncu)** → upgrade dependencies (`ncu -u`)  
- **dotenv-cli** → load `.env` vars into commands (`dotenv -- command`)  
- **lockfile-lint** → validate lockfiles for security (`lockfile-lint`)  

---

## PHASE 1: CRITICAL PAYMENT & AUTHENTICATION SYSTEM

### Section 1.1: Payment Gateway Integration
- [ ] **1.1.1** Configure Stripe with production keys (one-time + subscriptions)  
- [ ] **1.1.2** Create products: EV-only, Solar-only, EV+Solar bundle; add-ons (site visit, expedite, custom engineering)  
- [ ] **1.1.3** Implement checkout → success/cancel flows; persist order intents  
- [ ] **1.1.4** Webhooks: on payment success/failure, upsert customer + entitlement state  
- [ ] **1.1.5** E2E tests for all tiers/add-ons/webhooks (happy + failure paths)  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** HIGH  

### Section 1.2: User Authentication
- [ ] **1.2.1** Contractor auth: email/password + OAuth (Google/MS)  
- [ ] **1.2.2** Homeowner auth-lite: email + magic link (optional account)  
- [ ] **1.2.3** JWT session for API routes; role claims (homeowner/contractor/admin)  
- [ ] **1.2.4** Access control guards on pages + APIs  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** HIGH  

---

## PHASE 2: DATA & PRICING ENGINE (in-repo)

### Section 2.1: Property Data Intake
- [ ] **2.1.1** Address lookup adapter (Regrid/ATTOM API)  
- [ ] **2.1.2** Homeowner Q&A wizard  
- [ ] **2.1.3** Photo upload + CV parsing  
- [ ] **2.1.4** NREL PVWatts adapter  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** HIGH  

### Section 2.2: Materials Pricing Engine
- [ ] **2.2.1** Baseline cost tables (RSMeans or supplier CSVs)  
- [ ] **2.2.2** Supplier APIs (Graybar, Home Depot Pro, Grainger)  
- [ ] **2.2.3** Contractor markup + margin rules  
- [ ] **2.2.4** Regional pricing modifiers by ZIP/utility  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** HIGH  

### Section 2.3: Labor & Incentives Engine
- [ ] **2.3.1** NECA labor units seeded  
- [ ] **2.3.2** Regional wages (BLS + IBEW locals)  
- [ ] **2.3.3** Incentives (DSIRE + utility rebates)  
- [ ] **2.3.4** Federal ITC 30% calculator  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** HIGH  

---

## PHASE 3: QUOTING ENGINE (in `/lib/quoting-engine/`)

### Section 3.1: EV Charger Quoting Module
- [ ] **3.1.1** Input normalization (`/lib/quoting-engine/input/ev.ts`)  
- [ ] **3.1.2** BOM generator (wire, conduit, charger, breakers)  
- [ ] **3.1.3** Labor + margin estimator (rules + overrides)  
- [ ] **3.1.4** Proposal composer (PDF/HTML)  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** HIGH  

### Section 3.2: Solar Quoting Module
- [ ] **3.2.1** Roof scan adapter (Google Sunroof/EagleView)  
- [ ] **3.2.2** Array layout + system sizing (kW, panel selection, inverter mapping)  
- [ ] **3.2.3** Savings + payback calculator (tariffs, net metering)  
- [ ] **3.2.4** Proposal with incentives (ITC, local rebates)  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** HIGH  

### Section 3.3: Bundle & Add-On Quotes
- [ ] **3.3.1** Bundle compositor (EV + Solar unified output)  
- [ ] **3.3.2** Add-ons: battery storage, MPU (main panel upgrade), trenching  
- [ ] **3.3.3** Contractor branding (logos, company info)  
- [ ] **3.3.4** eSignature + acceptance  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** MEDIUM  

### Section 3.4: Battery Quoting Module
- [ ] **3.4.1** Battery sizing (load profile, backup duration)  
- [ ] **3.4.2** Hybrid integration with solar (inverter compat, EMS flags)  
- [ ] **3.4.3** Battery incentives (stack with ITC/rebates)  
- [ ] **3.4.4** ROI/payback  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** MEDIUM  

---

## PHASE 4: DASHBOARDS

### Section 4.1: Homeowner Dashboard
- [ ] **4.1.1** Guided wizard (plain-English, tooltips)  
- [ ] **4.1.2** Visual breakdown (materials, labor, incentives)  
- [ ] **4.1.3** Savings projection (yearly & lifetime charts)  
- [ ] **4.1.4** CTA: “Book site visit” → scheduling (Calendly/Make)  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** MEDIUM  

### Section 4.2: Contractor Dashboard
- [ ] **4.2.1** Quote management (view/edit/approve)  
- [ ] **4.2.2** CRM integration (HubSpot/Zoho/Make)  
- [ ] **4.2.3** Analytics (win rate, avg quote, ROI)  
- [ ] **4.2.4** Team accounts (installers under org)  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** MEDIUM  

---

## PHASE 5: CUSTOMER COMMUNICATION SYSTEM

### Section 5.1: Notifications
- [ ] **5.1.1** Email/SMS estimate copy to homeowners  
- [ ] **5.1.2** Contractor lead/quote alerts  
- [ ] **5.1.3** Status updates: pending → revised → accepted  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** MEDIUM  

### Section 5.2: Support System
- [ ] **5.2.1** Homeowner FAQ (“What’s a breaker upgrade?”)  
- [ ] **5.2.2** Contractor docs (markup rules, CRM setup)  
- [ ] **5.2.3** Support ticket form  
- [ ] **5.2.4** Live chat (Intercom/Crisp)  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** LOW  

---

## PHASE 6: QUALITY ASSURANCE & LAUNCH

### Section 6.1: Testing
- [ ] **6.1.1** End-to-end: homeowner → quote → contractor acceptance → payment  
- [ ] **6.1.2** Scenarios: EV-only, Solar-only, Bundle, Battery add-on  
- [ ] **6.1.3** Multi-device testing  
- [ ] **6.1.4** Load test: 1,000 concurrent quote requests  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** HIGH  

### Section 6.2: Security & Compliance
- [ ] **6.2.1** PCI compliance (Stripe)  
- [ ] **6.2.2** GDPR/CCPA compliance  
- [ ] **6.2.3** OWASP checks on API routes  
- [ ] **6.2.4** Audit log for contractor edits  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** HIGH  

### Section 6.3: Launch Prep
- [ ] **6.3.1** Production deploy  
- [ ] **6.3.2** Monitoring + alerting  
- [ ] **6.3.3** Docs (contractor onboarding, homeowner guide)  
- [ ] **6.3.4** SSL, SEO, performance (LCP/TTFB budgets)  
- **Status:** UNASSIGNED – Emily to route  
- **Priority:** HIGH  

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

    PROJECT ROADMAP (Gantt Chart)
gantt
    title EV + Solar Quoting Platform Roadmap
    dateFormat  YYYY-MM-DD
    axisFormat  %b %d

    section Phase 1: Payment & Auth
    Payment Gateway Integration       :done,    p1a, 2025-09-04, 7d
    User Authentication               :active,  p1b, after p1a, 7d

    section Phase 2: Data & Pricing Engine
    Property Data Intake              :p2a, after p1b, 10d
    Materials Pricing Engine          :p2b, after p2a, 10d
    Labor & Incentives Engine         :p2c, after p2b, 7d

    section Phase 3: Quoting Engine
    EV Quoting Module                 :p3a, after p2c, 7d
    Solar Quoting Module              :p3b, after p3a, 10d
    Bundle & Add-Ons                  :p3c, after p3b, 5d
    Battery Quoting Module            :p3d, after p3c, 7d

    section Phase 4: Dashboards
    Homeowner Dashboard               :p4a, after p3a, 7d
    Contractor Dashboard              :p4b, after p3a, 7d

    section Phase 5: Communication
    Notifications                     :p5a, after p4a, 5d
    Support System                    :p5b, after p5a, 5d

    section Phase 6: QA & Launch
    Testing                           :p6a, after p5b, 10d
    Security & Compliance             :p6b, after p6a, 7d
    Launch Prep                       :p6c, after p6b, 7d

