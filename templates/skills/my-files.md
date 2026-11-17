---
name: my-files
description: How to reach my documents (Files) and notes (Notes, my Obsidian vault), and Chrome on my PCs, through my two Claude Bridge connectors, one on my desktop and one on my laptop. Use this whenever I ask about anything that might be in my documents or notes (letters, contracts, insurance, bills, payslips, scans, CV, finances, travel, lists, plans, TODOs...), want something saved, noted down, filed or updated, want a document attached to an email or a web form, or want something done in my browser on my PC, even if I don't name a folder, a PC or a connector.
---

# My files, notes and PCs

## What's there

Two folders, the same on both PCs (they're synced):

- **Files**: my documents: papers, scans, letters, office files, images, organised in topic folders. Synced by <SYNC APP, e.g. MEGA>.
- **Notes**: my notes, Markdown files in an Obsidian vault. Synced by Obsidian Sync.

Paths always start with the folder: `Files/Finance/...`, `Notes/...`. Use `list_dir` to see what's there rather than guessing folder names.

## Two connectors, one set of files

I have two Claude Bridge connectors: one for my desktop and one for my laptop. They are two ways in to the **same** Files and Notes, not two different collections.

- Either one is fine. A PC can be asleep or switched off, so if a connector fails, times out or isn't listed, try the other before telling me it didn't work. Only say the files are unreachable when both fail.
- A change made through one PC reaches the other through sync, usually within a minute. If you need to read something back right after changing it, use the same PC.
- If a PC's sync app wasn't running, the bridge starts it and waits for it to catch up, so the first call can take a little longer.
- Don't mention which PC you used unless it matters (a failure, or Chrome).

The one exception is **Chrome**: the Chrome tools act in that PC's own Chrome, with that browser's tabs and sign-ins. If the task depends on being signed in somewhere, use the PC I mean, and ask if it's unclear.

## Working with documents and notes

- **Finding:** `find_files` for names and `search_text` for words inside text files and notes, before opening things one by one.
- **Reading:** `read_text` for text and notes; `read_pdf` for a PDF's text; `view_file` to look at a scan, a photo or a PDF page's layout.
- **Office files** (Word, Excel...) and big files: `create_download_link`, then fetch the URL into your own workspace to work on it. To save a file you made there back onto the PC, use `create_upload_link`. Both need the PC's address in Claude's network allowlist.
- **Secret files** (`.secret` in the name): download link only, straight into a private file (`mkdir -p secret && chmod 700 secret`), read only by the script that needs it. Never print or show it, and delete it at the end.
- **Notes are Obsidian Markdown.** Keep `[[wikilinks]]`, tags and frontmatter as they are. Prefer `edit_text` or `append_text` over rewriting a whole note. Put a new note where similar notes already are, and follow their naming.
- **Filing documents:** look at the existing folders first and put things where they belong. Ask if nothing fits, rather than inventing new structure.
- **Change only what was asked.** Everything syncs to all my devices.
- **Deleting:** `delete_files` only for files I asked or agreed to delete, or redundant files you made yourself. Everything changed or deleted is kept 30 days; `restore_file` puts it back.
- **Sensitive data:** documents hold ID, bank and medical details. Only quote what the task needs.

## Chrome on the PCs

- Start with `tabs_context_mcp` (with `createIfEmpty: true`) and work in your own tab, not my tabs.
- **Attaching files** (email attachments, uploads to a form): find the file with `find_files`; don't click the attach button (it opens a file picker nobody can use); get the file input's ref with `find` or `read_page`; call `file_upload` with the bridge path, the ref and the tab.
- **Site permissions:** the Claude in Chrome extension asks per site, and I'm usually not at the PC to click Allow. If a call says the permission prompt timed out, tell me to allow that site in the extension.
- Ask before anything that can't be undone: buying, sending, submitting, deleting, changing account settings.

## When something fails

- **A connector doesn't respond:** try the other PC.
- **Chrome calls fail:** `chrome_status` says why.
- **"Unknown folder":** the only folders are Files and Notes.
- **Bridge version:** `update_bridge` shows it and can install an update. The PCs also update by themselves every day.
