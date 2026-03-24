# Codex Debug

`codex-debug` is a toolkit repository of installable Codex skills.

## Purpose

It groups two related skills:

- `debug-diagnosis`
- `debug-checkup`

Together they support hypothesis-driven bug investigation:

- diagnose the likely cause first
- run targeted runtime checkups only when reasoning alone is not enough

## Skills

- `debug-diagnosis` analyzes the reported bug, reads the relevant code and entrypoint context, and tries to produce either a direct diagnosis or a small set of concrete, checkable hypotheses. It should be used first whenever the root cause is not yet clear.
- `debug-checkup` takes a diagnosis result, determines which runtime adapter would be needed to verify the remaining hypotheses, checks whether that adapter is currently available, and produces a clear report when runtime verification cannot proceed yet. It is the bridge between diagnosis and future adapter-driven runtime checks.

## Installation

Install one skill at a time with `skill-installer`, or install both in one run from the remote repository path that contains this product.

Install `debug-diagnosis`:

```text
$skill-installer install https://github.com/sablesoft/codex-debug/tree/main/debug-diagnosis
```

Install `debug-checkup`:

```text
$skill-installer install https://github.com/sablesoft/codex-debug/tree/main/debug-checkup
```

Install both skills:

```text
$skill-installer install the skills from https://github.com/sablesoft/codex-debug/tree/main/debug-diagnosis and https://github.com/sablesoft/codex-debug/tree/main/debug-checkup
```

After installation, restart Codex so the newly installed skills are discovered.

## Updating

If `skill-update` is installed, you can use it to update previously installed `codex-debug` skills through the standard reinstall workflow.

Natural-language prompts:

```text
Use skill-update to update the installed debug-diagnosis skill from https://github.com/sablesoft/codex-debug/tree/main/debug-diagnosis
```

```text
Use skill-update to update the installed debug-checkup skill from https://github.com/sablesoft/codex-debug/tree/main/debug-checkup
```

```text
Use skill-update to update the installed debug-diagnosis and debug-checkup skills from the codex-debug repository paths:
- https://github.com/sablesoft/codex-debug/tree/main/debug-diagnosis
- https://github.com/sablesoft/codex-debug/tree/main/debug-checkup
```

`$skill-update` prompts:

```text
$skill-update update the installed debug-diagnosis skill from https://github.com/sablesoft/codex-debug/tree/main/debug-diagnosis
```

```text
$skill-update update the installed debug-checkup skill from https://github.com/sablesoft/codex-debug/tree/main/debug-checkup
```

```text
$skill-update update the installed debug-diagnosis and debug-checkup skills from the codex-debug repository paths:
- https://github.com/sablesoft/codex-debug/tree/main/debug-diagnosis
- https://github.com/sablesoft/codex-debug/tree/main/debug-checkup
```

## Host Expectations

- write temporary artifacts under `tmp/codex-debug/`
- if the project-root `tmp/` directory is unavailable, fall back to a system temporary directory
- summarize results in the console and include links or clear paths to generated reports
- keep each installed skill self-contained

## Layout

- `product.yaml` describes this toolkit product for `product-engine`
- each root folder with `SKILL.md` is an installable Codex skill

## Principle

Each installed skill should stand on its own.  
This repository keeps related debugging skills together.
