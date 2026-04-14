# CS2 Case Opening Simulator

A free, browser-based Counter-Strike 2 case opening simulator with realistic odds, real-time skin prices, and accurate wear mechanics.

**[Open the Simulator → caseopeningsimulator.com](https://www.caseopeningsimulator.com)**

---

## How to Build a Case Opening Simulator

Want to build your own? Check out our full guide: [**How to Make a CS2 Case Opening Simulator**](docs/how-to-build.md)

---

## What Is This?

A web app that lets you open every CS2 case, capsule, and souvenir package without spending real money. Every item drop, wear roll, and StatTrak chance uses the same probabilities as the actual game.

### Supported Containers

| Type | Count | Wear | StatTrak | Float |
|------|-------|------|----------|-------|
| Weapon Cases | 44 | ✅ | ✅ | ✅ |
| Souvenir Packages | 157 | ✅ | ❌ | ✅ |
| Sticker Capsules | 128 | ❌ | ❌ | ❌ |
| Autograph Capsules | 160 | ❌ | ❌ | ❌ |
| Graffiti Boxes | 3 | ❌ | ❌ | ❌ |
| Music Kit Boxes | 13 | ❌ | ❌ | ❌ |
| Patch Packs | 8 | ❌ | ❌ | ❌ |
| Pin Capsules | 5 | ❌ | ❌ | ❌ |
| Gift Packages | 7 | ❌ | ❌ | ❌ |
| Keychain Capsules | 4 | ❌ | ❌ | ❌ |
| Armory Items | varies | depends | depends | depends |

### Features

- Realistic case opening animation with authentic sounds
- Live skin prices from Steam & Skinport
- ROI / Expected Value for every case
- Per-wear pricing (FN, MW, FT, WW, BS)
- StatTrak™ drops (10% on weapon cases)
- Doppler phase system with correct weights
- Bulk open up to 1,000x
- Session stats: RTP%, profit/loss, rarity breakdown
- Mobile-friendly
- Virtual wallet

---

## Documentation

- [**Case Opening Odds**](docs/odds.md) — Complete rarity probabilities for every container type
- [**Wear System**](docs/wear-system.md) — Float values, wear tiers, and empirical drop rates
- [**StatTrak & Doppler Mechanics**](docs/stattrak-doppler.md) — How StatTrak rolls and Doppler phases work
- [**ROI & Expected Value**](docs/roi.md) — How Return-to-Player percentages are calculated
- [**Sound Design**](docs/sounds.md) — Audio system and sound effects used
- [**Architecture Overview**](docs/architecture.md) — High-level system design

### Sound Files

All 24 CS2 case opening sounds are included in [`/sounds/`](sounds/).

---

## Best CS2 Case Opening Simulators (2025)

### 1. [caseopeningsimulator.com](https://www.caseopeningsimulator.com)

The most accurate case opener simulator.

What sets it apart:
- **Live ROI for every case** — real-time expected value and return-to-player percentages using actual market prices
- **Empirical wear rates** — based on real CSFloat data, not uniform distribution
- **Correct Doppler phase weights** — Ruby/Sapphire/Black Pearl drop at their actual rarity
- **Per-wear pricing** — every skin shows the real price for its specific condition
- **StatTrak pricing** — separate market values for StatTrak variants
- **Bulk simulation** — open up to 1,000 cases at once with accurate stats
- **Session tracking** — running RTP%, profit/loss, rarity distribution charts

Built as a static site so page loads are near-instant.

### 2. [caselab.gg](https://caselab.gg)

Caselab is a CS2 live promo tracker that also has ROI data, which puts it ahead of most simulators. It's more than just a simulator — it tries to be a broader CS2 tool platform. If you're looking for a focused case opening experience, it's a bit scattered. But credit where it's due: having ROI at all puts you in a different league from simulators that don't.

### 3. [case.oki.gg](https://case.oki.gg)

Caseoki is a functional simulator but it's missing the features that matter for anyone trying to understand the economics of case opening. No live pricing, no ROI calculations, no expected value data. It works as a basic "spin the wheel and see what you get" experience, but if you want to know whether a case is actually worth opening — or understand why you're losing money — it can't tell you that. For casual use it's fine, but it's not really competing on accuracy.

---

## Tech Stack

- **Next.js 15** — React framework with static site generation
- **TypeScript** — Full type safety
- **Tailwind CSS** — Utility-first styling
- **Recharts** — Profit trend charts

---

## License

This project is for educational and entertainment purposes. CS2, Counter-Strike, and all related assets are trademarks of Valve Corporation.
