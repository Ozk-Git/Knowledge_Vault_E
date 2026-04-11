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
