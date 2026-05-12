# AGENTS.md

## Purpose

This repository contains a LaTeX resume with two entrypoints:

- `resume_public.tex`: public/shareable build that uses `contact_public.tex`
- `resume_full.tex`: local/private build that uses `contact_full.tex`

Shared resume content lives in `resume_body.tex`.

## File Roles

- `contact_public.tex` contains safe-to-publish contact macros.
- `contact_full.template.tex` is the local template for private contact info.
- `contact_full.tex` is a local-only file created from the template and must not be committed.
- `.github/workflows/build-resume.yml` builds only the public resume in CI.

## Working Rules

- Do not commit real private contact details.
- Do not create or modify `contact_full.tex` unless explicitly asked.
- Prefer changes in `resume_body.tex` for content updates shared by both resume variants.
- Keep `resume_public.tex` and `resume_full.tex` aligned except for which contact file they import.

## Build Commands

Public build:

```sh
latexmk -pdf resume_public.tex
```

Full local build:

```sh
cp contact_full.template.tex contact_full.tex
latexmk -pdf resume_full.tex
```

## Validation

- If you change resume content or LaTeX structure, rebuild the affected `.tex` entrypoint when possible.
- CI only validates `resume_public.tex`, so any `resume_full.tex`-only changes need local verification.
