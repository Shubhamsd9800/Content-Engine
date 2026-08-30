---
name: scout
description: RESEARCH. Fetches recent post metrics for every creator on the watchlist, appends them to a per-creator metrics.csv, computes that creator's own median engagement, and flags the outliers at 2x or better. Writes pieces.md carrying every fetched post flagged WINNER or NORMAL, with the post INDEX so the URL can be fetched by hand, then transcribes the winners once the URLs are in. Never judges content and never picks by topic. Use when the watchlist needs refreshing — about monthly, or weekly to build history faster.
---

# scout

**Type: RESEARCH.** It goes and gets. **It never has an opinion.**

> **Law one:** research never judges, analysis never fetches. When a teardown is useless there
> are exactly two causes — thin material, or a wrong reading. Split, you know which.

**Read:** `work/creators/handles.md` · `brain/reference/tooling.md`
**Write:** `work/creators/<slug>/raw/metrics.csv` · `work/creators/<slug>/raw/pieces.md` ·
`work/creators/<slug>/raw/<index>-transcript.md`

**Never writes** `handles.md`, `qualified.md`, `teardown.md` or anything in `brain/`.

**Type note:** steps 1-5 are pure RESEARCH. Step 6 (transcribe) is also research — it fetches
and converts, it forms no opinion. No step here judges.

---

## BEFORE ANYTHING — read `tooling.md`

`brain/reference/tooling.md` is the ground truth for what these commands return and what
they cannot do. **Three limits shape every line of this skill:**

1. **No view counts.** `engagement = likes + comments`. A proxy. Never call it reach.
2. **Twelve posts per run.** `--limit` does not raise it — tested.
3. **No post URLs from any read command.** All 23 checked. The URL is fetched by hand.

---

## STEP 1 · FETCH

For each handle in `handles.md`:

```
opencli instagram user <handle> -f json
```

Add `--window background` on a batch run so it does not take over the screen.

**Returns per post:** `index` · `date` · `caption` (truncated ~100 chars) · `likes` ·
`comments` · `type`

**ASK BEFORE THE BATCH.** Say how many creators and roughly how long (~6s each). **On the very
first run of this skill, run ONE creator only and show the output** — four things in the
tooling chain have never been tested end to end and a twelve-creator batch is the wrong place
to discover that.

**If a creator returns nothing** — private, renamed, deleted, or the extension is not
connected — record it in `pieces.md` as `NO DATA` with the reason and move to the next.
**Never retry in a loop.** If two creators in a row return nothing, stop the batch and say so;
that is a tooling failure, not a creator problem.

---

## STEP 2 · APPEND TO `metrics.csv`

```csv
creator,date,caption,likes,comments,engagement,first_seen,last_seen
```

**Dedupe key: `creator + date + caption`.**

- **Post already in the file** → update `likes`, `comments`, `engagement` and `last_seen`.
  **Do not add a second row.**
- **New post** → append, `first_seen` = `last_seen` = today.

**This file is the point of the whole step.** The scrape ceiling is twelve, but the CSV
accumulates: three weekly runs is roughly 36 distinct posts, two months is roughly 100. It also
**re-measures older posts as they mature**, which is what removes the age bias described below.

> **The scrape is a snapshot. The CSV is the record.** Never overwrite it, never regenerate it
> from a single run.

---

## STEP 3 · THE ARITHMETIC

Per creator, over **every row in that creator's CSV** — not just this run's twelve.

```
engagement = likes + comments
median     = middle value of that creator's engagement column
             (even count: mean of the two middle values)
outlier    = engagement ÷ median
```

**Why the creator's own median:** it cancels follower count, algorithm and topic in one move.
Comparing two creators measures audience size. Comparing a creator to themselves measures the
piece. **This is the only honest comparison available**, and it is why this step can be
arithmetic instead of taste.

### The gates

| Gate | Rule | On failure |
|---|---|---|
| **Sample floor** | fewer than **8** posts in the CSV | **Do not compute a median.** Write the rows, mark `INSUFFICIENT DATA`, say how many are needed. A median of five is noise. |
| **Outlier bar** | keep `outlier ≥ 2.0` | below it, not a winner. **1.91× is not a winner.** |
| **Per-creator cap** | at most **3** winners | if more than three clear 2.0×, take the highest three |
| **The control set** | **every fetched post is handed on**, flagged `WINNER` or `NORMAL` | never hand winners alone — see below |
| **No outliers** | nothing clears 2.0× | legitimate result. Write `NO OUTLIERS THIS RUN`. **Do not lower the bar.** |

**Never round a number up to clear a gate. Never take the "best available" when nothing
qualifies.** A run that finds nothing is a successful run.

### THE CONTROL SET — why winners alone are useless

**The cap of 3 is a cap on *transcription*, never on what gets handed downstream.**

`creator-analyst` asks two questions that only the full set can answer:

1. **"Used in n of 10"** — a shape is promoted at **5 of 10**. Three pieces cannot contain
   five instances of anything. Hand over three and promotion becomes arithmetically
   impossible.
2. **"Hits vs their own misses"** — *what do the winners have that the others don't?* With
   only winners in hand there is nothing to subtract. Every winner has a hook; that does not
   make the hook the reason it travelled.

Traceable to `blueprint.md` ROUND 3(e): *"plus two ordinary pieces as a control. Without the
control there is nothing to compare the winners against, and every finding becomes a guess."*

**So: every post fetched this run is written to `pieces.md`, flagged `WINNER` or `NORMAL`.**
Only the `WINNER` rows get a transcript. The `NORMAL` rows contribute their caption, numbers
and outlier ratio — which is all the comparison needs.

### The age bias — flag it, do not correct it

Engagement accumulates. A post from yesterday scores low because it has had one day, not
because it failed.

**Do not exclude young posts** — with a twelve-post ceiling that can leave too few for a
median. Instead:

- Mark any post **under 7 days old** as `🌱 maturing` in `pieces.md`.
- **A young post that clears 2.0× anyway is a stronger signal, not a weaker one** — it got
  there faster. Note that where it happens.
- A young post that lands between 1.5× and 2.0× goes in a **WATCH** list, not the winners. The
  next run re-measures it fairly.

---

## STEP 4 · WRITE `pieces.md`

One per creator, at `work/creators/<slug>/raw/pieces.md`. Overwrite each run — the CSV
holds the history, this file holds the current call.

**Every post fetched this run appears in it.** Winners in full, the rest as a control table.

```
# pieces — <handle>
Run: <yyyy-mm-dd>   Posts in CSV: <n>   Median engagement: <n>
Handed to creator-analyst: <n> pieces — <w> WINNER, <c> NORMAL

## WINNERS — outlier ≥ 2.0x   ← these get transcribed

### #<index>  ·  <date>  ·  <outlier>x   <🌱 maturing, if under 7 days>
likes <n>  comments <n>  engagement <n>
caption:  <the truncated caption — enough to find the post in the grid>
URL:      ____________________________________________

## NORMAL — the control set   ← captions and numbers only, no transcript
| # | date | outlier | likes | comments | caption |

## WATCH — 1.5x to 2.0x, re-measure next run
| # | date | outlier | caption |

## RUN NOTES
<NO DATA / INSUFFICIENT DATA / NO OUTLIERS THIS RUN — with the reason>
```

**The `URL:` line is deliberately blank.** OpenCLI returns no post URLs, so Shubham opens the
profile, counts to that index in the grid, and pastes the link. **The caption is printed for
exactly this reason** — it is how he confirms he is looking at the right post.

**The index is reliable.** Verified: `opencli instagram save <handle> --index 9` saved the post
whose likes matched index 9 in the listing.

---

## STEP 5 · HAND OFF

Print a single table across all creators — handle, posts in CSV, median, winners found — and
then say plainly:

> `<n>` winners across `<m>` creators. Paste the URLs into each `pieces.md`, then step 6
> can run.

---

## STEP 6 · TRANSCRIBE THE WINNERS — only after the URLs are pasted

**This step belongs to `scout` because `scout` owns the tool surface.** Nothing else in the
engine may call a downloader. Before Day 24 no skill owned it and transcripts appeared in
`raw/` by magic; that gap is closed here.

**Runs only in Claude Code on the Windows host** — see `tooling.md` → WHERE EVERY TOOL RUNS.

For each `WINNER` row that now carries a URL:

```
opencli instagram download <url>      →  the mp4      ⚠️ UNTESTED
whisper <file>                        →  the words    CPU, slow
```

Write each transcript to `work/creators/<slug>/raw/<index>-transcript.md`, headed with the
handle, index, date, likes, comments, engagement and outlier ratio — so a piece never
reaches analysis separated from its numbers.

**Both commands are marked UNTESTED in `tooling.md`. Run ONE before running twelve**, and if
the first fails, stop and say so rather than working through the list.

**NORMAL rows are never downloaded or transcribed.** Their caption and numbers are already in
`pieces.md`, and that is their whole job.

---

**Then stop.** Scout does not tear down.

---

## RULES

1. **Never judge whether content is good.** The median decides. Not Shubham, not Claude.
2. **Never select by topic.** Topic may decide which *creators* are on the watchlist — that
   happened in `qualify`. It plays no part here.
3. **Never fetch a transcript or a video.** Different step.
4. **Never call a write command.** `like`, `follow`, `comment`, `save`, `post`, `reel`, `story`
   all exist in OpenCLI. This skill uses `user` and nothing else.
5. **Never describe engagement as views, reach or impressions.** It is likes + comments and it
   is a proxy. Say so wherever the number appears.
6. **Never lower the 2.0× bar**, and never round up to reach it.
7. **Never overwrite `metrics.csv`.** Append and dedupe.
8. **Ask before a batch.** One creator first, on the first ever run.
9. **Report failures as failures.** `NO DATA` and `INSUFFICIENT DATA` are real outputs. A
   fabricated median is worse than a missing one.
10. **If `handles.md` looks provisional or stale, say so and stop.** It is written by
    `qualify`, in a second pass, **only after Shubham has approved `qualified.md`** — never by
    this skill.
11. **Hand over the control set, always.** Winners alone cannot support "5 of 10" or
    "hits vs misses". The cap of 3 caps transcription, not the handoff.
