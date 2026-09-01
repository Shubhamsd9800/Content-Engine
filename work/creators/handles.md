# handles.md — the watchlist

**Derived from:** `decisions.md`, approved by Shubham 29 Aug 2026 (Day 24)
**Chain:** `creator-roster.md` (32) → `qualify` PASS 1 → `qualified.md` → Shubham's review →
`decisions.md` → `qualify` PASS 2 → this file.
**Count:** 15.  *(was 22 — seven cut on Day 26, 31 Aug 2026. See CUT ON DAY 26 below.)*

**Read by:** `scout` (Pipeline A, step 1).

> **This file was not hand-picked.** The Day 23 version was, and it was archived rather than
> edited. Every name below survived five written gates and then Shubham's own review — eleven
> rows were overturned against the gates and those overturns are applied verbatim, not
> re-argued.

---

## CUT ON DAY 26 — seven handles, with reasons

**31 Aug 2026.** Shubham read every collected creator's actual reels — captions, transcripts,
frames — and cut seven. **This is a membership change made by hand, which this file's own rule
at the bottom forbids.** It is recorded as a deliberate, reasoned override rather than hidden,
because the Day 23 failure was a list cut *without written reasons*, not a list cut by hand.

**Every cut below carries Shubham's stated reason, in his words. That is the difference.**

| handle | Shubham's reason |
|---|---|

Their folders were moved to `_to_delete/day26-cut-creators/` — **not deleted.** `metrics.csv`
and any frames travel with them. To bring one back: move the folder home and re-add the handle
here with a reason.

**Count is now 15.** Collection closed at **44 of 45 reels** — `saban.talks` post 9 was never
collected and Shubham decided on Day 26 to run that creator with **2 winners, not 3.**

---

## TWO BUDGETS — read this before using the list

The watchlist is **15** (was 22). `swipe.md` says 10–12. **Both are correct, because they are budgets on
different things**, and the engine used to conflate them:

| | Budget | Why |
|---|---|---|
| **SCRAPE scope** | **all 15** | 15 `opencli` calls is under 2 minutes. Every creator added starts accumulating a median in `metrics.csv` from today. Breadth is nearly free and it compounds. |
| **TEARDOWN budget** | **one at a time, in the order below** | Ten pieces from one creator beats two from five. A teardown is hours, not minutes. |

**This list is a scope, not a queue you have to finish.** `swipe.md` fills from the *first*
teardown, not the fifteenth.

---

## BUYER-FACING — their audience can hire him   *(4 after the Day 26 cut)*

```
forseth.ai
theautomationguy.ai
jasoncooperson
devtalksbusiness
```

## PEER-FACING — their audience builds it themselves   *(4 after the Day 26 cut)*

```
nick_saraev
techie007.dev
socialmasla
saban.talks
```

## CRAFT — read for retention and story mechanics, not for subject

```
thevibefounder
_roshnichellani
```

## MIXED — accounts running both readers; useful for seeing the switch   *(4 after the Day 26 cut)*

```
shashwat___agarwal
developer_mannjadwani
projectonepercent01
vaibhavsisinty
```

## CRAFT-ONLY — a deliberate exception, with a fence around it

```
kushal_vijay_
```

**`kushal_vijay_` fails GATE 2.** His audience is students and working professionals looking
for jobs — the supply side. Shubham overturned the cut knowingly, for the shapes: Indian, at
a comparable standing, doing news-with-an-opinion, which is ring 4 and thin in this set.

> **The fence:** his **structures** may be torn down. His **subject choices, audience framing
> and CTAs** may not, and nothing from him may be tagged `buyer`. If a teardown of him starts
> producing careers-shaped topics, that is the gate reasserting itself — drop him.

---

## MACHINE-READABLE — one handle per line, nothing else

```
forseth.ai
theautomationguy.ai
jasoncooperson
devtalksbusiness
nick_saraev
techie007.dev
socialmasla
saban.talks
thevibefounder
_roshnichellani
shashwat___agarwal
developer_mannjadwani
projectonepercent01
vaibhavsisinty
kushal_vijay_
```

---

## SCRAPE BATCHES — SUPERSEDED

> **This whole section is history as of Day 26.** All 22 were scraped on Day 25 with no rate
> limiting and the stop rule never fired. The batches below are kept as the record of how that
> run was structured; they are **not a plan to execute.** Seven of the handles named in them are
> now cut. If a fresh scrape is ever needed, rebuild the batches from the current 15.

### The Day 25 run, as it was executed (22 handles)

**Never all 22 in one call.** `tooling.md` records *rate limiting at 12+ sequential reads is
unknown* — untested. 22 is nearly double that, on a burner account. Batches keep the blast
radius small and make a failure legible.

**Batches follow the teardown order**, so if you stop after any batch the creators you have are
the ones you'd tear down first — and coverage is already spread across buyer, peer and craft
rather than sitting in one column.

| Batch | n | Handles | Why grouped this way |
|---|---|---|---|
| **0** | 1 | `nick_saraev` | **The test.** The only handle proven readable by the tooling. Stop and read the output before batch 1. |
| **1** | 5 | `forseth.ai` · `thevibefounder` · `theautomationguy.ai` · `techie007.dev` · `_roshnichellani` | Teardown order 2–6. Both craft accounts land here — craft is the scarcest column. |

**Between batches: pause, and check.** ~6 seconds per creator, so a batch of five is about
half a minute of calls.

**The stop rule, and it is not optional:** if **two creators in a row return nothing**, stop
the whole run and say so. That is a tooling failure — rate limit, expired session, extension
disconnected — not a creator problem, and continuing turns one bad batch into twenty-two
`NO DATA` rows that look like findings.

**Re-running is safe.** `metrics.csv` dedupes on `creator + date + caption`, so a repeated batch
updates the numbers instead of duplicating rows.

---

## TEARDOWN ORDER — ⛔ RETIRED DAY 27 · QUEUE COMPLETE

> **ALL FIFTEEN CREATORS ARE TORN DOWN.** This section ordered a queue that no longer exists.
> **Kept as the record of how the order was set — not as a live instruction.**
>
> **AND THE RANKING BASIS DID NOT HOLD.** `GAP` is `engagement ÷ median` where
> `engagement = likes + comments`, so it is inflated by comment-gating **by a different amount
> per creator** — `shashwat___agarwal` falls **11.86x → 3.48x** on likes alone while
> `kushal_vijay_` **rises** 13.02x → 14.12x. **A GAP figure cannot be compared between two
> accounts**, and this section compared fifteen.
>
> **What actually selected the reels was Shubham watching them.** He overrode this ranking every
> time it mattered, and was right each time: `nick_saraev` kept against a 2.50x ("must keep") is
> the best LinkedIn model on the list; `devtalksbusiness` kept against a lottery number gave the
> consequence chain; `kushal_vijay_` kept produced zero, exactly as its fence predicted.
>
> **`scout` now records GAP and GAP_likes for comprehension. Nothing ranks on either.**
> **Membership is unchanged and still moves only through `qualify` PASS 2.**

---

### The order as it was set (historical)

**REWRITTEN Day 25, session 2, from the scout numbers.** The previous order was written on
Day 24 with **zero reel data** — it could only rank on coverage and on which handle the tooling
had been proven against. Both of those reasons expired on Day 25: all 22 read cleanly, so
"the one we know works" stopped being a distinction, and every creator now has a measured GAP.
The file's own standing note permits this — *"re-order freely, this is a recommendation from
coverage, not a gate."*

**What the ranking uses**, in this order of weight:

1. **GAP** — biggest post ÷ that creator's own median. No distance between best and typical
   means the teardown's core question has no *"and this one didn't"* to point at.
2. **Cluster, not lottery** — do the top 3 decay smoothly, or does one post run away from a flat
   account? A single news hit is unrepeatable and teaches nothing.
3. **Scale match** — `swipe.md`'s confidence-downgrade rule. A shape from a 566-median account
   transfers to a standing start. A 660k-engagement news post does not.
4. **Column coverage** — buyer / peer / craft kept represented.

Engagement = likes + comments. A **proxy**, never reach.

---

### TIER 1 — collect and tear down · 5 creators, 15 reels

| # | handle | column | median | GAP | top 3 | why here |
|---|---|---|---|---|---|---|
| 1 | `forseth.ai` | buyer · intl | 566 | **34.7×** | 34.7 / 13.8 / 7.6 | **Start here.** Best on every axis at once. Smoothly decaying cluster, not one hit. Smallest scale on the shortlist, so the downgrade barely applies. All three winners are the **same repeating build-in-public series** — "Day N of letting Claude Code edit my videos" — which is structurally the closest thing on the watchlist to what this account is trying to be. |
| 2 | `jasoncooperson` | buyer · intl | 1,774 | **31.2×** | 31.2 / 8.4 / 5.7 | Same clustered shape, and the subject is the exact stack — Claude systems, skills, agent workflows, shipped and shown. Second buyer before any third peer. |
| 3 | `developer_mannjadwani` | mixed → peer | 610 | **17.2×** | 17.2 / 13.6 / 6.8 | **Tightest cluster on the entire list** — three consecutive August days all 7–17× over typical. Three back-to-back is structural, not lucky. Small account, Indian audience, and strikingly short captions — worth learning whether the hook is the caption or the first frame. |
| 4 | `theautomationguy.ai` | buyer | 2,202 | **13.8×** | 13.8 / 13.2 / 3.6 | Two near-identical hits, the signature of a repeatable format. Both open on a **pop-culture cold open** before any product appears — a hook family nothing else here uses. Caveat: two of the three are `🌱 maturing`, under 7 days at fetch. |
| 5 | `kushal_vijay_` | **craft — FENCED** | 965 | **13.0×** | 13.0 / 7.3 / 6.7 | Five posts over 2×. **The fence in this file is not optional:** structures may be torn down; his subject choices, audience framing and CTAs may not, and nothing from him is ever tagged `buyer`. |

**Tear down 3 first, then reassess** — that is the Day 25 settlement of the 10–15 vs 3–5
disagreement, and it is written up in `engine/design/status.md`. Collecting 5 gives a spare if
one comes back thin.

**Coverage note, stated rather than hidden:** Tier 1 is buyer-heavy and its only craft entry is
the fenced one. If the first three teardowns come back without a usable retention or story
mechanic, **pull `_roshnichellani` forward** — it is the strongest unfenced craft account here.

---

### TIER 2 — later, if a shape needs confirming · 5 creators

| handle | column | median | GAP | note |
|---|---|---|---|---|
| `_roshnichellani` | craft | 1,112 | 4.7× | **First pull-forward.** The strongest unfenced craft account. |
| `shashwat___agarwal` | mixed | 1,340 | 11.9× | One strong hit (11.9×) then a drop to 2.3× — closer to lottery than cluster, but on-subject. |
| `projectonepercent01` | mixed | 3,399 | 4.9× | ~~**7 posts over 2× — the most consistent account on the list.**~~ 🔴 **CORRECTED DAY 27: it is 5 on engagement and 4 on likes, not 7.** Check `raw/pieces.md`. This claim was the sole basis for the TIER 2 placement above. **The teardown ran anyway and produced zero structures** — 11 of 12 posts carry a comment-and-follow gate, and one post records **3 likes against 597 comments**. |
| `socialmasla` | peer | 2,879 | 4.2× | Two near-identical winners built on the same template (`Stop Wasting ₹X on Y Courses`). A visible repeatable formula. |
| `thevibefounder` | craft | 329 | 3.1× | Second craft account. Very recent posts, 4-day span — numbers not settled. |

---

### TIER 3 — KEPT AFTER THE DAY 26 CUT · 5 creators

**Four Tier 3 handles were cut on Day 26** (`tanishqharjani`, `abhishek_ux`, `ayushpanchmiyaai`,
`sanskarr.tiwari`). The five below were kept — three of them on Shubham's explicit call against
their numbers. **All five are fully collected: 3 reels each, except `saban.talks` at 2.**
Parked still means *the numbers say a teardown would discover little* — it is a queue position,
not a verdict.

| handle | GAP | why parked |
|---|---|---|
| `devtalksbusiness` | 312.6× | **KEPT — Shubham's call, Day 26:** good volume, and he works an Indian audience in raw *bhai*-register talk, plus runs numbered 30/100-day challenge series. Still a **news lottery** on the numbers: 660,213 on a Google-AI-tool announcement against a 2,112 median. Nothing about it repeats. |
| `vaibhavsisinty` | 25.8× | ~~News lottery on a large account — 7,098 median. Scale and mechanism both wrong.~~ 🔴 **HALF CORRECTED, DAY 27. SCALE: right** — 180,288 likes is not transferable. **MECHANISM: wrong.** The 25.8x post is a **profile of a named friend who built something**, with a mechanism, a hidden legal fact and a returned number — and his second winner is the identical shape about a different named person. **2 of 2. A repeatable format, not a lottery**, and he was parked on the half that was wrong. See `vaibhavsisinty/script.md`. |
| `nick_saraev` | 2.5× | **KEPT — Shubham's explicit call, Day 26:** *"must keep"*. Studied for **edit craft and visual style**, not for outlier shape. Demoted from #1 originally: Held that slot only because he was the one handle proven readable on 27 Aug; all 22 read cleanly on Day 25, so that reason expired. 2.5 / 2.0 / 1.8 is one of the flattest spreads here. |
| `techie007.dev` | 2.2× | Flat. 2.2 / 2.1 / 1.8. |
| `saban.talks` | 2.5× | Flat. |

---

**Re-order freely.** This is a recommendation from evidence, not a gate. What is *not*
negotiable is **one creator at a time.**

---

## NOT ON THIS LIST — 17, cut

**Cut by gate, upheld by Shubham** (3) — hard gates; coverage cannot promote from here.
`danmartell` · `garyvee` · `imangadzhi` — GATE 1, business inspiration. The value is the person.
`arshgoyalyt` — GATE 2, careers audience.

**Cut by Shubham, against a RESERVE verdict** (6)
`adley` · `andrewcodesmith` · `creatoranuj` · `thejamiebrindle` · `kirat_ins` ·
`padho_with_pratyush`

These passed their gates and were held on the bench; Shubham cut them outright. **No reason was
recorded on any of the six** — the note field was left blank. If one of them needs to come back,
it comes back through `qualified.md`, not from memory.

**Cut by Shubham on Day 26, after reading their actual reels** (7)
`roshanvadassery` · `aspirenest0b9` · `thevibebusiness` · `tanishqharjani` · `abhishek_ux` ·
`ayushpanchmiyaai` · `sanskarr.tiwari`

**Reasons ARE recorded** for all seven — see *CUT ON DAY 26* at the top of this file. Folders in
`_to_delete/day26-cut-creators/`.

---

## WHEN THIS FILE CHANGES

**MEMBERSHIP — who is on the list.** Normally only through `qualify` PASS 2, after a fresh
`qualified.md` review. **Never by `scout`, never by `creator-analyst`.** A watchlist edited in
passing is how the Day 23 list came to exist.

> **BROKEN ONCE, ON PURPOSE — Day 26.** Shubham cut seven by hand after reading every collected
> reel. The gates ran on capture notes and scout numbers; he was judging the actual content,
> which is strictly better evidence. **The rule's real purpose is served: every cut has a written
> reason and the folders are recoverable.** A hand-cut with reasons is not the Day 23 failure.
> If a future cut has no reason attached, it must go back through `qualified.md`.

**ORDER — which creator is torn down first.** Free to change, and changed by hand on Day 25
session 2 against the scout numbers. The `TEARDOWN ORDER` section has always carried its own
permission to be re-ordered; ranking is not membership. **No handle was added or removed** —
that was true through Day 25; on Day 26 seven were cut with reasons. If a re-ordering ever wants to *drop* a handle, that goes
back through `qualified.md`, not through an edit here.
