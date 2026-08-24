---
name: keyword-research
description: Use this skill to produce the foundational keyword research for a new SEO campaign — 3–5 primary priority groups, each with a focused set of primary keywords, AI visibility-tracking prompts, and a banked reserve of secondary keywords. This is start-of-campaign strategic groundwork that is tracked and revisited as the campaign progresses, not per-article keyword selection (that belongs to content-strategist). Trigger this whenever the user is beginning keyword research for a client or campaign, asks for keyword priority groups, keyword mapping, a keyword strategy, or declining-keyword analysis, or wants to establish which keywords a campaign should target. Use it even if they only say "keyword research" or "KWR" without more detail.
---

# Keyword Research

## Scope

This skill covers the keyword research and prioritisation phase that runs once, at the start of a campaign. Its job is to establish the strategic keyword foundation the campaign is built on and measured against. It does not write content, produce content briefs, or select keywords for individual articles — that is the content-strategist skill's job, downstream of this one.

The output is a **keyword priority map**: 3–5 primary groups (services, categories, or another logical grouping), each containing a focused set of primary keywords, 3–6 AI visibility-tracking prompts, and a banked reserve of secondary keywords for later expansion.

**Entry condition:** A client beginning a campaign, with a completed keyword context document (see below). **Exit condition:** A keyword priority map that has been explicitly approved by the account manager. **Gate rule:** Propose the groups and the keyword counts *first* and get them approved before generating any keywords. Do not generate a full keyword set against unapproved groups. A second approval gate covers the finished map.

This is not a comprehensive audit. The goal is a strong, defensible foundation the campaign can start on immediately, plus a reserve to expand from over the following months without redoing the research. Resist the urge to be exhaustive.

## Required context document

The account manager completes a keyword context document before this skill runs. It uses the same field names as the content workflow's client context document (so it stays transferable), but a simplified subset. If it is missing or half-filled, flag this before proceeding — most of the judgement below depends on it.

Fields:

- **Key priority areas** — the services, products, or categories the client most wants to grow. These seed the groups.
- **Key audience information** — who the customer is, their knowledge level, how they search.
- **Target geography** — local, regional, or national. This materially changes keyword selection, so it is not optional.
- **Primary commercial goal** — the business target, plus what counts as a conversion (sale, lead, call, enquiry). The conversion type sets how intent is weighted.
- **Key existing pages / URLs** — so groups map to a real home on the site rather than floating free.
- **Key converting pages** — the URLs that already convert, plus their top converting search terms if the client knows them.
- **Exclusions** — services the client does not offer, off-limits terms/topics, and irrelevant territories. Also **competitor brand terms**: the competitor brands and branded terms named here are excluded from targeting and tracking unless explicitly told otherwise. If there's crossover between a brand name and a generic keyword, flag this to the account manager for their insight and final decision. For example, if 'Lincolnshire Pond Plants' is a brand name, this might crossover with a viable keyword such as 'pond plants lincolnshire'.
- **In-house / previously tracked keywords** (optional) — usually supplied as a spreadsheet; see the caveat in Step 3.
- **GA4 export** (optional) — attach if available; the converting-pages field above is enough on its own.

## Workflow

### Step 1: Understand the account

Before touching keyword data, spend two minutes grounding yourself in the client.

Read the context document, then take a light look at the client's actual service and category pages. The purpose is narrow: sense-check the intended groups against how the business really structures itself, and catch mismatches — for example, the context doc names a priority the site barely covers, or the site is organised around something the doc doesn't mention. Surface any mismatch to the account manager.

**Caveat:** do not over-trust the site. A poorly structured site is often *why* the client hired an SEO. The site informs the groups; it does not dictate them.

### Step 2: Decide the mode(s)

This skill looks for two kinds of opportunity. They ask different questions of the data, so decide up front which apply.

- **Decline recovery** — a *trend* signal. Uses two time periods and asks "what did we rank for and lose?" Requires the client to have search history.
- **Striking distance** — a *state* signal. Uses a single current snapshot and asks "what are we close to winning?" Queries whose current average position sits at the bottom of page one (roughly 6–10) or on page two (roughly 11–20), with real impressions behind them. No trend required.

They overlap, and the overlap is often the best material: a query in striking distance *because* it slipped (was position 4, now 9) is both recoverable and high-upside. Flag such queries as qualifying under both rather than forcing them into one bucket.

**Which mode when:**

- New campaign on an established site → **both** (the default at kickoff). Recovery shows what to defend; striking distance shows what to attack.
- Young site with little history → lean on striking distance plus net-new discovery (SEMrush, Keyword Planner). Decline mode has little to work with — GSC holds roughly 16 months of data.
- Rescue engagement (traffic has dropped) → decline leads.
- Growth engagement (stable, wants more) → striking distance leads.
- Re-runs later in the campaign → same mode(s), later date windows, to show movement on the queries flagged at kickoff. This is the tracking story.

### Step 3: Gather and prepare data

Each source has one defined job. Do not blur them.

**Google Search Console** — "what we already have traction on." Usually the highest-ROI and most defensible material.

- Exported manually as CSV (agency GSC access is split across multiple Google accounts, so a single API connection won't cover every client). Ask the account manager for the **comparison view** (current period vs the same period the previous year), which exports both periods in one file — this feeds recovery (two periods) and striking distance (current snapshot) from one download.
- The UI export caps at ~1,000 rows, so sort by impressions before exporting to capture the queries that matter. For unusually large clients, use a Looker Studio export (no row cap, per-property) or the API for that client only.
- For recovery, compute the deltas and classify each declining query — this classification *is* the "high potential" filter:

| Signal | Cause | Action |
|---|---|---|
| Position dropped, impressions steady | Lost ranking on a term still in demand | **Recoverable — this is the gold** |
| Impressions dropped, position steady | Seasonality, fading interest, or traffic now exploring via LLMs | Confirm the decline is real via Keyword Planner data (see below). If the query is **informational-intent** and **part of a cluster** showing the same pattern, flag as **possible LLM/AIO demand migration**, cross-check against the group's tracking prompts (Step 6), and surface to the account manager as a GEO candidate rather than skipping. If commercial/transactional and isolated, still usually skip. |
| Position and impressions steady, clicks down | SERP feature / AI Overview / weak title eating the click | CTR optimisation, not content |

- To avoid mistaking seasonality for decline, compare year-over-year where the history exists, not quarter-over-quarter. For a longer trend window than the trailing 12 months, call `dataforseo_labs_google_historical_keyword_data` (DataForSEO Labs), which holds Google keyword history back to August 2021.

**Google Ads Keyword Planner data** — "demand shape and commercial value." Call `dataforseo:kw_data_google_ads_search_volume` (DataForSEO MCP connector, `KEYWORDS_DATA` module) for every candidate keyword — do not attempt to reach the Google Ads API directly, it requires a manager account, developer token approval, and OAuth setup the team does not need to maintain. Pass `keywords`, `language_code`, and `location_name` (matching the client's target geography from the context doc). It returns, per keyword:

- `search_volume` — average monthly searches
- `monthly_searches` — a 12-month breakdown, used for the seasonality check above
- `competition` / `competition_index` — Google's own low/medium/high rating and 0–100 score. **This is *ad-auction* competition, not SEO difficulty — never use it as a difficulty or achievability signal.**
- `low_top_of_page_bid` / `high_top_of_page_bid` (and `cpc` where available) — used as the commercial-value proxy when conversion data isn't available

**SEMrush (API)** — plugs the two holes GSC and Keyword Planner can't fill. Scope it to two signals only, not a full competitor audit:

- **Keyword difficulty** — the achievability guardrail. For any term the client doesn't already rank for, this is the *only* difficulty signal available, and picking unwinnable terms as primaries is the most common junior mistake.
- **Competitor-gap discovery** — the natural source of net-new terms for growth groups, which are areas the client doesn't yet rank for and where GSC is blind by definition (no impressions = invisible).

If SEMrush isn't connected for a given workspace, fall back to DataForSEO Labs: `dataforseo_labs_bulk_keyword_difficulty` covers the achievability guardrail, and `dataforseo_labs_google_domain_intersection` (client domain vs. competitor domain) covers competitor-gap discovery. Don't skip the achievability check just because SEMrush access is missing — this is the guardrail that prevents unwinnable primaries.

**In-house / previously tracked keywords** — use as a light input only, heavily caveated: clients don't always know what they're doing, so this is never a primary metric. Where the in-house list diverges sharply from what the data suggests, surface the divergence to the account manager rather than silently discarding it — that gap is a useful client conversation.

**Conversion data** — where GA4 or the converting-pages field is available, it beats the ad-bid proxy for judging commercial value. Use it to weight groups; don't block the work if it's absent.

### Step 4: Propose groups and counts — approval gate

Cluster the assembled keyword set into 3–5 candidate primary groups by theme, intent, and likely page type. Score and rank them (see Scoring model), then present to the account manager:

- The proposed groups, each with a one-line rationale.
- The **specific** keyword counts you propose for this account — how many primaries per group (within 5–10) and roughly how many secondaries (within 10–25 per group) — each with a one-line reason grounded in the client's industry, size, and breadth. Propose the numbers; don't default to the maximum. State plainly that this is initial groundwork plus a reserve, not a comprehensive list.

Do not generate the keyword sets until the account manager approves the groups and counts. If they change the groups, revise and re-present.

### Step 5: Build the keyword sets

Two tiers, with **different levels of rigour** — this is what keeps per-group affordable:

**Primary keywords (5–10 per group)** — individually selected. For each, apply the "useful" definition (see Scoring model) and attach a one-line rationale plus tags: intent (informational / commercial / transactional / local), opportunity type (recovery / striking distance / net-new), and volume. A good primary set spans intent and funnel stage; it is not five phrasings of one term. Where a keyword is in striking distance, note the **modelled click upside** — estimated extra monthly clicks if it moved to, say, position 3 (impressions × target-position CTR − current clicks) — which is a far better prioritisation signal than position alone.

**Secondary keywords (10–25 per group)** — a lighter-touch banked reserve. Volume-checked and sorted into the right group, but *not* individually justified. These are the pool the team draws from months into the campaign to expand a group without commissioning fresh research.

In the deliverable, keep the two tiers visually distinct — an active set and a reserve — so nobody starts working the whole reserve at once.

Do not target or track the competitor brand terms named in the context document — they are listed there specifically to be excluded from the research.

### Step 6: Generate AI visibility-tracking prompts (3–6 per group)

The primary purpose of these prompts is **tracking**: the client wants to see how they perform in each group across LLMs and AI Overviews over time. Generate them yourself (you hold the full campaign context); the client's prompt tool is used to *store, version, and re-run* them, not to generate them.

Rules for each prompt:

- **Brand-agnostic** — never name the client. You are testing whether they surface unprompted; naming them defeats the point. Unless the account manager specifically asks you for prompts that include the brand.
- **Phrased like a real user** would ask an LLM — a natural question, not a keyword string. Get a balance between specific, as a user might search, but not so specific that it's unusable. For example, "*I want to see a West End show while I'm in London — how do I choose which musical to watch?*" is good. "*I want to see a West End show while I'm staying near Hyde Park in London this weekend, but I don't know whether to watch the Lion King, Matilda, or Les Mis, which should I do and why*" is too long and hyper-specific, even if some users might cover that much detail.
- **Funnel-spanning within the group** — include an informational question, a commercial "best X", a comparison, and a local one where relevant. Visibility differs sharply by query type.
- **Stable and few (3–6)** — each prompt carries an ongoing cost because it is re-run across models over time, so fix the set and track the same prompts month to month.

Example, for a "solar panel installation" group:

- "What should I look for when choosing a solar panel installer?"
- "Who are the best solar panel installers in [region]?"
- "Is it worth installing solar panels in 2026?"

**Caveat to record for the client:** LLM output is non-deterministic — it varies by session, personalisation, region, and model version. This is a *directional* signal, not rank tracking. Run each prompt several times and across more than one model, and report trends rather than a single snapshot.

**Check the context doc for any AI prompts** the client has previously tracked. Treat these as a light input only — the prompts you generate here are grounded in the fresh campaign context and take priority — but don't silently discard an existing tracked set. If the client has real trend history against specific prompts, preserving them (or explicitly retiring them, visibly) protects continuity the client may already be measuring. Where the existing prompts diverge sharply from what this campaign's groups would produce, flag it to the account manager rather than quietly overwriting.

**Cross-check any GEO/AI-visibility candidates flagged in Step 3 against this group's tracking prompts.** Substantive, on-topic LLM answers support genuine migration — confirm the candidate. Thin or generic answers suggest the topic is simply fading — downgrade it back to skip.

Do **not** generate content-angle prompts here. Those are most useful when a group actually enters the content pipeline, in the SERP context that makes them good — defer them to the content-strategist handoff.

### Step 7: Assemble the map — approval gate and handoff

Assemble the keyword priority map: the 3–5 groups, each with its rationale, its primary set (with rationales and tags), its 3–6 tracking prompts, its secondary reserve, and its **GEO/AI-visibility candidates** (see below), plus any divergence flags raised in Step 3. Present it for approval. Do not treat the campaign foundation as set until the account manager signs off.

**GEO/AI-visibility candidates** — queries flagged in Step 3 as possible LLM/AIO demand migration and confirmed in Step 6. This is a separate, unscored list. Do not run these through the standard rubric (volume will score them low precisely because they're migrating off Google) and do not fold them into the primary/secondary groups. Present them to the account manager as flagged opportunities for a GEO follow-up.

Once approved, the map feeds two downstream places:

- **The content workflow's client context document.** The map populates that document's "Keyword directions" section directly, so it never has to be filled by hand. Map each primary group onto a **priority topic cluster** — group name → cluster name, the group's *primary* keywords → example keywords, the group's dominant intent → primary intent, and its score band (high / medium) → strategic priority. The **Terms and topics to avoid** section carries across as-is: services not offered, off-limits terms/topics, irrelevant territories, and competitor brand terms (the brands the account manager named to exclude). The secondary reserve, the tracking prompts, and the GEO/AI-visibility candidates do **not** go into this section — the reserve is a later-expansion pool, the prompts are for measurement, and the GEO candidates are account-manager judgement calls, not settled keyword direction.

- **The content-strategist skill.** Each primary group becomes an entry point — content-strategist consumes a group's topic and primary keyword as its starting request. The tracking prompts stay live for ongoing measurement; they do not pass into content-strategist. The GEO/AI-visibility candidates likewise do not pass into content-strategist — they are not a keyword-targeting decision, and stay with the account manager pending a GEO follow-up.

## Scoring model

Use a single, transparent rubric so different people reach roughly the same conclusions. Score each candidate group — and each candidate primary keyword — 1–5 on five dimensions:

- **Commercial value / business alignment** — fit to the client's priority areas and conversion goal (from the context doc and any conversion data).
- **Search demand** — volume from `dataforseo:kw_data_google_ads_search_volume`.
- **Achievability** — SEMrush difficulty (or the DataForSEO Labs fallback in Step 3), softened where GSC shows the client is already close (striking distance).
- **Existing momentum** — does GSC show an existing foothold to build on?
- **Content gap / effort** — how much content already exists versus what's needed.

Weight **commercial value** and **achievability** highest. Sum, rank, and take the top 3–5 groups.

**Definition of "useful", in priority order** — apply this whenever choosing between keywords so that volume never dominates:

1. Commercial fit to the group.
2. Intent match.
3. Achievability for a client of this size.
4. Volume (a supporting signal, not the deciding one).

## What good and bad look like

Anti-examples align judgement faster than more rules do. Using a solar installer as the running example:

**A good primary set** for a "solar panel installation" group — mixed intent, mapped to a real service, a winnable spread:

- "solar panel installation" — core commercial head term; the group's anchor.
- "solar panel installation cost" — high-intent, decision-stage, strongly commercial.
- "solar panel installers [region]" — local commercial; the terms that actually convert.
- "cost of solar panels for a 3 bed house" — specific long-tail, decision-stage.
- "are solar panels worth it" — consideration-stage, high volume, feeds the top of the funnel.

**Bad sets, and why:**

- *Five phrasings of one term* — "solar panels", "solar panel", "solar pv", "pv panels", "solar photovoltaic". No intent spread, no funnel coverage. One keyword wearing five hats.
- *Too broad / wrong intent as a primary* — "solar energy", "renewable energy", "how does solar work". Informational giants owned by national publishers. Fine as awareness-stage secondaries; wrong as commercial primaries.
- *Vanity / volume-chasing* — picking "solar" because the volume number is huge. Unwinnable, ambiguous intent, no commercial fit.
- *Out of scope* — "solar battery repair" when the client only installs. Violates the exclusions list.

## Principles

- Anchor on commercial value before volume. Big volume that doesn't convert is the classic trap.
- Every group must earn its place: it should map to something the business actually wants to grow, and to a real or plannable home on the site.
- Don't chase decline that is really seasonality, and don't treat a CTR problem as a content opportunity.
- Difficulty is a guardrail, not an afterthought — never propose unwinnable terms as primaries.
- Rigour is tiered on purpose: primaries are justified individually; secondaries are a banked reserve, not a second audit.
- Prefer a defensible, startable foundation over a comprehensive one. The reserve exists so the campaign can expand later without fresh research.

## Clarifying questions

Ask only where genuinely needed to produce a strong map, and keep questions strategic rather than bureaucratic. Do not ask what the context document already answers.

Useful areas to clarify if not established:

- Whether this is a rescue or a growth engagement (it sets the default mode).
- Target geography and conversion goal, if the context doc left them blank.
- Whether the client's prompt tool actually runs prompts against LLMs and monitors AI Overviews, or only stores them.
- Any priority area that the site structure appears to contradict.

### Known gaps / revisit

- **GSC Generative AI report → Step 3.** Not yet wired into the impressions-dropped-position-steady classification, but could in the future provide a data-led way to check if a term has shifted from organic to AIO visibility. Revisit once the report moves out of beta and includes query-level data (impressions-only, beta rollout as of June 2026 at time of writing).
