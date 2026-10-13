---
name: quality-check
description: "Use this skill to check finished content against The SEO Works content standards and give a clear verdict. Works on one piece or a batch, on blogs, guides, service, category and product pages, whoever wrote them. Use when someone asks to check, QA, sense-check, audit or sample content, or types /quality-check. It finds problems and only fixes them when asked. For the formal final review inside the content workflow, use content-reviewer."
---

# Quality check

*Version 1.0, October 2026*

**Reference files:** this skill comes with `references/content-standards.md` and `references/content-qa-standard.md`. Use the versions in the client's Claude project if it has them, otherwise use these.

A fast, honest check of finished content against our standards. It works on one piece or a batch, and whether or not the piece went through the full workflow.

## Before you start

1. **Get the content.** Attached docs, pasted text, or a page Claude can read. If nothing is there, ask for it in one line and stop.
2. **Work out the type of each piece:** blog or guide, or service, category or product page. Say which you assumed.
3. **Look for the brief and client context** in the project or chat. If there is a brief, check against it too. If not, say "No brief found" and carry on.
4. **Competitive keyword?** If the user says so, or the piece targets a broad, high-volume term, include the competitive checks.

## How to judge

- Judge first whether it does the job for the reader, then the details. Clean SEO on a piece that says nothing new is not ready.
- Be a strict editor, not a cheerleader. Don't invent problems to fill a list.
- Quote the exact words for every problem, and say which section it's in.
- Blogs and guides must add something the top results don't have. If one doesn't, it can't be Ready. On pages, flag missing information gain but don't block on it.
- Anything left behind, such as [CLIENT INSIGHT], [LINK NEEDED] or notes to the writer, means it can't be Ready.
- Never suggest invented facts, figures, quotes, reviews or credentials as a fix. Suggest a placeholder and who should supply it.

## The standards

### Does it do the job?

- **Follow the brief.** The brief is our plan for the piece. If it needs to change direction while writing, update the brief first so everyone works from the same plan.
- **Answer first.** Give readers what they searched for in the opening lines, and answer every question heading in the sentence straight after it.
  - Like this: How often should you clean an air fryer? Wipe it after every use and deep clean it every one to two weeks.
  - Not like this: How often should you clean an air fryer? It depends on a number of factors.
- **Be specific.** Real figures, names, steps and examples beat general statements every time.
  - Like this: Service it every 1,000 to 2,000 running hours.
  - Not like this: Service it regularly.
- **Make every section count.** No padding and no saying the same thing twice. If a section only has a couple of sentences, build it out or merge it.

### Information gain

- **Add something the top results don't have.** A must for blogs and guides, and worth doing on pages too. Plan it in the brief, because it can't be added at the end.
- **Don't rewrite what's already ranking.** If our piece could swap places with the top result and nobody would notice, it isn't finished.

### Standards and SEO

- **Keyword in the right places.** In the H1, the first 100 words and one H2. Never forced in.
- **Title and meta.** Title tag under 60 characters. Meta description under 155, describing the page honestly.
- **Internal links that help.** At least two. Put the main one near the top, with link text that says where it goes.
  - Like this: See our guide to pergola planning permission.
  - Not like this: Click here.
- **Headings that belong to this topic.** One H1, headings labelled and in order. Steer clear of the What is / Benefits / FAQs template.
- **Schema that matches the page.** Article, Product or Breadcrumb where they fit. No FAQ or HowTo schema just for rich results.

### Can it be trusted?

- **Nothing made up.** Quotes, stats, case studies, reviews and qualifications are all real, and we know where they came from. If we don't have something yet, use a placeholder agreed in the brief.
- **Show your sources.** Stats and claims link to their source. Regulations and official bodies link to their own website.
  - Like this: Under GOV.UK's permitted development rules, structures within 2m of a boundary must stay under 2.5m tall.
  - Not like this: Studies show that 80% of homeowners prefer a pergola.
- **Right for the audience.** Facts, spelling, currency, prices and regulations are correct and current for the client's market and readers.
- **Real people only.** A real author or an honest team byline. Anyone named as an expert has agreed to it and actually reviewed the piece.
- **Nothing left behind.** No placeholders, notes, [LINK NEEDED] or stray dashes in the version that goes to the client.

### How it reads

- **Sound like the client.** Match the tone of the client's own content examples. A specialist audience gets a knowledgeable peer; a consumer audience gets a helpful expert.
- **Show expertise, don't claim it.** Detail only someone who knows the subject would include does more than words like expert or leading.
  - Like this: Leave 60cm between the posts and any fence so you can maintain both.
  - Not like this: Our expert team are leaders in garden design.
- **Easy to scan.** One idea per paragraph. Bullets for lists, tables for comparisons, bold for the bits people look for.
- **Confident, not salesy.** Inform first. Mention the client's service where it genuinely helps the reader.
- **Doesn't read like AI.** No em dashes, no filler phrases and no runs of short, punchy sentences.
  - Like this: It's quick to fit. Most take under an hour.
  - Not like this: It's quick to fit — most take under an hour.
  - Avoid these phrases: when it comes to, it's important to note, unlock, elevate, seamless, game-changing, delve into, whether you're, ever-evolving, boost
  - Don't start paragraphs with Additionally, Furthermore or Moreover
  - Don't end sections with In conclusion or To summarise
  - Replace em dashes with a full stop, a comma or a colon
  - Three short sentences in a row reads like an advert. Join them into one that explains

### For competitive pieces

- **Check the competition.** Look at the top three results. What do they cover that we don't, and what do we add that they don't?
- **Match the format.** If the top results are comparisons, a how-to guide probably won't win.
- **Write a short answer near the top.** A clear 40 to 60 word answer to the main question, so it can be lifted into snippets and AI answers.
- **Show the experience.** An author bio, a reviewer for health, money, legal or safety topics, and an updated date.
- **Fit into the site.** No overlap with an existing page, and at least one existing page links to the new one.

### Where information gain comes from

- **The client's own data.** Prices, results, timings and figures from their own work.
- **First-hand experience.** What their team sees on the job, week in, week out.
- **An expert view.** A line from someone at the client who knows their stuff, with their name on it.
- **Something we built.** A comparison table, worked example or cost breakdown made for this piece.
- **Real customer questions.** What people actually ask the client, answered properly.
- **A visual made for it.** A diagram, process or checklist the designer can build.
- **Fresher and more relevant.** More up to date, or more specific to the audience, than what's already out there.

## The verdict

- **Ready:** Everything checks out. Send it.
- **Ready with minor changes:** Only standards and SEO points need work. Fix them, no need for another review.
- **Needs revision:** Something in the job, information gain or trust needs work. Fix it and review it again.

## How to reply

### One piece

**Verdict:** Ready, Ready with minor changes, or Needs revision, with one line on why.

1. **Fix before it goes out.** What's wrong, where (quote it), and the fix.
2. **Worth improving.** Same format, five at most.
3. **What's working.** Two or three lines.
4. **Left behind.** Any placeholders or notes still in the text, or "None".

End with: "Say **fix it** and I'll make these changes and check it again."

### A batch

Start with a table: Piece, Type, Verdict, Biggest issue. Then give the four sections above for each piece, kept short. Finish with **Patterns**: anything that shows up in more than one piece, and the standard it relates to.

## When asked to fix it

Fix everything under "Fix before it goes out", plus anything under "Worth improving" you're confident about. Keep the client's voice. Don't add facts, figures or quotes you can't source: use a placeholder instead. Give the full revised piece, then a short list of what you changed. Then check the new version again and give a new verdict.

## Don't

- Don't rewrite anything until asked.
- Don't pad the reply. If a piece is ready, say so in a few lines.
