# Bend 2 Package Ecosystem

A curated, regularly refreshed overview of [BendHub](https://hub.bend-lang.com) — the package registry for [Bend 2](https://github.com/bendlang/bend), the massively-parallel language with machine-checked proofs.

> **Snapshot: 2026-10-26** · **889 packages** — 179 named, 280 hash-only · refreshed weekly.
> The [full A–Z list](ALL_PACKAGES.md) is generated from the registry API each refresh.

## Using these packages

Import by name (pinned version, cached under `~/.bend/lib/names`):

```python
import bend-mathlib@0.7.5.0/nat.bend as MNat
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
| [bend-mathlib](https://hub.bend-lang.com/n/bend-mathlib) `@0.7.5.0` | 231 machine-checked lemmas (Nat, Bool, List, String, Maybe, equality, order, algebra, permutations, sorting) — zero `@unsafe` | [repo](https://github.com/bendlib/bendlib) · `import bend-mathlib@0.7.5.0/nat.bend as MNat` |
| [bend-ml-nat-lemmas](https://hub.bend-lang.com/n/bend-ml-nat-lemmas) `@0.1.1.0` | Proved Nat/List lemmas that Bend's Base doesn't ship — complements bend-mathlib | [repo](https://github.com/nuxyel/bend-ml) · `import bend-ml-nat-lemmas@0.1.1.0/main.bend` |
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
| [bend-ml-tensor](https://hub.bend-lang.com/n/bend-ml-tensor) `@0.1.2.0` | **Tensors with the shape in the TYPE** — "a shape error is a type error" | [repo](https://github.com/nuxyel/bend-ml) · `import bend-ml-tensor@0.1.2.0/tensor.bend` |
| [bend-ml-tensor-array](https://hub.bend-lang.com/n/bend-ml-tensor-array) `@0.1.16.0` | Tensors over a flat Array, shape in the type (still very actively developed) | [repo](https://github.com/nuxyel/bend-ml) · `import bend-ml-tensor-array@0.1.16.0/main.bend` |
| [bendtorch-core](https://hub.bend-lang.com/n/bendtorch-core) `@0.1.0.0` | PyTorch-like tensor library in Bend: F32 tensors, matmul, autograd tape, losses, SGD — laws and proofs throughout (~180 files) | [repo](https://github.com/aaaxn/bendtorch) · `import bendtorch-core@0.1.0.0/src/tensor/core.bend` |
| [bendtorch](https://hub.bend-lang.com/n/bendtorch) `@1.1.1.0` (+ [bendtorch-fast](https://hub.bend-lang.com/n/bendtorch-fast), [bendtorch-gpu](https://hub.bend-lang.com/n/bendtorch-gpu), [bendtorch-load](https://hub.bend-lang.com/n/bendtorch-load)) | **New — the bendtorch project restructured as named entry points**: same layers, types and bits — over bend-ml-tensor-fork (fast), bend-ml-tensor-gpu (GPU), or loading-only (binary-read is foreign C/JS, imported by no law file) | [repo](https://github.com/aaaxn/bendtorch) · `import bendtorch@1.1.1.0/tensor.bend` |
| [mlbend-*](https://hub.bend-lang.com/n/mlbend-datasets) `@0.1.x` | **New — a sklearn-shaped ML stack in one week**: `mlbend-datasets@0.1.6.0` (sklearn's datasets) · `mlbend-huggingface@0.1.1.0` (HF client) · `mlbend-cluster@0.1.0.0` (functional k-means) · `mlbend-metrics@0.1.0.0` (evaluation) · `mlbend-pipeline@0.1.0.0` · `mlbend-preprocess@0.1.0.0` (sklearn transformers over bend-ml's matrix) · `mlbend-select@0.1.0.0` (k-fold CV) · `mlbend-split@0.1.1.0` (seeded stratified split) | ⚠️ no public repo found yet · `import mlbend-datasets@0.1.6.0/main.bend` |
| [bend-ml-tensor-gpu](https://hub.bend-lang.com/n/bend-ml-tensor-gpu) `@0.1.2.1` · [bend-ml-tensor-fork](https://hub.bend-lang.com/n/bend-ml-tensor-fork) `@0.1.2.0` | **New** — tensor-array's products on the GPU; parallel blocks sharing operands (`par1`..`par4`) | [repo](https://github.com/nuxyel/bend-ml) |
| [bend-ml-llama](https://hub.bend-lang.com/n/bend-ml-llama) `@0.1.1.0` · [bend-ml-binary-read](https://hub.bend-lang.com/n/bend-ml-binary-read) `@0.1.0.0` | **New** — Llama-architecture LMs (SmolLM2 family) in Bend 2; little-endian F32 weight loading | [repo](https://github.com/nuxyel/bend-ml) |
| [bend-ml-autograd](https://hub.bend-lang.com/n/bend-ml-autograd) `@0.1.1.0` | Automatic differentiation **with a proved law** | [repo](https://github.com/nuxyel/bend-ml) · `import bend-ml-autograd@0.1.1.0/autograd.bend` |
| [bend-ml-bpe-tokenizer](https://hub.bend-lang.com/n/bend-ml-bpe-tokenizer) `@0.1.3.0` | Byte-level BPE tokenizer with proved roundtrip | [repo](https://github.com/nuxyel/bend-ml) · `import bend-ml-bpe-tokenizer@0.1.3.0/bpe.bend` |
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
| [bend-kit-postgres](https://hub.bend-lang.com/n/bend-kit-postgres) `@0.2.0.0` / [bend-kit-redis](https://hub.bend-lang.com/n/bend-kit-redis) `@0.2.0.0` | Postgres protocol 3.0 + SCRAM; Redis/Valkey RESP3 client with pipelining | via [bend-kit](https://github.com/paymog/bend-kit) |
| [bend-kit-runner](https://hub.bend-lang.com/n/bend-kit-runner) `@0.10.0.1` | Durable job runner: journaled scheduler queue, bounded resource pool, retry + breaker per target — **closes the "run background jobs" gap** | via [bend-kit](https://github.com/paymog/bend-kit) · `import bend-kit-runner@0.10.0.1/runner.bend` |
| [bend-kit-commands](https://hub.bend-lang.com/n/bend-kit-commands) `@0.4.0.0` / [bend-kit-gateway](https://hub.bend-lang.com/n/bend-kit-gateway) `@0.2.0.0` | Retry-safe commands (SQLite-transactional outbox); guarded read-through gateway (authorize, cache, fetch on miss) | via [bend-kit](https://github.com/paymog/bend-kit) |
| [bend-visgraph](https://hub.bend-lang.com/n/bend-visgraph) `@2.0.0.0` | **New** — ts2vg's visibility graphs of time series, in Bend 2, "on every CPU thread" | ⚠️ no public repo found yet · `import bend-visgraph@2.0.0.0/bend_visgraph.bend` |
| [bend-kit-crdt](https://hub.bend-lang.com/n/bend-kit-crdt) `@0.1.1.0` / [bend-kit-migrate](https://hub.bend-lang.com/n/bend-kit-migrate) `@0.2.0.0` | **New** — replicated data types (grow-only counters with proved merges); versioned subscription records (validated JSON decode, proved migrations, encode) | via [bend-kit](https://github.com/paymog/bend-kit) |

### Dev tooling

| Package | What | Links |
|---|---|---|
| [bolt](https://hub.bend-lang.com/n/bolt) `@1.19.0.0` | Linter, checker **and language server** for Bend 2 (~40 lint rules) | `import bolt@1.19.0.0/main.bend` · ⚠️ no public repo found yet |
| [ezx](https://hub.bend-lang.com/n/ezx) `@1.13.0.0` | `ez`, the package manager for Bend 2 | ⚠️ no public repo found yet |
| [shake](https://hub.bend-lang.com/n/shake) `@0.8.0.0` | Proven CLI argument parser with subcommands and help | ⚠️ no public repo found yet |
| [snap](https://hub.bend-lang.com/n/snap) `@1.5.0.0` | Run programs from Bend 2 with argv as a string list, no shell | ⚠️ no public repo found yet |
| [bend-lint-api](https://hub.bend-lang.com/n/bend-lint-api) `@0.2.0.0` + [bend-lint-rules](https://hub.bend-lang.com/n/bend-lint-rules) `@0.2.0.0` | Lint-rule framework for Bend (`rule()`) plus ~40 rules: language, layout, performance, suspicious patterns | ⚠️ no public repo found yet |
| [bend-lint-pack](https://hub.bend-lang.com/n/bend-lint-pack) `@0.1.1.0` | **New** — BendHub entry publishing all five lint rules + helpers (complexity, dead defs, graph fan-in/fan-out) | ⚠️ no public repo found yet · `import bend-lint-pack@0.1.1.0/all.bend` |
| [bend-semver-checks](https://hub.bend-lang.com/n/bend-semver-checks) `@0.1.0.0` / [bend-toon-codec](https://hub.bend-lang.com/n/bend-toon-codec) `@0.1.0.0` | **New** — semver diff/law/text checks; TOON codec (decode/encode/frame/json/num/text) — same GPL publisher family as bend-lint-pack, no repo found | ⚠️ no public repo found yet |
| [bend-kit-property](https://hub.bend-lang.com/n/bend-kit-property) `@0.3.0.0` | **Updated** — reproducible property checks with generated inputs and greedy shrinking (was generators-only) | via [bend-kit](https://github.com/paymog/bend-kit) |
| [bendcheck](https://hub.bend-lang.com/0x738b30530890e825e0ab81092b94cbfc/check.bend) | **New** — "property-based testing for Bend" (`check.bend`) | `import 0x738b30530890e825e0ab81092b94cbfc/check.bend` · ⚠️ no public repo found yet |

### The `bend-kit` standard library

The most-depended-on packages on the hub (`bend-kit-bytes` has 99 dependents). Actively versioned monorepo — [paymog/bend-kit](https://github.com/paymog/bend-kit). Import per package, e.g. `import bend-kit-http@0.36.0.0/http.bend`:

`bytes` · `json` · `encoding` · `url` · `wire` (TCP/UDP/TLS) · `http` (HTTP/1.1+2 client, HTTP/1.1 server) · `http2` (HPACK) · `camber` (fixed prepared HTTP apps) · `hairpin` (HTTP client: pool, cookies, mTLS, retries) · `crypto` (OpenSSL 3: hashes, HMAC, HKDF, RSA/ECDSA) · `regex` (RE2 syntax, Pike VM, linear time) · `collections` (maps, vector, deque, priority queue) · `parse` (parser combinators) · `time` · `zlib` · `dns` · `files` · `fmt` · `int` (U8–I64) · `f64` (IEEE 754 binary64) · `bignum` (bigint/decimal/rational) · `hash` (FNV-1a, xxHash, SipHash) · `property` (reproducible property checks + greedy shrinking) · `notch` (structured logging) · `jwt` · `oauth2` · `sigv4` (AWS) · `multipart` · `netip` · `websocket` · `webhooks` · `router` · `tar` · `archive` (ZIP) · `cbor` · `csv` · `tty` · `unicode` (UCD 17.0.0) · `stream` · `process` · `sqlite` · `postgres` · `redis` · `llm` (Anthropic + OpenAI, SSE streaming) · `authz` · `cache` · `journal` · `lemmas` (proved Word/U32↔Nat laws) · `protobuf` · `resources` · `retry` · `scheduler` · `runner` (durable job runner) · `commands` (retry-safe commands) · `gateway` (guarded read-through gateway) · `crdt` (proved grow-only counters — new) · `migrate` (proved migrations — new)

### Polished small families

- [**emerging-ez\***](https://hub.bend-lang.com/n/emerging-ezjson) (all MIT, all with top-level LICENSE): `ezjson` (parser/printer/pull cursor) · `eztoml` (proven parser/renderer) · `ezhttp` (client+server, auth/cookies/CORS) · `ezimg` (PNG + baseline JPEG) · `ezaudio` (WAV + MP3)
- [**gralha-\***](https://hub.bend-lang.com/n/gralha-text-scan) (all MIT): `text-scan` · `bytes` · `byte-words` · `deflate` · `gzip-frame` (now named) · `crc32` · `image` · `png-decode` · `jpeg-decode` · `css-style` · `xml-doc` · `ustar` · `truetype` · `coverage` · `bendquest` (proof-carrying game-rules kernel) · `raylib` · `http-core` · `http-server` · `svg-render` (new this week) — [repo](https://github.com/nicolas-abril/bend2-libs)
- [**bend-osdev-\***](https://hub.bend-lang.com/n/bend-osdev-word64) (all MIT, all ship `LAWS.bend`/`PROOF.bend`): `word64` · `bytes` · `caps` · `apparmor` · `acpi` · `bpf` · `aead` · `aes` · `algo` · `array` · `cbc` · `cipher-modes` · `crc` · `crypto` · `gf` · `hashes` · `legacy-ciphers` · `mode-core` · `pkcs7` · `u32` (new this week) — OS-dev in Bend with machine-checked laws — [repo](https://github.com/ScottMoore0/bend-osdev)
- **LLM SDKs**: [bend-anthropic-sdk](https://hub.bend-lang.com/n/bend-anthropic-sdk) ([repo](https://github.com/gouveags/anthropic-bend)) and [bend-openai-sdk](https://hub.bend-lang.com/n/bend-openai-sdk) — unofficial SDKs with typed requests, streaming, tool calling
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
| [aaaxn/bendtorch](https://github.com/aaaxn/bendtorch) | `bendtorch-core` + new `bendtorch`/`bendtorch-fast`/`bendtorch-gpu`/`bendtorch-load` — PyTorch-like tensor library in Bend, laws + proofs |
| [nuxyel/bend-ml](https://github.com/nuxyel/bend-ml) | The `bend-ml-*` family: tensors, GPU/fork variants, Llama, BPE tokenizer, autograd |
| [nicolas-abril/bend2-libs](https://github.com/nicolas-abril/bend2-libs) | The `gralha-*` family: bytes, deflate, image codecs, CSS/XML, raylib + http-core, http-server, svg-render |
| [ScottMoore0/bend-osdev](https://github.com/ScottMoore0/bend-osdev) | The `bend-osdev-*` family: word64, bytes, caps, apparmor, acpi, bpf + aead, aes, algo, array, cbc, cipher-modes, crc, crypto, gf, hashes, legacy-ciphers, mode-core, pkcs7, u32 — OS-dev with proved laws |
| [costamatheus97/bend-parallel](https://github.com/costamatheus97/bend-parallel) | `bend-parallel` — parallel histogram/scan/sort |
| [gouveags/anthropic-bend](https://github.com/gouveags/anthropic-bend) | `bend-anthropic-sdk` |
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
- **[@aaaxn](https://github.com/aaaxn)** — `bendtorch`, the PyTorch-like tensor library in Bend
- **[@nuxyel](https://github.com/nuxyel)** — the `bend-ml-*` family (tensors, GPU, Llama, BPE, autograd)
- **[@nicolas-abril](https://github.com/nicolas-abril)** — the `gralha-*` systems/media libraries
- **[@ScottMoore0](https://github.com/ScottMoore0)** — the `bend-osdev-*` verified OS-dev packages
- **[@costamatheus97](https://github.com/costamatheus97)** — `bend-parallel`
- **[@gouveags](https://github.com/gouveags)** — `bend-anthropic-sdk`
- **[@subtleGradient](https://github.com/subtleGradient)** — `bend-over-sqlite` (SQLite for C and Wasm targets); collaborator on this repo

## Looking for source

Promising packages with **no public repository found** — if you know the authors, point them here:

`bend-tensors` · `bend-blas-lapack` · `bend-ml` (`0x53dde92d…`) · tinygrad-laws (`0xe6b82fa6…`) · the LAWS-spec package (`0x983079cc7642…`) · `wordlib` (`0xb13667d5…`) · `bolt` · `ezx` · `shake` · `snap` · `emerging-ezjson/eztoml/ezhttp/ezimg/ezaudio` · `mylsm-lsm-store` · `bend-csv-parser` · `bend-math-lib` · `bend-prot` · `bend-edit-distance` · `bend-lint-api` / `bend-lint-rules` · `bendcheck` (`0x738b3053…`) · `bend-window-capture` · `bend-window-ref` · `bend-init` (`0x1e0cc367…`) · `bend-lawful-stdlib` · `bend-over-js-eval` (`0x646b2235…`) · **new 2026-10-26:** `mlbend-*` (datasets, huggingface, cluster, metrics, pipeline, preprocess, select, split) · `bend-visgraph` · `bendvy-ecs-core` · `bendonnect-rpc` · `bend-lint-pack` · `bend-semver-checks` · `bend-toon-codec` · `cswap-bend-cli` · `cli`

## Ecosystem gaps

What you'd expect in a healthy package ecosystem but won't find on BendHub yet — organized by the job you'd hire it for. Bend 2 is young, so read this as an opportunities list: most of these are one focused package away from existing. ★ marks the ones closest to [Tom's](https://github.com/lilalittle) active work (verified math, tensors, dev tooling).

**Want to build one?** Every gap is a claimable issue with blocked-by relationships — see [CONTRIBUTING.md](CONTRIBUTING.md).

### Build & ship
- **Start a new project** → no scaffolding: no `init` templates or example repos wired to `ez` (a start: unnamed `0x1e0cc367…` is "a proven Bend project in one command", but hash-only with no repo)
- ★ **Format code** → no formatter — no `gofmt`/`black` equivalent anywhere on the hub
- **Edit comfortably** → no Zed extension, no tree-sitter grammar — but a VS Code client now exists: `kbrianps.bend2` (highlighting, live diagnostics, hover, formatting through a bundled bend2-lsp; found via web search 2026-10-26, not a hub package)
- **Publish confidently** → `ezx` (the package manager) has no public repo or docs; the publish flow is tribal knowledge
- **Lock dependencies** → no lockfile story, no audit/vulnerability tooling

### Prove it's correct
- ★ **Run tests** → no general test runner or assertion library; property testing now exists (`bend-kit-property@0.3.0.0`: reproducible property checks with generated inputs + greedy shrinking; `bendcheck` `0x738b3053…`) — partially closed 2026-10-19
- ★ **Check laws before proving** → `lawcheck` (counterexample finder) lives in `bendlib/bendlib` but isn't published as a package
- **Debug & profile** → no debugger, no profiler, no REPL/notebook story
- ★ **Build verified math** → no mathlib equivalent; expressivity gaps limit what pure math can even be stated (see issue #64)

### Numbers & ML
- ★ **Train a model** → autodiff now on the hub (`bend-ml-autograd@0.1.1.0`, "automatic differentiation with a proved law"; `bendtorch@1.1.1.0`: F32 tensors, matmul, autograd tape, losses, SGD, all with laws+proofs) plus GitHub-only `bendygrad`; data-loading helpers arrived 2026-10-26 (`mlbend-datasets`, `mlbend-split`/`mlbend-select`, `mlbend-preprocess`, `mlbend-pipeline`, `mlbend-metrics`, `mlbend-cluster`) — still no optimizer zoo (Adam/RMSprop), no model serialization format
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
- ~~**Run background jobs** → no queue/scheduler~~ — closed 2026-10-19 by `bend-kit-runner@0.6.0.0` (durable job runner: journaled scheduler queue, bounded resource pool, retry + breaker per target)

### Databases
- **Evolve schema** → no migration tooling
- **Query safely** → no query builder or typed query layer
- **Use MySQL/Mongo** → no drivers (Postgres, SQLite, Redis are covered)

### Apps & interfaces
- **Build a TUI** → no terminal-UI library (no progress bars/spinners either)
- **Build a GUI** → nothing
- **Ship a game** → `jonlib` (graphics) + `ezaudio` exist; a typed ECS arrived 2026-10-26 (`bendvy-ecs-core@0.1.0.2`, 367 files) — input, physics, and audio mixing are still missing

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
