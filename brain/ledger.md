# ledger.md

**12 entries. Filled by interview — one question at a time.**

A list of real things Shubham has built, broken or fixed. Every post asks *"what proof do
you have?"* and reads this to answer.

**Rule: Claude does not write entries. Shubham answers, Claude writes down what he said.**

---

## Format

```
## <short name>
What:   what he was building
Broke:  what went wrong
Cause:  why — in his words
Fixed:  what worked
Proof:  what can be shown
```

---

# ENTRIES

## 01 — morning-kickoff + evening-wrapup

**What:** Two Claude skills that run a one-person standup. Evening-wrapup closes the day
and sets tomorrow's priorities. Morning-kickoff opens the next day by reading them back.
Everything writes into a Notion database through the connector.

**Why I built it:** I wanted to track my day to day, the way a company does — the scrum
master sets priorities in the morning, developers work to them and give updates in the
evening. I was trying to do it in Notion by hand and I couldn't do it in the right way.
So I built it.

**What I didn't know:** I didn't know what connectors, plugins or skills could do. I spent
a lot of time finding that out. Building this is how I learned it.

**The honest part:** I give so much time to building things and not to executing them.
**This is the one I built and actually execute, every day.**

**Proof:** The Notion database — Day 1 to Day 19, no gaps, 20 days of output. The skill
itself, saved in Notion and in this Claude account.

**Status:** running. `SHOWABLE`

---

## 02 — The vibe-code workflow

**What:** An 11-step chain of skills that takes an idea to a production-grade application
without ever saying "build me an app." App flow → UI → PRD → HLD → spec → tests → kanban →
implementation → review. Twelve skills. A tester, a developer, a kanban writer, an HLD
writer that calls an external skill to generate the architecture diagram.

**Why I built it:** People tell Claude "build an app for me" and get something that isn't
production grade. The AI has the knowledge — the problem is nobody asks it properly.
I wanted the multi-step version, not the one-shot version.

**What I didn't know when I started:** I could not understand how to design an
architecture, or what the complete flow even was. I asked a senior architect I know and
he told me to use a **top-down approach.** That was a new word for me. Then I took the
Claude subscription and went looking for how people actually do it.

**How I built it:** Many YouTube videos, many repos. I took a chunk from here and a chunk
from there — the PRD writer's grilling method came partly from Matt Pocock's material,
other parts from other creators. I can't name one source. **I gathered other people's
workflows and built my own out of them.**

**Time:** about seven days.

**The honest part:** **It is not proven yet. It has produced no output.** The Cafe
Management System is the project it was built alongside and that is still mid-flight.

**Proof:** `app-build-workflow-v5/` — 12 skill files. `WORKFLOW-V5.md`. The v4 version
kept alongside it, so the rewrite is visible. `SHOWABLE`

**Status:** built, unproven.

> ⚠️ **Naming constraint.** The architect works at Shubham's employer. The NOT-list bans
> anything about Capgemini under any framing. **Write it as "a senior architect I know" —
> never the company.** The lesson is his; the workplace stays out.

---

## 03 — Cafe queue & order-ahead system

**Where it started:** I went to a cafe. It was crowded. I couldn't get near the menu or a
table, and I had no idea how long the wait was. So I left and went to the next one so I
could eat quickly.

**The problem, stated properly:** A customer arrives at a busy cafe, sees a crowd, cannot
get a menu, and does not know whether the wait is twenty minutes or ninety. There are
three other cafes within walking distance. They leave. **The cafe loses a customer it had
already attracted to its door, at its busiest and most profitable hour — and nobody counts
these losses, because there is no record they ever existed.**

**The idea:** Not a cafe management system. Not plain QR ordering. A QR outside the door
and on the tables, a menu the customer can browse from the pavement, an order placed
before they're seated, **a ready-time they can plan around, and a proactive WhatsApp ping
when it's ready.** Twenty-five minutes stops being a reason to leave and becomes a known
interval they can spend somewhere else and come back from.

**Why it isn't already solved — the part I checked:** QR ordering is commoditised in India
(Petpooja has 45,000+ restaurants, plus DotPe and Posist) but every one of them **assumes
the customer is already seated**, so they never needed a ready-time. Waitlist products
solve the table wait and never touch the menu. **Nobody joins the two.** Cornell
Hospitality Research: digital waitlists show 25% fewer walkaway guests and 15% faster
table turns.

**What I built:** a 14,938-word PRD with 24 questions answered and 5 amendments, a
9,291-word app flow, and six journey diagrams — customer, owner and staff, in PNG and SVG.
Real roles, real access rules, and a deliberate no-forgot-password decision that removes
the email dependency from v1.

**Real prospect, researched for ₹0:** A cafe in Ballygunge, Kolkata — 4.3 stars, 568
reviews, ₹200–400 a head, open until 5am. **Their entire web presence is a Facebook page.**
The owner replies to three-year-old reviews, so someone there cares how the place looks
online.

**And then I wrote down that they were the wrong fit.** First floor, a reservation partner,
no footpath queue — the queue product doesn't apply to them. It's recorded in `memory.md`
as *"seed data, not design input"* rather than quietly ignored.

**Broke:** It stopped at step 3 of 11. `ui-brief`, `hld`, `threat-model`, `build-spec`,
`test-plan`, `kanban` were never written. **No code exists.**

**Proof:** `Cafe-Management-System/` — 54,211 words, 3 commits, a real GitHub remote, six
diagrams. `SHOWABLE`

**Status:** paused at 3 of 11. The only client-facing thing in this ledger.

> ⚠️ **The client brief contains a real business name, address and phone number. None of
> it goes in a post.** The problem and the research method are the content; the prospect
> is not.

---

## 04 — daily-push

**What:** A skill that gets a day's work onto GitHub in one pass, with the two checks that
matter **enforced rather than remembered.** Checks ignore rules, scans the staged diff for
phone numbers, emails and API keys, shows a one-screen summary of exactly what changed,
then commits and pushes only after approval. Four Python scripts do the real work —
`check_ignored.py`, `ensure_ignore.py`, `scan_staged.py`, `summarize_staged.py`.

**Why it exists — two failures that pull in opposite directions:**

*Losing work.* These folders have held days of work with no remote at all. Backups in
`%TEMP%` are not backups — Windows clears it without warning.

*Publishing someone else's data.* `Founder-Agency` holds real prospect research — cafe
owners' mobile numbers, pitch strategy, menu pricing. **A private repo is not a secret
store.** Collaborators, tokens, org transfers and future-you all read history, and history
is effectively permanent. **A phone number pushed tonight cannot be recalled tomorrow.**

**The design:** make the first failure impossible to reach by making the second one hard
to cause. Nothing commits until the scan is clean, or until it's been looked at and
explicitly waved through.

**What I found out the hard way:** running git through Cowork's mount leaves behind a
`.git/index.lock` that **cannot be deleted on Windows** and blocks every later git
operation in that repo. It happened once. The skill now refuses to run git from Cowork at
all and says why, then offers to do the safe parts — reading, reviewing, drafting the
commit message.

**A precision that took a while to get right:** `git rm --cached` removes a file from the
index and **leaves it on disk.** `.gitignore` only changes what git looks at and never
removes anything. Neither is a delete. Both sound like one.

**Proof:** `daily-push/SKILL.md` plus `references/first-time-setup.md`,
`references/troubleshooting.md` and four scripts. `SHOWABLE` — the scanner logic shows
well with the client data redacted.

**Status:** built. **Currently sitting in `Founder-Agency/_to_delete/`.**

---

## 05 — A project per purpose: the one-person company

**What:** Separate Claude projects, one per job, instead of one assistant that does
everything. Each has its own folder, its own memory, its own rules.

| Project | The role it plays |
|---|---|
| **Founder-Agency** | **the war room** — planning, brainstorming, working through a problem and its possible solutions |
| **Cafe-Management-System** | one project per client or per idea |
| **Content-Engine** | the content operation |
| morning-kickoff / evening-wrapup | the scrum master — sets the day's priorities, closes it out |
| the vibe-code workflow | the build team — architect, spec writer, tester, reviewer |

**The idea underneath it:** I am building a **one-person business model.** A company has
a scrum master, an architect, a build team, a planning room and a content team. I don't
have those people. So I built each one as its own project, with its own context, and I
switch between them.

**Why separate and not one big one:** because a war room and a client build are different
conversations. Mixed together, neither gets a memory that means anything.

**What I learned to make this possible:** what projects are, what skills are, how they
attach to a folder, and how memory works per project. **That is what unlocked the rest of
it.** I found out about projects because I needed somewhere to keep two different kinds of
thinking apart.

**The honest part:** the roles exist in different states. The scrum master runs daily. The
build team is built and unproven. The war room works. **The content team is still being
figured out** — that's what today is.

**Proof:** three project folders, each with its own `CLAUDE.md` and memory. 34 skills
installed. `SHOWABLE`

---

## 06 — brand-os

**What it is:** A **plugin** — not a skill. `brand-os` v1.0.0, MIT, author Shubham Das.
It has a `plugin.json`, a `/brand` command, a `brand-system` skill inside it, an
installer, and **nine Python scripts** that do the actual work.

**What it does:** Takes a brand from nothing to a usable system in one pipeline. It
orchestrates four existing skills — UI Color Palette, getdesign, web-typography and Radix
Colors — then adds three things they don't have: **a blocking contrast validator, an asset
renderer, and a rejection log.**

**Why I built it:** If I'm building my brand, I need guidelines — these background colours,
this type, and a way to stop myself picking something different next week. So I built the
thing that decides once and then enforces it.

**What comes out:**

- `brand.json` — 25 colour tokens per mode, every one with its Radix step and its role
  ("card background, resting", "component background, hover")
- **Typography with two scales that are explicitly not interchangeable** — canvas at ratio
  1.21, web at 1.25, separate line heights for each, measure 37ch on canvas and 65ch on web
- **A contrast audit with real WCAG grades**, checked rather than assumed — headline on
  page background 15.98 AAA, body 5.79 AA, accent 4.65 AA
- Exports in five formats: `tokens.json`, `brand.css`, `theme.css`, `_brand.scss`, `COLORS.md`
- **Six rendered proof images** — banner, slide, square, OG, light and dark

**The system:** shubhh.forge. Radix blue on slate. Clash Display, Geist Sans, Geist Mono,
Instrument Serif Italic — all free for commercial use.

**Broke — and this is my actual complaint:** **The workflow runs fine. The output isn't
what I wanted.** The pipeline does exactly what it was built to do and the things it
renders still don't look how I pictured them. That is a taste problem, not a tooling
problem, and I haven't solved it.

**One thing that got fixed:** the export used to ship colour only, so every renderer
hardcoded its own type scale. It now carries the full typography block. That defect is
closed.

**Proof:** `_plugins/brand-os/` — plugin manifest, 9 scripts, 4 reference docs, 6 rendered
proof images, its own git repo. `SHOWABLE` — the proof images are the artifact.

**Status:** working. Output not yet satisfying.

---

## 07 — Rebuilding the LinkedIn profile

**Date:** Aug 15–16

**What:** Refined the headline, the About section and all the experience descriptions. Used
a master prompt I found on Instagram, run through Claude Code.

**Why:** Everything on the profile was old — it described what I used to do, not what I'm
doing now. I'm about to start posting about AI and building, on LinkedIn and Instagram.
**When someone reads a post and clicks through to the profile, the two have to look like
the same person.** Posting about Claude while the profile says something unrelated makes
both of them look fake.

**Also created:** a new Instagram profile, **shubhh.forge** — the same name as my brand
system, so the two match.

**Still not done:** the projects section. Experience is rebuilt; projects needs another pass.

**What I learned doing it:** there is an API route for pulling LinkedIn data through the
Chrome extension. Useful beyond this one job.

**Proof:** the live profile. `SHOWABLE`

**Status:** mostly done. Projects section open.

---

## 08 — The Skills Tracker

**Date:** Aug 6

**What:** A Notion database holding every skill I have built. Twenty-three rows. Each row
records what the skill does in one line, **what file it produces**, whether it runs in
Cowork or Claude Code or both, and which step of the workflow it belongs to.

**Why I built it:** The skills already live in `.claude/skills`, so this is not a backup.
**These skills took real effort.** Weeks of grinding through YouTube, social media and
research to work out how they should be built. That knowledge is worth something to other
people, and I intend to hand it over. **The tracker is the inventory of what I would be
handing over.**

**Two decisions inside it:**

Every skill declares its output. `workflow-router` says *"No file — routes to next skill,"*
because its entire job is telling you where you are in a project and which step comes next.

`scope-interview` is kept as a **RETIRED** row rather than deleted. A skill that was tried
and dropped is worth knowing about.

**What it covers:** the eleven workflow skills from router through review, four daily-ops
skills, `codebase-architect` for periodic drift scans, four reference skills that other
skills call, and two utility skills.

**The version history behind it:** the workflow went **v1 → v2 → v3 → v4 → v5.** v4 and v5
are both still on disk, so the change between them is readable.

**The honest part:** all twenty-three rows say **Done.** The workflow they belong to has
never been run end to end.

**Proof:** the Notion database, and v4 sitting beside v5. `SHOWABLE`

---

## 09 — Content Studio: 67 pieces, none posted

**Date:** Aug 15

**What:** A Notion database with 67 content pieces. Every one has a title, an angle, and a
**hook already written.** Eleven have complete scripts in delivery-ready cue format.
Platform is set on each — Instagram, LinkedIn, or both.

**Why I made it:** It was never a finished plan. **In twenty days I learned a huge amount**
— from videos, from research, from building. Every time something landed I put it in as a
possible piece so it would not be lost. **I dumped what was in my head so I could decide
what to do with it later.** That is what those 67 rows are.

**Where it stands:** 65 rows say **Not started**, all dated the same day. Two say
**In progress.** None say **Done.** One row carries a post date — Aug 15 — and it was
never posted.

**What is in there:** *"Twelve days, zero code."* *"Three days of building. Zero output."*
Both have finished scripts. Both are unposted. **I wrote the description of the problem,
several times, as content, and never published any of it.**

**Proof:** the database — 67 rows, and a Status column that never reaches Done. `SHOWABLE`

**Status:** the ideas exist. Nothing has left the building.

---

## 10 — The marketplace skills: wired into step 3, never fired

**What:** Five skills taken from the Claude skill and MCP marketplaces — ui-ux-pro-max,
design-dna, test-frontend, system-architecture, and a mermaid diagram skill. Not loose
downloads. They are wired in as dependencies inside two skills I built: `hld-writer` calls
the architecture and diagram ones, `ui-brief-writer` calls the three design ones.

**The problem I was solving:** If you ask Claude or Codex or anything else directly for a
landing page, you get UI that looks AI-generated. People can tell instantly. The model has
the capability — the prompt is the bottleneck. The marketplaces exist because other people
hit the same wall and packaged the fix.

**Where I look — the actual list:**
claudepluginhub.com · skills.sh · skillsmp · mcpmarket.com · GitHub · Instagram ·
Reddit communities.

Instagram and Reddit are where I see something being used. The marketplaces and GitHub are
where I go to get it.

**The design:** my skill orchestrates theirs. `ui-brief-writer` doesn't just run a design
skill — it briefs it to work my way, routes into the others, and loops back before locking
one direction. The downloaded skills are components, not the workflow.

**Where it actually stands:** `prd.md` ran — 715 lines. `app-flow.md` ran — 743 lines.
`ui-brief.md` does not exist. `hld.md` does not exist. `wireframes/` does not exist. The
chain stopped at step 3 of 10 — the exact step that calls the skills I downloaded. Ten days.

**The honest part:** I wired five tools into a workflow and never reached the step that
uses them. The wiring is real work and it is not the same as running it. Other people have
run these with proof. That is their proof, not mine.

**Stage:** installed.

**Next:** run `ui-brief-writer`, then `hld-writer`, on Cafe-Management-System. This entry
gets rewritten from *installed* to *shipped* when `ui-brief.md`, `wireframes/` and `hld.md`
exist.

**Proof:** the two files that exist and the seven that don't, side by side.
`ui-brief-writer/SKILL.md`, which names the three design skills by name in its own
description. `SHOWABLE`

---

## 11 — The portfolio: a source of truth nobody can open

**What:** A portfolio site — landing page, about section, tech stack, and the projects I
have actually shipped. Built with **Next.js**, with shadcn/ui, GSAP and Framer Motion for
the animation work.

**Why I built it:** I'm a software engineer who wants to freelance. I needed one place
where someone can find out who I am and what I've built. My words: **the source of truth
of me is that portfolio.**

**Who I built it for:** Hiring managers and HR. When I designed it, the mindset was job
purpose. Someone lands on it, checks whether what I've built is relevant, decides whether
to talk to me. A digital resume.

**What changed:** I'm not only chasing a job now. Personal brand, freelancer, maybe an
agency later. That is a different reader with a different question. A hiring manager asks
*"is he good enough to employ."* A business owner asks *"can he fix my problem, and what
does it cost."* The site answers the first question and has no answer for the second.

**The distinction that matters:** **a resume asks to be evaluated. A service page makes an
offer.** I built a resume. I need a service page. It is the same material pointed the other
way — and that is why it feels like it needs a rebuild. It is not the design.

**The tell:** I want people to be able to book a one-to-one call. There is nowhere on the
site to do that. A resume has no booking link, because a resume doesn't need one.

**Where it actually stands:** the projects it showcases are deployed and live. The
portfolio itself has never left my disk. **The one document whose entire job is to be found
by strangers is the one thing nobody can reach.**

**Stage:** built, not deployed.

**Next:** rebuild the content for a buyer, not an evaluator. Add a booking path. Deploy it.

**Proof:** the codebase, and the deployed projects it points at. `SHOWABLE` once it has a
URL.

---

## 12 — The Content Engine

**What:** A content system in three layers. **BRAIN** — psychology, strategy, voice, niche,
swipe, ledger; slow, changes rarely. **PIPELINE** — research → analyze → write → my rewrite
→ doctor; runs per post. **RECORD** — published, hook-bank, corrections; grows every time
something ships, and after about twenty posts it overrides the brain. 24 files, 7 skills.

**Why I built it:** I watched a lot of people building content systems with Claude and took
the inspiration. Not the whole thing — I can't build that. Just the part that fits my actual
day to day: take an idea, run it through a workflow, get a post out.

**The principle underneath it:** If you go to the model and randomly say *"this is my topic,
give me content,"* it feels AI-generated. Everyone can tell. The fix is what sits in front
of the model — the brain, the niche, the ledger, the Brief. **There should be a feel that a
human is in the loop.** That is the whole product.

**The same wall, twice:** I hit this in UI first — ask AI directly for a landing page and it
looks AI-generated, so I wired design skills in front of it. Then in content — same problem,
same fix. Two domains, one thesis: **the model has the capability; the input layer is the
bottleneck.**

**What happens to the 67:** Content Studio isn't waste. Those pieces go back through the
engine later as input. The ideas were real; they had nothing structured to run through.

**Where it actually stands:** built and unproven. `published.md` says zero. `niche.md` is
written and the ring mix, the two offers and the NOT-list are wired through every skill.
`swipe.md` is empty — no creator teardowns collected yet, and it is the only file still
waiting on input. The blockers are known and named, not hidden.

**My position on that:** we are building it. It might fail. We execute it anyway. The
learning is the point, and later it can be made usable enough that other people can run it
too.

**Stage:** built, unproven.

**Proof:** the folder — `brain/`, `skills/`, `work/`, `sources/`. 24 files, 7 skills, every
rule traced to a named source in `sources/_log.md`. `SHOWABLE`

---

*(entry 13 — waiting for Shubham to pick the next topic)*
