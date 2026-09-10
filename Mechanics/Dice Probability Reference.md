---
description: The vault's single probability reference — DC-first success odds, per-die detail, degrees of success, opposed-roll odds, multi-die pools, and methodology.
tags: [mechanics, meta]
---

# Dice Probability Reference

This note gives the roll-outcome math behind [Dice and Rolls](../Mechanics/Questing%20Time!%20Mechanics.md#dice-and-rolls). It uses this vault's actual house rules, not generic dice math:

- **Exploding**: on the vault's rule, rolling the max value adds it and rolls again, repeating until a non-max value stops the chain.
- **Advantage / Disadvantage**: per [Dice and Rolls](../Mechanics/Questing%20Time!%20Mechanics.md#dice-and-rolls), you roll twice, "resolving each pool's explosions fully," then take the higher (advantage) or lower (disadvantage) total. So advantage and disadvantage here are two full exploding rolls, not a single flat roll.

All numbers below are exact analytic values (closed-form recursion over the exploding-die distribution), not simulated. See Methodology near the bottom.

Every table reads success chance as **P(total ≥ DC)**, matching the DC scale in [Challenge Rating](../Mechanics/Questing%20Time!%20Mechanics.md#challenge-rating).

---

## DC-First Success Lookup

You know the DC, you want the odds for the die you're holding. **P(total ≥ DC)**, by die size, single straight exploding roll (no advantage or disadvantage). DC range matches the [Challenge Rating](../Mechanics/Questing%20Time!%20Mechanics.md#challenge-rating) scale (1–20).

| DC | d4 | d6 | d8 | d10 | d12 | d20 |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | 100.0% | 100.0% | 100.0% | 100.0% | 100.0% | 100.0% |
| 2 | 75.0% | 83.3% | 87.5% | 90.0% | 91.7% | 95.0% |
| 3 | 50.0% | 66.7% | 75.0% | 80.0% | 83.3% | 90.0% |
| 4 | 25.0% | 50.0% | 62.5% | 70.0% | 75.0% | 85.0% |
| 5 | 25.0% | 33.3% | 50.0% | 60.0% | 66.7% | 80.0% |
| 6 | 18.8% | 16.7% | 37.5% | 50.0% | 58.3% | 75.0% |
| 7 | 12.5% | 16.7% | 25.0% | 40.0% | 50.0% | 70.0% |
| 8 | 6.2% | 13.9% | 12.5% | 30.0% | 41.7% | 65.0% |
| 9 | 6.2% | 11.1% | 12.5% | 20.0% | 33.3% | 60.0% |
| 10 | 4.7% | 8.3% | 10.9% | 10.0% | 25.0% | 55.0% |
| 11 | 3.1% | 5.6% | 9.4% | 10.0% | 16.7% | 50.0% |
| 12 | 1.6% | 2.8% | 7.8% | 9.0% | 8.3% | 45.0% |
| 13 | 1.6% | 2.8% | 6.2% | 8.0% | 8.3% | 40.0% |
| 14 | 1.2% | 2.3% | 4.7% | 7.0% | 7.6% | 35.0% |
| 15 | 0.8% | 1.9% | 3.1% | 6.0% | 6.9% | 30.0% |
| 16 | 0.4% | 1.4% | 1.6% | 5.0% | 6.2% | 25.0% |
| 17 | 0.4% | 0.9% | 1.6% | 4.0% | 5.6% | 20.0% |
| 18 | 0.3% | 0.5% | 1.4% | 3.0% | 4.9% | 15.0% |
| 19 | 0.2% | 0.5% | 1.2% | 2.0% | 4.2% | 10.0% |
| 20 | 0.1% | 0.4% | 1.0% | 1.0% | 3.5% | 5.0% |

A blank cell never appears here because every die's single-roll odds stay above 0% for any DC in this range — but they get very small for a small die against a high DC. Read those low values as "technically possible, don't count on it."

**d20 at higher DCs.** The d20 alone spans a wide enough range that a few DCs above 20 stay worth checking:

| DC | d20 |
| --- | --- |
| 22 | 4.8% |
| 24 | 4.2% |
| 26 | 3.8% |
| 28 | 3.2% |
| 30 | 2.8% |

---

## Per-Die Detail

Quantiles and the full outcome histogram for each die, single exploding roll unless noted.

### d4

**Quantiles**

| Roll type | 10% | 25% | 50% | 75% | 90% |
| --- | --- | --- | --- | --- | --- |
| Single, exploding | 1 | 1 | 2 | 3 | 7 |
| Advantage | 2 | 2 | 3 | 6 | 9 |
| Disadvantage | 1 | 1 | 2 | 2 | 3 |

**Histogram, single exploding die** (mass at each outcome, cutoff ≈ mean + 3 sd)

| Total | 1 | 2 | 3 | 5 | 6 | 7 | 9 | 10 | 11 | >12 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 25.0% | 25.0% | 25.0% | 6.3% | 6.3% | 6.3% | 1.6% | 1.6% | 1.6% | 1.6% |

(4 never appears alone — a roll of 4 always explodes and keeps adding; same pattern holds for every die below at its own max, and at multiples of the die size.)

### d6

**Quantiles**

| Roll type | 10% | 25% | 50% | 75% | 90% |
| --- | --- | --- | --- | --- | --- |
| Single, exploding | 1 | 2 | 3 | 5 | 9 |
| Advantage | 2 | 3 | 5 | 8 | 11 |
| Disadvantage | 1 | 1 | 2 | 3 | 5 |

**Histogram, single exploding die**

| Total | 1–5 (each) | 7–11 (each) | 13 | 14 | >14 |
| --- | --- | --- | --- | --- | --- |
| P | 16.7% | 2.8% | 0.46% | 0.46% | 1.9% |

### d8

**Quantiles**

| Roll type | 10% | 25% | 50% | 75% | 90% |
| --- | --- | --- | --- | --- | --- |
| Single, exploding | 1 | 2 | 4 | 6 | 10 |
| Advantage | 3 | 4 | 6 | 7 | 13 |
| Disadvantage | 1 | 2 | 3 | 4 | 6 |

**Histogram, single exploding die**

| Total | 1–7 (each) | 9–15 (each) | 17 | >17 |
| --- | --- | --- | --- | --- |
| P | 12.5% | 1.56% | 0.20% | 1.4% |

### d10

**Quantiles**

| Roll type | 10% | 25% | 50% | 75% | 90% |
| --- | --- | --- | --- | --- | --- |
| Single, exploding | 1 | 3 | 5 | 8 | 9 |
| Advantage | 4 | 5 | 8 | 9 | 15 |
| Disadvantage | 1 | 2 | 3 | 5 | 7 |

**Histogram, single exploding die**

| Total | 1–9 (each) | 11–19 (each) | >20 |
| --- | --- | --- | --- |
| P | 10.0% | 1.0% | 1.0% |

### d12

**Quantiles**

| Roll type | 10% | 25% | 50% | 75% | 90% |
| --- | --- | --- | --- | --- | --- |
| Single, exploding | 2 | 3 | 6 | 9 | 11 |
| Advantage | 4 | 6 | 9 | 11 | 17 |
| Disadvantage | 1 | 2 | 4 | 6 | 9 |

**Histogram, single exploding die**

| Total | 1–11 (each) | 13–21 (each) | 22 | >22 |
| --- | --- | --- | --- | --- |
| P | 8.33% | 0.69% | 0.69% | 1.4% |

### d20

**Quantiles**

| Roll type | 10% | 25% | 50% | 75% | 90% |
| --- | --- | --- | --- | --- | --- |
| Single, exploding | 2 | 5 | 10 | 15 | 18 |
| Advantage | 7 | 10 | 15 | 18 | 19 |
| Disadvantage | 2 | 3 | 6 | 10 | 14 |

**Histogram, single exploding die**

| Total | 1–19 (each) | 21–33 (each) | >33 |
| --- | --- | --- | --- |
| P | 5.0% | 0.25% | 1.75% |

Note the dip visible in the DC-First Success Lookup table above: a roll landing exactly on a die's max never stands alone — it always explodes into a higher total — so DC values a little above the die's face count draw from a thinner slice of outcomes than DC values just below it.

---

## Quantiles by Roll Type

Three tables — one per roll type — so you can compare across dice at a glance. Values are excerpted from each die's own Quantiles table above. For full DC-by-DC odds, see DC-First Success Lookup above; for histogram detail, see each die's own section above.

### Normal (single exploding)

| Die | 10% | 25% | 50% | 75% | 90% |
| --- | --- | --- | --- | --- | --- |
| d4  | 1   | 1   | 2   | 3   | 7   |
| d6  | 1   | 2   | 3   | 5   | 9   |
| d8  | 1   | 2   | 4   | 6   | 10  |
| d10 | 1   | 3   | 5   | 8   | 9   |
| d12 | 2   | 3   | 6   | 9   | 11  |
| d20 | 2   | 5   | 10  | 15  | 18  |

### Advantage

| Die | 10% | 25% | 50% | 75% | 90% |
| --- | --- | --- | --- | --- | --- |
| d4 | 2 | 2 | 3 | 6 | 9 |
| d6 | 2 | 3 | 5 | 8 | 11 |
| d8 | 3 | 4 | 6 | 7 | 13 |
| d10 | 4 | 5 | 8 | 9 | 15 |
| d12 | 4 | 6 | 9 | 11 | 17 |
| d20 | 7 | 10 | 15 | 18 | 19 |

### Disadvantage

| Die | 10% | 25% | 50% | 75% | 90% |
| --- | --- | --- | --- | --- | --- |
| d4 | 1 | 1 | 2 | 2 | 3 |
| d6 | 1 | 1 | 2 | 3 | 5 |
| d8 | 1 | 2 | 3 | 4 | 6 |
| d10 | 1 | 2 | 3 | 5 | 7 |
| d12 | 1 | 2 | 4 | 6 | 9 |
| d20 | 2 | 3 | 6 | 10 | 14 |

---

## Degrees of Success

[Degrees of Success](../Mechanics/Questing%20Time!%20Mechanics.md#degrees-of-success) sets these thresholds:

- Beat the DC by **10 or more**: an unbelievable success. Treat it as a critical.
- Beat the DC by **5 or more**: play it as effortless for the character.
- Fail by **5 or more**: nonserious short-term side effects.
- Fail by **10 or more**: serious short-term side effects, possibly long-lasting.

The tables below give the chance of each, per die, across the same DC range as DC-First Success Lookup above. "Beat by ≥5" is P(total ≥ DC+5); "fail by ≥5" is P(total ≤ DC−5), and so on.

### d4 Degrees of Success

| DC | Beat ≥5 (effortless) | Beat ≥10 (critical) | Fail ≥5 (nonserious) | Fail ≥10 (serious) |
| --- | --- | --- | --- | --- |
| 1 | 18.8% | 3.1% | 0.0% | 0.0% |
| 2 | 12.5% | 1.6% | 0.0% | 0.0% |
| 3 | 6.2% | 1.6% | 0.0% | 0.0% |
| 4 | 6.2% | 1.2% | 0.0% | 0.0% |
| 5 | 4.7% | 0.8% | 0.0% | 0.0% |
| 6 | 3.1% | 0.4% | 25.0% | 0.0% |
| 7 | 1.6% | 0.4% | 50.0% | 0.0% |
| 8 | 1.6% | 0.3% | 75.0% | 0.0% |
| 9 | 1.2% | 0.2% | 75.0% | 0.0% |
| 10 | 0.8% | 0.1% | 81.2% | 0.0% |
| 11 | 0.4% | 0.1% | 87.5% | 25.0% |
| 12 | 0.4% | 0.1% | 93.8% | 50.0% |
| 13 | 0.3% | 0.0% | 93.8% | 75.0% |
| 14 | 0.2% | 0.0% | 95.3% | 75.0% |
| 15 | 0.1% | 0.0% | 96.9% | 81.2% |
| 16 | 0.1% | 0.0% | 98.4% | 87.5% |
| 17 | 0.1% | 0.0% | 98.4% | 93.8% |
| 18 | 0.0% | 0.0% | 98.8% | 93.8% |
| 19 | 0.0% | 0.0% | 99.2% | 95.3% |
| 20 | 0.0% | 0.0% | 99.6% | 96.9% |

### d6 Degrees of Success

| DC | Beat ≥5 (effortless) | Beat ≥10 (critical) | Fail ≥5 (nonserious) | Fail ≥10 (serious) |
| --- | --- | --- | --- | --- |
| 1 | 16.7% | 5.6% | 0.0% | 0.0% |
| 2 | 16.7% | 2.8% | 0.0% | 0.0% |
| 3 | 13.9% | 2.8% | 0.0% | 0.0% |
| 4 | 11.1% | 2.3% | 0.0% | 0.0% |
| 5 | 8.3% | 1.9% | 0.0% | 0.0% |
| 6 | 5.6% | 1.4% | 16.7% | 0.0% |
| 7 | 2.8% | 0.9% | 33.3% | 0.0% |
| 8 | 2.8% | 0.5% | 50.0% | 0.0% |
| 9 | 2.3% | 0.5% | 66.7% | 0.0% |
| 10 | 1.9% | 0.4% | 83.3% | 0.0% |
| 11 | 1.4% | 0.3% | 83.3% | 16.7% |
| 12 | 0.9% | 0.2% | 86.1% | 33.3% |
| 13 | 0.5% | 0.2% | 88.9% | 50.0% |
| 14 | 0.5% | 0.1% | 91.7% | 66.7% |
| 15 | 0.4% | 0.1% | 94.4% | 83.3% |
| 16 | 0.3% | 0.1% | 97.2% | 83.3% |
| 17 | 0.2% | 0.1% | 97.2% | 86.1% |
| 18 | 0.2% | 0.0% | 97.7% | 88.9% |
| 19 | 0.1% | 0.0% | 98.1% | 91.7% |
| 20 | 0.1% | 0.0% | 98.6% | 94.4% |

### d8 Degrees of Success

| DC | Beat ≥5 (effortless) | Beat ≥10 (critical) | Fail ≥5 (nonserious) | Fail ≥10 (serious) |
| --- | --- | --- | --- | --- |
| 1 | 37.5% | 9.4% | 0.0% | 0.0% |
| 2 | 25.0% | 7.8% | 0.0% | 0.0% |
| 3 | 12.5% | 6.2% | 0.0% | 0.0% |
| 4 | 12.5% | 4.7% | 0.0% | 0.0% |
| 5 | 10.9% | 3.1% | 0.0% | 0.0% |
| 6 | 9.4% | 1.6% | 12.5% | 0.0% |
| 7 | 7.8% | 1.6% | 25.0% | 0.0% |
| 8 | 6.2% | 1.4% | 37.5% | 0.0% |
| 9 | 4.7% | 1.2% | 50.0% | 0.0% |
| 10 | 3.1% | 1.0% | 62.5% | 0.0% |
| 11 | 1.6% | 0.8% | 75.0% | 12.5% |
| 12 | 1.6% | 0.6% | 87.5% | 25.0% |
| 13 | 1.4% | 0.4% | 87.5% | 37.5% |
| 14 | 1.2% | 0.2% | 89.1% | 50.0% |
| 15 | 1.0% | 0.2% | 90.6% | 62.5% |
| 16 | 0.8% | 0.2% | 92.2% | 75.0% |
| 17 | 0.6% | 0.1% | 93.8% | 87.5% |
| 18 | 0.4% | 0.1% | 95.3% | 87.5% |
| 19 | 0.2% | 0.1% | 96.9% | 89.1% |
| 20 | 0.2% | 0.1% | 98.4% | 90.6% |

### d10 Degrees of Success

| DC  | Beat ≥5 (effortless) | Beat ≥10 (critical) | Fail ≥5 (nonserious) | Fail ≥10 (serious) |
| --- | -------------------- | ------------------- | -------------------- | ------------------ |
| 1   | 50.0%                | 10.0%               | 0.0%                 | 0.0%               |
| 2   | 40.0%                | 9.0%                | 0.0%                 | 0.0%               |
| 3   | 30.0%                | 8.0%                | 0.0%                 | 0.0%               |
| 4   | 20.0%                | 7.0%                | 0.0%                 | 0.0%               |
| 5   | 10.0%                | 6.0%                | 0.0%                 | 0.0%               |
| 6   | 10.0%                | 5.0%                | 10.0%                | 0.0%               |
| 7   | 9.0%                 | 4.0%                | 20.0%                | 0.0%               |
| 8   | 8.0%                 | 3.0%                | 30.0%                | 0.0%               |
| 9   | 7.0%                 | 2.0%                | 40.0%                | 0.0%               |
| 10  | 6.0%                 | 1.0%                | 50.0%                | 0.0%               |
| 11  | 5.0%                 | 1.0%                | 60.0%                | 10.0%              |
| 12  | 4.0%                 | 0.9%                | 70.0%                | 20.0%              |
| 13  | 3.0%                 | 0.8%                | 80.0%                | 30.0%              |
| 14  | 2.0%                 | 0.7%                | 90.0%                | 40.0%              |
| 15  | 1.0%                 | 0.6%                | 90.0%                | 50.0%              |
| 16  | 1.0%                 | 0.5%                | 91.0%                | 60.0%              |
| 17  | 0.9%                 | 0.4%                | 92.0%                | 70.0%              |
| 18  | 0.8%                 | 0.3%                | 93.0%                | 80.0%              |
| 19  | 0.7%                 | 0.2%                | 94.0%                | 90.0%              |
| 20  | 0.6%                 | 0.1%                | 95.0%                | 90.0%              |

### d12 Degrees of Success

| DC | Beat ≥5 (effortless) | Beat ≥10 (critical) | Fail ≥5 (nonserious) | Fail ≥10 (serious) |
| --- | --- | --- | --- | --- |
| 1 | 58.3% | 16.7% | 0.0% | 0.0% |
| 2 | 50.0% | 8.3% | 0.0% | 0.0% |
| 3 | 41.7% | 8.3% | 0.0% | 0.0% |
| 4 | 33.3% | 7.6% | 0.0% | 0.0% |
| 5 | 25.0% | 6.9% | 0.0% | 0.0% |
| 6 | 16.7% | 6.2% | 8.3% | 0.0% |
| 7 | 8.3% | 5.6% | 16.7% | 0.0% |
| 8 | 8.3% | 4.9% | 25.0% | 0.0% |
| 9 | 7.6% | 4.2% | 33.3% | 0.0% |
| 10 | 6.9% | 3.5% | 41.7% | 0.0% |
| 11 | 6.2% | 2.8% | 50.0% | 8.3% |
| 12 | 5.6% | 2.1% | 58.3% | 16.7% |
| 13 | 4.9% | 1.4% | 66.7% | 25.0% |
| 14 | 4.2% | 0.7% | 75.0% | 33.3% |
| 15 | 3.5% | 0.7% | 83.3% | 41.7% |
| 16 | 2.8% | 0.6% | 91.7% | 50.0% |
| 17 | 2.1% | 0.6% | 91.7% | 58.3% |
| 18 | 1.4% | 0.5% | 92.4% | 66.7% |
| 19 | 0.7% | 0.5% | 93.1% | 75.0% |
| 20 | 0.7% | 0.4% | 93.8% | 83.3% |

### d20 Degrees of Success

| DC | Beat ≥5 (effortless) | Beat ≥10 (critical) | Fail ≥5 (nonserious) | Fail ≥10 (serious) |
| --- | --- | --- | --- | --- |
| 1 | 75.0% | 50.0% | 0.0% | 0.0% |
| 2 | 70.0% | 45.0% | 0.0% | 0.0% |
| 3 | 65.0% | 40.0% | 0.0% | 0.0% |
| 4 | 60.0% | 35.0% | 0.0% | 0.0% |
| 5 | 55.0% | 30.0% | 0.0% | 0.0% |
| 6 | 50.0% | 25.0% | 5.0% | 0.0% |
| 7 | 45.0% | 20.0% | 10.0% | 0.0% |
| 8 | 40.0% | 15.0% | 15.0% | 0.0% |
| 9 | 35.0% | 10.0% | 20.0% | 0.0% |
| 10 | 30.0% | 5.0% | 25.0% | 0.0% |
| 11 | 25.0% | 5.0% | 30.0% | 5.0% |
| 12 | 20.0% | 4.7% | 35.0% | 10.0% |
| 13 | 15.0% | 4.5% | 40.0% | 15.0% |
| 14 | 10.0% | 4.2% | 45.0% | 20.0% |
| 15 | 5.0% | 4.0% | 50.0% | 25.0% |
| 16 | 5.0% | 3.7% | 55.0% | 30.0% |
| 17 | 4.7% | 3.5% | 60.0% | 35.0% |
| 18 | 4.5% | 3.3% | 65.0% | 40.0% |
| 19 | 4.2% | 3.0% | 70.0% | 45.0% |
| 20 | 4.0% | 2.8% | 75.0% | 50.0% |

---

## Opposed Rolls

This covers opposed rolls — one exploding die directly against another, the resolution system for combat and most contests per [Dice and Rolls](../Mechanics/Questing%20Time!%20Mechanics.md#dice-and-rolls). Unlike a DC-based check, there's no fixed target: two dice compete directly. This covers two things:

1. **Win probability** — for every pair of die sizes, the chance the attacker's total beats the defender's, and the chance of a tie.
2. **Margin bands** — the chance the attack lands in each of the five outcome bands from [Combat](../Mechanics/Questing%20Time!%20Mechanics.md#combat)'s margin table, for a same-size fight and several mismatched ones.

The margin-band section exists mainly to give real numbers for the question of how the combat margin table reconciles with the Health track, since settled in [Combat](../Mechanics/Questing%20Time!%20Mechanics.md#combat). This note only supplies data; it does not propose a resolution.

### Win / Tie Matrix

Each cell reads **attacker win% / tie%**, where the attacker is the row die and the defender is the column die. Both dice explode per the normal house rule. Read a cell as: "row die attacking column die wins P% of the time and ties T% of the time."

The matrix is not symmetric cell-for-cell (a d4 row against a d20 column is a different fight than a d20 row against a d4 column), but it obeys one identity throughout: win(row, col) + tie(row, col) + win(col, row) = 100%. That is, whatever isn't a row-die win or a tie is a column-die win.

| Attacker \ Defender | d4 | d6 | d8 | d10 | d12 | d20 |
| --- | --- | --- | --- | --- | --- | --- |
| **d4** | 40.00% / 20.00% | 32.91% / 13.85% | 26.77% / 11.81% | 22.41% / 9.56% | 19.04% / 8.21% | 11.65% / 5.00% |
| **d6** | 53.23% / 13.85% | 42.86% / 14.29% | 35.46% / 10.92% | 30.13% / 9.22% | 25.75% / 8.12% | 15.95% / 4.98% |
| **d8** | 61.42% / 11.81% | 53.62% / 10.92% | 44.44% / 11.11% | 37.63% / 8.99% | 32.67% / 7.72% | 20.57% / 4.95% |
| **d10** | 68.03% / 9.56% | 60.65% / 9.22% | 53.38% / 8.99% | 45.45% / 9.09% | 39.30% / 7.63% | 25.26% / 4.95% |
| **d12** | 72.75% / 8.21% | 66.13% / 8.12% | 59.61% / 7.72% | 53.06% / 7.63% | 46.15% / 7.69% | 29.88% / 4.83% |
| **d20** | 83.35% / 5.00% | 79.07% / 4.98% | 74.48% / 4.95% | 69.78% / 4.95% | 65.28% / 4.83% | 47.62% / 4.76% |

**Reading the diagonal.** A same-size matchup is not a 50/50 coin flip — it is close to it. A d4 vs. d4 fight wins 40.00% of the time and ties 20.00% of the time (40.00 × 2 + 20.00 = 100.00), and the tie share shrinks as the die gets bigger: d20 vs. d20 wins 47.62% of the time with only a 4.76% tie. Bigger same-size dice explode into more distinct totals, so exact ties get rarer even though the win/loss split stays even.

**Reading a mismatch.** The bigger die always wins more than it loses, but never as much as raw face-size ratio might suggest — a d20 only beats a d4 attacker's die 83.35% of the time (not 500%'s worth of dominance), because exploding chains give the smaller die a long tail of large totals it wouldn't get from a flat roll.

### Margin Bands (Combat Outcome Table)

[Combat](../Mechanics/Questing%20Time!%20Mechanics.md#combat) resolves a hit by margin = attacker's total − defender's total, sorted into five bands:

| Margin | Outcome |
| --- | --- |
| +0 or lower | Uninjured |
| +1 to +3 | Superficial |
| +4 to +6 | Moderate |
| +7 to +9 | Badly hurt |
| +10 or more | Dead or near-dead |

Note that "+0 or lower" absorbs every tie and every case where the defender's total is actually higher — the table as written in Mechanics has no separate "defender wins" band, so a defender who out-rolls the attacker lands in the same "uninjured" bucket as a narrow miss. That collapse is part of what R-1 is asking about.

Below: all six same-size matchups, plus several mismatched pairs (a 3-step gap and a max/min gap, in both attack directions) to show how the band shape shifts as the size gap grows.

**Same-size matchups**

| Matchup | Uninjured | Superficial | Moderate | Badly hurt | Dead/near-dead |
| --- | --- | --- | --- | --- | --- |
| d4 vs d4 | 60.00% | 25.00% | 10.42% | 2.92% | 1.67% |
| d6 vs d6 | 57.14% | 27.14% | 8.57% | 4.52% | 2.62% |
| d8 vs d8 | 55.56% | 24.40% | 11.90% | 3.77% | 4.37% |
| d10 vs d10 | 54.55% | 21.52% | 13.33% | 5.15% | 5.45% |
| d12 vs d12 | 53.85% | 19.06% | 13.29% | 7.52% | 6.29% |
| d20 vs d20 | 52.38% | 12.82% | 10.68% | 8.53% | 15.59% |

Every same-size matchup lands "Uninjured" a bit more than half the time (that band absorbs all ties plus all narrow defender wins). As die size grows, the distribution doesn't just spread out symmetrically — it shifts mass toward "Dead or near-dead": d4 vs d4 puts only 1.67% of fights there, but d20 vs d20 puts 15.59%. Bigger dice explode into much larger totals on their tail, and margin cares about the gap between two such totals, so big-die fights swing harder even at even odds.

**Mismatched matchups** (attacker die vs defender die)

| Matchup | Uninjured | Superficial | Moderate | Badly hurt | Dead/near-dead |
| --- | --- | --- | --- | --- | --- |
| d4 atk vs d12 def | 80.96% | 12.22% | 4.60% | 1.40% | 0.81% |
| d12 atk vs d4 def | 27.25% | 23.89% | 22.04% | 17.13% | 9.68% |
| d6 atk vs d12 def | 74.25% | 16.13% | 5.34% | 2.69% | 1.60% |
| d12 atk vs d6 def | 33.87% | 23.03% | 21.35% | 13.17% | 8.58% |
| d8 atk vs d10 def | 62.37% | 20.33% | 10.37% | 3.22% | 3.72% |
| d10 atk vs d8 def | 46.62% | 25.32% | 16.04% | 5.78% | 6.24% |
| d4 atk vs d20 def | 88.35% | 7.49% | 2.81% | 0.86% | 0.49% |
| d20 atk vs d4 def | 16.65% | 14.96% | 14.89% | 14.70% | 38.81% |

The widest gap in the vault's die range, d20 attacker against d4 defender, lands "Dead or near-dead" 38.81% of the time — more than any other single band in that fight. A d4 defender essentially cannot generate enough total to keep the margin under +10 against a d20's tail. Conversely the same pair reversed (d4 attacking a d12 or d20 defender) almost never gets past "Superficial": the small attacking die rarely rolls high enough, relative to the big defending die, to open a wide margin at all.

---

## Multi-Die Sums (NdX, exploding)

Some abilities roll more than one exploding die and sum the totals: [Rooted](../Mechanics/Abilities.md#rooted) both work this way (2 dice and 3 dice respectively; see each ability's holder's stat block for the die size in play). The tables below cover N = 2, 3, 4 dice for every die size in this vault, so the reference holds for any future ability of this shape, not just the two on record.

Each die in the pool explodes on its own, the same rule as a single die above. The pool total is the sum of all N (post-explosion) dice. These are exact convolutions of the single-die pmf from Methodology, not simulation — see the note at the end of this section.

### 4-sided pool (2d4, 3d4, 4d4)

**P(total ≥ DC)**

| Roll type | DC 5 | DC 10 | DC 15 | DC 20 | DC 25 |
| --- | --- | --- | --- | --- | --- |
| 2d4 | 62.5% | 18.7% | 4.7% | 1.2% | 0.2% |
| 3d4 | 93.7% | 46.1% | 16.2% | 4.6% | 1.3% |
| 4d4 | 99.6% | 72.3% | 35.0% | 13.4% | 4.4% |

**Quantiles**

| Roll type | 10% | 25% | 50% | 75% | 90% |
| --- | --- | --- | --- | --- | --- |
| 2d4 | 3 | 4 | 5 | 8 | 12 |
| 3d4 | 5 | 6 | 9 | 12 | 16 |
| 4d4 | 7 | 9 | 12 | 16 | 21 |

**Histogram, 2d4** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 2–3 | 4–5 | 6–7 | 8–9 | 10–11 | 12–13 | 14–15 | 16–17 | 18 | >18 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 18.8% | 31.2% | 15.6% | 15.6% | 6.6% | 5.9% | 2.3% | 2.0% | 0.8% | 1.4% |

**Histogram, 3d4** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 3–5 | 6–8 | 9–11 | 12–14 | 15–17 | 18–20 | 21–23 | 24 | >24 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 15.6% | 29.7% | 24.4% | 14.1% | 8.3% | 4.3% | 2.0% | 0.9% | 1.3% |

**Histogram, 4d4** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 4–6 | 7–9 | 10–12 | 13–15 | 16–18 | 19–21 | 22–24 | 25–27 | 28–30 | >30 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 5.9% | 21.9% | 23.7% | 19.0% | 13.2% | 7.7% | 4.3% | 2.2% | 1.1% | 1.0% |

---

### 6-sided pool (2d6, 3d6, 4d6)

**P(total ≥ DC)**

| Roll type | DC 5 | DC 10 | DC 15 | DC 20 | DC 25 | DC 30 |
| --- | --- | --- | --- | --- | --- | --- |
| 2d6 | 83.3% | 30.6% | 10.0% | 3.0% | 0.8% | 0.2% |
| 3d6 | 98.1% | 66.4% | 30.3% | 11.4% | 3.9% | 1.2% |
| 4d6 | 99.9% | 90.6% | 57.6% | 28.7% | 12.2% | 4.6% |

**Quantiles**

| Roll type | 10% | 25% | 50% | 75% | 90% |
| --- | --- | --- | --- | --- | --- |
| 2d6 | 4 | 5 | 7 | 10 | 14 |
| 3d6 | 7 | 9 | 11 | 16 | 20 |
| 4d6 | 10 | 12 | 16 | 20 | 26 |

**Histogram, 2d6** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 2–4 | 5–7 | 8–10 | 11–13 | 14–16 | 17–19 | 20–22 | >22 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 16.7% | 36.1% | 22.2% | 12.0% | 6.9% | 3.0% | 1.7% | 1.3% |

**Histogram, 3d6** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 3–5 | 6–8 | 9–11 | 12–14 | 15–17 | 18–20 | 21–23 | 24–26 | 27–29 | >29 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 4.6% | 19.9% | 26.4% | 18.8% | 13.3% | 7.7% | 4.5% | 2.4% | 1.2% | 1.2% |

**Histogram, 4d6** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 4–7 | 8–11 | 12–15 | 16–19 | 20–23 | 24–27 | 28–31 | 32–35 | 36 | >36 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 2.7% | 18.4% | 28.0% | 22.2% | 14.2% | 7.7% | 3.8% | 1.8% | 0.8% | 1.1% |

---

### 8-sided pool (2d8, 3d8, 4d8)

**P(total ≥ DC)**

| Roll type | DC 5 | DC 15 | DC 25 | DC 35 |
| --- | --- | --- | --- | --- |
| 2d8 | 90.6% | 17.6% | 2.2% | 0.2% |
| 3d8 | 99.2% | 47.9% | 9.4% | 1.3% |
| 4d8 | 100.0% | 78.8% | 25.9% | 5.3% |

**Quantiles**

| Roll type | 10% | 25% | 50% | 75% | 90% |
| --- | --- | --- | --- | --- | --- |
| 2d8 | 5 | 7 | 9 | 13 | 18 |
| 3d8 | 8 | 11 | 14 | 19 | 24 |
| 4d8 | 12 | 15 | 19 | 25 | 31 |

**Histogram, 2d8** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 2–4 | 5–7 | 8–10 | 11–13 | 14–16 | 17–19 | 20–22 | 23–25 | 26 | >26 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 9.4% | 23.4% | 28.5% | 17.6% | 8.6% | 6.1% | 3.2% | 1.4% | 1.0% | 1.4% |

**Histogram, 3d8** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 3–6 | 7–10 | 11–14 | 15–18 | 19–22 | 23–26 | 27–30 | 31–34 | 35 | >35 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 3.9% | 18.9% | 29.2% | 21.6% | 12.7% | 7.2% | 3.4% | 1.7% | 0.7% | 1.1% |

**Histogram, 4d8** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 4–8 | 9–13 | 14–18 | 19–23 | 24–28 | 29–33 | 34–38 | 39–43 | >43 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 1.7% | 14.3% | 29.1% | 25.1% | 15.5% | 8.0% | 3.7% | 1.6% | 1.0% |

---

### 10-sided pool (2d10, 3d10, 4d10)

**P(total ≥ DC)**

| Roll type | DC 5 | DC 15 | DC 25 | DC 35 |
| --- | --- | --- | --- | --- |
| 2d10 | 94.0% | 27.8% | 4.6% | 0.6% |
| 3d10 | 99.6% | 66.5% | 18.1% | 3.5% |
| 4d10 | 100.0% | 90.2% | 43.5% | 12.4% |

**Quantiles**

| Roll type | 10% | 25% | 50% | 75% | 90% |
| --- | --- | --- | --- | --- | --- |
| 2d10 | 5 | 8 | 11 | 15 | 20 |
| 3d10 | 10 | 13 | 17 | 22 | 28 |
| 4d10 | 15 | 18 | 23 | 29 | 36 |

**Histogram, 2d10** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 2–5 | 6–9 | 10–13 | 14–17 | 18–21 | 22–25 | 26–29 | 30 | >30 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 10.0% | 26.0% | 30.6% | 17.6% | 7.4% | 4.7% | 2.0% | 0.9% | 1.4% |

**Histogram, 3d10** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 3–7 | 8–12 | 13–17 | 18–22 | 23–27 | 28–32 | 33–37 | 38–40 | >40 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 3.5% | 18.2% | 30.6% | 23.7% | 12.6% | 6.6% | 2.9% | 1.3% | 1.2% |

**Histogram, 4d10** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 4–9 | 10–15 | 16–21 | 22–27 | 28–33 | 34–39 | 40–45 | 46–50 | >50 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 1.3% | 11.8% | 28.3% | 27.7% | 16.6% | 8.4% | 3.6% | 1.5% | 1.0% |

---

### 12-sided pool (2d12, 3d12, 4d12)

**P(total ≥ DC)**

| Roll type | DC 5 | DC 15 | DC 25 | DC 35 | DC 45 |
| --- | --- | --- | --- | --- | --- |
| 2d12 | 95.8% | 40.9% | 8.3% | 1.3% | 0.2% |
| 3d12 | 99.8% | 79.1% | 29.3% | 7.6% | 1.6% |
| 4d12 | 100.0% | 95.2% | 61.8% | 23.1% | 6.6% |

**Quantiles**

| Roll type | 10% | 25% | 50% | 75% | 90% |
| --- | --- | --- | --- | --- | --- |
| 2d12 | 6 | 9 | 13 | 18 | 23 |
| 3d12 | 12 | 15 | 20 | 26 | 33 |
| 4d12 | 17 | 21 | 27 | 34 | 41 |

**Histogram, 2d12** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 2–5 | 6–9 | 10–13 | 14–17 | 18–21 | 22–25 | 26–29 | 30–33 | 34–35 | >35 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 6.9% | 18.1% | 27.8% | 22.0% | 12.7% | 5.3% | 3.6% | 2.0% | 0.7% | 1.2% |

**Histogram, 3d12** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 3–7 | 8–12 | 13–17 | 18–22 | 23–27 | 28–32 | 33–37 | 38–42 | 43–46 | >46 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 2.0% | 10.7% | 23.3% | 26.2% | 18.0% | 9.8% | 5.3% | 2.6% | 1.2% | 1.2% |

**Histogram, 4d12** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 4–10 | 11–17 | 18–24 | 25–31 | 32–38 | 39–45 | 46–52 | 53–57 | >57 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 1.0% | 10.2% | 27.1% | 29.5% | 17.9% | 8.7% | 3.6% | 1.4% | 1.0% |

---

### 20-sided pool (2d20, 3d20, 4d20)

**P(total ≥ DC)**

| Roll type | DC 5 | DC 20 | DC 35 | DC 50 | DC 65 |
| --- | --- | --- | --- | --- | --- |
| 2d20 | 98.5% | 57.3% | 10.0% | 1.8% | 0.2% |
| 3d20 | 100.0% | 87.9% | 41.6% | 9.6% | 1.9% |
| 4d20 | 100.0% | 97.6% | 74.3% | 32.0% | 8.6% |

**Quantiles**

| Roll type | 10% | 25% | 50% | 75% | 90% |
| --- | --- | --- | --- | --- | --- |
| 2d20 | 10 | 15 | 21 | 28 | 34 |
| 3d20 | 18 | 25 | 32 | 40 | 49 |
| 4d20 | 27 | 34 | 43 | 53 | 63 |

**Histogram, 2d20** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 2–7 | 8–13 | 14–19 | 20–25 | 26–31 | 32–37 | 38–43 | 44–49 | 50–52 | >52 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 5.3% | 14.3% | 23.3% | 25.0% | 16.9% | 8.8% | 2.9% | 1.9% | 1.1% | 1.1% |

**Histogram, 3d20** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 3–10 | 11–18 | 19–26 | 27–34 | 35–42 | 43–50 | 51–58 | 59–66 | 67–70 | >70 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 1.5% | 8.7% | 21.0% | 27.2% | 21.7% | 11.3% | 4.9% | 2.3% | 0.9% | 0.9% |

**Histogram, 4d20** (mass at each range, cutoff ≈ mean + 3 sd)

| Total | 4–13 | 14–23 | 24–33 | 34–43 | 44–53 | 54–63 | 64–73 | 74–83 | 84–87 | >87 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| P | 0.4% | 5.1% | 17.6% | 28.5% | 25.1% | 13.7% | 5.9% | 2.3% | 0.8% | 0.8% |

---

## Methodology

All values in this note are computed analytically, not by simulation.

**Exploding single die.** For a die of size N, the outcome pmf satisfies the recursion:

- P(total = t) = 1/N for 1 ≤ t ≤ N−1
- P(total = N) = 0 (a roll of exactly N always explodes, so N alone is never a final total)
- P(total = t) = (1/N) · P(total = t−N) for t > N

This falls out of the rule directly: a non-max roll stops the chain, and a max roll adds N and repeats the same process.

**Advantage / disadvantage.** Built from the single-die cdf F(t): advantage's cdf is F(t)², disadvantage's is 1 − (1 − F(t))². This is standard "roll twice, take higher/lower" math, applied here to the exploding-die distribution per the vault's own advantage rule (two full exploding rolls, not one flat roll).

**Mean, closed form.** The exploding single-die mean is N(N+1) / (2(N−1)) — confirmed against the recursion output for every die size.

**Multi-die sums.** For a pool of N dice of the same size, the pool's pmf is the N-fold convolution of the single-die pmf above: P(pool total = t) = Σ P(die = k) · P(remaining N−1 dice sum = t−k). This is still exact analytic math, no simulation — each die's exploding tail is exact, and convolution of exact distributions stays exact.

**Win / tie (opposed rolls).** For attacker die A and defender die D with pmfs pA and pD, and cdf CD(t) = P(D < t):

- P(win) = Σₜ pA(t) · CD(t)
- P(tie) = Σₜ pA(t) · pD(t)
- P(loss) = 1 − P(win) − P(tie)

**Margin bands.** For the same pair, the margin m = (attacker total) − (defender total) has probability P(m) = Σₜ pA(t) · pD(t − m), computed directly as a joint sum over both dice's pmfs (equivalent to convolving pA with the reflection of pD) rather than by simulation. Each margin value is then sorted into its band per [Combat](../Mechanics/Questing%20Time!%20Mechanics.md#combat)'s table and the band masses summed.

**Verification.**

- The single-die recursion was checked two independent ways: evaluated out to a cutoff where the remaining tail probability is below 1e-15 (reported mass verified to sum to 1.0000000000 for every die), and separately evaluated out to a cutoff of 40×N per die with remaining tail mass below 1e-24 for every die from d4 through d20 (also exact to float precision). Both agree.
- Multi-die sums were checked two ways for every (die size, N) pair: the resulting pmf sums to 1.0000000000, and the pool's mean equals N times the single-die mean.
- Every win/tie/loss triple was checked to sum to 1.0000 (float precision) for all 36 die-pair combinations, and each matchup's identity win(A,D) + tie(A,D) + win(D,A) = 1 was confirmed to hold across the full matrix.
- Every margin-band row was checked to sum to 1.0000.
- As a spot check, same-die matchups come out close to an even split with a shrinking tie share as die size grows (e.g. d4 vs d4: 40.00% win / 20.00% tie / 40.00% loss; d20 vs d20: 47.62% win / 4.76% tie / 47.62% loss) — consistent with two identical exploding dice being a near-fair fight, with exact ties becoming rarer as the die's outcome space grows finer.

---

## See also

- [Dice and Rolls](../Mechanics/Questing%20Time!%20Mechanics.md#dice-and-rolls) — the house rules this note is built from.
- [Challenge Rating](../Mechanics/Questing%20Time!%20Mechanics.md#challenge-rating) — the DC scale these success percentages line up with.
- [Degrees of Success](../Mechanics/Questing%20Time!%20Mechanics.md#degrees-of-success) — the source rule for the Degrees of Success thresholds.
- [Combat](../Mechanics/Questing%20Time!%20Mechanics.md#combat) — the margin table the Opposed Rolls section resolves against.
- [Alignment](../Mechanics/Questing%20Time!%20Mechanics.md#alignment) — the alignment rules. The precomputed alignment-adjusted DC table (no die involved) lives on GM Screen, not here.
- [Combat](../Mechanics/Questing%20Time!%20Mechanics.md#combat) — the margin table the Opposed Rolls margin-band data speaks to.
