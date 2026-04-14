# StatTrak™ & Doppler Mechanics

How the CS2 Case Opening Simulator handles StatTrak drops and Doppler knife phases.

---

## StatTrak™

- **Chance:** 10% per weapon case opening
- **Applies to:** Weapon cases only
- **Pricing:** StatTrak skins use separate (higher) market prices

```
1. Weapon skin selected from case
2. Wear condition rolled
3. 10% StatTrak roll
4. If StatTrak + skin has StatTrak pricing → use StatTrak price
```

---

## Doppler Phase System

Doppler knives have 7 variants with different weights and values:

| Phase | Relative Weight | Rarity |
|-------|----------------|--------|
| Phase 1 | 0.80 | Common |
| Phase 2 | 0.80 | Common |
| Phase 3 | 0.80 | Common |
| Phase 4 | 0.80 | Common |
| Ruby | 0.09 | Rare (~11x rarer than a normal phase) |
| Sapphire | 0.09 | Rare (~11x rarer than a normal phase) |
| Black Pearl | 0.02 | Ultra-rare (~40x rarer than a normal phase) |

### Price Differences

Using a Karambit Doppler as an example:

| Phase | Approximate Price |
|-------|-------------------|
| Phase 3 | ~$850 |
| Phase 1 | ~$900 |
| Phase 4 | ~$1,000 |
| Phase 2 | ~$1,100 |
| Black Pearl | ~$4,600 |
| Ruby | ~$8,200 |
| Sapphire | ~$11,100 |

Each Doppler phase is a separate item in the case data with its own odds and price. The 0.26% gold-tier odds are split proportionally by weight.

```
Each item's gold-tier share = its weight / sum of all gold weights
```

### Gamma Doppler

Same system, different finishes:
- Gamma Phase 1–4 (common)
- Emerald (rare, equivalent to Ruby/Sapphire)
- Black Pearl (ultra-rare)
