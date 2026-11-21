# KrishiShield AI

A full-stack climate intelligence platform for agricultural risk monitoring, built for the hackathon track **"Climate, Resource Infrastructure & Global Supply Resilience."**

## What it does

KrishiShield AI helps farmers, cooperatives, and policymakers understand climate-driven risks to agriculture through ten integrated modules:

1. **Overview Dashboard** — live weather, six risk indicators, interactive charts, and an agricultural region map.
2. **Climate Risk Intelligence** — real weather from the Open-Meteo API with flood, drought, heatwave, agricultural, power-shortage, and supply-chain risk scoring.
3. **Satellite Intelligence** — NDVI vegetation health and crop stress monitoring with a prepared Sentinel-2 integration point (clearly labeled simulated data until STAC credentials are added).
4. **Smart Agriculture** — crop-specific health and risk assessments with irrigation, fertilizer, and action recommendations.
5. **AI Farmer Advisor** — multilingual chat (English, Hindi, Kannada) with a rule-based knowledge engine that works without any external AI API key.
6. **AI Agent System** — five cooperating agents (Weather, Satellite, Crop, Disaster, Advisory) produce a combined risk report with live status updates.
7. **Climate Simulator** — adjust rainfall, temperature, drought duration, and power availability to model impact on crops, water, productivity, and supply chains.
8. **Disaster Alerts** — view alerts and submit community disaster reports that are saved to the database.
9. **Supply Chain Monitor** — sample market prices, transport route status, and supply disruption risk (clearly labeled sample data).
10. **Reports** — generate, save, and review combined climate + agricultural risk reports stored in the database.

## Technology

- **Frontend:** React + Vite + TypeScript + Tailwind CSS
- **Charts:** Recharts
- **Maps:** Leaflet + react-leaflet
- **Backend intelligence:** client-side modules (weather, risk, satellite, crop advisor, agents, simulator, market) — no Python server required in this deployment
- **Database:** Supabase (Postgres) — alerts, disaster reports, generated reports, and farm assessments are persisted with row-level security
- **Weather API:** Open-Meteo (free, no key required) with graceful simulated fallback when the API is unreachable

## Data honesty

- Weather data is **live** from Open-Meteo when the API responds, otherwise a clearly-labeled **simulated fallback** is used.
- NDVI values are **simulated** from a weather-derived vegetation model. A Sentinel-2 STAC integration point is prepared but not connected — no live satellite imagery is claimed.
- Market prices are **sample data** for demonstration, clearly labeled in the UI.

## Running locally

```bash
npm install
npm run dev
```

The app runs entirely in the browser. Supabase credentials are pre-configured in the environment. The database schema (alerts, disaster_reports, reports, farm_assessments) is created via a Supabase migration that runs automatically.

## Project structure

```
src/
  App.tsx              # Navigation + layout
  components/           # Sidebar, RegionMap, UI primitives
  lib/                  # Business logic (weather, risk, agents, etc.)
  pages/                # 10 module pages
supabase/
  migrations/           # Database schema
```

## Build

```bash
npm run build      # production build
npm run typecheck  # type checking
```
