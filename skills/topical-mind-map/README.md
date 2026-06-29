# Topical Mind Map Generator

Generates a comprehensive hierarchical mind map for any topic, plus a semantic keywords table. Designed to help content teams understand the full scope of a subject before writing, and to support topical authority building for SEO.

Originally built as the Topical Mind Map Generator Streamlit app by The SEO Works.

---

## What it produces

Two outputs in sequence:

### 1. Topical Mind Map (table)

A hierarchical markdown table breaking the topic down from central concept through primary, secondary, and tertiary branches. Minimum 6 primary branches, each with 3-5 secondary branches. Branches cover informational, transactional, commercial, and navigational angles.

### 2. Semantic Keywords (table)

A table of nouns, entities, and semantically related keywords grouped into meaningful categories (People, Tools, Processes, Actions, Related Concepts, etc.).

---

## How to trigger it in Claude

Just describe what you want. Examples that will trigger this skill:

> "Generate a topical mind map for SEO and LLMs"

> "Mind map for electric vehicles"

> "Topic map for home insurance"

> "Map out this topic: sustainable fashion"

> "What topics should I cover for a content strategy around B2B SaaS?"

You do not need to say "Topical Mind Map Generator" — any request to map out a topic or plan content around a subject will trigger it.

---

## Follow-up options

After generating both tables, you can:

- **Visual mind map** — render an interactive visual of the full topic hierarchy as a downloadable HTML file (pan, zoom, click to collapse/expand branches)
- **Drill down** — pick any primary branch and Claude will expand it into a full sub-map
- **Content brief** — choose any branch and Claude will turn it into a full content brief
- **Export** — download both tables as a Word document

---

## Example prompt from testing

> "Generate a topical mind map for SEO and LLMs"

This produced 7 primary branches: How LLMs Are Changing Search, How LLMs Are Trained, Optimising for LLM Visibility, Technical SEO for LLMs, Content Strategy for LLMs, Measuring SEO in an LLM Era, and Risks & Challenges — each with multiple secondary and tertiary branches, plus a semantic keywords table across 10 categories.

Following up with "Visual mind map" produced an interactive HTML artifact with all nodes, pan/zoom controls, and click-to-collapse functionality.
