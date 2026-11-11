# kimi-marketing-skills-plugin

**53 marketing skills for [Kimi Code](https://www.kimi.com/code) — copywriting, SEO & AI-search visibility, paid ads, email, CRO, analytics, pricing, launches, competitor research, and go-to-market strategy. Ported from Corey Haines' `marketingskills` (MIT).**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Platform: macOS / Windows / Linux](https://img.shields.io/badge/Platform-macOS%20%2F%20Windows%20%2F%20Linux-black.svg)]()
[![Kimi Code](https://img.shields.io/badge/Kimi%20Code-plugin-orange.svg)](https://www.kimi.com/code/docs/en/kimi-code-cli/customization/plugins.html)

## Why

Marketing knowledge is scattered across playbooks, courses, and agency lore. This plugin gives your agent **53 specialized skills** covering nearly every marketing discipline, each with expert-level frameworks, worked examples, and hard-won guardrails (e.g. "never buy links that pass ranking credit", "fire conversion tags on confirmed success, not the submit click"). Built by [Corey Haines](https://corey.co) for technical marketers and founders; repackaged here as a Kimi Code plugin.

## Features

| Category | Skills |
|---|---|
| **Copywriting** | `copywriting` — write/rewrite page copy, headlines, promises · `copy-editing` — tighten existing copy, kill AI tells |
| **Content & Social** | `content-strategy` · `social` · `video` · `image` |
| **SEO** | `seo-audit` — technical/on-page audits · `ai-seo` — get cited by ChatGPT/Perplexity/AI Overviews · `programmatic-seo` · `site-architecture` · `schema` · `link-building` · `aso` |
| **Paid Ads** | `ads` — Google/Meta/LinkedIn strategy · `ad-creative` — hooks, angles, variations · `ab-testing` |
| **Email & Messaging** | `emails` — lifecycle flows · `cold-email` — outbound + deliverability · `sms` |
| **Analytics & Tracking** | `analytics` — GA4/GTM/UTMs, tracking plans · `conversion-tracking` — pixels, CAPI, GTM recipes · `attribution` — MMM, incrementality |
| **CRO & Product** | `cro` · `signup` · `onboarding` · `popups` · `paywalls` · `pricing` · `offers` |
| **Growth & Retention** | `referrals` · `free-tools` · `churn-prevention` · `community-marketing` · `lead-magnets` · `co-marketing` · `launch` · `influencer-marketing` · `events` · `directory-submissions` · `public-relations` |
| **Sales & GTM** | `revops` · `sales-enablement` · `prospecting` · `competitors` · `competitor-profiling` |
| **Strategy & Research** | `product-marketing` — the foundation context doc · `marketing-plan` · `marketing-ideas` — 139-tactic library · `marketing-psychology` · `customer-research` · `reverse-engineer-marketing` · `marketing-council` — simulated expert board · `marketing-loops` — recurring agent-run checks |

Skills cross-reference each other: `copywriting` ↔ `cro` ↔ `ab-testing`, `seo-audit` ↔ `schema` ↔ `ai-seo`, `revops` ↔ `sales-enablement` ↔ `cold-email`.

## Install

```
/plugins install https://github.com/mnshkv/kimi-marketing-skills-plugin
```

Then `/plugins reload` (or start a new session).

## Usage

Just ask — the right skill activates from your request:

- "Rewrite our homepage headline and hero copy" → `copywriting`
- "Why did our Google Ads CPA jump 40% this month?" → `ads`
- "Audit our SEO — traffic dropped after the last update" → `seo-audit`
- "Are we getting cited by ChatGPT and Perplexity? How do we improve it?" → `ai-seo`
- "Set up conversion tracking for our signup form" → `conversion-tracking`
- "Write a 5-email welcome sequence" → `emails`
- "What should we charge? Should we raise prices?" → `pricing`
- "How did [competitor] grow? What should we copy?" → `reverse-engineer-marketing`
- "Give me several expert takes on this positioning decision" → `marketing-council`

**Set up the foundation first:** ask "create our product marketing context doc" — the `product-marketing` skill builds `.agents/product-marketing.md` (product, ICP, positioning, voice), which every other skill reads automatically so you stop re-answering the same questions.

**Run recurring marketing checks:** the `marketing-loops` skill plus the SEO/outbound "operator" references define weekly/daily loops (ranking watches, churn watches, outbound triage). Schedule them with Kimi Code's `CronCreate`, or just say "run this every Monday".

## How it works

Each skill is a `SKILL.md` with trigger-rich `name`/`description` frontmatter plus on-demand `references/` deep dives. When your request matches a description, Kimi Code loads the skill and the agent applies its frameworks: diagnose before prescribing, label unavailable data as MISSING instead of guessing, keep observed facts apart from inference, and refuse unsupported claims. Two skills ship helper code: `conversion-tracking` (GTM recipe builder/checker in Python, ready-to-paste JS snippets) and `reverse-engineer-marketing` (`teardown.mjs`, a zero-dependency Node 18+ CLI that scans archived pages for marketing stacks).

## Differences from the original

- **Not ported:** `evals/` and `tests/` (upstream QA harness), the `tools/` directory (67 CLI utilities, API integration guides, Composio layer, partner registry) — these are optional external-API conveniences, not skill content. Links inside skills now point to the [upstream repo](https://github.com/coreyhaines31/marketingskills) for those guides.
- **Adapted:** Claude Code-only mechanics replaced — `ScheduleWakeup`/`/loop` scheduling → Kimi Code `CronCreate`/goal mode; "Claude reads/runs this" → neutral "the agent"; WebFetch → the agent's built-in fetch. Mentions of Claude as an AI *engine* (ChatGPT/Claude/Perplexity citation work) are content, not host references, and stay.
- **Everything else is verbatim:** all 53 skills, references, scripts, and assets, including per-skill `metadata.version`.

## License & attribution

- Upstream: [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills), © [Corey Haines](https://corey.co), [MIT](LICENSE).
- This port: © mnshkv, MIT. Not affiliated with Corey Haines or Kimi.
