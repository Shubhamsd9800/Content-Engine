# THE BRIEF

The contract between ANALYZE and WRITE. **The writers see only this** — never the raw
transcript, never the raw interview answers.

Saved as `work/briefs/<yyyy-mm-dd>-<slug>.md`.

```
ID              <yyyy-mm-dd>-<slug>
TYPE            external | personal
SOURCE          link, or "personal — <date>"
CONTENT TYPE    long-form video | short post | repo | announcement | article | personal event

CORE CLAIM      one sentence. the single thing being said.

EVIDENCE        artifact | numbers | demonstration | "assertion only"
SPECIFICS       named versions, real numbers, dates, timings, file paths
VERIFICATION    ✓ verified: … | ⚠ disputed: … | ✗ removed: …     [Mode A]

ROOT CAUSE      the full five-whys chain                          [Mode B]
FIX             what worked, including what didn't                [Mode B]
PROOF           what can be shown                                 [Mode B]

GAPS            what the source missed, assumed, or got wrong
YOUR STANDING   the specific ledger entry — or "none"

RING            1 | 2 | 3 | 4          ← 5 is not a legal value
READER          peer | buyer           ← exactly one. never both.
OFFER           service | product | none
TRUST LEG       attraction | authenticity | authority   ← one
VILLAIN         the practice / default this is against
FUNNEL SLOT     TOFU | MOFU | BOFU
STAGE           found | installed | testing | shipped | n/a
STANDING TYPE   built-for-self | delivered-to-client
NOT-LIST        ✓ cleared — or the item it hits

PLATFORM        instagram | linkedin    ← exactly one. "both" is not a legal value.
BUCKET          built | stuck | moving  ← REQUIRED on linkedin. optional on instagram.
CTA             none | question | offer ← REQUIRED on linkedin. "none" is the default.

VERDICT         publish | hold | kill
REASON          one line
ROUTE           single | linkedin-first
```

> **THREE FIELDS ADDED AND ONE CORRECTED, DAY 28.**
> `PLATFORM` was added to `brief-builder` on Day 26 and **never reached this template** — a
> Brief written from this file alone would have had no platform at all. `BUCKET` and `CTA` are
> required by `linkedin-writer` Gate 1, which fails without them. `ROUTE` no longer accepts
> `both`, because it was contradicting `PLATFORM — exactly one`.

---

## THE FOUR KILLS

A kill is a **successful run.** Report it as one.

| Condition | Why |
|---|---|
| `GAPS` empty **and** `YOUR STANDING` empty | nothing here is his |
| `RING` would be 5 | same cost to make, zero qualified attention |
| `NOT-LIST` hits any item | the list exists to be obeyed, not weighed |
| `READER` cannot be decided | a post for both readers is a post for neither |
| `BUCKET` needs a case study, testimonial or client result | no material exists. BUILT, NOT DELIVERED. |
| `BUCKET` is `moving` and the post adds no read of its own | a reaction is not commentary |

---

## FIELD NOTES

**RING** — from `brain/niche.md`. **1** resources found, what I built and broke, systems
and how they are wired, getting AI to produce work that doesn't look AI-generated ·
**2–3** the basics nobody teaches, beliefs I can argue, what a business needs built and
what getting it wrong costs · **4** AI and industry news with my opinion, founders'
journeys told from the reader's position · **5** never.

**The mix is 3-2-2 per seven pieces.** Check the last six entries in `work/log/published.md`
before assigning. If three ring-1 pieces already shipped in this seven, this one is ring
2–3 or 4.

**READER** — exactly one. `mixed` is not a value. Which reader is decided here, per Brief,
when the idea arrives. **Writing to both inside one piece is what makes content generic.**

**OFFER** — `service` (web development, SaaS/MVP builds — sold to buyers) · `product` (the
engine, workflows, templates — sold to peers, **deferred until post 20**, so `product`
Briefs are held, not published) · `none` (most pieces).

**STAGE** — every tool, resource or method named in the post declares its real stage in the
post. **A stage may never be skipped upward.** "I found this and here is why it looks
useful" publishes at *found*. **"Use this" requires *shipped*.** `n/a` when no tool is named.

**STANDING TYPE** — `built-for-self` on every entry in the ledger today. **A Brief may not
imply client delivery until a `delivered-to-client` entry exists.** This is a separate
check from the ledger match: a real ledger entry can still be used to imply something false.

**NOT-LIST** — check all five before writing the verdict. Day-in-my-life vlogging · dance,
trend or chamak-chalo reels, anything where the format is the content · reposting someone
else's story with no angle · anything about Capgemini · anything unshipped presented as
proven.

Item 5 has a positive form and it is the sharpest rule in the engine: **the angle does not
have to be his — it has to be the reader's problem.**

**TRUST LEG** — one. A post serving three serves none.

**ROUTE** — defaults to `both` on a publish. LinkedIn ships today; the reel is recorded
only if the written version landed.

Three claims is three Briefs, never merged.

Killed Briefs stay in `briefs/`. A kill is data — it stops the same dead idea being
reconsidered in three weeks.

---

## FIELD NOTES — added Day 28

**PLATFORM** — exactly one, and it decides the writer and the writing file.
```
instagram  →  script-writer     reads  brain/playbook.md
linkedin   →  linkedin-writer   reads  brain/linkedin-playbook.md
```
**The test: is there something to LOOK AT?** If the value survives being read with the sound
off and no screen — LinkedIn. If the value IS the thing on screen — Instagram. A piece that
genuinely fits both is **two Briefs and two drafts**, never one draft sent twice.

**BUCKET** — where the idea came from. Required on `linkedin`.
```
built    brain/ledger.md, a built-for-self entry        MOF
stuck    a real stuck-point, past or present            MOF
moving   what is happening in AI and building this week TOF
```
`moving` is a full bucket, not a lesser one — but a screenshot plus a reaction is not a post.
**A screenshot plus a read is.** Ask the brand promise: who is stuck, and what do they leave
with?

**CTA** — decided here, never by the writer.
```
none      the post ends when the idea ends. THE DEFAULT. Valid and common.
question  one they can answer from their own experience — never one testing
          whether they read the post
offer     a plain statement of what he builds and who it is for.
          buyer + BOFU only. A statement, never a pitch.
```
**Forced CTAs are a banned pattern on LinkedIn.** If none is earned, write `none`.
**Links never go in the post body — first comment only.** That is a platform fact, not a
choice this field makes.
