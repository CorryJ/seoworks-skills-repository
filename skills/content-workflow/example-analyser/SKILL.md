---
name: example-analyser
description: Use this skill to analyse client content examples and extract tone, voice, editorial patterns, and stylistic behaviours. Run this skill during client onboarding, before the first piece of content is planned for any new client, and whenever the client provides new examples. Output is used to populate the tone section of the client context document and inform all subsequent content work.
---

# Example Analyser

*Version 1.3, October 2026*

**Reference files:** this skill comes with `references/content-standards.md` and `references/content-qa-standard.md`. Use the versions in the client's Claude project if it has them, otherwise use these.


## Scope

This skill analyses provided client content examples — blogs, case studies, service pages, white papers, or any editorial output — and extracts the patterns that define how that client's content behaves. It does not write content. It does not plan content. It produces a structured tone and voice analysis that the content-strategist and content-writer skills use as their tonal reference.

**Entry condition:** One or more pieces of existing client content provided by the user.
**Exit condition:** A structured analysis report that can be directly inserted into the tone section of the client context document.
**Dependency:** The content-writer skill should not begin drafting for any client without example-analyser output in the project. If it does not exist, flag it.

---

## Getting the examples

Read the examples straight from Google Drive, following `references/drive-method.md`: the client's Content examples folder if the Client AI Context lists one, otherwise 3 to 5 recent finished pieces from their Content folder. List the documents you used, with links.

If the Drive connector isn't on, or the Client AI Context has no folder links, ask the user to attach the examples instead, and show the setup note from the Drive method once.

---

## What this analysis is for

The analysis answers one question: what does this client's content sound and behave like at its best, and what does it avoid?

This is not about imitation. It is about understanding the editorial register, structural tendencies, and tonal patterns so that new content feels consistent without feeling copied.

---

## Analysis framework

Analyse each provided example across the following dimensions. Where multiple examples are provided, identify what is consistent across all of them — those are the reliable patterns. Note where examples diverge, as this may indicate inconsistency in the client's existing output.

---

### 1. Tone and register

**Formality level:** Where does the writing sit on the spectrum from highly formal to conversational? Is it consistent across examples?

**Confidence level:** Does the writing make direct claims or hedge frequently? Does it sound assured or tentative?

**Emotional temperature:** Is the writing warm, neutral, or cool? Does it use personal pronouns ("we," "you") or maintain distance?

**Persuasion style:** Does the writing make explicit persuasive moves, or does it persuade through credibility and specificity alone?

**Peer relationship:** Does the writing treat the reader as a peer who already understands the domain, or as someone who needs to be educated? This distinction matters more than any other for technical and professional audiences.

Produce a 2 to 3 sentence tone summary that captures the register precisely. This summary should be specific enough that a writer who has never read the examples could use it to match the tone.

---

### 2. Sentence and paragraph patterns

**Sentence length:** What is the typical sentence length? Does it vary or is it uniform?

**Sentence structure:** Does the writing favour simple sentences, compound sentences, or complex sentences with subordinate clauses? What proportion of each?

**Paragraph length:** How long are typical paragraphs? Are they consistently short (2 to 3 sentences), medium (4 to 5 sentences), or variable?

**Paragraph structure:** Does each paragraph tend to open with a claim, then support it? Or does the writing build from context to conclusion? Or is it genuinely varied?

**Rhythm:** Describe the overall rhythm of the writing — does it have a fast, efficient pace or a more considered, deliberate one?

---

### 3. Structural and formatting tendencies

**Heading style:** What do the headings look like? Are they question-format, statement-format, keyword-led, or mixed? Do they reflect genuine user needs or do they feel keyword-driven?

**Use of bullets:** When does the writing use bullets? Are they for discrete lists, or for fragmenting continuous prose? How long are individual bullet points?

**Use of tables:** Does the writing use tables? For what content types?

**Use of bold:** Where is bold used? Key terms, lead-ins, or decorative emphasis?

**Introduction style:** How do the articles or pages open? Do they establish context immediately, or do they throat-clear? What is the typical first sentence structure?

**Conclusion/closing style:** How does the writing end? With a summary, a CTA, a forward-looking statement, or something else?

---

### 4. Commercial messaging style

**Where commercial messaging appears:** In body copy, in dedicated closing sections, in CTAs only, or woven throughout?

**How it is framed:** Does the writing pitch directly, or does it build credibility and let the commercial relevance emerge naturally?

**Restraint level:** Is the commercial messaging restrained and trust-building, or more direct and conversion-focused?

**CTA style:** What does the call to action look like? Directive ("get in touch"), soft ("find out more"), or question-led ("want to know if this works for your site")?

---

### 5. Vocabulary and terminology

**Domain vocabulary:** What technical or specialist terms does the writing use? Does it define them or assume reader knowledge?

**Preferred phrasings:** Are there recurring phrases or constructions that feel characteristic of this client's voice?

**Terms and phrasings to avoid:** Does the writing conspicuously avoid certain types of language (e.g. no hype words, no corporate jargon, no passive voice)?

**Analogy and example use:** Does the writing use analogies to explain complex ideas? What kind?

---

### 6. EEAT signals in existing content

**How expertise is demonstrated:** Through specificity, named frameworks, operational detail, case studies, or other means?

**Trust signals:** Does the writing cite sources, link to references, or name regulatory frameworks? Or does it make claims without support?

**Gaps:** Where is the existing content's EEAT weakest? This informs where new content can differentiate.

---

### 7. Weaknesses and AI-pattern risks

Identify any patterns in the existing content that should not be carried forward:

- Repetitive structures that feel formulaic
- Generic phrasing that could be more specific
- AI-sounding tendencies (stacked declaratives, symmetrical paragraph structure, mechanical transitions)
- Over-reliance on certain constructions
- Missed specificity where claims are made without operational grounding

These are not criticisms — they are patterns to consciously avoid repeating.

---

## Output format

Produce the analysis in two parts:

**Part 1: Tone and voice summary**
A structured summary suitable for direct insertion into the tone section of the client context document. This should include:
- Tone summary (3 to 5 words)
- Register description (one paragraph)
- What the writing sounds like at its best (one paragraph)
- What the writing must never sound like (one paragraph)
- Client-specific terms or phrasings to use
- Client-specific terms or phrasings to avoid

**Part 2: Full analysis**
The detailed findings across all six dimensions above, written as an analytical document. This is the reference material that informs writing decisions on more nuanced questions.

---

## How this output is used

The tone and voice summary from Part 1 is inserted directly into the client context document and becomes the tonal reference for all content produced for this client.

The content-writer skill checks for this output before beginning any draft. If it does not exist, the writer skill flags it. This is not a bureaucratic check — it is the mechanism that prevents new content from feeling tonally inconsistent with a client's existing output.

When new examples are provided by the client, re-run this skill and update the client context document accordingly.
