# References/AGENTS.md

Rules for managing materials under `References/`.
In addition to the Vault-wide rules in `../AGENTS.md`, follow these rules within this directory.

---

## Role of This Directory

Permanent archive for paper PDFs and books. **Do not delete. Do not move to Done/.**
This is fundamentally different from `Clippings/` (a temporary holding area).

- AI manages the correspondence table between reference IDs and current paths in `References/_index.md`
- When ingesting, create a literature note in `Literature/` while keeping the original PDF here
- Link here from `Papers/[slug]/02_evidence.md` using relative paths
- Subdirectories (e.g., `References/2025/`, `References/project-a/review/`) organized by year or project are optional
- When a PDF is moved, update its current path in `References/_index.md` as the canonical record

---

## Handling During Ingest

- **Paper PDFs**: May be placed anywhere under `References/`
  - Apply **Mode A (Reading)** in `templates/paperdesk.md`
- **Books and other materials**: May be placed anywhere under `References/`
  - Process into `Literature/` notes using the standard Ingest procedure

---

## Reference ID Management

### Role of References/_index.md

`References/_index.md` is not merely a list — it is a correspondence table between stable IDs and current paths.

- Use `zotero_key` as the primary key (Zotero internal key — 8-character alphanumeric string obtained via Zotero MCP or local API)
- Use `DOI` as the secondary key
- `DOI` may be left blank for materials without one (e.g., books)

### Update Format

When a paper PDF is added or processed under `References/`, update `References/_index.md` in the following format:

`| Current Path | zotero_key | DOI | Title | Author | Year |`

### Handling Moves

- When a PDF is moved within `References/`, identify the existing row using `zotero_key` or `DOI`, then update `Current Path`
- If the old path appears in `Papers/[slug]/02_evidence.md` or `Literature/` notes, and the file was successfully re-identified, update to the current path

### Handling Broken Links

- When a broken link to `References/` is detected, re-identify via `zotero_key` / `DOI` in `References/_index.md`
- If found, fix the link in the referencing note or `02_evidence.md`

---

## MCP Integration

> **Note**: Each MCP server requires a separate setup. When available, use the following tools for literature search and citation management.

### Available MCP Servers and Their Uses

- **PubMed MCP**: Keyword- and concept-based literature search in medicine and biology
- **Consensus MCP**: Evidence search and scientific claim verification
- **Scholar Gateway**: Broad academic paper exploration and metadata retrieval
- **Zotero MCP**: Citation key retrieval, library management, and reference list generation

### Retrieving Literature from Zotero Library

If you use Zotero, PDFs in your library can be used directly in the Vault.

**Connection methods (in order of preference)**

1. **Zotero MCP** (if installed): Search the library directly and retrieve metadata and PDF paths
2. **Zotero Local API** (no MCP needed — requires Zotero running): Access `http://localhost:23119/api/` via WebFetch. Enable "Allow other applications to communicate with Zotero" in Zotero preferences → Advanced → Allow other applications

**PDF Handling Policy**

| Use Case | Policy |
|---|---|
| One-time reference or reading | Read directly from the Zotero storage path. Do not copy to `References/` |
| Confirmed as a key reference for Papers/ | Copy to `References/` and register in `_index.md` |

Always obtain the PDF path from Zotero MCP or the local API before reading with the Read tool.
This works even if files are stored in a non-default location (e.g., when using ZotMoov or similar link-file managers) because the API returns the actual path. Never guess paths.

**Rules when reading**
When reading a paper PDF from Zotero, regardless of whether it is copied to `References/`:

1. Apply **Mode A (Reading)** in `templates/paperdesk.md`
2. Create a literature note at `Literature/[AuthorYear]-[keyword].md`. Use `zotero_key:` as the primary key instead of `source:`
3. Add an entry to `References/_index.md`. Record the actual path returned by the Zotero API as `Current Path`. Update the path if the file is later copied to `References/`

### Standard Citation Procedure

1. **Search**: Identify literature using Zotero library / PubMed / Consensus / Scholar Gateway
2. **Read**: Read the PDF directly or copy to `References/` and apply `paperdesk.md` Mode A
3. **Register**: Add to the library via Zotero MCP and obtain a unique citation key (Citekey)
4. **Record**: Add the citation key and relative path within `References/` to `Papers/[slug]/02_evidence.md`
5. **Output**: Generate a reference list in the specified journal format from Zotero MCP during writing
