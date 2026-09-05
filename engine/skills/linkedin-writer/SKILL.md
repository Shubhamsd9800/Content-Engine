---
name: linkedin-writer
description: WRITE a LinkedIn post using the CPIO framework. Runs Convey, Package, Information and Order as a written worksheet BEFORE drafting, then drafts, then runs the editing checklist. Use when a Brief has PLATFORM linkedin, or when Shubham says "write a LinkedIn post", "draft this for LinkedIn", "run CPIO", "LinkedIn draft", "post this on LinkedIn". READER and VOICE are inputs, never hardcoded, so this also writes for a client. Never use for Instagram — that is script-writer.
---

# linkedin-writer

**v2 · rebuilt Day 28.** v1 is archived at `_to_delete/day28-linkedin-writer-v1/SKILL.md`.
It wrote from `playbook.md` §5, which was five findings extracted from Instagram captions.
This version writes from a LinkedIn practitioner's own system.

---

# STEP 0 — LOAD

**Read these before anything else. In this order. Do not skip and do not summarise from memory.**

```
1  brain/linkedin-playbook.md    THE writing file. Everything below is a runner for it.
2  the Brief                     work/briefs/<id>.md
3  VOICE                         see the VOICE input below
4  brain/about-me.md             who is talking
```

**Optional, only when a specific line is in dispute:**
`brain/reference/frameworks/hat-tip-linkedin.md` — the raw source. Go there to check what the
framework actually said. Do not read it routinely.

**Never read `brain/playbook.md`.** That is the Instagram file. The two contradict each other
on purpose. Reading it here will import banned patterns — S02 THE CORRECTED ASSUMPTION is
`[C]` tier there and a **banned pattern** on LinkedIn.

---

# THE TWO INPUTS THAT ARE NEVER HARDCODED

This skill writes for whoever it is pointed at. Two fields decide that, and they are read at
run time — never baked in.

| Input | Default | What it changes |
|---|---|---|
| **READER** | from the Brief | vocabulary · what is assumed · what the close asks for |
| **VOICE** | `brain/voice.md` | how it sounds. Sentence length, register, what this person would never say |

**Writing for a client:** point `VOICE` at that client's voice file and set `READER` from their
Brief. **Nothing else in this skill changes.** That is the whole reason it is built this way —
it serves Shubham's account today and a ghostwriting client later, with no rewrite.

**Rule:** if `VOICE` is not supplied and `brain/voice.md` has no DERIVED section yet, say so in
the output. Do not silently write in a generic register and call it a voice match.

---

# STEP 1 — GATE 1 · IS THIS BRIEF RUNNABLE

**Check before any work. If it fails, stop and send it back to `brief-builder`. Do not
improvise around a thin Brief.**

```
☐ PLATFORM is linkedin.        "both" is illegal — that is two Briefs.
☐ READER is peer OR buyer.     "mixed" and "unknown" are illegal. A post for both is a
                               post for neither.
☐ There is ONE idea.           Three ideas is three Briefs.
☐ The idea passes the four-question test (playbook §1):
      · Does the reader already care about this?
      · Is there something useful and SPECIFIC to say?
      · Can it be supported with a real example, result, process or opinion?
      · Will it help the reader decide something or get a result?
☐ The BUCKET is BUILT, STUCK or MOVING (playbook §1). BOF is switched off.
☐ Nothing in it requires a client, a case study, or a money number.
```

**Failing this gate is a successful run.** Say which check failed and what the Brief needs.

---

# STEP 2 — CPIO · fill the worksheet IN WRITING

**This is the core of the skill. Complete all four in order. Do not draft a single line until
every field is filled.**

The playbook §2 holds the full method — the hook mechanisms, the package table, the accuracy
rules, the ARTIFACT HOOK substitution. **Read it there. Do not work from memory of it.**

```
── CPIO WORKSHEET ──────────────────────────────────────────

C · CONVEY
   Convey:        [ONE sentence. The exact purpose of this post.]
   Type:          story | opinion | framework | process
   Result:        [a literal result. "build authority" is not an answer.]

P · PACKAGE
   Package:       [from the playbook §2 table]
   Angle:         [how the idea is presented]
   Hook posture:  [what the hook leads with · what stays unresolved]
   Mechanism:     [which of the 3 curiosity-gap mechanisms]
   Proof source:  [ARTIFACT HOOK — the build, breakage, decision or real number
                   carrying the authority. NEVER a credential.]
   Media:         [what, or "text alone"]

I · INFORMATION
   Required:      [facts, stories, examples, context this post needs]
   Exclude:       [related material that would weaken the focus]
   Missing:       [what is needed to write this accurately — "None" when complete]
   Tool stages:   [every tool named + its real stage: found/installed/testing/shipped]

O · ORDER
   Hook:          [what the opening must establish]
   Setup:         [what context comes next]
   Development:   [how the idea develops]
   Support:       [where evidence and examples sit]
   Ending:        [how it finishes. No CTA unless the Brief calls for one.]
────────────────────────────────────────────────────────────
```

**If `Missing` is not "None", stop.** Ask for what is missing. **Never guess a number, a date,
a timeframe or a result to complete the worksheet.**

---

# STEP 3 — GATE 2 · SHOW THE WORKSHEET, THEN STOP

**Output the completed worksheet and wait.** Do not draft in the same turn.

This gate exists because the worksheet is cheap to fix and a draft is not. A wrong CONVEY
produces a well-written post about the wrong thing, and that failure is invisible once prose
exists.

**Three self-checks before showing it:**

```
☐ CONVEY is one sentence and every planned beat serves it
☐ The proof source is an ARTIFACT, not a credential
☐ Nothing planned requires a claim the ledger cannot back
```

---

# STEP 4 — DRAFT

Now write. Follow the ORDER block. Playbook §3 holds the drafting rules in full.

**The seven components, and where each is decided:**

| Component | Decided by |
|---|---|
| **PURPOSE** | CONVEY. One sentence, already written. |
| **READER** | the Brief. Never re-decided here. |
| **HOOK** | PACKAGE — mechanism + artifact proof. It makes a promise the body pays off. |
| **BODY** | INFORMATION + ORDER. Every sentence earns its place. |
| **PROOF** | the artifact, at its real stage. Built, never delivered. |
| **CTA** | the Brief. **No CTA is valid and common.** |
| **VOICE** | the VOICE input. |

**The rules that most often get broken, restated because they are worth the repetition:**

```
· ENGLISH. Always. No Hinglish on LinkedIn.
· Line breaks separate IDEAS AND ARGUMENTS — not individual lines.
· No block longer than about four lines on a phone.
· Write how you speak. If you would not say it aloud, do not write it.
· Length is set by the idea, never by a character target.
· No em dashes. No rhetorical questions. No "Most people…".
· Never state a common belief and then dramatically correct it. That is banned here.
· Every tool named carries its real stage.
· Nothing implies a client delivery. BUILT, NOT DELIVERED.
```

## How many drafts

```
DEFAULT     ONE draft, plus 3 hook options for it.
            CPIO already made the decisions three variants used to explore.
            Three full drafts from one worksheet is three ways of saying the same thing.

THREE       Only when the Brief says the angle is genuinely uncertain.
            Then each variant needs its OWN CPIO worksheet, because a different angle
            is a different CONVEY.
```

---

# STEP 5 — GATE 3 · THE EDITING CHECKLIST

**Run the full checklist from playbook §4. All six groups. No skipping.**

```
Point and Payoff · Context and Usefulness · Hook and Package
Clarity and Flow · Accuracy and Proof · Voice and Pride
```

Then **read it aloud.** Stumble → revise. Sounds like something this person would never say →
revise. A claim that cannot be proved → remove it or find the proof.

**Report the checklist honestly.** Name every check that did not pass and what was changed. A
checklist reported as all-clear without a single revision is a checklist that was not run.

**Then check the banned list — playbook §5, all 24 rules.** Rules 17–24 are engine rules and
they outrank everything.

---

# STEP 6 — OUTPUT

```
FROM BRIEF   <brief-id>
READER       peer | buyer
BUCKET       BUILT | STUCK | MOVING
PACKAGE      <format>  — because <one line>
MEDIA        <what, or text alone>
VOICE        <which voice file>

── CPIO WORKSHEET ──
<the completed worksheet from Step 2>

── HOOK OPTIONS ──
A. "<line 1>
    <line 2>"        → mechanism: <which>  · proof: <the artifact>
B. …
C. …

── THE POST ──
<the draft, formatted exactly as it would be pasted into LinkedIn>

── CHECKLIST ──
<every check that failed, and what was changed. "All passed first time" is a
 red flag, not a result — say so if it happens.>

── FLAGS ──
<anything unverified · any stage claim needing confirmation ·
 anything the ledger cannot back>
```

---

# RULES

```
 1  NEVER PUBLISH THIS DRAFT. Shubham always rewrites. That rewrite is the point —
    it fills work/log/corrections.md and voice.md DERIVED, which nothing else can.

 2  Never draft before the CPIO worksheet is complete and shown.

 3  One post, one reader, one idea. If you cannot name the reader, the Brief is not ready.

 4  Never invent a number, date, timeframe or result. Approximate stays approximate —
    "about two days" beats a fabricated "16 hours", and a real number beats both.

 5  ARTIFACT HOOK, never credential hook. No employer. No money numbers.
    No tenure claim doing the work of proof.

 6  Every tool named carries its real stage. Never skipped upward.

 7  BUILT, NOT DELIVERED. Zero clients. Nothing implies otherwise.

 8  The CTA comes from the Brief. Never hardcoded here. No CTA is a valid outcome.

 9  Never read brain/playbook.md. Wrong platform, contradictory rules.

10  Log every hook written to work/log/hook-bank.md — the ones cut as well as the one kept.

11  If a draft could have been written by anyone about anything, it fails.
    DELETE IT AND START AGAIN. Do not polish it.

12  script-doctor is still the gate after this. THIS SKILL'S CHECKLIST IMPROVES A POST;
    IT CANNOT KILL ONE. A kill verdict there is a successful run.
```
