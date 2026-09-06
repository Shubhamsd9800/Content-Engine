# linkedin-audit-day29.md — audit of the live profile

**Run:** Day 29, 5 Sep 2026. Read live in Chrome, section by section.
**Framework used:** Jean Kang's LinkedIn profile audit prompt (8 sections), run against
`brain/about-me.md`, `brain/niche.md` and `brain/strategy.md` rather than in isolation.
**Readable version, with the full section-by-section:**
`https://claude.ai/code/artifact/be840fe8-8991-464e-81de-9930c5efe6bf`

**SCORE: 4 / 10.** Not a bad profile. A profile built for a job search, being asked to do a
business's job.

---

## WHAT IS LIVE, RECORDED VERBATIM

```
HEADLINE   AI Engineer at Capgemini | I build and ship GenAI systems: LangGraph,
           RAG, FastAPI, React, Next.js | Documenting AI-assisted software
           delivery in public
           158 chars · mobile shows ~45

BANNER     "EMPOWER" over a brain-and-circuit graphic, pale ground. Stock.
PHOTO      White shirt, saturated teal backdrop, looking AWAY from lens, arms folded.
ABOUT      *** DOES NOT EXIST ***
FEATURED   ONE item. A post from 2 years ago, "Development is dead", 12 reactions.
           Its thumbnail reads "I'm a Full Stack Developer".
LINK       "Portfolio" — good label.
EXPERIENCE Capgemini 1y6m (AI Engineer 11m · Software Engineer 8m)
           E-Cell GLA 3y1m (Exec of Graphic Design Team · Volunteer)
PROJECTS   5, all old student repos — AuthApp, BlogApp. Nothing from this year.
SKILLS     Top 3 NOT READABLE from public view. ASP.NET Web API / ASP.NET Core
           surfaced on the SE role; Graphic Design / Illustrator on the student role.
           *** SHUBHAM MUST VERIFY THE PINNED TOP THREE HIMSELF. Not guessed. ***
STATS      695 followers · 500+ connections
```

---

## THE FINDING THE FRAMEWORK HAS NO BOX FOR

> **CORRECTED DAY 29, AFTER SHUBHAM PUSHED BACK. HE WAS RIGHT.**
> The first version of this audit said the employer must not appear on the profile at all.
> **That over-applied a content rule to the wrong surface.**
>
> **`niche.md` NOT-list item 1 governs POSTS** — what he writes in his own voice. **A profile
> is a factual employment record.** Hiding current employment there would be strange, and it
> would damage GOAL ONE: a recruiter assessing him for a remote switch WANTS to see it.
>
> **CAPGEMINI STAYS IN EXPERIENCE. Settled. Do not re-raise it.**

**The headline argument survives, and it is NOT about hiding.**

**LinkedIn already displays "Capgemini" beside his name automatically**, with the company logo,
in the top card. Repeating it in the headline buys the same information twice — and it spends
**24 of roughly 45 visible mobile characters** doing it.

Mobile truncates at ~45 characters. The visible half is currently the employer, which the page
already shows. The differentiated half — *documenting AI-assisted software delivery in public* —
sits invisible in third position.

**THE SEQUENCING, IN SHUBHAM'S OWN FRAMING — he is an engineer now, building toward something
else, and the profile grows with him:**

| Section | What it carries | Changes when |
|---|---|---|
| **Experience** | the factual record — Capgemini, both roles, honestly | the job changes |
| **Headline** | what he builds and who for | **as he grows — this is the field that MOVES** |
| **About** | the bridge — engineer by day, building and shipping in public | continuously |

**The headline is the one field allowed to run ahead of the CV. That is what it is for.**
Experience is where the present tense lives.

**Highest-leverage single edit on the page — reclaiming the first 45 characters, not concealing
the job.**

---

## SCORES BY SECTION

| # | Section | Verdict |
|---|---|---|
| 1 | Photo | minor gaps — not looking at lens; backdrop matches nothing |
| 2 | Banner | **CRITICAL** — stock AI graphic, no offer, no proof, no CTA |
| 3 | Headline | **CRITICAL** — first 45 mobile chars restate what the page already shows; best clause buried third; no reader named |
| 4 | Featured | **CRITICAL** — 2 years stale, thumbnail contradicts the headline |
| 5 | About | **DOES NOT EXIST** — the largest gap on the page |
| 6 | Custom link | working — verify the portfolio still loads (`ledger.md` 11) |
| 7 | Experience | gaps — off-niche student role, stale projects, zero metrics |
| 8 | Skills | verify — top three unreadable publicly, must be checked by hand |

---

## KEYWORDS — THE PROFILE IS THE EXCEPTION

**The engine's anti-keyword rule is about POSTS, not the profile.** A profile is genuinely
searched; headline, About and pinned skills are indexed fields. Keywords belong here, written
as sentences, never as a list.

| Use freely | Use as what he builds WITH | Never claim |
|---|---|---|
| full-stack development · web development · SaaS · MVP builds · React · Next.js · FastAPI · Node.js · Angular | RAG · LangGraph · LangChain · multi-agent · AI-assisted delivery — named inside a sentence, never as identity | **"AI expert"** · **"freelancer"** · anything not personally shipped. **The employer is NOT on this list — it belongs in Experience.** |

**Why "AI expert" is out.** `niche.md`: *AI is how the work gets done, never the identity.* It
fills the slot the position keeps empty on purpose, attracts peers when the profile's job is
converting buyers, and claims what 1.5 years cannot carry. **Same logic as the ARTIFACT HOOK —
the words available are what he BUILDS, not what he IS.**

**Why "freelancer" is out.** To a buyer it reads cheap and temporary. *Builds and ships
software products, solo* does more work and is already the locked line.

---

## TOP THREE PRIORITIES

1. **WRITE THE ABOUT SECTION.** It does not exist. Only place a story arc can live, one of the
   most search-weighted fields, and the only place a CTA can go. Material already exists.
2. **REWRITE THE HEADLINE.** Front-load the first 45 characters for mobile with what he BUILDS.
   **Not because the employer must be hidden** — it stays in Experience and LinkedIn shows it
   beside his name anyway — but because those characters must not buy it a second time.
3. **REPLACE FEATURED** with today's post + the public repo. Cheapest fix on the page.

---

## THE PATTERN UNDER ALL EIGHT

**This profile describes someone looking for a job. The position published today belongs to
someone building a business.** Every gap is a version of that one mismatch. Nothing is broken;
it is aimed at the wrong target.

---

## OPEN — decides the headline wording

**Is the profile primarily for the REMOTE-JOB SWITCH, or for FREELANCE BUYERS?** They pull the
headline in opposite directions — a recruiter scans for role and stack, a buyer scans for
outcome. **Not yet answered.** Claude's recommendation: weight to recruiters for now, since
that is the nearer goal, and let the About section carry the buyer.

## NEXT

Write `work/profile/linkedin.md` — the actual headline, About, featured order and banner copy —
after distilling whatever profile resources Shubham brings, ONE SOURCE AT A TIME, into
`brain/reference/frameworks/`. Do not write the copy before the sources land.
