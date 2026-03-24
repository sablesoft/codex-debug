---
name: debug-diagnosis
description: Analyze a code problem, localize likely causes, and decide whether runtime checking is actually needed.
---

# Purpose

Understand a bug before reaching for runtime instrumentation.

# Read before acting

- `references/entrypoint_schema.md`
- `templates/diagnosis_report_template.md`

# Behavior

1. Identify the reported symptom, reproduction context, and available entrypoint information.
2. Read the relevant host-project code around the suspected execution path.
3. Decide whether the issue can already be explained with high confidence from code and inputs alone.
4. If a direct diagnosis is not yet justified, generate a small set of concrete hypotheses that can be checked automatically.
5. For each hypothesis, define the minimal question, probe point, and data needed to confirm or reject it.
6. Write a user-facing diagnosis report to `tmp/codex-debug/` when that project-root directory is available and writable.
7. If the project-root `tmp/` directory is unavailable, write the diagnosis report to a system temporary directory instead.
8. Always duplicate the diagnosis result in the console response and include a clickable link or clear path to every generated report.

# Constraints

- do not jump into runtime debugging without first trying to reason from code and context
- do not produce more than five hypotheses in one pass
- do not leave hypotheses vague or uncheckable
- do not claim certainty when the available evidence is thin
- do not treat "interesting code" as a sufficient probe target; every target must answer a concrete question
- do not fail just because the project-root `tmp/` directory is unavailable; fall back to a system temporary directory
- do not generate a report without also summarizing it in the console response

# Output

1. diagnosis report in Markdown
2. either a direct diagnosis or a small checkable hypothesis set
3. recommendation on whether `debug-checkup` is needed
4. console summary plus report location
