# Revision

Support writing a Response to Reviewers for actual peer-review comments,
and revising the manuscript and Vault accordingly.

---

## Principles

- Take reviewer comments seriously — respond with either revision or evidence-based rebuttal
- Stay calm and unemotional; rely on evidence and logic
- Cite line numbers from the manuscript for all changes
- Do not mark as complete until all Major Comments have been addressed
- **Output language**: Response letter in English. Dialogue with user in English

---

## Step 1 — Read and Classify Comments

When reviewer comments are received, classify them and present a summary:

| Type | Response Policy |
|---|---|
| **Agree and revise** | State the revision content and the relevant location |
| **Partially agree** | Separate the points of agreement and revision content from the points of disagreement with rationale |
| **Disagree** | Politely rebut using existing data and literature as the basis |
| **Additional experiments required** | Add to `03_gaps.md` and present an action plan or alternative |

Confirm the classification with the user before proceeding to Step 2.

---

## Step 2 — Draft Response Letter

Create the response in the following format:

```
Dear Dr. [Editor],

We thank the Editor and reviewers for their thorough evaluation of our manuscript
and their constructive comments. We have carefully addressed all concerns below.
Changes to the manuscript are indicated by line numbers in the revised version.

---

Reviewer [N]

Comment [N-X]: [Quote the reviewer comment]

Response: [Response body]
  - If agreeing and revising: "We agree with this concern and have revised..."
  - If rebutting: "We respectfully disagree. As shown in [Fig./Table X / reference]..."
  - If additional experiments were requested: "We appreciate this suggestion. [Feasibility and rationale]..."

Changes made: [Description of manuscript changes with line numbers. If no changes, state the reason]
```

**Response style guidelines:**
- Open each response with "We thank the reviewer for..."
- Even in rebuttal, begin with "We respectfully..." and avoid adversarial language
- When citing data: "As shown in Fig. X, ..." / "Consistent with [ref]..."

---

## Step 3 — Manuscript Revision

Once responses to comments are finalized:

1. Copy the current version in `drafts/` and create `drafts/v[n]-revised.md`
2. Leave the corresponding Comment ID as a comment at each change location (e.g., `<!-- R1-C2 -->`)
3. Update the phase in `00_overview.md` to "under revision"

---

## Step 4 — Update the Vault

After the response letter is complete:

- **`03_gaps.md`**: Change resolved comments to `Status: resolved` (do not delete)
- **`01_claims.md`**: Update claims that were changed or strengthened through the revision
- **`Permanent/`**: Return deepened understanding from the revision process with `#paper-relevant` tag
- **`log.md`**: Append `## [YYYY-MM-DD] Revision | [Journal name] Round [N] complete`

---

## When Additional Experiments Are Required

When a reviewer requests additional experiments:

1. Add `[G-XX] Reviewer request: [content]` to `03_gaps.md`
2. Start the experiment cycle (pre/post-experiment templates) in `Papers/[slug]/experiments/`
3. Once results are obtained, update `02_evidence.md` and reflect in the Response letter
4. If the experiment is not feasible, honestly explain the alternative answer using existing data or frame it as a task for a future paper
