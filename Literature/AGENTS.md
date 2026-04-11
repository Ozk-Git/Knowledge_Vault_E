# Literature/AGENTS.md

Rules for managing literature and source notes under `Literature/`.
In addition to the Vault-wide rules in `../AGENTS.md`, follow these rules within this directory.

---

## Role

Create initial-draft notes in `Literature/` from content ingested from `Clippings/`, `References/`, and `Daily/`.
AI creates the initial draft; humans edit.

---

## Standard Ingest Procedure

Targets:
- Unprocessed files in `Clippings/`
- Materials under `References/books/`
- Memos in `Daily/`
- Memos in `Inbox/`

Procedure:

1. Read the source and extract key points
2. Create an initial-draft note in `Literature/`
3. Use `templates/literature-note.md` as the template
   - **Required**: The frontmatter must always include `type: literature`
   - If the source file has metadata (author, published date, etc.), integrate it with the template fields
4. Tag AI-generated notes with `#llm-draft`
5. Prioritize existing tags and add appropriate tags based on content
6. If no existing tag is appropriate, create a new one
7. Search for related existing notes and create relative-path links
8. Create a relative-path link back to the source file so it remains reachable after processing
9. If related memos exist in `Inbox/`, and they can be unified into one idea, create a literature note and link to the `Inbox/` memos

On completion:
1. Update `index.md` as a derived summary, to the extent necessary
2. Append major changes and decisions to `log.md`
   Format: `## [YYYY-MM-DD] {Operation} | {Content}`

---

## Note Principles

- A literature note is not a transcription of a summary — write it as a draft that can later be promoted to `Permanent/`
- Mark speculation explicitly with `[Speculation]`
- When suggesting connections to existing notes, include the reason where possible
- Do not include `AGENTS.md`, `index.md`, or `log.md` as related-link targets
- For paper PDFs, prioritize `templates/paperdesk.md`; use `Literature/` as the storage destination for reading results

---

## Lint

- Report literature notes with `#llm-draft` that have been untouched for more than 2 weeks since creation
- Report important note candidates not yet promoted to `Permanent/`
- Report notes with insufficient link candidates

---

## Source Field

Record the following in the `## Source` section:

- `source`: relative path in `References/...` or a relative-path link in `[note title](relative/path.md)` format (relative from Vault root)
- `zotero_key`: record if using Zotero (Zotero internal key)
- `doi`: record if available
- `related_papers`: record if a related paper project exists

---

## Post-Ingest Handling

- Notes from `References/` must be consistent with the rules in `References/AGENTS.md`
- Notes from `Clippings/` — move the source file to `Clippings/Done/` after processing
- Remove the `#clippings` tag from files moved to `Clippings/Done/`
- Notes from `Inbox/` or `Daily/` — indicate Promote candidates to `Permanent/` as appropriate

---

## Interactive Deepening Mode

When the user comments on or asks about literature note content:

- Return a critical question: "Can this really be said?" about the source's claim
- Distinguish between the author's interpretation and your own
- Propose adding new perspectives that emerge through dialogue to `Inbox/` as a memo
- Point out ideas that become Promote candidates to `Permanent/` as they arise
- Only write to notes after user confirmation
