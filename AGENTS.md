# Repository working contract

`aod` is the maintained `macqster/aod` checkout for the Archive.org download
script. Keep changes small and evidence-led.

## Before editing

- Start read-only: inspect `git status --short --branch`, the relevant diff,
  and the current remote before touching files.
- Preserve unrelated dirty, ignored, generated, and local-owner state. Do not
  reset, clean, stash, or overwrite another owner's work.
- Never read, print, copy, or commit passwords, tokens, cookies, private keys,
  or account/session data. The downloader's Archive.org credentials belong in
  the operator's private invocation environment, never in source or examples.
- Distinguish tracked Python source and requirements from downloaded PDFs,
  JPEGs, metadata, virtual environments, and other runtime output.

## Branch and publication policy

- `main` is the shared authority. Reconciliation to `main`/`master` is
  available only from an approved Mac host using the `mbp` or `imac` profile.
- Work originating on another machine must be published to a review branch,
  then independently reassessed from a current remote ref on the Mac before
  integration. A clean worktree or passing device test is not that
  reassessment.
- Use selective staging and review the staged diff before any commit or push.
  Do not force-push, rewrite, or delete shared history without a documented
  recovery path and explicit operator decision.

## Safe validation

Run these non-mutating checks after source edits:

```sh
python3 -m py_compile archive-org-downloader.py
git diff --check
```

The syntax check does not require third-party imports. Running the program,
even with `--help`, requires the modules in `requirements.txt`; dependency
installation and actual Archive.org downloads are operator actions outside
this repository validation contract. Never place credentials in commands,
shell history, examples, or tracked files.
