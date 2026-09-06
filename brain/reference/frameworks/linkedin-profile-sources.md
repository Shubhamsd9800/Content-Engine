# linkedin-profile-sources.md — the profile system, distilled from three sources

**Distilled:** Day 29, 5 Sep 2026.
**What this file is:** the raw material, recorded faithfully. It is the SOURCE.
**What reads it:** nobody routinely. `engine/skills/profile-optimizer/SKILL.md` is the
operating file assembled from this one. Come here only to check what a source actually said.

**Feeds:** `engine/skills/profile-optimizer/`

---

## THE THREE SOURCES

| tag | what | who |
|---|---|---|
| `[S1]` | `linkedin-profile-optimizer` skill — 440 installs, 390 stars | Brian Wagner, ai-marketing-claude-code-skills |
| `[S2]` | *"I rewrote my LinkedIn with 5 Claude prompts"* — AI Action Letter #29, 25 May 2026 | Abhijay Arora Vuyyuru |
| `[S3]` | *"10 Claude Prompts to Optimize Your LinkedIn Profile"* — 26 Jun 2026 | Denjie Garcia, boredlisted.com |

**Confidence.** Nothing here is `[C]`. Where two or three sources agree independently it is
marked **2-SOURCE** or **3-SOURCE** and that is the strongest evidence available.
**No line is confirmed until a rewritten profile produces a measurable change.**

---
---

# PART 1 · THE FINDING THAT REORDERED EVERYTHING

## SEQUENCE BEATS STACKING — `[S2]`, and it overrules `[S1]`

> *"Claude's output quality drops fast when you stack 6 jobs into one ask. You end up with
> shallow rewrites for every section instead of a brilliant rewrite of the one section that
> actually matters. Sequence beats stacking."*

**`[S1]` — the most-installed of the three — does exactly this.** Its Step 3 delivers all five
sections in a single response. `[S3]` splits into ten separate prompts and so agrees with
`[S2]` in practice.

**VERDICT: 2 sources to 1. The skill is SEQUENCED, one section per pass, with a gate.**

## THE FRAMING THAT CHANGES THE OUTPUT — `[S2]`

> *"You are my friend who has been a senior tech recruiter for 10 years. You owe me honesty,
> not politeness. I'd rather hear this from you than from a hiring manager who silently passes."*

`[S2]` reports that the standard *"act as a recruiter"* framing — which `[S3]` uses — produces
**corporate politeness**. The friend-who-owes-you-honesty framing produces an actual markup.
**Take the framing. It costs nothing.**

## THE ANCHOR — `[S2]`

> *"Claude can't optimize you for 'a better job.' It needs the actual JD of what you're applying
> to. Without that, you get corporate prose that could belong to anyone with a pulse."*

**The three reasons rewrites flop, per `[S2]`:** no target role · no real numbers · one-shot
prompting.

> **⊘ ADAPTED — SHUBHAM IS NOT JOB HUNTING, SO THERE IS NO JD.**
> The JD's JOB is to be a concrete anchor that stops generic output. **`brain/ledger.md` is the
> anchor instead** — 12 real entries, built, broken, fixed, already on disk. Plus the two offers
> stated plainly. Decided Day 29 with Shubham: no job descriptions, buyer and peer, not a role.

## THE 24-HOUR RULE — `[S2]`

> *"Push it live within 24 hours. You can iterate on a live profile. You cannot iterate on a
> draft sitting in your Claude history."*

**Keep this verbatim.** It is the same failure the first published post was about.

## MOBILE IS FUNCTIONAL, NOT AESTHETIC — `[S2]` `[S3]` **2-SOURCE**

80% of LinkedIn views are mobile. Line breaks are not decoration; a wall of text is scrolled
past. `[S3]`: the first two lines of About decide whether anyone taps *see more*.

> **⊘ GAP IN ALL THREE — none of them states the real headline constraint.**
> `[S1]` says max 220 characters. `[S2]` says max 120. `[S3]` says under 220.
> **220 is the LinkedIn maximum, not a target.** Mobile truncates the headline at roughly
> **45 characters**. That is the number that governs, and no source names it.

---
---

# PART 2 · THE BUZZWORD SCAN — `[S1]`, run before scoring

Flag every instance and **replace it with something specific**. Not a note in passing — a
visible call-out with a replacement.

```
results-driven · results-oriented · passionate about · passion for
dynamic professional · synergy · leveraging (as a noun)
comprehensive · robust · visionary · thought leader (self-applied)
seasoned professional · proven track record · go-getter
strategic thinker (unsubstantiated) · detail-oriented · team player
excited to announce · excited to share · in today's landscape
game-changing · revolutionary · cutting-edge
```

`[S1]`: *"'passionate about' is always replaceable with a specific claim. 'Results-driven' says
nothing."*

**Merge with `brain/voice.md` HARD RULES** — that file already bans *game-changer · leverage
(verb) · unlock · delve · seamless · robust · revolutionize · 10x · fake round numbers*.
**The two lists overlap and neither is a superset. Run both.**

---
---

# PART 3 · SECTION RULES

## HEADLINE

| Source | Length | Structure |
|---|---|---|
| `[S1]` | max 220 chars | 3 variants: **authority-forward · outcome-forward · niche-specific** |
| `[S2]` | max 120 chars | lead with the most credibility-dense fact; 3 versions ranked |
| `[S3]` | under 220 | searchable keyword FIRST, then a value line; 6 versions |

**AGREED, 3-SOURCE:** the headline must contain at least one **searchable keyword**, must not
be a job title alone, and appears everywhere — search results, connection requests, every
comment.

**`[S1]` extra:** the claim must be one *"a competitor can't immediately copy."*

## ABOUT

**`[S1]` structure — HOOK → CREDIBILITY → PROOF → CTA.** Max 220 **words**.
**`[S2]` structure —** hook / what I build + scale / 3-sentence origin *only if it
differentiates* / what I'm working on now / ONE specific CTA. Max 2,000 **characters**.
**`[S3]` —** hook in the first two lines, short paragraphs, proof, one soft CTA, plus **three
alternative opening hooks to test**.

> **⊘ CONFLICT, RECORDED NOT AVERAGED.** 220 words `[S1]` vs ~330 words `[S2]`.
> Both agree the first two lines carry the whole section. **Length is not the variable; the
> hook is.** Resolve by testing, not by picking a number.

**3-SOURCE AGREEMENT:** never open with *"I'm a [title]"*. `[S1]` goes further — **no
first-person opener at all**; start with the claim, not the person.

## EXPERIENCE BULLETS

**`[S1]`:** achievement-first · metric-anchored · keyword-rich · **15 words max** · active verbs
only. Banned: *responsible for · tasked with · helped with*.
**`[S2]`:** `[Strong verb] + [scope/scale] + [measurable outcome] + [business impact]`.
**3 bullets per role MAX.** Lead with the most impressive, not the most chronological.
Banned verbs: *spearheaded · championed · drove alignment · leveraged synergies · owned the
vision · delivered on*.
**`[S3]`:** flag any bullet that still reads like a job description after the rewrite.

**`[METRIC NEEDED]` — `[S2]`, and it is the most useful mechanic in all three sources.**
Claude never invents a number. It flags the exact place a number belongs so the user can go
and find it. **3-SOURCE agreement on never fabricating metrics.**

## SKILLS — **2-SOURCE, and the most underrated section**

`[S1]` and `[S3]` both: **LinkedIn lets you pin exactly THREE, and those carry the most
algorithmic weight.** Recruiters and buyers filter search by skill. `[S3]`: *"the wrong list
literally makes you invisible to the right people."*
`[S2]` adds: identify any skill appearing in 3+ target roles that is **missing**.

**Flag as weak:** anything generic — *Microsoft Office, Teamwork, Communication*.

## FEATURED — **2-SOURCE**

`[S1]`: 4 slots max, ordered for scan, with the one-line description that maximises mobile
click-through. `[S3]`: score each item 1–10 on **trust · goal relevance · click likelihood**,
keep 3–6, **strongest first because most people will not scroll**, and if there is a gap,
**name the one asset to create**.
`[S2]`: for any empty slot, suggest the SPECIFIC piece to make — a post, a one-page case study,
a portfolio link, a Loom.

## BANNER AND PHOTO — `[S3]`, `[S1]`

`[S3]`: score both on **clarity · trust · brand fit**. Banner gets ONE stronger concept —
simple layout, one short line of text, one clear focal point. **Keep advice practical for
someone shooting on a phone.**
`[S1]` banner rule: **two elements only** — the benefit you offer, and proof supporting it.
Right-align the important content so the profile picture does not cover it on mobile.

---
---

# PART 4 · THE AI VISIBILITY CHECKLIST — `[S1]` ONLY, and it is the differentiator

> *"AI-powered search engines surface people differently than Google. Every other LinkedIn
> optimizer ignores this."*

Score each ✅ pass / ⚠️ needs work / ❌ missing.

```
1  ENTITY CLARITY        name + specific role + specific audience in the first 50 words.
                         "marketing professional" is invisible. "fractional CMO for Series A
                         SaaS" gets cited.
2  NICHE SPECIFICITY     one hyper-specific claim: audience + method + outcome.
3  THIRD-PARTY MENTIONS  any external validation — media, podcasts, named companies.
4  CONTENT CONSISTENCY   profile vocabulary MATCHES post vocabulary. If the profile says
                         "growth marketing" and the posts say "demand gen", the model treats
                         them as two different people.
5  DIRECT ANSWER LANGUAGE at least one sentence that reads like the answer to a question
                         someone would type. "X helps SaaS founders…" beats "I am a marketer
                         with 15 years of experience."
6  RECENCY SIGNALS       current experience, accurate dates, recent activity.
7  URL / NAME MATCH      custom URL matching the name. /in/john-smith-cfo beats /in/jsmith8734.
8  CROSS-PLATFORM        same name + positioning on website, GitHub, X, Substack. Models
                         triangulate identity across platforms.
```

> **⊘ ADAPTED — check 3 is the one Shubham cannot pass, and it must not be faked.**
> No media, no named clients, no investor logos. **This is the credential-hook problem again
> and it has the same answer: the ARTIFACT HOOK** (`brain/linkedin-playbook.md` §2).
> A public repo, a documented system and a real build ARE external, checkable artifacts.
> They are not press mentions and must never be dressed as them.

---
---

# PART 5 · THE GUARDRAILS — `[S1]`, and they match the engine exactly

```
NO FABRICATION      no metrics, no external proof, no clients invented. Flag what to add.
SPECIFICITY MANDATE every recommendation ties to what the user actually gave you.
                    "Strengthen your headline" is not advice.
VOICE INTEGRITY     if a sentence could appear in a LinkedIn template, rewrite it.
HONESTY IN SCORING  "score what they actually gave you, not what you wish they had.
                    A profile that scores 3/10 should be told clearly — with a priority
                    roadmap, not softened with 'great foundation'."
```

**These are already engine rules.** `CLAUDE.md` rule 1 (strategist not typist), rule 5 (never
generic-guru voice), `script-doctor` check 13 (the generic test). **Three independent arrivals
at the same standard.**

---
---

# PART 6 · THE GAP ALL THREE SHARE

**Every source assumes social proof the user does not have.**

`[S1]` asks for *"as featured in Forbes"* and named clients. `[S2]`'s worked example is
*"I help YouTube ship the AI features that 2.7B people use every month"* — Google PM, Harvard
MBA, 77K followers. `[S3]` assumes an existing service history.

**Shubham has: 1.5 years, no clients, no press, no money numbers permitted, 695 followers and
one published post.**

> **THE SUBSTITUTION IS THE SAME ONE ALREADY WRITTEN INTO `linkedin-playbook.md` §2.**
> Authority comes from **the build, the breakage, the specific decision, the real number that
> came out of work actually done** — never from scale, tenure, headcount or revenue.
> **This is the single most important adaptation in this file.** Without it, every step of the
> skill asks for proof that does not exist, and the pressure is to inflate.

## OFFER vs CLAIM — the line, decided Day 29

```
✓ AN OFFER   "I build LinkedIn content systems for founders"
             legitimate. he can do it. saying so is not a claim.

✗ A CLAIM    "I've grown founders' accounts"
             NOT-list. zero clients. unavailable until one ships.
```

**Sellable today:** web development, SaaS and MVP builds.
**Testing, not shipped:** copywriting / ghostwriting as a service — `niche.md` OPEN list says
it moves to shipped *"when the posts prove the system works."* One post exists.

---
---

# PART 7 · WHAT IS NOT RUNNING

```
OFF — no target role
  · target-JD input `[S2]`          → replaced permanently by ledger.md. Not job hunting.
  · recruiter-search visibility     → switches on IF the remote-job track reopens.

OFF — no standing
  · third-party mentions, check 3   → never as-is. ARTIFACT HOOK instead.
  · endorsement-request DM templates `[S2]` → not while the skill list is being rebuilt.

OFF — duplicates the engine
  · `[S1]` "write 5 posts" close    → that is linkedin-writer.
  · `[S2]` 4-week authority stack   → that is brief-builder + the 3-2-2 mix.
  · `[S3]` prompt 8 posting plan    → same.
  · `[S3]` bonus connection-request prompt → outreach lives in Founder-Agency, not here.
```

**Everything else runs.**
