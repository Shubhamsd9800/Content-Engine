# CLAUDE.md — how to work in this folder

Read `README.md` first, this second, `engine/design/blueprint.md` third.

---

## Session start

1. Read those three files.
2. Read the `brain/` files the task needs.
3. **If the task touches Instagram, YouTube, transcripts or search — read
   `brain/reference/tooling.md` first.** It is the ground truth for what is installed, the
   exact commands, and the three things the tools cannot do. Guessing here wastes a session.
   **Start with its first section, WHERE EVERY TOOL RUNS.** The tools are Windows binaries
   plus a browser bridge on `127.0.0.1:19825`; **only Claude Code, running on the Windows
   host, can execute them.** A Cowork session reads and writes every file here but reaches no
   tool at all — verified by test, Day 24. Check which surface you are on before planning a
   step that fetches anything.
4. **Never load `brain/reference/transcripts/`** unless explicitly distilling a source. Those files are
   6,000–12,000 words of filler around 400 words of framework. Loading them makes output
   vaguer, not sharper.
5. **IF THE TASK WRITES, REVIEWS OR PLANS A POST — read `engine/design/how-to-run-the-pipeline.md` FIRST.**
   It is the operating checklist: **STEP 0 answers *where are we* from the folder rather than
   from a summary**, then both writers gate by gate, `script-doctor`'s 17 checks, and what
   happens after publishing. The picture version, with diagrams, is the **Content Engine Field
   Manual** artifact linked at the top of that file — open it when the shape is unclear.
   **When something changes, update `how-to-run-the-pipeline.md` AND the artifact. Never write a second one.**

6. **Writing a post? The platform decides which file you read — and you read ONE.**

```
   PLATFORM = instagram   →   brain/playbook.md            script-writer
   PLATFORM = linkedin    →   brain/linkedin-playbook.md   linkedin-writer
```

   **Never both. They contradict each other on purpose.** `playbook.md` was built from 15
   creators' Instagram reels — three channels: spoken, on-screen text, visual. LinkedIn has
   one, and `linkedin-playbook.md` was built from a LinkedIn practitioner's own system
   (added Day 28, source in `brain/reference/frameworks/hat-tip-linkedin.md`).

   The clearest case: **S02 THE CORRECTED ASSUMPTION** — *"You probably think X. You'd be
   wrong."* — is `[C]` tier and one of the strongest shapes in `playbook.md`, and a **banned
   pattern** on LinkedIn. Both files are correct. **Do not reconcile them.** `playbook.md`
   §5 is retired and holds nothing but a pointer.

6. Do the work.

## This folder is not

The daily journal (that is Notion) · client work (that is `Founder-Agency/`) · anything
to do with Capgemini.

---

## THE RULES

**1 — Be the strategist, not the typist.** If the idea under a request is weak, say the
idea is weak. A well-written post about nothing burns trust that took months to build.

**2 — Proof beats claims.** ~1.5 years professional. The edge is learning in public with
real artifacts: working code, real systems, real mistakes. Route every claim toward
something showable.

**3 — One idea per piece.** Three ideas is three drafts.

**4 — Everything traces to a source.** A draft names its Brief. A Brief names its input.
A structure names its teardown. If it can't, the engine is improvising.

**5 — Never generic-guru voice.** If a draft could have been written by anyone about
anything, delete it and start again. Do not polish it.

**6 — Volume over polish.** The first fifty posts are reps to build articulation, not a
portfolio.

**7 — A kill verdict is a successful run.** Never produce a post to be helpful.

**8 — Push back once, properly, with the strongest case available.** Then execute the
call without relitigating it.

**9 — Read the files before reasoning about them.** Never argue from memory.

**10 — Ask before moving, renaming or deleting anything.** Show what changes, wait for a
yes. Before a multi-step task, list the steps and wait for a go-ahead.

**11 — Never run git from Cowork.** Read-only commands included — `git status` takes the lock
too, and a git command through the mount leaves an undeletable `.git/index.lock` that makes
`daily-push` fail. Push from Claude Code or PowerShell only. **An existing lock can be MOVED
out of `.git/` into `_to_delete/`**, which the mount permits where it forbids a delete.

**12 — The Brief decides the CTA.** Never a writer. `none` is the default and it is valid and
common. Links go in the **first comment**, never the post body.

**13 — One session per folder.** On Day 29 two sessions edited `status.md` and `CLAUDE.md` at
the same time and silently overwrote each other's work, including a decision Shubham had just
made. Before writing a shared file, check whether it changed since you read it.

---

## THE INTERVIEW METHOD

Every `brain/` file is filled the same way. Claude never writes one from inference. This
applies to **ledger, niche, voice, about-me, strategy and psychology** without exception.

> **Corrected Day 28.** This line used to name `swipe` — archived Day 26, absorbed into
> `playbook.md`. **`playbook.md` and `linkedin-playbook.md` are NOT interview files.** They
> are built from distilled sources and corrected by published results, never by interview.
> Do not apply this method to them.

1. **Candidates, not entries.** Claude brings a short list of points — gaps it can see,
   topics it noticed. Never a written entry.
2. **Shubham picks one.**
3. **Two to four questions, one at a time.** Claude asks, stops, waits for the answer.
   Never a block of questions in one message.
4. **Check the folder before asking twice.** If the answer is on disk, read it. Never ask
   Shubham for something a file already says.
5. **Draft in full and show it.** Every blank Claude still needs is marked in the draft
   rather than filled with a guess.
6. **Ask before saving.** Nothing is written until Shubham says yes.

A file written any other way gets cleared and redone.

**Say why the file matters before starting.** If Shubham asks what a question is for, the
method was started without explaining what the file unblocks. Explain first.

---

## THE DECISIONS

These are settled. State them as facts; never explain what they replaced.

**The niche.** *How one person builds and ships real software products — and what breaks
on the way.* Full definition in `brain/niche.md`, status WORKING, revised from real data at
20 posts. AI is how the work gets done, never the identity.

**Positioning.** *"I go a step ahead into AI and building, and bring back the part that
actually works."* A behaviour, never a title — a title is a claim, a behaviour is proved by
the next post. **Never use "pathfinder" as a public label**; it is an internal compass only.

**Two audiences, two offers.** PEERS — students, engineers, working professionals — buy the
**product** (deferred until post 20). BUYERS — small business owners and solo founders with
no technical person — buy the **service**: web development, SaaS and MVP builds. **The peers
are not a leak. They are the second revenue line.**

**One post, one reader.** Every Brief names `peer` or `buyer`. `mixed` and `unknown` are not
legal values. Which reader is decided per Brief when the idea arrives, never by a standing
rule. **Writing to both inside one piece is what makes content generic.**

**The mix — 3-2-2 per seven pieces.** Three ring 1, two rings 2–3, two ring 4, **never ring
5.** Ring contents in `brain/niche.md`. `brief-builder` assigns the ring after reading the
last six entries of `work/log/published.md`; `script-doctor` writes ring and reader back on
publish. Without both steps the mix silently does not happen.

**Hook framing.** Frame broad, land narrow. Open on **pain or desire** — some permutation of
*"if you want…"* / *"if you don't want…"*. **Never open at the practitioner's level of
awareness.** Most people scrolling are not intentionally trying to learn.

**Built, not delivered.** Content shows what he **builds**. It never claims or implies what
he has **delivered to clients** — there are none, and every ledger entry is built-for-self.
Outreach starts September; content is the proof that makes it credible, not the client
channel itself.

**Platforms.** Instagram and LinkedIn. **X is not started.** *Open: Koe argues one platform
first, then leverage into the second. Not settled.*

**Sequencing.** One Brief produces a LinkedIn post that ships the same day and a reel
script recorded when a 2–3 hour block exists. The written version tests the idea before
an afternoon is spent filming it.

**Reel format**, chosen per piece by rule:
showable proof (code, an error, a diff, a benchmark) → **screen recording** ·
no artifact (a judgment, a story) → **talking head** ·
strong claim with an artifact → **hybrid**, face for the 3-second hook then cut to screen.
Default when unclear: screen recording.

**Reel language**, chosen per piece by rule:
India-facing, peer, story, rant → **Hinglish spoken, English on-screen** ·
buyer-facing, international, a technical claim → **English** ·
LinkedIn → **English, always**.
Before writing any Hinglish script, hold a few turns of casual Hinglish first. Warm-up
language sets the register.

**Funnel.** Every post declares a slot before it is written: **TOFU Monday** (attraction)
· **MOFU Wednesday** (trust) · **BOFU Friday** (the offer). A post with no slot does not
get written.

**Stage label.** Every tool, resource or method named in a post declares its real stage,
in the post: **found** (haven't used it) · **installed** (haven't run it) · **testing**
(running it, partial results) · **shipped** (used it in something that exists).

A post may share anything at any stage. It may never skip a stage upward. "I found this
and here is why it looks useful" is publishable at stage *found*. "Use this" requires
*shipped*.

**Tools.** Free and open source only. **₹0 per run, and it stays that way.** Apify was
assessed on Day 23 and rejected — it works and it would be cheap, but OpenCLI does the job for
nothing. Do not re-open it.

**How Instagram is actually read — settled Day 23, proven on live data.**

> **OpenCLI** bridges into a **burner Instagram** logged into its **own Chrome install** —
> never the brand account, never its browser profile. `agent-reach` installs and health-checks
> it; the reading is done by calling `opencli` directly.

Three limits that shape every step downstream, and none of them are negotiable:

1. **There are no view counts.** Instagram exposes none through any free route.
   `engagement = likes + comments`. **It is a proxy and must be called one** — never described
   as reach in any file or any post.
2. **Twelve posts per run.** `--limit` does not raise it. The accumulating `metrics.csv` is the
   fix, not a flag.
3. **No post URLs from any read command.** All 23 were checked. The URL is copied by hand —
   about two per creator. **This is the only manual step in Pipeline A**, and it is not a bug
   to be engineered away.

**Everything else — the exact commands, what each returns, what is still untested — lives in
`brain/reference/tooling.md`. That file wins over this one on anything tools-related.**

**Social proof as a hook device** is not available until a real number exists.

**Getting creator material.** Claude cannot watch video. It can read transcripts, read
captions, drive the Chrome extension to open a profile and screenshot posts, and pull public
post data through Apify's free tier. Video is a format constraint, not a blocker — name the
creator and the material gets collected.

**Deletion** is blocked on this mount. Move to `_to_delete/` and tell Shubham.

---

## THE BANNED LIST

**Openings and phrasings**
"In today's world…" · "Since the beginning of time…" · "Here's the thing" ·
"Let that sink in" · "the truth is" · game-changer · leverage · unlock · delve ·
seamless · robust · revolutionize · 10x · "Here's why everyone is wrong about X"

Also: emoji bullets · 👇 arrows · manufactured vulnerability · fake round numbers ·
single-word paragraphs used as drama · opening with credentials instead of a problem.

**Outputs**
- Any post where **gaps** and **your standing** are both empty
- Any number that failed two-source verification — deleted, not softened
- Any claim that multi-agent automation is a service line, until a client system ships
- Anything about Capgemini, under any framing
- **Day-in-my-life vlogging** — office routine, lunch break, friends. The script for this
  was already written once and it stays unwritten.
- **Dance reels, trend reels, chamak-chalo reels** — anything where the format is the content
- **Reposting someone else's story with no angle.** The angle does not have to be his —
  **it has to be the reader's problem.** Not *"Sharan failed and it's inspiring."* Instead:
  *"Sharan spent two years failing. You are eighteen months in. Here is the part of his road
  you are standing on right now."*
- **Ring 5** — "AI is changing everything", motivational content with nothing under it
- Any post whose `READER` is `mixed` or `unknown`
- Anything implying a client delivery
- Anything presented as recommended, proven, or as a service he offers, when it has
  not been personally shipped
- More than one idea per piece
- `brief-builder` producing a hook, caption or headline
- "DM me" at zero followers

---

## DESIGN — artifacts and UI

> ## ⛔ THE BRAND SYSTEM IS OUT OF SCOPE. DECIDED DAY 28, CONFIRMED DAY 29.
>
> **Do not read `_plugins/brand-os/brand-output/brand.json`. Do not apply a brand palette, a
> fixed set of colours, or a set typography to anything made for Shubham.** Not to artifacts,
> diagrams, working docs, thumbnails, carousels or post graphics. Not lightly. Not as a
> starting point.
>
> **This section is what caused the override on Day 28.** It previously told every session to
> read `brand.json` for colour and use Poppins / Instrument Serif. A brand system was then
> applied to a carousel built from an external prompt that carried its own design, overriding
> Shubham's own choice. He called it out. **The instruction is reversed here, at the source.**
>
> **RESTORED DAY 29 — this block was written once and silently reverted** when a second
> session overwrote `CLAUDE.md`. If `brand.json` or Poppins reappear as an instruction in this
> file, that is the revert happening again, not a new decision.
>
> **What to do instead:**
> - **A tool, skill or prompt supplies its own design defaults → use those, unchanged.**
> - **Nothing is supplied → ask him.** Never reach for a default.
> - **He asks for a brand system in that request → then, and only then.**
>
> *Historical note, not an instruction:* the retired system was Poppins / Instrument Serif
> Italic on a dark palette, with `brand-os` governing colour. It is in git history.
> **It is not a fallback and it is not a starting point.**

## MEMORY

There is no `memory.md`. A settled decision is written as a rule, once, in the file that
governs it — this file for cross-cutting decisions, the relevant `brain/` file otherwise.
Corrections to drafts go in `work/log/corrections.md`.

When a decision changes, **rewrite the rule.** Never append the new one beside the old.

When a decision is made, hand Shubham the revised block for the claude.ai project
instructions — that layer is the only thing that survives when the folder is not
connected.
