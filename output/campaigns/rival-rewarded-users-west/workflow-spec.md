# Workflow spec: Rival rewarded users (West)

**Status:** COPY-APPROVED 2026-11-27

Signal matrix W1, segment S1, signal #1 (`context/icp/signal-matrix.md`). Strategy idea #1 (`output/campaigns/campaign-strategy.md`). System steps refer to `context/docs/gtm-system.md`. Approved by Mide Olayiwola: sections 1 to 4 (with Germany added) and the angle matrix, 2026-11-27.

Source key: [CU] customers.md, [CO] company.md, [RN] rival-network-clients.md (in `context/docs/research/`); [CS] `context/docs/case-studies.md`; [FA] `context/messaging/facts.md`; [MS] `context/messaging/messaging.md`; [SM] signal-matrix.md; [GTM] gtm-system.md.

---

## 1. Mother Intent (Trigger) [ENGINE]

**A casual, puzzle, merge or word game studio is named as a client in a case study published in the last 24 months by a rival rewarded network (Mistplay, adjoe, Gamelight, Persona.ly, or AppsFlyer's customer pages).**

- Catalog match: Competitor customers (`knowledge-base/playbooks/workflow-anatomy.md`). Does not count toward mother intent coverage; deliberate first build.
- Why now: the studio already pays for rewarded UA, so there is budget and no category to sell (signal #1 scored 11/12 [SM]; decision 2026-11-27 in campaign-strategy.md).

## 2. Inclusion / Exclusion [ICP]

**Include**

| Filter | Value | Source |
|---|---|---|
| Industry and genre | Mobile game studio; main title's store primary category is Casual, Puzzle or Word (merge games sit in these) | `context/icp/icp.md` section 1 |
| Geography | Title live on the **US or DE** store; studio HQ outside KR, JP, CN (those go to W2) | icp.md section 1; DE is 9.7% of Freecash payouts [CO] |
| Readiness | Title live and offers in-app purchases | icp.md section 5 item 1 |
| Size | No filter (open question in ICP) | icp.md |
| Trigger | Named on a rival case-study page published on or after 2024-11-27 (rolling 24 months) | [RN] |

**Recipients** (up to 2 per account)

| Persona | Titles | Timing |
|---|---|---|
| Champion | User Acquisition Manager, UA Lead, Head of UA, Senior UA Manager | Sequence starts first |
| Economic buyer | CEO, Co-Founder, COO | Starts 1 week after the champion; starts first if no champion is found |

Marketing Director is out of v1 (keeps the matrix at 8 cells); candidate for v2. Source: `context/icp/personas.md`, [GTM] step 6.

**Exclude**

| Who | Why |
|---|---|
| Current Almedia customers (domain match against [CS]) | Already clients. TREEPLLA and SpringComes appear on both Almedia's and rival lists [RN] |
| HubSpot: customer, open deal, unsubscribed | [GTM] step 4. Manual check until HubSpot is authorized |
| HubSpot: closed lost under 90 days ago | [GTM] step 4 |
| Rival networks; reward or survey networks Almedia partners with (BitLabs, Make Opinion, Ayet Studios) | Competitors or partners [CU] |
| Publisher-side rival case studies (Gameloft, TapNation, MyB, PlayToWin) | Monetization stories, not UA buys. Park for Link workflows (S3, W7) |
| Genres outside ICP: RPG (e.g. Netmarble), Casino, Card, Board | Not ICP. Drops Vividjoan (Bingo Wild) and Riddle Road (Pyramid Solitaire) |
| Asia-HQ studios (37Games, Playlinks, 4399) | W2 |
| Not live, or no in-app purchases | "Not ready" list, re-checked in 90 days ([GTM] step 4) |

## 3. Sources [ENGINE]

| What | Source | Tool |
|---|---|---|
| **Trigger** | business.mistplay.com/resources, adjoe.io/success-stories, gamelight.io/case-studies, persona.ly/blog, appsflyer.com/customers | crawl4ai, weekly via n8n, rows into Clay "Signals" table |
| Case-study body (date, game, network, metrics) | Each case-study page | crawl4ai, then Clay formula and regex columns |
| Studio domain | Developer link on the store listing; fallback Clay company lookup by name | Clay HTTP / company enrichment |
| Store category, in-app purchases, availability | Google Play listing with `gl=us` and `gl=de`; App Store `us` and `de` as fallback | Clay HTTP |
| HQ country | Company enrichment | Clay |
| Rival network count per studio | Join on domain within the Signals table | Clay formula (no credits) |
| Exclusions | Customer list from [CS]; HubSpot | Clay lookup; HubSpot manual for now |
| People | Find People by title at domain | Clay |
| Email and LinkedIn | Email waterfall plus verifier; LinkedIn URL | Clay |

## 4. Signals table [ENGINE]

| # | Signal | Role | How it's read | Output |
|---|---|---|---|---|
| S1 | Named on a rival case-study page | trigger | Boolean: row exists in Signals table from a rival index crawl | `true` |
| S2 | Case study published in last 24 months | trigger (gate) | Date parsed from page. Boolean: date on or after today minus 730 days. No date found = Needs review | `true` / `false` / `needs_review` |
| S3 | ICP genre | trigger (gate) | Boolean: store primary category in {Casual, Puzzle, Word} | `true` / `false` |
| S4 | Live and monetizing in US or DE | trigger (gate) | Boolean: (US listing resolves OR DE listing resolves) AND in-app purchases shown. Market recorded, does not route | `us` / `de` / `both` / `false` |
| S5 | West HQ | trigger (gate) | Boolean: HQ country not in {KR, JP, CN} | `true` / `false` |
| S6 | Excluded account | trigger (gate) | Boolean: domain on customer list, or HubSpot status customer / open deal / unsubscribed / closed lost under 90 days | `true` = drop |
| R1 | Longest metric window in the rival case study | **router** | Count: case-insensitive regex `\bD(?:ay)?[\s-]?(\d{1,3})\b` over the case-study body; take the highest number found | Cluster below |
| R2 | Recipient persona | **router** | Regex on title: `(user acquisition\|\bUA\b\|growth)` = champion; `(CEO\|founder\|COO\|chief)` = economic buyer | `champion` / `economic_buyer` |
| C1 | Rival network name | context-clause | Text: source index page of the row | `{{rival_network}}` |
| C2 | Game in the case study | context-clause | Text: title extracted from the page heading | `{{case_game}}` |
| C3 | Runs more than one rival network | context-clause | Count of distinct networks per domain: 1 or 2+. One line of color only, never routes | `single` / `multi` |

**R1 count clusters**

| Highest day number | Cluster | Meaning |
|---|---|---|
| 1 to 7 | `short` | Rival's published story stops at week one |
| 8 to 30 | `d30` | Rival's story stops at D30 |
| 31 or more | `long` | They already report long windows |
| No match | `not_stated` | Story is about installs, spend, LTV or retention with no day window |

Axes: R1 (4 clusters) x R2 (2 personas) = 8 cells.

## 5. Routing matrix with angles [ENGINE]

Proof used (all Almedia-published, all pending approval in [FA]): Candivore reward window 50 to 90 days and D90 ROAS +70%; Candivore D30 ROAS up 65%, to 2x the D30 goal; Candivore spend +25% without losing performance; TREEPLLA D30 ROAS 2x competitor benchmarks, daily spend +550% while holding ROAS, CEO quote on aggressive growth goals; Superbox 3x D30 retention vs other rewarded channels (email 2 backup only, never the opener) [CS].

**Facts gap (blocks copy):** `facts.md` only lists Candivore's D30 claim. The reward window (50 to 90 days), D90 ROAS +70% and spend +25% must be added as pending rows before `/campaign-copy` can use them.

### Champion (UA Manager, UA Lead, Head of UA)

| Cell | Deterministic read | What it tells us (inferred situation) | The angle it earns |
|---|---|---|---|
| 1. short x champion | R1 = `short` AND R2 = `champion` | The studio's public rewarded result with `{{rival_network}}` is measured at week one. The UA team has proven rewarded at an early window; the published benchmark for this game is D7. | Take the same question past D7. They know what rewarded returns in week one for `{{case_game}}`; ask what that spend returns by D90. Proof: Candivore extended its reward window from 50 to 90 days and D90 ROAS rose 70%. |
| 2. d30 x champion | R1 = `d30` AND R2 = `champion` | The rival story stops at D30, the usual benchmark for judging rewarded partners. The team evaluates rewarded on a D30 window. | What happens between D30 and D90. D30 is where most rewarded comparisons stop. Proof covers both windows: Candivore reached 2x its D30 goal, then D90 ROAS rose 70% once the reward window ran to 90 days. |
| 3. long x champion | R1 = `long` AND R2 = `champion` | They already publish long-window results, so they measure D60 or later and compare partners on long cohorts. Asking about D90 would be redundant. | Reward-window length as the lever, not the question. The reward window can be built to match the window they already judge on. Proof: Candivore extended its window from 50 to 90 days to match its D90 goal. Offer: compare one cohort at their own window. |
| 4. not_stated x champion | R1 = `not_stated` AND R2 = `champion` | The rival story is about installs, spend or LTV with no window: they bought rewarded for scale. How they judge payback is not public. | Ask which window they judge rewarded on. No assumed window; question first, then the D90 proof (Candivore). No `{{reported_window}}` in this branch. |

### Economic buyer (CEO, Co-Founder, COO)

| Cell | Deterministic read | What it tells us (inferred situation) | The angle it earns |
|---|---|---|---|
| 5. short x economic_buyer | R1 = `short` AND R2 = `economic_buyer` | The company has a public rewarded win with `{{rival_network}}` measured at week one. Leadership backs rewarded as a channel; the open item is how long that spend keeps paying back. | Payback that lasts past week one supports growth targets: rewarded spend judged at D90 can scale further than spend judged at D7. Proof: TREEPLLA CEO quote on beating aggressive growth goals; daily spend +550% while holding ROAS. |
| 6. d30 x economic_buyer | R1 = `d30` AND R2 = `economic_buyer` | The company runs rewarded against a D30 benchmark and has a public success at that window. | Room to scale past the D30 benchmark. Proof: TREEPLLA D30 ROAS 2x competitor benchmarks while daily spend grew 550%. |
| 7. long x economic_buyer | R1 = `long` AND R2 = `economic_buyer` | Leadership already runs a team that judges long windows. The question at this level is scale at that window. | Scale spend without losing long-window ROAS. Proof: TREEPLLA daily spend +550% while holding ROAS; Candivore spend +25% without losing performance. |
| 8. not_stated x economic_buyer | R1 = `not_stated` AND R2 = `economic_buyer` | They bought rewarded for scale or installs. Leadership measures it on growth, not on a public window. | A rewarded partner judged on growth goals. Proof: TREEPLLA CEO quote on growth goals and daily spend +550%. No window variable in this branch. |

**Branch coverage:** `{{rival_network}}`, `{{case_game}}`, `{{company_name}}`, `{{first_name}}` exist in all 8 cells. `{{reported_window}}` exists in cells 1 to 3 and 5 to 7 only. The C3 multi-network line may appear in any cell where C3 = `multi`; it never changes the angle.

**Guardrails (all cells):** never describe the rival's result as weak; no "we beat other networks" opener; no D180 or D360 numbers; no ROAS guarantees; no raising the 2026 App Store removal unprompted [MS], [FA].

**Niche-native test:** every angle hangs on this studio's own rival case study and the window it reports. A rival network could not send it unchanged, because none claims the 90-day reward-window proof (`context/positioning/positioning.md`).

## 6. Variables contract [ENGINE]

| Variable | Source field | Exists in branches |
|---|---|---|
| `{{first_name}}` | Clay Find People: first name | All 8 |
| `{{company_name}}` | Clay company enrichment: name, cleaned (no "Ltd", "GmbH", "Inc") | All 8 |
| `{{rival_network}}` | Signals table: source network (Mistplay, adjoe, Gamelight, Persona.ly). AppsFlyer pages: network named in the case study | All 8 |
| `{{case_game}}` | Case-study page heading: game title | All 8 |
| `{{reported_window}}` | Formula from R1 cluster: `short` = "D7", `d30` = "D30", `long` = "D60+" (label, never the raw number) | Cells 1, 2, 3, 5, 6, 7. Never 4 or 8 |
| `{{is_multi_network}}` | C3: `true` when distinct networks per domain is 2 or more | All 8 (line used only when `true`) |
| `{{sender_name}}`, `{{sender_title}}` | `facts.md` sender identity: Mide Olayiwola, Growth Lead, Almedia | All 8 |

Internal fields (routing and rep reference, never in copy): `window_cluster` (R1), `persona` (R2), `store_market` (S4: us / de / both), `case_study_url`, `case_study_date`, `email_status`.

## 7. Cadence and channel [ENGINE]

**Periodicity:** always-on. Month 1 works the backlog from a full crawl of all five index pages; after that n8n re-crawls weekly (Mondays) and only new case studies enter. Dedupe: an account contacted in the last 90 days is skipped; a new case study for the same studio re-enters it with the new signal stacked ([GTM] step 1).

**Channel:** email (PlusVibe) plus LinkedIn (rep tasks in HubSpot; no LinkedIn automation in the stack [GTM]).

| Day | Champion | Economic buyer (starts day 8, or day 1 if no champion) |
|---|---|---|
| 1 | Email 1: cell angle plus one proof point | |
| 2 | LinkedIn connect (empty, no note) | |
| 4 | Email 2: second proof (Superbox head-to-head backup) | |
| 7 | LinkedIn DM 1 | |
| 8 | | Email 1: cell angle (cells 5 to 8) |
| 10 | Email 3: short close | |
| 11 | | LinkedIn connect (empty, no note) |
| 12 | LinkedIn DM 2 | |
| 13 | | Email 2 |
| 14 | | LinkedIn DM 1 |
| 17 | | Email 3: short close |
| 19 | | LinkedIn DM 2 |

Spacing is a v1 default, to change after the first 4 weeks' data ([GTM] step 11). DM schedule updated 2026-11-27 (2 DMs per persona), approved by Mide Olayiwola. LinkedIn DMs only go out if the connection is accepted.

**Email status routing ([GTM] step 7):** valid = email plus LinkedIn; catch-all = LinkedIn first, email only from a low-volume catch-all inbox; invalid or not found = LinkedIn only; neither = drop.

**Language:** English for all West accounts, DE included (assumption: UA teams at German studios work in English; switch to a German variant if replies show otherwise).

**Reply routing:** per [GTM] step 9. Any reply naming a window ("we judge at D30") is logged to HubSpot for the champion follow-up.

---

## Definition of done

- [x] Mother intent: one sentence, signal-led, matched to the catalog
- [x] Inclusion: ICP box, trigger definition, recipients, tagged [ICP]
- [x] Exclusion: who is out and why
- [x] Sources: trigger plus every enrichment
- [x] Signals table: every read deterministic, every role declared
- [x] Count clusters declared for R1
- [x] Routing matrix with angle column complete (8 cells)
- [x] Branch coverage checked
- [x] Variables contract mapped
- [x] Engine and ICP markers on every section
- [x] Cadence and channel declared

## Blockers before send (not before copy drafting)

- Resolved 2026-11-27: Candivore window, D90 and spend rows added to `facts.md`
- Resolved 2026-11-27: `facts.md` claims approved and sender set (Mide Olayiwola, Growth Lead)
- HubSpot not authorized: exclusion check S6 is manual

## Next step

Copy approved. Next: `/clay-build-plan` or `/campaign-contract` to build the Clay table, then sequencer export (`/campaign-copy` Phase 3) before launch.

---

## Copy

Written with `/campaign-copy` from the approved angles above. Facts from `context/messaging/facts.md` only (approved by Mide Olayiwola, 2026-11-27). Routing is exhaustive (R1 has 4 clusters including `not_stated`, R2 has 2 personas), so no fallback lines.

### Email 1 (approved 2026-11-27 by Mide Olayiwola)

Day 1 for the champion (cells 1 to 4), day 8 for the economic buyer (cells 5 to 8). New thread.

**Subject**
- Champion: `{{{case_game}} payback window|{{case_game}} at d90|reward window for {{case_game}}}`
- Economic buyer: `{scaling {{case_game}}|{{case_game}} growth|rewarded spend at {{company_name}}}`

**Shape**
```
{{first_name}},

{{e1l1}}

{{e1l2}}

Almedia is a rewarded user acquisition platform: advertisers pay when a Freecash user takes a real action, like playing for a set time or making a purchase.

{{e1_proof}}

{{e1_multi}}

{{e1_cta}}

{Best,|Cheers,}
Mide Olayiwola
Growth Lead, Almedia
```

Value line: locked Variant A from `facts.md`, kept by decision of Mide Olayiwola (2026-11-27): do not assume every prospect knows Almedia.

**Line 1 (`e1l1`)**
- + Cell 1 (short x champion): Read {{rival_network}}'s case study on {{case_game}}; it reports {{reported_window}} results.
- + Cell 2 (d30 x champion): Read {{rival_network}}'s case study on {{case_game}}; it tracks results to {{reported_window}}.
- + Cell 3 (long x champion): Read {{rival_network}}'s case study on {{case_game}}; it already reports long-window results.
- + Cell 4 (not_stated x champion): Read through the {{rival_network}} case study on {{case_game}}.
- + Cell 5 (short x economic_buyer): Read {{rival_network}}'s case study on {{case_game}}.
- + Cell 6 (d30 x economic_buyer): Read the {{case_game}} case study {{rival_network}} published.
- + Cell 7 (long x economic_buyer): Read {{rival_network}}'s write-up on {{case_game}}, with results well past D30.
- + Cell 8 (not_stated x economic_buyer): Read the {{rival_network}} case study on {{case_game}}.

**Line 2 (`e1l2`)**
- + Cell 1: Sounds like D7 is working for you. How does that same spend look by D90?
- + Cell 2: D30 is probably the bar you hold rewarded partners to. What happens to those cohorts between D30 and D90?
- + Cell 3: Which probably means you judge rewarded partners on long cohorts already. How long does the reward window run on your side?
- + Cell 4: What window do you judge rewarded on for that game: D30, D90, or longer?
- + Cell 5: So rewarded is probably already in the plan at {{company_name}}. My guess is the open question is how long that spend keeps paying back past {{reported_window}}.
- + Cell 6: My guess is rewarded clears your {{reported_window}} bar today, so the question is how far spend can grow from there.
- + Cell 7: So your team probably judges rewarded on long windows already. The question then is likely how much more budget you can put behind it.
- + Cell 8: So rewarded is probably part of how {{company_name}} grows. Could be off, but I'd guess the question is which partners can take more of that spend.

**Proof (`e1_proof`)**
- + Cells 1, 3, 4: Candivore extended its reward window from 50 to 90 days and ended up with D90 ROAS up 70%.
- + Cell 2: Candivore's D30 ROAS was up 65%, to 2x the D30 goal. With its reward window extended from 50 to 90 days, D90 ROAS was up 70% too.
- + Cell 5: TREEPLLA scaled daily spend by 550% while maintaining strong ROAS.
- + Cell 6: TREEPLLA hit D30 ROAS 2x competitor benchmarks, with daily spend up 550%.
- + Cell 7: TREEPLLA scaled daily spend by 550% while maintaining strong ROAS, and Candivore scaled ad spend 25% without losing performance.
- + Cell 8: TREEPLLA's CEO, San Heo: "We came into this partnership with aggressive growth goals, and Freecash helped us blow past every one of them."

**Multi-network line (`e1_multi`)**, only when `{{is_multi_network}}` = true; otherwise empty
- + Champion cells: You already run more than one rewarded partner, so one more in the comparison shouldn't be a big lift.
- + Economic-buyer cells: You already spread rewarded spend across more than one partner, so testing another is familiar ground.

**CTA (`e1_cta`)**
- Champion: `{Worth running one cohort with us and reading it at D90?|Open to testing one cohort with us and checking it at D90?|Would one test cohort, read at D90, be useful?}`
- Economic buyer: `{Is rewarded spend going up at {{company_name}}?|Is more rewarded spend planned at {{company_name}}?|Are you planning to grow rewarded spend?}`

**Sample as received (cell 1; "Maya", "Merge Valley" and Mistplay are a made-up example, not real data)**

> Subject: Merge Valley payback window
>
> Maya,
>
> Read Mistplay's case study on Merge Valley; it reports D7 results.
>
> Sounds like D7 is working for you. How does that same spend look by D90?
>
> Almedia is a rewarded user acquisition platform: advertisers pay when a Freecash user takes a real action, like playing for a set time or making a purchase.
>
> Candivore extended its reward window from 50 to 90 days and ended up with D90 ROAS up 70%.
>
> Worth running one cohort with us and reading it at D90?
>
> Best,
> Mide Olayiwola
> Growth Lead, Almedia

79 words. Longest route (cell 8 plus multi-network line): about 114 words including signature, under the 120 ceiling.

### Email 2 (approved 2026-11-27 by Mide Olayiwola)

Same thread, subject `Re:` plus the Email 1 subject. Routed by persona (R2) only; static within a persona. Run as one sequencer campaign per persona.

**Champion (day 4)**
```
{{first_name}},

{One more result, next to the Candivore one:|A second result to sit next to Candivore's:|Adding one more result to the Candivore one:}

Superbox saw 1.5 to 2x higher D30 ROAS than non-rewarded channels, and 3x higher D30 retention than other rewarded channels.

{Is D30 retention one of the numbers you compare rewarded partners on for {{case_game}}?|Do you line up D30 retention across rewarded partners for {{case_game}}?|Are you comparing D30 retention across your rewarded partners on {{case_game}}?}

{Best,|Cheers,}
Mide
```

**Economic buyer (day 13)**
```
{{first_name}},

{One more result, next to TREEPLLA's:|A second result to sit next to the TREEPLLA one:|Adding one more result to the TREEPLLA one:}

Superbox saw 1.5 to 2x higher D30 ROAS than non-rewarded channels, and 3x higher D30 retention than other rewarded channels.

{With rewarded already in the mix at {{company_name}}, that second number is probably the one your UA team watches.|Since {{company_name}} already runs rewarded, my guess is the second number matters most to your UA team.}

{Should I send the details to whoever runs UA on your team?|Worth me passing this to the person who owns UA on your team?|Want me to send this over to whoever leads UA on your team?}

{Best,|Cheers,}
Mide
```

### Email 3 (approved 2026-11-27 by Mide Olayiwola)

Same thread. Routed by persona only.

**Champion (day 10)**
```
{{first_name}},

{Last note from me on this.|I'll leave it here after this one.|Keeping this last one short.}

Candivore also scaled ad spend 25% without losing performance.

{If a test like that sits with someone else at {{company_name}}, who should I talk to?|If someone else at {{company_name}} owns a test like that, who would it be?|Is a test like that yours to run, or should I talk to someone else at {{company_name}}?}

{Best,|Cheers,}
Mide
```

**Economic buyer (day 17)**
```
{{first_name}},

{Last note from me.|I'll leave it here after this one.|Keeping this last one short.}

Potato Play, a studio we worked with, scaled from 5 to 15 markets with 26% higher D30 ARPU.

{Are more markets on the plan at {{company_name}}, or should I close the loop here?|Is market expansion on the plan at {{company_name}}, or should I close the loop?|Are new markets coming up at {{company_name}}, or should I leave it here?}

{Best,|Cheers,}
Mide
```

### LinkedIn (approved 2026-11-27 by Mide Olayiwola)

Connection request: empty, no note (champion day 2, economic buyer day 11). DMs only if accepted. No greeting, signature or PS. Sent by the rep from HubSpot tasks.

**DM 1 (`dm1`)**, one per cell (champion day 7, economic buyer day 14)
- + Cell 1 (short x champion): {{first_name}}, any plans to read rewarded cohorts on {{case_game}} past {{reported_window}}?
- + Cell 2 (d30 x champion): {{first_name}}, are you reading rewarded cohorts on {{case_game}} past D30, or is D30 the main window?
- + Cell 3 (long x champion): {{first_name}}, do you set the reward window to match the window you judge on for {{case_game}}?
- + Cell 4 (not_stated x champion): {{first_name}}, is D30 or D90 the window you judge rewarded on for {{case_game}}?
- + Cell 5 (short x economic_buyer): {{first_name}}, is rewarded spend on {{case_game}} set to grow, or holding steady for now?
- + Cell 6 (d30 x economic_buyer): {{first_name}}, any plans to grow rewarded spend on {{case_game}} beyond where it is today?
- + Cell 7 (long x economic_buyer): {{first_name}}, is the plan to put more budget behind rewarded on {{case_game}}, or keep it where it is?
- + Cell 8 (not_stated x economic_buyer): {{first_name}}, are you adding rewarded partners at {{company_name}}, or sticking with the current ones?

**DM 2**, static per persona (champion day 12, economic buyer day 19)
- Champion: `{Asking because|Only asking since|Reason I ask:} Candivore extended its reward window from 50 to 90 days and ended up with D90 ROAS up 70%. {Happy to share more if it's useful.|Can share more if helpful.|Glad to send details if useful.}`
- Economic buyer: `{Asking because|Only asking since|Reason I ask:} TREEPLLA scaled daily spend by 550% while maintaining strong ROAS with us. {Happy to share more if it's useful.|Can share more if helpful.|Glad to send details if useful.}`

Champion DM 2 reuses the Candivore D90 fact from Email 1 in different words on purpose: many LinkedIn accepters never opened the email.

### Review record

Persona review (UA Manager, CEO) and human test run on the full sequence 2026-11-27: passed. QA: insult, nexus, facts traced to `facts.md`, spintax same-meaning only, no em dashes or "!", subject unchanged in thread, no repeated lines across emails. Word counts: E1 79 (cell 1 sample, longest route about 114), E2 champion 45, E2 economic buyer 58, E3 champion 38, E3 economic buyer 40, DM 1 max 19, DM 2 max 27.

Before launch: final manual read against `knowledge-base/playbooks/copy-iron-laws.md`; HubSpot exclusion check (S6) is still manual.
