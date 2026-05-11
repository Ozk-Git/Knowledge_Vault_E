# Vault Architecture

## Information Flow

```
[External Sources]
  Web articles / SNS  → Clippings/    ← Temporary holding. Moved to Done/ after processing
  Paper PDFs          → References/   ← Permanent archive. Read-only
  Observations/memos  → Inbox/ Daily/ ← Drop in unprocessed
                           ↓ Ingest operation
                   Literature/         ← Literature notes (AI drafts)
                           ↓ Promote operation
                   Permanent/          ← Knowledge notes (atomic ideas + Wiki integrations)
                           ↓
                       Papers/                           ← Output layer
                                    ↑
                   [Data analysis directory (outside Vault)]
                   Analysis results → relative path links in 02_evidence.md
```

## Papers/ Structure

```
Papers/[paper-slug]/
├── 00_overview.md   # Claims, target journal, current phase
├── 01_claims.md     # Claim tree
├── 02_evidence.md   # Evidence, Permanent links, analysis results, code correspondence table
├── 03_gaps.md       # Unresolved issues, items needing additional experiments
├── protocols/       # Experimental and analysis protocols
├── scripts/         # Analysis code
├── results/         # Analysis result summaries and figures
└── drafts/          # Manuscript drafts (also editable in VS Code)
```

## Directory Roles

### Clippings/

Temporary holding area for lightweight external sources: web articles, saved social media posts, etc.
Processed files are moved to `Clippings/Done/`.

### References/

Permanent archive for paper PDFs and books. **Do not delete. Do not move to Done/.**
Follow `References/AGENTS.md`.

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
