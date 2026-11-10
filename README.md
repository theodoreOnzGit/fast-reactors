# fast-reactors

Fast reactor models (starting with EBR-II) built on
[OUTRAM PARK](https://github.com/theodoreOnzGit/outram-park).

| Folder | What |
|---|---|
| [`literature/`](literature/) | Open-access literature, each with its licence basis |
| [`rust/`](rust/) | Rust workspace, depending on [`outram-park`](https://crates.io/crates/outram-park) from crates.io |

```bash
cd rust && cargo build --release
```

Work is tracked in the
[outram-park-backend issues](https://github.com/theodoreOnzGit/outram-park-backend/issues).
Agent rules: [`AGENTS.md`](AGENTS.md).

> ⚠️ Research, education and V&V only. Not for reactor operation, licensing
> or safety-critical decisions.

Licence: AGPL-3.0.
