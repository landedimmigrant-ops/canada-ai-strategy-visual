# What has changed since "AI for All" launched

Research date: 2026-10-23. Baseline: the ledger was compiled 2026-06-05/06 against the ISED page as last modified 2026-06-04. The strategy was launched 2026-06-04.

How to read the labels (same spirit as the Verification tab):
- **Primary** means I opened an official Government of Canada page or a first-party release.
- **Secondary** means I read it in news or law-firm coverage, or on a partner's page, and did not see the official text.
- **Search only** means it showed up in a search result and I did not open it.

---

**Update, same day:** the low-risk status changes from section 3 have been applied to the visual and ledger (see "Applied" at the end). While doing that I read the AI literacy release, the VITAL release, the FedDev release and Parliament's bill pages directly, so several rows below were upgraded from secondary to primary. Where this file and the visual disagree, the visual and `ledger.json` are current.

---

## Bottom line

1. **The strategy text itself has barely moved.** The ISED page now says "Date modified: 2026-06-08". I re-checked it live against the ledger. 31 of 39 quotes matched as written. I read the other 8 by eye against the live page and the substance is the same. One has a wording difference (Job Bank, below). No dollar figure, target or date in the ledger has changed.
2. **The action since June is delivery, not revision.** Four things the strategy promised have now been formally launched or announced: regional AI funding, the VITAL data platform, the AI literacy initiative, and Mitacs work placements. Two new bodies exist that the strategy did not describe: a National Council on AI and Digital Transformation Canada. Two bills were tabled.
3. **No new headline money.** The only new named dollar figures are $13M (AI literacy) and up to $162M (Mitacs). Neither is confirmed as new money. Nothing changes the $2.36B new / ~$6.2B leveraged totals until that is settled.
4. **Three items need your decision before the visual is edited** (section 3): the educator target, the VITAL "five provinces" wording, and whether to carry the supercomputer's ~$890M program figure.
5. **Biggest upcoming checkpoint: Budget 2026 on Nov 5.** The strategy says Finance will "explore" reinvestment mechanisms for AI startups. Re-check the ledger the week after.

---

## 1. The strategy document itself

| Check | Result | Basis |
|---|---|---|
| ISED page "Date modified" | 2026-06-08 (we retrieved a 2026-06-04 version) | Primary |
| Ledger quotes vs live page | 31 matched exactly; 8 differed only by my matching method, and I confirmed each by eye against the live text | Primary |
| One real wording difference | **Job Bank.** The ledger quote says "Canada will invest $50 million over five years through Budget 2025 to modernize the Job Bank". The live page says "Canada is investing $50 million over five years through Budget 2025 to modernize the Job Bank" and adds that a national online training platform "has launched". The money is unchanged. This may be the June 8 edit, or it may have been a loose quote in the ledger. I cannot tell which. | Primary |
| "Five" vs "six" priority sectors | Still inconsistent on the live page. Pillar 2 still says Workforce Alliances span "six priority sectors" while the sector list has five. Already recorded in the ledger as `direct:five-sectors`. | Primary |
| What the June 8 edit was | **Not determined.** The Wayback Machine is blocked from this environment and I did not diff the PDF. | n/a |

Suggested follow-up: re-fetch the 29-page PDF and compare it to the web page to see if they still agree.

---

## 2. New decisions and initiatives (chronological)

| Date | What happened | Money | Status | Source |
|---|---|---|---|---|
| Jun 10 | **Bill C-34**, the Safe Social Media Act (enacts the Digital Safety Act and a Digital Safety Commission). First reading Jun 10. **In second-reading debate as of Oct 21.** | n/a | Not yet passed | Primary: [LEGISinfo C-34](https://www.parl.ca/legisinfo/en/bill/45-1/c-34). Also secondary: [DLA Piper](https://www.dlapiper.com/insights/publications/2026/06/canada-tables-bill-c36-the-protecting-privacy-and-consumer-data-act) |
| Jun 15 | **Bill C-36**, Protecting Privacy and Consumer Data Act; its long title also amends PIPEDA. DLA Piper reports it replaces Part 1 of PIPEDA, requires disclosure of automated decision-making with "legal or similarly significant effect", sets a higher standard for children's data, and carries administrative penalties up to the greater of $10M or 3% of global revenue (secondary only). **First reading Jun 15; second reading has had no activity as of Oct 23.** | n/a | Not yet passed | Primary for status: [LEGISinfo C-36](https://www.parl.ca/legisinfo/en/bill/45-1/c-36). Secondary for provisions: [DLA Piper](https://www.dlapiper.com/insights/publications/2026/06/canada-tables-bill-c36-the-protecting-privacy-and-consumer-data-act) |
| Jun 23 | **VITAL: $100M announced** in Toronto by Minister Solomon and Parliamentary Secretary Maggie Chi. First phase links 160 hospitals in Ontario, Alberta and Quebec (20M+ Canadians). | $100M | Announced. No dates. | Primary: [ISED release](https://www.canada.ca/en/innovation-science-economic-development/news/2026/06/government-of-canada-invests-100-million-in-vital-health-data-platform.html) |
| Sep 3 | **Digital Transformation Canada** launched, led by CEO Patrick Pichette. Merges Shared Services Canada with selected Treasury Board Secretariat and Public Services and Procurement Canada functions and the Canadian Digital Service. Minister: Joël Lightbound. The release names the strategy's anchor-customer commitment in a background paragraph and lists using purchasing power to help Canadian AI firms scale among its priorities, but **does not say the new body delivers that commitment** (my first wording overstated this; corrected after independent verification). Also a fellowship model for private-sector experts. | none stated | Launched | Primary: [PM release](https://www.pm.gc.ca/en/news/news-releases/2026/09/03/prime-minister-carney-launches-digital-transformation-canada-deliver) |
| Sep 9 (launch Sep 21) | **National AI Literacy Initiative launched** with the Alberta Machine Intelligence Institute (Amii). Three streams: Essentials for Students, Educators, and Canadians. Free three-hour course for post-secondary students from Sep 21. The Canadians stream launches Dec 4. | **$13M** | Launched | Primary: [ISED release, Edmonton, Sep 9](https://www.canada.ca/en/innovation-science-economic-development/news/2026/09/government-of-canada-launches-national-ai-literacy-initiative.html). The $13M appears in a minister's quoted statement in the release. The release says the initiative "is expected to reach up to one million post-secondary students and more than 50,000" K-12 educators. Also secondary: [BetaKit](https://betakit.com/canada-unveils-national-ai-literacy-initiative/), [HCA Mag](https://www.hcamag.com/ca/specialization/transformation/canada-launches-national-ai-literacy-initiative/589341), [Amii](https://www.amii.ca/updates-insights/amii-leads-national-ai-literacy-initiative). |
| Sep 25 | **Mitacs AI Advantage:** up to $162M over five years from 2026-27 for 10,000 co-funded AI work placements (ADOPT and AI+X streams). This is the "10,000 Mitacs ADOPT and AI+X" slice of the 90,000-placements target. | up to **$162M** | Announced. Whether it is new money is not stated. | Primary (partner): [Mitacs](https://www.mitacs.ca/news/government-of-canada-invests-in-10000-ai-related-work-placements-for-young-canadians/). Also [The Logic](https://thelogic.co/briefing/ottawa-awards-mitacs-162m-to-create-ai-focused-work-placements/) (search only). |
| Oct 2 | **Prime Minister's National Council on AI.** 12 people listed (the release states no count): Ajay Agrawal, Yoshua Bengio, Sanja Fidler, Gillian Hadfield, Jordan Jacobs, Eric Lamarre, Valérie Pisano, Senator Thomas Pitfield, Jody Thomas, Louis Vachon, Michelle Zatlyn, and Patrick Pichette (ex officio). Advises on adoption, national champions, sovereign infrastructure, AI safety and ensuring Canadians benefit. Supported by a small Privy Council Office team. Ministers stay accountable for decisions. The release names no chair, no meeting schedule and no budget. | none stated | Launched | Primary: [PM release](https://www.pm.gc.ca/en/news/news-releases/2026/10/02/prime-minister-carney-launches-new-national-council-artificial). Also [Dentons](https://www.dentons.com/en/insights/articles/2026/october/7/federal-government-launches-national-council-on-artificial-intelligence) (search only). |
| Oct 13 | **Regional AI Initiative expansion formally announced.** $500M over five years, total federal funding for the initiative $700M. Delivered through the regional development agencies. Priority sectors match the strategy. Deadlines: projects with eligible costs before Mar 31, 2027 are due Nov 24, 2026. Southern Ontario applications close Jan 19, 2027 (other regions' dates not given). Track record so far: 218 projects, 1,100+ jobs created or maintained. | $500M (already counted) | Open for applications | Primary: [FedDev Ontario / ISED release](https://www.canada.ca/en/economic-development-southern-ontario/news/2026/10/government-of-canada-expands-support-to-adopt-and-commercialize-artificial-intelligence.html) |
| Nov 5 (upcoming) | **Budget 2026** to be tabled Nov 5, per Finance Minister Champagne. PBO says deficits are deepening. The advisory does not mention AI. | ? | Pending | Primary: [Finance Canada media advisory, Oct 20](https://www.canada.ca/en/department-finance/news/2026/10/government-of-canada-to-release-budget-2026-on-november-5-2026.html). Also secondary: [The Hub](https://thehub.ca/2026/10/21/champagne-sets-nov-5-budget-date-as-watchdog-warns-deficits-are-deepening/) |

### Still pending, with no change found

- **Public AI supercomputer.** Applications to the AI Sovereign Compute Infrastructure Program closed June 1, 2026. The program page shows about $890M over seven fiscal years for the build layer, "notional and subject to negotiation". No selected proponent has been announced as of Oct 23. Simon Fraser and Queen's said they plan a joint bid (secondary, search only). Primary: [program page](https://ised-isde.canada.ca/site/ised/node/279), [Apr 15 launch release](https://www.canada.ca/en/innovation-science-economic-development/news/2026/04/canada-launches-national-initiative-to-build-large-scale-ai-supercomputing-capacity.html).
- **850 MW sovereign compute by 2030, scaling to 2.3 GW.** I found no federal announcement confirming finalized data-centre partnerships. One search summary says partnerships are being finalized (attributed to BetaKit). I could not open that article, so treat it as unverified. Private projects exist but are not federal commitments: Bell's non-binding Saskatchewan MOU for up to 900 MW (secondary: [Intelligent CIO](https://www.intelligentcio.com/north-america/2026/09/15/bell-ai-fabric-plans-1-2-gw-saskatchewan-ai-infrastructure-hub/), [Fierce Network](https://www.fierce-network.com/cloud/bell-canada-lengthens-its-sovereign-ai-lead-900-mw-expansion), search only) and a 320 MW HIVE project in the GTA (search only). The ledger's hedged label is still right.
- **Canadian Tech Growth Fund ($500M), Sovereign Wealth Fund, federal equity stakes.** No launch or first investment found. The Canada Strong Fund ($25B) was announced in April 2026, before the strategy, and AI is not named as a core sector (secondary, search only).
- **Trusted AI Certification, Workforce Alliances, AI Missions Program (the $200M health mission), Health Sector Data Space with CIHI, CAISI expansion ($50M), Standards Council program, Prime Minister's Innovation Fellows.** No launch or call for proposals found for any of them.
- **Canada-Germany Sovereign Technology Alliance.** Launched Feb 14, 2026. No later milestone found.
- **CAISI.** Only a July 8, 2026 blog post on reporting AI evaluation results (search only). No leadership, funding or legislation news.

### Context that pre-dates the strategy but is not in the ledger

- **AI Compute Access Fund, first awards, May 12, 2026:** $66M to 44 projects, out of a $300M fund. The strategy's $700M "expansion" builds on this. Secondary: [BetaKit](https://betakit.com/feds-announce-66-million-for-44-businesses-through-ai-compute-access-fund/), [ISED release](https://www.canada.ca/en/innovation-science-economic-development/news/2026/05/government-of-canada-supports-44-canadian-companies-using-ai-to-transform-industries-and-create-jobs.html) (search only).
- **Large-scale data centre call (over 100 MW), Jan 2026:** submissions closed Feb 15, 2026. ISED said the resulting MOUs are not contracts and the $2B compute envelope will not fund them. Secondary: [BetaKit](https://betakit.com/feds-call-for-proposals-to-build-large-scale-data-centres-in-canada/). This is the likely route to the 850 MW figure.
- **Cohere:** up to $240M federal investment in a $725M project, announced Dec 2024. Secondary: [BetaKit](https://betakit.com/cohere-secures-federal-backing-to-build-multibillion-dollar-canadian-ai-data-centre/).

---

## 3. What this means for the visual and ledger (nothing edited yet)

Needs a decision:

1. **K-12 educator target.** The strategy says "more than 3,000 educators" (the 1,500 baseline in the visual is our reading of "doubling"). The official literacy release says the initiative is "expected to reach" more than 50,000 K-12 educators. These may measure different things (trained vs reached). Neither figure is overwritten. **Status: flagged in amber on the Targets tab and the literacy card; unresolved.**
2. **VITAL "five additional provinces".** The strategy says $100M to expand VITAL in five additional provinces. I read the June 23 release in full: it says the first phase covers Ontario, Alberta and Quebec and the platform "could expand to additional provinces and territories over the coming months". It does not mention "five". **Status: flagged on the VITAL card; unresolved. The ledger claim is unchanged.**
3. **Supercomputer money.** The strategy lists the supercomputer with no dollar figure, so the ledger counts it as unfunded. ISED's program page names about $890M (notional, seven fiscal years). The strategy does not name that program, so linking the two is our reading. One aggregator lists $705M instead, which conflicts and looks unreliable. **Status: flagged on the supercomputer card; stays under Unfunded.**

Likely status changes (low risk):

| Item | Was | Now |
|---|---|---|
| Regional AI Initiative ($500M) | announced | open for applications; deadlines above |
| VITAL ($100M) | announced | announced again with first-phase scope |
| National AI Literacy Initiative | no dollar figure | launched, $13M with Amii (secondary) |
| Mitacs ADOPT and AI+X placements | no dollar figure | up to $162M announced (new vs existing unknown) |
| Governance | none described | National Council on AI exists; Digital Transformation Canada exists |
| Privacy and online-safety law | "continue its review" / soft language | two bills tabled (C-34, C-36). Note C-36 covers the private-sector law (PIPEDA). The strategy's soft claim is about the Privacy Act, which governs federal institutions. They are different laws, so that ledger claim is not resolved by C-36. |

Possible framing drift (minor): the Oct 2 PM release says "an additional $200 billion in economic growth over five years". The strategy frames about $200B as roughly a 3% GDP uplift from labour productivity. Same headline number, possibly a different horizon. Based on a summary of the release, so check the wording before acting.

Totals: do not change the $2.36B / ~$6.2B / "17 of 31 unfunded" headline counts yet. Adding $13M and $162M changes the counts, and whether they are new money is the open question.

---

## 4. Limits of this check

- The search tool is US-only and returned summaries. Several details above come from summaries of pages I could not read in full (CTV truncated, Fierce Network blocked with a 403, Wayback blocked).
- I only compared the live web page to the ledger. I did not re-compare the PDF.
- Facts about the bills' progress are as read from LEGISinfo on 2026-10-23 and will go stale. The details of C-36's provisions rest on DLA Piper only; the visual does not repeat them.
- The new ledger rows were first read in one AI pass, then independently re-read by three blind verifier agents (section 6). The verifiers are the same kind of model as the one that built the page, and the human sign-off step has still not been given.
- Absence of news is not proof nothing happened. "No launch found" means my searches did not surface one.
- Nothing here has had the human sign-off step from the STCL method.

## 5. Applied to the visual and ledger (2026-10-23)

Changed:
- **Status:** Regional AI Initiative expansion and National AI Literacy Initiative moved from "announced" to "live now".
- **Dated Update notes** (green) on the cards for: Regional AI Initiative, National AI Literacy Initiative, 90,000 placements (Mitacs), Government as anchor customer (Digital Transformation Canada), Modernize consumer privacy legislation (C-36), Online safety laws (C-34), Continue the Privacy Act review (C-36 amends a different law), Budget 2026 reinvestment mechanisms (Nov 5).
- **Open-question notes** (amber, nothing resolved) on: VITAL expansion, World-leading public supercomputer, National AI Literacy Initiative and the K-12 educators dumbbell on Targets.
- **Timeline:** new "Since launch" group with eight dated entries. Money badges there are grey and read "already counted" or "not in totals".
- **Overview:** one-paragraph as-of note under the headline tiles. Methodology (sections 2, 4, 10, 11) and the page footer say post-launch updates run through Oct 23, 2026.
- **Ledger:** ten new rows with ids starting `post:`, each with a verbatim quote from the official page, plus appended notes on six existing rows. Basis labels were set by the same rubric: five "confirmed in the document", four "the government hedges this" (they say "up to", "could", "approximately" or "expected to"), and one "confirmed + corroborated" (the Budget 2026 date, once the official Finance Canada advisory was found). Existing rows' bases are unchanged.
- **Verification tab:** the summary still counts only the strategy's own 52 claims (0 open). The ten new rows are in a separate "Since launch" section, with a plain note describing the independent verification in section 6.

Not changed, on purpose:
- Headline totals: $2.36B new, $6.16B leveraged ("~$6.2B"), 16 named dollar line-items, 31 programs, 17 of 31 unfunded (55%).
- `MONEY`, every program's dollar amount, the Targets figures and the Soft-commitments list.
- The $13M (literacy) and up to $162M (Mitacs) appear only in notes and the timeline, not in any total or count.

Checked in the browser: no console errors; totals and counts as above; notes, timeline group, ledger dialog and Verification tab render.

## 6. Independent verification of the ten new rows (2026-10-23)

Method: three verifier agents, each given three or four claims as the reader sees them plus the source link. They were not shown our quotes or basis labels, and were told to try to refute each claim, to read the page themselves (browser or curl, never a summary tool) and to copy verbatim spans. I then compared their findings with the ledger and re-read the two items I changed.

| Row | Verdict | What the verifier found, and what changed |
|---|---|---|
| Regional AI Initiative open | Confirmed, with a qualification | The claim left out "over five years". Wording now includes it. |
| VITAL $100M | Confirmed, with a qualification | "could expand ... over the coming months" is the source's qualifier. No number of additional provinces appears anywhere on the page, which independently supports the open question. |
| Supercomputer program | Confirmed, with a qualification | "Approximately $890 million", "notional and subject to negotiation", and it covers building and ongoing operation, so the claim now says "build and operate". Funding is contingent on Parliament and Treasury Board. |
| Budget 2026 date | Confirmed | The verifier also found the official Finance Canada advisory (Oct 20). I read it myself. The row now cites it and is "confirmed + corroborated". |
| Digital Transformation Canada | **Disputed, reworded, re-confirmed** | Date and CEO match, but the release names the anchor-customer commitment only in a background paragraph and never says the new body delivers it. The claim and the card note were reworded; the ledger keeps the dispute then adjudication trail. |
| National Council on AI | Confirmed | The page states no count; 12 is our count of listed names (11 plus Pichette ex officio). No chair, meeting schedule or budget. |
| Mitacs placements | Confirmed | "Up to" qualifies the $162M, not the 10,000. Page metadata shows the page was modified Oct 6, after its Sep 25 publication. |
| AI Literacy Initiative | Confirmed | The $13M appears once, in a minister's quoted statement, not in the body text. |
| Bill C-34 | Confirmed | Latest activity is still Oct 21; nothing later as of Oct 23. |
| Bill C-36 | Confirmed, with a qualification | LEGISinfo lists no short title; the Act's name is only in the long title, so the wording is now "would enact". Its status line says "At second reading" beside "Second reading: No activity"; we read it as first reading done, no debate yet. |

Tally: five confirmed as worded, five with qualifications now in the wording, one of those a dispute (Digital Transformation Canada) that was reworded and re-confirmed. The three open questions in section 3 are unchanged and remain unresolved.

Limits of this check: the verifiers are the same kind of model as the one that built the page, they were shown the claim text (they had to know what to check), and the human sign-off step has not been given.

## 7. Source list

Primary (opened):
- [Finance Canada media advisory, Budget 2026 date, Oct 20](https://www.canada.ca/en/department-finance/news/2026/10/government-of-canada-to-release-budget-2026-on-november-5-2026.html)
- [ISED, AI for All strategy page](https://ised-isde.canada.ca/site/ised/en/canadas-national-artificial-intelligence-strategy-ai-all) (live, modified 2026-06-08)
- [PM release, National Council on AI, Oct 2](https://www.pm.gc.ca/en/news/news-releases/2026/10/02/prime-minister-carney-launches-new-national-council-artificial)
- [FedDev Ontario release, Regional AI Initiative, Oct 13](https://www.canada.ca/en/economic-development-southern-ontario/news/2026/10/government-of-canada-expands-support-to-adopt-and-commercialize-artificial-intelligence.html)
- [PM release, Digital Transformation Canada, Sep 3](https://www.pm.gc.ca/en/news/news-releases/2026/09/03/prime-minister-carney-launches-digital-transformation-canada-deliver)
- [ISED release, VITAL $100M, Jun 23](https://www.canada.ca/en/innovation-science-economic-development/news/2026/06/government-of-canada-invests-100-million-in-vital-health-data-platform.html)
- [ISED release, supercomputing program opens, Apr 15](https://www.canada.ca/en/innovation-science-economic-development/news/2026/04/canada-launches-national-initiative-to-build-large-scale-ai-supercomputing-capacity.html)
- [ISED, AI Sovereign Compute Infrastructure Program page](https://ised-isde.canada.ca/site/ised/node/279)
- [Mitacs, $162M placements, Sep 25](https://www.mitacs.ca/news/government-of-canada-invests-in-10000-ai-related-work-placements-for-young-canadians/) (partner's own release)
- [ISED release, National AI Literacy Initiative, Sep 9](https://www.canada.ca/en/innovation-science-economic-development/news/2026/09/government-of-canada-launches-national-ai-literacy-initiative.html)
- [Parliament LEGISinfo, Bill C-34](https://www.parl.ca/legisinfo/en/bill/45-1/c-34)
- [Parliament LEGISinfo, Bill C-36](https://www.parl.ca/legisinfo/en/bill/45-1/c-36)

Secondary (opened):
- [DLA Piper, Bill C-36](https://www.dlapiper.com/insights/publications/2026/06/canada-tables-bill-c36-the-protecting-privacy-and-consumer-data-act)
- [BetaKit, National AI Literacy Initiative](https://betakit.com/canada-unveils-national-ai-literacy-initiative/)
- [HCA Mag, National AI Literacy Initiative](https://www.hcamag.com/ca/specialization/transformation/canada-launches-national-ai-literacy-initiative/589341)
- [Amii, literacy initiative](https://www.amii.ca/updates-insights/amii-leads-national-ai-literacy-initiative)
- [The Hub, Budget 2026 date](https://thehub.ca/2026/10/21/champagne-sets-nov-5-budget-date-as-watchdog-warns-deficits-are-deepening/)
- [BetaKit, data centre call, Jan 21](https://betakit.com/feds-call-for-proposals-to-build-large-scale-data-centres-in-canada/)
- [BetaKit, Cohere, Dec 2024](https://betakit.com/cohere-secures-federal-backing-to-build-multibillion-dollar-canadian-ai-data-centre/)
- [CTV London, Oct 13](https://www.ctvnews.ca/london/article/federal-government-expands-ai-program-with-500m-boost/) (excerpt only)

Search results only (not opened):
- [Dentons on the National Council](https://www.dentons.com/en/insights/articles/2026/october/7/federal-government-launches-national-council-on-artificial-intelligence)
- [Gowling on C-34/C-36](https://gowlingwlg.com/en/insights-resources/articles/2026/ottawa-tables-long-awaited-federal-privacy-reform-legislation)
- [Fasken, national AI strategy, Aug](https://www.fasken.com/en/knowledge/2026/08/canada-s-national-ai-strategy) (403 on fetch)
- [Intelligent CIO, Bell Saskatchewan hub](https://www.intelligentcio.com/north-america/2026/09/15/bell-ai-fabric-plans-1-2-gw-saskatchewan-ai-infrastructure-hub/)
- [Fierce Network, Bell 900 MW](https://www.fierce-network.com/cloud/bell-canada-lengthens-its-sovereign-ai-lead-900-mw-expansion) (403 on fetch)
- [BetaKit, Compute Access Fund $66M](https://betakit.com/feds-announce-66-million-for-44-businesses-through-ai-compute-access-fund/)
- [ISED, 44 companies release, May 2026](https://www.canada.ca/en/innovation-science-economic-development/news/2026/05/government-of-canada-supports-44-canadian-companies-using-ai-to-transform-industries-and-create-jobs.html)
- [The Logic, Mitacs $162M](https://thelogic.co/briefing/ottawa-awards-mitacs-162m-to-create-ai-focused-work-placements/)
- [ISED, Canada-Germany Sovereign Technology Alliance, Feb 2026](https://www.canada.ca/en/innovation-science-economic-development/news/2026/02/canada-and-germany-sign-ai-joint-declaration-and-launch-sovereign-technology-alliance.html)
- [Finance Canada, Budget 2026 consultations](https://www.canada.ca/en/department-finance/news/2026/07/government-of-canada-launches-consultations-ahead-of-budget-2026.html)
