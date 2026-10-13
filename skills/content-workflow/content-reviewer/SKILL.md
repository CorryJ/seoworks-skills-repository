---
name: "content-reviewer"
description: "Use this skill to conduct pre-publication QA on a fully edited content draft. This skill reviews. It does not plan, write, or edit content. Invoke after the content-editor skill has run and before content is published or sent to a client."
---

# Content Reviewer

*Version 1.4, October 2026*

**Reference files:** this skill comes with `references/content-standards.md` and `references/content-qa-standard.md`. Use the versions in the client's Claude project if it has them, otherwise use these.


## Scope

This skill assesses whether a draft is ready for publication. It critically evaluates strategic quality, editorial quality, SEO effectiveness, EEAT compliance, and readability. It does not produce first drafts, refine writing style, or conduct SERP analysis.

**Entry condition:** A fully edited draft that has passed through the content-editor skill.
**Exit condition:** A structured review report with a clear publication recommendation.
**Gate rule:** Do not review a draft that has not been edited. If the draft has come directly from the content-writer skill without editing, flag this and route it through the content-editor skill first.

**Standard:** Do not approve weak content easily. The purpose of this review is to identify problems before they reach the client or go live, not to validate work that is not ready.

---

## Review framework

Run the following assessments in order. Produce a structured report with findings under each heading.

---

### 1. Overall assessment

Open with a one-paragraph summary covering:
- Strategic quality (does the article achieve what the brief intended?)
- Editorial quality (does it read as the work of a credible human?)
- SEO effectiveness (is it structurally and semantically positioned to rank?)
- Publication confidence (ready / ready with minor changes / needs revision before publication)

Be direct. If the draft is not ready, say so clearly and explain why.

---

### 2. Standards compliance check

This is a binary pass/fail check against the Content Standards document. Check each item and flag any failure.

| Standard | Pass / Fail | Notes |
|---|---|---|
| No em dashes present | | |
| No forbidden phrases present | | |
| All headings carry correct tag labels | | |
| Title tag present and under 60 characters | | |
| Meta description present and under 155 characters | | |
| All regulatory frameworks and official schemes linked | | |
| All performance figures attributed or sourced | | |
| No unsupported superlatives | | |
| No stacked declarative AI cadence | | |
| No "matters" / "matter" used as an importance signal | | |
| No "actually" outside direct quotations | | |
| "This means" / "means that" not used as a repeated connective (max two per article, never twice in one section) | | |
| No brief language, competitor references, or angle announcements visible in the copy | | |
| Bullets used only for genuinely parallel discrete items | | |
| Tables used for comparative or structured data | | |
| Primary keyword in H1, first 100 words and at least one H2 | | |
| Most important internal link in the first third, descriptive anchors | | |
| No invented client quotes, data, case studies, reviews or credentials | | |

Any failure in this check must be flagged as a blocker. The draft does not proceed to publication until all failures are resolved.

**Placeholders left in the copy.** Search the whole draft, not just the header, for [LINK NEEDED], [CLIENT INSIGHT], [DATA NEEDED], [VISUAL] and any other square-bracket note or instruction. Placeholders are easy to miss in a finished-looking draft, so always report them, even when they were planned.

- List every one with its type, the section it sits in and who supplies it.
- Any placeholder still in the copy means the verdict cannot be "Ready". The best possible verdict is "Ready with minor changes", and only when every remaining placeholder was approved in the brief and has a named owner.
- A placeholder that was not planned in the brief, has no owner, or was filled with something that looks invented is a blocker.
- Every remaining placeholder goes in "Must fix", so it travels with the review.

---

### 2a. Quality scores

Score each criterion from 1 to 5, quote one short passage as evidence, and give one teachable note. Use this scale consistently, because these scores are tracked across writers and clients over time.

| Criterion | 1: weak | 3: acceptable | 5: excellent |
|---|---|---|---|
| Usefulness | Restates the topic; reader still needs to search again | Answers the main question | Answers fully, anticipates the next question, reader can act |
| Originality | Rewrites what already ranks | Some angle of its own | Adds something not found elsewhere: insight, data, analysis or evidence |
| Accuracy | Unsourced or doubtful claims | Correct, lightly sourced | Correct, sourced, official bodies linked, caveats stated |
| Expertise | General statements anyone could write | Some specific detail | Operational detail that shows knowledge rather than claiming it |
| Clarity | Dense, hard to scan | Clear but uneven | Scannable, logical, one idea per paragraph, descriptive headings |
| Voice | Generic or salesy, AI patterns | Mostly on tone | Sounds like the client and a credible person throughout |

---

### 2b. Distinctiveness review

- **Requirement by content type:** blogs, guides and articles must contain at least one distinctive element; category, service and product pages should; news and short updates are optional.
- **Planned versus present:** compare the brief's "What makes this ours" section with the draft. Name the distinctive element that is present, or state that none is.
- **Genuine or decorative:** a table that only restates the prose, or a "real questions" section that answers generic questions, does not count.
- **Author:** a real byline is planned, and an expert reviewer where the topic affects health, money, legal matters or safety.
- **Structure:** if the heading pattern looks like a default template ("What is X, Benefits, How to, FAQs") rather than this topic's needs, say so.

If a blog or guide has no genuine distinctive element, the verdict cannot be better than "Ready with minor changes".

---

### 3. Strategic review

**Intent alignment:** Does the article genuinely satisfy the search intent identified in the brief? Would a user who searched the primary keyword find what they were looking for?

**Angle integrity:** Does the article maintain the differentiated angle established in the brief throughout? Or does it drift into generic territory in any section?

**Brief leakage:** Does any sentence expose the brief to the reader? Examples include comparing the article to competitors or "most guides", announcing what the article will do differently, or echoing brief instructions. The angle should be felt in the content, never stated as a point of difference. Flag every instance as a blocker with the exact sentence quoted.

**Audience alignment:** Does the register, depth, and tone suit the target audience throughout? Are any sections too technical or too elementary for the intended reader?

**Topical completeness:** Does the article cover what users need without covering what they do not? Flag any section that feels thin, any question the user would naturally have that goes unanswered, and any section that feels padded or unnecessary.

**Commercial integration:** Where commercial relevance has been included, does it feel contextual and trust-building? Or does it feel forced or premature? Flag any commercial messaging that disrupts the informational flow.

---

### 4. EEAT review

**Expertise signals:** Does the article demonstrate genuine domain knowledge through specificity and operational detail? Or does it rely on general statements that any uninformed writer could produce?

**Authoritativeness:** Are claims that require sourcing properly linked or attributed? Are any [LINK NEEDED] placeholders still outstanding?

**Trustworthiness:** Is the content honest about limitations, caveats, and where CHP or the relevant topic is not a good fit? Content that oversells or overstates is an EEAT liability.

**Missed EEAT opportunities:** Identify any section where a specific example, named framework, or operational detail would strengthen credibility without adding unnecessary length.

---

### 5. SEO review

**Primary keyword:** Is the primary keyword present naturally in the H1, within the first 100 words of body copy, and in at least one H2? Does it appear organically throughout without forced repetition?

**Semantic coverage:** Does the article use entities, related terminology, and conceptually adjacent language that signals topical depth to search engines? Or is it too narrow in its vocabulary?

**Snippet potential:** Are there sections structured clearly enough to surface as featured snippets or AI Overview citations? Specifically: are there definition-style passages, structured lists, or comparison tables that answer common questions precisely?

**Internal linking:** Are all proposed internal links present and correctly placed? Are any [LINK NEEDED] placeholders still outstanding for internal links?

**Cannibalisation risk:** Does this article risk competing with any existing page on the same domain for the same terms? If so, flag it.

**Title tag and meta description:** Are they within character limits? Do they read as useful summaries that would earn a click from a relevant searcher?

---

### 6. Readability and UX review

**Scanning support:** Can a reader scan the article and understand its structure and main points without reading every word? Are visual anchors (headings, bold text, bullets, tables) used where they genuinely help?

**Paragraph discipline:** Does each paragraph carry one primary idea? Are any paragraphs running too long or covering multiple ideas?

**Sentence rhythm:** Does sentence length vary naturally? Are there runs of sentences that all have the same length or structure?

**Repeated phrasing and register:** Search for recurring constructions, in particular "matters", "actually" and "This means". Beyond the pass/fail check, judge whether repeated connectives make follow-up statements sound alike, and whether the phrasing is too casual or twee for the client's tone as set by the example-analyser output. Quote the offending passages.

**Flow:** Does the article move logically from section to section? Are there any transitions that feel abrupt or any sections where the connection to the previous section is unclear?

**Introduction quality:** Does the introduction establish relevance quickly and move naturally into the content? Does it avoid throat-clearing, broad industry statements, or unnecessary definitions?

---

### 7. Strengths

List what the article does well. Be specific. Generic praise ("well-written," "comprehensive") is not useful. Name the sections, passages, or decisions that work and explain why they work.

---

### 8. Required changes before publication

List every issue that must be resolved before the article can be published. Prioritise by impact:

- **Blockers** (must fix before publication): standards compliance failures, significant intent misalignment, missing EEAT requirements, factual errors
- **Important** (should fix before publication): thin sections, missed opportunities, tone inconsistencies, missing internal links
- **Minor** (consider fixing): small readability improvements, phrasing preferences

Be specific about what needs to change and where. "The second paragraph of the efficiency section uses a stacked declarative pattern and should be rewritten as a single connected explanation" is useful. "Some areas could be improved" is not.

---

### 9. Publication recommendation

Close with one of three clear verdicts:

- **Ready for publication:** No changes required. The article meets all standards and is strategically strong.
- **Ready with minor changes:** Specific minor issues are listed above. Resolve these before publishing, but no structural revision is needed.
- **Needs revision:** Significant issues are identified above. The article should be revised and re-reviewed before publication.

Do not issue a "ready for publication" verdict if any blocker remains unresolved, or if any placeholder is still in the copy.

---

### 9a. Save the final draft to Google Drive

When the verdict is **Ready for publication**, or **Ready with minor changes** and those changes have been made, save the final copy following `references/drive-method.md`: as a Google Doc in the client's Content folder (month folder YYYY-MM, named "YYYY-MM [Content type] - [Title]", heading labels kept, no internal notes), or as a downloadable Markdown file with the same name if Google Drive isn't set up yet. If Drive isn't set up, show the setup note from the Drive method once.

Don't save anything when the verdict is **Needs revision**.

---

### 10. Summary block

Finish every review with this block, exactly in this format, so it can be pasted into the team's QA tracker:

Lead with judgement, not polish. The Overall and Fit for purpose lines are the most important part of the block: say plainly who the piece is for, whether it gives them what they came for better than what already ranks, and the one change that would most improve it. When reviewing several drafts at once, give one block per draft, each starting with a "Doc: [number]" line.

```
QA RESULT
Overall: [two or three sentences: who this is for, whether it gives them what they came for, and the single biggest improvement]
Fit for purpose: [yes / partly / no] | [one line on why]
Usefulness: [1-5] | evidence: "[short quote]" | note: [one teachable sentence]
Originality: [1-5] | evidence: "[short quote]" | note: [one teachable sentence]
Accuracy: [1-5] | evidence: "[short quote]" | note: [one teachable sentence]
Expertise: [1-5] | evidence: "[short quote]" | note: [one teachable sentence]
Clarity: [1-5] | evidence: "[short quote]" | note: [one teachable sentence]
Voice: [1-5] | evidence: "[short quote]" | note: [one teachable sentence]
Distinctive: [yes or no] | element: [what it is, or "none"]
SEO: [pass or attention] | note: [keyword placement, title and meta, internal links, snippet-ready sections]
Placeholders: [number still in the copy] | [each one: type, section, who supplies it, or "None"]
Verdict: [Ready / Ready with minor changes / Needs revision]
Coaching:
1. [the most useful lesson for the writer]
2. [second]
3. [third]
Must fix:
- [each blocker, or "None"]
END
```