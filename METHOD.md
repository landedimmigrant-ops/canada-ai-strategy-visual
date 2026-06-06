# The Source-Traceable Claim Ledger (STCL)

*A reusable, transparent method for fact-checking a visual guide built from a strategy or report — and for stating how confident you are in every number on the screen.*

**Version 1.0 · June 2026**

---

## 0. Why this exists

When you turn a long government strategy or corporate report into an interactive visual, you make hundreds of small factual assertions — a dollar figure here, a date there, a percentage, a category label. A reader has no way to tell which of those you copied verbatim, which you calculated, and which you interpreted. "Trust me, I checked it" is not a method; it can't be audited, it can't be reused, and it can't be published as anything more than an assurance.

This method replaces the assurance with an **artifact**: a published, machine-readable ledger in which every claim in the visual is one row, traced to an exact place in the source, graded for confidence by a written rule, and stamped with who checked it and how. Anyone can re-run the checks against the ledger and get the same grades. That is what makes the work **transparent** (it's all in the open), **traceable** (pixel → ledger row → source quote), **confidence-bearing** (every claim carries a grade), and **publishable & reusable** (the protocol and schema don't depend on any one report).

The method is deliberately boring and mechanical. Boring is the point — boring is reproducible.

---

## 1. The core idea

> **Fact-checking is not an event you perform once; it is a standing artifact you maintain.**

The artifact is the **claim ledger** (`ledger.json`): one row per atomic claim. The visual reads the ledger to show a confidence badge on each claim; the ledger lives in version control so its full history is the audit trail. Confidence is **computed from the ledger's own fields by a published rule** — never asserted by hand — so the grade is reproducible, not editorial.

---

## 2. The unit of work: the atomic claim

A **claim** is a single checkable assertion — one number, one date, one name, one status, one relationship. "Up to 90,000 AI placements for young Canadians by 2031" is one claim. "$2.36B in new funding across 16 line-items" is *two* claims (a total, and a count). Atomize until each row can be true or false (or, for framing, defensible or not) on its own.

Every claim is exactly one of three **kinds**, because "confidence" means something different for each:

| Kind | Definition | Example |
|------|------------|---------|
| **`direct`** | Asserted *by the source*. A figure, date, name, or phrase copied (verbatim or near-verbatim) from the primary document. | "$500M BDC LIFT program" |
| **`derived`** | Computed *by you* from `direct` claims via a stated formula — a sum, count, percentage, or rollup. | "$2.36B new" = Σ line-items where `new` |
| **`editorial`** | *Your* framing, classification, or grouping. Not present in the source as such. | The Funded / Soft / Unfunded lens; persona→program mapping |

The single most common methodological error is grading an `editorial` claim as if it were `direct` — defending an interpretation as a "fact." Keeping the kind explicit prevents it.

---

## 3. The pipeline

Five stages, applied to every claim. Mnemonic: **Atomize → Cite → Corroborate → Grade → Sign-off.**

### 3.1 Atomize
Decompose the visual's content into atomic claims. Give each a **stable id** that also identifies it in the visual's data (the join key — see §5). Record the human-readable `claim` text and which views render it.

### 3.2 Cite (provenance)
For every `direct` claim, record **claim-level** provenance — not a link to the whole document, but:
- a **locator**: the most precise pointer the source allows (PDF page + section heading, or a web anchor), and
- a **verbatim quote**: the exact sentence(s) in the source that carry the claim (the *evidence span*).

For `derived` claims, record the **formula** instead. For `editorial` claims, record the **rule** (the classification criterion, stated so a reader can disagree with it).

The verbatim quote is the heart of traceability. A locator tells the reader where to look; the quote lets them check without leaving the page, and freezes the evidence even if the source later changes.

### 3.3 Corroborate
For `direct` claims that can be independently checked, record one or more **secondary sources** and whether each **agrees**. Corroboration catches two different errors: *extraction* errors (you mis-copied) and *source* errors (the document itself is wrong). Brand-new commitments often have no independent source yet — that is itself a finding (it caps the grade at B; see the rubric).

### 3.4 Grade
Assign a confidence grade by the **decision procedure** in `confidence-rubric.md`. Crucially, the grade is a *function of the fields already recorded* (kind, source-match result, corroboration count, hedge flag) — so it is deterministic and re-derivable. Two people grading the same ledger row get the same letter.

### 3.5 Sign-off (independent verification)
This is the stage that turns "I checked it" into something publishable. The claim is verified by a **second pass that is independent of the first** — a different person, or a different model run, ideally blind to the first pass's grade — which re-checks the claim against the source and either **confirms** or **disputes** it. Disagreements are logged and **adjudicated** by a human, who signs off. Every check (extraction, verification, adjudication) is recorded in the row's `checks[]` with its method, actor, date, and result.

> **Integrity rule:** never record a check that did not happen. An unverified claim is graded **U** (pending) and shown as such. A disputed claim is graded **F** and surfaced loudly. A ledger that honestly shows its gaps is more trustworthy than one that claims false completeness — and the gaps are simply the next cycle's to-do list.

---

## 4. Confidence: a two-axis model

Each claim carries **two** labels, shown together on its badge (e.g. `Direct · A`):

- **Axis 1 — kind**: `direct` / `derived` / `editorial` (what the claim *is*).
- **Axis 2 — grade**: how well-supported it is, *interpreted for that kind*.

| Grade | Name | Holds when |
|-------|------|-----------|
| **A** | Corroborated | `direct` matches the primary source **and** ≥1 independent source agrees (or `derived` from A/B inputs with a verified formula). |
| **B** | Verified, single-source | Matches the primary source, but not independently corroborated — often because the issuer is the only possible source. |
| **C** | Source-flagged / volatile | The source itself hedges, estimates, or contradicts itself. Verified as *what the source says*; the underlying fact is soft. Carries the hedge quote. |
| **D** | Editorial (rule-based) | An `editorial` claim whose rule is written down, applied consistently, and reversible by the reader. Not true/false — defensible. |
| **U** | Unverified / pending | Tracked but not yet checked this cycle. An honest placeholder, not a failure. |
| **F** | Disputed | Failed verification, or sources conflict and it isn't resolved. Should be ~0 at publish; always surfaced. |

Two axes instead of one number is a deliberate choice: collapsing fact and framing into a single "87% confident" hides exactly the distinction a careful reader needs. The full decision procedure (how the fields determine the grade) is in **`confidence-rubric.md`**.

---

## 5. The artifact and the traceability chain

The ledger is a single JSON file validated by **`ledger.schema.json`**. Each row's `id` is the **join key** that closes the loop:

```
a pixel on screen   →   the data item that renders it   →   LEDGER[id]   →   source.quote + locator   →   the source document
   (the badge)            (e.g. a MONEY line-item)         (grade, checks)     (verbatim evidence)
```

Because the `id` appears both in the visual's data and in the ledger, every claim the reader sees can be walked back to the exact words in the source — and forward from any ledger row to where it appears. The ledger is committed to version control, so `git log -- ledger.json` is a complete, timestamped record of every change to every claim and grade.

**Offline note.** If the visual must run from `file://` with no server (a common requirement for a self-contained `index.html`), inline the ledger as a `const LEDGER` literal in the page so badges work with no fetch, and keep `ledger.json` as the published, identical copy for auditors and reuse. Treat one as the source of truth and regenerate the other; note which in the project's README.

---

## 6. Transparency & publishing

A project using this method publishes, alongside the visual:
1. **`ledger.json`** — the filled claim ledger (this project's facts).
2. **`METHOD.md`** — this protocol (so the method itself is inspectable).
3. **`confidence-rubric.md`** — the grading criteria and decision procedure.
4. A **confidence summary** in the visual — distribution of grades, coverage (claims tracked vs. total), and a list of every C and U/F claim. This is the public-facing transparency dashboard; it should be generated *from* the ledger, never written by hand.

Publishing the rubric and the ledger together is what lets a third party reproduce your confidence grades rather than take them on faith.

---

## 7. Reusing this on the next report

The method is source-agnostic. To apply it to a new strategy or report:

1. **Copy the kit** — `METHOD.md`, `confidence-rubric.md`, `ledger.schema.json`, `ledger.template.json` — into the new project.
2. **Declare the source(s)** in `ledger.template.json`'s `meta` block (title, URL, retrieval date).
3. **Atomize** the new content into claims as you build the visual; assign each a stable id.
4. **Cite, corroborate, grade** each claim into the ledger.
5. **Run the independent second pass** and adjudicate disagreements.
6. **Wire the badges + confidence summary** into the visual (the join-key pattern in §5 is the only integration code).
7. **Publish** the visual with its ledger.

Nothing in steps 1, 2, 5, 6, 7 changes between projects. Only the claims (steps 3–4) are new each time. That is the reuse.

---

## 8. Limits & honest caveats

- **The ledger checks fidelity to the source, not the truth of the source.** A `direct · A` grade means "the document says this and others report it too," not "this dollar will be spent." Auditing the underlying reality is a different (harder) exercise; say so.
- **`editorial` claims can be excellent and still be `D`.** The grade is honesty about *kind*, not a quality penalty. A well-built lens is the most valuable thing in the visual; it is still your reading, not the source's.
- **Coverage is rarely 100% on the first cycle**, and shouldn't pretend to be. Report it. The `U` rows are the backlog.
- **Independence is what gives the grade its weight.** A second pass run by the same author with the same assumptions corroborates little. Separate the roles — different person, or at minimum a different model run prompted to *refute* — or downgrade your confidence in the confidence.
- **Snapshots go stale.** A strategy under "review and update" will drift from the ledger; stamp the retrieval date and treat the ledger as living.

---

## 9. Change control

- Bump the method **version** (top of this file) only when the pipeline or rubric changes; record it in each ledger's `meta.method`.
- Treat any change to a claim's grade as a reviewable event — it's in `git` either way, but a one-line reason in `notes` makes the history readable.
- When the source document is revised, re-run Cite → Sign-off for affected claims and date the new checks; don't silently overwrite the old evidence span.

---

*This document is the method. `confidence-rubric.md` is the grading detail. `ledger.schema.json` defines the artifact. `ledger.template.json` is an empty starting point. Together they are the reusable kit.*
