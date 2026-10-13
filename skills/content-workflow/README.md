# Content Workflow

A set of eight connected skills that take a piece of SEO content from client onboarding through to a published, schema-marked-up page. Each stage is its own skill with a single job, so Claude plans, writes, edits and reviews as separate steps rather than blending them together.

All eight skills share the same standards: `content-standards.md` (how we write) and `content-qa-standard.md` (how we check). Each skill carries its own copy in `references/`, and uses the version in the client's Claude project instead if there is one.

---

## The skills

| Skill | What it does | Run it when |
| :---- | :---- | :---- |
| **content-setup** | Checks a client's Claude project has the right connectors (Google Drive, Google Docs, Search Console, GA4, Canva) and a Client AI Context document, then helps fill any gaps | Starting a new client project, or checking an existing one |
| **example-analyser** | Analyses client content examples to extract tone, voice and editorial patterns, feeding the tone section of the client context document | During onboarding, and whenever the client sends new examples |
| **content-strategist** | SERP analysis, content angles, briefs and heading structure. Plans only, never drafts | Before any drafting begins |
| **content-writer** | Drafts the content from an approved brief | After a brief is approved |
| **content-editor** | Refines and elevates a completed draft | After a full draft exists |
| **content-reviewer** | Formal pre-publication QA against our standards | After editing, before publishing or sending to a client |
| **schema-builder** | Drafts JSON-LD structured data from the final copy | After the reviewer gives a "ready" or "ready with minor changes" verdict |
| **quality-check** | Fast standalone check of finished content, one piece or a batch, whoever wrote it | Any time you want a verdict on existing content |

---

## How the workflow fits together

```
content-setup
     |
example-analyser
     |
content-strategist  ->  content-writer  ->  content-editor  ->  content-reviewer  ->  schema-builder
```

`quality-check` sits outside this line. Use it for content that did not go through the full workflow, or for sampling and auditing a batch. For the formal final review inside the workflow, use `content-reviewer`.

---

## How to trigger them in Claude

Describe what you want and the right skill will pick it up. Examples:

> "Set up this client project for the content workflow" (or type `/content-setup`)

> "Analyse these content examples for tone"

> "Run a SERP analysis and brief for [topic]"

> "Draft the article from this brief"

> "Edit this draft"

> "Review this before it goes to the client"

> "Write the schema for this page"

> "Quality check these five blog posts" (or type `/quality-check`)

---

## Before you start

- Run **content-setup** first for any new client. It builds on the Client AI Context document, which the other skills read for tone, audience and priorities.
- The writer needs an approved brief in the conversation, the editor needs a full draft, and the schema-builder needs a reviewed page. Each skill will tell you if its input is missing.
- The skills follow `references/drive-method.md` for Google Drive and `references/data-method.md` for Search Console and GA4 data, so the relevant connectors need to be available in the project.

---

## Installation

Each sub-folder is a separate skill. Copy the ones you need (usually all eight) into your Claude skills directory, keeping each folder and its `references/` subfolder intact:

```
~/claude/skills/
├── content-setup/
├── example-analyser/
├── content-strategist/
├── content-writer/
├── content-editor/
├── content-reviewer/
├── schema-builder/
└── quality-check/
```

See the [main README](../../README.md) for finding your skills directory on macOS, Linux and Windows.

---

## Handoff from keyword research

The [keyword-research](../keyword-research/) skill runs before this workflow. Its approved keyword priority map populates the "Keyword directions" section of the client context document, and each primary group becomes a starting point for `content-strategist`.
