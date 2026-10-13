---
name: content-setup
description: "Get a client's Claude project ready for the content workflow: checks the plugins, connectors (Google Drive, Google Docs, Search Console, GA4, Canva) and the Client AI Context document, shows what's ready and what's missing, then helps fill the gaps: drafts the context doc from the client's website, finds and confirms the right Drive folders and GSC and GA4 properties, and offers the tone analysis. Use when starting a new client project, when someone types /content-setup, or to check an existing project is fully set up."
---

# Content setup

*Version 1.0, October 2026*

**Reference files:** this skill comes with `references/content-standards.md` and `references/content-qa-standard.md`. Use the versions in the client's Claude project if it has them, otherwise use these.

Follow `references/drive-method.md` for Google Drive and `references/data-method.md` for Search Console and GA4.

The job: by the end, this client's project has everything the content workflow needs, and the user knows exactly what, if anything, is left. Be quick and friendly. Do the work for them wherever you can; only ask them to do what needs their account or their judgement.

## Step 1: check what's in place

Check each item without asking the user, then show one table: **Item, Status (Ready / Missing / Needs checking), What to do**.

**Plugins and skills**
- Content workflow skills available (for example content-strategist, content-writer).
- Off-site content skills available (for example linkedin-post). Only needed if the client is having off-site work.

**Connectors** (check whether their tools are available in this chat)
- Google Drive and Google Docs: read examples, save final drafts.
- Search Console and GA4: performance data for planning and reporting.
- Canva: only needed for off-site designs.

**Project knowledge**
- Project instructions: the content workflow's instructions are in place.
- Client AI Context document uploaded.
- In its top table: Client ID, Client name, URL, Content folder (Google Drive), Content examples folder (optional), GSC property, GA4 property ID.
- Sections 1 to 4 filled in, not just the template's example text.
- Tone of voice analysis (from example-analyser), either in the context doc or as its own document.

For anything missing, the "What to do" column gives the exact steps, for example:
- Connector missing: "Settings, Connectors, connect Google Drive with your work Google account. Can't see it? Ask a Claude Owner to switch it on."
- Plugin missing: "Ask a Claude Owner to install the Content workflow plugin for the organisation."
- Project instructions missing: "Copy the Project Instructions from the skill bank into this project's instructions."

## Step 2: fill the gaps

Offer to do each missing piece now, one at a time, in this order. Skip anything already ready.

1. **Client AI Context draft.** If there isn't one, or it's mostly template text: read the client's website (homepage, main service or category pages, about page) and draft sections 1 to 3 in the template's structure. Mark every inferred line "[check]". Never invent commercial goals, figures or client preferences; leave those for the user. Ask the user to fill in or correct the "[check]" lines.
2. **Drive folders.** If the Drive connector is on but the links are missing: find candidate folders for this client on the Clients shared drive and show them with links. Ask the user to confirm the Content folder and, if there is one, the examples folder. Never assume a match.
3. **GSC and GA4 properties.** If the connections are on but the IDs are missing: list the properties that match the client's domain. Ask the user to confirm each one. Record the GSC property exactly as shown and the GA4 numeric property ID.
4. **Tone of voice.** If there's no tone analysis: offer to run example-analyser now, using the Drive examples or attached examples.
5. **Off-site.** If the client is having off-site work and the Off-site content plugin is installed: suggest /brand-profile to set up their brand and Canva templates.

## Step 3: hand over

1. **The updated Client AI Context**, with everything confirmed in this chat filled in: saved as a Google Doc in the client's Content folder if Drive is set up, otherwise as a downloadable Word or Markdown file. Tell the user to replace the old version in the project's knowledge.
2. **The status table again**, now updated, with anything still missing at the top.
3. **One line on what to do next**, usually "Ready to plan the first piece: ask for a content plan or a brief for [topic]."

## Running it again

Running /content-setup on a project that's already set up is a health check: show the table, flag anything out of date (for example the context doc not reviewed in six months, or a property the connection can no longer see), and offer fixes.

## Don't

- Don't guess folders, properties or IDs. Find candidates, then confirm with the user.
- Don't change project settings or share anything. Tell the user the steps instead.
- Don't overwhelm. One table, then one gap at a time.
