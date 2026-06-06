# Confidence Rubric

*The grading detail for the [Source-Traceable Claim Ledger](METHOD.md). Two axes — **kind** and **grade** — and a deterministic procedure for assigning the grade from the ledger's own fields.*

**Method version 1.0**

---

## Axis 1 — `kind` (what the claim is)

| Kind | Test | If unsure |
|------|------|-----------|
| **`direct`** | Could you point to a sentence in the source that asserts this, and copy it? | If you'd have to *calculate* it → `derived`. If you'd have to *decide* it → `editorial`. |
| **`derived`** | Did you produce this by combining other claims (sum, count, %, rollup)? | Record the exact `formula`. The inputs must themselves be claims in the ledger. |
| **`editorial`** | Is this a label, grouping, lens, or mapping *you* chose, not the source? | Record the `rule` you applied, phrased so a reader can disagree. |

A claim has exactly one kind. When a number is both quoted *and* re-aggregated (e.g. you quote a total and also re-sum the parts), enter two rows: the quoted total (`direct`) and your recomputation (`derived`).

---

## Axis 2 — `grade` (how well-supported)

| Grade | Name | Meaning |
|-------|------|---------|
| **A** | Corroborated | Source-faithful **and** independently confirmed. The strongest grade. |
| **B** | Verified, single-source | Source-faithful, but only the source says it. |
| **C** | Source-flagged / volatile | The source hedges, estimates, or contradicts itself. True-to-source, soft-in-fact. |
| **D** | Editorial (rule-based) | A defensible interpretation with a stated, consistent, reversible rule. |
| **U** | Unverified / pending | Tracked, not yet checked this cycle. |
| **F** | Disputed | Verification failed or sources conflict, unresolved. |

---

## The decision procedure (deterministic)

Apply in order; the first matching rule sets the grade. This is the function that makes confidence **reproducible** — re-run it on the ledger fields and you get the same letters.

```
1.  kind == editorial?
        → rule present AND applied consistently AND reversible by reader?
              → D
          else → F            (an editorial claim with no stated rule is not publishable)

2.  not checked this cycle (no verification entry in checks[])?
        → U

3.  source carries a hedge/estimate/qualifier, OR source is internally inconsistent?
        (markers: "proposed", "estimated", "up to", "where appropriate",
         "at times", "explore", "assess", "review", "being finalized", "some estimates")
        → C            (record the hedge phrase in source.quote)

4.  primary-source match CONFIRMED this cycle (or by a recorded prior extraction check)?
        → ≥1 independent corroboration with agrees == true?
              → A
          else → B

5.  otherwise (primary match failed, or corroborators disagree and it's unresolved)
        → F
```

Notes on the procedure:
- **Hedge beats corroboration.** A figure the source itself calls "proposed" is `C` even if three outlets repeat it — because they're repeating a proposal. The grade describes the *firmness of the underlying fact*, not how widely the number circulates.
- **`derived` grades inherit.** A sum is graded by its weakest input and the correctness of the arithmetic: all-A inputs + verified formula → A; any B input → B; any C input → C (the total is as soft as its softest part); a U input → U until that input is checked.
- **A requires independence.** Corroboration by a source that is just re-publishing the issuer's press release is not independent; mark `agrees: true` only for genuinely separate reporting/data.

---

## What counts as a "check"

Every grade above U rests on at least one recorded entry in the claim's `checks[]`. Each entry names its **stage**, **method**, **actor**, **date**, and **result**:

| Stage | Typical method | Produces |
|-------|----------------|----------|
| `extraction` | Read source, transcribe the figure (the original build pass) | the claim + provenance |
| `verification` | `recompute` (derived) · `source-match` (direct vs. primary) · `hedge-quote` (the qualifier is in the source) · `pending` | confirm / dispute / pending |
| `adjudication` | A human resolves an extractor↔verifier disagreement | the final grade + sign-off |

**The independence requirement** lives here: a `verification` entry carries weight only if it was produced independently of the `extraction` entry — a different actor, or a separate model run prompted to *refute* rather than confirm. Record the actor honestly (`human:<name>`, `ai:recompute`, `ai:independent-pass`) so a reader can judge how independent the check really was.

---

## Worked examples (from this project)

| Claim | kind | grade | Why |
|-------|------|-------|-----|
| "$2.36B new named commitments" | `derived` | **A/B** | Σ of the 10 new line-items; arithmetic recomputed this cycle (`confirm`). Grade follows the inputs. |
| "16 named dollar line-items" / "31 concrete programs" / "17 of 31 programs unfunded (55%)" | `derived` | **B** | Counts recomputed from the data this cycle. Pure arithmetic over the dataset. |
| "$500M BDC LIFT program" | `direct` | **A or B** | Matches the source; **A** if an independent source (e.g. BDC) confirms, else **B**. |
| "$130M commercialization programs, National AI Institutes" | `direct` | **B** | Source-faithful, but the strategy is the only place it appears. |
| "850 MW → 2.3 GW sovereign compute, proposed by 2030" | `direct` | **C** | The source says "proposed … up to" and partnerships are "being finalized." Soft by the source's own words. |
| "~$187B generative-AI upside" / "5.5 GW compute needed" | `direct` | **C** | The source attributes these to "some estimates"/"analysis suggests" — projections it hedges, not commitments. |
| Five priority sectors (not six) | `direct` | **C→B** | Source is internally inconsistent (enumerates five, later says six). Flagged `C` for the conflict; resolved to the enumerated five with a note. |
| The **Funded / Soft / Unfunded** lens | `editorial` | **D** | Our rule: "funded" = a named dollar figure is attached. Written down, applied to every item, reversible by the reader. |
| Unfunded **categories** (Law & rights, Standards & trust, …) | `editorial` | **D** | Our groupings of unpriced items, not the government's. Rule stated; consistently applied. |
| Persona → program mapping (who each program is "for") | `editorial` | **D** | Our reading of which audience each program touches. Defensible, not in the source as a mapping. |

---

## Displaying the grade

On each claim, show both axes: **`Direct · A`**, **`Derived · B`**, **`Direct · C`**, **`Editorial · D`** (label it "rule-based"), **`Direct · U`**. Colour by grade (A green, B blue, C amber, D slate/neutral, U grey, F red). The badge links to the claim's ledger row so the locator, quote, corroboration, and checks are one click away.

The project's **Confidence** view tallies these live from the ledger: counts per grade, coverage (tracked vs. total claims), and the full list of every `C` and `U`/`F` — the claims a careful reader should look at first.
