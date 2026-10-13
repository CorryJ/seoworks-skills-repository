# Working with Search Console and GA4

*Version 1.0, October 2026*

How the content skills use the Google Search Console (GSC) and Google Analytics 4 (GA4) connections, without ever reporting the wrong client's data.

## Where the IDs live

The details table at the top of every Client AI Context document has:

- **GSC property:** exactly as Search Console shows it. Either a domain property, `sc-domain:example.co.uk`, or a URL-prefix property, `https://www.example.co.uk/`. These are different properties with different data.
- **GA4 property ID:** the numeric ID, for example `123456789`, from GA4 Admin, Property details. Not the `G-XXXXXXX` measurement ID.

## Rules

1. **Only use the IDs in the Client AI Context.** Never pick a property by name.
2. **If an ID is missing:** list the properties the connection can see that match the client's domain, and ask the user which is right. Use the confirmed one for this chat, and suggest adding it to the Client AI Context.
3. **If the connection can't see the property:** say it's an access problem. The account behind the connection needs adding as a user on that client's property. Don't fall back to a different property.
4. **Always state the property and date range** with any figures, for example "GSC, sc-domain:example.co.uk, last 3 months".
5. **Use data to inform, not decorate.** Pull what changes a decision: pages already ranking for a topic, queries with impressions but few clicks, pages losing clicks, visits from tracked links.
6. **Never put client data in content.** GSC and GA4 figures are for planning and reporting, not for the published piece.

## If the connections aren't set up

Carry on without data and say so in one line. Suggest connecting GSC and GA4, and adding the property IDs to the Client AI Context.
