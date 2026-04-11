# Lint Rules

Detailed criteria for Vault health checks.

## Check Items

- Detect and report orphaned notes (zero incoming links)
- Report notes with `#llm-draft` tag left untouched for more than 2 weeks
- Report items that have remained in `Inbox/` for more than 2 weeks
- Check whether contradictory statements span multiple notes
- Check whether `#open-question` items from `Papers/*/03_gaps.md` are reflected in `Permanent/`
- When broken links to `References/` are detected, re-identify and fix them following the rules in `References/AGENTS.md`

## Exclusions from Counts

- Hidden files (`.*`) and `.gitkeep`
- OS-generated files: `.DS_Store` (macOS), `Thumbs.db` / `desktop.ini` (Windows)
- Files under `Done/`
- Unprocessed item counts target **only visible files directly under** `Inbox/` and `Clippings/` (excluding the above)
- Orphan note definition: a `Permanent/` note with zero incoming relative-path links in `[...](...)` format
