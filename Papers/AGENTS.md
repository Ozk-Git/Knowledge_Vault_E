# Papers/AGENTS.md

Operating rules for paper writing workspaces.
In addition to the Vault-wide rules in `../AGENTS.md`, follow these rules within this directory.

---

## Directory Structure

```
Papers/
└── [paper-slug]/
    ├── 00_overview.md   # Claims, target journal, current phase
    ├── 01_claims.md     # Claim tree
    ├── 02_evidence.md   # Evidence, Permanent links, analysis results, code correspondence table
    ├── 03_gaps.md       # Unresolved issues, items needing additional experiments
    ├── protocols/       # Experimental and analysis protocols (procedures and version control)
    ├── experiments/     # Experiment logs (dated records with protocol references)
    ├── scripts/         # Analysis code (Python, R, Shell, etc.)
    ├── results/         # Analysis result summaries and figures
    └── drafts/          # Manuscript drafts
```

- `protocols/` and `experiments/` serve different roles. Procedures are canonical in `protocols/`. `experiments/` should only reference protocols — avoid duplicating content.

When starting a new paper project, prompt the user to create `[paper-slug]/00_overview.md` using `../templates/paper-overview.md`.

---

## Principles

- **Always pair claims with evidence**
  Do not write claims in `01_claims.md` without supporting evidence.
  Mark claims with insufficient evidence as `[evidence needed]`.
- **Do not erase unresolved items — keep them in `03_gaps.md`**
  When resolved, mark with strikethrough (`~~`) and record — do not delete.
- **Do not move or edit data outside the Vault**
  Only reference external data via relative-path links from `02_evidence.md`.
- **Return insights from papers to `../Permanent/`**
  Papers/ is the writing space. Permanent/ is where knowledge accumulates.

---

## Operation Definitions

### Starting a New Project

1. Use `../templates/paper-overview.md` to create `[slug]/00_overview.md`
2. Create empty files: `01_claims.md`, `02_evidence.md`, `03_gaps.md`
3. Add an entry to the Papers/ section of `../index.md`

### Adding and Organizing Claims (01_claims.md)

Record format:
```
## [C-XX] Claim Title
Content: (state the claim in one sentence)
Status: confirmed / under consideration / evidence needed
Related Evidence: E-XX, E-XX
```

- Show dependencies between claims hierarchically
- Do not mark work as complete while claims with `Status: evidence needed` remain

### Adding Evidence (02_evidence.md)

Record format:
```markdown
| ID | Evidence Summary | Permanent Link | Analysis Result / Figure | Analysis Code | Protocol | zotero_key |
|---|---|---|---|---|---|---|
| E-01 | ProteinX expression increases only under condition Y | [ProteinX Expression Regulation](../../Permanent/ProteinX-expression-regulation.md) | ./results/fig1a.png | ./scripts/plot_exp.py | ./protocols/exp_v2.md | Smith2024 |
```

- Always include a `Permanent Link`. If none exists, run the Promote operation first
- Use relative paths within `Papers/[slug]/` for `Analysis Result / Figure`, `Analysis Code`, and `Protocol`
- Reference large datasets outside the Vault using relative paths like `../../analysis/`
- Obtain and manage `zotero_key` via Claude Code + Zotero MCP
- When a PDF in `References/` is moved, use the `zotero_key` or `DOI` in `References/_index.md` to update the relative path

### Managing Unresolved Issues (03_gaps.md)

Record format:
```
## [G-XX] Unresolved Issue Title
Content: (what is missing)
Related Claim: C-XX
Action: (additional experiments, literature review, etc.)
Status: open / in-progress / resolved
```

- When resolved, change to `Status: resolved` — do not delete
- Reflect `Status: open / in-progress` items as `#open-question` in `../Permanent/`

### Health Check (Paper-Lint)

Check and report the following:

- Any claims with `Status: evidence needed` remaining in `01_claims.md`
- Whether analysis result paths in `02_evidence.md` actually exist
- Whether unresolved items in `03_gaps.md` are reflected as `#open-question` in `../Permanent/`
- Whether the phase in `00_overview.md` matches the actual file state
- Whether there is a mismatch between `drafts/` content and claims in `01_claims.md`
- For broken links to `References/`, re-identify via `zotero_key` / `DOI` in `References/_index.md`, and fix the relative path in `02_evidence.md` if found

### Experiment Cycle (experiments/)

1. Before experiment: Use `templates/pre-experiment.md` to confirm the plan and design weaknesses
2. During experiment: Record in `experiments/YYYY-MM-DD_xxx.md`
3. After experiment: Conduct interpretation dialogue using `templates/post-experiment.md`
4. Return: Feed insights from the interpretation back to `Permanent/` and update `01_claims.md` and `02_evidence.md`

### Returning Insights to Permanent/

Timing for returning insights generated during paper writing to Permanent/:

- When new data analysis results emerge
- When important concepts are clarified through a literature review
- When an unresolved item in `03_gaps.md` is resolved
- When understanding deepens through responding to reviewer comments

Use `../templates/permanent-note.md` when returning insights, and tag with `#paper-relevant`.

---

## Directory-Specific Additional Rules

No subdirectory-specific rules currently exist for this directory.

---

## Sample Project

`Papers/example-project/` is a sample for new users.
You may delete it when you begin actual work. It is tagged `#example`.
