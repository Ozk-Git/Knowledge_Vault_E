# Drafting

Load the structure of `Papers/[slug]/` and support manuscript writing by integrating claims, evidence, and literature.

---

## Writing Mode Selection

Confirm which mode to proceed with at the start:

| Mode | Flow | Best for |
|---|---|---|
| **Direct English Mode** | Outline confirmation → Generate body text in English | Those who want to think directly in English |
| **Native Language-first Mode** | Organize content in the user's L1 → L1 draft → Convert to academic English | Those who prefer to fix the logic in their native language first |

If no preference is specified, proceed in Direct English Mode.
If Native Language-first Mode is selected, ask the user which language to use as L1 (e.g., Japanese, Chinese, Spanish, French, German, Korean, etc.) before proceeding.

---

## Style and Terminology Consistency

If `research-voice.md` exists at the Vault root, load it and apply:
- Preferred sentence patterns and expression styles
- Terminology to standardize
- Expressions to avoid

If `research-voice.md` does not exist, write in default academic English style (recommended to create: see `templates/research-voice.md`).

---

## Principles

- Use the claim tree in `01_claims.md` as the backbone of the manuscript
- Do not write claims in the body text that have no evidence in `02_evidence.md`
- Do not leave bullet points in the final manuscript (acceptable only at the outline stage)
- **Output language**: Manuscript body in English. Dialogue with user in English
- Express evidence strength rather than asserting ("suggest" / "indicate" / "is consistent with")
- Always cite numerical values and statistics from actual files in `results/` — do not rely on memory or speculation

---

## Process

### Stage 0 — Organize Content in L1 (Native Language-first Mode only)

Write out the main points of each section in the user's L1 and confirm with the user.
Proceed to Stage 1 once the content is settled.

### Stage 1 — Outline Confirmation

When a section to write is specified, collect and present the following:

1. Relevant claims (C-XX) from `01_claims.md`
2. Relevant evidence / figures (E-XX) and statistics from `02_evidence.md`
3. Citation candidates from `Literature/` (including zotero_key)
4. Relevant gaps (G-XX) from `03_gaps.md` (to use as limitations)

Confirm the outline with the user and obtain approval before proceeding to Stage 2.

### Stage 2 — Body Text Generation

**Direct English Mode**: Convert the outline directly into English prose.
**Native Language-first Mode**: First generate a draft in the user's L1; after user confirmation, proceed to Stage 3.

Rules for converting to English prose:

- Figure and table references: `(Fig. X)` / `(Table X)` format
- Citations: Insert as `[zotero_key]` placeholders
  - If Zotero MCP is available, convert to the journal-specified format
- Limit each paragraph to one argument
- Balance passive and active voice to avoid monotony

### Stage 3 — Academic English Conversion (Native Language-first Mode only)

Convert the Stage 2 L1 draft to academic English:
- **Do not translate literally**: Rather than mapping L1 sentence structure directly to English, rewrite the same meaning using natural academic English expression
- Apply sentence patterns, terminology, and prohibited expressions from `research-voice.md`
- Choose expressions appropriate to evidence strength ("demonstrate" > "indicate" > "suggest" > "imply")
- After conversion, ask the user to confirm and refine any unnatural passages through dialogue

---

## Section-Specific Guidelines

### Abstract
Check the target journal in `00_overview.md`.
Select structured (Background / Objective / Methods / Results / Conclusion) or unstructured format per journal requirements.
Place the top-level Claim from `01_claims.md` as the core expressed in one sentence.

### Introduction
1. Current state and gap in the field (from `Literature/` and `03_gaps.md`)
2. Purpose of this study (from `00_overview.md`)
3. Preview of the primary claim (top-level Claim from `01_claims.md`)

### Methods
- Reference `protocols/` procedure files as the canonical source
- Do not omit information necessary for reproducibility (reagents, instrument models, software versions, statistical methods)
- If animal experiments are included, comply with the ARRIVE 2.0 guidelines
- Statistics: State the rationale for the test chosen, significance level, and how sample size was determined

### Results
- Arrange evidence from `02_evidence.md` in logical order (following the flow of claims)
- Do not mix results and interpretation (interpretation goes to Discussion)
- Write in the order figures and tables are referenced
- State numerical values as mean ± SD / SEM and always include n

### Figure Legends

Create a legend for each figure and table:
- Make each legend self-contained so the figure can be understood without referring to the body text
- Include `n =` (sample size), error bar definition (SD / SEM / 95% CI), and statistical significance threshold (* p < 0.05, etc.)
- Cross-check against files in `results/` and descriptions in `02_evidence.md`

### Discussion
1. Revisit primary claims with evidence strength
2. Comparison with prior work (from `Literature/`)
3. Significance of this study
4. Limitations (use unresolved items from `03_gaps.md`)
5. Future directions (from `#open-question`)

---

## Reporting Guidelines

Refer to the following by research design:

| Design | Guideline |
|---|---|
| Animal experiments | ARRIVE 2.0 |
| Observational studies | STROBE |
| Systematic review / meta-analysis | PRISMA |
| Clinical trials | CONSORT |
| General experimental papers | IMRAD |

---

### Stage 4 — Polishing (all modes)

Polish the completed draft from Stage 2 or 3 overall. Do not change content — focus on **readability and expression quality**:

- **Flow**: Check transitions between paragraphs and fix abrupt shifts
- **Tense and voice consistency**: Standardize tense (past/present) and balance passive/active voice
- **Remove redundancy**: Remove expressions that add no meaning ("It is important to note that..." / "As mentioned above...")
- **Nearby repetition**: Rephrase places where the same word appears in close proximity
- **Match expression strength to evidence**: Adjust overconfident statements to appropriate strength ("demonstrate" ↔ "suggest")
- **Final check of prohibited expressions in `research-voice.md`**

After polishing, save as `drafts/v[n]-polished.md`.

---

## Return to Vault

- New insights arising during writing → propose returning to `Permanent/`
- Claims that need updating due to writing → propose revising `01_claims.md`
- After writing, save as `drafts/v[n].md` and update the phase in `00_overview.md`
