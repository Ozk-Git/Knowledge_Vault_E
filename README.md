# Knowledge Vault — AI-Integrated Knowledge Maturation System for Researchers

A unified system for knowledge management, paper writing, and research output,
integrating the design philosophies of Zettelkasten, LLM-Wiki, and obsidian-mind.

Compatible with Claude Code, Gemini CLI, and Codex — use whichever AI agent you prefer.
- Claude Code: Requires paid account
- Codex: Requires paid account
- Gemini CLI: Free to use

Recommended setup: use this as an Obsidian Vault with the ACP plugin and an AI CLI.
https://github.com/RAIT-09/obsidian-agent-client

---

## This System Is Not a "Note-Taking App"

Unlike ordinary note-taking apps (Obsidian, Notion), what makes this different is that **an AI assistant runs in the background — one that understands your intent and actually reorganizes your files**.

- **You**: Write notes freely, then tell the AI: "organize this," "find evidence for this claim."
- **AI**: Reads your instructions, loads files, moves them to the right places, creates links, and updates the index (`index.md`).
- **Division of labor**: **Humans handle creative thinking; AI handles tedious organization, management, and retrieval.**

---

## Quick Start

### 1. Setup

Click **"Use this template" → "Create a new repository"** on the GitHub page to create your own repository.
This way, the remote is yours from the start — no extra steps needed to save your notes.

> **If you want to back up personal notes to GitHub, a Private repository is recommended.**
> Making it Public will expose your research content and unpublished data.

Then clone your new repository using one of the methods below.

#### 1-1. VS Code (Recommended)

No GitHub CLI required — clone directly from the GUI.

1. **Launch VS Code**
2. **Click the "Source Control" icon in the left sidebar**
   - It's the branching icon (Y-shape) in the left icon bar.
3. **Click "Clone Repository"**
   - Shown at the top of the Source Control panel.
4. **Paste your repository URL and press Enter**
   ```
   https://github.com/YOUR_USERNAME/REPO_NAME.git
   ```
5. **Select a destination folder**
   - In the file dialog, choose the directory where you want to place Knowledge Vault.
   - When a confirmation dialog appears, click "Open" to open the cloned folder in VS Code.

#### 1-2. Terminal

```bash
git clone https://github.com/YOUR_USERNAME/REPO_NAME.git
cd REPO_NAME
```

### 2. Launch an AI Agent

Launch your preferred AI agent (Claude Code, Gemini CLI, or Codex) in this directory.

> ⚠️ **Gemini Code Assist (VS Code extension) is not supported.** The Agent mode's file access limitations prevent the session start procedure from completing. Use Gemini CLI instead.

If you prefer Obsidian, install the ACP plugin:
https://github.com/RAIT-09/obsidian-agent-client

### 3. Start a Session (Important)

After starting a chat, begin by saying:
> **"Report the current status of the Vault."**

**Why this matters**: This causes the AI to load the Vault's rules (`AGENTS.md`), transforming it into a dedicated assistant that knows exactly where each type of content belongs.

---

## Concept

The goal is not merely to accumulate information, but to **mature it into knowledge and connect it to output**.

```
Capture → Knowledge → Output
```

The AI drafts; humans judge and edit. This division of labor makes your knowledge network grow richer with compound interest the more you use it.

---

## Directory Structure

```
vault/
├── AGENTS.md               Shared operation rules for all agents
├── CLAUDE.md               Claude Code settings (MCP, paper operations)
├── GEMINI.md               Gemini CLI settings (daily operations, bulk processing)
├── index.md                Vault-wide map (AI updates continuously)
├── log.md                  Processing history, append-only (AI updates continuously)
│
├── Inbox/                  Drop zone for quick thoughts and rough notes
├── Clippings/              Temporary storage for web articles and SNS saves
├── Daily/                  Daily reflections, experimental observations
│
├── Literature/             Literature and source notes (AI drafts)
├── Permanent/              Knowledge core (permanent notes + Wiki integrated pages)
│
├── References/             Permanent storage for paper PDFs and books (read-only)
│   ├── papers/             Organize with sub/sub-sub directories as needed
│   └── books/              Organize with sub/sub-sub directories as needed
│
├── Papers/                 Paper writing workspace
│   ├── AGENTS.md           Detailed paper writing rules
│   └── [paper-slug]/
│       ├── 00_overview.md
│       ├── 01_claims.md
│       ├── 02_evidence.md
│       ├── 03_gaps.md
│       └── drafts/
│
├── templates/              Note templates and AI prompts
│   ├── literature-note.md
│   ├── permanent-note.md
│   ├── paper-overview.md
│   ├── inbox-note.md
│   ├── daily-note.md
│   ├── paperdesk.md        Paper reading / review simulation (all CLIs)
│   ├── drafting.md         Paper drafting support
│   ├── revision.md         Revision and response to reviewers
│   └── submission.md       Pre-submission checklist and cover letter
│
└── .claude/
    └── agents/
        ├── paperdesk.md    Claude Code wrapper (launch with @paperdesk)
        ├── drafting.md     Claude Code wrapper (launch with @drafting)
        ├── revision.md     Claude Code wrapper (launch with @revision)
        └── submission.md   Claude Code wrapper (launch with @submission)
```

---

## Knowledge Flow and AI Collaboration Workflow

You can give instructions in plain language. The AI follows the rules in `AGENTS.md` autonomously.

### Step 1: Ingestion (Ingest)

Drop files into the appropriate location based on content type:
- **`Inbox/`**: Sudden ideas, rough notes.
- **`Clippings/`**: Web articles or SNS content you want to read later.
- **`Daily/`**: Daily experiment notes, meeting records, end-of-day reflections.
- **`References/`**: Paper PDFs and book files (permanent storage; multi-level subdirectories allowed under `papers/` and `books/`).

After dropping files, tell the AI: **"Organize unprocessed files."** The AI will summarize the content, save it to `Literature/` (literature notes), and suggest connections to existing knowledge. For paper PDFs, PaperDesk Mode A is applied.

### Step 2: Promotion to Knowledge (Promote)

Transform summarized content into lifetime "personal knowledge."
- **Example instructions**: "Turn this literature note into a permanent note." "Connect related notes."
- **What the AI does**: Creates minimal-unit notes (permanent notes) in `Permanent/`. **Creates links to existing notes with rationale**, and moves processed files.

### Step 3: Knowledge Systematization (Wiki-Update)

When fragmented knowledge accumulates, have the AI draw the big picture.
- **Example instructions**: "Summarize recent notes into a Wiki page." "Integrate knowledge about [concept name]."
- **What the AI does**: Cross-searches multiple notes. Creates a systematic "Wiki page (tagged `#wiki`)" **in `Permanent/`** and updates the knowledge map.

### Step 4: Output (Paper-Work)

Connect accumulated knowledge to papers and research outputs.
- **Example instructions**: "Start a new paper project [slug]." "Find evidence in the Vault for this claim."
  - **What the AI does**: Auto-generates **numbered management files `00_`–`03_`** in `Papers/`. Links claims to supporting evidence (notes, code, data).

---

## Operations Reference

| Operation | Example Trigger | Description |
|---|---|---|
| **Ingest** | "Ingest this paper" | PDF/article → create Literature note, suggest Permanent connections |
| **Promote** | "Organize Inbox" | Inbox/Literature → create Permanent note, suggest links |
| **Wiki-Update** | "Integrate knowledge" | When ≥3 related notes accumulate, create integration page |
| **Paper-Work** | "Organize paper claims" | Manage claims / evidence / gaps, link to Permanent |
| **Paper-Lint** | "Run a health check on the paper" | Verify claim-evidence alignment, check open issues |
| **Lint** | "Run a Vault health check" | Report isolated notes, stale drafts, backlogged memos |

---

## Knowledge Application Examples

- **Turn experiment notes into paper evidence**: The AI promotes `Daily/` experimental results to `Permanent/` (as evidence) and links them to `02_evidence.md`.
- **Link analysis code to claims**: The AI tracks which figures (results) were generated by which code (scripts), supporting paper integrity.
- **AI as a "logic guardian"**: While writing, ask the AI "check for contradictions between claims and evidence" to maintain high-quality structure.
- **"LEGO bricks" for thinking**: Ask the AI "combine existing permanent notes to propose a new hypothesis" to induce serendipity.

---

## PaperDesk

When working with papers, use the dedicated multi-mode prompt (in `templates/paperdesk.md`) or simply **give instructions in natural language** — the AI responds as a world-class expert reviewer.

| Mode | Example Call | Description |
|---|---|---|
| **A. Reading Mode** | "Reading mode" / "Summarize this paper" | Read in Ochiai format → create Literature note → integrate into Vault |
| **B. Peer-Review Simulation** | "Review mode" / "Check before submission" | Unsparing critical evaluation → flag Desk Reject risks → update gaps.md |
| **C. Literature Survey** | "Survey mode" / "Survey related literature" | PubMed/Consensus search → Literature notes → thematic synthesis |

In Claude Code, launch with `@paperdesk`. For Gemini CLI and Codex, reference `templates/paperdesk.md` directly.

---

## Drafting & Submission Support

| Agent | Example Call | Description |
|---|---|---|
| **@drafting** | "Draft an Introduction" | Claims + evidence + literature → IMRAD-structured English draft |
| **@revision** | "Address reviewer comments" | Classify reviewer comments → Response letter → update claims/gaps |
| **@submission** | "Prepare for submission" | Journal formatting → cover letter → pre-submission checklist |

---

## Tag System

| Tag | Meaning |
|---|---|
| `#llm-draft` | AI-generated draft. Awaiting human review |
| `#wiki` | LLM-Wiki integrated page |
| `#paper-relevant` | Note connected to paper writing |
| `#open-question` | Unresolved question or item requiring further experiments |
| `#claim` | Idea in use or candidate as a paper claim |

---

## Tips and Caveats

### 1. Manual Editing Restrictions
`index.md` and `log.md` are automatically managed by the AI. Manually editing them can confuse the AI — let it handle updates.

### 2. What Removing the `#llm-draft` Tag Means
All AI-generated notes carry the `#llm-draft` tag.
Removing this tag is not just a chore — it is **a responsible declaration that "I have approved this knowledge."** Rather than leaving AI output as-is, adjust it in your own words and then remove the tag. This "extra step" transforms your Vault from "merely an AI output destination" into "your genuine intellect."

### 3. Request a "Health Check" (Lint)
As notes accumulate, ask the AI: **"Run a Vault health check (Lint)."**
- Discover "isolated notes" with no incoming links
- Flag "logical contradictions" lurking across multiple notes
- List abandoned `#llm-draft` (unreviewed) notes

This keeps your knowledge base fresh.

### 4. Use Each Agent's Strengths

- **Claude Code**: Excels at logical reasoning. Ideal for paper **writing** and **complex logic organization**.
- **Gemini CLI / Gemini Code Assist**: Huge context window is its weapon. Strong for bulk PDF processing and Vault-wide searches.
- **Codex**: General operations and script execution; great for routine maintenance.

---

## Per-Directory Rules

| Directory | Rules File | Content |
|---|---|---|
| `Literature/` | `Literature/AGENTS.md` | Ingest procedure, Interactive Deepening Mode, Promote bridging |
| `Permanent/` | `Permanent/AGENTS.md` | Promote, Wiki-Update, Lint |
| `Papers/` | `Papers/AGENTS.md` | Claims, evidence, gaps management, Paper-Lint, experiment cycle |
| `References/` | `References/AGENTS.md` | Reference ID management, MCP integration, Zotero API |

---

## VS Code / Obsidian ACP Integration

By recording relative path links to data analysis directories in `Papers/[slug]/02_evidence.md`,
you can review analysis results in VS Code while referencing Vault knowledge notes.

```markdown
| Claim ID | Evidence Summary | Permanent Link | Analysis Result | Analysis Code | Protocol | zotero_key |
|---|---|---|---|---|---|---|
| C-01 | GR66 responds to furanocoumarin | [GR66 Receptor](../../Permanent/GR66-receptor.md) | ./results/fig1a.png | ./scripts/plot.py | ./protocols/tiprec_v3.md | Smith2024 |
```

When using the Obsidian ACP plugin, you can seamlessly transition from `Inbox/` operations to paper operations within the same session (no new session needed).
Sub-directory `AGENTS.md` files are automatically loaded before operating in that directory.

---

## Design Background

This system integrates three design philosophies:

**Zettelkasten** — One note, one idea; written in your own words; knowledge network via bidirectional links

**LLM-Wiki** — AI-continuously-updated persistent knowledge base

**obsidian-mind** — Session start/end hooks; context carryover via Memories

---

## Acknowledgements

This system's design is inspired by the following ideas:

**obsidian-mind** by breferrari
An Obsidian vault template for engineers who use Claude Code as a thinking partner.
https://github.com/breferrari/obsidian-mind
License: MIT

**katmer-code** by hkcanan
A collection of academic research skills for Claude Code.
https://github.com/hkcanan/katmer-code
License: MIT

The agent designs for journal matching, citation verification, and research gap analysis served as references for `submission.md` (Step 0), `paperdesk-review.md` (Steps 2 & 3), and `paperdesk-survey.md` (Step 4b).

**LLM Wiki** by Andrej Karpathy
A pattern for building personal knowledge bases using LLMs.
https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
(No explicit license stated. Cited here as attribution to the design concept.)

---

## License

MIT

This system is an original implementation inspired by the two ideas above.
It is not a direct copy of any code or documents; it is built by referencing the design concepts.
In accordance with obsidian-mind's MIT license, copyright notices are retained.
For Karpathy's gist, which has no explicit license, honest attribution is provided here.
