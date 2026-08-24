# Keyword Research

Runs the foundational keyword research phase at the start of an SEO campaign, producing a **keyword priority map**: 3–5 primary groups, each with a focused set of primary keywords, AI visibility-tracking prompts, and a banked reserve of secondary keywords for later expansion.

This is start-of-campaign strategic groundwork, not per-article keyword selection — that belongs to the content-strategist skill, downstream of this one.

---

## What it produces

A keyword priority map with, per group:

- **A rationale** — why the group earns a place, tied to the client's priority areas and conversion goal
- **Primary keywords (5–10)** — individually selected and scored, each tagged with intent, opportunity type (recovery / striking distance / net-new), and volume
- **AI visibility-tracking prompts (3–6)** — brand-agnostic, natural-language prompts for tracking LLM/AI Overview visibility over time
- **Secondary keywords (10–25)** — a lighter-touch banked reserve, volume-checked but not individually justified
- **GEO/AI-visibility candidates** — queries showing signs of migrating from organic search to LLM/AI Overview usage, flagged separately for a GEO follow-up

---

## How to trigger it in Claude

Just describe what you want. Examples that will trigger this skill:

> "Let's start keyword research for [client]"

> "KWR for the new campaign"

> "I need keyword priority groups for this account"

> "What keywords should we target for this client?"

> "Run a declining-keyword analysis"

You do not need to describe the full workflow — any request to begin keyword research, mapping, or strategy for a campaign will trigger it.

---

## Before you start

The skill needs a completed **keyword context document** first: priority areas, audience, target geography, conversion goal, existing/converting pages, and exclusions (including competitor brand terms). If it's missing or incomplete, Claude will flag this before proceeding.

It also draws on live data via the DataForSEO MCP connector (search volume, keyword difficulty, competitor-gap discovery) and Google Search Console exports (comparison view, current vs. same period last year). SEMrush is used for difficulty and competitor-gap discovery where connected, with a DataForSEO Labs fallback if not.

---

## Approval gates

This skill has two built-in checkpoints, by design:

1. **Groups and counts** — Claude proposes the candidate groups and specific keyword counts first. It will not generate a full keyword set until these are approved.
2. **The finished map** — the assembled map (groups, primaries, prompts, reserve, GEO candidates) is presented for sign-off before it's treated as the campaign foundation.

---

## Handoff

Once approved, the map feeds two downstream places:

- **The content workflow's client context document** — each primary group maps onto a priority topic cluster, populating the "Keyword directions" section directly.
- **The content-strategist skill** — each primary group becomes an entry point for content planning, using the group's topic and primary keyword as the starting request.

The tracking prompts and GEO candidates stay with the account manager for ongoing measurement and GEO follow-up; they don't pass into content-strategist.
