# Wishes for `bend-packages`

The source of truth for what this repo is and what it should become.
Each wish states a desired state, where it came from, and how we'd check it.
**Reality is compared against these wishes; every gap becomes an issue.**
A wish changes only by pull request with Tom's (@subtleGradient) recorded approval.

Format: `W-BP-N · kind · status` — kind is `outcome` (a state to reach),
`invariant` (must always hold), or `standing-duty` (ongoing work).
Status: `active` | `proposed` | `superseded` | `withdrawn`.

## A. Purpose — why this repo exists

### W-BP-1 · outcome · active
**Wish:** This repo is the public, evergreen map of the Bend 2 package
ecosystem: what's on BendHub, who publishes it, where its source lives,
and what's missing.
**Source:** repo purpose since creation (2026-09-30); Tom's OSS-radar strategy.
**Check:** a newcomer can answer "what exists for X?" from these files alone.

### W-BP-2 · outcome · active
**Wish:** Someone who just discovered Bend can learn how to contribute to
the packages ecosystem here: how to publish, how to claim work, what good
looks like.
**Source:** Tom, chat 2026-10-01 ("as someone who just recently discovered
bend lang, I wish I knew how to contribute").
**Check:** CONTRIBUTING.md is accurate and a first-time contributor can go
from reading it to a claimed issue without asking a human.

### W-BP-3 · outcome · active
**Wish:** Every named package on BendHub maps to its source repository in
[PACKAGE_REPOS.md](PACKAGE_REPOS.md). Packages with no known repo are
explicitly listed as *looking for source*, never silently omitted.
**Source:** Tom, chat 2026-10-01 (evergreen package → repo map wish).
**Check:** the map covers every named package in the latest snapshot;
unknowns are named, not hidden.

## B. Evergreen rules — what stays fresh, and how fresh

### W-BP-4 · standing-duty · active
**Wish:** The registry snapshot refreshes **weekly, Monday mornings**:
refetch the BendHub API, diff against the previous snapshot, regenerate the
generated files, and update the README's snapshot line and counts.
**Source:** established practice (weekly watch, cron `bend-hub-watch`).
**Check:** no generated file is older than 8 days; the README snapshot date
matches the latest snapshot.

### W-BP-5 · invariant · active
**Wish:** Generated files are never hand-edited. Each carries its generator
and date; curated knowledge lives in `data/` and is edited by hand.
**Source:** Tom's evergreen directive; avoids silent drift.
**Check:** `ALL_PACKAGES.md`, `PACKAGE_REPOS.md`, `DISCORD_REPO_HUNT.md`
all name their generator; `git log` shows no direct edits to them.

### W-BP-6 · standing-duty · active
**Wish:** When the set of packages with unknown repos changes materially
(found or newly published), the Discord repo-hunt comment
([DISCORD_REPO_HUNT.md](DISCORD_REPO_HUNT.md)) is regenerated and reposted.
**Source:** Tom, chat 2026-10-01 (evergreen Discord comment wish).
**Check:** the posted comment's package list matches the current unknown set.

### W-BP-7 · invariant · active
**Wish:** This wishes file and [MAINTENANCE.md](MAINTENANCE.md) live **in
this repo** and are the source of truth for what the repo should be and how
it is kept. No copy elsewhere overrides them.
**Source:** Tom, chat 2026-10-01 ("everything about the bend-packages repo
should be specified in wishes"; "the source of truth for the instructions
you follow to refresh the repo lived inside the repo itself").
**Check:** the refresh runbook is followed from MAINTENANCE.md, not from
memory or chat history.

## C. Issue graph — what issues exist, their states, their relationships

### W-BP-8 · outcome · active
**Wish:** The repo has exactly 12 umbrella issues, one per domain, labeled
`umbrella`: Build & ship (#1), Prove it's correct (#2), Numbers & ML (#3),
Data (#4), Web services (#5), Databases (#6), Apps & interfaces (#7),
Text & documents (#8), Operate in prod (#9), Ecosystem health (#10),
formalized-math umbrella (#66), and the BHAG meta-umbrella (#65). Each
umbrella's body checklists its member issues.
**Source:** established structure (2026-09-30).
**Check:** 12 open issues carry the `umbrella` label; each links its members.

### W-BP-9 · outcome · active
**Wish:** Every ecosystem gap is exactly one issue with: the job to be
done, what's already on the hub, a suggested approach, and a definition of
done. No gap lives only in the README.
**Source:** established structure; CONTRIBUTING.md.
**Check:** each README gap bullet resolves to an issue; no orphan bullets.

### W-BP-10 · invariant · active
**Wish:** Issue relationships live **only** in GitHub-native blocked-by
edges, which are the single source of truth. No *Blocked by / Unlocks /
Builds on* prose sections — prose duplicates go stale, drift out of sync
with the edges, and are unnecessary busy work. If a relationship matters,
it is a blocked-by edge; if it doesn't, it isn't recorded.
**Source:** Tom, chat 2026-10-01 ("avoid state that can become stale…
rely on blocked by edge and NOT include blockers in prose").
**Check:** planning order derives from native edges; issues carry no prose
relationship sections. (As of 2026-10-01 relationships are prose-only —
migrating them to native edges and deleting the prose is tracked work.)

### W-BP-11 · invariant · active
**Wish:** Issue states mean what they say:
- **open, unassigned** — unclaimed, waiting for someone;
- **open, assigned** — claimed, with a claim comment on the issue;
- **closed** — done, with a link to the merged/published work as evidence.
**Source:** CONTRIBUTING.md ("How to claim work").
**Check:** no assigned issue lacks a claim comment; no closed issue lacks
evidence. (As of 2026-10-01 nothing is assigned — the claim flow is
untested.)

### W-BP-12 · outcome · active
**Wish:** Every package with no known source repo has a `question`-labeled
source-hunt issue asking *who wrote this?*, and the set of source-hunt
issues matches the unknown set in PACKAGE_REPOS.md.
**Source:** CONTRIBUTING.md ("Source-hunt issues"); W-BP-3.
**Check:** unknown count in the map == open source-hunt issues. (As of
2026-10-01: 5 hunt issues vs ~23 unknown packages — gap tracked.)

### W-BP-13 · invariant · active
**Wish:** Labels mean one thing each: `umbrella` (domain epic),
`enhancement` (build this), `good first issue` (leaf: no Blocked-by, build
anytime), `help wanted` (needs a human), `question` (source-hunt or RFC),
`documentation`.
**Source:** established labeling (2026-09-30).
**Check:** `good first issue` issues have no blockers; every leaf
gap carries the label.

### W-BP-14 · standing-duty · active
**Wish:** The issue graph is garbage-collected by the wish-gap process:
wishes are the roots; an issue that serves no wish and blocks nothing is
proposed for closure with its history intact, never silently deleted.
**Source:** Tom's mark-and-sweep directive (north#8).
**Check:** every sweep proposal links its GC report; closed issues keep full
bodies and comments.

## D. Contribution

### W-BP-15 · outcome · active
**Wish:** Claiming work is one comment: "I'm taking this" on the issue.
Scope discussion happens in the issue, not the umbrella. Blocked issues
welcome design discussion but not core code until dependencies land.
**Source:** CONTRIBUTING.md.
**Check:** the flow works end-to-end for a first-time claimant.

### W-BP-16 · invariant · active
**Wish:** If you publish Bend packages, put a `Source:` link in your hub
description — it's how this repo (and everyone else) finds your code.
**Source:** README ("Repositories"); only 3 repos are hub-linked today.
**Check:** the unknown set in PACKAGE_REPOS.md shrinks over time.

## E. Meta

### W-BP-17 · invariant · active
**Wish:** Proposals to change this repo arrive as pull requests, never as
attachments or bare instructions. A PR approval is the decision.
**Source:** Tom's process rules (chat 2026-10-01; north#10 lesson).
**Check:** no repo change lands without a PR; no separate "approve this PR"
issue exists.

### W-BP-18 · standing-duty · active
**Wish:** Public attribution points to Tom (@subtleGradient) for his work;
automation is credited to North (lilalittle) as maintainer.
**Source:** Tom's attribution rule (2026-10-01).
**Check:** README credits and package authorship name the human.
