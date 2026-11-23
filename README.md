# Bend 2 Package Ecosystem

A curated, regularly refreshed overview of [BendHub](https://hub.bend-lang.com) — the package registry for [Bend 2](https://github.com/bendlang/bend), the massively-parallel language with machine-checked proofs.

> **Snapshot: 2026-11-23** · **1489 packages** — 245 named, 331 hash-only · refreshed weekly.
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
| [bend-mathlib](https://hub.bend-lang.com/n/bend-mathlib) `@0.8.1.1` | 231 machine-checked lemmas (Nat, Bool, List, String, Maybe, equality, order, algebra, permutations, sorting, machine words) — zero `@unsafe` | [repo](https://github.com/bendlib/bendlib) · `import bend-mathlib@0.8.1.1/nat.bend as MNat` |
| [bend-ml-nat-lemmas](https://hub.bend-lang.com/n/bend-ml-nat-lemmas) `@0.1.1.0` | Proved Nat/List lemmas that Bend's Base doesn't ship — complements bend-mathlib | [repo](https://github.com/nuxyel/bend-ml) · `import bend-ml-nat-lemmas@0.1.1.0/main.bend` |
| [bend-schema-lib](https://hub.bend-lang.com/n/bend-schema-lib) `@0.1.0.0` | Schema validation library | `import bend-schema-lib@0.1.0.0/core.bend` · ⚠️ no public repo found yet |
| [qasim-bend-kit](https://hub.bend-lang.com/n/qasim-bend-kit) `@0.1.0.2` | JSON library with correctness laws and machine-checked proofs | ⚠️ no public repo found yet |
| [bend-kit-lemmas](https://hub.bend-lang.com/n/bend-kit-lemmas) `@0.1.5.1` | Proved laws relating Word and U32 arithmetic to Nat | via [bend-kit](https://github.com/paymog/bend-kit) |
| [bend-float64](https://hub.bend-lang.com/n/bend-float64) `@0.1.8.0` | **New — IEEE 754 float64 in pure Bend, correctly rounded**, with x86-64's bits (NaNs included): math (exp/log/trig/power), sqrt, formatting, text conversion — each with its own `*_LAWS.bend`/`*_PROOF.bend` (nine releases in a week) | `import bend-float64@0.1.8.0/float64.bend` · ⚠️ no public repo found yet |
| [bend-quant-signal](https://hub.bend-lang.com/n/bend-quant-signal) `@0.1.0.0` | **New — cross-sectional signal evaluation**: rank IC, IC, summary + Newey-West t over a T × N float32 panel, **26 proved laws** (alignment, causality, ranks — a signal built from its transforms can't see the future); values checked against scipy/pandas/statsmodels | [repo](https://github.com/robinmarin/bend-quant) · `import bend-quant-signal@0.1.0.0/signal.bend` |
| [bend-prot](https://hub.bend-lang.com/n/bend-prot) `@0.1.0.0` | **New** — protein/RMSD/PDB simulation with `LAWS.bend`/`PROOF.bend` | `import bend-prot@0.1.0.0/protein.bend` · ⚠️ no public repo found yet |
| [bend-collections-laws](https://hub.bend-lang.com/n/bend-collections-laws) `@1.0.0.0` (+ `-containers`, `-crypto`, `-math`) | Machine-checked law suites for containers, crypto, math — the largest packages on the hub | [repo](https://github.com/Giulio2002/bend-collections) |
| [bend-csv-parser](https://hub.bend-lang.com/n/bend-csv-parser) `@0.1.0.1` | Fast CSV parser **with proofs** | `import bend-csv-parser@0.1.0.1/core.bend` |
| [bend-trace-context](https://hub.bend-lang.com/n/bend-trace-context) `@0.2.0.0` | W3C Trace Context propagation, rules proved as laws | [repo](https://github.com/LucasGois1/bend-trace-context) |
| [bend-lawful-stdlib](https://hub.bend-lang.com/n/bend-lawful-stdlib) `@0.1.0.0` | Typeclass-style Ord / Semigroup / Group with their laws | `import bend-lawful-stdlib@0.1.0.0/src/class.bend` |
| [wordlib](https://hub.bend-lang.com/0xb13667d52aa56e002b4d09883d7fce3e/word.bend) | Laws about Base's fixed-width words, with `LAWS.bend`/`PROOF.bend` | `import 0xb13667d52aa56e002b4d09883d7fce3e/word.bend` |
| [lawful-words](https://hub.bend-lang.com/n/lawful-words) `@0.1.0.1` · [lawful-arrays](https://hub.bend-lang.com/n/lawful-arrays) `@0.1.0.1` · [lawful-bytes](https://hub.bend-lang.com/n/lawful-bytes) `@0.1.1.1` · [lawful-fields](https://hub.bend-lang.com/n/lawful-fields) `@0.1.1.1` · [lawful-halves](https://hub.bend-lang.com/n/lawful-halves) `@0.1.0.1` | A law-and-proof family: U32↔Nat arithmetic, Array operations via leaf lists, packed-byte buffers, byte-field splitting, balanced fork-join trees — all with `LAWS.bend`/`PROOF.bend` | [repos](https://github.com/luiscleto/lawful-words) (words, arrays verified; same author family) · `import lawful-words@0.1.0.1/defs.bend` |
| [element-math](https://hub.bend-lang.com/n/element-math) `@0.1.0.0` · [element-crypto](https://hub.bend-lang.com/n/element-crypto) `@0.1.0.0` (+ 11 more `element-*`) | **New — a stdlib-grade suite from the Element browser engine**: big naturals with Montgomery arithmetic, correctly-rounded binary64 transcendentals, full crypto (AES-GCM, ChaCha20-Poly1305, X25519, ECDSA, RSA), TLS 1.3, X.509, HTTP, HTML, CSS, PNG, DEFLATE — Apache-2.0, several with `LAWS.bend`/`PROOF.bend` | [repo](https://github.com/jonasporto/element-bend-libs) · `import element-math@0.1.0.0/f64.bend` |

The `bendlib` repo also ships [**lawcheck**](https://github.com/bendlib/bendlib) — finds counterexamples to your laws *before* you try to prove them.

### Tensors, autodiff & ML

| Package | What | Links |
|---|---|---|
| [bend-ml-tensor](https://hub.bend-lang.com/n/bend-ml-tensor) `@0.1.2.0` | **Tensors with the shape in the TYPE** — "a shape error is a type error" | [repo](https://github.com/nuxyel/bend-ml) · `import bend-ml-tensor@0.1.2.0/tensor.bend` |
| [bend-ml-tensor-array](https://hub.bend-lang.com/n/bend-ml-tensor-array) `@0.1.21.0` | Tensors over a flat Array, shape in the type (still very actively developed) | [repo](https://github.com/nuxyel/bend-ml) · `import bend-ml-tensor-array@0.1.21.0/main.bend` |
| [bend-ndarray](https://hub.bend-lang.com/n/bend-ndarray) `@0.1.4.0` · [bend-gpu-kernels](https://hub.bend-lang.com/n/bend-gpu-kernels) `@0.1.0.0` · [bend-gpu-attention](https://hub.bend-lang.com/n/bend-gpu-attention) `@0.3.0.0` · [bend-gpu-cublas](https://hub.bend-lang.com/n/bend-gpu-cublas) `@0.1.3.0` | **New — a second ML stack landed in one week**: NumPy-style n-d arrays with **broadcasting proved** (`bend-ndarray`, `.npy` I/O, RNG); data-parallel GPU kernels in plain Bend 2 — RMSNorm, int8 quant, SwiGLU, softmax — with laws+proofs (`bend-gpu-kernels`); fused FlashAttention-style attention, FP16/int8 tensor cores, no score matrix (`bend-gpu-attention`); cuBLAS GEMMs + a GPU weight store (`bend-gpu-cublas`) | ⚠️ no public repo found yet · `import bend-ndarray@0.1.4.0/ndarray.bend` · `import bend-gpu-kernels@0.1.0.0/nn.bend` |
| [bend-kit-f32array](https://hub.bend-lang.com/n/bend-kit-f32array) `@0.2.1.1` | **New — packed F32 arrays**: get/set/slice/concat/map/fold/zip/dot/sum/max, little/big-endian Bytes + files, with parallel + IO modules — the F32 substrate the tensor work keeps needing, now a proper package | via [bend-kit](https://github.com/paymog/bend-kit/tree/main/f32array) · `import bend-kit-f32array@0.2.1.1/f32array.bend` |
| [bend-cuda-launcher](https://hub.bend-lang.com/n/bend-cuda-launcher) `@0.1.0.0` · [bend-gpu-heap](https://hub.bend-lang.com/n/bend-gpu-heap) `@0.1.0.0` · [bend-safetensors-reader](https://hub.bend-lang.com/n/bend-safetensors-reader) `@0.1.0.0` · [bend-bpe-tokenizer](https://hub.bend-lang.com/n/bend-bpe-tokenizer) `@0.1.0.0` | **New — same cluster**: write CUDA kernels as source text in Bend, compile at run time (NVRTC), launch on Bend arrays; bulk-prefetch Bend's GPU heap back to CPU; read `.safetensors` into Bend arrays (checked header parser **with laws**, tensor lookup, raw/F32 loads); HF byte-level BPE tokenizers (Qwen2/3, Qwen3.5+, Llama 3, GPT-2), id for id with `tokenizers`, with laws | ⚠️ no public repo found yet · `import bend-cuda-launcher@0.1.0.0/cuda.bend` · `import bend-safetensors-reader@0.1.0.0/st.bend` · `import bend-bpe-tokenizer@0.1.0.0/bpe.bend` |
| [bendtorch-core](https://hub.bend-lang.com/n/bendtorch-core) `@0.1.0.0` | PyTorch-like tensor library in Bend: F32 tensors, matmul, autograd tape, losses, SGD — laws and proofs throughout (~180 files) | [repo](https://github.com/aaaxn/bendtorch) · `import bendtorch-core@0.1.0.0/src/tensor/core.bend` |
| [bendtorch](https://hub.bend-lang.com/n/bendtorch) `@2.1.0.0` (+ [bendtorch-fast](https://hub.bend-lang.com/n/bendtorch-fast), [bendtorch-gpu](https://hub.bend-lang.com/n/bendtorch-gpu), [bendtorch-load](https://hub.bend-lang.com/n/bendtorch-load)) | **2.0 — optimizer zoo + bit-exact serialization**: SGD, SGD+momentum, Adam ±L2, AdamW, AdamW-BF16; `Train.save`/`Params.save` resume bit-exact, safetensors loading — **closes the "Train a model" gap** (no RMSprop yet; serialization has no header/descriptor, U32 reader limits). 2.0.2 (2026-11-07) on Bend 2.0.40: SmolLM2-135M step 4.3s → 3.3s on 16 threads | [repo](https://github.com/nuxyel/BendTorch) · `import bendtorch@2.1.0.0/tensor.bend` |
| [mlbend-*](https://hub.bend-lang.com/n/mlbend-datasets) `@0.1.x` | **New — a sklearn-shaped ML stack in one week**: `mlbend-datasets@0.1.6.0` (sklearn's datasets) · `mlbend-huggingface@0.1.1.0` (HF client) · `mlbend-cluster@0.1.0.0` (functional k-means) · `mlbend-metrics@0.1.0.0` (evaluation) · `mlbend-pipeline@0.1.0.0` · `mlbend-preprocess@0.1.0.0` (sklearn transformers over bend-ml's matrix) · `mlbend-select@0.1.0.0` (k-fold CV) · `mlbend-split@0.1.1.0` (seeded stratified split) · **now also** `mlbend-generative@0.1.1.0` (generative skeleton) · `mlbend-report@0.1.0.0` (confusion matrix, per-class report) | ⚠️ no public repo found yet · `import mlbend-datasets@0.1.6.0/main.bend` |
| [bend-ml-tensor-gpu](https://hub.bend-lang.com/n/bend-ml-tensor-gpu) `@0.1.5.3` · [bend-ml-tensor-fork](https://hub.bend-lang.com/n/bend-ml-tensor-fork) `@0.1.7.2` | tensor-array's products on the GPU; parallel blocks sharing operands (`par1`..`par4`) | [repo](https://github.com/nuxyel/bend-ml) |
| [bend-ml-llama](https://hub.bend-lang.com/n/bend-ml-llama) `@0.3.0.0` · [bend-ml-binary-read](https://hub.bend-lang.com/n/bend-ml-binary-read) `@0.2.0.1` | Llama-architecture LMs (SmolLM2 family) in Bend 2; little-endian F32 weight loading | [repo](https://github.com/nuxyel/bend-ml) |
| [bend-ml-autograd](https://hub.bend-lang.com/n/bend-ml-autograd) `@0.1.1.0` | Automatic differentiation **with a proved law** | [repo](https://github.com/nuxyel/bend-ml) · `import bend-ml-autograd@0.1.1.0/autograd.bend` |
| [bend-ml-bpe-tokenizer](https://hub.bend-lang.com/n/bend-ml-bpe-tokenizer) `@0.1.3.0` | Byte-level BPE tokenizer with proved roundtrip | [repo](https://github.com/nuxyel/bend-ml) · `import bend-ml-bpe-tokenizer@0.1.3.0/bpe.bend` |
| [bend-tensors](https://hub.bend-lang.com/n/bend-tensors) `@0.0.0.2` | Dense linear algebra with **shapes in the types** (MIT) | `import bend-tensors@0.0.0.2/bend_tensors.bend` · ⚠️ no public repo found yet |
| [bend-blas-lapack](https://hub.bend-lang.com/n/bend-blas-lapack) `@0.0.0.1` | BLAS, LAPACK and cuBLAS — one def per routine, with C/JS shims | `import bend-blas-lapack@0.0.0.1/blas.bend` · ⚠️ no public repo found yet |
| [bend-ml](https://hub.bend-lang.com/0x53dde92df75268075f1bc6c33ecbb079/bend_ml.bend) | Parallel linear regression, batches, statistics, metrics — **with `LAWS.bend`/`PROOF.bend`** | `import 0x53dde92df75268075f1bc6c33ecbb079/bend_ml.bend` · ⚠️ no public repo found yet |
| [stelliferous](https://hub.bend-lang.com/n/stelliferous) `@0.0.4.0` | **New — tensor + convolution library, written and proved in Bend**: F32 tensors, conv2d, max_pool2d, activations; native convolution proved equal to its matrix spec bit-for-bit, plus a kernel cost model | [repo](https://github.com/Kaz9487/Stelliferous) · `import stelliferous@0.0.4.0/tensor_f32.bend as F` |
| [tinygrad-laws](https://hub.bend-lang.com/0xe6b82fa6c4c459c7023adf4b12a3ac46) | "The laws of tinygrad, stated for the Bend port" — someone is porting tinygrad to Bend too | `tensor.bend`, `shape.bend`, `nat.bend` + laws |
| [BendSR](https://hub.bend-lang.com/0xb1a81026c64fbbc00a8570155d77383d/BendSR.bend) | Massively parallel symbolic regression engine | [repo](https://github.com/k3ybladewielder/BendSR) |
| **bendygrad** | tinygrad front-end in Bend 2: views, buffers, autodiff, SGD — **GitHub only, not on the hub** | [repo](https://github.com/KapioKai/bendygrad) |

### Parallelism & systems

| Package | What | Links |
|---|---|---|
| [bend-parallel](https://hub.bend-lang.com/n/bend-parallel) `@0.1.0.0` | Parallel histogram, scan, sort (Apache-2.0) | `import bend-parallel@0.1.0.0/histogram.bend` |
| [bend-kit-concurrency](https://hub.bend-lang.com/n/bend-kit-concurrency) `@0.2.0.0` | Parallel map/reduce, worker pool, channel select, timeouts | `import bend-kit-concurrency@0.2.0.0/concurrency.bend` |
| [mylsm-lsm-store](https://hub.bend-lang.com/n/mylsm-lsm-store) `@0.6.0.2` | A **full LSM-tree storage engine in pure Bend** — memtable, WAL, SST files, merge iterators, crash-point testing (BSD-3-Clause) | `import mylsm-lsm-store@0.6.0.2/mylsm.bend` |
| [ber-core-store](https://hub.bend-lang.com/n/ber-core-store) `@0.1.2.0` | Content-addressed / Merkle state-tree store with certified merges (BSD-3-Clause) | [repo](https://github.com/FabianVegaA/ber) |
| [bend-kit-storage](https://hub.bend-lang.com/n/bend-kit-storage) `@0.6.0.1` | Content-addressed object store: Merkle trees, sync plans, reachability GC **with proved laws** | via [bend-kit](https://github.com/paymog/bend-kit/tree/main/storage) · `import bend-kit-storage@0.6.0.1/storage.bend` |
| [bend-kit-sqlite](https://hub.bend-lang.com/n/bend-kit-sqlite) `@0.1.0.0` | Prepared SQLite statements through libsqlite3 | `import bend-kit-sqlite@0.1.0.0/sqlite.bend` |
| [bend-kit-postgres](https://hub.bend-lang.com/n/bend-kit-postgres) `@0.3.1.2` / [bend-kit-redis](https://hub.bend-lang.com/n/bend-kit-redis) `@0.3.1.2` | Postgres protocol 3.0 + SCRAM; Redis/Valkey RESP3 client with pipelining | via [bend-kit](https://github.com/paymog/bend-kit) |
| [bend-kit-runner](https://hub.bend-lang.com/n/bend-kit-runner) `@0.20.0.0` | Durable job runner: journaled scheduler queue, bounded resource pool, retry + breaker per target — **closes the "run background jobs" gap** | via [bend-kit](https://github.com/paymog/bend-kit) · `import bend-kit-runner@0.20.0.0/runner.bend` |
| [bend-kit-commands](https://hub.bend-lang.com/n/bend-kit-commands) `@0.5.1.0` / [bend-kit-gateway](https://hub.bend-lang.com/n/bend-kit-gateway) `@0.5.0.0` | Retry-safe commands (SQLite-transactional outbox); guarded read-through gateway (authorize, cache, fetch on miss) | via [bend-kit](https://github.com/paymog/bend-kit) |
| [bend-visgraph](https://hub.bend-lang.com/n/bend-visgraph) `@2.0.0.0` | **New** — ts2vg's visibility graphs of time series, in Bend 2, "on every CPU thread" | ⚠️ no public repo found yet · `import bend-visgraph@2.0.0.0/bend_visgraph.bend` |
| [bend-kit-crdt](https://hub.bend-lang.com/n/bend-kit-crdt) `@0.2.1.1` / [bend-kit-migrate](https://hub.bend-lang.com/n/bend-kit-migrate) `@0.4.1.0` | Replicated data types (grow-only counters with proved merges); versioned subscription records (validated JSON decode, proved migrations, encode) | via [bend-kit](https://github.com/paymog/bend-kit) |
| [bend-kube-runtime](https://hub.bend-lang.com/n/bend-kube-runtime) `@0.10.0.0` | A Kubernetes runtime in Bend: client, config, leader election, leases, watchers, queues, proxy, serve, store, typed resources, YAML — with `LAWS.bend`/`PROOF.bend` (two more releases this week, still no repo) | ⚠️ no public repo found yet · `import bend-kube-runtime@0.10.0.0/package.bend` |

### GPU & windowing

| Package | What | Links |
|---|---|---|
| [bend-vulkan-library](https://hub.bend-lang.com/n/bend-vulkan-library) `@0.1.0.1` | **New — native Vulkan bindings for Bend**: GPU memory, command recording, synchronization, indexed graphics on 64-bit Linux — with `LAWS.bend`/`PROOF.bend` and examples | [repo](https://github.com/aivv73/bend-vulkan) · `import bend-vulkan-library@0.1.0.1/Vulkan.bend` |
| [bend-window-capture](https://hub.bend-lang.com/n/bend-window-capture) `@0.1.0.4` · [bend-window-ref](https://hub.bend-lang.com/n/bend-window-ref) `@0.1.0.3` | Read a Bend-owned X11 window's client pixels into an affine RGB array; export a window's display name + resource ID without transferring ownership | [repos](https://github.com/aivv73/bend-window-capture) · [bend-window-ref](https://github.com/aivv73/bend-window-ref) |
| [bend-ui-test](https://hub.bend-lang.com/n/bend-ui-test) `@0.1.0.2` | **New** — send key presses, clicks, close requests to Bend-owned X11 windows through copyable references | [repo](https://github.com/aivv73/bend-ui-test) (hub desc links entire.com, not GitHub) |

### Dev tooling

| Package | What | Links |
|---|---|---|
| [bolt](https://hub.bend-lang.com/n/bolt) `@1.67.0.0` | Linter, checker **and language server** for Bend 2 (~40 lint rules) — two more releases this week | `import bolt@1.67.0.0/main.bend` · ⚠️ no public repo found yet |
| [ezmcp](https://hub.bend-lang.com/n/ezmcp) `@0.5.0.0` | **New — MCP servers and clients for Bend 2**: tool servers over stdio or stateless Streamable HTTP, client for stateless HTTP endpoints; JSON-RPC initialize/ping/tools-list/tools-call | [repo](https://github.com/Emerging-Patterns/ezmcp) · `import ezmcp@0.5.0.0/main.bend` |
| [yaml-for-bend](https://hub.bend-lang.com/n/yaml-for-bend) `@0.1.1.0` | **New — YAML for Bend**: read YAML text into values, write values back as YAML | ⚠️ no public repo found yet · `import yaml-for-bend@0.1.1.0/yaml.bend` |
| [ezx](https://hub.bend-lang.com/n/ezx) `@1.18.0.0` | `ez`, the package manager for Bend 2 | ⚠️ no public repo found yet |
| [shake](https://hub.bend-lang.com/n/shake) `@0.9.0.0` | Proven CLI argument parser with subcommands and help | ⚠️ no public repo found yet |
| [snap](https://hub.bend-lang.com/n/snap) `@1.6.0.0` | Run programs from Bend 2 with argv as a string list, no shell | ⚠️ no public repo found yet |
| [bend-lint-api](https://hub.bend-lang.com/n/bend-lint-api) `@0.3.8.0` + [bend-lint-rules](https://hub.bend-lang.com/n/bend-lint-rules) `@0.3.8.0` | Lint-rule framework for Bend (`rule()`) plus ~40 rules: language, layout, performance, suspicious patterns | ⚠️ no public repo found yet |
| [bend-lint-pack](https://hub.bend-lang.com/n/bend-lint-pack) `@0.1.1.0` | **New** — BendHub entry publishing all five lint rules + helpers (complexity, dead defs, graph fan-in/fan-out) | ⚠️ no public repo found yet · `import bend-lint-pack@0.1.1.0/all.bend` |
| [bend-semver-checks](https://hub.bend-lang.com/n/bend-semver-checks) `@0.1.0.0` / [bend-toon-codec](https://hub.bend-lang.com/n/bend-toon-codec) `@0.1.0.0` | **New** — semver diff/law/text checks; TOON codec (decode/encode/frame/json/num/text) — same GPL publisher family as bend-lint-pack, no repo found | ⚠️ no public repo found yet |
| [bend-kit-property](https://hub.bend-lang.com/n/bend-kit-property) `@0.4.0.1` | **Updated** — reproducible property checks with generated inputs and greedy shrinking (was generators-only) | via [bend-kit](https://github.com/paymog/bend-kit) |
| [bend-kit-planner](https://hub.bend-lang.com/n/bend-kit-planner) `@0.5.1.0` | **New — dependency plans with proved order and closure**, incremental invalidation, and a parallel build runner (eight releases in a week) — LAWS/PROOF in the repo | via [bend-kit](https://github.com/paymog/bend-kit/tree/main/planner) · `import bend-kit-planner@0.5.1.0/planner.bend` |
| [bendcheck](https://hub.bend-lang.com/0x738b30530890e825e0ab81092b94cbfc/check.bend) | **New** — "property-based testing for Bend" (`check.bend`) | `import 0x738b30530890e825e0ab81092b94cbfc/check.bend` · ⚠️ no public repo found yet |

### The `bend-kit` standard library

The most-depended-on packages on the hub (`bend-kit-bytes` has 100 dependents). Actively versioned monorepo — [paymog/bend-kit](https://github.com/paymog/bend-kit). Import per package, e.g. `import bend-kit-http@0.40.0.1/http.bend`:

`bytes` · `json` · `encoding` · `url` · `wire` (TCP/UDP/TLS) · `http` (HTTP/1.1+2 client, HTTP/1.1 server) · `http2` (HPACK) · `camber` (fixed prepared HTTP apps) · `hairpin` (HTTP client: pool, cookies, mTLS, retries) · `crypto` (OpenSSL 3: hashes, HMAC, HKDF, RSA/ECDSA) · `regex` (RE2 syntax, Pike VM, linear time) · `collections` (maps, vector, deque, priority queue) · `parse` (parser combinators) · `time` · `zlib` · `dns` · `files` · `fmt` · `int` (U8–I64) · `f64` (IEEE 754 binary64) · `bignum` (bigint/decimal/rational) · `hash` (FNV-1a, xxHash, SipHash) · `property` (reproducible property checks + greedy shrinking) · `notch` (structured logging) · `jwt` · `oauth2` · `sigv4` (AWS) · `multipart` · `netip` · `websocket` · `webhooks` · `router` · `tar` · `archive` (ZIP) · `cbor` · `csv` · `tty` · `unicode` (UCD 17.0.0) · `stream` · `process` · `sqlite` · `postgres` · `redis` · `llm` (Anthropic + OpenAI, SSE streaming) · `authz` · `cache` · `journal` · `lemmas` (proved Word/U32↔Nat laws) · `protobuf` · `resources` · `retry` · `scheduler` · `runner` (durable job runner) · `commands` (retry-safe commands) · `gateway` (guarded read-through gateway) · `crdt` (proved grow-only counters) · `migrate` (proved migrations) · `bits` (bit readers/writers, Huffman tables) · `storage` (content-addressed store, Merkle trees, proved laws) · `markdown` (CommonMark 0.31.2 → HTML) · `stats` (descriptive statistics over F64 lists) · `template` (Mustache, HTML-escaping by default) · `f32array` (packed F32 arrays: dot, sum, max, parallel — new) · `planner` (proved dependency plans + build runner — new) · `text` (Myers diff, Levenshtein, word wrap — new)

### Polished small families

- [**ez\***](https://hub.bend-lang.com/n/ezjson) (all MIT, all with top-level LICENSE): `ezjson` (parser/printer/pull cursor) · `eztoml` (proven parser/renderer) · `ezhttp` (client+server, auth/cookies/CORS) · `ezimg` (PNG + baseline JPEG) · `ezaudio` (WAV + MP3) · **new:** `ezmcp` (MCP servers/clients — [repo](https://github.com/Emerging-Patterns/ezmcp)) · `ezsys` (whole-file reads, atomic saves). Note: `ezjson`/`ezhttp` graduated from the `emerging-` prefix this week (same content hashes, new short names). This week: `ezmcp` → 0.5.0.0, `ezhttp` → 0.26.0.0, `ezjson` → 1.5.0.0, `ezsys` → 0.2.0.0, `emerging-ezaudio` → 0.7.0.0, `emerging-ezimg` → 1.5.0.0, `emerging-eztoml` → 0.11.0.0.
- [**gralha-\***](https://hub.bend-lang.com/n/gralha-text-scan) (all MIT): `text-scan` · `bytes` · `byte-words` · `deflate` · `gzip-frame` (now named) · `crc32` · `image` · `png-decode` · `jpeg-decode` · `css-style` · `xml-doc` · `ustar` · `truetype` · `coverage` · `bendquest` (proof-carrying game-rules kernel) · `raylib` · `http-core` · `http-server` · `svg-render` — whole family bumped to `0.1.0.1` this week — [repo](https://github.com/nicolas-abril/bend2-libs)
- [**bend-osdev-\***](https://hub.bend-lang.com/n/bend-osdev-word64) (all MIT, all ship `LAWS.bend`/`PROOF.bend`): `word64` · `bytes` · `caps` · `apparmor` · `acpi` · `bpf` · `aead` · `aes` · `algo` · `array` · `cbc` · `cipher-modes` · `crc` · `crypto` · `gf` · `hashes` · `legacy-ciphers` · `mode-core` · `pkcs7` · `u32` · **new:** `aria` · `blowfish` · `camellia` · `cast5` · `cipher-core` (now named) — OS-dev in Bend with machine-checked laws — [repo](https://github.com/ScottMoore0/bend-osdev)
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
| [aaaxn/bendtorch](https://github.com/aaaxn/bendtorch) | `bendtorch-core` + the 1.x `bendtorch`/`bendtorch-fast`/`bendtorch-gpu`/`bendtorch-load` — PyTorch-like tensor library in Bend, laws + proofs |
| [nuxyel/BendTorch](https://github.com/nuxyel/BendTorch) | The 2.x `bendtorch`/`bendtorch-fast`/`bendtorch-gpu`/`bendtorch-load` — optimizer zoo + bit-exact serialization |
| [nuxyel/bend-ml](https://github.com/nuxyel/bend-ml) | The `bend-ml-*` family: tensors, GPU/fork variants, Llama, BPE tokenizer, autograd |
| [nicolas-abril/bend2-libs](https://github.com/nicolas-abril/bend2-libs) | The `gralha-*` family: bytes, deflate, image codecs, CSS/XML, raylib + http-core, http-server, svg-render |
| [ScottMoore0/bend-osdev](https://github.com/ScottMoore0/bend-osdev) | The `bend-osdev-*` family: word64, bytes, caps, apparmor, acpi, bpf + aead, aes, algo, array, cbc, cipher-modes, crc, crypto, gf, hashes, legacy-ciphers, mode-core, pkcs7, u32 — OS-dev with proved laws |
| [costamatheus97/bend-parallel](https://github.com/costamatheus97/bend-parallel) | `bend-parallel` — parallel histogram/scan/sort |
| [gouveags/anthropic-bend](https://github.com/gouveags/anthropic-bend) | `bend-anthropic-sdk` |
| [luiscleto/lawful-words](https://github.com/luiscleto/lawful-words) | `lawful-words` — U32↔Nat law library (same author family: `lawful-arrays`, `lawful-bytes`, `lawful-fields`, `lawful-halves`) |
| [Emerging-Patterns/ezmcp](https://github.com/Emerging-Patterns/ezmcp) | `ezmcp` — MCP servers/clients for Bend 2 (the `ez*` family's org) |
| [biocini/tree-sitter-bend](https://github.com/biocini/tree-sitter-bend) | Tree-sitter grammar + highlighting queries for Bend 2 (not a hub package — editor tooling) |
| [jonasporto/element-bend-libs](https://github.com/jonasporto/element-bend-libs) | The whole `element-*` family (13 packages: math, crypto, TLS 1.3, X.509, HTTP, HTML, CSS, image, compress, text, ASN.1, RFC 3986, ints, hostio) — from the Element browser engine |
| [aivv73/bend-vulkan](https://github.com/aivv73/bend-vulkan) | `bend-vulkan-library` — native Vulkan bindings |
| [aivv73/bend-window-capture](https://github.com/aivv73/bend-window-capture) | `bend-window-capture` — X11 window pixels |
| [aivv73/bend-window-ref](https://github.com/aivv73/bend-window-ref) | `bend-window-ref` — X11 window references |
| [aivv73/bend-ui-test](https://github.com/aivv73/bend-ui-test) | `bend-ui-test` — X11 input/lifecycle testing |
| [robinmarin/bend-quant](https://github.com/robinmarin/bend-quant) | `bend-quant-signal` — cross-sectional signal evaluation with 26 proved laws |
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
- **[@nuxyel](https://github.com/nuxyel)** — the `bend-ml-*` family (tensors, GPU, Llama, BPE, autograd) + BendTorch 2.x (optimizer zoo, bit-exact serialization)
- **[@nicolas-abril](https://github.com/nicolas-abril)** — the `gralha-*` systems/media libraries
- **[@ScottMoore0](https://github.com/ScottMoore0)** — the `bend-osdev-*` verified OS-dev packages
- **[@costamatheus97](https://github.com/costamatheus97)** — `bend-parallel`
- **[@gouveags](https://github.com/gouveags)** — `bend-anthropic-sdk`
- **[@luiscleto](https://github.com/luiscleto)** — the `lawful-*` law-and-proof family (words, arrays, bytes, fields, halves)
- **[@Emerging-Patterns](https://github.com/Emerging-Patterns)** (org) — the `ez*` family (`ezjson`, `ezhttp`, `ezmcp`, `ezsys`)
- **[@jonasporto](https://github.com/jonasporto)** — the `element-*` family (math, crypto, TLS 1.3, X.509, HTTP, HTML — from the Element browser engine)
- **[@aivv73](https://github.com/aivv73)** — `bend-vulkan-library` + the X11 window family (`bend-window-capture`, `bend-window-ref`, `bend-ui-test`)
- **[@robinmarin](https://github.com/robinmarin)** — `bend-quant-signal`, cross-sectional signal evaluation with 26 proved laws
- **[@subtleGradient](https://github.com/subtleGradient)** — `bend-over-sqlite` (SQLite for C and Wasm targets); collaborator on this repo

## Looking for source

Promising packages with **no public repository found** — if you know the authors, point them here:

`bend-tensors` · `bend-blas-lapack` · `bend-ml` (`0x53dde92d…`) · tinygrad-laws (`0xe6b82fa6…`) · the LAWS-spec package (`0x983079cc7642…`) · `wordlib` (`0xb13667d5…`) · `bolt` · `ezx` · `shake` · `snap` · `emerging-eztoml/ezimg/ezaudio` (note: `emerging-ezjson`/`emerging-ezhttp` graduated to short names `ezjson`/`ezhttp` this week, same hashes; `ezmcp`'s repo found: `Emerging-Patterns/ezmcp`) · `mylsm-lsm-store` · `bend-csv-parser` · `bend-math-lib` · `bend-prot` · `bend-edit-distance` · `bend-lint-api` / `bend-lint-rules` · `bendcheck` (`0x738b3053…`) · `bend-init` (`0x1e0cc367…`) · `bend-lawful-stdlib` · `bend-over-js-eval` (`0x646b2235…`) · **new 2026-10-26:** `mlbend-*` (datasets, huggingface, cluster, metrics, pipeline, preprocess, select, split) · `bend-visgraph` · `bendvy-ecs-core` · `bendonnect-rpc` · `bend-lint-pack` · `bend-semver-checks` · `bend-toon-codec` · `cswap-bend-cli` · `cli` · **new 2026-11-02:** `bend-kube-runtime` · `mlbend-generative` · `mlbend-report` · `yaml-for-bend` · `bend-pipe-session` · `bend-stdio-pipes` · `minebender-game` · **new 2026-11-09:** repos found for `bend-window-capture`/`bend-window-ref`/`bend-ui-test` (`aivv73/*`), the whole `element-*` family, and the bendtorch 2.x line (`nuxyel/BendTorch`); `bend-kube-runtime` still sourceless after a second search · **new 2026-11-16:** the whole GPU/ML cluster — `bend-ndarray`, `bend-float64`, `bend-bpe-tokenizer`, `bend-safetensors-reader`, `bend-gpu-kernels`, `bend-gpu-attention`, `bend-gpu-cublas`, `bend-gpu-heap`, `bend-cuda-launcher`, `bend-raw-cells` (searched the web, no repo found; not in `nuxyel/bend-ml`'s README) · `bend-kit-markdown` / `bend-kit-template` (no `Source:` in desc; presumed `paymog/bend-kit` subdirs) · `bend-kube-runtime` still sourceless (now 0.8.1.0) · **new 2026-11-23:** repo found for `bend-quant-signal` (`robinmarin/bend-quant`, verified via `Source:` link); still sourceless, searched the web with no repo found: the `hhefesto-*` cluster — ten named packages (`hhefesto-bcrypt`, `hhefesto-bucket`, `hhefesto-entropy`, `hhefesto-json`, `hhefesto-markdown`, `hhefesto-radix`, `hhefesto-sha2`, `hhefesto-text`, `hhefesto-time`, `hhefesto-wire`) plus two hash-only mirrors (`bend-route` `0x23d6c01e…`, `bend-wire` `0xfdfa1bd0…`) — a new publisher re-publishing classic Bend libraries under its own prefix; `bend-kit-planner`/`bend-kit-text` carry no `Source:` either, but their `paymog/bend-kit` subdirs are verified on GitHub · `bend-kube-runtime` still sourceless (now 0.10.0.0)

## Ecosystem gaps

What you'd expect in a healthy package ecosystem but won't find on BendHub yet — organized by the job you'd hire it for. Bend 2 is young, so read this as an opportunities list: most of these are one focused package away from existing. ★ marks the ones closest to [Tom's](https://github.com/lilalittle) active work (verified math, tensors, dev tooling).

**Want to build one?** Every gap is a claimable issue with blocked-by relationships — see [CONTRIBUTING.md](CONTRIBUTING.md).

### Build & ship
- **Start a new project** → no scaffolding: no `init` templates or example repos wired to `ez` (a start: unnamed `0x1e0cc367…` is "a proven Bend project in one command", but hash-only with no repo)
- ★ **Format code** → no formatter — no `gofmt`/`black` equivalent anywhere on the hub (a formatter exists off-hub: the `bendlang/bend` VS Code extension publishes `bend-fmt` to npm — found via web search 2026-11-09; no formatter package on the hub itself)
- **Edit comfortably** → no Zed extension — but a VS Code client now exists: `kbrianps.bend2` (highlighting, live diagnostics, hover, formatting through a bundled bend2-lsp; found via web search 2026-10-26, not a hub package), and a tree-sitter grammar now exists: `biocini/tree-sitter-bend` (generated C parser, language bindings, Neovim setup; found via builtwithbend.com 2026-11-02, not a hub package)
- **Publish confidently** → `ezx` (the package manager) has no public repo or docs; the publish flow is tribal knowledge
- **Lock dependencies** → no lockfile story, no audit/vulnerability tooling

### Prove it's correct
- ★ **Run tests** → no general test runner or assertion library; property testing now exists (`bend-kit-property@0.4.0.1`: reproducible property checks with generated inputs + greedy shrinking; `bendcheck` `0x738b3053…`) — partially closed 2026-10-19
- ★ **Check laws before proving** → `lawcheck` (counterexample finder) lives in `bendlib/bendlib` but isn't published as a package
- **Debug & profile** → no debugger, no profiler, no REPL/notebook story
- ★ **Build verified math** → no mathlib equivalent; expressivity gaps limit what pure math can even be stated (see issue #64)

### Numbers & ML
- ~~★ **Train a model** → autodiff now on the hub (`bend-ml-autograd@0.1.1.0`, "automatic differentiation with a proved law"; `bendtorch@1.3.0.0`: F32 tensors, matmul, autograd tape, losses, SGD, all with laws+proofs) plus GitHub-only `bendygrad`; data-loading helpers arrived 2026-10-26 (`mlbend-datasets`, `mlbend-split`/`mlbend-select`, `mlbend-preprocess`, `mlbend-pipeline`, `mlbend-metrics`, `mlbend-cluster`) and evaluation/generative pieces arrived 2026-11-02 (`mlbend-report`, `mlbend-generative`) — still no optimizer zoo (Adam/RMSprop), no model serialization format~~ — closed 2026-11-09 by `bendtorch@2.0.2.0` + `bendtorch-load@2.0.2.0` (optimizer zoo: SGD, SGD+momentum, Adam ±L2, AdamW, AdamW-BF16; bit-exact serialization with safetensors loading — per author nuxyel's answers to bend-packages issues #23/#25). Residual: no RMSprop; serialization has no header/architecture descriptor, and reader U32 limits block 360M AdamW checkpoints. Progress 2026-11-16: `bend-safetensors-reader@0.1.0.0` (checked safetensors header parser with laws) and the GPU cluster (`bend-gpu-kernels`/`bend-gpu-attention`/`bend-gpu-cublas`, `bend-ndarray` with proved broadcasting) deepen the stack, but the residuals stand.
- **Do statistics** → no distributions, sampling, or hypothesis-testing package — progress 2026-11-16: `bend-kit-stats@0.1.7.0` (descriptive statistics over F64 lists) covers the descriptive leg only — progress 2026-11-23: `bend-quant-signal@0.1.0.0` (rank IC, IC, summary + Newey-West t over a T × N float32 panel, 26 proved laws) adds a hypothesis-testing leg
- ★ **Sparse / FFT / signal** → dense linear algebra only (`bend-tensors`, `bend-ml-tensor`); no sparse matrices, no FFT — progress 2026-11-16: `bend-ndarray@0.1.4.0` (NumPy-style n-d arrays, broadcasting proved) strengthens dense, still no sparse/FFT — progress 2026-11-23: `bend-kit-f32array@0.2.1.1` (packed F32 arrays with dot/sum/max, parallel) strengthens dense again
- **Plot results** → no charting or SVG generation

### Data
- **Read common formats** → YAML arrived 2026-11-02 (`yaml-for-bend@0.1.1.0`: read YAML text into values, write values back as YAML); still no MessagePack, Parquet/Arrow, or PDF
- **Wrangle tables** → no dataframe
- ~~**Validate schemas** → no JSON Schema / validation library~~ — closed 2026-10-05 by `bend-schema-lib@0.1.0.0`

### Web services
- **Build an API** → servers exist (`bend-kit-http`, `ezhttp`); missing middleware, sessions, HTML templating, GraphQL, gRPC/protobuf — progress 2026-11-16: HTML templating arrived (`bend-kit-template@0.2.0.0`, Mustache) and Markdown→HTML (`bend-kit-markdown@0.3.1.0`, CommonMark 0.31.2) — progress 2026-11-23: template → 0.3.0.0, markdown → 0.3.10.0
- ~~**Send email** → no SMTP client~~ — closed 2026-10-12 by [bend-smtp](https://github.com/kbrianps/bend-smtp) (TLS, OAuth, DKIM, SMTPUTF8, attachments; machine-checked proof on the pure core)
- ~~**Run background jobs** → no queue/scheduler~~ — closed 2026-10-19 by `bend-kit-runner@0.6.0.0` (durable job runner: journaled scheduler queue, bounded resource pool, retry + breaker per target)

### Databases
- **Evolve schema** → no migration tooling
- **Query safely** → no query builder or typed query layer
- **Use MySQL/Mongo** → no drivers (Postgres, SQLite, Redis are covered)

### Apps & interfaces
- **Build a TUI** → no terminal-UI library (no progress bars/spinners either)
- **Build a GUI** → nothing (Vulkan bindings arrived — `bend-vulkan-library@0.1.0.1`, native, with LAWS/PROOF — plus X11 window helpers `bend-window-capture`/`bend-window-ref`/`bend-ui-test`, but no GUI toolkit yet)
- **Ship a game** → `jonlib` (graphics) + `ezaudio` exist; a typed ECS arrived 2026-10-26 (`bendvy-ecs-core@0.1.0.7`, 367 files) — input, physics, and audio mixing are still missing

### Text & documents
- **Go multilingual** → no i18n/l10n
- **Search text** → no full-text search index

### Operate in prod
- **Deploy** → no container/CI helpers (a Kubernetes runtime now exists — `bend-kube-runtime@0.10.0.0`, proved laws — but that's a controller runtime, not build/CI tooling)
- **Watch it run** → logging (`notch`) + tracing (`bend-trace-context`) exist; no metrics (Prometheus-style) or alerting

### Meta
- **Publisher concentration** — one publisher (`paymog`) accounts for roughly half of all named packages: great velocity, real bus-factor risk
- **Sourceless packages** — many of the most interesting packages (`bend-tensors`, `bolt`, `ezx`, `bend-ml`…) have no public repo: can't audit them, can't contribute, can't fully rely on them

---

*Curated by [North](https://github.com/lilalittle) 🧭 — a weekly snapshot of the BendHub registry. New packages, version bumps, and newly found repos land here every Monday. Corrections welcome via issues.*
