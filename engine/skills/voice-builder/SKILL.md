---
name: voice-builder
description: >
  Builds Shubham's voice foundation for the Content Engine: brain/about-me.md (who is
  talking) and brain/voice.md (how it sounds). Runs a gap-driven interview against what
  the engine already decided, then derives absence signals from real samples of his own
  writing. Use this whenever the voice layer needs building, rebuilding or extending -
  trigger on "build my voice", "run voice-builder", "voice.md is thin", "about-me.md",
  "how should I sound", "the drafts do not sound like me", or at the start of any session
  where a writer skill is about to run and voice.md has no DERIVED section yet. Also
  trigger when a new batch of Shubham's own writing arrives and the absence signals should
  be recomputed. Do not use this to write a post - that is linkedin-writer or script-writer.
---

# Voice Builder

Builds two files: `brain/about-me.md` and `brain/voice.md`.

They answer different questions, and keeping them apart is the whole point:

| File | Question | Changes |
|---|---|---|
| `about-me.md` | **Who is talking** - role, audience, pillars, point of view, promise, off-limits | Rarely |
| `voice.md` | **How it sounds** - sentence mechanics, rhythm, what the voice never does | Slowly, from real rewrites |

A third file already answers the remaining question and this skill never touches it:
`brain/playbook.md` holds **what shape a piece takes**, borrowed deliberately from 15 torn-down
creators. That borrowing is legitimate. Borrowing *voice* is not - see Step 3.

---

## Step 0. Read before asking

Read these first, every run:

- `brain/niche.md` - the niche, the rings, the two audiences
- `CLAUDE.md` - THE DECISIONS section
- `brain/strategy.md`
- `brain/voice.md` if it exists - to know what is already decided
- `brain/about-me.md` if it exists - this may be a re-run, not a first build

The engine's own rule is *check the folder before asking twice*. Roughly half of a generic
voice interview is already answered on disk: role, audience, topic pillars, the ring
structure. Asking again wastes the session and signals that the files were not read.

After reading, state in one short paragraph what is already answered and what is genuinely
missing. Then interview only the gaps. If a file contradicts another, say so rather than
picking one silently.

---

## Step 1. The interview - in chat, one question at a time

Ask in chat. Do not use `AskUserQuestion`. The form was tried on Day 27 and stopped twice:
it renders four questions at once with no room for the reasoning behind them, and the first
response to a form question was "I am not getting the question." A question whose purpose is
invisible gets a wrong answer or no answer, and both are worse than a slower interview.

**One question per message.** Each carries four things:

1. **The question as a complete plain sentence.** Not a label. *"Your point of view"* is a
   label. *"What do you believe about building software that other people would argue with?"*
   is a question.
2. **What the files already say, and what is missing.** One or two lines. This proves the
   folder was read and narrows what is actually being asked.
3. **Four options, lettered, one line each.**
4. **A recommendation with its reason, and why the others lose.** Two to four sentences.

Then stop and wait for a raw answer.

**Calibration, learned the hard way.** Long reasoning was rejected as "too much extra
content". A bare question with four options was rejected as too thin. The working length is
roughly what is described above - a short paragraph of reasoning, not an essay and not one
line.

**When an answer does not come back:**

- *He says he does not understand the question.* Do not re-offer the options. Explain the
  question itself with a plain everyday example - facts have no other side, opinions do -
  then re-ask it unchanged.
- *He reaches for the same option twice after being argued out of it.* That is the real
  answer. Find out why he keeps returning to it rather than repeating the argument.
- *Two answers could be combined.* Allow it only when they form **one claim with a cause and
  an effect**. Two beliefs stapled together means every future piece has to defend both.

**Never change the criteria between recommendations without saying so.** Recommending one
option on *"which serves the reader"* and then a different one on *"which has evidence"* is a
flip-flop, and it costs more trust than a wrong recommendation held consistently.

**Show progress.** Number the questions - *"Q2 of 5"* - and after each answer restate what was
locked in one line before moving on. An interview with no visible end is why people stop
answering.

---

## Step 2. Write about-me.md

```
# About Me

## Name and role
## Audience
## Topic pillars
## Point of view
## Brand promise
## Off limits
```

Fill from the interview plus what Step 0 found on disk. Every line has to be something a
writer skill would actually reference mid-draft - if a line would never change a sentence in
a post, it is padding and should be cut.

Do not impose a word limit. Short because there is nothing more to say is good; short because
a cap forced it is not.

The `Off limits` section carries the engine NOT-list explicitly: Capgemini, client specifics,
and any claim of multi-agent systems or delivered client work that has not shipped.

---

## Step 3. Get real samples

Ask for 3 to 5 pieces of writing. Then hold this line, because it is the thing most likely
to go wrong:

**A sample must be text Shubham himself wrote, for another human to read.**

**Never accept as a sample:**

- **Anything generated inside this engine.** The teardowns, `playbook.md`, the Notion logs,
  the status files - all of it is Claude's prose. Feeding it back produces a `voice.md` that
  describes Claude, and then every future draft gets graded against Claude's own fingerprint.
  It is a closed loop that looks like it is working while it quietly makes the engine worse.
- **Another creator's writing, however much he admires it.** This is where the source skill
  this was forked from gets it wrong. It permits "someone whose voice you admire" and still
  calls the output a voice profile. Structure is borrowable and lives in `playbook.md`.
  Sentences are not. If Kallaway's phrasing lands in `voice.md`, in six months every post
  sounds like Kallaway and anyone who watches him will feel it.

**Acceptable sources, in order of quality:**

1. Published or sent long-form writing of his own - posts, READMEs, docs, essays, long
   explanations written to a real person.
2. His messages in Cowork and Claude sessions. Real and unedited. Note the caveat in the
   analysis: much of it is voice-to-text, so sentence-length and punctuation signals are
   unreliable, while tone, directness, how he pushes back and what he never says read clearly.
3. Nothing. If fewer than 3 acceptable samples exist, say so plainly, write `about-me.md`,
   and leave the DERIVED section of `voice.md` marked empty with the reason. An honest gap
   beats a filled section built from the wrong evidence.

State which source is being used and why, before analysing anything.

---

## Step 4. Analyse - five signal families

Look for patterns across *all* samples. A quirk in one piece is a quirk; the same move in
four pieces is a voice.

**Voice signals** - average sentence length, paragraph rhythm (staccato vs flowing), opening
style (contrarian, question, data point, story, confession, observation), point of view,
tone (deadpan, warm, blunt, playful, clinical), recurring phrases, closing style.

**Structural signals** - length range, lists vs prose, how pieces open, close and transition.

**Topic signals** - subjects recurring across samples, who the reader appears to be, what the
author is consistently standing for.

**Absence signals** - the most valuable family, and the reason this skill is worth running.
Words and punctuation absent from every sample. Hook types never used. Tones never hit.
Structures avoided. Report these as counts, not impressions: *"no rhetorical questions in
0 of 5"* is checkable; *"rarely uses questions"* is not.

**Rewrite diffs** - what he changed between a draft and what he actually published. This is
the only family that cannot be produced by analysis or interview, because it is a difference,
not an answer. It is empty until a post ships and fills at B6 via `script-doctor`. Note it as
empty rather than skipping it, so the file shows its own missing half.

If samples contradict each other, record the contradiction. Do not average it into something
smooth - the engine treats an unresolved conflict as information and a smoothed one as a lie.

---

## Step 5. Write voice.md

Three sections, in this order, and the separation is load-bearing. It marks how much each
line is actually worth, the same way `playbook.md` grades entries [C] / [S] / [X].

```
# voice.md - how Shubham sounds

## DECIDED
Carried forward. Evidence-backed. An interview cannot re-derive these and must not overwrite
them.

  - THE LANGUAGE LOCK - Hinglish spoken, English on-screen text always, तुम register,
    switch mid-clause on the word that matters. Locked Day 26 from teardown evidence
    (pure Hindi 17.19x inside a developer audience only; Hinglish 13.82x reaching past them).
    Chosen against the larger number, for a stated reason.
  - THE ANGLE RULE - open on the story, land on the reader. The five things that count as
    an angle. Corrected Day 26.
  - THE TWO-READER REGISTER TABLE - PEER vs BUYER across jargon, unit, proof and close.
    Without it "one post, one reader" is unenforceable.

## DERIVED
NEW this run. From the interview and the sample analysis. Lower confidence than DECIDED -
these are patterns observed once, not decisions tested against data.

  ### Who I sound like
  ### Tone                 [attributes hit, plus tones never hit]
  ### Sentence rhythm      [with avoidance patterns]
  ### Hook patterns        [observed, with an example each, plus hook types absent]
  ### How I open
  ### How I close
  ### Signature phrases
  ### What this voice never does   [each item backed by an absence count]

## OBSERVED
Empty until post 1. Fills only from real rewrite diffs, logged by script-doctor into
work/log/corrections.md. Two diffs of the same class is a bug in a skill, not a note here.
```

Every DERIVED line names its evidence. A line with no source is an opinion, and the engine
deletes opinions.

No word cap. Nothing invented. If a section has no evidence behind it, write that it has no
evidence rather than filling it - a visible blank is what makes the file honest, and it is
also what tells the next session where to look.

---

## Step 6. Show it, then ask before saving

Nothing is written to `brain/` until Shubham says yes. Show both files in full. If an existing
`voice.md` is being replaced, show exactly what is being replaced and where the old copy is
going before moving it. Moving is treated the same as deleting here.

Then hand off:

> `about-me.md` and `voice.md` are in `brain/`. `brief-builder` reads both when it assigns
> READER and STAGE. `linkedin-writer` and `script-writer` read `voice.md` before drafting.
> The OBSERVED section is still empty and stays empty until a post ships - that is expected,
> not a gap to fill now.

---

## Rules

- Read the folder before asking. A question whose answer is on disk costs trust in the whole
  interview.
- Work from evidence. Never invent a pattern to complete a section.
- Structure is borrowable, voice is not. `playbook.md` holds borrowed structure on purpose.
- Nothing Claude wrote inside the engine is a sample.
- Record contradictions rather than smoothing them.
- Minimum 3 acceptable samples before the DERIVED section is written. Fewer means the section
  is marked empty with the reason, not filled with guesses.
- Never overwrite DECIDED content from an interview answer. If an answer genuinely conflicts
  with a locked decision, surface the conflict and let Shubham choose.
- Ask before saving, and before moving anything that already exists.
