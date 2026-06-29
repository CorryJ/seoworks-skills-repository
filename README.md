# The SEO Works — Skills Repository

A collection of Claude skills built by The SEO Works, ported and improved from internal Streamlit applications.

Each skill is a structured markdown file that instructs Claude how to behave for a specific task. Install a skill by dropping its `SKILL.md` into your Claude skills directory.

---

## Skills

### [persona-plotter](./skills/persona-plotter/)

Generates 5 distinct audience personas for any topic, each with 20 long-tail search phrases and a list of key questions. Ported from the PersonaPlotter Streamlit app with improved persona differentiation, intent variation across search phrases, and follow-up capabilities.

**Triggers:** "persona plotter", "generate personas", "audience personas", "who searches for [topic]", "map my audience"

---

### [content-titles-generator](./skills/content-titles-generator/)

Generates catchy, magnetic article and content titles for any topic, with control over writing style (19 options) and tone (43 options). Ported from the Content Titles Generator Streamlit app. Always prompts for style and tone before generating, with the option to suggest your own.

**Triggers:** "content titles", "title ideas", "headline ideas", "generate titles", "give me title ideas for [topic]", "suggest headlines for"

---

### [topical-mind-map](./skills/topical-mind-map/)

Generates a comprehensive hierarchical mind map for any topic, breaking it down from central concept through primary, secondary, and tertiary branches, plus a semantic keywords table grouped by category. Ported from the Topical Mind Map Generator Streamlit app. Can also render an interactive visual mind map as a downloadable HTML artifact.

**Triggers:** "topical mind map", "mind map", "topic map", "map out this topic", "topic clusters", "content planning for [topic]", "brainstorm topics around"

---

## Repository structure

\`\`\`
seoworks-skills-repository/
├── README.md                             # This file
└── skills/
    ├── persona-plotter/
    │   ├── SKILL.md                      # Core skill instructions & metadata
    │   ├── README.md                     # What the skill does & how to use it
    │   └── resources/                    # Assets (logos, templates, examples)
    ├── content-titles-generator/
    │   ├── SKILL.md                      # Core skill instructions & metadata
    │   └── README.md                     # What the skill does & how to use it
    └── topical-mind-map/
        ├── SKILL.md                      # Core skill instructions & metadata
        └── README.md                     # What the skill does & how to use it
\`\`\`

---

## How to add a skill to Claude

Skills are installed via the Claude desktop app or Claude Code. Each skill is a \`SKILL.md\` file placed in your Claude skills directory.

### Step 1 — Find your skills directory

On macOS and Linux, your Claude skills directory is typically:

\`\`\`
~/claude/skills/
\`\`\`


On Windows, your Claude skills directory is typically:

\`\`\`
C:\Users<your-username>.claude\skills\
\`\`\`

You can also open it quickly from PowerShell or Command Prompt by running:

\`\`\`
explorer %USERPROFILE%.claude\skills
\`\`\`

Note: the `.claude` folder is hidden by default on Windows. In File Explorer, go to View and tick "Hidden items" to make it visible.

If it does not exist yet, create it.

### Step 2 — Add the skill folder

Copy the skill folder (e.g. \`persona-plotter/\`) into your skills directory so the structure looks like:

\`\`\`
~/claude/skills/
└── persona-plotter/
    └── SKILL.md
\`\`\`

### Step 3 — Restart Claude

Restart the Claude desktop app or start a new Claude Code session. The skill will be picked up automatically.

### Step 4 — Use it

Just talk to Claude naturally. Skills trigger on the phrases listed in each skill's description. You do not need to name the skill explicitly — just describe what you want.

> "Generate personas for sustainable fashion"

> "Give me 10 title ideas for a blog post about AI in recruitment"

> "Mind map for electric vehicles"

---

## Adding a new skill to this repository

1. Create a folder under \`skills/\` named after the skill (lowercase, hyphenated)
2. Add a \`SKILL.md\` with frontmatter \`name\` and \`description\` fields
3. Add a \`README.md\` explaining what the skill does and how to trigger it
4. Add a \`resources/\` subfolder if the skill needs supporting assets
5. Update this README with the skill name, description, and trigger phrases

---

Built by [The SEO Works](https://www.seoworks.co.uk) — Digital Growth Experts.
