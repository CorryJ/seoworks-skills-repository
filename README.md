# The SEO Works — Skills Repository

A collection of Claude skills built by The SEO Works, ported and improved from internal tools and Streamlit applications.

Each skill is a structured markdown file that instructs Claude how to behave for a specific task. Drop the `SKILL.md` into your Claude skills directory to activate it.

---

## Skills

### [persona-plotter](./skills/persona-plotter/)

Generates audience personas with targeted long-tail search phrases and key questions for any topic. Originally built as the PersonaPlotter Streamlit app — ported to a Claude skill with improved persona differentiation, intent variation across search phrases, and follow-up capabilities the original app couldn't support.

**Triggers:** "persona plotter", "generate personas", "audience personas", "who searches for [topic]", "map my audience"

---

### [content-titles-generator](./skills/content-titles-generator/)

Generates catchy, magnetic article and content titles for any topic, with optional control over writing style and tone. Originally built as the Content Titles Generator Streamlit app — ported to a Claude skill with 19 style options, 43 tone options, topic-implied tone detection, and the ability to develop a chosen title into an outline or intro paragraph.

**Triggers:** "content titles", "title ideas", "headline ideas", "generate titles", "give me title ideas for [topic]", "I need a title for", "suggest headlines for"

---

## Structure

\`\`\`
seoworks-skills-repository/
├── README.md                        # This file
└── skills/
    ├── persona-plotter/
    │   ├── SKILL.md                 # Core skill instructions & metadata
    │   └── resources/               # Assets (logos, templates, examples)
    └── content-titles-generator/
        └── SKILL.md                 # Core skill instructions & metadata
\`\`\`

---

## Adding a new skill

1. Create a folder under \`skills/\` named after the skill (lowercase, hyphenated)
2. Add a \`SKILL.md\` with the frontmatter \`name\` and \`description\` fields
3. Add a \`resources/\` subfolder if the skill needs supporting assets
4. Update this README with a description and trigger phrases

---

Built by [The SEO Works](https://www.seoworks.co.uk) — Digital Growth Experts.
