---
name: creator-analyst
description: ANALYZE. Tears down one creator at a time — reel transcripts, captions and engagement numbers — into a teardown that captures SHAPE and strips TOPIC. Compares their hits against their own misses, and records which of the two readers each shape serves. Feeds brain/swipe.md. Use when Shubham names a creator he admires or drops material from one account.
---

# creator-analyst

**One creator at a time.** Ten pieces from one beats two from five — the finding is the
*repeated* pattern, and repetition is invisible in two.

**Read:** `work/creators/<slug>/raw/` · `brain/niche.md` · `brain/psychology.md` ·
`brain/swipe.md`
**Write:** `work/creators/<slug>/teardown.md`

**INPUT CONTRACT.** `raw/` is populated by **`scout`**, which fetches the creator's recent
pieces, selects the anomalies by arithmetic, and transcribes the winners. This skill never
fetches anything and never chooses which pieces to analyse — **it analyses what is in `raw/`
and nothing else.** If `raw/` is empty, say so and stop; do not go looking for material.

---

> **Shapes are reusable forever. Topics are theirs.**
>
> **Confidence downgrade.** A structure from a large account carries that account's
> authority. Authority does not transfer. Every structure records what it sounds like at
> Shubham's standing — 1.5 years in, real artifacts, no follower base, zero clients.

---

## WHAT IS IN `raw/`

```
pieces.md                  every post scout fetched — WINNER and NORMAL, with numbers
<index>-transcript.md      one per WINNER only
metrics.csv                that creator's full history, all runs
```

**Two kinds of piece, and both are needed.**

| | | |
|---|---|---|
| **WINNER** | that creator's **top 3 pieces by engagement** — selected by rank in `scout`, never re-judged here | full transcript |
| **NORMAL** | everything else scout fetched | caption + numbers only |

**Captions: read `FULL CAPTION`, never the truncated line.** OpenCLI cuts every caption at 100
characters, mid-word — the CTA and the offer usually sit past the cut. The truncated line exists
to identify a post, not to be analysed. If `FULL CAPTION` is blank for a winner, **say the
caption was not collected and analyse the transcript alone.** Never infer a CTA from a sentence
that was cut off.

**The NORMAL rows are not filler.** Two things in this skill are impossible without them:
*"used in n of 10"* needs ten pieces to count across, and *"hits vs their own misses"* needs
the misses. Three winners alone cannot support either. **Do not discard the control set and
do not analyse winners in isolation.**

`scout` has already done the selection, by arithmetic. **Do not re-select and do not add
pieces of your own.**

Every piece arrives with `date · caption · likes · comments · engagement · outlier`.
**`engagement = likes + comments`** — Instagram exposes no view counts through any free
route (`tooling.md` LIMIT 1). It is a proxy and must be named as one; **never describe it as
views, reach or impressions.** Anything missing its numbers is analysed as *"no data"* —
never estimated.

**Fewer than 8 pieces total: say what that costs.** You can describe; you cannot find a
pattern — and the pattern is the whole output. Ask for another `scout` run first.

**Claude cannot watch video.** A reel with no transcript and no screenshots is invisible.

---

## THE STEPS

**1 · Strip the topic — first.** Their subject matter is theirs. What remains is shape.

**2 · Timestamp-map every piece, separately.**
```
0-3s     SPOKEN / ON-SCREEN TEXT / VISUAL   ← all three, recorded separately
3-8s     the pivot. what changes.
8-20s    body beats — how many, how long, what's on screen
close    question | CTA | hard cut | loop back to the hook
```
For written posts: the fold, the first two lines, paragraph rhythm, where the data lands
relative to the story, the close.

**3 · Find the repetition.** **"Used in 7 of 10" is a finding. "He did this once" is
noise.** Report the count every time.

**4 · Name the mechanic** against `psychology.md`. This is what makes a teardown usable
instead of descriptive.

Not *"he opens with a bold claim"* — **which** mechanic?
orienting response · an open loop, and where does it close · click confirmation ·
the undercut · contrarian contrast · stated cost · objection handling · which trust leg ·
second-best-first ordering or strongest-first · where the rehooks are and what the seam
lines sound like.

**4b · RETENTION and REWARD — the two the engine used to miss.**

A hook explains why someone *starts*. These two explain why anyone *stays*, and what they
*keep*. Record both on every structure.

> **RETENTION** — what holds attention at **5s, 12s and 20s.** Name the device, not the
> feeling: an open loop and where it closes, a pattern interrupt, a seam line, a rehook, a
> visual change on the beat. *"It's engaging"* is not an answer.
>
> **REWARD** — what the viewer **walks away holding.** A method they can run, a name for
> something they had noticed but could not label, a number, a resource, a decision made
> easier. If the honest answer is *"nothing — they were entertained"*, write that. It is a
> real finding, and it is usually why a piece did not travel.

**5 · The awareness level of the opening.** Record this on every hook, because it is the
one thing the engine is currently weakest on.

> Does the opening land on **pain or desire** — a broad *"if you want…"* / *"if you don't
> want…"* — or does it open **at the practitioner's level**, inside a problem only people
> already in it recognise?

Both appear in the wild. Broad openings travel; practitioner openings convert an existing
audience. **A creator with 500k followers can afford a practitioner opening. Shubham cannot
yet.** Note which, every time.

**6 · Hits vs their own misses.** This is the "why are they performing so well" answer, and
it is done by comparing them **to themselves** — which controls for audience, algorithm and
topic, everything that makes cross-creator comparison meaningless.

The `WINNER` rows are this creator's **three highest-engagement pieces**; the `NORMAL` rows are
everything else they posted. Each row carries its `ratio` against their own median — read it as
context for how far ahead a winner actually was, never as a bar something had to clear.
**What do the winners have that the others don't** — hook mechanic, awareness level, format,
length, proof on screen, emotional register? What do the misses share?

The winners have transcripts and the control set has captions only, so **compare at the level
both support** — opening line, format, length, subject framing — and say plainly when a
difference could only be checked with a transcript the control set doesn't have.

**Without numbers: say so.** Never infer performance from vibes.

**7 · The adaptation note.** For each structure: **what transfers and what does not.** If a
move works because they have 500k followers and an assumed track record, it does not
transfer, and copying it reads as posturing. Say so explicitly.

**8 · Which reader does this shape serve?**

The engine writes to **one reader per piece.** Both readers are defined in `brain/niche.md`
by **state, never by job title**:

> **PEER** — someone trying to build something and stuck. Codes or doesn't; irrelevant.
> Wants the craft.
> **BUYER** — someone with a business problem who wants it gone. Wants the outcome.

They are often the same person at two different moments, so **the tag is decided by which end
the piece opens on, not by who the creator is.** A build opened at the craft end reaches
peers; the same build opened at the cost end reaches buyers. That is the hook-end rule in
`niche.md`, applied to somebody else's work.

A shape promoted to `swipe.md` without a reader is unusable — the writer cannot tell whether
it fits the piece in front of them.

Tag every structure **peer**, **buyer**, or **both** — and *both* only when it genuinely
survives being told to someone with no technical background.

**9 · Watchlist coverage — not a purity check.**

The old question here was *"is his watchlist drifting all-peer?"*, on the theory that peers
are a leak. **That is settled and it was wrong: peers are the second revenue line.**

The real question is **coverage**:

> Does the watchlist teach shapes for **both** offers — peer shapes for the product line,
> buyer shapes for the service line?

If every creator on the list makes tooling content for builders, the engine learns only peer
shapes and the buyer half of the funnel has nothing to imitate. **Say so when it happens.**
That is a gap to fill with one more creator, not a reason to drop the ones he has.

---

# OUTPUT — `teardown.md`

```
CREATOR      <name / handle>
SERVES       peer | buyer | both        ← which reader this creator's shapes teach
AUDIENCE     who actually watches
SELLS        what they monetise, if visible — product | service | both | unclear
ANALYSED     <n> pieces — <w> winner, <c> control · engagement = likes + comments

── STRUCTURES ──
S1  <shape name>                    used in <n> of <n>
    0-3s / 3-8s / body / close
    RETENTION  <what holds at 5s / 12s / 20s — name the device>
    REWARD     <what the viewer walks away holding, or "nothing">
    MECHANIC   <psychology.md principle>
    AWARENESS  broad (pain/desire) | practitioner-level
    READER     peer | buyer | both
    DOWNGRADE  <what this sounds like at his standing>
    TRANSFERS  yes | no | partly — because <one line>

── HOOK PATTERNS ──   <openings as reusable moves, mechanic + awareness level named>
── PACING ──          <cut rhythm · dead air · text timing · beat length>
── LANGUAGE ──        <register · English/Hinglish ratio · sentence length>
── HITS vs MISSES ──  winners share: … | misses share: …
── DOES NOT TRANSFER ── <and why — stops re-adopting a bad idea in three months>
── COVERAGE NOTE ──   <what this creator adds to the watchlist, and what is still missing>
── PROMOTE TO SWIPE ── <5+ of 10 AND transfers = yes>
```

# RULES
1. One creator per run.
2. Never record a topic. Topic may decide which pieces get read; it may never leave the
   teardown. If you catch yourself writing what they talk about, stop.
3. Always report the count — "7 of 10", never "often".
4. Never infer performance without numbers.
5. Every structure gets `RETENTION`, `REWARD`, `AWARENESS`, `READER` and a downgrade line.
   No exceptions — `swipe.md` refuses an entry missing any of them.
6. Promote to `brain/swipe.md` only at **5+ of 10 AND transfers = yes**.
7. Never treat a peer-serving creator as a problem. Report coverage, not purity.
