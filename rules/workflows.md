# Workflows

Detailed procedures for operations defined in AGENTS.md.

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
