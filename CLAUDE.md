# Almedia GTM Context OS

## Company

Almedia (Berlin, founded 2020, bootstrapped) runs Freecash, a rewarded user acquisition platform where advertisers, mainly mobile game publishers, pay when its 95M+ users take real in-app actions, plus Link, which pays publishers per player linked. Source: `context/docs/research/company.md` (https://almedia.co/about).

## How this folder works

- `.claude/skills/`: reusable Claude skills for repeat GTM tasks. Read when a task matches a skill.
- `context/icp/`: ideal customer profiles and buyer personas. Read before any targeting, list building or copy.
  - `icp.md`: five-layer ICP plus who is not a fit. `personas.md`: champion, economic buyer, influencer. `signal-matrix.md`: segments x personas, buying signals, workflow tracker.
- `context/positioning/`: positioning, differentiation and competitors. Read before writing messaging or copy.
  - `positioning.md`: category, target, alternative, unique value, statement. `value-proposition.md`: job, pain, gain, proof per persona. `competitors.md`: competitor table, wins, losses, responses.
- `context/messaging/`: approved messaging, value props and proof points. Read before writing any copy.
  - `messaging.md`: core message, pillars, persona angles, words to use and avoid. `facts.md`: the only source of names, claims and numbers for copy (approval pending).
- `context/brand-kit/`: voice, tone, visual and style rules. Read before producing anything customer-facing.
  - `brand.md`: tone of voice and key phrases from Almedia's own copy.
- `context/docs/`: `case-studies.md`, every customer story with result, quote and source. Read before citing proof. `gtm-system.md`: the end-to-end outbound system (steps, tools, decisions). Read before building or changing a workflow.
- `diagrams/`: flowchart specs and SVGs for Miro (`almedia-gtm-system.json`).
- `context/docs/research/`: raw research notes with sources. Read when you need to verify or cite a fact.
  - `company.md`, `customers.md`, `competitors.md`, `market.md`, `signals.md`, `voice.md`, `leadership-posts.md`, `customer-videos.md`, `rival-network-clients.md`, `almedia-website-2026-11-25.md`.
- `knowledge-base/playbooks/`: step-by-step GTM workflows. Read before running or specing a workflow.
- `knowledge-base/learnings/`: what worked, what failed, and why. Read before planning a new campaign.
- `inspiration/`: ads and examples from other companies to learn from. Read when drafting copy or creative for ideas, never copy verbatim.
- `meetings/`: meeting notes and transcripts. Read when a task references a meeting or decision.
- `output/campaigns/`: finished campaign assets. Write deliverables here; read to reuse past work.
- `output/outbound/`: outbound sequences, emails and call scripts. Write outbound deliverables here; read before writing new outbound.
- `output/social/`: social posts and content. Write social deliverables here; read before drafting new posts.
- `output/data/`: lists, exports and analysis outputs (CSV/XLSX are gitignored). Write data outputs here; read when a task needs past data.
- `tools/`: tool configs, scripts and integration notes. Read when a task touches a GTM tool.
- `weekly-priorities/`: one file per ISO week (`YYYY-Www.md`). Read at the start of every session.
- `work-log/`: one file per ISO week logging every change. Read at session start; append after every change.

## Rules

1. Cite a source (URL or file path) for every company fact.
2. Never invent numbers. If a figure is unknown, write "unknown" and flag it.
3. No em dashes in any copy.
4. Ask before sending or publishing anything.
5. Log every change in this week's work log (`work-log/YYYY-Www.md`) with a timestamp.

## Skills

In `.claude/skills/`, imported from github.com/bolaji-ships/gtm-starter-kit. Run with `/<name>`.

Strategy and copy (typical order: signal-matrix, campaign-strategy, build-workflow-spec, campaign-copy):
- `signal-matrix`: builds ICP and signal matrices (segments plus the signals that find them). Saves to `context/icp/signal-matrix.md`.
- `campaign-strategy`: generates 15 to 25+ tiered outbound campaign ideas. Saves to `output/campaigns/campaign-strategy.md`.
- `build-workflow-spec`: turns one campaign idea into a gated workflow spec (no copy). Saves to `output/campaigns/<slug>/workflow-spec.md`.
- `campaign-copy`: writes cold email and LinkedIn DM copy, only from an approved workflow spec and verified facts.
- `prompt-builder`: builds or repairs a reusable per-row prompt, such as a Clay AI column prompt.

Clay build and run:
- `clay-build-plan`: step-by-step Clay build guide plus a flow diagram, from a workflow spec. Instructions only.
- `campaign-contract`: writes `contract.md`, the build sheet for one Clay campaign table.
- `design-clay-table-json`: writes the Clay table JSON blueprint from a campaign contract.
- `import-clay-table`: imports a table JSON into Clay, tests paid columns on sample rows, runs the rest only within budget.
- `build-clay`: builds, audits or repairs a full Clay outbound workbook (Companies and People tables).
- `save-clay-schema`: saves an approved Clay table to the local registry in `tools/rex/registry/`.
- `export-tables`: exports Clay tables to local CSV.

QA, cost and deliverability:
- `campaign-qa`: checks a Clay table or Instantly/PlusVibe campaign against its workflow spec.
- `calculate-costs`: reports the real dollar and credit cost of a Clay table's columns.
- `workspace-cost-audit`: reports a whole Clay workspace's spend for one month.
- `inbox-placement-test`: inbox placement test on cold email senders (EmailBison plus MailReach).

Research and diagrams:
- `crawl4ai`: crawls websites into clean Markdown or JSON, free and local.
- `agent-browser`: drives a browser to click, fill forms, log in and screenshot.
- `miro-gtm-flowchart`: draws a GTM system as an editable flowchart on a Miro board.

## Tools

- **Miro** (MCP, via the `miro@miro-ai` plugin): for diagrams, such as workflows, account maps and campaign flows. Enabled in `.claude/settings.json`.
- **Notion** (MCP, `https://mcp.notion.com/mcp`, configured in `.mcp.json`): where we publish finished docs. GitHub stays the source of truth, so write and edit here first, then publish to Notion. Ask before publishing (rule 4).

<!-- Empty for now. -->
