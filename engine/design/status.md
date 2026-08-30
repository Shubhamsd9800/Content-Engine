# workflow-status.md — the engine, step by step, with live status

**Last revised:** Day 24, 28 Aug 2026.
**What this file is:** the running map of the engine and where every step actually stands.
Companion to `engine/design/blueprint.md` — the single design document. This file holds the live task list; the blueprint holds the design.
**This file carries STATE, not design.** When they disagree: they win on design, this wins on
what is true today. For anything tools-related, `brain/reference/tooling.md` wins over all
three.

Legend: ✅ done · 🟡 built, never run · ⚠️ works but untested end to end · ⛔ blocked · ⬜ not started

---

## THE SHAPE OF IT

Two pipelines. They share exactly ONE file — `brain/swipe.md`. No shared skill, no shared
trigger. Do not re-merge them.

```
                 ┌──────────────────────────────────────┐
                 │        THE DECIDED LAYER  brain/     │
                 │  niche · voice · strategy ·          │
                 │  psychology · ledger · swipe         │
                 │  Filled ONLY by interview.           │
                 └──────────────────┬───────────────────┘
                                    │  read by every skill
              ┌─────────────────────┴──────────────────────┐
  ┌───────────▼──────────────┐              ┌──────────────▼─────────────┐
  │  PIPELINE A — LEARN      │   swipe.md   │  PIPELINE B — WRITE        │
  │  from creators           │─────────────>│  a post                    │
  │  runs about monthly      │  ONE file    │  runs per post             │
  │  ends at swipe.md        │              │  ends at published.md      │
  └──────────────────────────┘              └────────────────────────────┘
```

---

## PIPELINE A — learning shapes from creators

| Step | What happens | Output | Status |
|---|---|---|---|
| A1 | CAPTURE — creators entered in the Creator Capture artifact, exported | `work/creators/creator-roster.md` | ✅ 32, Day 23 |
| A2 | **QUALIFY** — five written gates cut the roster to a watchlist | `work/creators/qualified.md` | 🟡 **skill built Day 24, never run** |
| A3 | FETCH — recent posts + engagement per creator | `<slug>/raw/metrics.csv` | ⬜ **`scout` NOT BUILT** — the last missing piece |
| A4 | RANK — median, then outlier = engagement ÷ median, keep ≥ 2× | `<slug>/raw/pieces.md` | ⬜ lives inside `scout` |
| A5 | LINKS — Shubham copies ~2 post URLs per creator | URLs in `pieces.md` | ⚠️ manual, by design — OpenCLI returns no URLs |
| A6 | TRANSCRIBE — download the winners, run Whisper | `<slug>/raw/reel-NN.md` | ⚠️ tools installed, **never run on a reel** |
| A7 | TEARDOWN — `creator-analyst` | `<slug>/teardown.md` | 🟡 skill fixed Day 23, never run |
| A8 | PROMOTE — 5+ of 10 AND survives the downgrade | `brain/swipe.md` | 🟡 rule exists, file empty |

**A2 note.** A shortlist was produced on Day 23 from capture notes alone, with zero reel data,
and presented as analysis. It was discarded. `qualify` exists so that cut is a repeatable step
with checkable criteria rather than a judgement made in conversation.

**`handles.md` exists again — 22 handles, derived, Day 24.** The Day 23 file was 12 names
hand-cut without criteria; it was archived rather than edited, because editing a list that was
never derived would have carried the bias forward under a cleaner label. The new file came
through the full chain: `creator-roster.md` (32) → `qualify` PASS 1 → `qualified.md` →
Shubham's review in the verdict board → `decisions.md` (11 overturns) → `qualify` PASS 2.
**Pipeline A is unblocked. `scout` is the next step, and it runs in Claude Code.**
`qualify` replaces it.

---

## PIPELINE B — writing and publishing a post

| Step | What happens | Output | Status |
|---|---|---|---|
| B1 | IDEA IN — six inputs | idea | 🟡 input 6 (`thought-partner`) not built |
| B2 | `topic-scout` | candidate topics | 🟡 built, never run |
| B3 | `brief-builder` — assigns RING + READER + STAGE + SLOT | `work/briefs/` | 🟡 built, never run |
| B4 | WRITE — `script-writer` / `linkedin-writer` | `work/drafts/` | 🟡 built, never run |
| B5 | `script-doctor` — THE GATE. A kill verdict is a successful run. | pass/kill | 🟡 built, never run |
| B6 | SHUBHAM REWRITES | `work/log/corrections.md` + `voice.md` OBSERVED | ⬜ never happened |
| B7 | PUBLISH | `work/log/published.md` | ⬜ **never happened — day thirteen** |
| B8 | HOOKS BANKED — 9 written, 8 kept | `work/log/hook-bank.md` | ⬜ never happened |

**Pipeline B is fully built and has never been run once.**

---

## FILE STATUS

| File | State | Fills from |
|---|---|---|
| `brain/niche.md` | ✅ edited Day 23 — PEER/BUYER by state, hook-end rule | interview |
| `brain/swipe.md` | ⛔ **EMPTY** — schema fixed Day 23 | Pipeline A |
| `brain/voice.md` | 🟡 written; OBSERVED empty | Shubham's rewrites (B6) |
| `brain/strategy.md` · `psychology.md` | ✅ written | interview |
| `brain/ledger.md` | ✅ 12 entries | interview |
| `work/log/hook-bank.md` | ⛔ EMPTY — schema ready | writing posts (B4) |
| `work/log/corrections.md` | ⛔ EMPTY — schema ready | rewrites (B6) |
| `work/log/published.md` | ⛔ EMPTY — schema ready | publishing (B7) |
| `work/creators/creator-roster.md` | ✅ 32 | the capture artifact |
| `work/creators/handles.md` | ✅ 22, derived Day 24 | done — `decisions.md` applied verbatim |
| `brain/reference/tooling.md` | ✅ **new Day 24** | the ground truth for tools |

**Five files empty. Only ONE — `swipe.md` — fills from creator research. The other four fill
from publishing.**

---

## SKILL STATUS — 8 built, 2 missing

| Skill | State | Pipeline |
|---|---|---|
| `qualify` | 🟡 **built Day 24, never run** | A — the roster cut |
| `creator-analyst` | 🟡 fixed Day 23, never run | A — the teardown |
| `topic-scout` · `brief-builder` · `script-writer` · `linkedin-writer` · `script-doctor` | 🟡 built, never run | B |
| `niche-finder` | ✅ has run | setup |
| **`scout`** | ⬜ **NOT BUILT** | A — fetch + rank |
| **`thought-partner`** | ⬜ NOT BUILT | B — idea input 6 |

---

## THE TOOLS — installed and proven, Day 23

**Full detail, exact commands and every limit: `brain/reference/tooling.md`.**

| | |
|---|---|
| Instagram | **OpenCLI + burner Chrome profile — ✅ proven live** |
| YouTube · web · RSS | ✅ yt-dlp · Jina Reader · feedparser |
| Exa search | ⚠️ configured, **never queried** |
| Whisper + ffmpeg | ✅ installed, **never run on a reel** |
| Cost | **₹0** |

**Three limits that shape Pipeline A:**

1. **No view counts.** `engagement = likes + comments` — a proxy, never described as reach.
2. **12 posts per run.** `--limit 50` returns 12. The accumulating `metrics.csv` is the fix.
3. **No post URLs.** All 23 subcommands checked. The one manual step in the system.

**Proven on live data:** `nick_saraev`, 12 posts, median engagement 6,252, two outliers at
2.60× and 2.08×.

---

## OPEN GAPS — found Day 24

| # | Gap | Cost |
|---|---|---|
| 1 | **`scout` not built** | Pipeline A cannot run at all |
| 2 | **No FORMAT field on the Brief** | Nothing decides whether a piece is an idea, advice, a story, a build or a breakage. `script-writer` is told who and what, never *what kind of thing*. |
| 3 | ~~`brain/reference/frameworks/` orphaned~~ **— RETRACTED Day 24** | **Not a gap.** Each file carries a `Feeds:` line: frameworks feed the BRAIN, skills read the brain. Verified by grep — Zeigarnik, peak-end, pratfall, hook modifiers, curse-of-knowledge and IKEA are all in `psychology.md`; TOFU/MOFU/BOFU is in `strategy.md`. The design works. **What the check DID find:** `searchable vs shareable` never crossed over. Added to `strategy.md` Day 24. `mimetic desire` also missing — left out deliberately, no current job. |
| 4 | `work/briefs/` and `work/drafts/` are empty dirs | Git does not track empty folders — they will not survive a clone. Needs `.gitkeep`. |
| 5 | `ChromeSetup.exe` (12 MB) + `debug.log` in `work/creators/` | A stray browser download from 27 Aug. **Not from any tool.** Delete before the next push; `.gitignore` has no `*.exe` or `*.log` rule. |
| 6 | Four `.bak-*` files | Manual backups from before git. Delete once pushed. |
| 7 | ~~`README.md` + `architecture.md` contradict the fixed files~~ **CLOSED Day 24** | README still defines peers by job title and still says there is no git repo. ARCHITECTURE says six running skills and never mentions the two-pipeline split. |
| 8 | ~~`brain/strategy.md` carried the old job-title PEER/BUYER definition~~ **— FIXED Day 24** | Found while adding searchable-vs-shareable. It contradicted `niche.md` directly. Now state-based and pointing at `niche.md` rather than restating it. **Brain files were not grepped in the first audit pass — only skills were. That was the miss.** |

---

## WHAT IS LEFT, IN ORDER

| # | Task | Blocked by |
|---|---|---|
| 1 | Delete the stray `.exe` and `.log`; add `*.exe` `*.log` to `.gitignore` | Shubham (deletion blocked on the mount) |
| 2 | ~~`.gitkeep` into `briefs/` and `drafts/`~~ **DONE Day 24** | — |
| 3 | ~~Point `CLAUDE.md` at `tooling.md`~~ **DONE Day 24** | — |
| 4 | **Build `scout`** | nothing — written against `tooling.md` |
| 5 | Run `qualify` on all 32 → Shubham reviews → rebuild `handles.md` | task 4 not required |
| 6 | Run `scout`, fetch winners, transcribe **one** creator | tasks 4, 5 |
| 7 | First teardown → **first entry in `swipe.md`** | task 6 |
| 8 | Fix the FORMAT gap — taxonomy + Brief field + both writers | needs a format source |
| 9 | Build `thought-partner` | nothing |
| 10 | ~~Reconcile `README.md` and `architecture.md`~~ **DONE Day 24** — architecture.md folded into blueprint.md and archived | nothing |
| 11 | Second push — everything since `5bf0c08` | Shubham |
| 12 | Replace the stale claude.ai project description | Shubham |

---

## STANDING RULES

- **Ask before running any skill, agent or scraper.** Name what it does first. Broken twice on
  Day 23.
- **Never run git from Cowork** — a git command through the mount leaves an undeletable
  `.lock`. PowerShell or Claude Code, via `daily-push`.
- **Artifacts cannot be read back from a Cowork session** — the network allowlist blocks
  `*.frame.claudeusercontent.com`. Route data out via the artifact's Export button into the
  folder, then read the file.
- **Deletion is blocked on the mount.** Move to `_to_delete/` and tell Shubham.
- **Folder grants do not persist across sessions.** Re-request each time.
- **Never the brand account, never its browser profile.** Burner in its own Chrome install.
