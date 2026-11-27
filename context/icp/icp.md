# Almedia ICP

Built only from `context/docs/research/`. Source key: [CO] company.md, [CU] customers.md, [SI] signals.md, [MK] market.md, [LP] leadership-posts.md, [CP] competitors.md, [VO] voice.md. INFERRED = our reading of the research, not a stated fact.

Two products, two buyers:
- **Freecash (rewarded UA):** advertisers pay per user action. Main ICP. [CO]
- **Link (publisher monetization):** Almedia pays the publisher per linked player. [CO]

## 1. Firmographic

| Attribute | Fit | Source |
|---|---|---|
| Industry | Mobile game publishers and studios. Every named case study is a mobile game. | [CU], [LP] "primarily mobile game publishers and retailers" |
| Genre | Casual, puzzle, merge, word games (Jewels Jungle, Match Masters, Office Cat, Word Collect, Word Farm Adventure, Merge Inn) | [CU] (genre grouping INFERRED) |
| Secondary | Retailers (cashback), brands and apps ("now for brands"). Predicted next: fintech, retail, finance, education, iGaming, health/fitness | [CO], [LP] |
| Markets they acquire in | US, DE, GB, CA, FR (top payout markets; TREEPLLA's launch markets) | [CO], [CU] |
| Almedia sales coverage | Berlin, Seoul, Tokyo, Beijing, New York, London | [CO] |
| Company size | Open question. No customer headcount or revenue found. Summit guests "representing $10B+ in combined yearly revenue". | [CU], [LP] |
| Studio size hint | "100% ROAS before the rewarded window ends… most common with smaller studios" | [LP] |

## 2. Technographic

| Attribute | Fit | Source |
|---|---|---|
| Paid UA stack | Already buys on Google, Meta, AppLovin (Almedia's named budget rivals) | [LP] |
| Rewarded networks | May already use other rewarded channels (Superbox benchmark was "other rewarded UA channels") | [CU] |
| Platforms | iOS and Android | [CU] (Candivore) |
| Measurement | Tracks cohort ROAS and retention at D7/D30/D60/D90+ (every case study reports these) | [CU] |
| MMP | Open question. Almedia cites AppsFlyer and Singular indexes; customer MMP use not stated. | [CO] |
| Link fit | Can add an SDK or "magic link" and choose in-game placements | [CO] |

## 3. Intent signals

Only signals you can see from outside the account, ranked by how close they are to a buy. Each has a named example in the research.

| # | Observable signal | How to spot it | Research example | Source |
|---|---|---|---|---|
| 1 | Already buys rewarded UA from a rival | Named on a competitor's site or case study | TREEPLLA is quoted by Mistplay and is an Almedia case study; Netmarble, Caveduck (Mistplay); Zynga logo (exmox) | [CP], [CU] |
| 2 | Attended or spoke at Almedia events | Summit panels, ChinaJoy, G-STAR, Gamesforum Vietnam | PlayStudios, Papaya, Whalo, Unico Studio, Original Games, Tatem Games, Supersolid on Summit panels | [LP], [SI] |
| 3 | Casual, puzzle, merge or word title live in US, DE, GB or CA | Store listing genre plus top-grossing markets | Games popular on Freecash: Merge Restaurant, Word Farm Adventure, Word Collect, Office Cat. US 57.9%, DE 9.7%, UK 8.2%, CA 3.7% of payouts | [CU], [CO] |
| 4 | Expanding to new countries | Launch news, new country store listings | TREEPLLA launched DE, GB, CA, FR; Potato Play went 5 to 15 markets | [CU] |
| 5 | Relaunch or reactivation of an older title | Update or relaunch announcement | TREEPLLA Office Cat: "it was a relaunch powered by insight" | [CU] |
| 6 | Publisher with many live titles (Link) | Count of titles on the developer's store page | Ovivo 24 titles, SpringComes 13, Gryphon Games 6 | [CU] |
| 7 | Studio in Korea, Japan or China | HQ location | Almedia is hiring growth sales roles in Seoul, Tokyo, Beijing | [CO] |

Removed as not observable or not supported: rising CPI (applies to every UA vendor; figure unsourced [MK]), soft launch (only Almedia's unsourced 63% stat [SI]), hiring UA managers (no data [SI]). Internal pains (weak retention, ROAS pressure) moved to `personas.md` as discovery questions, not list filters.

Open question: which signal converts best. No win data in research.

## 4. Persona (detail in personas.md)

| Role | Titles seen in research | Source |
|---|---|---|
| Champion | UA Manager, UA Lead, Senior Manager | [CU] |
| Economic buyer | CEO, Co-Founder, COO | [CU] |
| Influencer | Marketing Director | [CU] (role mapping INFERRED) |

## 5. Engagement readiness

What a prospect must already have for a first campaign to work. Each item is something the setup or results depend on, per the research. Case-study spend growth is an outcome, not a prerequisite, so it is not used here.

| # | Ready when | Why it matters | How to check | Source |
|---|---|---|---|---|
| 1 | Game is live and earns from players (IAP or ads) | Rewarded users must pay back; Almedia: "Strong product quality to sustain UA success"; advertisers "aim to reach 100% ROAS before the rewarded window ends" | Store listing shows in-app purchases; top-grossing presence | [LP] |
| 2 | Can track in-game events and milestones | Rewards are paid on milestones: "Users complete levels and purchase activities unique to your app"; "Custom reward structures and challenges" | Ask on discovery call | [CO], [VO] |
| 3 | Judges channels on D30+ cohort ROAS, not CPI | Reward windows run 50 to 90 days (Candivore); "measuring true success not by the volume of installs, but on post-install value" | Ask what ROAS window UA is held to | [CU], [LP] |
| 4 | Has a UA owner who can launch a test and move budget | Setup is "Initial consultation, Campaign design, Reward build, Go live"; "Launch markets, shift budgets… without waiting on anyone"; Superbox began with one CPI-based test | Named UA Manager or Lead exists | [CO], [VO], [CU] |
| 5 | For Link: can add an SDK and choose in-game placements | "Install in an afternoon with our SDK"; "You control entry points (button, modal, rewarded moment)" | Ask who owns the client build | [CO], [VO] |

Not ready yet: pre-launch games with no monetization data; teams that cannot report beyond D7. (INFERRED from items 1 and 3.)

Open questions: minimum monthly budget, minimum DAU or revenue, and required MMP. None found in research.

## Not a fit (and why)

| Not a fit | Why | Source |
|---|---|---|
| Teams judging only on CPI or short-term ROAS | Almedia sells long-window value (D30 to D360); COO calls short-term ROAS over-reliance "the mobile sector's most common mistake" | [LP], [SI] |
| Games with weak monetization or product | "Strong product quality to sustain UA success" | [LP] |
| Non-gaming brands needing proven vertical results | No non-gaming case study found; brands product is "now for brands" | [CU] |
| Advertisers with strict brand-safety rules on reward apps | 2026 App Store removal, TechCrunch "scammed" coverage, BBB complaints | [CO] (INFERRED risk) |

## Open questions

- Ideal company size and UA budget floor
- Minimum spend or contract terms (not found)
- Win rate by genre, platform or region
