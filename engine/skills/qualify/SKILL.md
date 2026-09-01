---
name: qualify
description: QUALIFY. Filters the captured creator roster down to a watchlist, using five written gates instead of taste. Pulls follower data with one free profile call per creator, scores every candidate, and writes work/creators/qualified.md with the verdict and the killing gate for each. Stops there — handles.md is only written after Shubham reviews. Use when the roster changes, when a creator is added, or when the watchlist needs rebuilding.
---

# qualify

**Type: ANALYZE.** It judges. Its only fetch is one profile call per creator, and that returns
follower counts — never a reel, never a caption, never engagement.

**Read — the whole brain cycle, not a subset:**
`work/creators/creator-roster.md` · `brain/niche.md` · `brain/strategy.md` ·
`brain/psychology.md` · **`brain/playbook.md`** *(read §1 SHAPES and §8 DO NOT — what the
engine already has, and what it has already rejected.)*

> **`strategy.md` was missing from this list and it holds two things the gates depend on:**
> the PEER/BUYER definitions by state, and the searchable-vs-shareable axis. Gate 2 cannot be
> run correctly without it. `psychology.md` is read for gate 1 — whether a creator's value is
> in the mechanic or in who they are.
**Write:** `work/creators/qualified.md` — and nothing else.

> **This skill does not write `handles.md` in the same pass.** It produces the table, shows
> it, and stops. Shubham overturns rows. **Then, invoked a second time, it writes
> `handles.md` from the approved survivors** — see PASS 2 at the end. Nothing else in the
> engine may author that file.

---

## WHY THIS EXISTS

On Day 23 a shortlist was produced by reading Shubham's capture notes and forming an opinion.
It was presented as analysis. It had no criteria anyone could check and no way to be argued
with row by row.

**A cut made in Claude's head is not a pipeline step.** This skill is that cut, written down,
so the same input always produces the same output and every verdict carries its reason.

---

## THE TWO SELECTIONS — do not confuse them

| | **QUALIFY** (this skill) | **RANK** (a step inside `scout`, not a skill) |
|---|---|---|
| Question | *Does this creator teach shapes I can use?* | *Which of their posts beat their own normal?* |
| Decided by | **judgement, against written gates** | **arithmetic** |
| Needs reel data | **no** | **yes** |
| Runs | once on the roster, again when a creator is added | every scout run |

Qualify may never ask *"is this content good?"* — that question belongs to the RANK step
inside `scout`, which answers it with a median. **There is no skill called `rank`.**

---

## INPUT

**1. The roster.** `work/creators/creator-roster.md` — every captured creator, with
Shubham's own one-line note on what he gets from them. **His note is the primary evidence for
gates 1, 2 and 4.** Read it carefully; it usually states the audience outright.

**2. One profile call per creator.** Free, ~3 seconds each:

```
opencli instagram profile <handle> -f json
```

Returns `username · name · followers · following · posts · verified · bio`.

**Ask before running the batch.** Name how many calls it will make. If OpenCLI is unavailable,
say so and run on the notes alone — recording `followers: unknown` rather than guessing.

---

## THE FIVE GATES

Run in order. **The first gate a creator fails is the killing gate** — record it and stop
evaluating that creator.

### GATE 1 · FORMAT

> Do they make the kind of thing Shubham will make — **short informational reels**?

**CUTS:** business philosophy · pure entertainment · aesthetic-only accounts · anything where
the format is the content.

Traceable to `swipe.md`: *"Business inspiration is a different list and does not belong here.
Raj Shamani, Nikhil Kamath, Matt Pocock and Alex Hormozi are inspiration for how a business
gets built, not shape references for this account."*

**The test:** if the value is in *who is saying it* rather than *how it is built*, it fails.

### GATE 2 · READER

> Who actually watches them — `peer` · `buyer` · `both` · `neither`?

Both readers are defined in `niche.md` **by state, never by job title**:

> **PEER** — someone trying to build something and stuck. Codes or doesn't; irrelevant.
> **BUYER** — someone with a business problem who wants it gone.

**CUTS `neither`:** job-seeker and careers audiences · fashion · general entertainment.

**Careers content is the trap.** An account about jobs, layoffs and interview prep has an
audience actively looking to be hired — the opposite of an audience that hires. It reads
in-niche because the topic is tech. It is not.

### GATE 3 · SCALE — records, never cuts

> Follower count.

**No threshold. No ceiling. This gate cuts nobody.**

A number here would be arbitrary, and it answers the wrong question. What matters is not how
big the account is but whether a **specific move** works without their authority — and that is
only answerable once the move is visible, which is at teardown.

So follower count is **recorded** here and **used** later, by the `DOWNGRADE` field on every
structure in `swipe.md`. A shape that only works because 500k people already trust them fails
there, individually, with a written reason.

Record the number. Move on.

### GATE 4 · NICHE

> `in-niche` · `adjacent` · `unrelated`

**in-niche** — AI, building, software, shipping products, business-building
**adjacent** — a neighbouring field whose shapes still transfer
**unrelated** — CUTS

Only `unrelated` fails. **Adjacent survives** — an adjacent creator is where a format is
found before it reaches the niche, which is the one genuinely new idea in the tier ladder.

### GATE 5 · COVERAGE — set-level, and it never cuts

Run once, after every creator has a verdict. **It examines the surviving set, not individuals.**

Two axes must both hold:

| Axis | Must contain | What breaks otherwise |
|---|---|---|
| **READER** | peer **and** buyer | All-peer means the engine only learns shapes for people who build it themselves. The service half of the funnel has nothing to imitate. |
| **REACH** | Indian **and** international | All-Indian teaches a ceiling he did not choose. All-international teaches shapes that miss his actual market. |

Traceable to `swipe.md`: *"it must teach shapes for both readers."*

**When an axis is thin, coverage PROMOTES A CREATOR BACK IN** from those cut at gate 3 or 4 —
never from those cut at gates 1 or 2, which are hard. Record the promotion and why.

**Coverage never removes anybody.**

---

## OUTPUT — `work/creators/qualified.md`

Every creator on the roster gets a row. No creator is omitted, including obvious cuts.

```
| # | handle | followers | G1 format | G2 reader | G3 scale | G4 niche | VERDICT | killed by | why |
```

- `VERDICT` — `KEEP` · `CUT` · `RESERVE`
- `RESERVE` — passed every gate but is covered by a stronger creator in the same column.
  **Not a rejection.** Coverage promotes from here.
- `why` — one line, and it must be checkable. *"Business philosophy — value is in who he is"*
  is checkable. *"Not a great fit"* is not.

Below the table, three short sections:

**COVERAGE CHECK** — the reader and reach counts across survivors, and any promotion made.
**THE SURVIVORS** — the proposed watchlist, grouped by what each one is there to teach.
**NOT ON THE LIST** — grouped by killing gate, so a cut can be argued with as a group.

Then stop, show it, and say plainly:

> Nothing has been written to `handles.md`. Overturn any row and I'll rebuild the list.

---

## PASS 2 — writing `handles.md`, and only after approval

**Runs only when Shubham says the table is right.** Before Day 24 this file had no author:
`scout` said `qualify` wrote it, `qualify` said it never did, and "never by hand" closed the
last door. It is authored here.

**Input:** `qualified.md` plus his overturns. **Output:** `work/creators/handles.md`.

1. Take every `KEEP`, apply his overturns verbatim — an overturn is a decision, not a
   suggestion, and it is never re-argued.
2. Re-run **GATE 5 - COVERAGE** on the final set. Both axes must hold. Promote from `RESERVE`
   if one is thin, and record the promotion and why.
3. Target **10-12**. Fewer than 10, say which axis is short rather than padding. More than
   12, say which are marginal and let him cut.
4. Write the file: the grouped list, a machine-readable block of one handle per line, and a
   `NOT ON THIS LIST, ON PURPOSE` section grouped by killing gate.
5. Head it with the date and **`Derived from: qualified.md, approved <date>`** — so a future
   session can tell a derived list from a hand-picked one. **The Day 23 file could not, and
   that is why it was archived rather than edited.**

---

## RULES

1. **Never write `handles.md` in pass 1.** Show the table, wait for Shubham. Writing it is
   pass 2 and requires his approval first.
2. **Never cut on follower count.** Gate 3 records only.
3. **Never judge whether content is good.** That belongs to the RANK step inside `scout`,
   and it uses a median.
4. **Never open a reel, a caption or an engagement number.** Wrong step.
5. **Every creator gets a row**, including the obvious cuts. A missing row looks like an
   oversight three weeks later.
6. **Every verdict names its killing gate** and gives a checkable reason.
7. **Coverage promotes, never cuts** — and only from gate 3 or 4 casualties.
8. **Adjacent survives.** Only `unrelated` fails gate 4.
9. **Ask before the profile batch.** Say how many calls.
10. **If a creator's note is too thin to judge**, mark the gate `unknown` and say so rather
    than inferring. An honest gap beats a confident guess.
