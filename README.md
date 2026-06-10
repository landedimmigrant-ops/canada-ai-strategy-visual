# Canada's National AI Strategy — Visual Explorer

An interactive, single-file visual breakdown of [Canada's National AI Strategy: AI for All](https://ised-isde.canada.ca/site/ised/en/canadas-national-artificial-intelligence-strategy-ai-all) (ISED, June 2026).

**Open `index.html` in any browser — no build, no dependencies, works offline.**

## What's inside

Nine tabs, driven by a shared sidebar with search and value/pillar filters:

- **Overview** — the architecture: three values (Trust, Opportunity, Sovereignty) carrying six pillars, plus the five priority sectors. Click a pillar for its themes and key actions.
- **By audience** — pick who you are (SME owner, founder, student, mid-career worker, researcher, creator, Indigenous communities, public servant) and see the programs that touch you, grouped by pillar.
- **Opportunities** — eight gap → response pairings, above the full catalogue of every concrete program, grouped by pillar with *live now* listed before *announced*.
- **Funded commitments** — the named dollars: a ribbon diagram tracing money from values → pillars → programs ($2.36B new, ~$6.2B leveraged), with line-by-line bars.
- **Soft commitments** — promises the strategy hedges in its own words ("where appropriate," "explore," "proposed"), grouped by type of hedge.
- **Unfunded commitments** — every commitment with no named dollar figure (laws, standards, diplomacy, infrastructure), navigable by category.
- **Targets** — headline tiles and baseline → target dumbbells (12% → 60% business adoption by 2034, 130 → ~200 CIFAR chairs, 0 → 850 MW sovereign compute by 2030).
- **Timeline** — every launch, dollar and target from Budget 2025 to 2050; click any entry for context.
- **Methodology** — how it was made: source, classification rules, the accuracy check, and caveats.

Together the **Funded → Soft → Unfunded** tabs form a spectrum of commitment strength. Every card links back ("read more ↗") to the relevant pillar section of the official strategy.

## Methodology

A full methodology and transparency note lives in the **Methodology** tab: the single source and how
figures were corroborated, the classification rules (funded vs. unfunded, new vs. leveraged, what counts as
a "soft" commitment), the line-by-line accuracy check against the official PDF, and the honest caveats.
The analytical lenses (Funded / Soft / Unfunded) are our interpretation, built to make the gap between
rhetoric and dollars legible — not the government's framing.

It was researched, structured and fact-checked with **AI assistance — Anthropic's Claude (Opus 4.8)** —
under human direction. Because the strategy is recent, figures were taken from the source document itself
(not the model's prior knowledge), corroborated against public sources, and verified line-by-line; every
item links back to the strategy so any claim can be audited rather than trusted.

## Fact-checking method & verification

This project doubles as a worked example of a reusable fact-checking method: the
**Source-Traceable Claim Ledger (STCL)**. Instead of asserting "we checked it," every tracked claim
is a row in [`ledger.json`](ledger.json) — traced to an exact place in the source and labelled — so
anyone can replay the checks.

- **[`METHOD.md`](METHOD.md)** — the protocol: Atomize → Cite → Corroborate → Grade → Sign-off.
- **[`confidence-rubric.md`](confidence-rubric.md)** — the two-axis labelling: **kind** (direct / derived / editorial) × **basis** (corroborated · per the source · qualified by the source · recomputed · our analysis · unverified · disputed) — categories, not a graded scale — with a deterministic procedure so the labels are reproducible, not asserted.
- **[`ledger.schema.json`](ledger.schema.json)** + **[`ledger.template.json`](ledger.template.json)** — the portable, source-agnostic artifact to reuse on the next strategy/report → visual project.

The in-page **Verification** tab is generated live from the ledger: it tallies the per-category distribution,
surfaces the flagged (C) and pending (U) claims first, and links every figure's badge to its record.
To reuse the method elsewhere, copy the four kit files, declare the new source, and fill the ledger —
the protocol doesn't change, only the claims do.

> Verified June 6, 2026: every claim was put through an independent pass — three verifier agents
> re-fetched the official source blind to the labels and re-derived each quote, headline dollar figures
> were corroborated against outside sources, and the one initially-disputed claim was adjudicated and
> confirmed. Current state: **0 pending, 0 disputed** (6 A · 25 B · 15 C · 6 D).

`ledger.json` is the authoritative record; `index.html` inlines a compact mirror (`const LEDGER`) so
the badges and Verification tab work offline, regenerated from `ledger.json`.

## Sharing via GitHub Pages

The entry file is named `index.html`, so with **Settings → Pages → Deploy from branch** the visual is live
at `https://<username>.github.io/<repo>/`.

## Source

All figures, targets and dates were extracted from the ISED strategy (web page + 29-page PDF) on
June 5, 2026, and verified line-by-line against the source. Amounts in CAD unless noted.
This is an unofficial visualization, not a Government of Canada product.
