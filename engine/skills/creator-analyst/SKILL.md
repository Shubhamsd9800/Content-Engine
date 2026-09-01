---
name: creator-analyst
description: ANALYZE. Tears down one creator at a time — reel transcripts, captions, frames and engagement numbers — into TWO files: script.md (the writing, line by line, on the Kallaway grid) and teardown.md (the account — shape, ratios, what transfers). Compares hits against their own misses and records which reader each shape serves. Feeds the playbook. Use when Shubham names a creator he admires or drops material from one account.
---

# creator-analyst

**One creator at a time.** Ten pieces from one beats two from five — the finding is the
*repeated* pattern, and repetition is invisible in two.

**Read:** `work/creators/<slug>/raw/` · `brain/niche.md` · `brain/psychology.md` ·
`brain/reference/transcripts/kallaway--script-framework.md` · **`brain/playbook.md`**
**Write:** `work/creators/<slug>/script.md` **and** `work/creators/<slug>/teardown.md`

> ## THE ORDER MATTERS. SCRIPT FIRST.
>
> **Revised Day 27.** This skill used to produce shape and ratios and never open the script.
> It ran over four creators in Batch 2 and promoted **zero** structures — not because the
> creators were thin, but because the writing was never examined.
>
> **`script.md` is written FIRST and it is the primary output.** `teardown.md` is the account
> record that sits under it. A run that produces a teardown and no script has not run.

---

**INPUT CONTRACT.** `raw/` is populated by **`scout`**. This skill never fetches anything and
never chooses which pieces to analyse — **it analyses what is in `raw/` and nothing else.**
If `raw/` is empty, say so and stop.

> **The transcript's origin is not part of this contract.** `raw/<index>-transcript.md` may have
> come from `opencli download` + Whisper, or been typed in by Shubham. **Both are valid and this
> skill must not distinguish between them, ask which was used, or refuse a transcript for
> lacking tool provenance.** Judge the words, never the route.

---

## STEP 0 — VERIFY BEFORE ANALYSING. Not optional.

**Added Day 27 after a real failure.** `devtalksbusiness` #12 carried the right numbers attached
to a completely different reel's transcript. It was caught only because a comment ratio looked
odd. Had it been trusted, a phantom structure would have been promoted from a job advert.

**For every winner, before reading a word of it:**

```
grep '<date>' raw/metrics.csv     →  does the caption match <n>-transcript.md ?
```

| Result | Do this |
|---|---|
| **match** | proceed |
| **mismatch** | 🔴 **The creator becomes a CRAFT REFERENCE for that piece — permanently, not pending.** Analyse the script; exclude every number; quote no ratio; attempt no hits-vs-misses. Say so in both output files. **A craft reference is never a sole source:** its devices reach the playbook only where a second, numerically-clean account confirms them, and devices unique to it are recorded **CRAFT-ONLY, UNTESTED**. **Do not stop the run and do not open a blocker.** |

`metrics.csv` is ground truth. `pieces.md` is derived. **A transcript is neither.**

## STEP 0b — RECORD BOTH RATIOS

`engagement = likes + comments`. Instagram exposes no view counts on any free route
(`tooling.md` LIMIT 1). **It is a proxy and must be named as one — never reach, never views.**

**Compute and record TWO figures per creator:**

```
engagement ratio  =  (likes + comments) ÷ median(likes + comments)
likes-only ratio  =  likes ÷ median(likes)
```

**Why both.** Comment volume is real engagement — a creator who gets people commenting is
genuinely engaging an audience, and that is not to be dismissed. **But it is a different
signal from likes, and the two diverge unpredictably per account.** Measured Day 27:

| creator | GAP on engagement | GAP on likes | direction |
|---|---|---|---|
| `shashwat___agarwal` | 11.86x | **3.48x** | collapses 70% |
| `kushal_vijay_` | 13.02x | **14.12x** | rises 8% |

**Record both. Never average them. Where they disagree by more than ~2x, say so in one line** —
that is a fact about the creator's comment behaviour, not about any single post.

---

## WHAT IS IN `raw/`

```
pieces.md                  every post scout fetched — WINNER and NORMAL, with numbers
<index>-transcript.md      one per WINNER only
metrics.csv                that creator's full history, all runs — GROUND TRUTH
frames/post-<n>/           screenshots, where collected
```

| | | |
|---|---|---|
| **WINNER** | that creator's **top 3 by engagement** — selected by rank in `scout`, never re-judged here | full transcript |
| **NORMAL** | everything else scout fetched | caption + numbers only |

**Captions: read `FULL CAPTION`, never the truncated line.** OpenCLI cuts every caption at 100
chars mid-word; the CTA and the offer sit past the cut. **If `FULL CAPTION` is blank in
`pieces.md`, check the transcript file — it often carries it.** If neither has it, say the
caption was not collected and analyse the transcript alone. **Never infer a CTA from a cut-off
sentence.**

**The NORMAL rows are not filler.** *"Used in n of 10"* needs ten to count across, and
*"hits vs their own misses"* needs the misses.

**Fewer than 8 pieces total: say what that costs.** You can describe; you cannot find a pattern.

**Claude cannot watch video.** A reel with no transcript and no frames is invisible.

---

# ═══ PASS 1 · SCRIPT ═══  →  `script.md`

**The backbone is `brain/reference/transcripts/kallaway--script-framework.md`.** Read it before
running this pass. Its master principle governs everything below:

> **EXPECTATIONS vs REALITY.** Expectations are what the viewer thinks will happen. Reality is
> what happens. **When reality beats expectations they stay. When expectations beat reality they
> leave.** Every check below is a way of asking where that gap opened or closed.

**Run every winner separately. Never summarise across scripts inside this pass** — that is
PASS 4's job.

### The nine checks, in this order

**1 · PACKAGING** — what expectation is set *before a word is spoken*?
Record all three channels separately: **title card** (verbatim) · **caption** (verbatim) ·
**cover frame**. Then state the expectation in one sentence.

**2 · CLICK CONFIRMATION** — quote the **first line verbatim**. Then two verdicts:
- Does it **confirm** the packaging? (the viewer knows they are in the right place)
- Does it **beat** it? (something arrives that the packaging did not promise)

**Confirming is the floor. Beating is the finding.** Most pieces only confirm. Say which.

**3 · THE INTRO, five parts** — mark each ✅ present / ✗ skipped, and quote it if present:

| | |
|---|---|
| **context** | states bluntly what this is about, so the viewer can opt in |
| **common belief** | restates what the viewer already thinks — builds the ground to push off |
| **contrarian take** | contradicts that belief. **This is where reality beats expectation.** |
| **proof** | why this person should be trusted on it |
| **the plan** | the ordered list of what is coming |

*(proof and plan may run in either order)*

**A skipped part is a finding, not a gap to excuse.** Short-form frequently drops three of five.
**Record WHICH three** — the pattern across 45 scripts is the whole point of this pass.

**4 · BODY ORDER** — how many points, and in what order of strength?

> **Kallaway's rule: the SECOND-BEST point goes FIRST, the best goes second.** Two things
> escalating trains the viewer that value is climbing, so they stay for the third. Best-first
> trains the opposite.

Verdict: **escalating · flat · decaying**. Say which point was strongest and where it sat.

**5 · THE VALUE LOOP** — for each body point, mark three things:

```
what   context — what it is, stated as simply as possible
how    application — how to do it, with an example
why    framing — why it matters, how it fits the whole
```

**A point with `what` only is a list item, not a body point.** Count how many of the points
carry all three. That count is one of the most transferable numbers this pass produces.

**6 · REHOOKS** — **quote the seam lines verbatim.** The sentence at the end of one point that
makes the next one unskippable. *"That one matters, but without this next one the magic is
lost."*

**"No rehooks" is a real and common finding.** Write it plainly. Then say what holds the viewer
across the seam instead — a visual change, a count, a number — or whether nothing does.

**7 · OUTRO** — does it summarise, remind the viewer of the pain solved, and land on a high note?
Or does it stop dead / cut to a CTA? **Quote the last line.**

**8 · NATIVE EMBED** — where does the CTA sit?

| | |
|---|---|
| **native** | woven into a point as the solve for a pain already raised |
| **bolted on** | appended after the content ends |

**9 · E vs R VERDICT** — one line. Did reality beat the expectation, meet it, or miss it?
Then two lines: **WHAT TO STEAL** and **WHAT TO DROP.**

### The two rules of this pass

1. **Quote, do not paraphrase.** *"He opens with a bold claim"* is worthless.
   *"You just need 5 weeks to master the 5 pillars of AI engineering"* is usable. Every verdict
   carries the words it is a verdict about.
2. **Strip the topic, keep the sentence architecture.** What they talk about is theirs. **How
   the sentence is built is reusable forever.**

---

# ═══ PASS 2 · CAPTION ═══  →  `script.md`

Per winner, the **full** caption. Instagram captions do a different job from the spoken track.

| Check | |
|---|---|
| **LENGTH** | word count |
| **JOB** | **the argument** (carries the thinking) · **the shelf** (indexes a series, e.g. `"Ep 16:"`) · **the list** (restates the content) · **the gate** (only a CTA) · **nothing** |
| **CTA** | where it sits — first line, last line, absent |
| **HASHTAGS / SEO** | count, and whether it is a keyword wall |
| **RELATION TO CARD** | does it repeat the title card, extend it, or do a different job? |

> **THE OPEN CONFLICT — record, never average.** `developer_mannjadwani` runs 3–8 word captions
> at 17.19x. `_roshnichellani` runs 100–150 word arguments at 4.69x. `devtalksbusiness` runs a
> **6-word series index** at 3.37x. **Three lengths, three jobs, all working.**
> **Add this creator's data point. Do not resolve it.**

---

# ═══ PASS 3 · PROFILE ═══  →  `teardown.md`

> **⚠️ REVISED DAY 27 — THE FOLLOWER COUNT IS OUT OF SCOPE.** This pass used to require
> `opencli instagram profile <handle>`, which runs on **Windows only** and has never been run
> for any creator. **A step that can never execute from here is a bug, not a blocker** — so it
> is removed rather than left failing. `qualify` gate 3 already records `followers: unknown`
> and cuts nobody, so nothing downstream ever depended on it. **Never estimate a follower
> count, and do not open a blocker for its absence.**

**Run this pass entirely from the frames in `raw/frames/`.** Reel Intake screenshots show the
creator's grid in the background — that is the whole source.

| Check | |
|---|---|
| **GRID SYSTEM** | is there a repeating title-card template? same position, same face, same colour? Does the grid read as one account or as unrelated posts? |
| **PINNED** | what did they choose to pin, and does it match what they now make? (`pieces.md` carries the pinned rows) |
| **THREE-SECOND READ** | a stranger lands on this profile — what do they understand? |

**If no frames exist, write `grid: not assessable — no frames` and move on.**
**If frames exist but were not reviewed, say exactly that.** Never write "not collected" for
material that is on disk.

---

# ═══ PASS 4 · THE ACCOUNT ═══  →  `teardown.md`

*(This is the original teardown. It now runs AFTER the script pass, and it is the smaller half.)*

**1 · Strip the topic.** Their subject is theirs. What remains is shape.

**2 · Find the repetition.** *"Used in 7 of 10"* is a finding. *"He did this once"* is noise.
**Report the count every time.**

**3 · Name the mechanic** against `psychology.md` — orienting response · open loop and where it
closes · click confirmation · the undercut · contrarian contrast · stated cost · objection
handling · which trust leg · second-best-first ordering.

**4 · RETENTION and REWARD** on every structure.

> **RETENTION** — what holds attention at **5s, 12s and 20s.** Name the device, not the feeling.
> **REWARD** — what the viewer **walks away holding.** If the honest answer is *"nothing — they
> were entertained"*, write that. It is a real finding and usually explains why a piece did not
> travel.

**5 · AWARENESS of the opening** — **broad** (pain/desire, *"if you want…"*) or
**practitioner-level** (inside a problem only insiders recognise)?

> **A conditional frame is only as broad as its CONDITION.** *"If you want to stop paying for X"*
> is broad — almost anyone qualifies. *"If you use Claude AI"* is a practitioner filter wearing a
> broad frame's clothing, and it ran at **0.18x**. Test the fraction of the scroll that qualifies,
> never the words *"if you"*.

**6 · HITS vs THEIR OWN MISSES.** Comparing a creator to themselves controls for audience,
algorithm and topic. Winners have transcripts, controls have captions — **compare at the level
both support**, and say plainly when a difference could only be checked with a transcript.

**7 · THE ADAPTATION NOTE.** What transfers, what does not. If a move works because they have
500k followers and an assumed track record, **it does not transfer and copying it reads as
posturing.** Say so.

**8 · WHICH READER?** `peer` (wants the craft, buys the product) · `buyer` (wants the outcome,
buys the service) · `both`. **Decided by which end the piece OPENS on, not by who the creator
is** — the hook-end rule in `niche.md`. `both` only when it genuinely survives being told to
someone non-technical.

**9 · COVERAGE.** Does the watchlist teach shapes for **both** offers? Not a purity check — a
coverage check. **Peers are the second revenue line, never a leak.**

> **THE STANDING CHECK, and it is failing.** Content that reaches only people who do what
> Shubham does builds the **supply side**. Ten teardowns in, that is what the watchlist mostly
> teaches. **State plainly, every run, who this creator's audience actually is and whether they
> could hire him.** Freelancers and creators building SaaS, MVPs, AI automation and dev projects
> are inside the audience. **Video editors and job-seekers are not.**

---

# OUTPUT 1 — `script.md`

```
# script — <handle>
RUN <date> · <n> scripts · VERIFIED against metrics.csv: <pass|FLAGGED>

── SCRIPT #<n> · <engagement ratio>x / <likes ratio>x · <word count> words ──

PACKAGING      card:    "<verbatim>"
               caption: "<verbatim>"
               cover:   <what is on screen at 0s>
               expectation set: <one sentence>

CLICK CONFIRM  line 1: "<verbatim>"
               confirms: ✅/✗    beats it: ✅/✗ — <why>

INTRO          context ✅/✗  "<quote>"
               common belief ✅/✗  "<quote>"
               contrarian ✅/✗  "<quote>"
               proof ✅/✗  "<quote>"
               plan ✅/✗  "<quote>"

BODY ORDER     <n> points · <escalating|flat|decaying> · strongest was #<n>
VALUE LOOP     what <n>/<n> · how <n>/<n> · why <n>/<n>
REHOOKS        "<verbatim seam line>"  — or NONE, and what holds instead
OUTRO          "<last line verbatim>"  — <summarises|stops dead|cuts to CTA>
NATIVE EMBED   <native|bolted on> — <where>

E vs R         <beat|met|missed> — <one line>
WHAT TO STEAL  <one line>
WHAT TO DROP   <one line>

── CAPTION #<n> ──
LENGTH <n> words · JOB <argument|shelf|list|gate|nothing> · CTA <where>
HASHTAGS <n> · vs CARD <repeats|extends|different job>

── ACROSS THESE SCRIPTS ──
what all <n> do the same · what only the best one does · the intro parts always skipped
```

# OUTPUT 2 — `teardown.md`

```
CREATOR / SERVES / AUDIENCE — can they hire him? / SELLS
ANALYSED <n> pieces — <w> winner, <c> control · engagement AND likes ratios · GAP both ways

── PROFILE ──        bio · grid system · pinned · three-second read
── STRUCTURES ──     S<n> name · used in <n> of <n>
                     beats / RETENTION / REWARD / MECHANIC / AWARENESS / READER
                     DOWNGRADE <what this sounds like at his standing> / TRANSFERS
── HOOK PATTERNS ──  openings as reusable moves, mechanic + awareness named
── PACING ──         cut rhythm · dead air · text timing · beat length
── LANGUAGE ──       register · Hindi/Hinglish/English · on-screen language
── HITS vs MISSES ── winners share … | misses share …
── DOES NOT TRANSFER ── and why
── COVERAGE NOTE ──  what this adds · WHO THE AUDIENCE IS · what is still missing
── PROMOTE ──        5+ of 10 AND transfers = yes  ·  see the two bars below
── LIMITS ──         what could not be checked and why
```

---

# RULES

1. **One creator per run. Script pass first.**
2. **Verify every winner against `metrics.csv` before analysing it.** (Step 0)
3. **Never record a topic.** Topic may decide which pieces get read; it may never leave the file.
4. **Always report the count** — "7 of 10", never "often".
5. **Quote, never paraphrase**, in the script pass. A verdict without its words is an opinion.
6. **Never infer performance without numbers.** Record both ratios. Never average them.
7. Every structure gets `RETENTION`, `REWARD`, `AWARENESS`, `READER` and a `DOWNGRADE` line.
8. **Never treat a peer-serving creator as a problem.** Report coverage, not purity — but always
   state whether the audience could hire him.

## THE TWO BARS — added Day 27

**A caption-level pattern promotes at 5 of 10.** The control set is captions, so ten exist to
count across. This is the original bar and it is unchanged.

**A pattern living in the BODY, the SCRIPT or the FRAMES cannot reach 5 of 10 by construction** —
only 3 winners have transcripts and at most 2 have frames. Applying the caption bar to them
silently discards every script finding. **That defect cost Batch 2 five real findings.**

> **SCRIPT and PRODUCTION patterns promote at: 3 of 3 winners in this account
> AND confirmed in a second account.**
>
> **Cross-account is the substitute for cross-post.** A pattern in one account's three winners is
> a hypothesis; the same pattern in a second account's three is a finding. **Record it as a
> hypothesis on the first sighting so the second one has something to confirm.**
