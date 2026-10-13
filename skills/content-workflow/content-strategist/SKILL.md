---
name: content-strategist
description: Use this skill for SERP analysis, content angle development, content briefs, and heading structure planning. This skill covers everything before drafting begins. It does not write content. Invoke this skill when the user asks for a SERP analysis, a content plan, a content brief, or a recommended article structure.
---

# Content Strategist

*Version 1.4, October 2026*

**Reference files:** this skill comes with `references/content-standards.md` and `references/content-qa-standard.md`. Use the versions in the client's Claude project if it has them, otherwise use these.


## Scope

This skill covers the planning phase of the content workflow only. It does not draft articles, edit content, or review published work. Its job is to establish the strategic foundation that all subsequent work builds on.

**Entry condition:** A topic, keyword, or content request from the user.
**Exit condition:** A content brief that has been explicitly approved by the user.
**Gate rule:** Do not allow the workflow to move to the content-writer skill until the user has confirmed the brief. If the user requests a draft before approving a brief, flag this and return to the brief stage.

---

## Pre-planning check

Before any planning begins, confirm two things:

1. **Client context document:** Has a client context document been established for this client? If not, flag this to the user. Planning without a client context document risks misaligned tone, audience assumptions, and strategic direction.

2. **Example-analyser output:** Has the example-analyser skill been run on this client's content? If not, flag this. Tone and editorial alignment depend on it. Proceed if the user confirms examples are unavailable, but note the limitation.

---

## Workflow

### Step 0: What the client already ranks for

If the Search Console connection is on and the Client AI Context has a GSC property, follow `references/data-method.md` and check the last 3 months for the topic:
- Pages already getting impressions or clicks for the main and related queries. If one exists, recommend improving it rather than writing a competing page.
- Queries with plenty of impressions but few clicks, which point to gaps the new piece can answer.

Summarise in three or four lines, with the property and date range. If the connection isn't on, say so in one line and carry on.

### Step 1: SERP and intent analysis

Before proposing any structure, analyse the topic from a search intent perspective.

**Identify:**
- Dominant search intent (informational, commercial, transactional, navigational, mixed)
- Funnel stage (awareness, consideration, decision)
- Audience knowledge level (expert, informed professional, general consumer)
- What users are actually trying to achieve when they search this term
- Whether this is a stable or event-driven search demand

**Analyse the competitive SERP:**
- What types of pages currently rank (OEM, installer, aggregator, editorial, government)?
- What structural patterns do ranking pages share?
- What questions do they answer well?
- What do they consistently fail to address?
- Where is there a genuine gap between what users need and what currently ranks?

Also note how similar the ranking pages are to each other. If they all share one template, that is a gap: a structure built around what this reader needs will stand out.

Never blindly imitate competitor structures. Understand why they rank, then identify where they are weak and where a genuinely better answer exists.

**Output:** A plain-language SERP summary covering intent, dominant patterns, and the identified opportunity. Present this before proposing any structure.

---

### Step 2: Strategic angle

Based on the SERP analysis, propose a single clear editorial angle for the article.

The angle is not a topic. It is the specific perspective, emphasis, or framing that makes this article meaningfully different from what already ranks. A strong angle answers the question: why does this article need to exist, and what does it offer that competitors do not?

**The angle should:**
- Emerge directly from the competitive gap identified in the SERP analysis
- Align with the client's positioning and differentiators (from the client context document)
- Serve the audience's actual need, not just the keyword
- Feel editorial and intentional, not manufactured for search

**Present the angle as a single statement**, then explain the reasoning. Ask the user to confirm before proceeding to structure.

---

### Step 3: Content brief

Once the angle is confirmed, produce a full content brief. The brief is the document a writer uses to produce the draft. It must be specific enough that the draft could be written without further clarification.

**Brief structure:**

**Page details**
- Working title (H1 candidate)
- Primary keyword
- Secondary and supporting keywords
- Search intent
- Funnel stage
- Target audience
- Geographic market

**Strategic context**
- Why this article (the SERP gap and opportunity in plain language)
- The competitive gap (what competitors do and where they fall short)
- The editorial angle (the differentiated perspective this article takes)

**What makes this ours (distinctiveness plan)**

This section is required in every brief. Google now judges content on effort, originality, skill and accuracy, and generic pages that add nothing new are the main risk. Distinctiveness has to be planned here: it cannot be added at QA.

- **Content type and requirement:** blogs, guides and articles need at least one distinctive element; category, service and product pages should include one where possible (the bar is specific, accurate product or service detail); news and short updates are optional.
- **Planned distinctive element(s):** choose from the menu below and say exactly what it is and which section it belongs in.
  - Client insight: one specific answer from the client (see the client question).
  - Evidence from the client's own site: case studies, product specs, reviews, team expertise or photography they already publish, quoted and linked.
  - Original analysis: a comparison table, a decision guide ("which option suits whom"), a worked example or a cost breakdown.
  - Real questions answered: what people actually ask (SEOmonitor data, People Also Ask, forums), answered directly.
  - A visual made for this piece: a diagram, process flow, annotated screenshot, checklist or simple calculator.
  - Market and sector specifics for the client's audience: named regulations, standards and bodies, local pricing, seasons and examples.
  - Named expertise: a "reviewed by" expert for higher-stakes topics.
- **One client question:** a single, specific question the user can send the client now, so the answer can arrive before drafting. Examples: "What is the most common mistake your customers make with this?", "What do customers ask you most often about this?", "Is there a real job or example that shows this well?". One line from the client is worth more than a full quote that never arrives.
- **Placeholder decision (required):** say plainly whether the draft will contain placeholders. Placeholders are gaps the writer leaves because something is not available yet: [CLIENT INSIGHT], [DATA NEEDED], [VISUAL] or [LINK NEEDED]. They are easy to miss once a draft looks finished, so they are decided here, on purpose, not discovered later. Choose one:
  - **No placeholders (recommended default):** the distinctive element uses only what is available now (the client's own site, original analysis, real questions, UK specifics). Clients rarely send input in time, so prefer an element that needs nothing from them over a placeholder that may never be filled.
  - **Placeholders approved:** list each one with what it is, which section it sits in, who supplies it (client, designer, account lead, writer) and when it is needed. Send the client question now so the answer can arrive before drafting.
- **Visual brief (if a visual is planned):** what it shows, the data or steps it needs, and where it sits.
- **Author and reviewer:** who the byline is (a real person or an honest team byline) and whether an expert reviewer is needed. Never plan an invented persona.
- **Schema plan:** Article or BlogPosting with the real author as a minimum, plus any type that genuinely applies (Organization, Person, BreadcrumbList, Product, VideoObject). Do not plan FAQ or HowTo schema as a ranking or rich result tactic: FAQ rich results are limited to well-known government and health sites and HowTo rich results were removed.

**Audience considerations**
- Motivations (what the reader is trying to achieve)
- Anxieties (what they are worried about or uncertain of)
- Assumed knowledge (what they already understand — do not over-explain this)
- Gaps (what they need to learn or have clarified)

**Recommended structure**

For each heading:
- Heading text with tag label ([H1], [H2], [H3])
- Purpose (what this section achieves)
- What it should cover (key points, not a script)
- Considerations (tone, depth, what to avoid)
- EEAT opportunities (where specificity, citations, or operational detail strengthen credibility)
- Readability notes (where bullets, tables, or bold would support scanning)

**Internal linking plan**
- Which existing pages or articles this should link to
- Where in the content those links naturally belong
- Placeholder links to be activated before publication
- The most important internal link should sit in the first third of the article, with anchor text that says where it goes

**Commercial integration notes**
- Where, if at all, the client's services or expertise should be referenced
- How to frame commercial relevance without disrupting informational flow

**Tone and style notes**
- Register (expert peer, informed guide, accessible explainer)
- Specific tone guidance for this article based on audience and intent
- Any client-specific tone notes from example-analyser output

**Content parameters**
- Target word count range
- Use of tables (yes/no, where)
- Use of bullets (yes/no, where)
- Proposed title tag (under 60 characters)
- Proposed meta description (under 155 characters)

---

### Step 4: Approval gate

Present the full brief to the user. A brief is not complete without the "What makes this ours" section.

Open the brief summary with the placeholder decision in one plain line, so it cannot be missed. For example:

```
HEADS UP: this draft will contain 2 placeholders that must be filled before publishing:
[CLIENT INSIGHT] in "Common mistakes" (client, by 20 October) and [VISUAL] in "The process" (designer).
```

or

```
No placeholders: everything this draft needs is available now.
```

Approving the brief means approving those placeholders. Ask the user to confirm they are happy for the draft to contain them, or to switch to an element that needs no input. Do not proceed to drafting until the user explicitly approves. If the user requests changes, revise the brief and re-present before proceeding.

Once approved, the brief passes to the content-writer skill.

---

## Structural principles

Every section in a content plan must justify its existence. Apply these tests to every heading proposed:

- Does this section answer a genuine user question or need?
- Is it distinct from adjacent sections, with no meaningful overlap?
- Does it advance the article's logical progression?
- Would removing it leave the user worse off?

If the answer to any of these is no, remove or merge the section.

**Avoid:**
- "Everything You Need To Know" headings
- "Benefits of X" sections unless the structure genuinely requires it and competitors do not do it better
- "Types of X" unless classification is the primary user need
- Sections added to increase perceived comprehensiveness
- Near-duplicate headings that cover the same ground twice
- Reusing the same skeleton as other recent briefs for this client (for example "What is X, Benefits, How to, FAQs" every time). Structural sameness across many pages is a signal of mass-produced content. Each structure should follow what this topic and reader need.

---

## EEAT integration in planning

The brief should actively identify where EEAT signals can be built into the content. These are not afterthoughts — they are planned into the structure.

**Where EEAT is strongest:**
- Sections covering operational detail that only a practitioner would know
- Sections referencing named regulatory frameworks, compliance requirements, or official schemes
- Sections that use specific figures, intervals, or thresholds rather than generalities
- Sections where competitor content is generic and this article can be specific

**Flag in the brief:**
- Any claim or figure that will need a citation
- Any regulatory programme or official scheme that must be linked
- Any section where an example, case, or scenario would strengthen credibility

---

## Clarifying questions

Ask clarifying questions only where genuinely needed to produce a strong brief. Questions should feel strategic, not bureaucratic.

Useful areas to clarify if not established by the client context document:
- Target audience and awareness level
- Funnel stage priority
- Commercial intent (informational only, or should the article build toward a service)
- Internal linking priorities
- Any topics or angles to avoid

Do not ask questions the client context document or project instructions already answer.
