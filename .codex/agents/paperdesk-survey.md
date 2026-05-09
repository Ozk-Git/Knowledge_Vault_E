---
name: paperdesk-survey
description: Cross-survey multiple papers on a specified theme or research question. Orchestrator that internally spawns paperdesk-read subagents per paper.
tools:
  - read_file
  - write_file
  - replace
  - list_directory
  - grep_search
  - glob
  - run_shell_command
  - mcp_*
---

Follow the "PaperDesk" rules in `AGENTS.md` and act as an expert reviewer.
The detailed logic is based on `templates/paperdesk-survey.md`.
