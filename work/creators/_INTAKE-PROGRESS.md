# _INTAKE-PROGRESS.md — what is collected, what is not

**As of Day 25, 30 Aug 2026, end of session 2.** Companion to `_INTAKE-SOURCE.md`
(which says *where* the words live). This file says *how much* of it exists.

**11 of 22 creators collected · 31 reels on disk.**

---

## ON DISK — words written, safe, pushable

| creator | tier | reels | note |
|---|---|---|---|
| `forseth.ai` | 1 | 3 | post 5's paste repeats a block — flagged in the file, kept verbatim |
| `jasoncooperson` | 1 | 3 | posts 9 and 8 repeat a block — flagged, kept verbatim |
| `developer_mannjadwani` | 1 | 3 | **Hindi.** posts 8 and 10 have NO frames yet |
| `theautomationguy.ai` | 1 | 3 | **Hinglish** |
| `kushal_vijay_` | 1 | 3 | English. FENCED — structures only |
| `_roshnichellani` | 2 | 3 | English + Hindi mixed mid-sentence |
| `shashwat___agarwal` | 2 | 3 | **Hindi** |
| `projectonepercent01` | 2 | 3 | **Hindi.** post 2's transcript is cut mid-word in the paste |
| `socialmasla` | 2 | 3 | **Hindi.** post 9 is a CAROUSEL — no transcript, frames are the evidence |
| `aspirenest0b9` | 2 | **1** | post 3 only, and it is a CAROUSEL. Posts 9 and 4 not collected |
| `thevibefounder` | 2 | 3 | **UNRANKED — see below** |

## NOT COLLECTED — 11 creators

**Tier 2 remaining (2):** `roshanvadassery` · `thevibebusiness`
**Tier 3 (9):** `devtalksbusiness` · `tanishqharjani` · `vaibhavsisinty` · `abhishek_ux` ·
`ayushpanchmiyaai` · `nick_saraev` · `saban.talks` · `sanskarr.tiwari` · `techie007.dev`

Their 33 empty frame folders and intake slots already exist.

---

## THE `thevibefounder` CORRECTION — read before using those three files

`scout` measured posts 3, 12 and 10 from the grid. Shubham went to the creator's **Reels tab**
and collected three *different* reels, on the judgement that the grid posts were not the
creator's best work. Verified by caption comparison — none of the three match.

Filed as `unranked-u1/u2/u3-transcript.md`, each carrying a header that says: **no engagement
numbers, not a measured winner, unusable for hits-versus-misses.** The three measured posts
remain uncollected and their slots stay open.

**This is not an error to be corrected away.** It is a real limit: OpenCLI reads the profile
grid, and several creators push their strongest work to the Reels tab only. See the DECISION
NEEDED in `day-26-start-here`.

---

## THREE THINGS THE COLLECTION ALREADY SHOWS — before any teardown

1. **Language splits the watchlist down the middle.** `forseth.ai`, `jasoncooperson` and
   `kushal_vijay_` speak English. `developer_mannjadwani`, `shashwat___agarwal`,
   `projectonepercent01`, `socialmasla` and `theautomationguy.ai` speak **Hindi or Hinglish**,
   often switching language mid-sentence. `_roshnichellani` does both inside one reel.
   Shubham's own stated preference is Hinglish scripts. This is not a small detail — it is
   probably the single biggest structural choice waiting in `voice.md`, and it was invisible
   until the words existed.
2. **Comment-to-DM is near-universal.** Every collected creator except `_roshnichellani` and
   `thevibefounder` closes on *"comment X and I'll send it"*. On `forseth.ai`'s best post the
   comments (13,293) are **more than double the likes** (6,334) — the CTA is not decoration,
   it is the engine driving the number the ranking is built on.
3. **Carousels are in the winner set.** Two of 31 have no spoken audio at all. `scout` ranks
   them alongside reels because engagement is engagement — but a carousel teaches layout and
   copy, never retention. `creator-analyst` must not average the two.

---

## HOW A CREATOR GETS CLOSED

1. Fill URL, full caption and transcript in the **Reel Intake** artifact, and **save**.
2. Drop one or two frames into `raw/frames/post-<n>/`.
3. A session reads the artifact, writes `raw/<n>-transcript.md` and fills the `pieces.md` slots.
4. Only then is the creator eligible for `creator-analyst`.

**Steps 1 and 2 are Shubham's. Step 3 is a Cowork session's. Nothing here needs a tool.**
