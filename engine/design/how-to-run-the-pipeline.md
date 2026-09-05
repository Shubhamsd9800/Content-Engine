# how-to-run-the-pipeline.md — the steps, gate by gate

**Built:** Day 29, 5 Sep 2026.
**What this file is:** the OPERATING checklist. Not the design, not the state — the steps.
**Read this before writing or reviewing any post.** Every time. No exceptions.

| File | Answers |
|---|---|
| `README.md` | what this project is |
| `CLAUDE.md` | how to work in this folder, and the rules |
| `engine/design/blueprint.md` | the design — WHY it is shaped this way |
| `engine/design/status.md` | the state — what is true TODAY |
| **`engine/design/how-to-run-the-pipeline.md`** ← this file | **the steps — HOW to run one post** |

**The picture version of this file:**
**https://claude.ai/code/artifact/4746dfe9-6e6e-453f-b177-80cee895d532**
Three layers, both pipelines, the fork, all eighteen gates, every file's state, with diagrams.
**Open it when the shape is unclear. Update it when something changes — never write a second one.**

---
---

# STEP 0 — WHERE ARE WE? Answer from disk, never from memory.

**Run this before anything else.** The answer falls out of what exists on disk.

```
ls work/briefs/          a Brief exists?     → B3 is done
ls work/drafts/          a draft exists?     → B4 is done
grep ENTRIES work/log/published.md           → has anything shipped?
head -20 engine/design/status.md             → what did the last session say?
```

| What you find | Where you are | Go to |
|---|---|---|
| No Brief | before B3 | STEP 1 |
| Brief, no draft | B3 done | STEP 3 |
| Brief and draft, nothing published | B4 done | STEP 5 |
| Published, no log entry | B7 done | STEP 7 |

> **THIS STEP EXISTS BECAUSE IT WAS SKIPPED.** On Day 29 a session read a `status.md` frozen
> at Day 26, concluded Pipeline B had never run, and re-produced a CPIO worksheet that was
> already complete and approved. **A stale status file reads as authoritative.** Check the
> folder, not the summary — including when Shubham is the one summarising.

---
---

# STEP 1 — AN IDEA ARRIVES

Six inputs. Two of them are the ones nobody else can copy.

| # | Input | Skill |
|---|---|---|
| 1 | something trending | `topic-scout` |
| 2 | a resource found | `topic-scout` |
| 3 | a link pasted | — |
| 4 | **your own bug or fix** | — |
| 5 | **something you built** | — |
| 6 | a thought you had | `thought-partner` |

**Inputs 4 and 5 are the moat.** A trend, a resource, a link and even a thought can be had by
anyone. Nobody else has your bugs. Those two are what `ledger.md` stores.

**Candidates land in `work/ideas/queue.md` first.** A line there means *"this exists and it is
in the right neighbourhood."* It is never a decision. **Prune anything older than 14 days** — a
queue nobody prunes becomes a guilt list.

---
---

# STEP 2 — BRIEF-BUILDER · the fork happens here

Run `brief-builder`. It writes `work/briefs/<yyyy-mm-dd>-<slug>.md` and returns a verdict.

**Eight fields, and none of them are the same axis:**

```
RING          1 · 2-3 · 4                    never 5
READER        peer | buyer                   mixed and unknown are ILLEGAL
FUNNEL SLOT   TOFU | MOFU | BOFU             BOFU is switched off
PLATFORM      instagram | linkedin           both is ILLEGAL
BUCKET        built | stuck | moving         bof is ILLEGAL   [LinkedIn]
CTA           none | question | link         none is the DEFAULT
STAGE         found | installed | testing | shipped
STANDING      built-for-self                 delivered-to-client does not exist yet
```

## THE PLATFORM TEST — the only one that matters

```
Is there something to LOOK AT?

value survives sound-off, screen-blank   →   LINKEDIN
the value IS the thing on screen         →   INSTAGRAM
both genuinely fit                       →   INSTAGRAM FIRST,
                                             LinkedIn as a SEPARATE REWRITE
```

**A reel is not a LinkedIn post with video.** A piece that fits both is **two Briefs and two
drafts**, never one Brief routed twice.

## THE FOUR KILLS — a kill is a successful run

| Condition | Verdict |
|---|---|
| `GAPS` empty **and** `YOUR STANDING` empty | **kill** — nothing here is his |
| `RING` would be 5 | **kill** — same hour, zero qualified attention |
| Hits any NOT-list item | **kill** — the list is obeyed, not weighed |
| `READER` cannot be decided | **hold** — a post for both is a post for neither |

**Report a kill as a success.** Never produce a post to be helpful.

---
---

# STEP 3 — THE FORK. Read ONE writing file. Never both.

```
PLATFORM = instagram   →   script-writer     reads brain/playbook.md
PLATFORM = linkedin    →   linkedin-writer   reads brain/linkedin-playbook.md
```

> **THE TWO FILES CONTRADICT EACH OTHER ON PURPOSE.**
> **S02 — THE CORRECTED ASSUMPTION** (*"You probably think X. You'd be wrong."*) is `[C]` tier
> and one of the strongest shapes in `playbook.md`. It is a **BANNED PATTERN** on LinkedIn,
> `linkedin-playbook.md` §5 rule 2. **Both are correct. Never reconcile them.** Reading the
> wrong file imports banned patterns without anyone noticing.

---

## 3A · LINKEDIN — `linkedin-writer` v2

```
GATE 1   IS THE BRIEF RUNNABLE
         PLATFORM linkedin · READER peer or buyer · ONE idea ·
         the four-question test · BUCKET is not bof ·
         nothing needs a client, a case study or a money number
         FAILING THIS GATE IS A SUCCESSFUL RUN. Send it back to brief-builder.

STEP 2   CPIO WORKSHEET — filled IN WRITING, before a single line of prose
         C  CONVEY       one sentence. the exact purpose.
                         "build authority" is NOT a result.
         P  PACKAGE      format · angle · hook posture · which curiosity-gap
                         mechanism · the ARTIFACT proof · media or text alone
         I  INFORMATION  required · exclude · missing · every tool's real stage
                         IF "MISSING" IS NOT "NONE", STOP AND ASK.
         O  ORDER        hook · setup · development · support · ending

GATE 2   SHOW THE WORKSHEET. THEN STOP.
         Do not draft in the same turn. A wrong CONVEY produces a well-written
         post about the wrong thing, and that failure is invisible once prose
         exists. The worksheet is cheap to fix. A draft is not.

STEP 4   DRAFT — one draft plus three hook options. Not three drafts.

GATE 3   THE EDITING CHECKLIST — six groups, then read it ALOUD.
         Then the 24 banned rules, §5. Rules 17-24 are engine rules and
         they outrank everything.
         REPORT IT HONESTLY. "All passed first time" is a red flag, not a result.
```

**The ARTIFACT HOOK, and it is permanent.** The credential hook — *"I've built X for Y
companies over Z years"* — is the genre default and it is **unavailable**. Authority comes from
the build, the breakage, the specific decision, the real number. Never from tenure, headcount
or revenue. **No employer name. No money number. Nothing unshipped presented as proven.**

---

## 3B · INSTAGRAM — `script-writer`

```
STEP 0   THE REFUSALS — refuse format-led content up front.
STEP 1   Four fields decide the reel. READER changes the register.
         STAGE is spoken out loud.
STEP 2   Two production decisions, stated at the top.
STEP 3   THE GATE — the outline must clear the uniqueness gate before
         an intro is written.

THE FIVE STEPS, IN THIS ORDER, ALWAYS
  1 PACKAGING
  2 OUTLINE      ← the uniqueness gate
  3 INTRO        the five-part hook. WRITTEN AFTER THE OUTLINE, never before.
  4 BODY         second-best point FIRST, best second, then descending
  5 OUTRO
```

**Three channels — spoken, on-screen text, visual.** They must say the same thing in different
words. **Hinglish spoken by default; on-screen text English always.** Output is 3 variants ×
3 hooks plus a production block. **Budget 2–3 hours.**

---
---

# STEP 4 — SHUBHAM REWRITES. Never skipped.

**The whole system exists to protect this step.**

> **SAVE THE AI DRAFT TO `work/drafts/` BEFORE HE TOUCHES IT.**
> On Day 28 the AI draft was never saved — only the rewritten version survives. **The rewrite
> diff for post one cannot be computed**, so `corrections.md` and `voice.md` OBSERVED got
> nothing from the strongest evidence source the engine has. **Do not repeat this.**

---
---

# STEP 5 — SCRIPT-DOCTOR · the real gate

**It runs on the REWRITE, never on the AI draft.** 17 checks. It flags; it never rewrites.

```
 1 specific lost          10 pratfall check
 2 specific gained        11 hard rules vs voice.md
 3 reader drift           12 one idea
 4 stage honesty          13 THE GENERIC TEST        ← a STOP, not a flag
 5 built vs delivered     14 triple hook alignment   [reels]
 6 NOT-list               15 LinkedIn banned patterns [LinkedIn]
 7 ring 5 drift           16 CTA matches the Brief
 8 hook integrity         17 mobile shape            [LinkedIn]
 9 claims vs ledger
```

**`ship` is valid and frequent. Do not manufacture flags to look useful.**
**A kill verdict is a successful run.**

---
---

# STEP 6 — PUBLISH

```
LinkedIn   English always · link in the FIRST COMMENT, never the body
Instagram  on-screen text English · Hinglish spoken
```

---
---

# STEP 7 — AFTER PUBLISHING. This is the only loop that closes.

**Do this the same day. Everything upstream is theory until it runs.**

```
1  append to work/log/published.md — including READER and RING
2  report the rolling mix: of the last seven, how many ring 1, 2-3, 4
3  log every real diff into brain/voice.md OBSERVED
4  log any overridden flag into work/log/corrections.md
5  log every hook written into work/log/hook-bank.md — the cut ones too
6  UPDATE engine/design/status.md
```

**Two diffs of the same class is a bug in a skill, not a note for `voice.md`.**
**At ~20 entries `published.md` overrides the brain.** Until then everything upstream is theory
and must be described honestly as theory.

---
---

# THE STANDING RULES — they outrank convenience

```
· ASK before running any skill, agent or scraper. Name what it does first.
· ASK before moving, renaming or deleting anything. Show what changes, wait for a yes.
· LIST THE STEPS before a multi-step task, and wait for a go-ahead.
· NEVER RUN GIT FROM COWORK — read-only commands included. `git status` takes the
  lock too. daily-push from Claude Code or PowerShell only. An existing lock can be
  MOVED out of .git/ into _to_delete/, which the mount permits.
· DELETION IS BLOCKED on the mount. Move to _to_delete/ and say so.
· FOLDER GRANTS DO NOT PERSIST across sessions. Re-request each time.
· READ THE ACTUAL FILES. Never argue from a summary — including a Notion one, and
  including when Shubham is the one summarising.
· NEVER READ brain/reference/transcripts/ unless distilling a source.
· THE BRAND SYSTEM IS OUT OF SCOPE by default, everywhere.
· ONE SESSION PER FOLDER. Two sessions editing status.md at once silently
  overwrote a day's record on Day 29.
· KEEP EXPLANATIONS MEDIUM-LENGTH. State the finding, give the reason, stop.
· PUSH BACK ONCE, properly, with the strongest case available. Then execute his
  call without relitigating it.
```

# WHEN SOMETHING CHANGES

**Update this file and the artifact. Never write a second steps file, and never recreate a file
that was archived.** A stale instruction is worse than a missing one, because it reads as
authoritative.
