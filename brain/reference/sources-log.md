# _log.md — every source, and every creator

Two tables. **The first is material studied. The second is creators whose shapes we take.**

The operating rules extracted from all of this live in `brain/psychology.md` and
`brain/strategy.md`. **Those are the memory.** `raw/` is archive — never loaded as context.

---

# SOURCES

**Rules for this table.** One row per source. `Gave us` names a specific mechanism, never
"it was good." A source that gave nothing is logged as **killed** with the reason — a kill
is data, and it stops the same source being reconsidered.

| Source | Creator | Gave us | Where it lives |
|---|---|---|---|
| Trust matrix | Dan Koe | three legs — attraction / authenticity / authority, each fails alone · authentic polarization · personal brand is a traffic source not a business | `brain/psychology.md`, `brain/strategy.md` |
| Strategic thinking | Dan Koe | strategy = positioning, tactics = execution · anti-vision → post-mortem → mission · concentration of force | `brain/strategy.md` |
| Two levers | Dan Koe | content compounds slowly; direct outreach is fast and doesn't compound. Both are needed. | `brain/strategy.md` |
| 7 content strategies | unnamed | problem match · the villain · [blank] for [blank] · personality over product | `brain/strategy.md` |
| Mission-based niche | unnamed | **Mission + Skill = Desired Outcome.** The chosen method. | `engine/skills/niche-finder/` |
| Script framework | Kallaway | **expectations vs reality** · five steps: packaging → outline → intro → body → outro · click confirmation · the uniqueness gate · **second-best point first** · the value loop · rehooking · native embeds | `brain/psychology.md`, `engine/skills/script-writer/` |
| Hooks / interrupt theory | Kallaway | orienting response · freeze point · **the 4 S's** · **the triple hook** | `brain/psychology.md` |
| Addictive storytelling | Kallaway | **dopamine is prediction, not pleasure** · vending machine vs slot machine | `brain/psychology.md` |
| Storytelling techniques | Kallaway | but/therefore never and-then · rhythm · write the last line first · visual hooks | `brain/psychology.md` |
| Zoom into the moment | Philip | **don't summarise — zoom in.** location · actions · raw thoughts · shown emotion · exact dialogue | `brain/psychology.md` |
| AI scripting system | Aftab (Hinglish) | strong script ← strong idea ← strong angle · **never paste raw transcripts, structure first** · content for everyone is a trap | `engine/skills/brief-builder/` |
| Research + storytelling | Hindi documentary course | **Kipling 5W1H** builds the problem · context then conflict · data interleaved with emotion · **warm up in the target language first** · hunt small creators whose good idea flopped | `engine/skills/brief-builder/`, `engine/skills/script-writer/` |
| Six-stage master prompt | unnamed | **verify every claim against 2+ sources; delete what fails** | `engine/skills/brief-builder/` |
| Outlier formula | Sandy Lee | (views ÷ channel average) × 100 · 5-day window · sub-50k channels | `engine/skills/topic-scout/` |
| **1-1-1 funnel** | **Maria Ledentsova** | **every post has a goal or you don't post it** · TOFU / MOFU / BOFU, Mon / Wed / Fri · the earlier slots earn the right to ask · a free resource that costs you a day and saves a stranger a day is the strongest TOFU format | `brain/strategy.md`, `frameworks/one-one-one-funnel.md` |
| **11 hook modifiers** | unnamed | **the modifier layer** — hook delivery as distinct from hook content · "in [n] seconds" · countdown · objection handling · beat drop on the reveal | `brain/psychology.md`, `frameworks/hook-modifiers.md` |
| **marketingskills** | Corey Haines | **Zeigarnik** (open loops) · **Peak-End** (the outro) · **Pratfall — and it inverts for the unestablished** · searchable vs shareable | `brain/psychology.md`, `frameworks/marketing-psychology.md` |
| Storymaxxing EP1 | The Story ARC | specificity beats polish · relatability before credentials · story before strategy | `brain/psychology.md` |
| 30-day storytelling plan | @thegrowthconsultant_ | **KILLED.** 28 prompts, all inner-journey — zero attraction, zero offer. Would build a peer audience. Storytelling technique kept; the calendar is not used. | — |
| "Claude takeover: LinkedIn" | @gauthamcity | **KILLED.** Four generic prompts, weaker than our writers. An unverifiable impressions claim. A lead magnet. | — |
| 5 Claude agents | unnamed (Hinglish) | **KILLED.** researcher / strategist / writer / editor / publisher. Nothing we don't have — and we do not auto-publish. | — |
| Clone-a-creator | unnamed (Hinglish) | **KILLED.** Depends on paid scraping. The method is `creator-analyst`, done by hand. | — |

## What we deliberately do not take

The 4-act documentary structure and scene formatting — a reel has no Act 2B ·
auto-posting and AI asset generation — we need writing and thinking, not video assets ·
agents that read a published channel — there isn't one yet ·
**all paid tools.**

---

# CREATORS

Creators whose **methods** we study. Never creators whose **topics** we copy.

> **Who you learn from determines who you attract.** If every creator here teaches
> developers, the engine faithfully learns to reach developers — and developers do not
> hire developers.

| # | Creator | Handle | Platform | Slot | What they specifically do | Status |
|---|---|---|---|---|---|---|
| 1 | Maria Ledentsova | @marialeden | LinkedIn / IG | **buyer-audience** | Assigns every post a funnel slot before writing it, and says out loud that a post without a goal doesn't get posted. Her audience is professionals and founders. | **candidate** — no material collected |
| 2 | — | @thegrowthconsultant_ | Instagram | craft | Turns an abstract ask into 28 literal fill-in-the-blank prompts on hand-lettered carousels; the packaging does as much work as the content. | **candidate** — no material collected |
| 3 | | | | peer-audience | | **unfilled** |
| 4 | | | | bilingual | | **unfilled** |

**Candidate ≠ on the list.** A creator earns a row once 8–10 pieces are in
`creators/<slug>/raw/` and `creator-analyst` has produced a teardown.

**At least one buyer-audience creator is required.** That is the slot people skip.

## Intake

1. Add a row with a specific reason. *"Their content is good"* is not a reason. *"They open
   every reel with the outcome before any setup"* is.
2. `mkdir work/creators/<slug>/raw/`
3. Drop material in: transcripts, screenshots, captions, view counts.
   **8–10 pieces from ONE creator.** Ten from one beats two from five — the finding is the
   *repeated* pattern, and repetition is invisible in two.
4. Run `creator-analyst` → `creators/<slug>/teardown.md`
5. Structures at **5+ of 10 and transferable** get promoted into `brain/swipe.md`.

**Four creators is enough to start.** More produces overlap, not insight.

## How material is collected

| Platform | Method |
|---|---|
| Instagram | Chrome extension in Brave, logged in · saved collections · screenshots |
| YouTube | Data API, free tier — views and channel averages |
| LinkedIn | Chrome extension, logged in |

**Claude cannot watch video.** Transcripts, screenshots and captions only.
Engagement numbers say *which* of their posts worked. They never say *why* — the why comes
from the teardown, and the teardown is reading.
