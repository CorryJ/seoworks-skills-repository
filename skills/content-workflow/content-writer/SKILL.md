---
name: "content-writer"
description: "Use this skill to draft SEO content after a content brief has been approved. This skill writes. It does not plan, analyse SERPs, or review content. Invoke only when an approved brief exists in the conversation."
---

# Content Writer

*Version 1.3, October 2026*

**Reference files:** this skill comes with `references/content-standards.md` and `references/content-qa-standard.md`. Use the versions in the client's Claude project if it has them, otherwise use these.


## Scope

This skill drafts content. It does not conduct SERP analysis, produce briefs, or review finished work. Those belong to the content-strategist and content-reviewer skills respectively.

**Entry condition:** An approved content brief.
**Exit condition:** A complete draft ready for the content-editor skill.
**Gate rule:** If no approved brief exists in the conversation, do not begin drafting. Return to the content-strategist skill and flag this to the user.

---

## Pre-draft check

Before writing a single word, confirm three things:

1. **Approved brief exists:** Is there an approved content brief in the conversation? If not, stop and flag.

2. **Example-analyser output:** Has the example-analyser skill been run on this client's content? If yes, apply the extracted tone patterns, editorial register, and stylistic behaviours throughout the draft. If no output exists, flag this before proceeding. Do not invent a tone — ask the user for client content examples.

3. **Distinctiveness plan:** Does the brief's "What makes this ours" section name the distinctive element(s), the client question, the author and the schema plan? If the section is missing, flag it and return to the content-strategist skill. If the client has answered the client question, use their answer.

4. **Content Standards:** The Content Standards document governs this draft. The rules within it — em dash prohibition, heading tags, forbidden phrases, EEAT requirements, readability standards — apply from the first word. Do not produce a draft that violates them and rely on the editor to catch the errors.

---

## Drafting principles

### Write from the brief, not from convention

The brief defines the angle, the structure, and the section-level purpose. Follow it. Do not add sections the brief does not include because they seem logical or comprehensive. Do not remove sections the brief includes because they seem minor. If something in the brief needs adjusting mid-draft, flag it rather than silently changing direction.

### Every sentence must earn its place

Do not write to fill space. Every sentence should either advance the reader's understanding, provide a specific detail that adds credibility, or transition the reader logically to what follows. If a sentence does none of these things, remove it.

### Specificity over generality, always

Concrete numbers, named frameworks, accurate terminology, and realistic operational detail carry more credibility than general statements. "Typically every 1,000 to 2,000 running hours" is always better than "regularly." "The jacket cooling water, exhaust gases, and intercoolers" is always better than "various heat sources."

### The brief is instruction, not copy

Everything in the brief is direction for the writer. None of it is text for the reader. The competitive gap, the editorial angle, the SERP analysis, the "why this article" rationale, and any tone or "what to avoid" notes must shape the draft invisibly.

- Never refer to what competitors, other guides, or "most articles" do or fail to do. Lines such as "one door that hardly ever makes the list" or "a bit longer on the part most guides squeeze into a single line" are the brief's angle showing through. Just cover the point properly and let the depth speak for itself.
- Never announce the angle or the article's structure as a point of difference ("here's what really separates...", "unlike other guides...", "we'll spend longer on...").
- Never echo brief wording, section purposes, or instructions back as sentences in the copy.
- Test each introduction and section opener: if the sentence only makes sense to someone who has read the brief, or is describing the article rather than informing the reader, rewrite it as a direct statement of the subject.

### Demonstrate expertise — do not perform it

Expertise shows in specificity and operational detail, not in rhetorical authority signals. Do not write sentences designed to convince the reader that the topic matters. Write sentences that advance their understanding of it.

---

## Distinctive elements

Build the distinctive element(s) the brief plans. They are the part of the article only this client, or this team, could have published.

- **Original analysis:** build the comparison table, decision guide, worked example or cost breakdown properly, with real criteria and figures, not a decorative table that restates the prose.
- **Real questions:** answer the questions in the brief in the reader's words, directly and specifically.
- **Client site evidence:** quote and link the client's own published case studies, specs or reviews accurately.
- **Visuals:** where a visual is planned, write it out as structured content the designer can use (the steps, labels and data), marked [VISUAL: what it shows].

**Never fabricate.** Do not invent client quotes, opinions, data, case studies, reviews, results, credentials or author details. Where the brief needs client input that has not arrived, insert a clear placeholder instead, for example:

```
[CLIENT INSIGHT: ask what the most common mistake customers make is]
[DATA NEEDED: average lifespan from the client's own figures]
[VISUAL: five-step process diagram, steps listed below]
```

Placeholders are better than plausible inventions. A fabricated quote or statistic is a trust failure that QA may not catch.

**Only use the placeholders the brief approved.** Check the brief's placeholder decision before drafting:
- If the brief says no placeholders, write without them. Where information is missing, build the point from what is available (the client's site, sources you can link) or leave the point out. Never invent to fill the gap.
- If a new gap appears that the brief did not plan for, you may add a placeholder, but mark it UNPLANNED in the draft header so the user sees it straight away.
- Put every placeholder in bold on its own line, so nobody can publish past it: **[CLIENT INSIGHT: ...]**.

---

## Tone and register

Tone is set by the brief, the client context document, and the example-analyser output. Apply all three. When they conflict, the example-analyser output takes precedence on tone; the brief takes precedence on structure and angle.

**For specialist and professional audiences:**
- Write as a peer with operational knowledge, not as someone explaining the industry from the outside
- Assume the reader already understands the stakes — do not perform urgency at them
- Earn credibility through specificity, not through rhetorical structure
- Sentences should build understanding, not build tension

**Test for every sentence:** Is this sentence trying to make the reader feel something, or understand something? If it is trying to make them feel something, rewrite it so it makes them understand something instead.

**For general consumer audiences:**
- Prioritise clarity and accessibility over operational depth
- Analogies and comparisons help — use them
- Some persuasive warmth is appropriate, but never at the expense of accuracy

---

## Structural execution

### Heading tags

Every heading must carry its tag label. No exceptions.

```
[H1] Article Title
[H2] Main Section
[H3] Sub-section
```

### Introductions

Do not open with:
- A broad industry statement ("The energy sector is changing rapidly...")
- A vague observation that could apply to anything
- An unnecessary definition of the topic
- Generic "importance" framing ("Understanding X has never been more important...")

Open with the concept itself. Establish relevance quickly. Frame the article clearly. Move into the content without throat-clearing.

### Paragraphs

One primary idea per paragraph. Paragraphs should ideally be 3 to 4 sentences. If a paragraph is running to 6 or more sentences and covering more than one idea, split it.

### Bullets and tables

Apply the readability rules from the Content Standards document:

**Use bullets** when content consists of discrete, parallel items of roughly equal weight that do not flow naturally as prose. Lead-ins for bullet points should use bold text followed by a colon, not an em dash.

**Use tables** for comparative or tiered structured data: technology comparisons, service tiers, maintenance schedules, pricing structures. Every table needs a clear header row and meaningful column labels.

**Use bold** to mark key terms, lead-ins, and critical figures where a scanner would benefit from a visual anchor. Do not bold whole sentences.

### Transitions

Transitions should emerge from the logic of the content. Do not use mechanical transition words ("Additionally," "Furthermore," "Moreover") as paragraph openers. Do not use "In conclusion" or "To summarise" as section closers.

---

## EEAT requirements in drafting

These apply at the point of writing, not as an afterthought for the editor to fix.

**Link at the point of writing:** Any named regulatory programme, government scheme, official standard, or industry body must be linked inline as the draft is produced. Do not leave this for later. If the correct URL is not known, insert a [LINK NEEDED] placeholder — do not omit the link entirely.

**Anchor all figures:** Efficiency percentages, cost savings claims, operational intervals, and similar figures must be sourced or attributed. If a figure comes from a cited source, link it. If it is industry-standard knowledge, state it as such and still link where possible.

**No unsupported superlatives:** "Most," "best," "highest," "leading," "unrivalled" must be removed or sourced. If the claim cannot be evidenced, rewrite it.

---

## Forbidden constructions

These are enforced here, at the point of writing — not left to the editor.

**Em dashes (—):** Forbidden entirely. Replace with a colon, a full stop, a comma, or a rewritten sentence. Not negotiable.

**Stacked declarative sentences:** Three or more short sentences building to a conclusion, each designed to land emotional weight. This pattern signals marketing copy to professional audiences. Rewrite as continuous, building explanation.

**Rhetorical urgency:** Sentences that tell a specialist reader that something they already know matters. Remove them.

**Forbidden phrases:** See Content Standards document. Do not use any phrase on the forbidden list regardless of context.

### Overused filler constructions

Team feedback shows these recur in drafts and make copy repetitive, patronising, or too casual for professional clients. Treat them as forbidden unless a specific exception below applies.

- **"matters" / "matter" used to signal importance** ("this distinction matters because...", "these steps matter to ensure..."). Do not tell the reader something is important. State the consequence directly. Instead of "That distinction matters because it drives every document requirement," write "That distinction drives almost every document requirement that follows." Literal uses ("the matter was referred to...") are fine.
- **"actually"** ("what do these terms actually mean", "how each one actually works", "actually requires"). Delete it. It adds no information and can read as talking down to the reader. It is only acceptable inside a direct quotation.
- **"This means" / "That means" / "which means" / "means that"** as the default way to draw a consequence, including the mangled "means to matching..." form. When these open consecutive follow-up sentences, every explanation sounds identical and the tone turns twee for professional audiences. Restructure so the consequence is carried by the sentence itself, using a verb ("This raises the cost of...", "The result is...") or a joined sentence. Use "means" only in genuine definitions ("A dual citizen holds two nationalities; a second passport is a travel document"). Never use "This means" to open two sentences within the same section, and no more than twice in a whole article.
- **Same-shape consequence sentences.** More broadly, do not repeat any one connective or sentence template as the standard way to close a point. If two paragraphs in a row end with the same construction, change one.

Before delivering, search the draft for "matter", "actually" and "means" and rewrite every hit that falls under the rules above.

---

## Draft output format

Deliver the draft in the following format:

```
Title tag: [proposed title tag, under 60 characters]
Meta description: [proposed meta description, under 155 characters]
Primary keyword: [primary keyword]
Secondary keywords: [secondary keywords]
Word count: [approximate]
Content type: [blog / guide / category page / service page / product page / news]
Distinctive element(s): [what, and which section]
Author: [byline] | Reviewed by: [name, or none]
Schema plan: [types]
PLACEHOLDERS TO FILL BEFORE PUBLISHING: [number, or "None"]
- [type] in "[section heading]" | supplied by: [who] | [planned in brief, or UNPLANNED]

---

[H1] Article Title

[Body of draft]
```

Every heading carries its tag. Every internal link is either active or marked [LINK NEEDED]. Every regulatory reference is linked or marked [LINK NEEDED]. Title tag and meta description are present and within character limits. No brief language, competitor comparison, or angle announcement appears in the copy, and the overused-filler search ("matter", "actually", "means") has been run.

The primary keyword appears in the H1, the first 100 words and at least one H2. The planned distinctive element is present (or marked with a placeholder the brief approved) and nothing has been invented to fill a gap. The placeholder count in the header matches the placeholders in the body.

Do not deliver a draft without all of these elements in place.