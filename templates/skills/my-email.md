---
name: my-email
description: My email assistant: finding and reading my Outlook mail, and drafting/replying as me with my style and formatting. Use for any email search, read, draft or reply task.
---

# My email

Mailbox: <ADDRESS> (via the Microsoft 365 connector).

**Draft only.** Never send an email, or a draft, without my explicit agreement to send that particular email.

## 1. Searching

These took trial and error with the Microsoft 365 connector:

- **Results come back newest first.** A search over several months fills page 1 with recent mail, and older matches only appear on later pages. If `moreResults` is true, keep paging (or narrow the window) until the whole period is covered. Never conclude "not found" from page 1.
- **Numbers and symbols ("5%") match very broadly.** They work only with a tight date window and/or a `sender`/`recipient`, and with every page checked.
- **Don't combine terms with OR.** One broad term swamps the rest. Run separate searches instead.
- **If the counterparty and rough period are known, filter by them** (`recipient`/`sender` plus dates) and read the bodies.
- **Try the words I would actually have written**, plus variants and synonyms.
- **Don't guess an email domain in `sender`.** A wrong domain returns nothing, with no error. Get the real address from a name search first.
- **Documents are usually attachments on threads with generic subjects.** Search by organisation, person, address or reference number rather than the document name.
- **Before saying "not found"**, list the searches that were run.

## 2. Writing style

Have Claude work this out from your sent mail, then correct it. Mine, for example:

- **Very brief.** Most replies are 1–3 sentences. Say the thing, ask for the thing, stop. No small talk, no recap of the thread.
- **Direct and polite.** Requests use "Could you please...". Confirmations are plain: "3PM Tuesday works."
- **Factual, not emotional**, even on sensitive topics.
- **British English**; contractions are fine. Bullet lists for several facts, dates or time slots.
- Avoid: preambles, filler, over-apologising, exclamation marks, emojis.
- **Greeting:** "Dear [first name]," for a named professional contact, "Hi [first name]," once informal, "Hello," for a company inbox.
- **Sign-off:** "Kind regards," then my full name on the next line; just my first name for family and friends.

## 3. Formatting and attachments

- Create drafts in clean HTML: one `<div>` per line, `<div><br></div>` for blank lines, `<ul><li>` for bullets, no `<p>`. For replies, use the reply-draft tools with only the new text in `body`.
- The connector rejects `style` attributes and `span`/`font` tags, so it can't set a font, and it can't attach files. I had Claude finish both in Outlook on the web through Chrome on my PC, but that proved unreliable, so now: draft everything, and tell me in one line which files to attach (with their paths).
