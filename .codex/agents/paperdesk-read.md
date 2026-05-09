---
name: paperdesk-read
description: Read and deeply analyze a single paper by others, integrating it into the Vault. Pass the PDF path or DOI to start. Also used as a subagent spawned by paperdesk-survey.
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
The detailed logic is based on `templates/paperdesk-read.md`.
