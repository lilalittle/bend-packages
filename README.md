# Bend 2 Package Ecosystem

A curated, regularly refreshed overview of [BendHub](https://hub.bend-lang.com) — the package registry for [Bend 2](https://github.com/bendlang/bend), the massively-parallel language with machine-checked proofs.

> **Snapshot: 2026-10-12** · **581 packages** — 106 named, 255 hash-only · refreshed weekly.
> The [full A–Z list](ALL_PACKAGES.md) is generated from the registry API each refresh.

## Using these packages

Import by name (pinned version, cached under `~/.bend/lib/names`):

```python
import bend-mathlib@0.7.2.0/nat.bend as MNat
```

or by content hash (always resolves to the exact same code):

```python
import 0x53dde92df75268075f1bc6c33ecbb079/bend_ml.bend as ML
```

Publish your own with `bend <file>.bend --publish <name>@<version>` (public and permanent; needs `bend login`). Per [Tom's rule](https://github.com/lilalittle/bend-math): decompose Bend work into packages others can rely on.

---

## Top picks

### Verified math & proofs

Bend 2's killer feature is machine-checked proofs: `law` states a proposition, a paired `def` proves it, and `bend PROOF.bend` prints `All terms check.` These packages give you lemmas to import instead of re-proving.

| Package | What | Links |
|---|---|---|
| [bend-mathlib](https://hub.bend-lang.com/n/bend-mathlib) `@0.7.3.0` | 231 machine-checked lemmas (Nat, Bool, List, String, Maybe, equality, order, algebra, permutations, sorting) — zero `@unsafe` | [repo](https://github.com/bendlib/bendlib) · `import bend-mathlib@0.7.3.0/nat.bend as MNat` |
| [bend-ml-nat-lemmas](https://hub.bend-lang.com/n/bend-ml-nat-lemmas) `@0.1.1.0` | Proved Nat/List lemmas that Bend's Base doesn't ship — complements bend-mathlib | `import bend-ml-nat-lemmas@0.1.1.0/main.bend` · ⚠️ no public repo found yet |
| [bend-schema-lib](https://hub.bend-lang.com/n/bend-schema-lib) `@0.1.0.0` | Schema validation library | `import bend-schema-lib@0.1.0.0/core.bend` · ⚠️ no public repo found yet |
| [qasim-bend-kit](https://hub.bend-lang.com/n/qasim-bend-kit) `@0.1.0.2` | JSON library with correctness laws and machine-checked proofs | ⚠️ no public repo found yet |
| [bend-kit-lemmas](https://hub.bend-lang.com/n/bend-kit-lemmas) `@0.1.0.0` | **New** — proved laws relating Word and U32 arithmetic to Nat | via [bend-kit](https://github.com/paymog/bend-kit) |
| [bend-prot](https://hub.bend-lang.com/n/bend-prot) `@0.1.0.0` | **New** — protein/RMSD/PDB simulation with `LAWS.bend`/`PROOF.bend` | `import bend-prot@0.1.0.0/protein.bend` · ⚠️ no public repo found yet |
| [bend-collections-laws](https://hub.bend-lang.com/n/bend-collections-laws) `@1.0.0.0` (+ `-containers`, `-crypto`, `-math`) | Machine-checked law suites for containers, crypto, math — the largest packages on the hub | [repo](https://github.com/Giulio2002/bend-collections) |
| [bend-csv-parser](https://hub.bend-lang.com/n/bend-csv-parser) `@0.1.0.1` | Fast CSV parser **with proofs** | `import bend-csv-parser@0.1.0.1/core.bend` |
| [bend-trace-context](https://hub.bend-lang.com/n/bend-trace-context) `@0.2.0.0` | W3C Trace Context propagation, rules proved as laws | [repo](https://github.com/LucasGois1/bend-trace-context) |
| [bend-lawful-stdlib](https://hub.bend-lang.com/n/bend-lawful-stdlib) `@0.1.0.0` | Typeclass-style Ord / Semigroup / Group with their laws | `import bend-lawful-stdlib@0.1.0.0/src/class.bend` |
| [wordlib](https://hub.bend-lang.com/0xb13667d52aa56e002b4d09883d7fce3e/word.bend) | Laws about Base's fixed-width words, with `LAWS.bend`/`PROOF.bend` | `import 0xb13667d52aa56e002b4d09883d7fce3e/word.bend` |

The `bendlib` repo also ships [**lawcheck**](https://github.com/bendlib/bendlib) — finds counterexamples to your laws *before* you try to prove them.

### Tensors, autodiff & ML

| Package | What | Links |
|---|---|---|
| [bend-ml-tensor](https://hub.bend-lang.com/n/bend-ml-tensor) `@0.1.2.0` | **Tensors with the shape in the TYPE** — "a shape error is a type error" | `import bend-ml-tensor@0.1.2.0/tensor.bend` · ⚠️ no public repo found yet |
| [bend-ml-tensor-array](https://hub.bend-lang.com/n/bend-ml-tensor-array) `@0.1.7.0` | Tensors over a flat Array, shape in the type (4 releases this week — active development) | `import bend-ml-tensor-array@0.1.7.0/tensor_array.bend` · ⚠️ no public repo found yet |
| [bend-ml-autograd](https://hub.bend-lang.com/n/bend-ml-autograd) `@0.1.1.0` | Automatic differentiation **with a proved law** | `import bend-ml-autograd@0.1.1.0/autograd.bend` · ⚠️ no public repo found yet |
| [bend-ml-bpe-tokenizer](https://hub.bend-lang.com/n/bend-ml-bpe-tokenizer) `@0.1.2.0` | Byte-level BPE tokenizer with proved roundtrip | `import bend-ml-bpe-tokenizer@0.1.2.0/bpe.bend` · ⚠️ no public repo found yet |
| [bend-tensors](https://hub.bend-lang.com/n/bend-tensors) `@0.0.0.2` | Dense linear algebra with **shapes in the types** (MIT) | `import bend-tensors@0.0.0.2/bend_tensors.bend` · ⚠️ no public repo found yet |
| [bend-blas-lapack](https://hub.bend-lang.com/n/bend-blas-lapack) `@0.0.0.1` | BLAS, LAPACK and cuBLAS — one def per routine, with C/JS shims | `import bend-blas-lapack@0.0.0.1/blas.bend` · ⚠️ no public repo found yet |
| [bend-ml](https://hub.bend-lang.com/0x53dde92df75268075f1bc6c33ecbb079/bend_ml.bend) | Parallel linear regression, batches, statistics, metrics — **with `LAWS.bend`/`PROOF.bend`** | `import 0x53dde92df75268075f1bc6c33ecbb079/bend_ml.bend` · ⚠️ no public repo found yet |
| [stelliferous](https://hub.bend-lang.com/n/stelliferous) `@0.0.2.0` | **New — tensor + convolution library, written and proved in Bend**: F32 tensors, conv2d, max_pool2d, activations; native convolution proved equal to its matrix spec bit-for-bit, plus a kernel cost model | [repo](https://github.com/Kaz9487/Stelliferous) · `import stelliferous@0.0.2.0/tensor_f32.bend as F` |
| [tinygrad-laws](https://hub.bend-lang.com/0xe6b82fa6c4c459c7023adf4b12a3ac46) | "The laws of tinygrad, stated for the Bend port" — someone is porting tinygrad to Bend too | `tensor.bend`, `shape.bend`, `nat.bend` + laws |
| [BendSR](https://hub.bend-lang.com/0xb1a81026c64fbbc00a8570155d77383d/BendSR.bend) | Massively parallel symbolic regression engine | [repo](https://github.com/k3ybladewielder/BendSR) |
| **bendygrad** | tinygrad front-end in Bend 2: views, buffers, autodiff, SGD — **GitHub only, not on the hub** | [repo](https://github.com/KapioKai/bendygrad) |

### Parallelism & systems

| Package | What | Links |
|---|---|---|
| [bend-parallel](https://hub.bend-lang.com/n/bend-parallel) `@0.1.0.0` | Parallel histogram, scan, sort (Apache-2.0) | `import bend-parallel@0.1.0.0/histogram.bend` |
| [bend-kit-concurrency](https://hub.bend-lang.com/n/bend-kit-concurrency) `@0.2.0.0` | Parallel map/reduce, worker pool, channel select, timeouts | `import bend-kit-concurrency@0.2.0.0/concurrency.bend` |
| [mylsm-lsm-store](https://hub.bend-lang.com/n/mylsm-lsm-store) `@0.5.0.0` | A **full LSM-tree storage engine in pure Bend** — memtable, WAL, SST files, merge iterators, crash-point testing (BSD-3-Clause) | `import mylsm-lsm-store@0.5.0.0/mylsm.bend` |
| [ber-core-store](https://hub.bend-lang.com/n/ber-core-store) `@0.1.2.0` | Content-addressed / Merkle state-tree store with certified merges (BSD-3-Clause) | [repo](https://github.com/FabianVegaA/ber) |
| [bend-kit-sqlite](https://hub.bend-lang.com/n/bend-kit-sqlite) `@0.1.0.0` | Prepared SQLite statements through libsqlite3 | `import bend-kit-sqlite@0.1.0.0/sqlite.bend` |
| [bend-kit-postgres](https://hub.bend-lang.com/n/bend-kit-postgres) `@0.1.0.1` / [bend-kit-redis](https://hub.bend-lang.com/n/bend-kit-redis) `@0.1.0.1` | Postgres protocol 3.0 + SCRAM; Redis/Valkey RESP3 client with pipelining | via [bend-kit](https://github.com/paymog/bend-kit) |

### Dev tooling

| Package | What | Links |
|---|---|---|
| [bolt](https://hub.bend-lang.com/n/bolt) `@1.12.0.0` | Linter, checker **and language server** for Bend 2 (~40 lint rules) | `import bolt@1.12.0.0/main.bend` · ⚠️ no public repo found yet |
| [ezx](https://hub.bend-lang.com/n/ezx) `@1.5.0.0` | `ez`, the package manager for Bend 2 | ⚠️ no public repo found yet |
| [shake](https://hub.bend-lang.com/n/shake) `@0.5.0.0` | Proven CLI argument parser with subcommands and help | ⚠️ no public repo found yet |
| [snap](https://hub.bend-lang.com/n/snap) `@1.2.0.0` | Run programs from Bend 2 with argv as a string list, no shell | ⚠️ no public repo found yet |

### The `bend-kit` standard library

The most-depended-on packages on the hub (`bend-kit-bytes` has 99 dependents). Actively versioned monorepo — [paymog/bend-kit](https://github.com/paymog/bend-kit). Import per package, e.g. `import bend-kit-http@0.32.0.0/http.bend`:

`bytes` · `json` · `encoding` · `url` · `wire` (TCP/UDP/TLS) · `http` (HTTP/1.1+2 client, HTTP/1.1 server) · `http2` (HPACK) · `camber` (fixed prepared HTTP apps) · `hairpin` (HTTP client: pool, cookies, mTLS, retries) · `crypto` (OpenSSL 3: hashes, HMAC, HKDF, RSA/ECDSA) · `regex` (RE2 syntax, Pike VM, linear time) · `collections` (maps, vector, deque, priority queue) · `parse` (parser combinators) · `time` · `zlib` · `dns` · `files` · `fmt` · `int` (U8–I64) · `f64` (IEEE 754 binary64 — new) · `bignum` (bigint/decimal/rational) · `hash` (FNV-1a, xxHash, SipHash) · `property` (pure generators + shrink) · `notch` (structured logging) · `jwt` · `oauth2` · `sigv4` (AWS) · `multipart` · `netip` · `websocket` · `webhooks` · `router` · `tar` · `archive` (ZIP) · `cbor` · `csv` · `tty` · `unicode` (UCD 17.0.0) · `stream` · `process` · `sqlite` · `postgres` · `redis` · `llm` (Anthropic + OpenAI, SSE streaming) · `authz` · `cache` · `journal` · `lemmas` (proved Word/U32↔Nat laws) · `protobuf` · `resources` · `retry` · `scheduler` (all new this week)

### Polished small families

- [**emerging-ez\***](https://hub.bend-lang.com/n/emerging-ezjson) (all MIT, all with top-level LICENSE): `ezjson` (parser/printer/pull cursor) · `eztoml` (proven parser/renderer) · `ezhttp` (client+server, auth/cookies/CORS) · `ezimg` (PNG + baseline JPEG) · `ezaudio` (WAV + MP3)
- **LLM SDKs** (newest packages on the hub, ~2026-09-29): [bend-anthropic-sdk](https://hub.bend-lang.com/n/bend-anthropic-sdk) and [bend-openai-sdk](https://hub.bend-lang.com/n/bend-openai-sdk) — unofficial SDKs with typed requests, streaming, tool calling
- [**awesome-bend**](https://github.com/777genius/awesome-bend) — the community-curated list; a good second stop for discovery

---

## Repositories

| Repo | Publishes |
|---|---|
| [paymog/bend-kit](https://github.com/paymog/bend-kit) | All 39 `bend-kit-*` packages (linked via `Source:` in hub descriptions) |
| [paymog/bend-net](https://github.com/paymog/bend-net) | `bend-net-*` predecessors |
| [bendlib/bendlib](https://github.com/bendlib/bendlib) | `bend-mathlib`, `bendlib-kernel-list`, `lawcheck` |
| [Giulio2002/bend-collections](https://github.com/Giulio2002/bend-collections) | `bend-collections`, `bend-collections-laws*` — verified containers + SHA-256 |
| [k3ybladewielder/BendSR](https://github.com/k3ybladewielder/BendSR) | BendSR parallel symbolic regression |
| [KapioKai/bendygrad](https://github.com/KapioKai/bendygrad) | tinygrad front-end in Bend (GitHub only) |
| [LucasGois1/bend-trace-context](https://github.com/LucasGois1/bend-trace-context) | `bend-trace-context` (linked in hub description) |
| [FabianVegaA/ber](https://github.com/FabianVegaA/ber) | `ber-core-store` — version-controlled data, certified merges |
| [fraylabs/stiff](https://github.com/fraylabs/stiff) | Experimental HTTP/routing/streaming/SQLite for Bend 2 |
| [jonathanperis/jonlib](https://github.com/jonathanperis/jonlib) | Graphics/game library, raylib parity goal |
| [phenomenon0/bend-u64](https://github.com/phenomenon0/bend-u64) | 64-bit unsigned ints in pure Bend, checked commutation law |
| [PedroAVJ/n](https://github.com/PedroAVJ/n) | `near-architecture`, `near-v-framework` ("V" framework) |
| [Kaz9487/Stelliferous](https://github.com/Kaz9487/Stelliferous) | `stelliferous` — tensor + convolution library, written and proved in Bend |
| [kbrianps/bend-smtp](https://github.com/kbrianps/bend-smtp) | SMTP client (TLS, OAuth, DKIM, attachments) with a machine-checked proof on the pure core |
| [777genius/awesome-bend](https://github.com/777genius/awesome-bend) | Curated ecosystem list |

Only 3 repos are actually linked from hub package descriptions — the rest were found by searching. If you publish Bend packages, put a `Source:` link in your description.

## People & publishers

The humans (GitHub handles) behind the packages above — follow them if you work in Bend:

- **[@paymog](https://github.com/paymog)** — the `bend-kit`/`bend-net` monorepos; the de-facto standard library, most-depended-on packages on the hub
- **[@bendlib](https://github.com/bendlib)** (org) — `bend-mathlib` (231 machine-checked lemmas, zero `@unsafe`), `lawcheck`, BendHub API docs
- **[@Giulio2002](https://github.com/Giulio2002)** — verified containers (`bend-collections`) + SHA-256
- **[@KapioKai](https://github.com/KapioKai)** — `bendygrad`, the tinygrad front-end in Bend
- **[@k3ybladewielder](https://github.com/k3ybladewielder)** — BendSR, massively parallel symbolic regression
- **[@LucasGois1](https://github.com/LucasGois1)** — `bend-trace-context`, W3C Trace Context with proved laws
- **[@FabianVegaA](https://github.com/FabianVegaA)** — `ber`, version-controlled data with certified merges
- **[@777genius](https://github.com/777genius)** — `awesome-bend`, the curated ecosystem list
- **[@phenomenon0](https://github.com/phenomenon0)** — `bend-u64`, 64-bit words in pure Bend
- **[@Kaz9487](https://github.com/Kaz9487)** — `stelliferous`, tensors + convolution written and proved in Bend
- **[@kbrianps](https://github.com/kbrianps)** — `bend-smtp`, SMTP client with a proved pure core
- **[@subtleGradient](https://github.com/subtleGradient)** — `bend-over-sqlite` (SQLite for C and Wasm targets); collaborator on this repo

## Looking for source

Promising packages with **no public repository found** — if you know the authors, point them here:

`bend-tensors` · `bend-blas-lapack` · `bend-parallel` · `bend-ml` (`0x53dde92d…`) · tinygrad-laws (`0xe6b82fa6…`) · the LAWS-spec package (`0x983079cc7642…`) · `wordlib` (`0xb13667d5…`) · `bolt` · `ezx` · `shake` · `snap` · `emerging-ezjson/eztoml/ezhttp/ezimg/ezaudio` · `mylsm-lsm-store` · `bend-csv-parser` · `bend-math-lib` · `bend-anthropic-sdk` · `bend-openai-sdk` · the `bend-ml-*` family (`bend-ml-tensor`, `bend-ml-tensor-array`, `bend-ml-autograd`, `bend-ml-bpe-tokenizer`, `bend-ml-nat-lemmas`) — typed tensors + proved autodiff, no repos found by search · `bend-prot` · `bend-edit-distance`

## Ecosystem gaps

What you'd expect in a healthy package ecosystem but won't find on BendHub yet — organized by the job you'd hire it for. Bend 2 is young, so read this as an opportunities list: most of these are one focused package away from existing. ★ marks the ones closest to [Tom's](https://github.com/lilalittle) active work (verified math, tensors, dev tooling).

**Want to build one?** Every gap is a claimable issue with blocked-by relationships — see [CONTRIBUTING.md](CONTRIBUTING.md).

### Build & ship
- **Start a new project** → no scaffolding: no `init` templates or example repos wired to `ez`
- ★ **Format code** → no formatter — no `gofmt`/`black` equivalent anywhere on the hub
- **Edit comfortably** → no editor support: no Zed/VS Code extension, no tree-sitter grammar — `bolt` ships an LSP server with no client to talk to
- **Publish confidently** → `ezx` (the package manager) has no public repo or docs; the publish flow is tribal knowledge
- **Lock dependencies** → no lockfile story, no audit/vulnerability tooling

### Prove it's correct
- ★ **Run tests** → no test runner or assertion library (`bend-kit-property` has generators + shrink, but nothing to run them)
- ★ **Check laws before proving** → `lawcheck` (counterexample finder) lives in `bendlib/bendlib` but isn't published as a package
- **Debug & profile** → no debugger, no profiler, no REPL/notebook story
- ★ **Build verified math** → no mathlib equivalent; expressivity gaps limit what pure math can even be stated (see issue #64)

### Numbers & ML
- ★ **Train a model** → autodiff now on the hub (`bend-ml-autograd@0.1.1.0`, "automatic differentiation with a proved law") plus GitHub-only `bendygrad`; still no optimizer zoo (Adam/RMSprop), no data-loading/batching helpers, no model serialization format
- **Do statistics** → no distributions, sampling, or hypothesis-testing package
- ★ **Sparse / FFT / signal** → dense linear algebra only (`bend-tensors`, `bend-ml-tensor`); no sparse matrices, no FFT
- **Plot results** → no charting or SVG generation

### Data
- **Read common formats** → no YAML, MessagePack, Parquet/Arrow, or PDF
- **Wrangle tables** → no dataframe
- ~~**Validate schemas** → no JSON Schema / validation library~~ — closed 2026-10-05 by `bend-schema-lib@0.1.0.0`

### Web services
- **Build an API** → servers exist (`bend-kit-http`, `ezhttp`); missing middleware, sessions, HTML templating, GraphQL, gRPC/protobuf
- ~~**Send email** → no SMTP client~~ — closed 2026-10-12 by [bend-smtp](https://github.com/kbrianps/bend-smtp) (TLS, OAuth, DKIM, SMTPUTF8, attachments; machine-checked proof on the pure core)
- **Run background jobs** → no queue/scheduler

### Databases
- **Evolve schema** → no migration tooling
- **Query safely** → no query builder or typed query layer
- **Use MySQL/Mongo** → no drivers (Postgres, SQLite, Redis are covered)

### Apps & interfaces
- **Build a TUI** → no terminal-UI library (no progress bars/spinners either)
- **Build a GUI** → nothing
- **Ship a game** → `jonlib` (graphics) + `ezaudio` exist; input, physics, and audio mixing are missing

### Text & documents
- **Go multilingual** → no i18n/l10n
- **Search text** → no full-text search index

### Operate in prod
- **Deploy** → no container/CI helpers
- **Watch it run** → logging (`notch`) + tracing (`bend-trace-context`) exist; no metrics (Prometheus-style) or alerting

### Meta
- **Publisher concentration** — one publisher (`paymog`) accounts for roughly half of all named packages: great velocity, real bus-factor risk
- **Sourceless packages** — many of the most interesting packages (`bend-tensors`, `bolt`, `ezx`, `bend-ml`…) have no public repo: can't audit them, can't contribute, can't fully rely on them

---

*Curated by [North](https://github.com/lilalittle) 🧭 — a weekly snapshot of the BendHub registry. New packages, version bumps, and newly found repos land here every Monday. Corrections welcome via issues.*
