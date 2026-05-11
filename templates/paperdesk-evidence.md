# PaperDesk — Evidence Check (Mode D)

Use this mode to quickly check whether scientific claims in biology, medicine, informatics, physics, or related fields are supported by existing research.

**Use case**: The user asks whether there is scientific evidence for a claim, whether a statement is supported by papers, or whether a claim is safe to include in an article or manuscript.

Mode D does not automatically create Literature notes or run Ingest.
Only propose Vault integration at the end when it is useful.

---

## Shared Principles

- **Accuracy first**: minimize hallucination
- **State unknowns**: if a paper does not report something, say "not reported"
- **Separate evidence levels**: distinguish observational studies, intervention studies, RCTs, meta-analyses, and guidelines
- **Avoid overclaiming**: for medical, health, financial, or other high-stakes domains, do not turn evidence into direct personal advice
- **Output language**: reason internally in English and answer the user in English unless instructed otherwise

---

## Step 0 — Decompose the Claim

Break the user's question into testable scientific claims.

When useful, specify:

- Population
- Intervention or exposure
- Comparison
- Outcome
- Timeframe

---

## Step 1 — Primary Check with Consensus

**Use Consensus MCP as the main entry point.**

Convert the claim into a short English research question.
When reading results, check:

- Whether supporting papers are numerous
- Whether contradictory papers exist
- Study type: RCT, meta-analysis, observational study, review, guideline, etc.
- Whether the population and conditions match the user's context
- Whether the effect size and outcome are practically meaningful

Do not treat Consensus output as the final answer by itself. Use Step 2 when primary literature verification is needed.

---

## Step 2 — Auxiliary Search and Primary Literature Verification

Use these sources as needed:

| Source | Use |
|---|---|
| PubMed | Biomedical primary literature, reviews, and guidelines |
| Semantic Scholar | Cross-disciplinary related papers and citation context |
| Zotero | Papers already stored by the Vault user |
| OpenAlex | OA papers and metadata completion |

Evidence priority:

1. Systematic reviews / meta-analyses
2. Guidelines / professional society statements
3. RCTs / intervention studies
4. Prospective cohorts
5. Cross-sectional studies / case reports
6. Animal studies / in vitro studies / mechanistic hypotheses

---

## Step 3 — Classify the Support Status

Classify the conclusion as one of:

| Classification | Meaning |
|---|---|
| Supported | Multiple high-quality studies consistently support the claim |
| Limited support | Some evidence exists, but population, condition, or effect size is limited |
| Mixed evidence | Supporting and non-supporting studies coexist |
| Insufficient evidence | Direct studies are scarce or low quality |
| Nearly unsupported | Major studies do not support the claim or the claim is likely overstated |

---

## Step 4 — Output Format

```md
## Conclusion

Classification: Supported / Limited support / Mixed evidence / Insufficient evidence / Nearly unsupported

Write the conclusion in 1–3 sentences.

## Evidence

- Summarize representative studies, reviews, or guidelines with study type and population
- If Consensus was used, summarize the overall pattern visible in the results
- Add primary literature checked via PubMed / Semantic Scholar / Zotero when needed

## Caveats

- Population differences
- Effect size
- Study design limitations
- Wording to avoid in articles or manuscripts

## Safer Wording

If the claim is intended for an article or manuscript, propose wording that is scientifically defensible.
```

---

## Step 5 — Vault Integration Proposal

Only propose additional work when:

- The evidence will likely be referenced again
- The evidence supports a claim in an article or `Papers/`
- Multiple papers deserve full Literature note treatment

Possible proposals:

- Create a `Literature/` evidence note
- Add the evidence to `Papers/[slug]/02_evidence.md`
- Switch to Mode C / survey for a cross-paper literature synthesis

