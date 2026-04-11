# Submission

Support final pre-submission preparation. Format the manuscript according to the target journal's submission requirements,
and create supplementary materials and a cover letter.

---

## Step 0 — Journal Selection Support (if target journal is not yet determined)

Run this step when `00_overview.md` does not yet have a target journal.

### 0-1. Survey Candidate Journals

Collect candidates in the following order:

1. **Survey journals publishing similar papers**: Search PubMed MCP / Consensus MCP for papers on the same topic and identify their publication venues
2. **SCImago**: Retrieve field-specific quartile (Q1–Q4) and SJR metrics via WebFetch
3. **Journal official site**: Retrieve Aims & Scope via WebFetch and assess fit with this study

### 0-2. Credibility Check (Screening for Predatory Journals)

For each candidate journal, check the following and exclude or flag any with issues:

**Required checks**

| Check item | Method | Warning condition |
|---|---|---|
| PubMed indexing | Search journal name via PubMed MCP | Not indexed → ⚠️ Caution |
| Scopus indexing | Confirm listing in SCImago | Not listed → ⚠️ Caution |
| DOAJ (for OA journals) | Search `doaj.org` via WebFetch | Not registered → ⚠️ Caution |

**Detection of suspicious signals**

Retrieve Aims & Scope and submission guidance from the official site via WebFetch and detect:

- Explicitly stated unusually short review periods ("results within XX days")
- Language implying acceptance is guaranteed upon payment
- Unable to verify editorial board members or affiliations
- Publisher or contact information unclear

If any of the above applies, explicitly state **"Possible predatory journal"** and do not recommend submission.

### 0-3. Compare and Present Candidates

Present only journals that pass the credibility check in the following table:

| Journal | Quartile | PubMed/Scopus | DOAJ | Scope Fit | OA Option |
|---|---|---|---|---|---|

- Record Impact Factor only if stated on the official journal site
- Final journal selection is the user's decision

### 0-4. Record After Selection

Record the selected journal in the target journal field of `00_overview.md` and proceed to Step 1.

---

## Principles

- Use the target journal information in `00_overview.md` as the canonical reference
- Obtain submission requirements from the journal's official page (ask the user to provide the URL, or retrieve via WebFetch)
- Present revision proposals for any non-compliance, and execute after user confirmation
- **Output language**: Manuscript and cover letter in English. Dialogue with user in English

---

## Step 1 — Review Submission Requirements

Confirm the target journal from `00_overview.md` and investigate / organize the following:

| Item | Content |
|---|---|
| Word count limits | Upper limits for body text, Abstract, and title |
| Figure / table count | Upper limits for main text and supplementary materials separately |
| Figure format | Resolution (dpi), file format (TIFF / EPS / PDF, etc.) |
| Reference style | Vancouver / APA / journal-specific |
| Supplementary material rules | Accepted file formats, size limits |
| Data sharing policy | Requirements for sharing raw data and code |
| Other | Ethics approval, conflicts of interest, author contribution statement format |

Present the findings as a table to the user.

---

## Step 2 — Format the Manuscript

Adjust the latest version in `drafts/` to meet submission requirements:

- **Word count check**: If over the limit, propose candidate passages for reduction
- **Figure / table count check**: If over the limit, propose candidates for moving to supplementary materials
- **Reference format**: If Zotero MCP is available, convert to the specified format
- Save formatted manuscript as `drafts/v[n]-submission-ready.md`
- After word count reduction or sentence splitting / merging, check the flow and consistency around the changed passages (full polishing is not required — only changed passages)

---

## Step 3 — Create Supplementary Materials

Propose a structure for supplementary materials from `results/`, `experiments/`, and `protocols/`:

**Candidates for supplementary materials**
- Additional data and figures omitted due to figure count limits in the main text
- Detailed statistical results (main text contains only summary)
- Detailed experimental protocols (from `protocols/`)
- Repository links / DOIs to raw data
- Repository information for analysis code (from `scripts/`)

**Data and code sharing**
Per the journal's data sharing policy, add references to repositories (GitHub, Zenodo, Dryad, etc.) where data and code will be made public.

Present the proposed structure, then create `drafts/supplementary.md` after user confirmation.

---

## Step 4 — Check / Create Figure Legends

For all figures and tables in `results/`, verify:

- Does each figure / table have a legend?
- Is each legend self-contained (can the figure be understood without reading the body text)?
- Does each legend include statistical notation (n, error bar definition, significance threshold)?
- Propose creating any missing legends based on evidence descriptions in `02_evidence.md`

---

## Step 5 — Write Cover Letter

Collect the following information and write the cover letter:

**Information to gather**
- Editor's name (if unknown, use "Dear Editor" format)
- Primary contribution of this study (from top-level Claim in `01_claims.md`)
- Significance to the field (from `00_overview.md`)
- Presence / absence of conflicts of interest and ethics approval
- Suggested reviewers (optional)
- Excluded reviewers (optional)

**Cover letter structure**

```
Dear Dr. [Editor] / Dear Editor,

[Paragraph 1] State the manuscript title, authors, and intention to submit to the journal.
Describe the primary finding(s) of the study in 1–2 sentences.

[Paragraph 2] Explain the significance of the research and its fit with the journal's scope.
Briefly show the current state of the field and the gap this study fills.

[Paragraph 3] Include standard declarations:
- The manuscript is unpublished and not under simultaneous review elsewhere
- All authors have reviewed and approved the content
- Conflicts of interest (state presence or absence)

Sincerely,
[Author name]
```

---

## Step 6 — Pre-Submission Checklist

Check and report the following:

- [ ] Does every Claim in `01_claims.md` have corresponding Evidence in `02_evidence.md`?
- [ ] Are there no unresolved major issues (Major) remaining in `03_gaps.md`?
- [ ] Does every figure / table have a self-contained Figure legend?
- [ ] Are word count and figure / table count within submission requirements?
- [ ] Is the reference format consistent?
- [ ] Are author information, acknowledgments, ethics approval, and conflicts of interest stated?
- [ ] Is there a reference to data / code sharing (if the policy requires it)?
- [ ] Is the cover letter complete?
- [ ] Are supplementary materials in order?

Present the checklist results and, if any items are incomplete, propose how to address them.
