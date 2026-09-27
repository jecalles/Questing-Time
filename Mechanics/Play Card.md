---
description: "The table's play card — damage margins, Health track, opposed-roll and DC odds, initiative, and alignment DC lookup, ordered for lookup during play. Static; it does not change between sessions."
tags: [mechanics, player-reference]
---

# Play Card

This card holds the numbers, and they do not change. It is printed once
and reused. What changes each session is the crib.

Full rules and math: [Questing Time! Mechanics](../Mechanics/Questing%20Time!%20Mechanics.md) and
[Dice Probability Reference](../Mechanics/Dice%20Probability%20Reference.md).

---

## Damage Margin Bands (Combat)

Opposed roll: attacker's relevant stat vs. defender's. Read the margin (attacker total − defender total):

| Margin | Result |
| --- | --- |
| +0 or lower | Defender uninjured, narrates outcome. |
| +1 to +3 | Defender narrates the hit; hurt superficially/temporarily (stunned). |
| +4 to +6 | Attacker narrates, defender narrates defense, attacker explains overcoming it; hurt moderately (concussed, cracked rib). |
| +7 to +9 | Attacker narrates and can alter details of the defense; badly hurt (unconscious, bleeding, broken bones). |
| +10 or more | Defender dead or nearly; permanent issues even if saved. |

A spell/weapon can jump multiple steps at once if its own text says so — no upper limit.

## Health Track

Buffed → **Normal** → Minor Damage → Major Damage → Critical Damage → Incapacitated → Dead

- **Minor Damage** — cosmetic. No mechanical hindrance.
- **Major Damage** — lasts until a long rest. Reduced mobility OR disadvantage on one stat (GM's call, by damage type).
- **Critical Damage** — lasts until medically treated. Reduced mobility AND disadvantage on proactive rolls.
- **Incapacitated** — unconscious, needs immediate medical attention, at risk of death.
- **Dead** — dead. Only divine magic revives.

A character with reduced mobility must roll Constitution against a DC (rising with severity) to cross a zone at all.

---

## Opposed Roll Odds — Die vs. Die

The resolution system for combat and most contests. Each cell is **attacker win% / tie%**, row die attacking column die, both exploding. Whatever is left over is the defender's win.

| Atk \ Def | d4 | d6 | d8 | d10 | d12 | d20 |
| --- | --- | --- | --- | --- | --- | --- |
| **d4** | 40 / 20 | 33 / 14 | 27 / 12 | 22 / 10 | 19 / 8 | 12 / 5 |
| **d6** | 53 / 14 | 43 / 14 | 35 / 11 | 30 / 9 | 26 / 8 | 16 / 5 |
| **d8** | 61 / 12 | 54 / 11 | 44 / 11 | 38 / 9 | 33 / 8 | 21 / 5 |
| **d10** | 68 / 10 | 61 / 9 | 53 / 9 | 45 / 9 | 39 / 8 | 25 / 5 |
| **d12** | 73 / 8 | 66 / 8 | 60 / 8 | 53 / 8 | 46 / 8 | 30 / 5 |
| **d20** | 83 / 5 | 79 / 5 | 74 / 5 | 70 / 5 | 65 / 5 | 48 / 5 |

Ties are common on small dice, rare on big ones; a same-size fight is close to even but never exact; the bigger die never dominates as hard as its face count suggests. Full explanation: [Win / Tie Matrix](../Mechanics/Dice%20Probability%20Reference.md#win--tie-matrix).

Margin-band odds per matchup — how often a given fight lands in each damage band above — are in [Margin Bands (Combat Outcome Table)](../Mechanics/Dice%20Probability%20Reference.md#margin-bands-combat-outcome-table).

---

## Challenge Rating (DC bands)

| DC | Meaning | Example |
| --- | --- | --- |
| 1–2 | Guaranteed except in extreme cases | Buying a cheeseburger |
| 3–6 | Easy for everyone but the truly unskilled | Sitting silently through a risky conversation |
| 7–9 | Certain for the skilled, not for others | Persuading a bachelorette party to take shots |
| 10–12 | Impressive, but expected from someone truly skilled | Kicking in a heavy locked door |
| 13–16 | Extraordinary — possible, not likely | A spy resisting CIA interrogation |
| 17–19 | Nearly impossible | Talking police out of an arrest with no relationship to lean on |
| 20 | A practical impossibility | Lifting a car off a child |

**Planned Action auto-success.** A Planned Action (no time pressure, ideal conditions) auto-succeeds if the DC is half the die size or less. Snap Decisions always roll, and cannot take Determination Token help.

## Degrees of Success

- Beat DC by **10+** → unbelievable success, treat as a critical.
- Beat DC by **5+** → effortless for the character.
- Fail by **5+** → nonserious short-term side effects.
- Fail by **10+** → serious, possibly long-lasting side effects.

---

## Per-Die Success Odds (DC 5 / 10 / 15)

P(total ≥ DC), single straight exploding roll, no advantage/disadvantage.

| DC  | d4    | d6    | d8    | d10   | d12   | d20   |
| --- | ----- | ----- | ----- | ----- | ----- | ----- |
| 5   | 25.0% | 33.3% | 50.0% | 60.0% | 66.7% | 80.0% |
| 10  | 4.7%  | 8.3%  | 10.9% | 10.0% | 25.0% | 55.0% |
| 15  | 0.8%  | 1.9%  | 3.1%  | 6.0%  | 6.9%  | 30.0% |

Full 1–20 DC range and multi-die pools: [Dice Probability Reference](../Mechanics/Dice%20Probability%20Reference.md).

## What Advantage / Disadvantage Buys You

Median and 90th-percentile total, by roll type:

| Die | Median (Normal / Adv / Disadv) | 90th %ile (Normal / Adv / Disadv) |
| --- | --- | --- |
| d4 | 2 / 3 / 2 | 7 / 9 / 3 |
| d6 | 3 / 5 / 2 | 9 / 11 / 5 |
| d8 | 4 / 6 / 3 | 10 / 13 / 6 |
| d10 | 5 / 8 / 3 | 9 / 15 / 7 |
| d12 | 6 / 9 / 4 | 11 / 17 / 9 |
| d20 | 10 / 15 / 6 | 18 / 19 / 14 |

Advantage pushes the whole curve up; disadvantage pulls it down — bigger dice swing harder in both directions.

---

## Initiative

- Roll Prowess (exploding) once per combat — holds for the whole fight, all rounds.
- Some abilities allow rolling Instinct instead ([Quick](../Mechanics/Abilities.md#quick)).
- **Ties**: bigger Prowess die wins (d12 beats d8) regardless of roll. Same die size → GM decides.
- All combat actions are Snap Decisions by default (no Determination Token assist) unless an ability says otherwise.

---

## Alignment — DC × Tier Lookup

| Tier | DC change |
| --- | --- |
| Enemy | +20% (roll at disadvantage too) |
| Misaligned | +20% |
| Neutral | none |
| Aligned | −20% |
| Ally | −20% (roll at advantage too) |

Everyone starts **Misaligned** by default with a faction they've never met; a shared racial identity bumps the starting tier up by one before anything else applies.

Precomputed adjusted DC, base DC 1–20 (do not recompute at the table):

| Base DC | Enemy / Misaligned | Neutral | Aligned / Ally |
| --- | --- | --- | --- |
| 1 | 2 | 1 | 1 |
| 2 | 3 | 2 | 1 |
| 3 | 4 | 3 | 2 |
| 4 | 5 | 4 | 3 |
| 5 | 6 | 5 | 4 |
| 6 | 7 | 6 | 5 |
| 7 | 8 | 7 | 6 |
| 8 | 10 | 8 | 6 |
| 9 | 11 | 9 | 7 |
| 10 | 12 | 10 | 8 |
| 11 | 13 | 11 | 9 |
| 12 | 14 | 12 | 10 |
| 13 | 16 | 13 | 10 |
| 14 | 17 | 14 | 11 |
| 15 | 18 | 15 | 12 |
| 16 | 19 | 16 | 13 |
| 17 | 20 | 17 | 14 |
| 18 | 22 | 18 | 14 |
| 19 | 23 | 19 | 15 |
| 20 | 24 | 20 | 16 |

---

## See also

- [Questing Time! Mechanics](../Mechanics/Questing%20Time!%20Mechanics.md) — full rules text.
- [Dice Probability Reference](../Mechanics/Dice%20Probability%20Reference.md) — full probability math: per-die distributions, DC lookups, degrees of success, opposed-roll odds, and methodology.
- The session's **crib** — where the party is, who is in front of them, and what is live tonight. It lives in `tmp/crib/`, outside the link graph.
