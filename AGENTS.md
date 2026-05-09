# AGENTS.md

This Vault is a researcher's external knowledge system supporting the flow:
Capture → Knowledge → Output.

---

## Session Start

**Trigger**: "Start a session" / "Please start the session"

1. Read `index.md` to get an overview of the entire Vault
2. If actual file counts or update status matter, verify the real directory rather than trusting `index.md` blindly
3. Check the last 5 entries in `log.md` to identify tasks carried over from the previous session
4. If `log.md` records appear insufficient, refer to actual files or Git history as needed
5. Based on the information below, propose up to 3 tasks to tackle this session (in priority order):
   - Number of unprocessed items in `Inbox/` and `Clippings/` (include counts)
   - Notes tagged `#llm-draft` left untouched for more than 2 weeks
   - Unresolved items in `Papers/*/03_gaps.md` (`status: open / in-progress`)
   - Carry-over tasks from `log.md`
6. Run Probe and include the results in the session-start report
7. Report the current Vault status

## Session End

**Trigger**: "End the session" / "Please end the session"

1. Update `index.md` as a derived summary, to the extent necessary
2. Append major changes and decisions to `log.md` as a supplementary operation log
   Format: `## [YYYY-MM-DD] {Operation} | {Content}`
3. If new questions or half-formed ideas emerged this session, propose adding a memo to `Inbox/`
4. Summarize the key points of this session's work in 3 lines or fewer as a closing report

---

## Directory Roles

### Clippings/
Temporary holding area for lightweight external sources: web articles, saved social media posts, etc.
Processed files are moved to `Clippings/Done/`.

### References/
Permanent archive for paper PDFs and books. **Do not delete. Do not move to Done/.**
Follow the rules in `References/AGENTS.md`.

### Daily/
Daily observations, experiment notes, and meeting memos.
Periodically promote these to `Inbox/` or `Literature/`.
If a note is already close to one-note-one-idea, it may be Promoted directly from `Daily/` to `Permanent/`.

### Inbox/
Drop zone for fleeting thoughts and rough notes.
Processed files are moved to `Inbox/Done/`.

### Literature/
Literature and source notes generated from `Clippings/`, `References/`, and `Daily/`.
AI creates the initial draft; humans edit. Follow `Literature/AGENTS.md`.

### Permanent/
The core of the knowledge system. Manages permanent notes and Wiki integration pages.
Follow `Permanent/AGENTS.md`.

### Papers/
Per-paper workspaces managed as `Papers/[paper-slug]/`.
Follow `Papers/AGENTS.md`.

---

## Principles

- **AI creates drafts. Final judgment and editing are done by humans.**
- Always tag AI-generated notes with `#llm-draft`
- Always ask for user confirmation before overwriting or deleting existing notes
- `References/` is read-only — do not move or delete files
- When output contains speculation, mark it explicitly with `[Speculation]`
- Do not generate long text without instruction. Follow **propose → confirm → execute** order
- Maintain the one-note-one-idea (Atomicity) principle
- When discussing knowledge, append one "next question" at the end of the response. Omit this during task execution

---

## Operation Definitions

### Ingest — Source Ingestion
Targets: Unprocessed files in `Clippings/`, paper PDFs and books under `References/`, memos in `Daily/`

Use the appropriate prompt based on source type:
- **Paper PDF** (under `References/papers/`)
  → Apply `templates/paperdesk-read.md`
- **Peer-review simulation of your own paper**
  → Apply `templates/paperdesk-review.md`
- **Books and other sources** (under `References/books/`, `Clippings/`, `Daily/`)
  → Follow the standard procedure in `Literature/AGENTS.md`

### Promote — Create Permanent Note
Targets: `Inbox/`, `Literature/`, or `Daily/` notes ready for direct promotion
Follow `Permanent/AGENTS.md`.

### Wiki-Update — Update Knowledge Integration Pages
Targets: Concept, entity, and comparison pages within `Permanent/`
Follow `Permanent/AGENTS.md`.

### Paper-Work — Paper Writing Management
Targets: `Papers/[paper-slug]/`
Follow `Papers/AGENTS.md`.

### Lint — Vault Health Check
Run periodically or on demand:

- Detailed checks follow `rules/lint.md`
- **AGENTS.md bloat check**: If the root `AGENTS.md` exceeds 170 lines, propose at session start to move redundant detail to `rules/workflows.md`

### Probe — Proactive Inquiry
Run automatically at session start.

- Search recently Ingested notes for contradiction, complementarity, or extension relationships with existing Permanent notes, and report findings
- Flag `status: confirmed` Claims whose supporting evidence appears thin
- From `#open-question` notes, suggest ones that existing knowledge may already answer
- Highlight 1–2 long-neglected Permanent notes and prompt connection with recent knowledge

### Connect — Serendipity Exploration
Run on demand or alongside Lint. See `rules/workflows.md` for details.

### Remember — Save Discussion to Memory
**Trigger**: "Please save this discussion to memory"
See `rules/workflows.md` for details.

---

## Per-Directory Additional Rules

If a subdirectory contains an `AGENTS.md`, read it before operating in that directory.

- `Literature/` → `Literature/AGENTS.md`
- `Permanent/` → `Permanent/AGENTS.md`
- `Papers/` → `Papers/AGENTS.md`
- `References/` → `References/AGENTS.md`

---

## System Improvement

When asked to modify AGENTS.md or templates:

1. Read the target file
2. Propose the changes and obtain user confirmation
3. Write the changes after confirmation
4. Record in `log.md` (format: `## [YYYY-MM-DD] System | {change content}`)

- If the change affects other AGENTS.md files, state this explicitly
- Template changes do not apply retroactively to existing notes

---

## Optional References

- `rules/architecture.md` — Vault information flow and Papers/ structure diagram
- `rules/workflows.md` — Detailed procedures for Probe and Connect
- `rules/lint.md` — Detailed Lint criteria
- `rules/tags.md` — Tag system
- `rules/index-log.md` — Management rules for `index.md` and `log.md`
