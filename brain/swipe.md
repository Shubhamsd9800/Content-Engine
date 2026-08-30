# swipe.md — structures taken from creators

**EMPTY.** Fills from `creator-analyst` teardowns in `work/creators/`.
**Every writer reads this.** It is the shape library.

---

> **Shapes are reusable forever. Topics are theirs.**

"Opens with a stated outcome in six words, no context, then undercuts it" is a shape.
"Talks about RAG chunking" is a topic. Taking topics is how you become a worse copy of
someone with a bigger account.

> **Confidence downgrade.** A structure from a large account carries that account's
> authority, and authority does not transfer. Every entry records what the structure sounds
> like at Shubham's actual standing — 1.5 years in, real artifacts, no follower base, zero
> clients.

**Promotion bar: seen in 5+ of 10 pieces AND it transfers.** A pattern seen once is noise.

---

## HOW MATERIAL GETS HERE

Koe's method, run through the Pipeline A tooling. This is the standard for this file.

1. **The watchlist**, in `work/creators/handles.md`, chosen for **coverage** — never for
   whose content looks best. It is written only by `qualify` PASS 2, after Shubham's review.

   **Two budgets, and they are not the same number.** The engine used to run one figure for
   both and it was wrong:

   | | Budget | Why |
   |---|---|---|
   | **SCRAPE scope** | as wide as coverage needs — **22 as of Day 24** | a fetch is seconds, and every creator added starts accumulating a median in `metrics.csv` from that day. Breadth is nearly free and it compounds. |
   | **TEARDOWN budget** | **one creator at a time**, in the order the watchlist sets | ten pieces from one beats two from five. A teardown is hours. More produces overlap, not insight. |

   **The watchlist is a scope, not a queue that must be finished.** This file fills from the
   *first* teardown, not the last one.
2. **`scout` fetches recent pieces per creator** into `work/creators/<slug>/raw/`.
   Whatever route the data arrives by — a CLI, a browser bridge, or screenshots — it
   normalises to one table:
   `creator | date | caption | likes | comments | engagement`.
   **Nothing downstream may depend on how it arrived.**
3. **Selection is arithmetic, never taste.** Per creator: the `median` of their recent
   pieces, then `outlier = engagement ÷ median`, where **`engagement = likes + comments`**.
   Instagram exposes no view counts through any free route — the number is a **proxy** and
   must be named as one, never called reach. Keep pieces at **2× or better**, at most 3 per
   creator. **No piece enters a teardown because somebody liked it.**
4. **Anomalies get transcribed — but the ordinary pieces are still handed over.** The cap of
   3 caps transcription, not the handoff. A teardown promotes a shape at **5 of 10** and it
   answers *"what do the winners have that the others don't"* — neither is possible with three
   winners and no control set. `scout` hands over every piece it fetched, flagged `WINNER` or
   `NORMAL`. Under each winner, **3-5 bullets on why it worked**: the psychological pattern,
   how it held attention, why anyone cared.
5. `creator-analyst` turns those into a teardown at `work/creators/<slug>/teardown.md`.
   **Only teardowns promote into this file.**

**One hard constraint on the watchlist:** it must teach shapes for **both readers.** If
every creator makes tooling content for builders, the engine learns only peer shapes and the
buyer half of the funnel has nothing to imitate.

**THE TOPIC RULE — how selection and the founding law coexist.**

Choosing creators and pieces by niche relevance looks like it contradicts *shapes are yours,
topics are theirs*. It does not, and the boundary is exact:

> **Topic may decide WHICH pieces get read. Topic may never leave the teardown.**

Selecting a creator because they reach business owners is legitimate — it is how both readers
get covered. Carrying their subject matter into this file is not. **The moment a structure
entry names what somebody talks about, it has failed.**

Business inspiration is a different list and does **not** belong here. Raj Shamani, Nikhil
Kamath, Matt Pocock and Alex Hormozi are inspiration for how a business gets built, not
shape references for this account.

---

## STRUCTURES

```
### S01 — <shape name>
FROM        <creator> — used in 7 of 10
SHAPE       0-3s … / 3-8s … / body … / close …
RETENTION   what holds attention at 5s / 12s / 20s
            — open loop, pattern interrupt, seam line, rehook
REWARD      what the viewer walks away holding
MECHANIC    which psychology.md principle it exploits
AWARENESS   broad (pain/desire) | practitioner-level
READER      peer | buyer | both
DOWNGRADE   what this sounds like at his standing
USED IN     <post ids>
```

**`RETENTION`, `REWARD`, `AWARENESS` and `READER` are not optional.** A shape missing any one
of them is unusable, and each for a different reason:

- No **`AWARENESS`** — the writer cannot tell whether the opening reaches anyone at zero
  followers. A **practitioner-level** shape is only usable on a piece already aimed at peers,
  and even then the hook gets reframed broad.
- No **`READER`** — the writer cannot tell who it is for. `mixed` is illegal.
- No **`RETENTION`** — the entry explains how a piece *opens* and nothing about why anyone
  stays. A hook with no retention behind it buys three seconds and loses the viewer at eight.
- No **`REWARD`** — the piece was entertainment. The viewer leaves holding nothing, and
  nothing is what they remember.

*(empty)*

## HOOK PATTERNS

*Reusable opening moves, separated from full structures. Same fields — mechanic, awareness
level, reader.*

*(empty)*

## DID NOT TRANSFER

*Structures torn down and rejected, with the reason. Stops the same bad idea being
re-adopted in three months.*

*(empty)*
