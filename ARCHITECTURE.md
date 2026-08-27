# ARCHITECTURE — the workflow, end to end

---

# THREE LAYERS

```
┌──────────────────────────────────────────────────────────┐
│ BRAIN            slow · changes rarely                   │
│   niche · psychology · strategy · voice · swipe · ledger │
│   Everything below reads these.                          │
└──────────────────────────────────────────────────────────┘
                          ▲ reads
┌──────────────────────────────────────────────────────────┐
│ PIPELINE         fast · runs per post                    │
│   RESEARCH → ANALYZE → WRITE → your rewrite → DOCTOR     │
└──────────────────────────────────────────────────────────┘
                          │ writes back
┌──────────────────────────────────────────────────────────┐
│ RECORD           grows every time something ships        │
│   published · hook-bank · corrections · ledger           │
│   After ~20 posts this layer overrides the brain.        │
│   When evidence contradicts theory, evidence wins.       │
└──────────────────────────────────────────────────────────┘
```

**`brain/niche.md` is the strategy.** Everything else in this document is tactics executing
it. It is written, status WORKING, and it is revised from real data at 20 posts — not
re-argued before then.

---

# RESEARCH VS ANALYZE

> **RESEARCH answers "what exists?" — it never has an opinion.**
> **ANALYZE answers "so what, and what in it is mine?" — it never fetches.**

Research hands Analyze facts. Analyze hands the writers a verdict. A skill that does both
cannot be debugged: when the output is bad you can't tell whether the input was thin or the
judgment was wrong.

| | RESEARCH | ANALYZE |
|---|---|---|
| Direction | outward — goes and gets | inward — judges what it was given |
| Output | material, links, facts | a teardown, a Brief, a verdict |
| Never | recommends, ranks by taste | fetches, searches, browses |

---

# THE SIX RUNNING SKILLS

| Skill | Type | Job | Clock |
|---|---|---|---|
| `topic-scout` | RESEARCH | 10-minute sweep, two halves — trending (ring 4) and resources (ring 1). Recommends nothing. | daily |
| `creator-analyst` | ANALYZE | tear down one creator → shapes only, topics stripped, reader and awareness level tagged | per creator |
| `brief-builder` | ANALYZE | the Brief + verdict. Assigns ring, reader, stage. | per post |
| `linkedin-writer` | WRITE | LinkedIn post or carousel. English. One reader. | per post |
| `script-writer` | WRITE | Instagram reel — spoken / on-screen / visual, three tracks | per post |
| `script-doctor` | ANALYZE | reads **your** rewrite, flags what you weakened, records the mix | per post |

`niche-finder` is a **setup skill and it has run.** `brain/niche.md` was written on
2026-08-25. It runs again only if the niche is deliberately reopened — not as part of the
per-post loop.

---

# THE PER-POST LOOP

```
  INPUT ─── 1 trending          (topic-scout, or you spot it)   external → Mode A
        ├── 2 a resource found  (topic-scout half B, or you)    external → Mode A
        ├── 3 repo / release / article  (you paste a link)      external → Mode A
        ├── 4 YOUR failure, bug or fix  (you say one line)      PERSONAL → Mode B
        └── 5 what you BUILT            (you name it)           PERSONAL → Mode B
                          │
                    brief-builder
              assigns RING · READER · STAGE
                          │
                     THE BRIEF ──▶ publish | hold | kill
                          │
                    you approve
                          │
            ┌─────────────┴─────────────┐
            ▼                           ▼
      linkedin-writer            script-writer
      ships today                records later
            │                           │
            └─────────────┬─────────────┘
                          ▼
                   YOU REWRITE   ← the real work, never skipped
                          ▼
                   script-doctor  flags only, never rewrites you
                          ▼
                 publish → work/published.md
                   with RING and READER recorded
```

Inputs 4 and 5 are yours, and **only those are structurally impossible to make generic.**
Nobody else has your bugs.

> **Open:** Shubham wants the Mode A / Mode B labels removed and a third branch added for
> *something you thought* — a raw note or opinion with no external source and no build
> behind it. Deferred deliberately until the niche was written. Now unblocked, not yet done.

---

# THE FOUR GATES

Every Brief passes all four or it does not become a post.

| Gate | Fails when | Result |
|---|---|---|
| **The kill rule** | `GAPS` empty **and** `YOUR STANDING` empty | kill |
| **The ring** | it would be ring 5 | kill |
| **The NOT-list** | it hits any of the five | kill |
| **The reader** | `peer` or `buyer` cannot be decided | hold |

**A kill is a successful run.** Never produce a post to be helpful.

---

# THE MIX — 3-2-2, and how it is actually enforced

A mix is arithmetic over a series, so something has to hold the series.

```
brief-builder   reads the last six entries of work/published.md
                assigns RING with the rolling count in front of it
script-doctor   writes RING and READER into work/published.md on publish
                and reports the rolling mix and the peer/buyer ratio
```

**Without those two steps the mix silently does not happen.** Neither does the peer/buyer
ratio, and neither does the post-20 review.

| Ring | Content | Per seven |
|---|---|---|
| **1** | resources found and where · what I built and broke · systems and how they're wired · getting AI to produce work that doesn't look AI-generated | **3** |
| **2–3** | the basics nobody teaches · beliefs I can argue · what a business needs built and what getting it wrong costs | **2** |
| **4** | AI and industry news with my opinion · founders' journeys told from the reader's position | **2** |
| **5** | — | **0** |

---

# THE FUNNEL — every post declares a slot

| Slot | Day | Job | Trust leg |
|---|---|---|---|
| **TOFU** | Mon | make new people find you — strong opinions, a release you have a view on, **free value resources** | attraction |
| **MOFU** | Wed | make them believe you — lessons, **mistakes**, tutorials, a real build | authenticity + authority |
| **BOFU** | Fri | say what you build and who it is for | the offer |

**The earlier slots earn the right to ask in the later one.**

**BOFU splits by reader.** To a **buyer**: state plainly what you build and who for — a
statement, never a pitch at zero followers. To a **peer**: hold. There is no product yet,
and a peer-BOFU with nothing behind it is a promise the engine cannot keep.

---

# THE BRIEF — the contract between analyze and write

The writers see only this. Never the raw transcript, never the raw interview answers.

```
ID · TYPE (external|personal) · SOURCE · CONTENT TYPE
CORE CLAIM      one sentence
EVIDENCE · SPECIFICS · VERIFICATION            [Mode A]
ROOT CAUSE · FIX · PROOF                       [Mode B]
GAPS            what the source missed or got wrong
YOUR STANDING   the ledger entry that qualifies him — or "none"
RING            1 | 2 | 3 | 4                  ← 5 is not legal
READER          peer | buyer                   ← exactly one
OFFER           service | product | none
TRUST LEG       attraction | authenticity | authority   ← one
VILLAIN         the practice or default this is against
FUNNEL SLOT     TOFU | MOFU | BOFU
STAGE           found | installed | testing | shipped | n/a
STANDING TYPE   built-for-self | delivered-to-client
NOT-LIST        ✓ cleared — or the item it hits
VERDICT         publish | hold | kill    ROUTE  linkedin | reel | both
```

Full field notes in `work/_TEMPLATE-brief.md`.

---

# TIME

| | LinkedIn | Reel |
|---|---|---|
| Brief + writing | 35 min | 20 min |
| Recording | — | 20–45 min |
| Editing | — | 45–90 min |
| **Total** | **~35 min, ships today** | **~2–3 hrs, needs a block** |

Only ideas that prove out in text get recorded.

---

# WHAT THE ENGINE DOES NOT HAVE

Named honestly, because a missing piece that nobody names becomes a silent failure.

- **No `outreach` skill.** `niche.md` makes outreach the client channel and content the
  proof layer, with a September start. Nothing in the folder does outreach. **This is the
  most valuable missing skill.**
- **No post counter.** Four decisions are deferred to post 20. `script-doctor` announces it;
  nothing else tracks it.
- **No product.** The peer half of the funnel has nothing to sell until one exists.
- **No git repo.** Every file here exists in exactly one place.

---

# WHERE THE RULES COME FROM

`sources/_log.md` lists every source and what it gave. The operating rules live in
`brain/niche.md`, `brain/psychology.md` and `brain/strategy.md` — **those are the memory.**
`sources/raw/` is archive, never loaded as context.

**Five rules are ours, invented here:** the kill rule · confidence downgrade · `ledger.md`
as a maintained file · the buyer-vs-peer check, resolved into two offers · text first, reel
as the multiplier.
