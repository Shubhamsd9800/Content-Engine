# handles.md — the watchlist

**Derived from:** `decisions.md`, approved by Shubham 29 Aug 2026 (Day 24)
**Chain:** `creator-roster.md` (32) → `qualify` PASS 1 → `qualified.md` → Shubham's review →
`decisions.md` → `qualify` PASS 2 → this file.
**Count:** 22.

**Read by:** `scout` (Pipeline A, step 1).

> **This file was not hand-picked.** The Day 23 version was, and it was archived rather than
> edited. Every name below survived five written gates and then Shubham's own review — eleven
> rows were overturned against the gates and those overturns are applied verbatim, not
> re-argued.

---

## TWO BUDGETS — read this before using the list

The watchlist is **22**. `swipe.md` says 10–12. **Both are correct, because they are budgets on
different things**, and the engine used to conflate them:

| | Budget | Why |
|---|---|---|
| **SCRAPE scope** | **all 22** | 22 `opencli` calls is ~2.5 minutes. Every creator added starts accumulating a median in `metrics.csv` from today. Breadth is nearly free and it compounds. |
| **TEARDOWN budget** | **one at a time, in the order below** | Ten pieces from one creator beats two from five. A teardown is hours, not minutes. |

**This list is a scope, not a queue you have to finish.** `swipe.md` fills from the *first*
teardown, not the twenty-second.

---

## BUYER-FACING — their audience can hire him

```
forseth.ai
theautomationguy.ai
jasoncooperson
aspirenest0b9
devtalksbusiness
```

## PEER-FACING — their audience builds it themselves

```
nick_saraev
techie007.dev
socialmasla
saban.talks
sanskarr.tiwari
ayushpanchmiyaai
thevibebusiness
abhishek_ux
```

## CRAFT — read for retention and story mechanics, not for subject

```
thevibefounder
_roshnichellani
```

## MIXED — accounts running both readers; useful for seeing the switch

```
shashwat___agarwal
developer_mannjadwani
roshanvadassery
projectonepercent01
tanishqharjani
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
aspirenest0b9
devtalksbusiness
nick_saraev
techie007.dev
socialmasla
saban.talks
sanskarr.tiwari
ayushpanchmiyaai
thevibebusiness
abhishek_ux
thevibefounder
_roshnichellani
shashwat___agarwal
developer_mannjadwani
roshanvadassery
projectonepercent01
tanishqharjani
vaibhavsisinty
kushal_vijay_
```

---

## SCRAPE BATCHES — how the 22 are actually run

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
| **2** | 5 | `jasoncooperson` · `saban.talks` · `sanskarr.tiwari` · `socialmasla` · `ayushpanchmiyaai` | Third buyer, then the peer bench. |
| **3** | 5 | `aspirenest0b9` · `devtalksbusiness` · `shashwat___agarwal` · `developer_mannjadwani` · `roshanvadassery` | Remaining buyer, then mixed. |
| **4** | 6 | `projectonepercent01` · `tanishqharjani` · `thevibebusiness` · `abhishek_ux` · `vaibhavsisinty` · `kushal_vijay_` | The overturned-in rows, last. Least evidence behind them, so least cost if the run has to stop. |

**Between batches: pause, and check.** ~6 seconds per creator, so a batch of five is about
half a minute of calls.

**The stop rule, and it is not optional:** if **two creators in a row return nothing**, stop
the whole run and say so. That is a tooling failure — rate limit, expired session, extension
disconnected — not a creator problem, and continuing turns one bad batch into twenty-two
`NO DATA` rows that look like findings.

**Re-running is safe.** `metrics.csv` dedupes on `creator + date + caption`, so a repeated batch
updates the numbers instead of duplicating rows.

---

## TEARDOWN ORDER — the queue `creator-analyst` works down

Ordered so that **coverage builds evenly from the first teardown**, not after the last. It
alternates reader columns rather than clearing one at a time, because a `swipe.md` holding six
peer shapes and nothing else is less useful than one holding two of each.

| # | handle | column | why here |
|---|---|---|---|
| 1 | `nick_saraev` | peer | **Start here.** The only handle already proven readable by the tooling — verified live 27 Aug. The first run tests `download` and Whisper, both UNTESTED. Test them on a known-good handle. |
| 2 | `forseth.ai` | buyer · intl | Fills the two thinnest axes at once. |
| 3 | `thevibefounder` | craft | The open loop, which Shubham named himself. Craft is 2 of 22 — the scarcest thing here. |
| 4 | `theautomationguy.ai` | buyer | Second buyer shape before a third peer. |
| 5 | `techie007.dev` | peer | Closest standing match on the list. |
| 6 | `_roshnichellani` | craft | The second craft account. |
| 7 | `jasoncooperson` | buyer · intl | Third buyer, second international. |
| 8 | `saban.talks` | peer | Series structure — a shape the others don't have. |
| 9+ | the remaining 13 | — | Order set at the time, by whichever axis is thinnest in `swipe.md` then. |

**Re-order freely.** This is a recommendation from coverage, not a gate. What is *not*
negotiable is one creator at a time.

---

## NOT ON THIS LIST — 10, cut

**Cut by gate, upheld by Shubham** (3) — hard gates; coverage cannot promote from here.
`danmartell` · `garyvee` · `imangadzhi` — GATE 1, business inspiration. The value is the person.
`arshgoyalyt` — GATE 2, careers audience.

**Cut by Shubham, against a RESERVE verdict** (6)
`adley` · `andrewcodesmith` · `creatoranuj` · `thejamiebrindle` · `kirat_ins` ·
`padho_with_pratyush`

These passed their gates and were held on the bench; Shubham cut them outright. **No reason was
recorded on any of the six** — the note field was left blank. If one of them needs to come back,
it comes back through `qualified.md`, not from memory.

---

## WHEN THIS FILE CHANGES

Only through `qualify` PASS 2, and only after a fresh `qualified.md` review. **Never by hand,
never by `scout`, never by `creator-analyst`.** A watchlist edited in passing is how the Day 23
list came to exist.
