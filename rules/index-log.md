# Index and Log Rules

Management rules for `index.md` and `log.md`.

## index.md

`index.md` is managed by AI. Maintain it with the following structure:

```markdown
# Vault Index
Last updated: YYYY-MM-DD

## Statistics
- Permanent/: XX notes (of which #wiki: XX, #llm-draft: XX)
- Literature/: XX notes
- References/: XX items
- Inbox/ unprocessed: XX / Clippings/ unprocessed: XX

## Permanent/ — By Category
### [Category Name]
- [Note title](relative/path.md) — one-line summary

## Papers/ — Active Papers
| Slug | Phase | Next Action |
|---|---|---|
| [paper-slug] | [drafting/under review/etc.] | [what to do next] |
```

## log.md

- Treat `log.md` as an append-only operation history
- Format: `## [YYYY-MM-DD] {Operation} | {Content}`
- Record every agent's operations so that work can be continued across sessions
