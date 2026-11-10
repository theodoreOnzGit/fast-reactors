# Agent Instructions

Rules for every agent (Claude, Codex or other) working in this repository.
`CLAUDE.md` is a short summary that points here; **this file is the
authority**. Conventions follow
[outram-park-backend](https://github.com/theodoreOnzGit/outram-park-backend),
which this repository builds on.

## What this repository is

Fast reactor work (EBR-II and others) built on outram-park, the maintainer's
hobby alongside the MSRE repository. Licence: AGPL-3.0 (`LICENSE`).

| Folder | What |
|---|---|
| `literature/` | Open literature only (see below), with its licence table in `literature/README.md` |
| `rust/` | The Rust workspace (`rust/Cargo.toml`, members under `rust/crates/`) |

- **The Rust workspace depends on OUTRAM PARK from crates.io only**: the
  `outram-park` metacrate, `default-features = false`, enabling one feature
  per backend used (e.g. `teh-o-prke`, `tuas_boussinesq_solver`). Never a
  `path =` or `git =` dependency on outram-park-backend.
- Generic capability (geometry, criticality, kinetics, thermal hydraulics
  solvers) belongs upstream in outram-park-backend; this repository holds the
  fast-reactor models and V&V cases built on it.
- Build and test in release mode, from `rust/`:
  `cargo build --release`, `cargo test --release`. Toolchain is pinned in
  `rust/rust-toolchain.toml`, matching outram-park-backend.

## Task tracking

Track work in **GitHub issues** on `theodoreOnzGit/outram-park-backend` with
`gh` (`--repo theodoreOnzGit/outram-park-backend`), under the relevant crate's
epic. This repository has no tracker of its own.

```bash
R=theodoreOnzGit/outram-park-backend
gh issue list -R $R --state open
gh issue view -R $R <number>
gh issue create -R $R --title "..." --body "..."
gh issue comment -R $R <number> --body "..."
```

- Use `gh` issues for all task and roadmap tracking, not markdown TODO lists.
- **Do not close issues on your own initiative.** Propose the closure with its
  evidence; the maintainer decides.
- State blocking relationships in the issue body in words ("blocked by #12").

## Literature: access tier and where it lives

- **This repository is public.** Only literature with a verified
  redistribution basis goes into `literature/`, filed by ground (`cc-by/`,
  ...) with a row in `literature/README.md` quoting the licence statement and
  saying where in the PDF it is.
- **The access tier comes from the document's own licence or copyright
  statement, never from where it is hosted.** Being free to download on OSTI,
  ADAMS or a publisher's site is not a redistribution basis.
- **Anything without one is proprietary** and goes to the private repository
  `theodoreOnzGit/propreitrary-literature-theodore`, with its row in that
  repository's `README.md`. Never copy a proprietary document, or its
  extracted full text, into this repository. Citations, notes and short
  excerpts about it are fine.
- U.S. Government *contractor* reports (ANL, INL, ORNL, Sandia...) are
  proprietary unless the document is marked for public release or unlimited
  distribution: the U.S. Government disclaimer alone is not enough.
- **The maintainer supplies the literature.** Do not fetch or add documents
  on your own initiative.
- Keep PDFs unmodified and verify copies byte for byte (`cmp`).

## Physics and V&V

- Cite the source (document, section, page or table) for every number,
  correlation and benchmark value. Never invent data; leave unknowns empty.
- Say what was verified and how; an AI draft is not reviewed code.
- Research, education and V&V only: not for reactor operation, licensing or
  safety-critical decisions.

## Git

- Commit or push only when the maintainer asks. Never force-push.
- If a push is rejected, stop and report the exact error.

## Non-interactive shell commands

`cp`, `mv` and `rm` may be aliased to `-i` and hang. Use `cp -f`, `mv -f`,
`rm -f`, `rm -rf`; `ssh`/`scp` with `-o BatchMode=yes`.
