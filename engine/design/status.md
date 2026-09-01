# workflow-status.md — the engine, step by step, with live status

**Last revised:** Day 26, 31 Aug 2026 — **end of day.** Pipeline A ran end to end for the first time.
**What this file is:** the running map of the engine and where every step actually stands.
Companion to `engine/design/blueprint.md` — the single design document. This file holds the live task list; the blueprint holds the design.
**This file carries STATE, not design.** When they disagree: they win on design, this wins on
what is true today. For anything tools-related, `brain/reference/tooling.md` wins over all
three.

Legend: ✅ done · 🟡 built, never run · ⚠️ works but untested end to end · ⛔ blocked · ⬜ not started

---

## THE SHAPE OF IT

Two pipelines. They share exactly ONE file — **`brain/playbook.md`**. No shared skill, no
shared trigger. Do not re-merge them.

> **DAY 27:** `brain/swipe.md` was **absorbed into `playbook.md` and archived**. One writing
> file, not two. Archive copy: `archive/superseded/swipe.md.day26-absorbed-into-playbook`.

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
| A2 | **QUALIFY** — five written gates cut the roster to a watchlist | `work/creators/qualified.md` | ✅ **ran twice, Day 24** — PASS 1 + PASS 2 → `handles.md` |
| A3 | FETCH — recent posts + engagement per creator | `<slug>/raw/metrics.csv` | ✅ **RAN Day 25 — all 22 creators.** 12 posts each except `forseth.ai` (10). No rate limiting, no `NO DATA` rows, stop rule never triggered. |
| A4 | RANK — median, then outlier = engagement ÷ median; **top 3 by rank**, plus GAP per creator | `<slug>/raw/pieces.md` | ✅ **Day 25 — 66 winners across 22 creators.** The 2× bar was removed from selection this day; it is recorded, not a gate. |
| A5 | LINKS — Shubham copies the post URL **and the full caption** per winner | `pieces.md` slots ← the **Reel Intake** artifact | ✅ **CLOSED Day 26 — 15 creators / 44 of 45 reels.** `saban.talks` runs with 2 winners. Manual by design: OpenCLI returns no URLs (LIMIT 3) and cuts captions at 100 chars (LIMIT 4). |
| A6 | TRANSCRIBE — the winners' spoken words reach `raw/` **by any route** | `<slug>/raw/<index>-transcript.md` | ✅ **COMPLETE — 44 reels transcribed**, all typed by hand, plus 85 frames. `download` + Whisper never used and never needed. See the A6 note below. |
| A7 | TEARDOWN — `creator-analyst` | `<slug>/teardown.md` **+ `<slug>/script.md`** | ✅ **COMPLETE Day 27 — ALL 15 CREATORS, TWICE.** Day 26: 6 accounts. Day 27: the skill was rebuilt around the Kallaway grid and **re-run over all 15** — every creator now has an account teardown **and** a line-by-line script analysis. **30 files, 7,840 lines.** |
| A8 | PROMOTE — **two bars now:** caption patterns at 5 of 10 · **script/production patterns at 3 of 3 in one account AND a second account** | **`brain/playbook.md`** | ✅ **BUILT Day 27 — 1,141 lines.** 10 structures (S01–S10), 22 hooks, 7 rules, 15 rejections, the **SCRIPT GRID**, a **LINKEDIN** section and a **PRODUCTION** section. Every entry tiered **[C] / [S] / [X]** and cited. **Absorbs and replaces `swipe.md`.** |

**A2 note.** A shortlist was produced on Day 23 from capture notes alone, with zero reel data,
and presented as analysis. It was discarded. `qualify` exists so that cut is a repeatable step
with checkable criteria rather than a judgement made in conversation.

**`handles.md` exists again — 22 handles, derived, Day 24.** The Day 23 file was 12 names
hand-cut without criteria; it was archived rather than edited, because editing a list that was
never derived would have carried the bias forward under a cleaner label. The new file came
through the full chain: `creator-roster.md` (32) → `qualify` PASS 1 → `qualified.md` →
Shubham's review in the verdict board → `decisions.md` (11 overturns) → `qualify` PASS 2.
**Pipeline A is unblocked.**

**A6 NOTE — decided Day 25, session 2. The blocker was dissolved, not solved.**
`opencli instagram download` + Whisper were only ever a *convenience* — a way to produce
`raw/<index>-transcript.md` without typing. `creator-analyst`'s input contract names the file,
never the tool that wrote it. **A transcript Shubham pastes in is the same input.** Both commands
stay UNTESTED in `tooling.md` and are now optional, not gating. This removes A6 from the critical
path, where it had sat since Day 23.

---

## THE DAY 25 PLAN — agreed, in order

**Scrape wide, rank on evidence, tear down few.** Scouting is cheap; teardown is not. That is
the whole logic of the ordering, and it is the Day 24 split (**scrape scope** vs **teardown
budget**) applied to a working day.

| Phase | What | Surface | Output | Status |
|---|---|---|---|---|
| **1** | `scout` all 22 — batch 0 alone first, then batches 1–4 | Claude Code | 22 × `raw/metrics.csv` + 22 × `raw/pieces.md` | ✅ **DONE Day 25.** 66 winners. |
| **2** | **THE CUT** — rank all 22 on the numbers, no tools | Cowork | rewritten `TEARDOWN ORDER` in `handles.md` | ✅ **DONE Day 25 s2.** |
| **3** | Depth, one creator at a time | Cowork — A6 is manual paste | `teardown.md` + `script.md` → `brain/playbook.md` | ✅ **COMPLETE Day 27 — 15 of 15** |

**Phase 2 ranks on, and only on:**
- **outlier ratio** — max engagement ÷ that creator's own median. The one that matters: a
  creator sitting inside 1.2× of their median across 12 posts has **no gap between hit and miss**
  for a teardown to explain, and is unlearnable however good the content feels.
- how many posts clear **2×** — zero outliers means the same thing
- **volume** — under 8 posts is skipped, not scored
- whether hits **cluster or scatter** — clustered suggests a repeatable shape
- **column coverage** — the queue keeps buyer, peer and craft represented. Craft is the scarcest
  column; a purely numeric ranking that wipes it out is a bad ranking.

**Nothing is deleted by the cut.** All 22 stay scraped — `metrics.csv` accumulates and costs
nothing to keep. The cut produces an **order**, not a shorter watchlist. A creator can be pulled
forward later without re-running anything.

**THE TEARDOWN COUNT — settled Day 25, session 2, against the numbers.** Shubham's position
going in was 10–15, Claude's was 3–5, recorded as a disagreement to be settled by data. The data
settled it: **start with 3, reassess at 3.** Six of the 22 came back with a GAP under 2.6× —
`nick_saraev` 2.5×, `techie007.dev` 2.2×, `saban.talks` 2.5×, `sanskarr.tiwari` 2.4× on 32 total
engagements — and a creator with no distance between their best and typical piece has no
*"and this one didn't"* for a teardown to point at. Transcribing them discovers nothing. The
remaining spread is wide enough that three well-chosen creators cover buyer, peer and craft.
**Nothing is cut.** All 22 stay scraped; the queue is an order, not a list to finish.

**THE RISK THAT WAS CARRIED — now closed.** This plan knowingly deferred the untested
`download` + Whisper step to the end of Phase 1, accepting that 22 scrapes could turn out to be
inert data. That risk is gone, and not because the commands were tested: **A6 accepts a
hand-pasted transcript, so it never needed them.** See the A6 note under Pipeline A.

---

## PIPELINE B — writing and publishing a post

| Step | What happens | Output | Status |
|---|---|---|---|
| B1 | IDEA IN — six inputs | idea | 🟡 all six available; `thought-partner` IS built (corrected day 27) |
| B2 | `topic-scout` | candidate topics | 🟡 built, never run |
| B3 | `brief-builder` — assigns RING + READER + STAGE + SLOT | `work/briefs/` | 🟡 built, never run |
| B4 | WRITE — `script-writer` / `linkedin-writer` | `work/drafts/` | 🟡 built, never run |
| B5 | `script-doctor` — THE GATE. A kill verdict is a successful run. | pass/kill | 🟡 built, never run |
| B6 | SHUBHAM REWRITES | `work/log/corrections.md` + `voice.md` OBSERVED | ⬜ never happened |
| B7 | PUBLISH | `work/log/published.md` | ⬜ **never happened — day fifteen** |
| B8 | HOOKS BANKED — 9 written, 8 kept | `work/log/hook-bank.md` | ⬜ never happened |

**Pipeline B is fully built and has never been run once.**

---

## FILE STATUS

| File | State | Fills from |
|---|---|---|
| `brain/niche.md` | ✅ edited Day 23 — PEER/BUYER by state, hook-end rule | interview |
| **`brain/playbook.md`** | ✅ **BUILT Day 27 — 1,141 lines.** The only writing file. | Pipeline A |
| ~~`brain/swipe.md`~~ | 📦 **ARCHIVED Day 27** — absorbed into `playbook.md` | — |
| `brain/voice.md` | 🟡 written; OBSERVED empty | Shubham's rewrites (B6) |
| `brain/strategy.md` · `psychology.md` | ✅ written | interview |
| `brain/ledger.md` | ✅ 12 entries | interview |
| `work/log/hook-bank.md` | ⛔ EMPTY — schema ready | writing posts (B4) |
| `work/log/corrections.md` | ⛔ EMPTY — schema ready | rewrites (B6) |
| `work/log/published.md` | ⛔ EMPTY — schema ready | publishing (B7) |
| `work/creators/creator-roster.md` | ✅ 32 | the capture artifact |
| `work/creators/handles.md` | ✅ **15** (22 cut to 15 on Day 26, reasons recorded). **TEARDOWN ORDER retired Day 27 — queue complete.** | done |
| `work/creators/<slug>/script.md` | ✅ **15 of 15, new Day 27** | `creator-analyst` PASS 1 |
| `brain/reference/tooling.md` | ✅ **new Day 24** | the ground truth for tools |

**⚠️ DAY 27: FOUR files empty, and EVERY ONE fills from publishing.** `queue.md` ·
`hook-bank.md` · `corrections.md` · `published.md`, plus `work/briefs/` and `work/drafts/`.
**Not one of them fills from a teardown. Pipeline A can no longer move them.**

*(historical, Day 26:)* **Five files empty. Only ONE — `swipe.md` — fills from creator research. The other four fill
from publishing.**

---

## SKILL STATUS — ✅ **ALL 10 BUILT** *(corrected Day 27)*

| Skill | State | Pipeline |
|---|---|---|
| `qualify` | ✅ **ran twice, Day 24** | A — the roster cut |
| `creator-analyst` | ✅ **REBUILT Day 27 around the Kallaway grid · ran over all 15 creators** | A — the teardown |
| `topic-scout` · `brief-builder` · `script-writer` · `linkedin-writer` · `script-doctor` · `thought-partner` | 🟡 **built, never run — all six** | B |
| `niche-finder` | ✅ has run | setup |
| **`scout`** | ✅ **built Day 24**, first live run Day 25 | A — fetch + rank |
| **`thought-partner`** | ✅ **BUILT — 184 lines.** 🔴 This row said `NOT BUILT` from Day 26 to Day 27 and it was wrong. The file has existed since 29 Aug: four drivers, an output contract, a reader-trap check. **Nothing in Pipeline B is missing a skill.** | B — idea input 6 |

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
| 1 | ~~**`scout` not built**~~ **CLOSED Day 24** — built, and skills junctioned into `%USERPROFILE%\.claude\skills` Day 25 | — |
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
| 4 | ~~**Build `scout`**~~ **DONE Day 24** | — |
| 5 | ~~Run `qualify` → review → rebuild `handles.md`~~ **DONE Day 24** — 22 handles | — |
| 6 | Run `scout`, fetch winners, transcribe **one** creator | tasks 4, 5 |
| 7 | First teardown → **first entry in `swipe.md`** | task 6 |
| 8 | Fix the FORMAT gap — taxonomy + Brief field + both writers | needs a format source |
| 9 | Build `thought-partner` | nothing |
| 10 | ~~Reconcile `README.md` and `architecture.md`~~ **DONE Day 24** — architecture.md folded into blueprint.md and archived | nothing |
| 11 | ~~Second push~~ **DONE Day 25** — `06c8eb5` on `origin/pipeline-v3` | — |
| 12 | Replace the stale claude.ai project description | Shubham |

---

## DAY 26 — the priorities, set at the close of Day 25

**Day 25 ended with A6 open for eleven years' worth of excuses and closed in one evening.**
31 transcripts exist. `swipe.md` is still empty. That gap is the whole of Day 26.

> ## ⚠️ THE TABLE BELOW IS THE DAY 26 PLAN. IT IS COMPLETE. SUPERSEDED DAY 27.
> Tasks 2, 3 and 4 all ran. **Pipeline A is finished: 15 of 15 creators, `playbook.md` built.**
> **Task 5 — PIPELINE B, first run, end to end — is the ONLY item still open, and it is now
> the only thing left in the engine that has never executed.** Day twenty-seven of zero.
> **Nothing in Pipeline A blocks it. Every skill it reads is current.**
> **It needs exactly one input: an idea.**

| # | Task | Surface | Why it is in this order |
|---|---|---|---|
| **1** | **PUSH.** 31 transcripts + 8 corrected docs, none of it backed up. | Claude Code / PowerShell — `daily-push` | Same shape of risk as Day 24's two unbacked days. Do it before anything else. |
| **2** | **First teardown — `forseth.ai`.** `creator-analyst`, one creator, 3 winners against 7 normals. | Cowork | The first time this project turns material into a finding. Everything else waits behind it. |
| **3** | **First entries in `brain/swipe.md`.** | Cowork | Five Pipeline B skills read it and it has never had a line. This is the moment Pipeline A justifies its existence. |
| **4** | Teardowns 2 and 3 — `jasoncooperson`, then `developer_mannjadwani`. | Cowork | Buyer, buyer, then the tightest cluster. Three is the settled count. |
| **5** | **PIPELINE B, first run, end to end** → a published post. | Cowork | Day sixteen of zero. |

**Collecting the remaining 11 creators is NOT on this list.** It is Shubham's own time and can
happen in parallel — but it must not displace the teardown again. **Eleven creators is already
more material than three teardowns need.**

### DECISIONS NEEDED FROM SHUBHAM ON DAY 26

1. **Three creators were removed from the watchlist and NOT named.** Said in conversation at the
   close of Day 25, never written down. **`handles.md` still lists 22.** Name them, or the
   removal does not exist. *(Do not guess. Day 23's list was destroyed by exactly this.)*
2. **The Reels-tab problem.** Several creators keep their strongest work in the Reels tab, which
   `scout` cannot see — the profile grid is all OpenCLI returns. Options: accept grid-only and
   live with it; add a documented "Shubham's pick" class that carries no numbers (this is what
   `thevibefounder` currently uses); or find a Reels-tab read. **Until decided, hand-picked
   reels never receive a multiplier.**
3. **`aspirenest0b9` has one reel of three**, and it is a carousel. Collect the other two or drop
   it to Tier 3.

---

---

## DAY 27 — the priorities, set at the close of Day 26

**Day 26 was the day Pipeline A finished.** `swipe.md` has 8 shapes in it. **Pipeline B has
still never run and `published.md` is still empty — day seventeen.**

| # | Task | Surface | Why |
|---|---|---|---|
| **1** | **PUSH.** Nothing since `38e9b5c`. 44 transcripts, 6 teardowns, `swipe.md`, `voice.md`, `niche.md`, `handles.md`, the audit file. | Claude Code / PowerShell — `daily-push` | Two full days of irreplaceable work unbacked. **Never git from Cowork.** |
| **2** | **PIPELINE B, END TO END. One Brief → one draft → one published piece.** | Cowork | Ten skills, zero runs, seventeen days. **Nothing else on this list matters more.** |
| **3** | The `linkedin-writer` adaptation framework — see below. | Cowork | New, raised by Shubham on Day 26. |
| **4** | Teardowns 7+ — only if 2 and 3 are done. | Cowork | 9 creators remain collected and untouched. **They are an asset, not a to-do list.** |

### DECIDED ON DAY 26 — do not relitigate

- **Watchlist cut 22 → 15.** Seven removed **with written reasons** (`handles.md` → CUT ON DAY 26).
  Folders in `_to_delete/day26-cut-creators/`. This broke the file's own membership rule
  knowingly; the reasons are the reason it is acceptable.
- **A5 closed at 44 of 45 reels.** `saban.talks` runs with **2 winners, not 3.**
- **LANGUAGE LOCKED — Hinglish spoken, English on-screen text.** `voice.md` v0.1.
- **PLATFORM DECIDED — Instagram AND LinkedIn, both live, routed per Brief.**
  `brief-builder` now carries a `PLATFORM` field. `niche.md` OPEN list updated.
- **The teardown count is no longer 3.** Shubham's call: all 15 eventually, in batches, with a
  look at `swipe.md` after each batch. Six are done.

### NEW WORK RAISED ON DAY 26 — the LinkedIn adaptation gap

> **All 8 structures in `swipe.md` were torn down from Instagram REELS.** Every one assumes
> three channels — spoken, on-screen text, visual. **A LinkedIn post has one.**
>
> | shape | survives on LinkedIn |
> |---|---|
> | S02 corrected assumption · S07 person explainer · S08 stated position | ✅ arguments and stories |
> | S01 · S03 · S05 · S06 | ❌ all four depend on something being VISIBLE |
>
> **What is needed:** a written conversion framework in `linkedin-writer` — given a reel script
> or a Brief, what becomes the fold, what carries the visual's job in text, what gets cut.
> **Not a paste. A rebuild.** `swipe.md` needs its own LinkedIn section eventually, from
> teardowns of LinkedIn material, which do not exist.

### STILL OPEN AFTER DAY 26

- **Cadence.** The only remaining decision in `niche.md`. Not a blocker — a scheduling question.
- **The FORMAT gap.** No field decides idea vs advice vs story vs build vs breakage. Open since Day 24.
- **Caption length — a recorded CONFLICT, not averaged.** `developer_mannjadwani` 5-word titles
  at 17.2x vs `_roshnichellani` 150-word arguments at 4.7x. **A test to run, not a rule to derive.**
- **`thevibefounder`** — 3 reels held as UNRANKED reference (no numbers). Collect his 3 measured
  posts, or leave them unranked permanently. Not torn down.
- **`_roshnichellani` #4** — post identity uncertain. Flagged in the teardown, no promotion rests on it.
- **A buyer-facing account with STORY or CRAFT.** The clearest gap in the watchlist after six
  teardowns — all three buyer accounts are proof, authority or spectacle.

## STANDING RULES

- **Ask before running any skill, agent or scraper.** Name what it does first. Broken twice on
  Day 23.
- **Never run git from Cowork** — a git command through the mount leaves an undeletable
  `.lock`. PowerShell or Claude Code, via `daily-push`.
- ~~**Artifacts cannot be read back from a Cowork session.**~~ **FALSE AS OF DAY 26.** The
  allowlist entry added on Day 24 has taken effect — `Artifact action:"read"` works from Cowork
  and was used this day. **But read the caveat:** the artifact only returns what was PUBLISHED.
  The Reel Intake artifact's Save was failing silently, so a read returned 21 of 44 reels. **The
  page's own "Copy everything" button reads the browser's local draft and returned all 44.**
  When an artifact's save is broken, the Copy button is the truth and the read is not.
- **Deletion is blocked on the mount.** Move to `_to_delete/` and tell Shubham.
- **Folder grants do not persist across sessions.** Re-request each time.
- **Never the brand account, never its browser profile.** Burner in its own Chrome install.
