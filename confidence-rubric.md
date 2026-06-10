# Basis Rubric

*The labelling detail for the [Source-Traceable Claim Ledger](METHOD.md). Two axes — **kind** and **basis** — and a deterministic procedure for assigning the basis from the ledger's own fields. The basis is a **category, not a graded scale** (no A–F): a claim the source merely hedged is not "worse" than one stated firmly — it is a different kind of statement.*

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

## Axis 2 — `basis` (how the claim is grounded)

Categories, not a ranking. The first four describe how a *source* statement is grounded; the next two are *our* contributions; the last two are open states.

| Basis | What it means |
|-------|---------------|
| **`corroborated`** | Confirmed against the source **and** an independent outside source agrees. |
| **`per-source`** | A `direct` statement, confirmed word-for-word against the source — but only the source says it. |
| **`qualified`** | A `direct` statement the source's own wording hedges, estimates, or contradicts itself on. Verified verbatim — the qualification is the source's, not ours. |
| **`recomputed`** | A `derived` figure (total, count, share) we computed from the data and re-derived this cycle. |
| **`our-analysis`** | An `editorial` framing, lens, or grouping — a stated, consistent, reversible rule. Defensible, not a source claim. |
| **`unverified`** | Tracked, but not yet checked this cycle. An honest placeholder, not a failure. |
| **`disputed`** | Verification failed, or sources conflict, unresolved. Should be none at publish; always surfaced. |

---

## The decision procedure (deterministic)

Apply in order; the first matching rule sets the basis. This is the function that makes the labelling **reproducible** — re-run it on the ledger fields and you get the same categories.

```
1.  kind == editorial?
        → rule present AND applied consistently AND reversible by reader?
              → our-analysis
          else → disputed        (an editorial claim with no stated rule is not publishable)

2.  not checked this cycle (no verification entry in checks[])?
        → unverified

3.  source carries a hedge / estimate / qualifier, OR is internally inconsistent?
        (markers: "proposed", "estimated", "up to", "where appropriate",
         "at times", "explore", "assess", "review", "being finalized", "some estimates")
        → qualified              (record the hedge phrase in source.quote)

4.  primary-source match CONFIRMED this cycle (or by a recorded prior extraction check)?
        → ≥1 independent corroboration with agrees == true?
              → corroborated
          else → (kind == derived ? recomputed : per-source)

5.  otherwise (primary match failed, or corroborators disagree and it's unresolved)
        → disputed
```

Notes on the procedure:
- **Hedge beats corroboration.** A figure the source itself calls "proposed" is `qualified` even if three outlets repeat it — they're repeating a proposal. The basis describes the *firmness of the underlying statement*, not how widely the number circulates.
- **`derived` claims inherit.** A computed figure is grounded by its inputs and the correctness of its arithmetic: confirmed by an outside source → `corroborated`; otherwise `recomputed`; if an input is `qualified` or `unverified`, the total is no firmer than that input.
- **`corroborated` requires independence.** A source that just re-publishes the issuer's press release is not independent; set `agrees: true` only for genuinely separate reporting or data.

---

## What counts as a "check"

Every basis other than `unverified` rests on at least one recorded entry in the claim's `checks[]`. Each entry names its **stage**, **method**, **actor**, **date**, and **result**:

| Stage | Typical method | Produces |
|-------|----------------|----------|
| `extraction` | Read source, transcribe the figure (the original build pass) | the claim + provenance |
| `verification` | `recompute` (derived) · `source-match` (direct vs. primary) · `hedge-quote` (the qualifier is in the source) · `pending` | confirm / dispute / pending |
| `adjudication` | A human resolves an extractor↔verifier disagreement | the final basis + sign-off |

**The independence requirement** lives here: a `verification` entry carries weight only if it was produced independently of the `extraction` entry — a different actor, or a separate model run prompted to *refute* rather than confirm. Record the actor honestly (`human:<name>`, `ai:recompute`, `ai:independent-pass`) so a reader can judge how independent the check really was.

---

## Worked examples (from this project)

| Claim | kind | basis | Why |
|-------|------|-------|-----|
| "$2.36B new named commitments" | `derived` | **corroborated** | Σ of the 10 new line-items, recomputed this cycle, and matched by KPMG ("more than $2.3 billion"). |
| "16 named dollar line-items" / "31 concrete programs" / "17 of 31 unfunded (55%)" | `derived` | **recomputed** | Counts re-derived from the data this cycle. Pure arithmetic over the dataset. |
| "$500M BDC LIFT program" | `direct` | **corroborated** | Matches the source, and BDC's own release confirms the $500M program. |
| "$130M commercialization programs, National AI Institutes" | `direct` | **per-source** | Confirmed verbatim, but the strategy is the only place it appears. |
| "850 MW → 2.3 GW sovereign compute, proposed by 2030" | `direct` | **qualified** | The source says "proposed … up to" and partnerships are "being finalized." Hedged in the source's own words. |
| "~$187B generative-AI upside" / "5.5 GW compute needed" | `direct` | **qualified** | The source attributes these to "some estimates" / "analysis suggests" — projections it hedges, not commitments. |
| Five priority sectors (not six) | `direct` | **qualified** | Source is internally inconsistent (enumerates five, later says six). Flagged for the conflict; we use the enumerated five with a note. |
| The **Funded / Soft / Unfunded** lens | `editorial` | **our-analysis** | Our rule: "funded" = a named dollar figure is attached. Written down, applied to every item, reversible by the reader. |
| Persona → program mapping (who each program is "for") | `editorial` | **our-analysis** | Our reading of which audience each program touches. Defensible, not a mapping the source provides. |

---

## Displaying the basis

On each claim, show both axes as words — e.g. **`Direct · Corroborated`**, **`Direct · Per the source`**, **`Direct · Qualified by the source`**, **`Derived · Recomputed`**, **`Editorial · Our analysis`**. Colour distinguishes the categories but is **not** a green→red ladder; the labels carry the meaning. The badge links to the claim's ledger row so the locator, quote, corroboration, and checks are one click away.

The project's **Verification** view tallies these live from the ledger: a count per category, coverage (tracked vs. total claims), and the full list of every `qualified` claim (the source's own hedges) plus any `unverified`/`disputed` open items — what a careful reader should look at first.
