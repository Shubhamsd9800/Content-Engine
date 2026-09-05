# Content Engine

A content system one person runs, by hand, with an AI doing the structured parts.

It turns raw input — something built, something broken, something trending, a thought that
hasn't been named yet — into a published post on **Instagram (reels)** or **LinkedIn
(text)**. It does not write the post for you and publish it. It gets a draft in front of you,
checked against rules you set once, so the writing muscle is the only part left to do by
hand.

The goal isn't post count. It's becoming a name that a cold email can point to — so that when
outreach lands, the person on the other end can search and find something real.

---

## The three layers

```
┌──────────────────────────────────────────────────┐
│  BRAIN              what it believes              │
│  niche · voice · strategy · psychology · ledger · │
│  playbook.md · linkedin-playbook.md               │
│  filled only by interview, or by tearing down     │
│  real creator posts — never guessed               │
└─────────────────────┬──────────────────────────────┘
                       │ read by every skill
┌─────────────────────▼──────────────────────────────┐
│  PIPELINE           11 skills, no opinions of       │
│                     their own                       │
│  they read the brain and act on it — a skill        │
│  changed here changes nothing about WHAT is         │
│  believed, only what gets DONE with it              │
└─────────────────────┬──────────────────────────────┘
                       │ writes only after something ships
┌─────────────────────▼──────────────────────────────┐
│  RECORD             what actually happened          │
│  work/log/published.md · corrections.md ·           │
│  hook-bank.md — grows only when a real post goes    │
│  out, never from a draft or a plan                  │
└──────────────────────────────────────────────────────┘
```

The separation is the whole point. Edit one line in `brain/niche.md` — say, who the audience
is — and every skill downstream reads the new line the next time it runs. Nobody has to open
11 skill files and change them one by one. The skills hold structure (how to build a Brief,
how to run an editing checklist); the brain holds opinion (who this is for, what's banned,
what a post is allowed to claim). Mixing the two is how a system quietly drifts — a rule gets
buried inside one skill, forgotten, and contradicted by the next skill that gets written.

---

## Pipeline A — learning shapes from real creators

Before this system writes anything, it studies what already works. It does not guess at
structure — it takes real posts from real accounts, measures which ones actually did well
relative to that creator's own average, and only then writes down what those posts have in
common.

```
32 creators  →  qualify  →  15-creator watchlist
  (roster)      (5 written gates,
                 not taste)
                                    │
                                    ▼
                          scout  (fetch + rank)
                 pulls recent posts per creator, computes
                 each creator's own median engagement, and
                 flags the posts that clear it as WINNERS
                                    │
                                    ▼
                        creator-analyst  (teardown)
                 line-by-line script analysis of the winners
                 + an account-level teardown of what transfers
                                    │
                                    ▼
                        brain/playbook.md
                 the Instagram writing file — structures,
                 hooks and rules, each one tiered by how many
                 accounts actually prove it
```

This pipeline runs occasionally — about monthly, to keep the watchlist fresh — not per post.

---

## Pipeline B — writing one post

This is the pipeline that runs every time an idea becomes a post. It has one deliberate fork
in the middle.

```
   idea arrives
        │
        ▼
  brief-builder
  writes a Brief: RING · READER · PLATFORM · FUNNEL SLOT ·
  STAGE · CTA, ending in a publish / hold / kill verdict
        │
        ├──────────────────────┬──────────────────────┐
        │                      │                       │
  verdict: KILL           verdict: HOLD          verdict: PUBLISH
  (stop here —                 │                       │
   a success,             READER can't        THE FORK — one platform,
   not a failure)         be decided          read from ONE file only
                                               │
                     ┌─────────────────────────┴─────────────────────────┐
                     │                                                   │
            PLATFORM = instagram                             PLATFORM = linkedin
                     │                                                   │
              script-writer                                     linkedin-writer
                     │                                                   │
        reads brain/playbook.md                        reads brain/linkedin-playbook.md
                     │                                                   │
                     └─────────────────────────┬─────────────────────────┘
                                                │
                                     Shubham rewrites the draft
                                        (never skipped, ever)
                                                │
                                     script-doctor — 17 checks
                                      run on the rewrite, never
                                        on the raw AI draft
                                                │
                                        publish, or kill here too
```

**The fork is deliberate, and the two files it reads are never merged.** `playbook.md` was
built from 15 Instagram creators across three channels — spoken, on-screen text, visual.
`linkedin-playbook.md` was built separately, from a LinkedIn practitioner's own system,
because LinkedIn has exactly one channel: text on a screen. The two files actively contradict
each other. One structure that's rated one of the strongest shapes on Instagram is a named
banned pattern on LinkedIn. Both are correct — for their platform.

### The test that decides the fork

Every Brief answers one question before it picks a writer:

```
Is there something to LOOK AT?

value survives sound-off, screen-blank    ->   LINKEDIN
the value IS the thing on screen          ->   INSTAGRAM
both genuinely fit                        ->   INSTAGRAM FIRST,
                                                LinkedIn as a separate rewrite,
                                                never a paste of the same words
```

A reel is not a LinkedIn post with a video attached to it. If a piece genuinely works both
ways, it becomes two Briefs and two drafts — never one Brief routed to both writers.

---

## The 11 skills

| Skill | What it does | Pipeline |
|---|---|---|
| `qualify` | Cuts the creator roster down to a watchlist using five written gates instead of taste | A |
| `scout` | Fetches recent post metrics per creator, ranks them against that creator's own median, flags winners | A |
| `creator-analyst` | Tears down one creator's winning posts into a script analysis and an account-level teardown | A |
| `topic-scout` | Runs a daily sweep for trending material and ring-1 resources; returns candidates, decides nothing | B |
| `thought-partner` | Turns a thought Shubham already has into a named, postable concept | B |
| `brief-builder` | Turns any input into a structured Brief with a publish / hold / kill verdict | B |
| `script-writer` | Writes an Instagram reel script from a Brief — three aligned tracks, three hook options | B |
| `linkedin-writer` | Writes a LinkedIn post from a Brief using the CPIO worksheet, before drafting a single line | B |
| `script-doctor` | Runs 17 checks on Shubham's rewrite — never on the AI's draft — before it goes out | B |
| `voice-builder` | Builds `brain/voice.md` and `brain/about-me.md` from real writing samples and a gap-driven interview | B — voice layer |
| `niche-finder` | Interviews Shubham to produce `brain/niche.md` — a one-time setup, not a per-post step | setup |

Full detail on how these fit together, gate by gate, lives in
[`engine/design/how-to-run-the-pipeline.md`](engine/design/how-to-run-the-pipeline.md).

---

## The gates — a kill is a successful run

Nothing in this system exists to be helpful. A post produced just to fill a slot burns trust
that took months to build, so every stage has a gate that's allowed to stop the post cold —
and stopping it counts as the system working, not failing.

A few of the sharpest kill conditions:

- **Nothing here is his.** If a Brief has no gap the source missed *and* nothing of Shubham's
  own experience behind it, it's a kill — not a hold, not a rewrite.
- **It would land in Ring 5.** "AI is changing everything," motivation with nothing under it —
  same hour to write, zero qualified attention. Not a preference, a hard never.
- **It hits the NOT-list.** Anything not personally shipped and presented as proven, anything
  implying a client that doesn't exist, anything about the day job under any framing — the
  list is obeyed, not weighed against how good the draft otherwise is.
- **The reader can't be decided.** Every post is written to one reader — a peer trying to
  build something, or a buyer with a business problem. A post that tries to serve both is a
  hold, because it ends up serving neither.

"All checks passed on the first try" is treated as a reason to look closer, not a result to
celebrate.

---

## Honest status

- **Zero posts published.** No performance data exists yet — every rule about what works is
  still theory, and is described that way on purpose.
- **One Brief, one draft.** `work/briefs/` and `work/drafts/` each hold exactly one file,
  written and approved, not yet posted.
- **Pipeline A is complete.** All 15 creators on the watchlist have been torn down into
  `brain/playbook.md`.
- **Pipeline B has run once, and stopped one step short of publishing.**

This isn't dressed up as further along than it is. The system is built; it has produced one
approved draft. Everything after that is next.

For the full operating checklist — every gate, every file, what happens after a post goes
out — read
[`engine/design/how-to-run-the-pipeline.md`](engine/design/how-to-run-the-pipeline.md).
