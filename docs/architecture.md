# Architecture Overview

High-level system design of the CS2 Case Opening Simulator.

---

## System Components

```
┌─────────────────────────────────────────────────┐
│                   Frontend                       │
│              (Next.js 15 + React)                │
│                                                  │
│  Static HTML pages (SSG)                         │
│  Case opening UI + animations                    │
│  Client-side simulation logic                    │
│  Virtual wallet system                           │
│  Session stats tracking                          │
│                                                  │
│  Reads from: static JSON files at build time     │
│  Image CDN: Steam Community + Cloudflare R2      │
│  Hosted on: Vercel                               │
└──────────────────────┬──────────────────────────┘
                       │ build-time only
                       ▼
┌─────────────────────────────────────────────────┐
│                 Skin Prices API                   │
│                                                  │
│  Live skin price aggregation                     │
│  ROI / Expected Value pre-computation            │
│  Price endpoints for build enrichment            │
└─────────────────────────────────────────────────┘
```

---

## Data Flow

```
1. Backend scrapes prices from Steam, Skinport, CSFloat
2. Prices stored in a database
3. Bake script reads API → enriches static JSON files with per-wear prices
4. Next.js builds all pages as static HTML (SSG)
5. Vercel serves the static site
6. All simulation logic runs client-side in the browser
7. No server requests during case opening — everything is local
```

---

## Key Design Decisions

### 100% Static Site (SSG)

Every page is pre-rendered at build time. No server-side rendering, no API calls during gameplay.

### Client-Side Simulation

Case opening logic runs in the browser using pre-baked JSON data.

### Price Pipeline

```
Steam/Skinport/CSFloat → Database → Bake Script → Static JSON → Browser
```

---

## Container Categories

The simulator handles 11+ container types, each with different behavior:

| Behavior | Weapon Cases | Souvenirs | Stickers/Capsules | Pins |
|----------|-------------|-----------|-------------------|------|
| Rarity tiers | 5 (+ gold) | 6 | 4 (+ gold) | 5 |
| Wear system | ✅ | ✅ | ❌ | ❌ |
| StatTrak | ✅ (10%) | ❌ | ❌ | ❌ |
| Key cost | $2.49 | $0 | $0 | $0 |
| Per-wear pricing | ✅ | ✅ | ❌ | ❌ |

---

## Image Sources

Most skin and sticker images are available for free from Steam's Akamai CDN:

```
https://community.akamai.steamstatic.com/economy/image/<hash>
```

Each item in the Steam economy has a unique image hash. You can get these from the Steam API or community market listings. No authentication required — they're public CDN URLs.

**Doppler phase images** are the exception. Steam doesn't serve separate images per Doppler phase — a "Karambit | Doppler" returns the same generic image whether it's a $850 Phase 3 or an $11,000 Sapphire. You'll need to source phase-specific images separately.

All 176 Doppler knife images are included in this repo under [`/images/cs2-doppler-knives-caseopeningsimulator/`](../images/cs2-doppler-knives-caseopeningsimulator/). Covers every knife × every phase (Phase 1–4, Ruby, Sapphire, Black Pearl, Emerald).
