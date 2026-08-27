# THE ENGINE BLUEPRINT

**Content Engine — complete documentation**
Written Day 22 · 26 August 2026

The whole system in one place — two pipelines, three layers, nine files, nine skills,
seven gates, and the honest list of what is blocking it. Written to be learned in an
hour, not followed as a checklist.

> 2 pipelines · 9 skills · 7 gates · 2 new to build · 4 blockers · **0 posts published**

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
  creators ──▶ creator-scout ──▶ creator-analyst ──▶ swipe.md
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

### ROUND 3 — creator-scout
One creator at a time. This is where the tools do real work.

**a.** List their last 30 pieces with **view count and like count** attached.

**b.** Compute **that creator's own median views** — theirs, not an industry figure. This
controls for audience size, algorithm and topic at once, which is exactly what makes
comparing two different creators meaningless and comparing a creator to themselves
meaningful.

**c.** Flag two kinds of signal, because they are not the same thing.
**Reach outliers** — 2× the median views or more.
**Resonance outliers** — normal views but an unusually high like-to-view ratio.
The first travelled. The second landed. A piece that did both is the most valuable thing
on the list.

**d.** Tag each flagged piece *peer-facing* or *buyer-facing* by its subject. This is the
one place topic is allowed to matter — and only to guarantee coverage, never to be copied.

**e.** Pull full transcripts for the flagged pieces only, **plus two ordinary pieces as a
control.** Without the control there is nothing to compare the winners against, and every
finding becomes a guess.

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

## 06 · THE TOOLS LAYER

Skills describe procedure. Something still has to fetch a page. That something is a
separate layer underneath, and keeping it separate is what makes it replaceable.

**Agent-Reach is a toolbox, not a step.** It doesn't wrap anything — reading is done by
calling upstream tools directly, with no wrapper in between.

It does three things: installs the right tool per platform, writes a skill file saying which
tool to use for what, and keeps that routing current when a platform breaks a backend. Each
platform has an ordered list — preferred, then fallbacks — and `agent-reach doctor` reports
which one is live.

**Why that separation matters:** Agent-Reach never knows what a creator is or what a median
view count means. `creator-scout` never knows how to install a downloader. Neither can break
the other, and swapping the whole toolbox out later touches no skill.

| What's needed | Tool | Login? | Used by |
|---|---|---|---|
| A creator's videos, views, likes, transcripts | yt-dlp | **No** | creator-scout |
| Any web page as clean text | Jina Reader | No | topic-scout, outreach |
| Semantic search across the web | Exa | No | topic-scout |
| Repos, releases, issues | gh CLI | No, for public | topic-scout |
| Feeds you follow | feedparser | No | topic-scout |
| Instagram profile and recent posts | OpenCLI, browser session | **Yes — burner only** | creator-scout, exception path |

**Five of six rows need no account.** Because the creators worth studying publish on
YouTube as well, most of Pipeline A runs through the free, no-login, no-risk door. Instagram
becomes the careful exception for the few who are only there — not the road everything
travels.

**Note who is absent from the last column:** `creator-analyst`, both writers,
`script-doctor`, `thought-partner`. None of them ever touch a tool. That is law one being
useful rather than decorative.

**Burner rule:** never the brand account, and never in the same browser profile as it —
same profile means same fingerprint, and a flagged burner drags the real one with it.

---

## 07 · EVERY FILE — WHAT FILLS IT, AND FROM WHERE

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

## 08 · THE GATES — SEVEN CHECKS

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

## 09 · TWO LAWS THAT STOP IT ROTTING

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

## 10 · BLOCKERS AND BUGS

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

### Blocker 2 — no git repo, seventh day

Every file in `Content-Engine` exists in exactly one place. On Day 21, fourteen files were
rewritten in place over originals with no backup — the only rollback that existed was chat
history. Nothing was lost. That was luck, not design.

Tomorrow's plan writes new skills and edits four existing files. **This is the session where
it finally bites.** Fifteen minutes in PowerShell, before anything else.

### Bug 3 — selecting by topic contradicts the topic rule

You asked to pick a creator's "most business-purpose videos, based on my niche."
`swipe.md`'s founding law says topics are theirs, shapes are yours. Selecting *by* topic is
how a study quietly turns into topic-borrowing.

**Resolvable, and the resolution is a rule worth writing down:** topic may decide *which
pieces get read*, so that both readers are covered. Topic may never leave the teardown.
Select by subject, extract only shape. Without that line stated explicitly, the drift
happens by accident.

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

## 11 · TOMORROW, IN ORDER

Nothing here waits on a decision that hasn't been made.

**0 · Git repo on Content-Engine.**
PowerShell, not Cowork. Before any file is touched.
*15 minutes. Seventh day on this.*

**1 · Two fields into `swipe.md`.**
`RETENTION` and `REWARD`, plus the select-by-topic-extract-only-shape rule from bug 3.
*10 minutes. Must land before the first teardown.*

**2 · Build `thought-partner`.**
Four drivers, one question at a time, ends at a named concept. No tools, no scraper, no
account.
*The only path to a published post this week — which unblocks four of the five empty files.*

**3 · Install Agent-Reach — YouTube and web channels only.**
Leave Instagram unconfigured until the burner is separated from the brand account's browser
profile.
*Minutes. Free, no keys.*

**4 · Your creator list.**
Links plus one line each on what you get from them. Round 1 sorting happens together.
*Your hour.*

**5 · Build `creator-scout`, run it on one creator.**
Written against tools observed working, not assumed. Then one full teardown, one shape
promoted, and `swipe.md` stops being empty.

---

## STATUS

`creator-scout` and `thought-partner` are proposals, not built. Everything else described
here exists in `D:\Claude-cowork\Content-Engine` today.

**Companion documents from the same session:**

- Ten-Source Teardown — what each of the ten sources gave and what was rejected
  https://claude.ai/code/artifact/cdb1abe4-8c0a-4d4d-ab79-f5da22bd4153
- Engine Workflow v2 — carries the ScrapeGraphAI assessment
  https://claude.ai/code/artifact/25421537-f623-44fc-be2b-5daedab1736d
- This document, as a web page
  https://claude.ai/code/artifact/e8dd48a8-48c4-4ee8-95ca-a2561a5b5078
