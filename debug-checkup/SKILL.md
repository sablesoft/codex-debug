---
name: debug-checkup
description: Verify diagnosis hypotheses through targeted runtime observations using the smallest viable adapter workflow.
---

# Purpose

Check a limited hypothesis set through focused runtime probes rather than broad step-by-step debugging.

At the current implementation stage, this skill's concrete responsibility is:

- determine which adapter is needed
- check whether that adapter is actually available for use
- stop early with a clear report when no suitable adapter is available yet

# Read before acting

- `references/entrypoint_schema.md`
- `references/hypothesis_schema.md`
- `references/adapter_selection.md`
- `adapters.yaml`
- `templates/checkup_report_template.md`
- `adapters/php-xdebug/README.md`
- `adapters/node-inspector/README.md`

# Behavior

1. Read the available diagnosis result and extract the hypotheses worth checking.
2. Decide whether the requested runtime question can be automated safely and usefully.
3. Select the smallest fitting adapter for the host project's runtime.
4. Read `adapters.yaml` and use it as the source of truth for adapter status.
5. Check whether the selected adapter is actually available for use in the current host project and current implementation stage.
6. If no suitable adapter is selected, or the selected adapter is not available, stop immediately and prepare a report that explains:
   - which adapter was expected
   - why it was selected
   - what `adapters.yaml` says about its status
   - why it is unavailable or not ready
   - what the user can do next
7. If the project-root `tmp/` directory is available and writable, write the checkup report there under `tmp/codex-debug/`.
8. If the project-root `tmp/` directory is unavailable, write the report to a system temporary directory instead.
9. Always duplicate the checkup result in the console response and include a clickable link or clear path to every generated report.
10. Do not proceed into real runtime observation collection until adapter execution support is implemented.

# Constraints

- do not run a checkup when the diagnosis already resolves the issue confidently
- do not use runtime stepping as the default exploration strategy
- do not collect broad context "just in case"
- do not let adapters decide the business meaning of the bug
- do not leave temporary execution artifacts outside `tmp/codex-debug/` unless required by the tool
- do not fail just because the project-root `tmp/` directory is unavailable; fall back to a system temporary directory
- do not generate a report without also summarizing it in the console response
- do not pretend that adapter execution already works when the current implementation can only select and validate adapter availability
- do not infer adapter readiness from folder presence alone; use `adapters.yaml` as the status source of truth

# Output

1. selected adapter decision
2. adapter availability status
3. checkup report in Markdown
4. console summary plus report locations
