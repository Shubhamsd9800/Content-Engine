# teardown — devtalksbusiness

**Run:** Day 27, 1 Sep 2026 · Batch 2, creator 10 of 15
**Skill:** `creator-analyst` · **Input:** `raw/` only, per the input contract
**Frames reviewed:** post-8, post-2

```
CREATOR      devtalksbusiness
SERVES       peer — despite the "business" handle. See COVERAGE NOTE.
AUDIENCE     Indian, Hindi-first: video editors, freelancers and creators. NOT business owners.
SELLS        unclear on-platform. Runs paid creator meetups (#3, #10) and hires editors (#12).
ANALYSED     12 pieces — 3 WINNER, 9 NORMAL. Zero pinned (UNEXPECTED ORDER).
             ⚠️ EFFECTIVELY **ONE USABLE WINNER**. See the DATA ERROR below.
             engagement = likes + comments. A proxy. Never reach, never views.
             median 2,112 · GAP 312.60x (scout flags it soft) · span 177 days
```

---

## ── 🔴 DATA ERROR FOUND — #12's TRANSCRIPT IS FROM THE WRONG POST ──

**`raw/12-transcript.md` carries post #12's numbers attached to a different reel's content.**

| source | 8/7/2026 · 11,706 likes · 25,965 comments · 37,671 |
|---|---|
| **`metrics.csv`** *(ground truth from `scout`)* | *"**This might be my biggest hiring till now!!!** looking for a lot of them for freelance full-time and in…"* |
| **`pieces.md`** | *"This might be my biggest hiring till now!!!…"* — **agrees** |
| **`raw/12-transcript.md`** | *"**Five free website, so she will make you smartest person in the room**"* — **and a full transcript about Z-Library, Our World in Data, Google Scholar, TED-Ed and Aeon** |

**`metrics.csv` and `pieces.md` agree with each other. The transcript disagrees with both.**
The transcript was collected from a different post and given #12's numbers.

**This also resolves an anomaly that would otherwise have become a finding.** #12 shows **25,965
comments against 11,706 likes** with **no gate anywhere in the transcript** — which looked like a
new mechanic worth naming. It is not a mechanic. **It is a hiring post.** *"Looking for a lot of
them for freelance, full-time and interns"* generates tens of thousands of applications in the
comments, and that is the whole explanation.

> **Had the transcript been trusted, this teardown would have promoted a phantom structure —
> "a resource list that generates comments without asking for them" — built on a caption that
> belongs to a job advert.**

**#2 and #8 were both re-verified against `metrics.csv` line by line and both MATCH.** Only #12
is corrupt.

> ### THIS IS THE FOURTH INSTANCE OF THE SAME LESSON, AND THE FIRST FOUND IN THE DATA ITSELF.
>
> Day 24: audit the contracts before believing a blocker. Day 25: the blocker did not exist.
> Day 26: `thevibefounder` — numbers attached to the wrong reels, caught by checking `pieces.md`.
> **Day 27: `devtalksbusiness` #12 — caught by checking `metrics.csv`.**
>
> The first three were errors in *reasoning about* the files. **This one is an error IN the
> files**, and it survived collection, `pieces.md` and a teardown queue placement. The only thing
> that caught it was reading `metrics.csv` because a comment ratio looked wrong.
>
> **`creator-analyst` should verify every winner's caption against `metrics.csv` before
> analysing it.** It costs one grep. It is not in the skill today.

**#12 IS EXCLUDED FROM THIS TEARDOWN.** Nothing below rests on it.

**What that leaves:** #2 — which `scout` itself flags as *"almost certainly a pinned/legacy viral
post… treat GAP and the median as unreliable"* at **312.60×**, an 18× gap to the next post — and
**#8**. **One clean winner, on a 12-post control set.** The skill's own rule applies: *you can
describe; you cannot find a pattern, and the pattern is the whole output.*

---

## ── THE NUMBERS, RECOMPUTED ──

```
likes, 12 scored:  209 · 414 · 527 · 884 · 1,109 · 1,335 · 1,431 · 3,642 · 3,753 · 4,122 · 11,706 · 549,048
likes median = 1,383      engagement median = 2,112
```

| # | what it is | likes | comments | engagement ratio | **likes ratio** |
|---|---|---|---|---|---|
| #2 | Google-beats-Canva **(lottery)** | 549,048 | 111,165 | 312.60x | **396.9x** |
| #12 | **hiring post — EXCLUDED** | 11,706 | 25,965 | 17.83x | 8.46x |
| #8 | **Ep 16, gated** | 4,122 | 3,005 | 3.37x | **2.98x** |
| #6 | **founder profile — Dev Taneja, Unjob.ai** | **3,753** | **79** | 1.81x | **2.71x** |
| #1 | *"revealing what I've been building for a year"* | 3,642 | 395 | 1.91x | **2.63x** |
| #11 | free prompt website | 1,431 | 612 | 0.97x | 1.03x |
| #4 | founder profile — *"this bro"*, jewellery | 209 | 8 | 0.10x | **0.15x** |

**#2 confirms the conversion/distribution split found on `projectonepercent01`.** It carries an
explicit gate — *"comment link"* — and its comment ratio is **0.20 : 1**, the LOWEST gated ratio
anywhere in this batch. At 549k likes the reach massively outruns the gate.

> **The gate's yield falls as reach rises.** It converts a fixed fraction of a small, engaged
> audience. It does not scale with a viral hit. **Third piece of evidence that the gate is a
> conversion mechanic**, and the strongest, because it comes from the largest post in the project.

---

## ── STRUCTURES ──

### D1 · THE SERIES-INDEX CAPTION  ·  #8, frame-confirmed

```
SHAPE       the CAPTION does not describe the piece. It states the piece's POSITION IN A SERIES.
              caption, in full:   "Ep 16: Building your freelance business"  + 5 hashtags
              title card, in full: "Trending music that make your content viral! 🙈🔥"
            The card carries the content. The caption carries the shelf it sits on.
RETENTION   n/a — this is a packaging device, not a retention device
REWARD      a named list the viewer can act on immediately (the gate adds links, see below)
MECHANIC    open loop at the SERIES level, not the piece level — "Ep 16" implies 15 behind it
            and an Ep 17 coming. The loop never closes, by design.
AWARENESS   n/a
READER      both
DOWNGRADE   SURVIVES COMPLETELY. "Ep 1" is available to anyone on day one. It requires no
            authority — only the willingness to still be posting at Ep 16.
TRANSFERS   YES.
USED IN     #8 (Ep 16), frame-confirmed. Series count implies 15 prior instalments not in the fetch.
```

> ### THIS SETTLES THE RECORDED CAPTION-LENGTH CONFLICT — WITHOUT AVERAGING IT.
>
> `_BATCH-1-AUDIT.md` records an unresolved conflict, deliberately not averaged:
> `developer_mannjadwani` runs **3–8 word captions, no hashtags** → 17.19×.
> `_roshnichellani` runs **100–150 word arguments** → 4.69×.
>
> **`devtalksbusiness` #8 is a third option neither of them shows: a SHORT caption that is not
> empty.** Six words — and those six words do a job the long caption cannot. They index the piece.
>
> **The conflict was never about length. It is about what the caption is FOR.**
> `_roshnichellani`'s long caption carries **the argument**. `developer_mannjadwani`'s short one
> carries **nothing, and the title card carries everything**. #8's short one carries **the shelf**.
> **Three jobs, three lengths. Still a test to run — but it is now a test with three arms, not
> two, and the third one is the cheapest.**

### ⚠️ AND IT CORRECTS THE `shashwat___agarwal` READ FROM EARLIER TODAY

`shashwat___agarwal`'s pinned **Ep1 / Ep2** family-business series ran at **0.17×** and 2,306,
and that teardown concluded journey content is profile content, not feed content.

**`devtalksbusiness` is at Ep 16 and it is a WINNER at 3.37× — his best non-lottery post.**

> **A numbered series is not judged by its first episodes. It compounds, and the early ones are
> supposed to underperform.** Ep1 at 0.17× is not evidence the series fails; it is what Ep1 looks
> like. Ep16 is what the same shape looks like after fifteen.
>
> **This materially changes the advice.** The earlier read — *don't judge journey posts by reach*
> — stands. But *"they never travel"* is wrong. **They travel later.** The thing that kills a
> series is stopping at Ep 3 because Ep 1 did 0.17×.
>
> **⚠️ CAVEAT, and it is not small:** Ep 16 is one post, on an account whose median is
> contaminated by a 312× lottery, with **no other episode in the fetch to compare against.** This
> is a two-account observation, not a finding. **It should not be promoted until a third series
> appears, or until `devtalksbusiness` is re-scraped for more episodes.**

---

### D2 · THE NAMED FOUNDER PROFILE  ·  2 of 12 — one hit, one failure

**This is the only content on the entire watchlist that tells a story about a real business owner,
and both instances are in this account's control set — captions only, no transcript.**

| # | the opening | likes | comments | likes ratio |
|---|---|---|---|---|
| #6 | *"**Dev Taneja is the founder and CEO of Unjob.ai.** Alongside building the company, he's a business cont[ent creator]"* | **3,753** | **79** | **2.71x** |
| #4 | *"**This bro** is running a startup beating many jewellery brands. Highly customising proposal rings for…"* | **209** | 8 | **0.15x** |

**An 18× spread between two posts of the same format, three weeks apart, same account.**

**Two differences, and both are visible in the first eight words:**

1. **#6 NAMES THE PERSON AND THE COMPANY.** *"Dev Taneja, founder and CEO of Unjob.ai."*
   #4 says *"this bro."* An unnamed subject cannot be verified, cannot be looked up, and reads
   as an anecdote rather than a report.
2. **#6's subject is in the audience's world** (an AI/tech founder who is also a content creator).
   #4's is a consumer jewellery brand — a real business, and irrelevant to video editors.

> **#6 is also the cleanest ORGANIC signal in this entire batch: 3,753 likes against 79 comments,
> no gate, no resource, no DM.** A ratio of **0.02 : 1** — the inverse of every gated post read
> today. **Nobody was farming it, and it still landed at 2.71× on likes.**

**⚠️ NOT PROMOTED. 2 of 12, captions only, no transcript, and one of the two failed.** It is
recorded because it is the **only measured evidence in nine teardowns about telling a business
owner's story**, and because it produces a testable rule rather than a shape:

> **If the story names a real person and a real company the reader can look up, it works.
> If the subject is anonymous, it does not.** Two data points. **A hypothesis, not a rule.**

---

## ── HOOK PATTERNS ──

**D-H1 · THE INCUMBENT KILLED, PHYSICALLY** — #2 opens *"Google ne Canva ko kya maara hai bhai!"*
— *"Google has absolutely killed Canva."* This is `H12 · THE PRICE-TAG KILL` and
`shashwat___agarwal`'s W-H1, in a **third** account. Third confirmation, and the most violent
register of the three.

**⚠️ And its 312× is a lottery, not a shape.** `scout` says so; `handles.md` says so. **The hook
is confirmed by three accounts. This account's NUMBER confirms nothing.**

**D-H2 · "बात सुनो" / "भाई"** — a direct-address particle before the first content word. #8 opens
*"बात सुनो।"* — *"listen."* Not a greeting: a **command that costs one word**. Compatible with
`S04 · NO INTRO, NO CONTEXT` rather than a violation of it — S04 forbids throat-clearing, and
*"listen"* is an attention grab, not a setup. **Worth testing in Hinglish; it has no clean English
equivalent that does not sound aggressive.**

## ── PACING ──

**#8 is timestamped in the transcript and it is the tightest structure in the batch:**

```
00:00   the claim + the instruction        ("videos don't go viral without trending music")
00:09   THE LIST — 3 categories, 3-4 items each, no transitions between them
00:23   a personal pick ("my favourite is Beanie") → the gate → follow
```

**23 seconds to the close.** Three categories delivered in fourteen seconds. And note the
**personal pick immediately before the gate** — after a neutral list, one line of actual opinion,
then the ask. That is a small, reusable move: **the opinion is what makes the list his.**

**#2 is 24 seconds, three beats, phone-at-laptop throughout.** W1 again — **fourth account.**

## ── LANGUAGE ──

**Hinglish, `तुम` register, and the on-screen text is ENGLISH.** #8's card: *"Trending music that
make your content viral!"* — English, and ungrammatical, and it did not matter.

**Second independent confirmation of the Day 26 language lock today**, after
`shashwat___agarwal`. **Two accounts, neither consulted when the lock was made.**

**⚠️ AND THE TITLE CARD IS NEARLY IDENTICAL TO `shashwat___agarwal`'s.** Black rounded box, white
**serif**, two lines, top third. Two unconnected accounts, same treatment.

> **That downgrades W2 from "a distinctive choice" to "a regional convention."** This morning it
> looked like the serif card was what made `shashwat___agarwal` stand out. It is what this
> cohort does. **`shubhh.forge`'s job is therefore harder and more valuable than it looked:
> the differentiation has to come from the brand system, because the FORM is already standard.**

## ── HITS vs MISSES ──

With one clean winner, this is stated as observation, not as a pattern.

**What travels here:** a killed incumbent (#2) · a named list with a personal pick (#8) ·
a named founder (#6) · *"revealing what I've been building for a year"* (#1, 2.63× on likes).

**What does not:** *"Just sharing things I wish I knew six years back"* (#5, **0.30×**) —
a promise of wisdom with no named subject and nothing to take. **R-A, fifth confirmation.**
*"This bro is running a startup"* (#4, **0.15×**) — anonymous subject.
Event promotion (#3 0.38×, #10 0.64×) — asks the viewer to travel to Delhi.

## ── DOES NOT TRANSFER ──

| | why |
|---|---|
| **The comment gate** | **10th account.** #2 and #8 both run it. Same rejection, corrected reasoning (see `projectonepercent01`). |
| **The 312× number** | `scout` flags it soft; it is a legacy/pinned viral hit on a news announcement. **`handles.md` already calls this creator a news lottery and it is right.** Read #2 for its hook. Never for its scale. |
| **Physical creator meetups** | #3, #10. A distribution channel requiring an existing local audience. |
| **Hiring posts as content** | #12. 25,965 comments from applicants. Not a shape — a job advert with an audience attached. **And the source of today's data error.** |
| **"Ep N" without the intent to reach Ep 16** | The whole mechanic is the count. A series abandoned at Ep 3 is worse than no series — it advertises that he stopped. |

## ── COVERAGE NOTE ──

**Adds:** the series-index caption (D1) and the third arm of the caption-length conflict; the
named-founder hypothesis (D2) — the only buyer-story evidence in the project; the fourth W1
confirmation; the second language-lock confirmation; the correction to today's `shashwat___agarwal`
journey-content read; and the strongest evidence yet that the gate is a conversion mechanic.

**⚠️ DOES NOT CLOSE THE BUYER GAP — AND MAKES THE WATCHLIST'S PROBLEM WORSE.**

This was the last buyer-column creator in Batch 2 and the one carried specifically to close the
gap. **His audience is video editors, freelancers and creators.** Ep 16 of *"Building your
freelance business"* is a reel telling **editors** which music to put on **their clients'** videos.
The word *business* in the handle refers to **the viewer's** freelance business.

> **FOURTH CONSECUTIVE SUPPLY-SIDE ACCOUNT.** `kushal_vijay_` → job-seekers.
> `shashwat___agarwal` → would-be agency owners. `projectonepercent01` → would-be creators.
> `devtalksbusiness` → freelance editors.
>
> **Batch 2 did not move the buyer gap. It made the pattern impossible to ignore:** ten teardowns
> in, the watchlist teaches **supply-side shapes almost exclusively.** The project's standing
> constraint — *"peers are the supply side; they do not buy web development"* — is not a risk to
> watch any more. **It is a property of the watchlist**, and `handles.md`'s membership was set
> before anyone had read a reel.
>
> **The one exception found today is #6, and it is a control-set caption on a failed pair.**

## ── PROMOTE TO SWIPE ──

**ZERO NEW STRUCTURES PROMOTED. Fourth in a row. Batch 2 promoted nothing.**

| target | change | needs a call? |
|---|---|---|
| `H12 · PRICE-TAG KILL` | **third account.** Strongest cross-account hook in the file after S04. | no |
| `S04 · NO INTRO, NO CONTEXT` | third account. `"बात सुनो"` noted as compatible, not a breach. | no |
| `S01` / W1 | **fourth account.** Phone-at-laptop is settled beyond argument. | no |
| `R-A` | fifth confirmation — #5, 0.30x | no |
| gate rejection | **10th account** + #2 proves yield **falls** as reach rises | no |
| **D1 · series-index caption** | **⚠️ PROPOSE AS A NEW ENTRY** — survives the downgrade fully, resolves the caption conflict into three arms | **YES — Shubham** |
| caption-length CONFLICT | **third arm found.** Do not average. Now a 3-way test. | **YES — Shubham** |
| `shashwat___agarwal` journey read | **CORRECTED — series compound; Ep1 is supposed to lose** | **YES — Shubham** |
| W2 serif card | **downgraded** — a regional convention, not a differentiator | no |
| `creator-analyst` SKILL | **⚠️ add a step: verify every winner's caption against `metrics.csv` before analysis** | **YES — Shubham** |
| `raw/12-transcript.md` | **⚠️ carries the wrong content. Needs a red warning block — NOT WRITTEN, awaiting your yes** | **YES — Shubham** |

## ── LIMITS OF THIS TEARDOWN ──

- **⚠️ ONE CLEAN WINNER.** #12 excluded as corrupt; #2 is a `scout`-flagged lottery on a 177-day
  span. The skill's own floor — *"fewer than 8 pieces: you can describe, you cannot find a
  pattern"* — applies in spirit even though 12 pieces were fetched.
- **GAP 312.60× is not a real number** and neither is the median it rests on. `scout` says so.
- `pieces.md` shows **blank URL and blank FULL CAPTION for all three winners.** The transcripts
  carry them. **`pieces.md` was never backfilled from the A5 intake for this creator** — a data
  hygiene gap, unrelated to the #12 error, and worth checking on the other 14.
- Control captions truncated at 100 chars — control-set counts are **opening-line only**.
- **D2 rests entirely on two truncated control captions.** No transcript, no frames.
- **Nothing here has been tested against Shubham's audience, because there isn't one.**
  Zero posts published, day twenty-seven.
