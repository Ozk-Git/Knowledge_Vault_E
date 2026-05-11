# AGENTS.md

This Vault is a researcher's external knowledge system supporting the flow:
Capture → Knowledge → Output.

The root `AGENTS.md` is an entry point. Detailed procedures are delegated to `rules/` and directory-specific `AGENTS.md` files.

---

## Sessions

### Session Start

**Trigger**: "Start a session" / "Please start the session"

Follow `rules/workflows.md#session-start`: check `index.md`, `log.md`, unprocessed item counts, and Probe results, then propose up to 3 tasks for the session.

### Session End

**Trigger**: "End the session" / "Please end the session"

Follow `rules/workflows.md#session-end`: update `index.md` and `log.md` as needed, then summarize the session in 3 lines or fewer.

---

## Directory Operations

For the overall Vault structure and directory roles, see `rules/architecture.md`.

If a subdirectory contains an `AGENTS.md`, read it before operating in that directory.

- `Literature/` → `Literature/AGENTS.md`
- `Permanent/` → `Permanent/AGENTS.md`
- `Papers/` → `Papers/AGENTS.md`
- `References/` → `References/AGENTS.md`

---

## Core Principles

- **AI creates drafts. Final judgment and editing are done by humans.**
- Always tag AI-generated notes with `#llm-draft`
- Always ask for user confirmation before overwriting or deleting existing notes
- `References/` is read-only — do not move or delete files
- When output contains speculation, mark it explicitly with `[Speculation]`
- Do not generate long text without instruction. Follow **propose → confirm → execute** order
- Maintain the one-note-one-idea (Atomicity) principle
- When discussing knowledge, append one "next question" at the end of the response. Omit this during task execution

---

## Operations

- Ingest — Source ingestion: `rules/workflows.md#ingest`
- Promote — Create permanent notes: `Permanent/AGENTS.md`
- Wiki-Update — Update knowledge integration pages: `Permanent/AGENTS.md`
- Paper-Work — Paper writing management: `Papers/AGENTS.md`
- PaperDesk — Paper search, reading, review, survey, and evidence checks: `rules/workflows.md#paperdesk`
- Lint — Vault health check: `rules/lint.md`
- Probe — Proactive inquiry: `rules/workflows.md#probe`
- Connect — Serendipity exploration: `rules/workflows.md#connect`
- Remember — Save discussion to memory: `rules/workflows.md#remember`

---

## PaperDesk Overview

Use PaperDesk for paper search, reading, peer-review simulation, cross-paper surveys, and scientific evidence checks.
Detailed mode selection and execution scope are defined in `rules/workflows.md#paperdesk`.

- Mode A / read: Read and integrate one external paper into the Vault
- Mode B / review: Critically evaluate the user's own manuscript before submission
- Mode C / survey: Survey multiple papers across a topic or research question
- Mode D / evidence-check: Check the support status of a scientific claim

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
