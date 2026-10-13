---
name: schema-builder
description: Use this skill to draft JSON-LD structured data for a finished page, after the content-reviewer has given a "ready" or "ready with minor changes" verdict, or when the user asks for schema for a page. It writes markup from the final copy only. It does not plan, write or review content.
---

# Schema Builder

*Version 1.0, October 2026*


## Scope

This skill produces JSON-LD structured data for a page whose copy is final. It describes what is visibly on the page. It never adds claims, ratings, authors or details that are not on the page.

**Entry condition:** Final copy, the page URL (or planned URL), and the brief's schema plan if one exists.
**Exit condition:** Validated-ready JSON-LD in a code block, with a short list of what the user must check.

---

## Choosing types

Use what genuinely describes the page:

| Page | Types |
|---|---|
| Blog post or guide | BlogPosting (or Article) with author (Person or Organization), datePublished, dateModified, headline, image, publisher |
| Any page | BreadcrumbList when breadcrumbs are visible; Organization for the publisher |
| Named author | Person with name, jobTitle and url to a real author page, only if that page exists |
| Product page | Product with name, description, image, brand, offers (price, priceCurrency, availability) taken from the page |
| Page with an embedded video | VideoObject with name, description, thumbnailUrl, uploadDate and embedUrl |

**Do not use as a default tactic:** FAQPage (rich results limited to well-known government and health sites since 2023) and HowTo (rich results removed). Only add FAQPage if the page genuinely is a set of questions and answers and the user asks for it, and say that it will not create a rich result for most sites.

**Never add:** aggregateRating or review markup unless real reviews are visible on the page; invented authors, credentials or dates.

---

## Method

1. Read the final copy and list the facts available: headline, author, dates, images, products, prices, videos, breadcrumbs.
2. Choose types from the table above. Use one @graph where several types belong together.
3. Fill only properties supported by the visible page. Where a value is unknown (an image URL, the publish date), insert a clear placeholder such as "[IMAGE URL]" rather than guessing.
4. Check every name, price and date against the copy.

---

## Output format

```json
{ ...JSON-LD... }
```

Then list:
- **Placeholders to fill:** each "[ ]" value.
- **Check before publishing:** run the page through Google's Rich Results Test and the Schema Markup Validator, and confirm the markup matches what is visible on the page.
