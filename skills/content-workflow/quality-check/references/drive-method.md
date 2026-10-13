# Working with Google Drive

*Version 1.1, October 2026*

How the content workflow reads examples from, and saves final drafts to, each client's Google Drive folders. Uses the Google Drive and Google Docs connectors in Claude.

## Where the links live

Every client's Client AI Context document has two rows in the details table at the top:

- **Content folder (Google Drive):** the link to the client's Content folder on the Clients shared drive.
- **Content examples folder (Google Drive):** optional. A folder of hand-picked pieces that best show the client's voice.

Always use these links. Never search the drive by client name to find a folder, because similar names lead to the wrong client. If the links are missing, ask the user for the Content folder link, and suggest adding it to the Client AI Context document.

## Before you start

Check what's set up in this chat:
- **Google Drive connector:** reads examples, creates folders, moves files.
- **Google Docs connector:** creates the final draft as a Google Doc.
- **Folder links:** the two Google Drive rows at the top of the client's Client AI Context document.

If anything is missing, don't stop. Carry on with the fallback below, and show the setup note once in the chat (not after every message).

### Setup note

Show this, ticking off what's already done:

> **Get set up with Google Drive (2 minutes, once)**
> 1. In Claude, open Settings, then Connectors, and connect **Google Drive** and **Google Docs** with your work Google account. If you can't see them, ask a Claude Owner to switch them on for the organisation.
> 2. In the client's Client AI Context document, paste the **Content folder (Google Drive)** link, and the **Content examples folder** link if they have one.
> 3. Re-upload the Client AI Context document to the client's Claude project.
>
> Once that's done, I'll read tone examples straight from Drive and save final drafts into the client's folder for you.

### Fallbacks

- **No Drive for examples:** ask the user to attach 3 to 6 examples (Google Docs exported as PDF or Word, or pasted text).
- **No Drive or Docs for saving:** create the final draft as a downloadable Markdown file named `YYYY-MM [Content type] - [Title].md`, with the same content a Google Doc would have. Tell the user where it should go: the client's Content folder, in the YYYY-MM month folder.
- **Connectors on, but no folder links:** ask for the Content folder link once. Use it for this piece, and suggest adding it to the Client AI Context document so nobody has to ask again.

## Reading tone examples

1. If the Client AI Context has a **Content examples folder**, read every document in it. These are the best examples by choice, so they take priority.
2. If there's no examples folder, look in the **Content folder** and pick 3 to 5 finished pieces:
   - Prefer the most recent months.
   - Skip briefs, plans, notes and anything with "draft", "brief" or "v1" in the name.
   - Prefer the content types you're about to write, for example blogs for a blog.
3. List the documents you used, with links, so the exec can check you picked well.
4. If a piece reads like it was written for a different client or brand, leave it out and say so.

## Saving the final draft

Save once the piece has passed review: a verdict of Ready, or Ready with minor changes once those changes are made.

1. **Month folder:** inside the Content folder, find the folder for this month, named `YYYY-MM` (for example `2026-10`). If it doesn't exist, create it.
2. **Name the doc:** `YYYY-MM [Content type] - [Title]`, for example `2026-10 Blog - How to fill raised beds`.
3. **Create** the Google Doc with the final copy:
   - Keep the heading labels exactly as in the draft, for example `[H2] What soil to use`, so the client and developers can see the structure.
   - Put the title tag and meta description at the top, labelled.
   - No internal notes, review comments or placeholders in the doc.
4. **Move** it into the month folder. Claude may ask the user to approve the move; that's expected.
5. **Hand over** the link to the doc and the folder it's in.

If the month folder can't be created or the move fails, give the doc link and say where it should go, so the exec can move it by hand. If the Google Doc can't be created at all, fall back to the Markdown file.

## Don't

- Don't save briefs, early drafts or review notes to the client's folder.
- Don't overwrite or edit existing documents. Always create a new one.
- Don't share documents with anyone. Sharing stays with the project lead.
