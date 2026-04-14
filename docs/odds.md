# Case Opening Odds

Complete rarity probabilities used in the CS2 Case Opening Simulator.

---

## Weapon Cases

| Rarity | Color | Probability |
|--------|-------|-------------|
| Mil-Spec Grade | Blue | 79.92% |
| Restricted | Purple | 15.98% |
| Classified | Pink | 3.20% |
| Covert | Red | 0.64% |
| Rare Special Item ★ | Gold | 0.26% |
| **Total** | | **100.00%** |

Within each rarity tier, every item has equal probability: `tier_odds / item_count_in_tier`.

---

## Sticker / Autograph / Graffiti / Music Kit / Patch Capsules

Same 1:5 ratio per tier. Capsules have 1–4 tiers depending on type. When tiers are absent, odds redistribute so the total sums to 100%.

### 4-tier capsules (57 capsules)

| Rarity | Color | Probability | Ratio to Next |
|--------|-------|-------------|---------------|
| High Grade | Blue | ~80.00% | 5:1 ↓ |
| Remarkable | Purple | ~16.00% | 5:1 ↓ |
| Exotic | Pink | ~3.20% | ~4:1 ↓ |
| Extraordinary | Red | ~0.80% | — |
| **Total** | | **100.00%** | |

### 3-tier capsules (48 capsules)

Blue / Purple / Pink or Blue / Purple / Red. Missing tier probability is absorbed into remaining tiers.

### 2-tier Holo/Foil capsules (30 capsules)

Tournament Holo/Foil capsules contain only Remarkable + Exotic tiers.

| Rarity | Color | Probability |
|--------|-------|-------------|
| Remarkable | Purple | ~83.33% |
| Exotic | Pink | ~16.67% |
| **Total** | | **100.00%** |

### 1-tier capsules (128 capsules)

Team-specific autograph capsules — all items are Blue-tier with equal probability.

### The 1:5 Ratio

```
P(tier N+1) = P(tier N) / 5

Weapon cases:  79.92 / 15.98 ≈ 5.0
4-tier sticker: 80.00 / 16.00 = 5.0
2-tier holo:    83.33 / 16.67 ≈ 5.0
Souvenirs:      80.00 / 16.00 = 5.0
```

---

## Souvenir Packages (6-tier)

Souvenir packages use a deeper rarity ladder:

| Rarity | Probability |
|--------|-------------|
| Consumer Grade | 80.00% |
| Industrial Grade | 16.00% |
| Mil-Spec Grade | 3.20% |
| Restricted | 0.640% |
| Classified | 0.128% |
| Covert | 0.0256% |
| **Total** | **99.99%** |

If a package doesn't have all 6 tiers, odds adjust to the tiers present.

---

## Pin Capsules

| Rarity | Color | Probability |
|--------|-------|-------------|
| Consumer Grade | Blue | 80.00% |
| Mil-Spec | Purple | 16.00% |
| Restricted | Pink | 3.20% |
| Classified | Red | 0.64% |
| Covert | Gold | 0.16% |

---

## Item Selection

```
1. Roll random number [0, 100)
2. Walk rarity tiers, subtracting each tier's probability
3. When roll falls within a tier → pick random item from that tier
```
