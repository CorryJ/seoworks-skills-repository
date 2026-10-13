---
name: "content-editor"
description: "Use this skill to refine and elevate a completed content draft. This skill edits. It does not plan content, produce briefs, or conduct final QA review. Invoke after a full draft exists and before the content-reviewer skill runs."
---

# Content Editor

*Version 1.3, October 2026*

**Reference files:** this skill comes with `references/content-standards.md` and `references/content-qa-standard.md`. Use the versions in the client's Claude project if it has them, otherwise use these.


## Scope

This skill refines drafted content so it reads as the work of a knowledgeable, experienced human writer — not as AI-assembled text. It does not rewrite content unnecessarily, restructure approved briefs, or conduct publication-readiness QA. Those belong to the content-writer and content-reviewer skills respectively.

**Entry condition:** A complete content draft.
**Exit condition:** A refined draft ready for the content-reviewer skill.
**Gate rule:** Do not apply this skill to a brief, a plan, or an incomplete draft. If no full draft exists, flag this and return to the content-writer skill.

---

## Primary objective

The goal is not to make content sound more "professional." The goal is to make content feel more human, more natural, more intentional, and less like it was assembled algorithmically.

Edited content should sound like the work of a skilled practitioner who writes clearly — not a marketing AI, not a corporate copywriter, not a generic SEO template.

**Edit with restraint.** Do not rewrite for stylistic preference. Preserve the writer's meaning and the brief's structure. Refine what weakens the content; leave what works alone.

---

## Editorial checks — run in this order

### 1. Em dash check

Search the entire draft for em dashes (—). Remove every one. Replace with a colon, a full stop, a comma, or a rewritten sentence as appropriate to context. This is a non-negotiable check that runs first, before any other editing begins.

### 2. Forbidden phrase check

Scan for every phrase on the forbidden list in the Content Standards document. Remove or rewrite each one. Pay particular attention to paragraph-opener transitions ("Additionally," "Furthermore," "Moreover") and closing summaries ("In conclusion," "To summarise").

### 2a. Overused filler phrase check

Search the whole draft for the following and rewrite every hit. These are recurring habits flagged by the team, and each one makes copy repetitive, patronising, or too casual for professional clients.

- **"matters" / "matter" used to signal importance** ("this distinction matters because...", "these steps matter to ensure..."). Replace with a direct statement of the consequence: "That distinction drives almost every document requirement that follows." Literal uses of "matter" (a legal matter, a matter of days) stay.
- **"actually"** ("what do these terms actually mean", "how each one actually works"). Delete it. Leave it only inside direct quotations.
- **"This means" / "That means" / "which means" / "means that"**, including malformed versions such as "means to matching". Where these are used to chain follow-up statements, restructure so the consequence is carried by a verb or a joined sentence. Keep "means" only in genuine definitions. Allow no more than two "This means"-style openers in the whole article and never two in the same section.
- **Repeated closers.** If consecutive paragraphs end with the same connective or sentence template, vary at least one.

When rewriting, do not swap in a near-synonym that carries the same habit ("this is significant because", "this essentially means"). Remove the signposting and state the point.

### 2b. Brief bleed-through check

Compare the draft against the approved brief. Remove or rewrite any sentence that exposes the brief's instructions, angle, or competitive rationale to the reader. Typical signs:

- References to what other guides, competitors, or "most articles" leave out, squeeze into a line, or get wrong ("one door that hardly ever makes the list", "a bit longer on the part most guides skip").
- The article announcing its own differentiation or structure ("here's what really separates...", "unlike other guides...", "so we'll spend longer on...").
- Wording lifted from the brief's purpose, considerations, or tone notes.

The fix is to state the underlying point directly to the reader, and keep the depth the brief asked for without announcing it. If removing a sentence leaves a gap in the logic, rewrite it as a plain statement of the subject. Do not change the structure or angle themselves.

### 3. Heading tag check

Confirm every heading carries its correct tag label ([H1], [H2], [H3]). If any heading is missing its tag, add it. If any tag label appears without correct heading formatting, correct it.

### 4. AI cadence patterns — identify and rewrite

These are the hardest patterns to detect and the most damaging to credibility with professional audiences.

**Stacked short declaratives.** Three or more short sentences building toward a conclusion, each landing a point. The pattern exists to make the reader feel the weight of something rather than understand it. Rewrite as connected, building explanation.

Problematic: "Maintenance gets deferred. Efficiency drops. The asset degrades."
Better: "Deferred maintenance degrades efficiency progressively, not dramatically at first, but steadily and expensively over time."

**Rhetorical urgency performed at the reader.** Sentences that tell a specialist reader that a problem they already understand is important. These sentences exist to perform expertise rather than demonstrate it. Remove them.

**Overly symmetrical paragraph structure.** When every paragraph follows the same shape — claim, explanation, example, summary — the content reads as templated. Vary the internal structure of paragraphs so the rhythm feels natural rather than mechanical.

**Repetitive sentence openings.** If three or more consecutive sentences open with the same word or grammatical construction, vary them.

**Generic transitions used as paragraph openers.** "Additionally," "Furthermore," "Moreover," "It's important to note" — rewrite so the transition emerges from the logic of the content rather than being announced.

### 5. Sentence rhythm

Read the draft aloud (or simulate reading aloud). Sentence length should vary naturally. Look for:

- Extended runs of long, complex sentences — break some up
- Extended runs of short sentences — some may need to be combined or elaborated
- Paragraphs where every sentence is approximately the same length — vary them
- Monotonous cadence — the reader should not be able to predict the rhythm of the next sentence

### 6. Paragraph discipline

Every paragraph should carry one primary idea. If a paragraph is running to six or more sentences and covering more than one idea, split it. If a paragraph is only one sentence and it cannot justify that status, merge it with an adjacent paragraph or expand it.

### 7. Specificity audit

Scan for vague language that could be made more specific without adding length:

- "regularly" — can this be given an interval?
- "significant" — can this be quantified?
- "many sites" — can this be characterised more precisely?
- "various factors" — can the factors be named?
- "industry best practice" — can a named standard or framework be cited?

Replace vague language with specific language where doing so adds credibility without adding bloat.

### 8. Readability and scannability

Apply the readability rules from the Content Standards document:

- Confirm bullets are only used for genuinely discrete, parallel items
- Confirm tables are used for comparative or structured data, not prose reformatted as rows
- Confirm bold is used for key terms and lead-ins, not for decorative emphasis
- Confirm no major section is entirely solid prose where visual anchors would help a scanner

If a section contains four or more discrete items in prose that would benefit from bullets, convert them. If a section compares two or more things across consistent attributes, consider whether a table would serve the reader better.

### 9. EEAT check

Confirm:
- All named regulatory frameworks and official schemes are linked
- All figures (efficiency percentages, performance claims, operational intervals) are attributed or sourced
- No unsupported superlatives remain
- [LINK NEEDED] placeholders are present wherever a citation is required but the URL was not available at drafting stage

If any of these are missing, add them. If the correct source is not known, insert [LINK NEEDED] rather than leaving the claim unsupported.

### 10. Meta elements

Confirm the draft includes a proposed title tag and meta description. If either is missing, add them. Title tag under 60 characters. Meta description under 155 characters, reading as a genuine summary rather than a keyword-stuffed teaser.

### 11. Distinctiveness and placement

Confirm:
- The distinctive element planned in the brief is still present after editing. Do not cut or flatten it to make the article smoother: it is the most valuable part.
- Nothing in the draft looks invented: any client quote, statistic, case study, review or credential that cannot be traced to a source or the client is replaced with a placeholder and flagged.
- The primary keyword appears in the H1, the first 100 words and at least one H2, and secondary keywords read naturally.
- The most important internal link sits in the first third of the article, with descriptive anchor text (never "click here" or "read more").
- Alt text and any schema in the draft describe what is actually on the page.
- Every placeholder in the body is listed in the draft header, and the count matches. Never remove or soften a placeholder silently, and never fill one with invented content. If one can now be filled from a real source (a link you found, a fact on the client's site), fill it and update the list.

---

## What not to do

**Do not rewrite unnecessarily.** If a passage is clear, specific, and reads naturally, leave it alone. Editing is not polishing — it is removing what weakens the content.

**Do not flatten voice.** A distinctive observation or an unexpected construction is usually worth keeping, even if it could be made more conventional. The goal is human credibility, and humans write idiosyncratically.

**Do not make content more corporate.** Adding formality, hedging language, or institutional phrasing makes content sound less credible to professional audiences, not more. Resist the impulse.

**Do not over-polish.** Content that is too smooth, too consistent, and too uniform reads as AI-generated even when it is not. Some variation and roughness is natural and useful.

**Do not restructure the article.** If the structure approved in the brief is wrong, that is a conversation to have with the user — not a silent change to make during editing. Flag structural concerns separately.

---

## Output format

Deliver the edited draft in the same format as the incoming draft, with all heading tags intact, all EEAT elements present, and all forbidden constructions removed. Where significant changes have been made to a section, note them briefly at the end of the draft so the user understands what changed and why.