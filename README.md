# Landspare — National Digital Platform for Land Governance

AI-powered digital platform for land records research, GIS cadastral analytics, policy impact ML prediction, and evidence-based governance.

*Built for SIH 2026 — Problem Statement PS SIH26019 — by Circuit Minds.*

## Overview

Landspare brings together India's fragmented land-records ecosystem (DILRMP, SVAMITVA, Bhoomi, Mahabhumi, Dharani, Bhulekh, and more) into a single console for policymakers, researchers, and citizens. It combines a GIS cadastral map viewer, an AI policy advisory engine, a machine-learning policy-impact simulator, an open dataset catalog, and a citizen-facing Khasra/ULPIN search into one application.

## Features

- **Executive Overview** — high-level KPIs and national land-governance summary
- **GIS Map Viewer** — interactive cadastral parcel mapping (Leaflet-based)
- **AI Policy Advisor** — generates evidence-based policy briefs via the Gemini API, with a domain-expert fallback when no API key is configured
- **Policy Impact ML** — simulates the effect of policy levers (stamp duty, drone survey coverage, fast-track tribunals, etc.) on litigation time, revenue, and tenure security
- **State Comparison Dashboard** — cross-state benchmarking of land governance indicators
- **Data Catalog** — open catalog of national and state land datasets with filtering
- **Research Portal** — curated resources for empirical land-policy research
- **OpenAPI Playground** — interactive explorer for the platform's REST endpoints
- **Citizen Khasra Search** — public search over cadastral parcels by Khasra number, ULPIN, or owner
- **Multi-language support** — UI translations via a built-in i18n layer

## Tech Stack

- React 19 + TypeScript
- Vite 8 (build/dev server) with Tailwind CSS 4
- Express (API server, `server.ts`)
- Leaflet (GIS mapping)
- Google Gemini API (`@google/genai`) for AI-generated policy content
- Bun-compatible lockfile (`bun.lock`); npm also works

## Project Structure

```
.
├── server.ts                  # Express API server + Vite middleware
├── index.html                 # App entry HTML
├── src/
│   ├── main.tsx                # React entry point
│   ├── App.tsx                  # Root component, tab/state orchestration
│   ├── index.css                 # Global styles
│   ├── types/landspare.ts         # Shared TypeScript types
│   ├── i18n/translations.ts        # Localized UI strings
│   ├── data/mockLandData.ts         # Mock cadastral parcels & datasets
│   └── components/
│       ├── Header.tsx
│       ├── ExecutiveOverview.tsx
│       ├── GISMapViewer.tsx
│       ├── AIPolicyAdvisor.tsx
│       ├── PolicyImpactML.tsx
│       ├── StateComparisonDashboard.tsx
│       ├── DataCatalog.tsx
│       ├── ResearchPortal.tsx
│       ├── OpenAPIPlayground.tsx
│       └── CitizenKhasraSearch.tsx
├── vite.config.ts
├── tsconfig.json
└── .env.example
```

## Getting Started

**Prerequisites:** Node.js (or Bun)

1. Install dependencies:
   ```bash
   npm install
   ```
2. Copy `.env.example` to `.env` and set your Gemini API key:
   ```bash
   cp .env.example .env
   ```
   ```
   GEMINI_API_KEY="your-gemini-api-key"
   ```
   The app runs without a key — AI-powered features fall back to a built-in domain-expert response engine.
3. Start the dev server:
   ```bash
   npm run dev
   ```
   The app serves at `http://localhost:3000`.

## Available Scripts

| Script | Description |
|---|---|
| `npm run dev` / `npm start` | Run the Express + Vite dev server |
| `npm run build` | Production build via Vite |
| `npm run preview` | Preview the production build |
| `npm run lint` | Type-check with `tsc --noEmit` |
| `npm run clean` | Remove build output |

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/ai/policy-brief` | Generate an AI policy recommendation brief |
| `POST` | `/api/ai/analyze-parcel` | Risk/title analysis for a land parcel |
| `GET` | `/api/v1/datasets` | Query the open land-dataset catalog |
| `POST` | `/api/v1/ml-predict` | Run the policy-impact ML simulation |

## License

Not specified.
