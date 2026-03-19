# Chart Aggregator - Personal TODO List

This document tracks completed milestones and outlines the remaining actionable items for the Chart Aggregator project based on the PMLC, JTBD, and TOS-compliant Tech Stack constraints.

## Phase 1: Ideation & Research (Active)
- [x] Adopt JTBD framework and break down the "Chart finding" user struggles.
- [x] Define 7 PMLC phases in `PMLC.md`.
- [x] Setup basic README architecture.
- [x] Draft `survey_draft.md` to validate assumptions with users.
- [ ] Send out Google Form survey, collect responses, and synthesize results.

## Phase 2: Value Proposition & Tech Stack Definition
- [ ] Select Next.js + Vanilla CSS for the free-tier UI.
- [ ] Define Supabase (PostgreSQL) as the database.
- [ ] Define Upstash (Redis) for real-time VATSIM cache.
- [ ] Define the TOS-Compliant Architecture (Indexing & Direct Linking, NO scraping/hosting charts).
- [ ] Create a "Pains vs. Relievers" table comparing against existing tools (e.g., ChartFox, Navigraph).

## Phase 3: Prototype (POC) - The Minimally Functional Logic
- [ ] Generate static `mock-airports.json` for initial UI testing and schema validation.
- [ ] Connect `mock-airports.json` to a basic Next.js layout.
- [ ] Verify the UI successfully displays the links grouped by Categories (STAR, SID, APP, GEN, ARR).
- [ ] Verify outbound direct `target="_blank"` routing to AAI eAIP.
- [ ] Build a Python/Next.js script to pull and parse the live VATSIM API data.
- [ ] Map the live VATSIM data onto the mock airports in the UI to confirm feasibility.

## Phase 4: Design & Architecture (Blueprint)
- [ ] Create Mermaid.js user flow diagrams reflecting the true "Directory/Index" path.
- [ ] Migrate `mock-airports.json` over to the true Supabase PostgreSQL schema.
- [ ] Set up `CONTRIBUTORS.md` using RACI Matrix.

## Phase 5: Build
- [ ] Develop the robust Next.js App Router structure.
- [ ] Implement search/filter logic for airports and charts querying the Supabase db.
- [ ] Implement VATSIM or Discord OAuth through Supabase Auth to mitigate account creation fatigue.
- [ ] Add the Upstash Redis caching layer for the VATSIM data stream.
- [ ] Finalize a sleek, glassmorphism UI using Vanilla CSS.

## Phase 6 & 7: Launch & Iterate
- [ ] Deploy to Vercel (Hobby tier).
- [ ] Solicit feedback from Discord aviation groups.
- [ ] Add additional countries/AIPs to the database safely.
