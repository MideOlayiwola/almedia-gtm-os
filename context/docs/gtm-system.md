# Almedia outbound GTM system

Work in progress. Built from `context/icp/icp.md`, `context/icp/personas.md` and `context/icp/signal-matrix.md`, with copy rules from `context/messaging/`. Segments (S1 to S4), signals (#1 to #10) and workflows (W1 to W8) refer to `signal-matrix.md`.

Tools: **GitHub** (Context OS repo, source of truth), **Claude Code** (reads the Context OS, writes specs and copy, weekly review), **Clay** (signals, enrichment, ICP check, routing, people, emails), **n8n** (schedules, webhooks, glue between tools), **PlusVibe** (email sending and inbox), **HubSpot** (CRM, LinkedIn tasks, pipeline).

Diagram: Miro board "Almedia GTM System": https://miro.com/app/board/uXjVEJJa834=/ (spec: `diagrams/almedia-gtm-system.json`, rebuild with `.claude/skills/miro-gtm-flowchart/scripts/build_flowchart.py`).

## Step 0: Context OS

| | |
|---|---|
| What happens | ICP, personas, signal matrix, messaging and `facts.md` live in the repo. Every later step reads from here; nothing is typed from memory. |
| Tool | GitHub (store), Claude Code (read, update, run skills) |
| Decision: are the claims in `facts.md` approved? | Yes → copy can be sent. No (today: all "pending") → copy stays draft; nothing goes to PlusVibe. |
| Decision: is the sender set in `facts.md`? | Yes → sequences can be built. No (today: "unknown") → stop at step 8. |

## Step 1: Buying signals (always on)

| | |
|---|---|
| What happens | n8n runs each signal on a schedule and writes hits into one Clay "Signals" table (company name, signal #, date, evidence URL). |
| Tool | n8n (schedule, scrapes), Clay (Find Jobs, Find People, HTTP) |
| Schedule | #1 rival case-study pages: weekly. #2 event speaker pages: weekly in event season. #3 UA hiring: weekly. #4 new Tier-1 market launch: weekly (needs store-intelligence API). #5 publisher new title: monthly. #6 new UA leader: monthly. |
| Decision: same company already hit in the last 90 days? | No → new row, go to step 2. Yes, same signal → skip. Yes, new signal → add the signal to the existing row (stacking), re-run step 4. |

## Step 2: Find companies

| | |
|---|---|
| What happens | Turn each signal hit (a game, studio or speaker name) into one company with a domain. |
| Tool | Clay (company lookup from name, developer page on the App Store or Google Play) |
| Decision: domain found? | Yes → step 3. No → "Needs review" view in Clay, checked weekly; dropped after 2 weeks. |

## Step 3: Enrichment

| | |
|---|---|
| What happens | Add 2 to 4 facts the routing and copy need: genre of top titles, number of live titles, markets live in (Tier-1 or not), HQ region (West or Asia), monetization (in-app purchases yes or no), headcount. |
| Tool | Clay (company enrichment, store data via HTTP) |
| Decision: enrichment complete? | Yes → step 4. Missing genre or titles → one retry with a second provider; still missing → "Needs review". |

## Step 4: ICP fit check

| | |
|---|---|
| What happens | Clay formula columns apply `icp.md` sections 1 and 5. |
| Tool | Clay (formulas), HubSpot (lookup) |
| Decision: casual, puzzle, merge or word games? | Yes → next check. No, other games → drop. No, non-gaming app → S4 holding list (parked, no outreach). |
| Decision: live and monetizing? | Yes → next check. No → "Not ready" list, re-checked in 90 days. |
| Decision: already in HubSpot? | No → step 5. Customer → send to account owner, no outreach. Open deal → notify deal owner, no outreach. Closed lost over 90 days ago → step 5 with a re-engage tag. Unsubscribed → drop. |

## Step 5: Routing by segment

| | |
|---|---|
| What happens | Each account gets one segment, one lead product and one angle from `signal-matrix.md`. |
| Tool | Clay (formula), angles from `messaging.md` |
| Decision: on the rival rewarded list (#1)? | Yes → **S1** Rival rewarded users. Lead Freecash, long-window angle (Candivore D90), Link upsell. |
| Decision: 5 or more live titles? | Yes → **S3** Multi-title publishers. Lead Link (Gryphon Games, Ovivo), Freecash upsell. If also on the rival list, S1 wins and Link becomes the upsell. |
| Otherwise (scaling trigger #3 or #4) | → **S2** Scaling studios, rewarded status unknown. Angle "your first rewarded partner" (Superbox). First message asks if they run rewarded today. |
| Decision: region? | West → English sequence. Asia (KR, JP, CN) → local-language sequence and an Asia sender (open question: who). |

## Step 6: Find people

| | |
|---|---|
| What happens | Up to 3 contacts per account, one per persona. |
| Tool | Clay (Find People by title) |
| Titles | Champion: User Acquisition Manager, UA Lead, Head of UA. Economic buyer: CEO, Co-Founder, COO. Influencer: Marketing Director, Head of Growth. For S3 add monetization or product leads (INFERRED; no Link buyer title in research). |
| Decision: champion found? | Yes → champion gets the first sequence; others follow 1 week later. No → economic buyer leads (common at small studios, INFERRED). Nobody found → "Needs review"; dropped after 2 weeks. |

## Step 7: Find and verify emails

| | |
|---|---|
| What happens | Email waterfall across providers, then verification. |
| Tool | Clay (waterfall plus verifier) |
| Decision: email status? | Valid → email plus LinkedIn sequence. Catch-all → LinkedIn first; email only on a low-volume catch-all inbox (cap set after the first send). Invalid or not found → LinkedIn only. |
| Decision: LinkedIn profile found? | Yes → LinkedIn steps added. No → email only. Neither email nor LinkedIn → drop. |

## Step 8: Sequence (email and LinkedIn)

| | |
|---|---|
| What happens | Claude Code writes copy per segment and persona with `/build-workflow-spec` then `/campaign-copy`, using only `facts.md`. A person approves every new sequence before launch (CLAUDE.md rule 4). Email goes out from PlusVibe; LinkedIn steps go to the rep as HubSpot tasks. |
| Tool | Claude Code (copy), GitHub (spec saved in `output/campaigns/`), PlusVibe (email), HubSpot (LinkedIn tasks), n8n (pushes Clay rows to PlusVibe and HubSpot) |
| Shape | Email 1 (signal plus one proof point), LinkedIn connect, email 2 (second proof), LinkedIn message, email 3 (short close). Spacing set in the workflow spec. |
| Decision: sequence approved? | Yes → launch. No → back to Claude Code with edits. |
| Decision: account in Asia? | Yes → local-language copy and Asia sender. No → English. |

## Step 9: Reply handling

| | |
|---|---|
| What happens | PlusVibe sends each reply to n8n by webhook; n8n tags the reply type and acts. A rep checks every tag before anything is sent back. |
| Tool | PlusVibe (inbox), n8n (webhook, tagging), HubSpot (records) |
| Interested | → HubSpot deal at "Meeting requested", rep books the call. |
| Answers "do you run rewarded?" | Yes → move from S2 to S1 angle. No → stay in S2, "first rewarded partner" follow-up. |
| Objection (App Store removal, data, price) | → rep answers using `context/positioning/competitors.md` "How to respond"; price is an open question, send to sales lead. |
| Not now | → stop sequence, HubSpot task to re-contact in 90 days. |
| Wrong person or referral | → add the named person in Clay (step 6), sequence them with the referral mention. |
| Out of office | → pause, resume on return date. |
| Unsubscribe or angry | → stop everywhere, HubSpot "Do not contact", global suppression in PlusVibe. |
| Bounce | → mark email invalid in Clay and HubSpot, switch to LinkedIn only. |

## Step 10: CRM

| | |
|---|---|
| What happens | HubSpot is the single record. Every contact pushed to a sequence is created or updated there with: segment, signal #, workflow W#, persona, region, sequence name, email status. |
| Tool | HubSpot (n8n keeps it in sync with Clay and PlusVibe) |
| Pipeline stages | Meeting requested → Meeting held → Test campaign scoped → Test live → Scaling → Closed lost. (INFERRED from the Superbox "first CPI-based test" path; confirm with sales.) |
| Decision: meeting held? | Yes → "Meeting held". No-show → one rebook attempt, then "Not now" (90 days). |
| Decision: test live? | Yes → track ROAS at D7, D30, D90 as the case studies do. Lost → reason logged; goes into step 11. |

## Step 11: Weekly feedback loop

| | |
|---|---|
| What happens | Every Monday n8n exports last week's numbers from PlusVibe and HubSpot per workflow (sent, replies, positive replies, meetings, by segment, signal and persona). Claude Code reviews them against the Context OS and proposes changes; a person approves; changes are committed to GitHub. |
| Tool | n8n (export), Claude Code (review, edits), GitHub (commit), HubSpot and PlusVibe (data) |
| Writes to | `context/icp/signal-matrix.md` Matrix 3 tracker; `knowledge-base/learnings/` (what worked, what failed); `context/messaging/` (angles, words to avoid); `context/messaging/facts.md` (new approved proof); `weekly-priorities/`; `work-log/` |
| Decision: workflow reply rate below target 2 weeks running? | Yes → change the copy angle (one variable at a time). Still low after 2 iterations → pause the signal and log why in `knowledge-base/learnings/`. No → keep running; scale volume. Targets: unknown, set from the first 4 weeks' baseline. |
| Decision: new objection seen 3+ times? | Yes → add a response to `competitors.md` and a line to `personas.md`. |
| Decision: new customer result? | Yes → add to `context/docs/case-studies.md`, then to `facts.md` as pending until approved. |

## Four pillars check

| Pillar | How the system meets it | Gap |
|---|---|---|
| Clean data | One company per domain (step 2); 90-day dedupe (step 1); verified emails only (step 7); HubSpot as single record with suppression (steps 4, 9, 10); every claim from `facts.md` | HubSpot connector not yet authorized; property names to agree with sales |
| Always-on signals | n8n runs each signal on a schedule (step 1); stacking when a known account fires again | Signal #4 depends on a store-intelligence API not yet confirmed |
| Composable workflows | Universal signals (#2, #3, #6, #7) are one Clay build reused by keyword swaps; segments are routing rules, not separate builds; copy comes from reusable skills | Asia copy and sender not defined |
| Tight feedback loops | Weekly review writes back into the Context OS (step 11); reply tags reroute accounts live (step 9) | No baseline targets yet; LinkedIn results only as good as reps' HubSpot task logging |

## Open questions

- Sender identity (West and Asia) and approval of `facts.md` claims: both block step 8
- LinkedIn automation: none of the six tools automates LinkedIn; today it is rep tasks in HubSpot
- HubSpot authorization in Claude, and whether a HubSpot deal pipeline already exists
- Store-intelligence API (AppMagic, Appfigures or Sensor Tower) for signals #4 and #5
- Clay credit budget per month; PlusVibe inbox and domain count
- Reply-rate and meeting targets (set after 4 weeks)
