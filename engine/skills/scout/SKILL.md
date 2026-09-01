---
name: scout
description: RESEARCH. Fetches recent post metrics for every creator on the watchlist, appends them to a per-creator metrics.csv, computes that creator's own median engagement, selects that creator's TOP 3 POSTS BY ENGAGEMENT, and records the creator's GAP (best divided by median) as a number. Writes pieces.md carrying every fetched post flagged WINNER or NORMAL, with the post INDEX so the URL can be fetched by hand, then transcribes the top 3 once the URLs are in. Never judges content and never picks by topic. Use when the watchlist needs refreshing — about monthly, or weekly to build history faster.
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
ratio      = engagement ÷ median          (per post — recorded, never a gate)
GAP        = highest engagement ÷ median  (per creator — recorded, NEVER ranked on)

  ── ADDED DAY 27 · compute BOTH, always ──────────────────────────────────
likes_median = middle value of that creator's LIKES column (unpinned only)
likes_ratio  = likes ÷ likes_median       (per post)
GAP_likes    = highest likes ÷ likes_median   (per creator)
SPLIT flag   = raise when GAP and GAP_likes disagree by more than ~2x
```

### STEP 3a · FIND THE PINNED POSTS — before any arithmetic

**Instagram lets a creator pin up to 3 posts to the top of their grid.** OpenCLI returns grid
order, so a pinned post sits at index 1, 2 or 3 **regardless of its age**. Found live on Day 25:
`techie007.dev` index 1 was **757 days old**; `theautomationguy.ai` had two pinned, at 166 and
306 days, before recency resumed at index 3.

**How to detect them — by date order, never by guessing:**

1. Read the dates in index order.
2. Find the **longest run at the end of the list whose dates never increase.** That run is the
   creator's genuine recent posts.
3. **Everything before that run is pinned.** Mark each `📌 PINNED`.
4. **Never mark more than 3.** Instagram allows no more. If the rule produces four or more,
   something else is wrong — write `UNEXPECTED ORDER` in RUN NOTES and mark none.

*Worked example, `theautomationguy.ai`:* dates run `3/17/26 · 10/28/25 · 8/28/26 · 8/28/26 ·
8/24/26 · …`. The never-increasing run starts at index 3, so indexes **1 and 2 are pinned**.

**What pinning does to the numbers, and why both effects must be removed:**

1. **A pinned post is one the creator already chose as their best.** Selecting it as a top-3
   discovers nothing — it hands back the creator's own answer. `theautomationguy.ai`'s two
   pinned posts sat at 17.61× and 11.00×; they would have taken two of three teardown slots.
2. **A pinned post is usually old, from a smaller account.** Letting it into the median stops
   the comparison being creator-to-themselves and makes it creator-to-a-past-version-of-themselves.
   `techie007.dev`'s baseline was mixing a 2024 post with this week's.

**So pinned posts are excluded from the median and excluded from the top 3 — and still handed
over**, listed in their own section, flagged `NORMAL` for the control set. **What a creator
chooses to pin is itself a signal**; it is read in the teardown, it just never sets the baseline.

---

**Selection is by RANK, not by threshold. Take the top 3 by engagement.** The three highest
posts in that creator's CSV are the ones tearing down. That is the whole rule.

**Revised Day 25 — why the 2.0× bar was removed from selection.** The bar was doing two jobs
at once: choosing which posts to study, and judging whether a creator was worth studying. As a
selection rule it fails in both directions — nick_saraev's first live run produced exactly one
post over 2.0×, and moving the median by 8% would have produced zero, from the same twelve
posts and the same numbers. "Three posts to tear down" is what the teardown needs; a threshold
cannot promise three. The ratio is still computed and still written down. **It is a recorded
number, not a gate.**

**GAP is the creator-level question**, asked once per creator, not per post: *is there any
distance between this creator's best post and their typical post?* If there is not, the
teardown's core question — *why did this one work when the others didn't?* — has no "didn't"
to point at, and the hours spent will find nothing.

> **⚠️ REVISED DAY 27 — GAP IS NO LONGER A RANKING NUMBER.** It used to be recorded *"for Phase 2
> to rank on"*. It is now recorded for **comprehension only**. `handles.md`'s TEARDOWN ORDER —
> its single consumer — is retired; the queue is complete. **Nothing ranks on GAP. `scout`
> never acted on it and still does not.**
>
> **AND IT IS NOT COMPARABLE BETWEEN CREATORS.** `engagement = likes + comments`, so a creator
> who gates only their winners has a GAP inflated far above one who gates their whole feed.
> Measured Day 27: `shashwat___agarwal` **11.86x → 3.48x** on likes alone, while
> `kushal_vijay_` **13.02x → 14.12x** — the correction moves accounts in **opposite
> directions**. A single GAP figure cannot be read across two accounts and never could.
>
> **THEREFORE: compute and record BOTH.** `GAP` and `GAP_likes`, side by side, every run.
> Where they disagree by more than ~2x, write **`SPLIT — engagement <a>x vs likes <b>x`** in
> RUN NOTES. **That is a fact about the creator's comment behaviour, not about any one post.**

**Why the creator's own median:** it cancels follower count, algorithm and topic in one move.
Comparing two creators measures audience size. Comparing a creator to themselves measures the
piece. **This is the only honest comparison available**, and it is why this step can be
arithmetic instead of taste.

### The gates

| Gate | Rule | On failure |
|---|---|---|
| **Pinned** | detected per STEP 3a, **max 3** | excluded from the median **and** from the top 3. Still handed over, flagged `NORMAL`, listed under `📌 PINNED`. |
| **Sample floor** | fewer than **8** **unpinned** posts in the CSV | **Do not compute a median.** Write the rows, mark `INSUFFICIENT DATA`, say how many are needed. A median of five is noise. |
| **Date span** | unpinned posts span more than **90 days** | still compute, but write `WIDE SPAN — <n> days` in RUN NOTES. The account may have grown across the window, so the median crosses eras and **GAP is soft**. Say so; never silently present it as firm. |
| **Selection** | the **top 3 by engagement** in that creator's CSV | fewer than 3 posts total → take what exists and say so |
| **Ties** | equal engagement at the boundary | take the **older** post — it has had longer to settle |
| **The control set** | **every fetched post is handed on**, flagged `WINNER` or `NORMAL` | never hand winners alone — see below |
| **GAP** | record `highest ÷ median` per creator, to 2 decimals | never a gate. **Recorded for comprehension — nothing ranks on it.** |
| **GAP_likes** | record `highest likes ÷ likes median` per creator, to 2 decimals | **ADDED DAY 27.** Always computed alongside GAP. |
| **SPLIT flag** | GAP and GAP_likes disagree by more than ~2x | write `SPLIT — engagement <a>x vs likes <b>x` in RUN NOTES. A creator-level fact, never a post-level one. |
| **FLAT flag** | `GAP < 1.5` | still hand over the top 3, but write **`FLAT — low variance`** in RUN NOTES. Phase 2 decides whether to skip. `scout` does not skip. |

**Never reorder the top 3 by taste, topic, or how good a caption looks.** Rank by engagement
and stop. The numbers choose; nobody else does.

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

**Do not exclude young posts, and do not correct for age.** Two reasons, and the second is the
one that settles it:

1. A twelve-post ceiling means excluding them can leave too few for a median.
2. **There is no "finished" post.** New audience arrives daily and old posts keep collecting.
   A post is only finished from the creator's side; the platform never closes it. So there is
   no honest line to draw, and top-3-by-engagement does not need one — young posts sit low and
   simply do not reach the top 3.

- Mark any post **under 7 days old** as `🌱 maturing` in `pieces.md`.
- **A young post that reaches the top 3 anyway is a stronger signal, not a weaker one** — it
  got there faster. Note that where it happens.
- Ranks **4 and 5** go to **WATCH** — the next in line if a top-3 post cannot be transcribed,
  and re-measured next run.

**The accumulating CSV is what makes this safe.** A young post that would eventually rank top 3
is picked up on a later run. Nothing is lost, it is only late.

---

## STEP 4 · WRITE `pieces.md`

One per creator, at `work/creators/<slug>/raw/pieces.md`. Overwrite each run — the CSV
holds the history, this file holds the current call.

**Every post fetched this run appears in it.** Winners in full, the rest as a control table.

```
# pieces — <handle>
Run: <yyyy-mm-dd>   Posts in CSV: <n>   Pinned: <n>   Scored: <n unpinned>
Median engagement: <n over unpinned only>   Date span: <n> days
GAP: <best unpinned ÷ median, 2dp>   <FLAT — low variance, if GAP < 1.5>
GAP (likes only): <best likes ÷ likes median, 2dp>   <SPLIT — …, if they differ by >2x>
Handed to creator-analyst: <n> pieces — <w> WINNER, <c> NORMAL

## WINNERS — top 3 by engagement   ← these get transcribed

### #<index>  ·  <date>  ·  <engagement>  ·  <ratio>x   <🌱 maturing, if under 7 days>
likes <n>  comments <n>  engagement <n>
caption (truncated at 100 chars by OpenCLI — for FINDING the post, never for analysis):
          <the truncated caption>
URL:      ____________________________________________
FULL CAPTION:
          ____________________________________________

## NORMAL — the control set   ← captions and numbers only, no transcript
| # | date | ratio | likes | comments | caption |

## 📌 PINNED — the creator's own picks, excluded from median and top 3
| # | date | age | engagement | caption |
|---|---|---|---|---|

> Not scored. Pinned posts are pre-selected by the creator and usually predate the account's
> current size. Read them in the teardown for **what he chose to pin**; never as a discovery.

## WATCH — ranks 4 and 5, next in line
| # | date | engagement | ratio | caption |

## RUN NOTES
<NO DATA / INSUFFICIENT DATA / FLAT / WIDE SPAN / UNEXPECTED ORDER — with the reason>
```

**The `URL:` and `FULL CAPTION:` lines are deliberately blank.** OpenCLI returns no post URLs
and truncates every caption at exactly 100 characters — **no flag raises either.** So Shubham
opens the profile, counts to that index in the grid, and pastes both from the same screen. The
truncated caption is printed for exactly this reason: it is how he confirms he is on the right
post.

**Why the full caption is worth the extra paste.** On Instagram the caption carries the CTA and
the offer — `Comment "DESIGN" to get…` is a mechanic, not a label. A caption cut off mid-word
cannot be analysed, and `creator-analyst` must never treat the truncated line as the real one.
It is collected only for the winners of creators actually being torn down — never for all 22.

**The index is reliable.** Verified: `opencli instagram save <handle> --index 9` saved the post
whose likes matched index 9 in the listing.

---

## STEP 5 · HAND OFF

Print a single table across all creators — **handle · posts · pinned · scored · median · span ·
GAP · top-3 engagements · flags** — sorted by GAP, highest first. GAP is what Phase 2 ranks the teardown
queue on, so it is the column that has to be readable at a glance.

Then say plainly:

> Top 3 selected for `<m>` creators. `<f>` flagged FLAT. Paste the URLs into each
> `pieces.md`, then step 6 can run.

---

## STEP 6 · TRANSCRIBE THE WINNERS — only after the URLs are pasted

**This step belongs to `scout` because `scout` owns the tool surface.** Nothing else in the
engine may call a downloader. Before Day 24 no skill owned it and transcripts appeared in
`raw/` by magic; that gap is closed here.

### TWO ROUTES. BOTH COMPLETE THIS STEP.

**The output of STEP 6 is a FILE, not a tool run.** What has to exist when this step is done is
`work/creators/<slug>/raw/<index>-transcript.md`, headed with its numbers. How the words got
into it is not this step's business.

| Route | Surface | State |
|---|---|---|
| **A · By hand** — Shubham watches the reel and pastes the words | **anywhere, Cowork included** | ✅ **the default route.** Needs no tool, no bridge, no Windows host. |
| **B · By tool** — `opencli instagram download` then `whisper` | Claude Code on the Windows host only | ⚠️ **both commands still UNTESTED.** A convenience, never a prerequisite. |

**Route A is not a fallback and is not lesser.** Decided Day 25, session 2: the two commands in
route B had been sitting on the critical path since Day 23 purely because nobody had noticed
that `creator-analyst` reads a file and cannot tell who wrote it. **Never block a teardown
waiting on route B, never ask which route produced a transcript, and never mark a
hand-supplied transcript as provisional.**

**Route B runs only in Claude Code on the Windows host** — see `tooling.md` → WHERE EVERY TOOL
RUNS. Route A runs anywhere.

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

1. **Never judge whether content is good.** Engagement rank decides which posts. Not Shubham,
   not Claude. Craft is `creator-analyst`'s question, on transcripts, in a later step.
2. **Never select by topic.** Topic may decide which *creators* are on the watchlist — that
   happened in `qualify`. It plays no part here.
3. **Never fetch a transcript or a video.** Different step.
4. **Never call a write command.** `like`, `follow`, `comment`, `save`, `post`, `reel`, `story`
   all exist in OpenCLI. This skill uses `user` and nothing else.
5. **Never describe engagement as views, reach or impressions.** It is likes + comments and it
   is a proxy. Say so wherever the number appears.
6. **Never take more or fewer than the top 3**, and never reorder them by taste or topic.
   Rank by engagement, break ties toward the older post, stop.
7. **Never overwrite `metrics.csv`.** Append and dedupe.
8. **Ask before a batch.** One creator first, on the first ever run.
9. **Report failures as failures.** `NO DATA` and `INSUFFICIENT DATA` are real outputs. A
   fabricated median is worse than a missing one.
10. **If `handles.md` looks provisional or stale, say so and stop.** It is written by
    `qualify`, in a second pass, **only after Shubham has approved `qualified.md`** — never by
    this skill.
11. **Hand over the control set, always.** Winners alone cannot support "5 of 10" or
    "hits vs misses". Selecting 3 caps transcription, not the handoff.
12. **Never let a pinned post into the median or the top 3**, and never mark more than three.
    A pinned post is the creator's own answer; selecting it discovers nothing.
13. **Never act on GAP, and never rank on it.** Record **both** figures — `GAP` and
    `GAP_likes` — and move on. **Revised Day 27:** GAP's only consumer was `handles.md`'s
    TEARDOWN ORDER, which is now retired. It is a number for reading a creator, not for
    ordering them, and it is **not comparable between accounts.**
