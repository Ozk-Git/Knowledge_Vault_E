# Workflows

Detailed procedures for operations defined in AGENTS.md.

## Session Start

**Trigger**: "Start a session" / "Please start the session"

1. Read `index.md` to get an overview of the entire Vault
2. If actual file counts or update status matter, verify the real directory rather than trusting `index.md` blindly
3. Check the last 5 entries in `log.md` to identify tasks carried over from the previous session
4. If `log.md` records appear insufficient, refer to actual files or Git history as needed
5. Based on the information below, propose up to 3 tasks to tackle this session:
   - Number of unprocessed items in `Inbox/` and `Clippings/`
   - Notes tagged `#llm-draft` left untouched for more than 2 weeks
   - Unresolved items in `Papers/*/03_gaps.md` (`status: open / in-progress`)
   - Carry-over tasks from `log.md`
6. Run Probe and include the results in the session-start report
7. Report the current Vault status

## Session End

**Trigger**: "End the session" / "Please end the session"

1. Update `index.md` as a derived summary, to the extent necessary
2. Append major changes and decisions to `log.md`
   Format: `## [YYYY-MM-DD] {Operation} | {Content}`
3. If new questions or half-formed ideas emerged, propose adding a memo to `Inbox/`
4. Summarize the key points of this session's work in 3 lines or fewer

## Ingest — Source Ingestion

Targets: unprocessed files in `Clippings/`, paper PDFs and books under `References/`, and memos in `Daily/`.

Use the appropriate prompt based on source type:

- Paper PDF under `References/papers/`: apply `templates/paperdesk-read.md`
- Peer-review simulation of the user's own paper: apply `templates/paperdesk-review.md`
- Books and other sources under `References/books/`, `Clippings/`, or `Daily/`: follow `Literature/AGENTS.md`

## PaperDesk

PaperDesk mode selection depends on the user's request granularity.
The root `AGENTS.md` only provides the overview; detailed execution scope is managed here.

| Mode | Use | Main artifact |
|---|---|---|
| Mode A / read | Read and integrate one external paper | `templates/paperdesk-read.md`, `paperdesk-read` skill/agent |
| Mode B / review | Critically evaluate the user's own manuscript | `templates/paperdesk-review.md`, `paperdesk-review` skill |
| Mode C / survey | Survey multiple papers across a topic | `templates/paperdesk-survey.md`, `paperdesk-survey` agent |
| Mode D / evidence-check | Quickly check whether a scientific claim is supported | `templates/paperdesk-evidence.md`, `paperdesk-evidence` skill |

### Mode Selection Principles

- If a specific external paper is given, default to Mode A
- If the request is manuscript review, peer-review simulation, or critical evaluation, default to Mode B
- If the request concerns a theme, question, field, or multiple papers, default to Mode C
- If the user asks whether a scientific, health, or research claim has evidence or is supported, default to Mode D
- If the user only asks for search or candidates, stop after candidate presentation
- If the user asks for survey, synthesis, gaps, consensus, or contradictions, proceed through reading and integration as needed

### Mode C — survey

Mode C is a subagent orchestrator.
It spawns `paperdesk-read` subagents for individual papers and integrates the literature landscape.

Explicit requests for "PaperDesk Mode C", "survey", or "cross-paper survey" should be treated as requests for subagent orchestration.

### Mode D — evidence-check

Mode D checks the evidence behind scientific claims.

Typical requests:

- "Is there scientific evidence for X?"
- "Is this claim supported by papers?"
- "Check the evidence for the relationship between X and Y"
- "Can I safely include this claim in an article or manuscript?"

Basic policy:

- Use Consensus MCP as the main entry point
- Use PubMed / Semantic Scholar / Zotero as needed to verify primary literature
- Classify conclusions as supported / limited / mixed / insufficient evidence
- Avoid overclaiming in medical, health, financial, or other high-stakes domains
- Do not automatically create Literature notes or Ingest records; propose Vault integration only when useful

## Probe — Proactive Inquiry

Run automatically at session start.

- Search recently Ingested notes for contradiction, complementarity, or extension relationships with existing Permanent notes
- Flag `status: confirmed` Claims whose supporting evidence appears thin
- From `#open-question` notes, suggest ones that existing knowledge may already answer
- Highlight 1–2 long-neglected Permanent notes and prompt connection with recent knowledge

## Remember — Save Discussion to Memory

**Purpose**: Save design decisions, background context, and judgments made during a session to the Vault so they can be reliably carried over across devices and AI agents.

**Procedure**:

1. Organize decisions, design rationale, and background from the current session
2. Determine the save location:
   - Content related to a specific directory's work → save in a `context/` folder within that directory (e.g., `Papers/slug/context/design-decisions.md`)
   - Content spanning the entire Vault or multiple directories → append to `rules/session-memory.md`
3. Record in the following format:
   ```
   ## [YYYY-MM-DD] {Topic}
   ### Decisions
   ### Background and Rationale
   ### Future Direction
   ```
4. Write in plain Markdown that any AI agent can interpret (avoid agent-specific syntax)
5. Record the save location and summary in `log.md` (format: `## [YYYY-MM-DD] Remember | {save location} — {summary}`)

---

## Connect — Serendipity Exploration

- Search for unexpected connections between Permanent notes older than 2 weeks and recently added notes
- Present potential relationships between isolated notes
- Limit output to a list of candidates — the user decides whether to adopt them
