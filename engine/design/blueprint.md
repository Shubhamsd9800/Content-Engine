# THE ENGINE BLUEPRINT — v3

**Content Engine — the only design document.**
Written Day 22 · 26 August 2026 · **revised Day 24, 29 August 2026**

> **This file is the single source of truth for how the engine is built.**
> `engine/design/architecture.md` was a second document describing the same system. It has
> been folded into this one and moved to `archive/superseded/`. If you are looking for the
> Brief contract, the 3-2-2 mix, the funnel or the time costs, they are sections 06 to 09
> below — they used to live in that file and nowhere else.

**What v2 changed:** the tools layer stopped being a plan — Agent-Reach and OpenCLI are
installed and were proven against a live account. Section 10 is written against what
actually ran. Blocker 2 (no git repo) and Bug 3 (the topic rule) are both closed.
**What v3 changed:** `architecture.md` folded in (sections 06-09 and 16), the folder
restructured to three roots, `scout` · `thought-partner` · `qualify` built.

`brain/reference/tooling.md` is the ground truth for anything tools-related and wins over
this document where the two disagree. `engine/design/status.md` holds the live task list.

The whole system in one place — two pipelines, three layers, the files, the skills, the
gates, and the honest list of what is blocking it. Written to be learned in an hour, not
followed as a checklist.

> 2 pipelines · 10 skills · 7 gates · 0 skills left to build · **0 posts published**

---

## 01 · WHAT THIS IS FOR

Ask a model for a LinkedIn post and it reads as AI-generated. Everyone can tell. Ask it
for a landing page and you get the same effect in another medium.

You hit that wall twice, in two unrelated domains, and both times built the same fix:
**a structured input layer in front of the model.** Design skills in front of the UI
request; a brain, a niche and a Brief in front of the content request.

**The model already has the capability. The input is the bottleneck.** That sentence is
what this entire engine implements — and it's why the engine is mostly files rather than
code. The files *are* the input layer.

It also settles what is being sold, if this ever gets sold: **never "AI writes your
posts."** Everyone has the model. Almost nobody has the layer that stops the output
sounding like it.

---

## 02 · TWO PIPELINES, ONE CONNECTION

This is the thing that keeps tangling. It is not one system. It is two, they run on
different schedules, and they touch at exactly one file.

```
PIPELINE A — LEARN · about monthly
  creators ──▶ qualify ──▶ scout ──▶ creator-analyst ──▶ swipe.md
  (links +      gets, never       judges, never       shapes,
   your notes)  judges            gets                not topics
                                                         │
                                            the only shared file
                                                         │
                                                   read at write time
                                                         │
PIPELINE B — WRITE · per post                            ▼
  an idea ──▶ brief-builder ──▶ 4 gates ──▶ a writer ──▶ YOU REWRITE
  (1 of 6      ring · reader     publish     linkedin      never skipped
   inputs)     · stage           or kill     or script          │
                                                                ▼
       published.md  ◀──  script-doctor  ◀────────────────────┘
       + voice · hooks · fixes    flags, never rewrites

       └────▶ every published post feeds the brain back
              this is the only loop that closes
```

**Pipeline A** fills `swipe.md`. **Pipeline B** reads it. They share no other file, no
skill and no trigger.

The long return path is the loop that makes the engine improve — and **it only turns when
something is actually published.**

---

## 03 · THREE LAYERS — WHAT CHANGES AT WHAT SPEED

Underneath both pipelines. The layers are separated by *how often they change*, not by
what they hold.

**BRAIN** — slow · everything reads it
What you believe and who you're for. Revised deliberately, never mid-post.
`niche.md` · `psychology.md` · `voice.md` · `strategy.md` · `swipe.md` · `ledger.md`

**PIPELINE** — fast · runs per post
The skills. They hold no opinions — every judgment is read out of the brain. That's why
changing one brain file changes every future post without editing a single skill.

**RECORD** — grows when something ships
What actually happened. Around twenty posts it starts overriding the brain, because by
then you have evidence and evidence beats theory.
`published.md` · `hook-bank.md` · `corrections.md`

---

## 04 · PIPELINE A — LEARNING FROM CREATORS, STEP BY STEP

Three rounds, cheapest first. The point of the ordering is that expensive work only ever
runs on creators that survived cheap work.

**Why study creators at all:** to learn *how* things are said, never *what* is said. A
structure is reusable forever. A topic belongs to them, and borrowing it makes you a worse
copy of someone with a bigger account.

### ROUND 1 — the sort
All 30. Costs nothing — no tools, no fetching.

From your links, your one-line notes, and their bios: sort each into **shape reference**,
**business inspiration only**, or **neither**. Tag reader — peer or buyer. Tag position —
in-niche or adjacent.

**Check before continuing:** does at least one survivor serve *buyers*? If every creator
teaches builders, the engine only ever learns peer shapes and half the funnel has nothing
to imitate.

*Out: roughly 15.*

### ROUND 2 — the shallow pass
Channel-level numbers only. Cheap — one call each.

Posting frequency, median views, follower-to-view ratio. This finds two things worth
knowing before spending real effort: creators whose reach is dead despite a big following,
and creators posting so rarely there is nothing to find a pattern in.

*Out: 8–10 worth going deep on.*

### ROUND 3 — scout
One creator at a time. This is where the tools do real work.

**a.** List their recent pieces with **likes and comments** attached. Twelve per run is the
ceiling (`tooling.md` LIMIT 2); `metrics.csv` accumulates across runs.

**b.** Compute **that creator's own median engagement**, where `engagement = likes +
comments` — theirs, not an industry figure. Instagram exposes no view counts through any free
route, so this is a **proxy** and is never called reach. This
controls for audience size, algorithm and topic at once, which is exactly what makes
comparing two different creators meaningless and comparing a creator to themselves
meaningful.

**c.** Take that creator's **top 3 pieces by engagement**. Record each piece's `ratio`
(engagement ÷ median) and the creator's **GAP** (highest ÷ median). Selection is by **rank**;
the ratio is recorded, never used as a gate.

> **Superseded Day 25 — the 2× bar.** It was picking pieces *and* judging creators at the same
> time, and as a picking rule it cannot promise three: `nick_saraev`'s first live run gave one
> post over 2×, and an 8% move in his median would have given none, from the same twelve posts.
> The teardown needs three pieces; a threshold cannot guarantee three. The creator-level
> judgement moved to **GAP**, which is recorded here and acted on in the cut, never inside a
> fetch step.

> **Superseded Day 24.** This round originally split *reach outliers* from *resonance
> outliers* — the second needed a like-to-view ratio. **There are no view counts**, so the
> split is unmeasurable and the engine uses one bar. Recorded rather than deleted, so it is
> not reinvented.

**d.** Tag each flagged piece *peer-facing* or *buyer-facing* by its subject. This is the
one place topic is allowed to matter — and only to guarantee coverage, never to be copied.

**e.** Pull full transcripts for the flagged pieces only, **and hand on every piece fetched,
flagged `WINNER` or `NORMAL`.** Without the control set there is nothing to compare the
winners against, every finding becomes a guess, and a shape can never reach "5 of 10".

> **This step was dropped when `scout` was written on Day 24 and restored the same day.**
> The cap of 3 caps *transcription*, never the handoff.

*Out: a folder of material and a numbers file. No opinions anywhere in it.*

### ROUND 4 — creator-analyst
Reads that folder. Never goes online.

Maps each piece second by second: what is said, what is on screen, what changes at the
pivot. Names the mechanic against `psychology.md`. Records the awareness level of the
opening, the retention device in the middle, the reward at the end, which reader it serves,
and what the same move would sound like at your standing — no followers, 1.5 years in, no
clients.

Then compares their hits to **their own misses**. That is the real answer to "why is this
working", and it is only answerable within one account.

### ROUND 5 — promotion
A shape enters `swipe.md` only if it appears in **5 or more of 10** pieces *and* survives
the standing downgrade. Everything else is written to **DID NOT TRANSFER** with the reason,
so the same bad idea is not re-adopted in three months.

---

## 05 · PIPELINE B — HOW A POST ACTUALLY GETS WRITTEN

A real trace, from one sentence you say out loud to a published post.

**YOU**
> "I wired five marketplace skills into a build chain and the chain stopped at step three
> of ten."

One line. That's the whole input. Six input types exist: something trending, a resource
found, a link you paste, **your own bug or fix**, **something you built**, and — once it's
built — **a thought you had**. The middle two are the only inputs that are structurally
impossible to make generic, because nobody else has your bugs.

**brief-builder**
Asks what broke, the root cause, the fix, and what proves it. Checks `ledger.md` — entry 10
covers exactly this, so **standing is populated**.

Assigns **ring 1**, **reader: peer**, **stage: installed**, **slot: MOFU**, **standing:
built-for-self**. It never writes a hook — that is the writer's job, and separating them is
what stops a Brief being quietly optimised for a clever line instead of a true one.

**THE GATES**
Kill rule — standing present, passes. Ring 5 — no. NOT-list — no client claim, no vlog,
passes. Reader — peer, decided. **Verdict: publish.**

**linkedin-writer**
Reads `voice.md` for register, `psychology.md` for the mechanic, `swipe.md` for a shape that
survives the downgrade. Opens on the pain, broadly framed — never at the practitioner's
level, because most people scrolling are not trying to learn.

Generates **nine hooks, uses one.** The other eight go to `hook-bank.md` — a rejected hook
often fits a different post exactly.

**YOU**
> The rewrite. Never skipped.

This is the step the entire system exists to protect. Everything before it is scaffolding
so that what you're rewriting is already structurally sound.

**script-doctor**
Compares your version to the draft. Flags what you softened. Logs every diff into
`corrections.md` and `voice.md`'s OBSERVED section, writes ring and reader into
`published.md`, reports the rolling mix.

**One correction is taste. Two of the same class is a bug in the skill** — the skill gets
rewritten, not the draft patched.

---

> ### The skills are copyable. The ledger is not.
> ### That asymmetry is the business.

---

## 06 · THE BRIEF — the contract between analyze and write

The writers see **only this**. Never the raw transcript, never the raw interview answers.
That boundary is what stops a writer inventing evidence: it cannot reach the source.

```
ID · TYPE (external|personal) · SOURCE · CONTENT TYPE
CORE CLAIM      one sentence
EVIDENCE · SPECIFICS · VERIFICATION            [external input]
ROOT CAUSE · FIX · PROOF                       [personal input]
GAPS            what the source missed or got wrong
YOUR STANDING   the ledger entry that qualifies him -- or "none"
RING            1 | 2 | 3 | 4                  <- 5 is not legal
READER          peer | buyer                   <- exactly one
OFFER           service | product | none
TRUST LEG       attraction | authenticity | authority   <- one
VILLAIN         the practice or default this is against
FUNNEL SLOT     TOFU | MOFU | BOFU
STAGE           found | installed | testing | shipped | n/a
STANDING TYPE   built-for-self | delivered-to-client
NOT-LIST        cleared -- or the item it hits
VERDICT         publish | hold | kill    ROUTE  linkedin | reel | both
```

Full field notes in `work/_TEMPLATE-brief.md`.

> **The FORMAT field is missing from this contract.** See section 15. It is the one known
> hole in the Brief and it is not yet fixed.

---

## 07 · THE MIX — 3-2-2, and how it is actually enforced

A mix is arithmetic over a **series**, so something has to hold the series. Two steps do,
and if either is skipped the mix silently does not happen.

```
brief-builder   reads the last six entries of work/log/published.md
                assigns RING with the rolling count in front of it
script-doctor   writes RING and READER into work/log/published.md on publish
                and reports the rolling mix and the peer/buyer ratio
```

**Without those two steps there is no mix, no peer/buyer ratio, and no post-20 review.**
Nothing else in the engine counts anything.

| Ring | Content | Per seven |
|---|---|---|
| **1** | resources found and where; what I built and broke; systems and how they are wired; getting AI to produce work that does not look AI-generated | **3** |
| **2-3** | the basics nobody teaches; beliefs I can argue; what a business needs built and what getting it wrong costs | **2** |
| **4** | AI and industry news with my opinion; founders' journeys told from the reader's position | **2** |
| **5** | -- | **0** |

---

## 08 · THE FUNNEL — every post declares a slot

| Slot | Day | Job | Trust leg |
|---|---|---|---|
| **TOFU** | Mon | make new people find you -- strong opinions, a release you have a view on, **free value resources** | attraction |
| **MOFU** | Wed | make them believe you -- lessons, **mistakes**, tutorials, a real build | authenticity + authority |
| **BOFU** | Fri | say what you build and who it is for | the offer |

**The earlier slots earn the right to ask in the later one.** A BOFU with no TOFU and MOFU
behind it is a pitch from a stranger.

**BOFU splits by reader.** To a **buyer**: state plainly what you build and who for -- a
statement, never a pitch, at zero followers. To a **peer**: hold. There is no product yet,
and a peer-BOFU with nothing behind it is a promise the engine cannot keep.

---

## 09 · TIME — what each route actually costs

| | LinkedIn | Reel |
|---|---|---|
| Brief + writing | 35 min | 20 min |
| Recording | -- | 20-45 min |
| Editing | -- | 45-90 min |
| **Total** | **~35 min, ships today** | **~2-3 hrs, needs a block** |

**Only ideas that prove out in text get recorded.** The reel is the multiplier on something
already known to work, never the first test of whether it works.

---

## 10 · THE TOOLS LAYER

Skills describe procedure. Something still has to fetch a page. That something is a
separate layer underneath, and keeping it separate is what makes it replaceable.

**Agent-Reach is a toolbox, not a step.** It doesn't wrap anything — reading is done by
calling upstream tools directly, with no wrapper in between.

It does three things: installs the right tool per platform, writes a skill file saying which
tool to use for what, and keeps that routing current when a platform breaks a backend. Each
platform has an ordered list — preferred, then fallbacks — and `agent-reach doctor` reports
which one is live.

**Why that separation matters:** Agent-Reach never knows what a creator is or what a median
view count means. `scout` never knows how to install a downloader. Neither can break
the other, and swapping the whole toolbox out later touches no skill.

> **INSTALLED AND PROVEN — Day 23.** This section described a plan when it was first written.
> It no longer does. Full detail, exact commands and every limit live in
> **`brain/reference/tooling.md`**, which is the ground truth. Where that file and this one
> disagree, that file wins.

| What's needed | Tool | Login? | State | Used by |
|---|---|---|---|---|
| **Instagram posts + likes + comments** | **OpenCLI** | **burner only** | ✅ **proven live** | `scout`, `qualify` |
| A creator's videos and transcripts | yt-dlp | No | ✅ installed | `scout` (YouTube cross-posters) |
| Reel → text | Whisper + ffmpeg | No | ✅ installed, **untested on a reel** | `scout` |
| Any web page as clean text | Jina Reader | No | ✅ | `topic-scout`, outreach |
| Semantic search across the web | Exa via mcporter | No | ⚠️ configured, **never queried** | `topic-scout` |
| Feeds you follow | feedparser | No | ✅ | `topic-scout` |
| Repos, releases, issues | gh CLI | No, for public | ❌ not installed | `topic-scout` |

**The correction v2 makes:** this table originally listed yt-dlp as the source of a creator's
views and likes, and called Instagram *"the careful exception for the few who are only there."*
**That is backwards.** Every creator on the watchlist is on Instagram, so **OpenCLI is the road
everything travels** and YouTube is the bonus lane for those who cross-post.

**Three limits that shape every step downstream:**

1. **No view counts.** Instagram exposes none through any free route. `engagement = likes +
   comments`, recorded as a proxy, never described as reach.
2. **Twelve posts per run.** `--limit 50` returns 12. The accumulating `metrics.csv` is the fix,
   not a flag.
3. **No post URLs from any read command.** All 23 subcommands checked. `pieces.md` carries the
   post INDEX and the URL is copied by hand — **the only manual step in Pipeline A.**

**Note who is absent from the last column:** `creator-analyst`, both writers,
`script-doctor`, `thought-partner`. None of them ever touch a tool. That is law one being
useful rather than decorative.

**Burner rule:** never the brand account, and never in the same browser profile as it —
same profile means same fingerprint, and a flagged burner drags the real one with it. In
practice this is a **separate Chrome install**, containing the burner Instagram and nothing
else. The OpenCLI extension holds `debugger`, `cookies` and `<all_urls>` on that profile —
**the isolation is the security control.**

---

## 11 · EVERY FILE — WHAT FILLS IT, AND FROM WHERE

The most useful table in this document, because it shows which files are waiting on
research and which are waiting on you to publish something. They are not the same problem.

| File | State | What fills it |
|---|---|---|
| `niche.md` | WRITTEN | Done. Revised from real data at 20 posts. |
| `psychology.md` | WRITTEN | Done. Grows from creator teardowns. |
| `strategy.md` | WRITTEN | Done. |
| `ledger.md` | 12 ENTRIES | By interview, when you build something new. |
| `swipe.md` | **EMPTY** | **Pipeline A.** The only empty file research can fill. |
| `voice.md` — rules | WRITTEN | Done — banned words, sentence length, two registers, the angle rule. |
| `voice.md` — OBSERVED | **EMPTY** | **Your rewrites.** Fills after post 1. Cannot be filled any other way. |
| `hook-bank.md` | **EMPTY** | **Writing posts.** Nine hooks per post, eight banked. |
| `corrections.md` | **EMPTY** | **Your rewrites.** |
| `published.md` | **EMPTY** | **Publishing.** |

**Read the right-hand column again.** Five files are empty. *One* of them is filled by
studying creators. **Four are filled by publishing a post and rewriting it.**

That is the single most important fact in this document, and it reframes the whole plan:
the creator pipeline is worth building, and it unblocks exactly one file.

---

## 12 · THE GATES — SEVEN CHECKS

Many gates, small map. That's how both things you asked for are true at once.

**1 — Enough material?** Fewer than five pieces from a creator and you stop.
*Pipeline A · you can describe one piece, but a pattern needs repetition, and repetition is
the finding.*

**2 — Repeated, or a fluke?** A shape needs 5 of 10 to be promoted.
*Pipeline A · "used in 7 of 10" is a finding. "He did it once" is noise.*

**3 — Survives the downgrade?** Does it still work with no followers and no track record?
*Pipeline A · authority does not transfer. A move that works at 500k reads as posturing at
zero.*

**4 — The kill rule.** Gaps empty *and* standing empty means it dies.
*Pipeline B · nothing to add and no right to speak means no post.*

**5 — Ring 5.** Motivational content with nothing under it. Automatic kill.
*Pipeline B · the mix is 3 ring-1, 2 ring-2-3, 2 ring-4 per seven pieces.*

**6 — The NOT-list.** Five items, any hit is a kill.
*Pipeline B · vlogs, trend reels, unangled reposts, client-delivery claims, the day job.*

**7 — One reader.** Peer or buyer, exactly one. Undecidable means hold.
*Pipeline B · writing to both inside one piece is what makes content generic.*

**A kill is a successful run.** A system that never refuses isn't filtering, it's just
producing.

---

## 13 · TWO LAWS THAT STOP IT ROTTING

The parts that break silently, and therefore the parts that matter most if this is ever
handed to someone else.

### Law one — research never judges, analysis never fetches

A skill that gathers *and* evaluates cannot be debugged. When a teardown is useless there
are exactly two causes: thin material, or a wrong reading. Split, you know which and rerun
only the broken half.

Practically too: fetching is mechanical and can repeat unattended. Judging needs a human.
Different work, different cadence, different amount of you.

### Law two — every decision lives in exactly one file

Skills **reference** decisions. They never restate them. The moment a rule is copied into a
skill, that copy starts drifting and nothing tells you.

**This already happened here.** An audit found fourteen decisions no file enforced —
including a skill instructed to carry on regardless if the niche file wasn't ready. The
engine had been told to skip its own strategy, and it took a dedicated search to notice.

The check is cheap: whenever a skill is written or edited, one pass asking *does this
restate a rule, or point at it?*

---

## 14 · BLOCKERS AND BUGS

Found by reading the files, not guessed. Four, ranked by what they cost.

### Blocker 1 — the voice plan does not work as stated

You said you have no brand voice and want it built from studying creators. **Two things are
wrong with that, and the first is good news.**

**You already have one.** `voice.md` is written — banned openings and words, sentence
length, failure language, numbers policy, two full registers for peer and buyer, the
language split, and the angle rule. That is a brand voice. What is missing is not the
voice, it's evidence of it.

**And the file forbids the plan.** Its own words:

> *"Nothing below is written by Claude. voice.md earns its content from diffs — what
> Shubham changed between the draft and what he published."*

That rule is right. Voice copied from creators is how you become a fluent imitation of
someone with a bigger account — the exact failure `swipe.md` exists to prevent, one level
deeper. Creators can teach you **structure**. They cannot give you a voice.

**The fix:** publish one post, rewrite it yourself, and let the diff be the first OBSERVED
entry. That is the only mechanism that exists, and it is unblocked today.

### ~~Blocker 2 — no git repo, seventh day~~ · **CLOSED Day 23**

For seven days every file here existed in exactly one place. On Day 21 fourteen files were
rewritten in place with no backup and the only rollback was chat history. Nothing was lost —
that was luck, not design.

**Fixed.** `github.com/Shubhamsd9800/Content-Engine`, private, initial commit `5bf0c08`,
39 files, verified against `origin/main`.

**Standing rule that came out of it:** never run git from Cowork. A git command through the
Cowork mount leaves an undeletable `.lock` that blocks every later operation on the repo.
PowerShell or Claude Code only, via the `daily-push` skill.

### Bug 3 — selecting by topic contradicts the topic rule

You asked to pick a creator's "most business-purpose videos, based on my niche."
`swipe.md`'s founding law says topics are theirs, shapes are yours. Selecting *by* topic is
how a study quietly turns into topic-borrowing.

**RESOLVED Day 23 — the rule is now written into `swipe.md` as THE TOPIC RULE:**

> **Topic may decide WHICH pieces get read. Topic may never leave the teardown.**

Selecting a creator because they reach business owners is legitimate — it is how both readers
get covered. Carrying their subject matter into `swipe.md` is not. The moment a structure entry
names what somebody talks about, it has failed.

### Note 4 — the word you wanted was not retention

You described a video with 25k comments asking for a link, versus one with 4k likes that a
business owner noticed — and asked to be corrected if the term was wrong. It was, and the
distinction underneath it is sharp.

**Retention** is within a single piece: what percentage keep watching past three seconds,
past twenty. It's a craft property of the video itself.

What you actually described is **reach versus qualified attention** — and that is precisely
your two-reader model showing up in real numbers. Peer content produces volume: comments,
saves, link requests, an Indian audience that engages hard. Buyer content produces few
numbers and the *right* viewer. **A post that reaches one business owner outperforms one
that reaches 25,000 peers, if the goal is a client.**

Which is why the engine refuses to average them: `READER` is one value per post, and judging
a buyer post by peer metrics would kill the posts that actually earn money. Your instinct
was right; only the label was off.

---

## 15 · WHAT IS LEFT — revised Day 24

**This section originally listed Day 23's plan. Most of it is done.** The live task list lives
in `engine/design/status.md`; this is the summary.

### Done on Day 23

| | |
|---|---|
| **Git repo** | `5bf0c08`, private remote, verified |
| **`swipe.md`** | `RETENTION` + `REWARD` added and made mandatory; THE TOPIC RULE written |
| **Agent-Reach + OpenCLI** | installed, source-audited, **proven live on Instagram** |
| **The creator list** | 32 captured via the Creator Capture artifact |
| **`niche.md`** | PEER/BUYER redefined by state; THE HOOK-END RULE added |
| **`creator-analyst`** | input contract; reads `raw/`, never fetches, never re-selects |
| **`qualify`** | **new skill** — the 32 → watchlist cut, five written gates |

### Done on Day 24

| | |
|---|---|
| **`scout`** | **built** — the last missing piece of Pipeline A. Reads `handles.md`, runs `opencli instagram user <h> -f json`, appends to `metrics.csv` deduped, computes the median and the outlier ratio, writes `pieces.md` carrying every fetched post flagged WINNER or NORMAL, and owns transcription of the winners. Written against the commands in `tooling.md` — observed, not assumed. |
| **`thought-partner`** | **built** — input 6 of Pipeline B. No tools, no scraper, no account. Gate: *no name, no file.* |
| **The folder** | restructured to three roots — `brain/` · `engine/` · `work/`. 86 path references rewritten, zero broken links. |
| **`architecture.md`** | folded into this document and archived. One design file, not two. |
| **`archive/`** | superseded drafts, old backups and downloaded junk moved out of the tree and out of git. |
| **`handles.md`** | **deleted** — the 12 names were picked by hand before `qualify` existed. Archived, not edited. Pipeline A now has no watchlist until `qualify` produces one. |

### Still to do, in order

**1 · Run `qualify` on all 32.** Reads the roster note, the profile screenshot and the link
for each. Produces `qualified.md` — a verdict and a named killing gate per creator. Shubham
overturns rows. **Only then does `handles.md` get rebuilt.**

**2 · Run `scout`, then fetch the winners.** ~2 URLs per creator by hand, then download and
transcribe. **This is where the four untested things get tested** — see the last section of
`tooling.md`.

**3 · One teardown, one creator.** Then promote, and `swipe.md` stops being empty.

**4 · Fix the FORMAT gap.** Below.

### The FORMAT gap — found Day 24, not yet fixed

`brief-builder` assigns `RING · READER · STAGE · SLOT · TRUST LEG · VILLAIN · OFFER`.
**There is no FORMAT field.** Nothing in the engine decides whether a piece is an idea, a piece
of advice, a story, a build, or a breakage — so `script-writer` is told who it is for and what
it is about, but never *what kind of thing it is.*

Fix: a format taxonomy in `brain/reference/frameworks/`, a `FORMAT` field on the Brief, and both writers
reading it. **Not built.**

---

## 16 · WHERE THE RULES COME FROM, AND WHAT IS MISSING

`brain/reference/sources-log.md` lists every source studied and what each one gave. The
operating rules live in `brain/niche.md`, `brain/psychology.md` and `brain/strategy.md` —
**those are the memory.** `brain/reference/transcripts/` is archive, never loaded as context.

**Five rules are ours, invented here, not taken from any source:** the kill rule · the
confidence downgrade · `ledger.md` as a maintained file · the buyer-vs-peer check resolved
into two offers · text first, reel as the multiplier.

### What the engine does not have

Named honestly, because a missing piece nobody names becomes a silent failure.

- **No `outreach` skill.** `niche.md` makes outreach the client channel and content the
  proof layer, with a September start. Nothing in the folder does outreach.
  **This is the most valuable missing skill.**
- **No post counter.** Four decisions are deferred to post 20. `script-doctor` announces it;
  nothing else tracks it.
- **No product.** The peer half of the funnel has nothing to sell until one exists.
- **No FORMAT field.** Section 15.

---

## STATUS

**As of Day 24:** every skill described here is built. Everything else described here exists
in `D:\Claude-cowork\Content-Engine` and is under version control.

**Nothing here has produced a post yet.** `swipe.md`, `voice.md` OBSERVED, `hook-bank.md`,
`corrections.md` and `published.md` are all still empty. The tooling being real does not change
that — only publishing does.

**Ground truth for tools:** `brain/reference/tooling.md`. **Live task list:**
`engine/design/status.md`. Where either disagrees with this document, they win.

**Companion documents from the same session:**

- Ten-Source Teardown — what each of the ten sources gave and what was rejected
  https://claude.ai/code/artifact/cdb1abe4-8c0a-4d4d-ab79-f5da22bd4153
- Engine Workflow v2 — carries the ScrapeGraphAI assessment
  https://claude.ai/code/artifact/25421537-f623-44fc-be2b-5daedab1736d
- This document, as a web page (**current**)
  https://claude.ai/code/artifact/504123bc-16c2-409a-9453-d9425f1f67b8
- Pipeline A, walked step by step
  https://claude.ai/code/artifact/d5a7f5dc-367e-4a82-8a8e-7d16601e1d25
