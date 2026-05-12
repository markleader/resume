# Resume

This repository stores a LaTeX resume with two variants:

- `resume_public.tex` builds a shareable public PDF with safe contact information.
- `resume_full.tex` builds a local-only version that can include private contact details through `contact_full.tex`.

The shared resume content lives in `resume_body.tex`.

## Local Build

If you have a LaTeX toolchain installed, build the public version with:

```sh
latexmk -pdf resume_public.tex
```

To build the full version locally, first create `contact_full.tex` from the template and then compile:

```sh
cp contact_full.template.tex contact_full.tex
latexmk -pdf resume_full.tex
```

## CI

GitHub Actions builds only `resume_public.tex` on pushes and pull requests. If the document fails to compile, the workflow fails. Successful runs upload `resume_public.pdf` as a workflow artifact.

## Private Contact File

`contact_full.tex` is intentionally ignored and should be created only on your local machine from `contact_full.template.tex`. Do not commit real private contact details to this repository.
