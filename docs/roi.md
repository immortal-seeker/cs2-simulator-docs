# ROI & Expected Value

How the CS2 Case Opening Simulator calculates Return-to-Player percentages and expected value for every case.

---

## What Is ROI / RTP?

- **EV:** Average dollar value per opening
- **RTP:** `(EV / total_cost) × 100%`

RTP of 55% = ~$0.55 back per $1.00 spent.

---

## Formula

### Weapon Cases

```
EV = Σ over all items (item_odds × item_expected_value)

item_EV = Σ over wears (wear_probability × (
    (1 - stattrak_chance) × normal_price
  + stattrak_chance × stattrak_price
))

total_cost = case_price + key_price ($2.49)
RTP% = (EV / total_cost) × 100
```

### Non-Weapon Containers (Stickers, Pins, etc.)

```
EV = Σ (item_odds × item_value)
RTP% = (EV / capsule_price) × 100
```

No key price, no wear calculation, no StatTrak.

---

## Worked Example — Kilowatt Case

```
Case: $0.46 + Key: $2.49 = $2.95 total
10,000 openings: $29,500 spent → ~$16,500 won → ~55.9% RTP
```

> Most simulators don't calculate per-wear EV with StatTrak weighting. Our formula accounts for every wear tier price and the 10% StatTrak multiplier.

---

## Monte Carlo Verification

100,000-open simulations across 14 case types:

| Case | Type | Sim RTP | Backend ROI | Delta |
|------|------|---------|-------------|-------|
| Kilowatt Case | Weapon | 55.2% | 55.6% | –0.4pp |
| Chroma 2 Case | Weapon | 69.3% | 67.6% | +1.7pp |
| Revolution Case | Weapon | 68.6% | 67.1% | +1.5pp |
| Dreams & Nightmares | Weapon | 52.0% | 51.3% | +0.7pp |
| Gallery Case | Weapon | 51.1% | 50.3% | +0.8pp |
| CS:GO Weapon Case | Weapon | 129.0% | 130.5% | –1.5pp |
| CS20 Case | Weapon | 85.2% | 83.9% | +1.3pp |
| Paris 2023 Legends | Sticker | 86.2% | — | — |
| Antwerp 2022 Autograph | Autograph | 212.8% | — | — |
| Community Graffiti Box | Graffiti | 174.2% | — | — |
| Half-Life: Alyx Pin | Pins | 141.1% | — | — |
| Masterminds Music Kit | Music Kit | 73.5% | — | — |
| Paris 2023 Nuke Souvenir | Souvenir | 120.1% | — | — |
| Stockholm 2021 Patches | Patch | 67.6% | — | — |

All weapon cases converge within 1–3 percentage points of backend ROI.

---

## Price Sources

| Source | Priority |
|--------|----------|
| Steam Community Market | 1st |
| Skinport | 2nd (fallback) |
| CSFloat | 3rd (Doppler phases) |
