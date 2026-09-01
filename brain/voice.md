# voice.md — how Shubham sounds

**v0.2** — rebuilt 1 Sep 2026 (Day 27) by `voice-builder`. Replaces v0.1.

Three sections, and the separation is the point: it marks how much each line is actually
worth, the same way `playbook.md` grades entries **[C] / [S] / [X]**.

| Section | What it is | Confidence |
|---|---|---|
| **DECIDED** | carried from v0.1 — teardown evidence or a stated decision | high — an interview must never overwrite it |
| **DERIVED** | from interview and sample analysis | lower — patterns seen once |
| **OBSERVED** | from real rewrite diffs | highest — and empty until post 1 |

`about-me.md` answers **who is talking**. This file answers **how it sounds**.
`playbook.md` answers **what shape a piece takes** — that one is borrowed from 15 creators
on purpose. Voice is not borrowable. If a studied creator's phrasing lands in this file,
in six months every post sounds like them.

---

# DECIDED

## The language rule — MERGED Day 27

**v0.1 and `CLAUDE.md` disagreed, and both were live.** v0.1 read as a default with one
exception. `CLAUDE.md` read as a three-condition test decided per piece. A technical claim to
an Indian peer audience got opposite answers from the two files. Resolved by merge, not by
picking a winner.

> **DEFAULT: Hinglish spoken. On-screen text English, always. LinkedIn English, always.**

**The named exceptions that override the default:**

| The piece is | Spoken |
|---|---|
| buyer-facing | **English** |
| aimed outside India | **English** |
| a technical claim | **English** |
| India-facing · peer · story · rant | **Hinglish** — the default |

A default means no decision most of the time. The exceptions are a short named list, not a
fresh judgment on every script.

**Why Hinglish and not pure Hindi — Day 26 teardown evidence.** `developer_mannjadwani` runs
pure Hindi in Devanagari at **17.19×**, inside a developer audience only.
`theautomationguy.ai` runs Hinglish at **13.82×**, reaching far past developers — which is
where the buyer half of the audience lives. **Pure Hindi wins harder in a narrower room.**
Chosen against the larger number, deliberately.

**What Hinglish means mechanically** — from `theautomationguy.ai` and `_roshnichellani`:

- English technical and cultural nouns **stay English, untranslated**. Never *अभिकलन*, always
  *deployment*. Never *जालक्रम*, always *pipeline*.
- Hindi carries the **sentence structure and the emotional beats**. English carries the
  **technical spine**.
- **The switch is the emphasis.** Do not pause to switch languages — switch mid-clause, on
  the word that matters.
- Second person **तुम**, not आप. Friend register, not teacher register.
- **On-screen text stays English** — it is what a non-Hindi viewer and the search index read.

**The warm-up applies.** Before writing any Hinglish script, hold a few turns of casual
Hinglish first. Warm-up language sets the register; skip it and the script reads like a
translation.

## Hard rules

**Banned openings** — "In today's world…" · "Since the beginning of time…" · "Here's the
thing" · "Let that sink in" · "the truth is" · "Here's why everyone is wrong about X" · any
manufactured vulnerability · any post opening with credentials instead of a problem.

**Banned words** — game-changer · leverage (verb) · unlock · delve · seamless · robust ·
revolutionize · 10x · fake round numbers.

**Banned moves** — emoji bullets · 👇 arrows · single-word paragraphs used as drama ·
claiming a service line he cannot deliver this month · **implying a client delivered when
every ledger entry is built-for-self** · borrowing a big account's confidence level · any
sentence that could appear unchanged in ten thousand other developers' posts.

## Starting position

| | |
|---|---|
| **Sentence length** | Short. Break a long thought into two sentences rather than joining with commas. |
| **Openings** | The problem or the cost. Never context or setup. **Broad framing — pain or desire.** Never open at the practitioner's level of awareness. |
| **Failure language** | "This broke." Not "we encountered an issue." Direct, unhedged, no self-blame drama. |
| **Numbers** | Real and specific, or absent. "About two days" beats a fabricated "16 hours." |
| **Humour** | Dry, occasional, never the point of the sentence. |
| **Stage honesty** | Every tool named carries its real stage. *"I installed it, haven't run it yet"* is a stronger sentence than a fake recommendation, and it is the only one he can defend. |

## Technical level — set by the reader, not by default

The engine serves **two readers** and they need different registers. `READER` on the Brief
decides which. **Never blend them inside a piece.**

| | **PEER** — trying to build something, stuck | **BUYER** — a business problem, no technical person |
|---|---|---|
| **Assume** | real tools, real versions, real file paths | nothing. They have never heard of an MCP |
| **Jargon** | used freely, unexplained | only if named the way a beginner would Google it, then explained in one clause |
| **The unit** | the mechanism — *why* it broke | the consequence — what it cost, in time or money |
| **Proof** | the diff, the log, the benchmark | the before and after, in plain outcomes |
| **Close** | what to try, or what to stop doing | what this means for the thing they are trying to get built |

**Explaining basics is not beneath this account.** Ring 2–3 is explicitly *"the basics nobody
is teaching, for people who do not know the tools exist"* — the gap he named and chose to
fill. Writing over their heads is the failure mode, not the standard. **This is now also the
point of view**, recorded in `about-me.md`: teaching aimed above people's heads is the thing
this account exists to correct.

**The check that catches drift:** name the reader out loud before the first line, and again
at the close. If the opening speaks to a founder and the close speaks to an engineer, the
piece has two readers and belongs in two drafts.

## The angle rule

> **The angle does not have to be his. It has to be the reader's problem.**

**CORRECTED Day 26.** An earlier reading made *"the stage you are standing on"* sound like
the only permitted angle. It is one of several.

**What fails:** *"Sharan failed for two years and it's inspiring."* — a repost with a caption.
It fails for having **no takeaway at all**, not for missing one particular device.

**What passes — any ONE of these is enough:**

- a decision the reader also faces
- a belief the story corrects
- a mechanism they can reuse
- a real cost, named — *"two years, no salary"*
- a stage they recognise — **one option, not the rule**

**The hook is NOT the angle. Do not open on the reader.** `_roshnichellani`'s best post opens
on *"you can store 1 million GB in 1 gram of DNA"* — an impossible fact. The reader arrives at
the **close**. **Open on the story. Land on the reader.** Opening on the reader is a lecture,
and lectures do not get watched.

**Keep it short.** The angle is a sentence, not a framework. If it needs explaining, it is not
an angle.

Full version in `brain/playbook.md` → **§1 S07**.

---

# DERIVED

**EMPTY — skipped deliberately on Day 27, with the reason recorded.**

This section fills from **sample analysis**: reading 3–5 pieces of Shubham's own writing and
extracting what repeats across all of them. Four families —

1. **Voice signals** — average sentence length, rhythm, opening style, tone, closing style.
2. **Structural signals** — length range, prose vs lists, how pieces open, close and transition.
3. **Topic signals** — subjects that recur, who the reader appears to be, what is consistently defended.
4. **Absence signals** — words, punctuation and moves that appear in **zero** samples, reported
   as counts. *"No rhetorical questions in 0 of 5"* is checkable; *"rarely uses questions"* is not.
   This is the family worth having: the HARD RULES above are things he **decided** to avoid,
   while absence signals are things he avoids **without knowing he does**. Nobody can report
   their own; they only appear in counting.

**Why it is empty and not filled with guesses.**

Zero posts exist. The only long-form writing in this project was written by Claude — the
teardowns, `playbook.md`, the Notion logs, this file. Feeding those back would produce a
voice profile describing **Claude**, and every future draft would then be graded against
Claude's own fingerprint: a closed loop that looks like it is working while quietly making
the engine worse.

The 15 creator transcripts were also considered and **rejected**. Their structure is already
extracted into `playbook.md`, which is the legitimate borrowing. Their sentences are not
borrowable.

**What fills it, and when.** The first LinkedIn draft Shubham rewrites. That produces family
5 below, which is stronger evidence than families 1–4 anyway, because it is him writing **to
an audience** rather than typing in a chat. Days away, not months.

---

# OBSERVED

**Empty until post 1.**

**Family 5 — rewrite diffs.** What Shubham changed between the draft and what he actually
published. This cannot be produced by analysis or interview, because it is a **difference,
not an answer**.

`script-doctor` records each diff. `work/log/corrections.md` classifies them.
**Two diffs of the same class is a bug in a skill, not a note for this file.**

Nothing below this line is written by Claude.
