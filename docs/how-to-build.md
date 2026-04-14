# How to Make a CS2 Case Opening Simulator

The full breakdown of what goes into building an accurate case opening simulator.

I built [caseopeningsimulator.com](https://www.caseopeningsimulator.com) from scratch. Here are the real engineering decisions.

---

## Step 1: Understand the Drop System

Every weapon case in CS2 uses a fixed rarity distribution:

- **Mil-Spec (Blue):** 79.92%
- **Restricted (Purple):** 15.98%
- **Classified (Pink):** 3.20%
- **Covert (Red):** 0.64%
- **Rare Special Item / Knife (Gold):** 0.26%

These numbers are non-negotiable. Within each tier, every item has equal probability.

---

## Step 2: The Wear Problem

Every weapon skin has a float value (0–1) that maps to a condition. Don't use uniform distribution — real drops are skewed toward mid-tier.

Empirical data from CSFloat:

| Wear | Real Drop Rate |
|------|---------------|
| Factory New | ~3% |
| Minimal Wear | ~24% |
| Field-Tested | ~33% |
| Well-Worn | ~24% |
| Battle-Scarred | ~16% |

Using uniform distribution inflates ROI by ~15 percentage points.

Each skin also has a restricted float range. Filter impossible wears and re-normalize.

---

## Step 3: StatTrak and Doppler Phases

StatTrak: 10% chance on weapon cases, 0% on everything else. Roll after wear selection, use separate pricing.

Doppler phases are where it gets interesting. A "Karambit | Doppler" has 7 variants:

- Phase 1–4 (common, weight ~0.80 each)
- Ruby (rare, weight ~0.09)
- Sapphire (rare, weight ~0.09)
- Black Pearl (ultra-rare, weight ~0.02)

A Sapphire Karambit is ~$11,000 vs Phase 3 at ~$850. Store each phase as a separate item with its own weight and price, then split the 0.26% gold-tier odds proportionally.

---

## Step 4: Getting Real Prices

You need live market data from multiple sources:

- **Steam Community Market** — largest, most accurate for common items
- **Skinport** — fallback for items not listed on Steam
- **CSFloat** — Doppler phase-specific pricing

You need per-wear and per-phase prices. For [caseopeningsimulator.com](https://www.caseopeningsimulator.com), prices are baked into static JSON at build time — zero API latency during gameplay.

---

## Step 5: ROI and Expected Value

The formula for a weapon case:

```
item_EV = Σ (wear_probability × ((1 - 0.10) × normal_price + 0.10 × stattrak_price))
case_EV = Σ (item_odds × item_EV)
RTP = case_EV / (case_price + key_price) × 100%
```

For non-weapon containers: just odds × price.

Verified via 100,000-open Monte Carlo simulations across 14 case types — converges within 1–3 percentage points.

---

## Step 6: The Animation

CS2 uses a horizontal wheel that decelerates with cubic-bezier easing. The winner is pre-determined — placed at a specific strip position.

Key details:
- ~46 random items as visual filler
- Winner at position 41
- CSS transform with cubic-bezier timing
- Tick sounds during scroll, rarity-specific reveal sounds

---

## Step 7: Scale and Performance

100% static site generation. Every page is pre-rendered HTML served from an edge CDN. All simulation logic runs client-side.

470+ case pages load instantly because they're just static files.

---

## Final Thoughts

Getting the odds correct is ~20% of the work. The rest is wear distribution, Doppler phases, price aggregation, and ROI math.

Try it: [caseopeningsimulator.com](https://www.caseopeningsimulator.com)
