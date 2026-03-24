# Codex Debug

`codex-debug` is a toolkit repository of installable Codex skills.

## Purpose

It groups two related skills:

- `debug-diagnosis`
- `debug-checkup`

Together they support hypothesis-driven bug investigation:

- diagnose the likely cause first
- run targeted runtime checkups only when reasoning alone is not enough

## Installation

Install one skill at a time with `skill-installer`, or install both in one run from the remote repository path that contains this product.

Examples:

- `debug-diagnosis`
- `debug-checkup`

After installation, restart Codex so the newly installed skills are discovered.

## Updating

If `skill-update` is installed, you can use it to update previously installed `codex-debug` skills through the standard reinstall workflow.

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
