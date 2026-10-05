# Contributing

This repo is a contribution on-ramp for the Bend ecosystem. The gaps in the README aren't just a list — each one is a **GitHub issue** you can claim, discuss, and close.

## The issue graph

- **10 umbrella issues** (labeled `umbrella`), one per domain: [Build & ship](https://github.com/lilalittle/bend-packages/issues/1), [Prove it's correct](https://github.com/lilalittle/bend-packages/issues/2), [Numbers & ML](https://github.com/lilalittle/bend-packages/issues/3), [Data](https://github.com/lilalittle/bend-packages/issues/4), [Web services](https://github.com/lilalittle/bend-packages/issues/5), [Databases](https://github.com/lilalittle/bend-packages/issues/6), [Apps & interfaces](https://github.com/lilalittle/bend-packages/issues/7), [Text & documents](https://github.com/lilalittle/bend-packages/issues/8), [Operate in prod](https://github.com/lilalittle/bend-packages/issues/9), [Ecosystem health](https://github.com/lilalittle/bend-packages/issues/10).
- **One issue per gap**: a job-to-be-done, what's already on the hub, a suggested approach, and a definition of done.
- **Relationships**: every issue has a *Blocked by / Unlocks / Builds on* section. Some issues are leaves (build anytime); others form chains — e.g. the YAML parser builds on the existing `bend-kit-parse` parser combinators, and the formatter is blocked on the parser library.

## How to claim work

1. Pick an umbrella in your domain and read its checklist.
2. Prefer a **leaf**: issues labeled `good first issue` with no "Blocked by" section can be built without waiting on anyone.
3. **Comment on the issue** to claim it — a short "I'm taking this" is enough. Scope discussion happens in the issue, not the umbrella.
4. If the issue is blocked, design discussion is still welcome — but don't start coding the core until the dependency lands.

## Source-hunt issues

Some of the most interesting packages (`bend-tensors`, `bolt`, `ezx`, `bend-ml`…) have no public repo. Their issues are `question` issues asking: *who wrote this?* If you know the author — or you are the author — drop a link. No judgment, just provenance.

## Build rules (Bend conventions)

- **Decompose into packages** that others can rely on. One concern per package.
- **Prove what matters**: keep important rules in `LAWS.bend`, fill them in `PROOF.bend`, and keep `bend PROOF.bend` printing `All terms check.`
- **License**: a `LICENSE` file next to the entry file, opening with `SPDX-License-Identifier: MIT`. (No license means MIT-0; adding one later changes the package hash.)
- **Publish**: `bend <file>.bend --publish <name>@<version>` — needs `bend login`, and publishes are **public and permanent**.
- **Imports**: consumers use `import name@version/file.bend` or `import 0x<hash>/file.bend`.

New here? Start with the [Prove it's correct](https://github.com/lilalittle/bend-packages/issues/2) umbrella — its leaves are small, well-specified, and very testable.
