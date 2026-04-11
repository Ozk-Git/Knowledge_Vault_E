# Permanent/AGENTS.md

Rules for managing knowledge notes under `Permanent/`.
In addition to the Vault-wide rules in `../AGENTS.md`, follow these rules within this directory.

---

## Role

`Permanent/` is the core of the knowledge system and contains two types of notes:

- **Permanent notes**: One atomic idea each, written in your own words
- **Wiki integration pages**: Cross-note synthesis of a concept, entity, or comparison. Tagged with `#wiki`

Tag AI-generated or AI-updated content with `#llm-draft`.
Remove `#llm-draft` once the human has reviewed and edited the note.
Treat existing notes without tags as legacy notes — do not rewrite them wholesale. Migrate them gradually during editing or promotion.

---

## Promote

Targets:
- `Inbox/`
- `Literature/`
- `Daily/` notes ready for direct promotion

Procedure:

1. Confirm the one-note-one-idea principle
2. Create the note in `Permanent/`
3. Use `templates/permanent-note.md` as the template
4. Tag AI-generated notes with `#llm-draft`
5. Propose links to related existing `Permanent/` notes **with reasons**
6. Point out any connection possibilities to active papers
7. If the source file is in `Inbox/`, move it to `Inbox/Done/`
8. If the source file is in `Literature/` or `Daily/`, leave the original in place and treat it as the link source
9. Ask: "What changed in your understanding before and after writing this note?"

---

## Wiki-Update

Targets: Concept, entity, and comparison pages within `Permanent/`

- When 3 or more notes on the same concept accumulate, propose creating an integration page
- When contradictory statements are found, flag them and report to the user
- After new source Ingest, present candidate related integration pages for updating
- Tag integration pages with `#wiki`

---

## Interactive Deepening Mode

When the user comments on or asks about permanent note or Wiki integration page content:

- Return the question: "How can this connect with other concepts?"
- Present related, contradictory, or complementary relationships with existing `Permanent/` notes
- Point out unresolved questions that should remain as `#open-question`
- If splitting or merging existing notes appears necessary from the dialogue, propose it
- Only write to notes after user confirmation

---

## Lint

- Detect and report orphaned notes (zero incoming links)
- Report notes with `#llm-draft` left untouched for more than 2 weeks
- Report legacy notes that should be migrated next
- Check for contradictory statements spanning multiple notes
- Verify that `#open-question` items from `Papers/*/03_gaps.md` are reflected in `Permanent/`
