# Almedia signal matrix

Work in progress, to validate with Almedia sales and leadership. Built from `context/icp/icp.md`, `context/icp/personas.md` and `context/docs/research/`. Method: `knowledge-base/playbooks/signal-matrix-framework.md`, `workflow-anatomy.md`. Source key: [CU] customers.md, [CP] competitors.md, [RN] rival-network-clients.md, [LP] leadership-posts.md, [CO] company.md, [SI] signals.md, [VO] voice.md, [MK] market.md. INFERRED = not supported by research.

**Axis (rows): what the studio uses today.** Same casual, puzzle, merge and word game studios, split by existing solution, because that changes the pitch: displacement vs greenfield vs monetization. Asia (Korea, Japan, China) is a geo filter inside rows 1 to 3, not a row (user decision 2026-11-26). Columns: the three personas in `personas.md`.

Exclude current Almedia customers from all rows (see `context/docs/case-studies.md`).

## Matrix 1: Segments x personas

| Segment | Target definition (filterable) | Real examples | Lead / upsell | Priority | Champion: UA Manager / Lead | Economic buyer: CEO / Co-Founder / COO | Influencer: Marketing Director |
|---|---|---|---|---|---|---|---|
| **1. Rival rewarded users** | Casual, puzzle, merge or word game studio named in a rival rewarded network's case study (Mistplay, adjoe, Gamelight, Persona.ly) in the last 24 months; live title in US, DE, GB, CA or FR (West) or KR, JP, CN (Asia) | West: Futureplay, Higgs Studio, Vividjoan, Trailmix, Century Games, East Side Games, Huuuge Games, Green Panda Games, MagicLab, Riddle Road, LevelApp. Asia: Playlinks, 37Games, 4399 [RN]. Genre of each to verify in store data; Netmarble excluded (its Mistplay case is RPG, outside ICP genres) [RN] | Freecash / Link | **High.** They already buy rewarded; Almedia's proof is vs other rewarded channels [CU] | "You run rewarded with {{rival}} today. How does it look at D90? Candivore moved its reward window from 50 to 90 days on Freecash and D90 ROAS rose 70%." Proof: Candivore; backup: Superbox D30 retention vs other rewarded channels [CU] | "Studios running several rewarded networks keep the ones that beat benchmarks." Proof: TREEPLLA CEO quote [CU] | "Adding markets? TREEPLLA launched DE, GB, CA, FR on Freecash." [CU] |
| **2. Scaling studios, rewarded status unknown** | Same genres, showing a scaling trigger (signal 3: hiring UA roles, or signal 4: new Tier-1 market launch) and **not** named in any rival rewarded case study [RN] or as an Almedia customer. Rewarded status is not assumed: reps confirm it in the first message ("do you run rewarded today?"). Studios that say yes move to segment 1 | Requires Clay research: output of signals 3 and 4, minus the segment 1 list and Almedia customers. Model customer: Superbox, which "selected Almedia as their first partner for a CPI-based rewarded user acquisition campaign" [CU] | Freecash / Link | **High.** Almedia's COO names paid networks as the main budget rival: "we fight for ad budgets against Google, Meta and Applovin" [LP]. Best-documented win is a first-time rewarded buyer (Superbox) [CU]. Found through timing signals, not by absence. Pool may be smaller than it looks: Almedia's survey says 77% of US/UK developers have run reward-based UA [MK] | "Your first rewarded partner. Superbox started with one CPI-based test and saw 1.5 to 2x D30 ROAS vs its non-rewarded channels." [CU] | "Growing into new markets? Add a channel that pays back at D30 and beyond, next to Google, Meta and AppLovin." Proof: Superbox 4x daily spend [CU] | "TREEPLLA launched DE, GB, CA, FR on Freecash; Potato Play went from 5 to 15 markets." [CU] |
| **3. Multi-title publishers (Link first)** | Publisher with 5+ live casual titles (threshold INFERRED; customers have 6 to 24) | Unico Studio (16 puzzle games) [RN]; Microfun, Learnings (merge portfolios, title count not verified) [RN]. Others: requires AppMagic/Clay research on title count | Link / Freecash | **High.** Link proof with holdout test; Almedia pays the publisher [CU] | "Link goes in with an SDK in an afternoon; you pick the placements." [VO] | "Gryphon Games saw 18.6% higher total revenue per user with Link." [CU] | "Ovivo put Link across 24 titles." [CU] |
| **4. Non-gaming apps** | Fintech, retail, education, iGaming, health apps with ad restrictions | Requires Clay research. No verified examples | Freecash for Brands | **Low.** No non-gaming proof; Almedia predicts fintech first [LP] | INFERRED; no proof to cite | INFERRED | INFERRED |

## Matrix 2: Signals (priority segments 1, 2 and 3, West and Asia variants)

Segment 2 has no signal of its own: it is the output of signals 3 and 4 after removing segment 1 and Almedia customers (updated 2026-11-26).

Four tests scored 1 (weak) to 3 (strong): **BR** clear buying reason, **V** enough volume, **D** data you can get, **S** natural story. Total /12. Credits per Clay action: unknown, check in Clay before running. Volumes are INFERRED estimates.

| # | Type | Signal (mother intent) | Segment | Data source | Tool / Clay action | Key filters | BR | V | D | S | Total | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Niche | **Named in a rival rewarded network case study** (Competitor customers) | 1 West + Asia | business.mistplay.com/resources, adjoe.io/success-stories, gamelight.io/case-studies, persona.ly/blog, appsflyer.com/customers [RN] | crawl4ai or Clay HTTP scrape of case-study index pages; then Clay "Find People" for UA titles | Published in last 24 months; casual genres; exclude Almedia customers | 3 | 2 | 3 | 3 | **11** | VERIFIED (sources exist [RN]; volume ~25 named so far, INFERRED total in the low hundreds) |
| 2 | Universal | **Speaks at or sponsors a UA event** (Companies attending/sponsoring an event) | 1, 3 West + Asia | Speaker and sponsor pages: Pocket Gamer Connects, Gamesforum, G-STAR, ChinaJoy, Almedia Summit [CO], [LP], [RN] | crawl4ai/Apify scrape of agenda pages; Clay "Find People" | Event in next 60 days or last 30; studio speakers on UA, growth or monetization panels | 2 | 2 | 3 | 3 | **10** | VERIFIED (PARTIAL: Almedia Summit page now 404 [LP]) |
| 3 | Universal | **Hiring UA or growth roles** (Hiring specific roles) | 1, 2, 3 | Job posts | Clay "Find Jobs at Company" | Titles: User Acquisition Manager, UA Lead, Growth Manager, Head of UA; game studios only | 2 (INFERRED: hiring = more UA spend) | 3 | 3 | 2 | **10** | VERIFIED (COMPOUND: pair with genre filter; then route: on segment 1 list → segment 1, else → segment 2) |
| 4 | Niche | **Title launching in a new Tier-1 market** (New product launches) | 1, 2 | App store availability and chart data (store-intelligence tools such as AppMagic, Appfigures, named in research [RN], [CO]) | Store-intelligence API via Clay HTTP (INFERRED: API access and cost not checked) | New country in US, DE, GB, CA, FR in last 30 days | 3 (TREEPLLA, Potato Play [CU]) | 2 | 2 | 3 | **10** | VERIFIED (PARTIAL: tool access unconfirmed). Main feed for segment 2; route as signal 3 |
| 5 | Niche | **Publisher ships a new title** (New product launches, Link) | 3 | Developer pages on App Store / Google Play; store-intelligence tools | Clay HTTP or store-intelligence API, monthly snapshot of title count | Publisher with 5+ live titles adds 1 or more | 2 (INFERRED: new title = new Link placement) | 2 | 2 | 2 | **8** | VERIFIED (PARTIAL) |
| 6 | Universal | **New UA leader in last 90 days** (New leadership) | 1, 2 | People data | Clay "Find People", start date < 90 days | Titles: Head of UA, VP Growth, CMO at game studios | 2 (INFERRED) | 2 | 3 | 2 | **9** | VERIFIED (COMPOUND) |
| 7 | Universal | **Lookalike of Almedia customers** (Lookalike of customers) | 1, 2, 3 | Seed list: Superbox, Candivore, TREEPLLA, Potato Play, Ovivo, Gryphon Games [CU] | Clay lookalike / "Find Companies" | Same genres and size band | 1 (static, no timing) | 3 | 3 | 2 | **9** | VERIFIED (use as ICP filter, not a trigger) |
| 8 | Niche | Game live on a rival consumer rewards app's offer wall | 1 | Mistplay / KashKick apps | Would need app scraping | n/a | 3 | 2 | 1 | 2 | 8 | **KILLED:** not programmatically accessible from public web; manual research only |
| 9 | Universal | Recent funding round | 1, 2 | Crunchbase | Clay "Find Organization" | n/a | 1 | 1 | 2 | 1 | 5 | **KILLED:** no research shows funding drives rewarded UA buying; Almedia's own buyers skew to "smaller studios" [LP] |
| 10 | Niche | Non-gaming app in ad-restricted category | 4 | n/a | n/a | n/a | 1 | ? | ? | 1 | n/a | **PARKED:** no proof; revisit once a non-gaming case study exists |

**Compounding:** signals 2, 3, 6, 7 are universal (one Clay build each, keyword swaps per segment and per West/Asia). Signals 1, 4, 5 are niche builds. Asia variants change only inputs: event list (G-STAR, ChinaJoy), case-study filter (KR/JP/CN markets), job titles in local language (INFERRED).

## Build first (top 4)

| Rank | Signal | Why |
|---|---|---|
| 1 | **#1 Named in a rival network case study** | Highest score (11). They already buy rewarded and spend at scale; proof exists that studios run several networks at once (SpringComes, TREEPLLA, Unico Studio) [RN]; the story writes itself ("saw your {{game}} results with {{rival}}"). Same build covers West and Asia. |
| 2 | **#4 New Tier-1 market launch** | Clearest timing trigger with Almedia proof attached (TREEPLLA DE/GB/CA/FR, Potato Play 5 to 15 markets) [CU]. Now also the main feed for segment 2 (first rewarded partner, Superbox proof). Confirm store-intelligence API access first. |
| 3 | **#2 UA event speakers and sponsors** | Cheap scrape, natural opener, and Almedia is already at these events (G-STAR, ChinaJoy, Gamesforum Vietnam) so reps can meet in person [CO], [RN]. |
| 4 | **#3 Hiring UA roles, compounded with genre** | Highest volume universal signal; on its own the buying reason is INFERRED, so only run it stacked on a genre filter. Feeds segment 1 (if on the rival list) or segment 2 (if not). |

## Matrix 3: Workflow tracker

| W # | Status | Workflow name | Mother intent | Campaigns | Launch | Persona | Industry | Channel | Clay URL | Copy URL | Total leads |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | Planned | Rival rewarded users (West) | Competitor customers | | | | Casual games | | | | |
| 2 | Planned | Rival rewarded users (Asia) | Competitor customers | | | | Casual games | | | | |
| 3 | Planned | New Tier-1 market launch (segments 1 and 2) | New product launches | | | | Casual games | | | | |
| 4 | Planned | UA event speakers and sponsors | Companies attending an event | | | | Casual games | | | | |
| 5 | Planned | Hiring UA roles, stacked (segments 1 and 2) | Hiring specific roles | | | | Casual games | | | | |
| 8 | Planned | First rewarded partner (segment 2, fed by W3 and W5) | New product launches / Hiring specific roles | | | | Casual games | | | | |
| 6 | Planned | New UA leader | New leadership | | | | Casual games | | | | |
| 7 | Planned | Link: publisher ships new title | New product launches | | | | Game publishers | | | | |

## Open questions

- Is head to head still the lead angle for segment 1, given Mistplay makes the same claim? [RN]
- Store-intelligence API access and cost (AppMagic, Appfigures, Sensor Tower)
- Title-count threshold for Link (5+ is INFERRED)
- Which of the segment 1 examples are already Almedia customers (CRM check)
- Segment 2 size: how many scaling studios truly run no rewarded today (Almedia survey suggests a minority: 77% have run it [MK])
- Is "first rewarded partner" a fit for studios that tried rewarded before and stopped? (no research)
