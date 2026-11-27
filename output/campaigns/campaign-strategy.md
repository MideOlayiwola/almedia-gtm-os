# Campaign Strategy for Almedia

**Status:** Draft for review, 2026-11-27. Built by `/campaign-strategy` from the Context OS only (no new external research). Next step: `/build-workflow-spec` on the recommended idea.

**Source key:** [CO] company.md, [CU] customers.md, [CP] competitors.md, [RN] rival-network-clients.md, [LP] leadership-posts.md, [SI] signals.md, [MK] market.md, [VO] voice.md (all in `context/docs/research/`); [CS] `context/docs/case-studies.md`; [SM] `context/icp/signal-matrix.md`; [GTM] `context/docs/gtm-system.md`; [FA] `context/messaging/facts.md`; [CR] `knowledge-base/playbooks/clay/actions-data-credits.md`. INFERRED = our reading, not a sourced fact.

**Target audience (given):** Casual, puzzle, merge and word mobile game studios that already buy UA, live in US, DE, GB, CA, FR or KR, JP, CN; champion UA Manager or Lead, economic buyer CEO, Co-Founder or COO, influencer Marketing Director [SM], `context/icp/icp.md`.
**Core value proposition:** Rewarded users who keep paying back long after day 7 (Freecash), and a CPA for every existing player who links to Freecash (Link) [CO], `context/messaging/messaging.md`.
**Key differentiators:** Long-window proof (Candivore reward window 50 to 90 days, D90 ROAS +70%) and Link's CPA-per-linked-player model, neither claimed the same way by any competitor in research. Head-to-head proof vs other rewarded channels is support only, because Mistplay makes the same claim [CU], [RN], `context/positioning/positioning.md`.

---

## Read this first: how the numbers in this file were made

CLAUDE.md rule 2 says never invent numbers. Three columns below need numbers that the research does not contain, so here is exactly what they are.

| Column | What it is | Basis |
|---|---|---|
| **Volume / month** | INFERRED planning range of accounts (or people, where marked) per month. **Not a fact.** Each range must be replaced by the count from a one-week test pull before its workflow spec is approved. | Only idea 1 has a research basis (about 25 named rival clients so far [RN]). All others are flagged estimates. |
| **Spend** | Clay data credits per month = volume x credits per row. | [CR] benchmarks: Accounts table about 4 to 6 credits per row, People table about 6 to 8 credits per row. One account worked with up to 3 people = **about 22 to 30 credits**. One person-led row (account plus 1 person) = **about 10 to 14 credits**. AI columns (Claygent), Find Jobs and third-party tools are extra and **unknown**. Dollars per credit: **unknown** ("several pennies each" [CR]). |
| **Return ("ROAS")** | Rated High / Medium / Low on how close the list is to a buy and how strong the proof fit is. | Return in dollars is **unknown**: no Almedia pricing, deal size, minimum spend or win rate exists in research [CO], [CP]. Flagged for sales input. |

**Scores used for ranking (as requested: signal strength, then ease of data):** Signal strength 1 to 3 (how strongly the filter means "needs this now"), Data ease 1 to 3 (can it be pulled programmatically today with the GTM stack: Clay, n8n, crawl4ai [GTM]). Ranked by the sum, ties broken by signal strength, then by volume. Signal and data scores for ideas already in the signal matrix reuse its BR and D scores [SM].

---

## Customer Discovery Analysis

**Case studies reviewed** (all Almedia-published, company size not found for any [CS]):

| Company | Product | Game / genre | Key metric | Problem solved | Authorized for copy? [FA] |
|---|---|---|---|---|---|
| Superbox | Freecash | Jewels Jungle (match-3, INFERRED) | D30 retention 3x vs other rewarded (2% to 6%); D30 ROAS 1.5 to 2x vs non-rewarded | First rewarded partner, one CPI-based test | Yes (pending) |
| Candivore | Freecash | Match Masters (match-3, INFERRED) | Reward window 50 to 90 days, D90 ROAS +70%, D30 ROAS +65% (2x goal) | "Better Value, Larger Scale" | Yes (pending) |
| TREEPLLA | Freecash | Office Cat | D30 ROAS 2x competitor benchmarks; daily spend +550%; launched DE, GB, CA, FR | Reactivation and new markets | Yes (pending) |
| Potato Play | Freecash | Not found | 5 to 15 markets; D30 ARPU +26% | Partners that hold metrics at high spend | Yes (pending) |
| Super Free Games | Freecash | Word Collect (word) | D60 ROAS 72% to 100%; daily spend ~20x | Not found | No |
| Mad Brain | Freecash | Word Farm Adventure (word) | D7 ROAS +30% vs rewarded sources | Not found | No |
| Innplay Labs | Freecash | Not found | D30 retention +70% vs industry average | Not found | No |
| Gryphon Games | Link | 6 titles on Link | +18.6% total revenue per user (holdout) | Monetize existing players | Yes (pending) |
| Ovivo | Link | 24 titles | est. 16.8% LTV uplift; 66,000 links | Monetize a catalogue | Yes (pending, always "estimated") |
| SpringComes | Link | Merge Sweets, Hello Town (merge) | ARPU +15.9% | Not found | No |
| Original Games | Link | Merge Inn (merge) | IAP revenue per user +25.6% | Not found | No |

**Patterns identified:**
- Industry: 100% mobile games; no non-gaming story exists [CU].
- Genres: match-3, word and merge dominate (INFERRED from titles) [CU].
- Roles that bought or were quoted: UA Manager, Senior Manager, CEO, Co-Founder, COO, Marketing Director [CU].
- Problems: retention from other rewarded channels, holding ROAS while scaling spend, entering new Tier-1 markets, relaunching a title, monetizing an existing catalogue [SI].
- Two products, two buyers: Freecash (UA team buys) and Link (publisher leadership is paid) [CO].

**Targeting recommendation (challenging the given ICP):**
1. **Studios already on rival rewarded networks are the closest list to a buy**, and some run several networks at once (SpringComes, TREEPLLA, Unico Studio) [RN]. Treat "already buys rewarded" as an advantage, not a reason to skip.
2. **Link opens a second buyer the UA ICP misses:** publishing and monetization leadership at multi-title studios, including studios with no UA budget. That is why three ideas below lead with Link.
3. **Non-gaming stays a test, not a segment.** Almedia predicts fintech moves first [LP] but has no proof; keep it Tier 3 until a case study exists [SM].
4. **Agencies and consultants that run UA for studios** are outside the ICP but sit next to it. Untested; partner or referral terms are unknown.

**Best customers for the Lookalike campaign:** Superbox, Candivore, TREEPLLA, Potato Play (authorized names, pending). Use Super Free Games, Mad Brain and Original Games as extra **seed** companies for list building only, never named in copy [FA].

---

## Section 1: Ranked campaign list

19 ideas, ranked by signal strength plus data ease (user request). Targeting level shown per idea. Required types: Creative Ideas = #15, New Hire = #9, Lookalike = #16, Creative (non-ICP) = #17 and #18, Unrewarded = #11, Golden ICP = #5, No-AI = see Section 3.

| Rank | Campaign | Level | Mother Intent | Segment / persona | Signal and data source | Sig | Data | Volume / month (INFERRED) | Spend (credits/mo) vs return | Difficulty | Tier |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | **Rival rewarded users: the D90 question (West)** | Niche | Competitor customers | S1 / UA Manager or Lead | Named in a Mistplay, adjoe, Gamelight, Persona.ly or AppsFlyer customer case study, last 24 months [RN]. crawl4ai on case-study index pages, then Clay Find People | 3 | 3 | Month 1 backlog 25 to 100 accounts (about 25 named so far [RN]); then 5 to 15 new | 550 to 3,000 vs **High** (already pays for rewarded) | Easy | **Tier 1:** strongest signal, public pages, fast build |
| 2 | Rival rewarded users (Asia) | Niche | Competitor customers | S1 Asia (KR, JP, CN) / UA Manager, CEO | Same as #1, filtered to Asian studios and markets (37Games, Playlinks, 4399 named [RN]) | 3 | 3 | 20 to 50 one-off, then trickle | 440 to 1,500 vs **High** | Medium (local language) | Tier 2: Asia sender and copy undefined [GTM] |
| 3 | **Freecash alumni: champion migration** | Niche | Champion/user migration | S1 or S2 / UA Manager, Head of UA at their new studio | Person's past company = an Almedia case-study customer, UA or growth title, now at another game studio. Clay Find People (past company filter); HubSpot export later | 3 | 3 | Under 30 people one-off (INFERRED), then a few per month | 100 to 420 (person-led) vs **High** | Easy | **Tier 1:** warmest cold list, tiny cost |
| 4 | New Tier-1 market launch | Focused | New product launches | S1 or S2 / UA Manager, Marketing Director | Casual title newly live or charting in US, DE, GB, CA or FR in last 30 days. Store-intelligence API (AppMagic, Appfigures or Sensor Tower) via Clay HTTP [SM] | 3 | 2 | 30 to 100 | 660 to 3,000 + API cost (unknown) vs **High** | Medium | Tier 2: becomes Tier 1 once API access is confirmed |
| 5 | **Golden ICP: rival user that is also scaling** | Niche | Competitor customers + Hiring specific roles / New product launches | S1 / UA Manager plus CEO | On the #1 list AND (hiring UA roles OR new Tier-1 market) in the last 30 days. Reuses rows from #1, #4, #7 | 3 | 2 | Under 10 | About 0 extra (reuses enriched rows) vs **Very high** | Medium (needs 3 feeds live) | Tier 2: highest relevance, lowest volume |
| 6 | **Link: one SDK, every title** | Focused | Niche-specific play (multi-title catalogue) | S3 / CEO, COO, Co-Founder, monetization lead | Publisher with 5+ live casual titles (threshold INFERRED [SM]). Google Play and App Store developer pages via Clay HTTP or crawl4ai | 2 | 3 | Pool est. 300 to 1,000; work 100 to 200 | 2,200 to 6,000 vs **Medium** (Almedia pays them; revenue comes from linked users) | Easy | **Tier 1:** Link model is the least copied claim [CP], public data |
| 7 | Hiring UA roles (stacked on genre) | Focused | Hiring specific roles | S1 or S2 / UA Lead, Head of UA | Open job: User Acquisition Manager, UA Lead, Growth Manager, Head of UA at a casual game studio. Clay Find Jobs [SM] | 2 | 3 | 50 to 150 | 1,100 to 4,500 + Find Jobs credits (unknown) vs **Medium** | Easy | **Tier 1:** abundant data, high volume, reuses as feed for #5 and #11 |
| 8 | UA event speakers and sponsors | Focused | Companies attending / sponsoring an event | S1 or S3 / speaker plus UA lead | Studio speaker or sponsor on agenda pages: Pocket Gamer Connects, Gamesforum, G-STAR, ChinaJoy [CO], [LP], [RN]. crawl4ai on agenda pages | 2 | 3 | 20 to 80 per event (seasonal) | 440 to 2,400 vs **Medium** | Easy | **Tier 1:** cheap scrape, natural opener, can meet in person |
| 9 | **New UA leader, first 90 days** (New Hire) | Focused | New leadership (past 90/180 days) | S1 or S2 / new Head of UA, VP Growth, CMO | Started role under 90 days ago at a casual game studio. Clay Find People with start date | 2 | 3 | 20 to 60 people | 200 to 840 (person-led) vs **Medium** | Easy | **Tier 1:** reliable start dates, new leaders re-plan the channel mix |
| 10 | Relaunch or reactivation | Niche | New product launches | S1 or S2 / UA Manager, CEO | Title relaunch, major re-release or "reactivation" news; TREEPLLA called its result "a relaunch powered by insight" [CU]. Trade press and store update notes, Claygent | 3 | 1 | 5 to 20 | 110 to 600 + Claygent credits vs **High** | Hard (unstructured data) | Tier 3: strong signal, unreliable detection |
| 11 | **Unrewarded: first rewarded partner** | Focused | Niche-specific play (new intent: active paid-UA advertiser, flagged) | S2 / UA Manager, Head of UA | Studio runs active ads in the public Meta Ad Library AND is not on the #1 rival list AND not an Almedia customer. Apify Meta Ad Library scraper, matched in Clay | 2 | 2 | 100 to 300 | 2,200 to 9,000 + scraper cost (unknown) vs **Medium** | Medium (ad library to studio matching is fuzzy) | Tier 2: can't prove they run no rewarded; 77% of US/UK devs have run it [MK] |
| 12 | LinkedIn engagers on rewarded UA content | Focused | LinkedIn content engagement | S1 or S2 / UA Manager, Head of UA | People at game studios who comment on or like rewarded UA posts by Almedia leaders, Mistplay, adjoe or Matej Lancaric's Summit post [LP]. LinkedIn engager scraper (tool not chosen) | 2 | 2 | 50 to 200 people | 500 to 2,800 (person-led) vs **Medium** | Medium | Tier 2: no scraper picked yet; engagement on Almedia posts is warm |
| 13 | Link: publisher ships a new title | Niche | New product launches | S3 / CEO, COO, monetization lead | Publisher with 5+ live titles adds a title. Monthly snapshot of developer pages [SM] | 2 | 2 | 30 to 80 | 660 to 2,400 vs **Medium** | Medium | Tier 2: needs #6 pool first, then a diff |
| 14 | Top-grossing climbers | Focused | Companies in hypergrowth (variant: revenue rank, flagged) | S1 or S2 / CEO, UA Lead | Casual title climbs US top-grossing chart over 30 days. Store-intelligence API | 2 | 2 | 20 to 60 | 440 to 1,800 + API cost vs **Medium** | Medium | Tier 2: same API blocker as #4 |
| 15 | **"3 reward ideas for {{game}}"** (Creative Ideas) | Broad | Niche-specific play | S1 to S3 base list / UA Manager | No trigger. AI reads the store listing to draft 3 milestone reward ideas | 1 | 3 | 200 to 500 | 4,400 to 15,000 + AI column credits vs **Low to Medium** | Medium (AI quality check) | Tier 2: no timing; best used as the fallback message for #4, #7, #9 |
| 16 | Lookalike of Almedia customers | Broad | Lookalike of customers | S1 or S2 / UA Manager | Same genre and size band as Superbox, Candivore, TREEPLLA, Potato Play (seeds plus Super Free Games, Mad Brain). Clay Find Companies lookalike [SM] | 1 | 3 | Pool est. 500 to 2,000; send 200 to 400 | 4,400 to 12,000 vs **Low to Medium** | Easy | Tier 2: high volume, no timing signal |
| 17 | Non-gaming: ad-restricted apps (Creative non-ICP) | Focused | Niche-specific play (S4, parked) | S4 / Head of Growth at fintech apps | Fintech app in a category with ad restrictions; Almedia predicts fintech adopts fastest [LP]. Clay Find Companies by category | 1 | 2 | 100 to 300 one-off | 2,200 to 9,000 vs **Unknown** (no proof) | Hard (no proof to cite) | Tier 3: parked until a non-gaming case study exists [SM] |
| 18 | **UA agencies and consultants** (Creative non-ICP) | Focused | Niche-specific play (new intent: partner channel, flagged) | Outside ICP / agency founder, head of UA services | Agency or consultancy whose site lists mobile game clients and UA services. Google search plus Claygent on service and client pages | 1 | 2 | 50 to 150 one-off | 1,100 to 4,500 + Claygent vs **Unknown** (partner terms unknown) | Medium | Tier 2: untouched audience; needs a referral or partner offer from Almedia first |
| 19 | US web-shop adopters | Niche | Website content mentions | S1 or S2 / CEO, UA Lead | Game links to a web shop (allowed in US apps since the April 2025 ruling [MK]). Claygent check on game site | 1 | 2 | 20 to 80 | 440 to 2,400 + Claygent vs **Unknown** | Medium | Tier 3: link from web shops to higher bids is INFERRED, no source [MK] |

Tier 1 ideas: #1, #3, #6, #7, #8, #9.

---

## Section 2: Campaign cards (handoff detail)

Every proof point below is in `facts.md` and still **pending approval** [FA]. `{{placeholders}}` are filled per row by Clay. No copy here: `/campaign-copy` writes it after `/build-workflow-spec`.

### 1. Rival rewarded users: the D90 question (West) | Tier 1
- **Segment / persona:** S1, champion UA Manager or Lead; economic buyer CEO one week later [GTM step 6].
- **Signal and source:** Studio named in a rival network case study in the last 24 months. Pages: business.mistplay.com/resources, adjoe.io/success-stories, gamelight.io/case-studies, persona.ly/blog, appsflyer.com/customers [RN]. Weekly crawl via n8n [GTM]. Exclude Almedia customers (TREEPLLA, SpringComes are on both lists [RN]).
- **AI strategy:** Extract from the rival case study: game, rival network, metric window they reported (D7, D30). Route on the window: if the rival story stops at D7 or D30, the email asks about D90.
- **Value proposition:** Make more money. Users that still pay back at D60 to D90, not only D7.
- **Angle:** "You run rewarded with {{rival}} today; how does {{game}} look at D90?" Proof: Candivore moved its reward window from 50 to 90 days and D90 ROAS rose 70% [CU]. Backup (email 2): Superbox 3x D30 retention vs its other rewarded channels [CU].
- **CTA:** Question about their D90 numbers, then an offer to compare one cohort.
- **Differs from others:** The only list where the prospect already pays for rewarded, so the pitch is "add or compare", never "try rewarded".
- **Guardrails:** Do not open with "we beat other networks" (Mistplay claims the same [RN]); never name the rival's results as weak.

### 2. Rival rewarded users (Asia) | Tier 2
- Same build as #1, filtered to KR, JP, CN studios (37Games, Playlinks, 4399 [RN]). Almedia has growth roles in Seoul, Tokyo and Beijing and spoke at G-STAR [CO], [RN].
- **Angle:** Same D90 question in Korean, Japanese or Chinese. TREEPLLA's CEO quote on aggressive growth goals [CU] as second proof.
- **Blocker:** Asia sender and local copy undefined [GTM].

### 3. Freecash alumni: champion migration | Tier 1
- **Segment / persona:** Anyone with a UA, growth or marketing title whose previous company is an Almedia case-study customer (Superbox, Candivore, TREEPLLA, Potato Play, Super Free Games, Mad Brain, Innplay Labs [CU]) and who now works at another game studio.
- **Signal and source:** Clay Find People, past-company filter. Later: HubSpot export of real past contacts (HubSpot not yet authorized [GTM]).
- **AI strategy:** Pull previous company, title there, start date at the new studio, the new studio's top game and genre.
- **Value proposition:** Save time. A channel they may already know, at their new studio.
- **Angle:** "{{past_company}} is one of our case studies; now that you're at {{new_company}}, is rewarded part of the plan for {{game}}?" Name the past company only if it is authorized in `facts.md` (Superbox, Candivore, TREEPLLA, Potato Play); otherwise do not name it.
- **Guardrail:** Do not claim the person worked with Almedia unless HubSpot confirms it.

### 4. New Tier-1 market launch | Tier 2 (Tier 1 once API is confirmed)
- **Signal and source:** Casual title newly live or newly charting in US, DE, GB, CA or FR, last 30 days. Store-intelligence API via Clay HTTP [SM]. API access and cost not checked.
- **AI strategy:** Name the new market and the game; check whether it is the first Tier-1 market for the studio.
- **Value proposition:** Make more money. Users that pay back in the markets they just opened.
- **Angle:** "Saw {{game}} went live in {{market}}. TREEPLLA launched DE, GB, CA and FR on Freecash." Second proof: Potato Play went from 5 to 15 markets with 26% higher D30 ARPU [CU]. Routes to S1 or S2 copy depending on the rival list [GTM step 5].

### 5. Golden ICP: rival user that is also scaling | Tier 2
- **What a rep would send after 10 minutes of research:** they already buy rewarded ({{rival}}), they are hiring a {{ua_role}} or just opened {{market}}, and their genre matches our customers.
- **Angle:** Combine both signals in one line, then Candivore D90 proof. CEO and UA Lead in parallel.
- **Build:** No new list. A Clay view filtering rows that carry signal #1 plus signal #3 or #4 within 30 days [GTM step 1 stacking].

### 6. Link: one SDK, every title | Tier 1
- **Segment / persona:** S3 publishers with 5+ live casual titles; CEO, COO or Co-Founder (Link is paid to the publisher [CO]).
- **Signal and source:** Count of live titles on the developer's Google Play and App Store pages (Clay HTTP or crawl4ai). Examples to start: Unico Studio (16 puzzle games [RN]). Exclude Link customers (Ovivo, Gryphon Games, SpringComes, Original Games [CU]).
- **AI strategy:** Count titles, list the top 3 by rating count, note genre mix.
- **Value proposition:** Make more money. A CPA for every player who links to Freecash, on top of in-game revenue.
- **Angle:** "{{title_count}} live games, one SDK. Ovivo put Link across 24 titles." Proof: Gryphon Games +18.6% total revenue per user (holdout test); Ovivo est. 16.8% LTV uplift (always "estimated") [CU]. Install claim: "Install in an afternoon with our SDK" [VO].
- **Upsell:** Freecash UA once Link is live [SM].

### 7. Hiring UA roles (stacked on genre) | Tier 1
- **Signal and source:** Clay Find Jobs for UA Manager, UA Lead, Growth Manager, Head of UA; casual game studios only [SM].
- **AI strategy:** Parse the job description for the channels it names (Meta, Google, AppLovin, rival rewarded networks). Named rewarded network → route to S1 angle. Only paid networks named → route to #11 angle.
- **Value proposition:** Make more money. A channel the new hire can own that pays back past D30.
- **Angle:** "You're hiring a {{role}} to scale {{game}}; one channel worth having on their plan before they start." Proof routes by S1 or S2.
- **Caveat:** Buying reason for hiring is INFERRED [SM]; only send stacked on genre.

### 8. UA event speakers and sponsors | Tier 1
- **Signal and source:** Agenda and sponsor pages of Pocket Gamer Connects, Gamesforum, G-STAR, ChinaJoy [CO], [LP], [RN]; scrape 60 days before and 30 days after each event.
- **AI strategy:** Pull talk title and panel topic; write one line connecting the talk to long-window ROAS or monetization.
- **Value proposition:** Make more money; meet in person.
- **Angle:** Before the event: "Your talk on {{topic}} at {{event}}; worth 15 minutes there?" After: reference one point from the talk. Proof routed by segment.

### 9. New UA leader, first 90 days (New Hire) | Tier 1
- **Signal and source:** Clay Find People, start date under 90 days, titles Head of UA, VP Growth, CMO at casual game studios [SM].
- **AI strategy:** Previous company, start date, top game of the new studio, whether the new studio is on the rival list.
- **Value proposition:** Make more money fast. A quick test that shows results inside the first quarter.
- **Angle:** "New at {{company}}, so the channel mix is yours to set. Superbox started with one CPI-based test and saw 1.5 to 2x higher D30 ROAS than its non-rewarded channels" [CU].

### 10. Relaunch or reactivation | Tier 3
- **Signal and source:** Trade press (e.g. PocketGamer.biz) and store update notes mentioning relaunch, re-release or global launch; Claygent search. Unstructured, so expect misses.
- **Angle:** TREEPLLA relaunched Office Cat on Freecash: D30 retention +133%, daily spend +550% [CU]. Only "D30 ROAS 2x competitor benchmarks, daily spend up 550%" is approved phrasing; the retention figure needs adding to `facts.md` first [FA].

### 11. Unrewarded: first rewarded partner | Tier 2
- **Segment / persona:** S2, studios with no visible rewarded network; UA Manager or Head of UA.
- **Signal and source:** Active ads in the public Meta Ad Library (Apify scraper) for a casual game studio, AND not on the #1 rival list, AND not an Almedia customer. Rewarded status is never assumed: the first email asks [SM].
- **AI strategy:** Count active ads and countries targeted; name the game advertised.
- **Value proposition:** Make more money. A channel next to Google, Meta and AppLovin that pays back at D30 and beyond (Almedia's COO names these as the budget rivals [LP]).
- **Angle:** "Do you run rewarded for {{game}} today, or is it Meta, Google and AppLovin?" Then: Superbox started with one CPI-based test; D30 ROAS 1.5 to 2x vs non-rewarded channels [CU].
- **Routing:** Reply "yes, we run rewarded" moves the account to the #1 angle [GTM step 9].
- **Risk:** Pool may be smaller than it looks: 77% of US and UK developers say they have run reward-based UA (Almedia-commissioned survey [MK]).

### 12. LinkedIn engagers on rewarded UA content | Tier 2
- **Signal and source:** Engagers on rewarded UA posts by Jan Sommerfeld, Moritz Holländer, Mistplay, adjoe, and Matej Lancaric's Summit write-up [LP]. Scraper not chosen.
- **AI strategy:** Quote the post they engaged with, check title and studio.
- **Angle:** "You commented on {{post_topic}}; here is what D90 looked like for Candivore." People who engaged with Almedia's own posts are a warm sub-list.

### 13. Link: publisher ships a new title | Tier 2
- **Signal:** Monthly diff of #6 developer pages: a new title appears [SM].
- **Angle:** "New launch for {{new_title}}; Link can go in before players settle. You pick the placements (button, modal, rewarded moment)" [VO].

### 14. Top-grossing climbers | Tier 2
- **Signal:** Casual title rises on US top-grossing over 30 days (store-intelligence API). Rising revenue also meets readiness item 1 (live and earning) [`icp.md`].
- **Angle:** "{{game}} is climbing; users that pay back at D90 help keep that going." Candivore proof.

### 15. "3 reward ideas for {{game}}" (Creative Ideas) | Tier 2
- **Segment:** Whole ICP base list, or as the fallback message on #4, #7, #9 when no rival is found.
- **AI strategy:** Read the store listing (genre, core loop, IAP, level structure) and draft 3 milestone ideas in Almedia's model: rewards for levels and purchases unique to the app, custom reward structures and challenges [CO], [VO]. Example shape: "reach level {{n}}", "first purchase", "day-7 streak", plus one Link placement idea.
- **Value proposition:** Make more money; shows the work up front.
- **Opener:** "I had an idea for {{game}}..." plus 3 bullets. CTA: "Would any of these work for {{game}}?"
- **Guardrails:** No predicted ROAS or install numbers (banned guarantees [FA]); a human checks 20 rows before send.

### 16. Lookalike of Almedia customers | Tier 2
- **Seeds:** Superbox, Candivore, TREEPLLA, Potato Play, plus Super Free Games and Mad Brain as unnamed seeds [CU], [FA].
- **AI strategy:** Pick the nearest authorized customer by genre (match-3 → Superbox or Candivore; casual sim → TREEPLLA) and name it.
- **Angle:** "{{customer}} runs a game a lot like {{game}}; here's what changed for them." Proof per named customer from `facts.md` only.
- **Note:** Lookalike is a filter, not a trigger [SM]. Stack with #7 or #9 to add timing.

### 17. Non-gaming: ad-restricted apps (Creative non-ICP) | Tier 3
- **Why outside ICP:** Almedia sells "Freecash for Brands" and predicts fintech adopts fastest; ad-restricted categories may move budget into rewarded [CO], [SI]. No non-gaming case study exists [CU].
- **Angle:** Question-only, no results claimed: "Are paid channels limiting how you can advertise {{app}}?" Offer a scoped pilot.
- **Banned:** Any claim of non-gaming results [FA]. Keep parked until a case study exists [SM].

### 18. UA agencies and consultants (Creative non-ICP) | Tier 2
- **Why outside ICP:** Agencies buy or advise on UA for many studios, so one yes reaches several game advertisers. Untouched by game-studio outbound (INFERRED).
- **Signal and source:** Agency sites listing mobile game clients and UA services; Google search plus Claygent on service and client pages. Check client overlap with the ICP genres.
- **AI strategy:** Pull 2 or 3 named game clients from their site; check if any is on the #1 rival list.
- **Value proposition:** Make more money for their clients; Link as an extra revenue line for publisher clients.
- **Angle:** "You run UA for {{client_1}} and {{client_2}}; is rewarded in the mix for them?" Proof: Candivore D90.
- **Blocker:** Partner, referral or reseller terms are not in research; ask Almedia before launch.

### 19. US web-shop adopters | Tier 3
- **Signal:** Game links to a web shop, allowed in US apps after the April 2025 Epic v. Apple ruling [MK]. Claygent check.
- **Angle (INFERRED):** Higher margin per payer means a studio can afford to bid more per user (Naavik [MK]); rewarded users that buy are worth more to them now. No source links web shops to rewarded UA, so test small.

---

## Section 3: No-AI campaigns

**A. Link: one SDK, every title (static version of #6)**
- **Why it works without AI:** The list filter (5+ live titles) is the message. The offer is simple and Almedia pays the publisher, so no research line is needed.
- **Core message:** Count of their live games (formula column, not AI) → "Link pays you a CPA for every player who links to Freecash" → Gryphon Games +18.6% total revenue per user → "Worth a look for your catalogue?"

**B. The D90 question (static version of #1)**
- **Why it works without AI:** Everyone on the list already runs rewarded, so one question lands for all of them.
- **Core message:** "How does rewarded look for you at D90, not D7?" → Candivore: reward window 50 to 90 days, D90 ROAS +70% → "Want to compare one cohort?"

---

## Section 4: Front-end offer suggestions

1. **One-cohort test on the Advertiser Platform.** Almedia added self-serve game launch to its Advertiser Platform on 2026-10-27 [CO]. Superbox started with one CPI-based test [CU]. Offer: a small, capped test read at D30 and D60. The prospect sees their own cohort pay back before a bigger commitment. Budget floor and terms unknown; needs sales input.
2. **Link revenue estimate for their catalogue.** Take their live titles and show where Link could sit (button, modal, rewarded moment [VO]) and what Almedia pays per verified link [CO]. Any conversion figure must say "projected" (15 to 20% projected [FA]); CPA level is unknown, so leave it blank until sales gives one.
3. **Long-window ROAS benchmark.** Almedia publishes a "Rewarded Returns" report series and "The rewarded UA Handbook" [VO]. Offer the latest edition plus a 20-minute walkthrough of D30 to D90 cohorts for their genre. Low-commitment for teams not ready to test.

---

## Section 5: Recommendation: build #1 first

**Build "Rival rewarded users: the D90 question (West)" first.**

> **Decision (2026-11-27, Mide Olayiwola):** Keep #1 (Tier 1) as the first build. These studios already use rewarded UA, which saves the cost and time of convincing them about rewarded. #3 Freecash alumni would have been a good option, but its list is too narrow to give enough outbound layers.

1. **Strongest signal with the easiest data.** Every account already pays for rewarded UA, so there is budget and no need to sell the category. The list comes from public case-study pages with crawl4ai at about $0 tool cost; about 25 studios are already named [RN].
2. **Cheapest to prove.** Month 1 is about 550 to 3,000 Clay credits [CR], small enough to run inside a Launch plan's 2,500 to 10,000 credits a month if the backlog stays near 25 to 100 accounts.
3. **The angle is our least copied claim.** Long-window value (Candivore D90 +70%) is not claimed the same way by any competitor in research [RN], [CP], and it answers the exact comparison these studios already make.
4. **It is the signal matrix's top-ranked signal (11/12) and workflow W1** [SM], so the spec builds on approved thinking.
5. **It feeds other ideas.** The same list powers the Golden ICP (#5) and the Asia variant (#2) later.

**Quick add-on (same week, near zero cost):** #3 Freecash alumni. Under 30 people, one Clay search.

**Blockers before anything is sent (not before speccing):**
- All claims in `facts.md` are pending approval, and the sender is unknown [FA], [GTM step 0].
- HubSpot is not authorized, so the "exclude current customers and open deals" check is manual for now [GTM].
- Volumes and returns above are estimates; replace them with the test-pull count and sales' deal-size figure.

**Next step:** run `/build-workflow-spec` on idea #1.
