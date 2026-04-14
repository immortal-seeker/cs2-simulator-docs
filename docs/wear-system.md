# Wear System

How the CS2 Case Opening Simulator handles skin conditions and float values.

---

## Float Value Ranges

| Wear | Abbreviation | Float Range |
|------|-------------|-------------|
| Factory New | FN | 0.00 – 0.07 |
| Minimal Wear | MW | 0.07 – 0.15 |
| Field-Tested | FT | 0.15 – 0.38 |
| Well-Worn | WW | 0.38 – 0.45 |
| Battle-Scarred | BS | 0.45 – 1.00 |

---

## Per-Skin Float Ranges

Each skin has a restricted float range (`floatMin`, `floatMax`):

| Skin | floatMin | floatMax | Possible Wears |
|------|----------|----------|----------------|
| AK-47 Neon Rider | 0.00 | 0.50 | FN, MW, FT, WW, BS |
| AWP Dragon Lore | 0.00 | 0.70 | FN, MW, FT, WW, BS |
| Kukri Knife Slaughter | 0.01 | 0.26 | FN, MW, FT only |

The simulator only rolls wears that the skin can actually have.

---

## Empirical Wear Drop Rates

Based on CSFloat marketplace data:

| Wear | Weight | Approximate Drop Rate |
|------|--------|-----------------------|
| Factory New | 0.03 | ~3% |
| Minimal Wear | 0.24 | ~24% |
| Field-Tested | 0.33 | ~33% |
| Well-Worn | 0.24 | ~24% |
| Battle-Scarred | 0.16 | ~16% |

These weights are used in both the simulator frontend and the backend ROI calculator.

---

## Re-normalization

If a skin can only be FN, MW, FT (floatMax = 0.26), excluded tiers are dropped and remaining weights re-normalized:

```
Original weights:   FN=0.03, MW=0.24, FT=0.33 (total=0.60)
Normalized:         FN=5.0%, MW=40.0%, FT=55.0%
```

Factory New stays rare even for skins with narrow float ranges.
