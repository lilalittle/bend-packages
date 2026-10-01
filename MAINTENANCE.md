# Maintenance — the refresh runbook

This file is the source of truth for how this repo is kept evergreen.
Follow it; don't improvise from memory. (W-BP-7)

## Schedule

**Weekly, Monday mornings** (cron `bend-hub-watch`). One pass:

1. **Fetch** the BendHub registry API, paginated:
   `https://hub.bend-lang.com/packages.json?sort=hot&limit=25&after=N`
   for `after = 0, 25, 50, …` until a page returns fewer than 25 records.
   Each record: `{hash, files, bytes, ts, desc, name, version, dependents,
   mentions, score, hot, license}`.
2. **Snapshot** the raw records to the snapshots dir as
   `packages-YYYY-MM-DD.json` (kept alongside the generator's workspace;
   the repo only carries the generated outputs).
3. **Diff** package hashes + `name@version` pairs against the previous
   snapshot. Descriptions are whitespace-normalized before comparing (the
   fetch tool wraps long lines) — diff on hash/version/desc-content, never
   raw bytes.
4. **Regenerate** the generated files (below).
5. **Update** the README's snapshot line (date, totals) and any curated
   sections affected by the diff (new repos found → Repositories table,
   found source → remove from "Looking for source").
6. **Report** only what's genuinely new: new packages, new versions of
   tracked names, newly discovered source repos. An unchanged week stays
   silent.

## Generated vs curated

| File | Kind | Generator |
|---|---|---|
| `ALL_PACKAGES.md` | generated | `bin/gen_all_packages.py` from latest snapshot |
| `PACKAGE_REPOS.md` | generated | `bin/gen_package_repos.py` from latest snapshot + `data/package_repos.json` |
| `DISCORD_REPO_HUNT.md` | generated | `bin/gen_package_repos.py` (same run) |
| `README.md` | curated (snapshot line updated each refresh) | by hand |
| `CONTRIBUTING.md` | curated | by hand |
| `WISHES.md` | curated — changes need Tom's approval via PR | by hand |
| `data/package_repos.json` | curated knowledge: package → repo | by hand |
| `bin/*.py` | curated tooling | by hand |

Never hand-edit a generated file (W-BP-5). To correct a generated file,
fix its generator or its `data/` input and re-run.

## Regenerating manually

```bash
# from the repo root, with a fresh snapshot at SNAP:
python3 bin/gen_package_repos.py SNAP data/package_repos.json
# writes PACKAGE_REPOS.md and DISCORD_REPO_HUNT.md in place
```

`gen_all_packages.py` lives with the snapshot tooling; its output is
committed here as `ALL_PACKAGES.md`.

## The Discord repo-hunt comment

`DISCORD_REPO_HUNT.md` is a copy-paste-ready comment for the Bend Discord.
Repost it when the unknown-repo set changes materially (W-BP-6): a package
found its repo, or a notable new package appeared without one. Don't spam
it weekly — post on change.

## Curating `data/package_repos.json`

Shape:

```json
{
  "packages": {
    "<name>": {"repo": "owner/name", "via": "hub|curated", "note": "…"},
    "<name>": {"repo": null, "note": "why it's unknown / where to look"}
  },
  "github_only": {
    "<name>": {"repo": "owner/name", "note": "not on BendHub"}
  }
}
```

- `via: "hub"` — the hub description carries a `Source:` link (detected
  automatically; only 3 repos today).
- `via: "curated"` — found by searching; note how, so it can be re-verified.
- `repo: null` — unknown; this is what feeds the hunt list and the
  source-hunt issues (W-BP-12).

## Corrections

Anyone can open an issue or PR: wrong repo link, missing package, stale
counts. Corrections to generated files are applied to `data/` or the
generator and regenerated — never patched in the output.

## Who

Maintained by [North](https://github.com/lilalittle) 🧭 for
[@subtleGradient](https://github.com/subtleGradient). Tom is a collaborator
with write access; his approval is required for WISHES.md changes and any
externally visible commitment.
