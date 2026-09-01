# tooling.md — what is installed, what it returns, what it cannot do

**Established:** Day 23, 27 Aug 2026, by running every command against a live account.
**Status:** VERIFIED unless a line says otherwise. Nothing here is assumed.

> **This file is the ground truth for the tools layer.** When `engine/design/blueprint.md` or
> `engine-blueprint.md` disagree with it, this file wins — they describe design, this
> describes what actually ran.

---

## WHERE EVERY TOOL RUNS — read this before planning any step

**Established Day 24 by testing, not assumed.** This section exists because the rest of this
file documents commands without saying who can run them, and a session that plans a step it
cannot execute wastes an hour before finding out.

### Three machines, not one

| | Where it is | What it can do |
|---|---|---|
| **Windows host** | `D:\Claude-cowork\Content-Engine` | **Every tool in this file.** opencli, agent-reach, yt-dlp, whisper, ffmpeg, and the Chrome extension bridge on `127.0.0.1:19825`. All installed under the user profile via npm / pipx / winget. |
| **Claude Code** | runs ON the Windows host | Has a Windows shell. **This is the only surface that can run the tools.** |
| **Cowork session** | Anthropic cloud + a Linux VM on the device | Reads and writes every file in the folder. **Cannot reach any tool in this file.** |

### Tested from the Cowork session, Day 24

```
opencli        NOT FOUND        agent-reach    NOT FOUND
yt-dlp         NOT FOUND        whisper        NOT FOUND
127.0.0.1:19825                 PORT CLOSED
```

The Cowork device shell is a Linux VM that mounts the project folder and nothing else. The
tools are Windows binaries and the bridge is a Windows-local port. **Neither is reachable, and
no amount of retrying changes that.**

### What this means per pipeline step

| Step | Needs a tool | Runs where |
|---|---|---|
| `qualify` gates 1 · 2 · 4 · 5 | **no** — evidence is Shubham's roster note | **either** |
| `qualify` gate 3 (followers) | `opencli instagram profile` | Claude Code |
| `scout` | `opencli instagram user` | **Claude Code only** |
| fetch winner URLs | manual, by hand | Shubham |
| download + transcribe | `opencli download`, `whisper` | **Claude Code only** |
| `creator-analyst` | **no** — reads `raw/` | **either** |
| all of Pipeline B | **no** | **either** |

**Gate 3 cuts nobody** — it records a number. So `qualify` completes without tools, recording
`followers: unknown`, and the profile calls become a backfill rather than a prerequisite.
`scout` is the first step that genuinely cannot run outside Claude Code.

### Skill discovery on Windows — the part that silently breaks

Claude Code discovers skills at **`.claude/skills/<name>/SKILL.md`** only. This project keeps
its skills at `engine/skills/<name>/SKILL.md`, so **Claude Code does not see them by default.**

`--add-dir` does not solve it: that flag looks for a `.claude/skills/` folder *inside* the added
directory, which is not the layout here.

**The fix is a directory junction per skill** — supported, and it keeps one source of truth:
`.claude/skills/<name>` points at `engine/skills/<name>`. The file exists once; two paths reach
it. Run once, in **cmd.exe** (not PowerShell). Junctions need no admin rights.

> **CORRECTED Day 25.** This section used to say the junctions live in a `.claude\skills` folder
> **at the project root**. That is not what was done and not what works here. They were created
> in the **global** skills folder, `%USERPROFILE%\.claude\skills`, on Day 25 session 1, verified
> `LinkType=Junction`. A project-root `.claude\skills` is only read when Claude Code is started
> from that exact directory; the global folder is read wherever it starts. **Use the global path.**

```
mkdir "%USERPROFILE%\.claude\skills"
for %S in (brief-builder creator-analyst linkedin-writer niche-finder qualify scout script-doctor script-writer thought-partner topic-scout) do mklink /J "%USERPROFILE%\.claude\skills\%S" "D:\Claude-cowork\Content-Engine\engine\skills\%S"
```

Verify with `dir "%USERPROFILE%\.claude\skills"` — ten entries, each marked `<JUNCTION>`.
After this, `/qualify` and `/scout` work as slash commands in Claude Code.

> `.claude/skills/` holds junctions, never copies. **A copied SKILL.md is a second source of
> truth and will drift.** If a skill is renamed or added, redo its junction.

---

## THE SEPARATION — why the tools sit in their own layer

**Agent-Reach is a capability layer, not a step in any pipeline.** It selects, installs and
health-checks the right tool per platform. It never reads anything itself — the reading is
done by calling upstream tools directly, with no wrapper in between.

**`scout` never knows how to install a downloader. Agent-Reach never knows what a median view
count means.** Neither can break the other, and the whole toolbox can be swapped later without
touching a single skill.

---

## INSTALLED — verified 27–28 Aug 2026

| Tool | Version | Installed how | Config lives |
|---|---|---|---|
| agent-reach | pinned commit `06c202b` | `pipx install <github zip>` | `~/.agent-reach/` |
| opencli | `@jackwener/opencli@1.8.7` | `npm install -g` | `~/.opencli/` |
| OpenCLI Chrome extension | Web Store `ildkmabpimmkaediidaifkhjpohdnifk` | burner Chrome profile only | Chrome profile storage |
| yt-dlp | `2026.08.19` | `pip install "yt-dlp[default]"` | `~/.config/yt-dlp/config` |
| ffmpeg | `9.0.1-full` | winget | — |
| openai-whisper | turbo model, CPU | `pip install openai-whisper` | `~/.cache/whisper` |
| mcporter + Exa | — | `npm install -g mcporter` | `~/.mcporter/mcporter.json` |

**Nothing installs into this project folder.** All of it lives under the user profile.

### Two warnings that cost real time

**1. `pip install agent-reach` installs the WRONG PACKAGE.** The PyPI name belongs to an
unrelated project by a different author (`jgalea`), one version, no license. Install from
GitHub only.

**2. Instagram and Facebook channels exist only on `main`, not on tag `v1.5.0`.** Verified by
HTTP status: `agent_reach/channels/instagram.py` returns 200 at `main`, 404 at `v1.5.0`. They
landed after the tag. Pinning to that tag removes the feature the engine depends on.

---

## `agent-reach doctor` — what is actually live

| Channel | State | Notes |
|---|---|---|
| Any web page — Jina Reader | ✅ | zero config, `curl https://r.jina.ai/URL` |
| YouTube — yt-dlp | ✅ | needed `--js-runtimes node` in the yt-dlp config |
| RSS / Atom | ✅ | zero config |
| Bilibili, V2EX | ✅ | not used by this engine |
| Exa semantic search | ⚠️ **UNVERIFIED** | config written to mcporter; doctor will not claim it works without pinging the remote. **Untested against a real query.** |
| GitHub — gh CLI | ❌ | not installed. Not needed yet. |
| Instagram | ✅ via OpenCLI | see below |

**Twitter, Reddit, Facebook, XiaoHongShu and LinkedIn are deliberately NOT configured.**
Twitter is the only channel requiring a Cookie-Editor export — session cookies are full account
access, and the engine has no use for Twitter. Leave it off.

---

## INSTAGRAM — the only route that works, and its three hard limits

Instagram is read by **OpenCLI**, not by Agent-Reach. OpenCLI bridges into a logged-in Chrome
session through its extension. Agent-Reach's job stops at installing and health-checking it.

### The command that works

```
opencli instagram user <handle> -f json
```

**Returns, per post:** `caption` (truncated ~100 chars) · `comments` · `date` · `index` ·
`likes` · `type`

**Verified live against `nick_saraev` on 27 Aug.** Values moved between two consecutive runs
(734 → 739 likes), confirming a live read rather than a cache.

### LIMIT 1 — no view counts, ever

Instagram exposes no reel play counts through any free route. Checked against OpenCLI, the
Agent-Reach channel list and Apify's documentation.

```
engagement = likes + comments
```

**This is a proxy and must be recorded as one.** No file downstream may describe it as reach.

### LIMIT 2 — twelve posts, and `--limit` does not raise it

`--limit 50` was tested and returned 12. Twelve is what the profile grid loads.

**The fix is the file, not the flag.** `metrics.csv` appends across runs and dedupes on
`date + caption`. Three weekly runs ≈ 36 distinct posts; two months ≈ 100. Older posts also get
**re-measured as they mature**, which removes the bias where a two-day-old reel scores 0.26×
purely because engagement had not accumulated yet.

### LIMIT 3 — no post URLs from any read command

All 23 Instagram subcommands were checked. `user` and `saved` both omit URLs. `search` returns
a `url` column, but **only for profiles, never for posts.**

**Consequence:** `pieces.md` carries the post **INDEX**, and the URL is copied by hand — three
per creator, roughly fifteen minutes a month.

**The index is reliable.** Verified: `opencli instagram save nick_saraev --index 9` saved the
post whose likes matched index 9 in the listing exactly.

### LIMIT 4 — captions truncate at exactly 100 characters

**Verified Day 25 against the raw tool output, not against `scout`:**

```
opencli instagram user nick_saraev -f json --limit 1
→ "caption": "Comment \"SKILL\" to get Nvidia SkillSpector to protect your Claude Code from getting hacked.   If you"
                                                                                              ↑ cut, mid-word, at 100
```

Every caption comes back at exactly 100 characters. **No flag raises it** — the data arrives
already cut, so no skill can print what it never received.

**Why it matters:** on Instagram the caption carries the **CTA and the offer**.
`Comment "DESIGN" to get…` is a mechanic worth studying, and the rest of it sits past the cut.

**Consequence:** the truncated caption identifies a post and nothing else. The full caption is
copied by hand from the post page — **the same page, the same trip as the URL**, so it costs no
extra navigation. Collected only for the winners of creators actually being torn down, never
for all 22. `pieces.md` carries a blank `FULL CAPTION:` line for it, and `creator-analyst` is
told to say so rather than analyse the truncated line when it is empty.

**LIMITS 3 and 4 together are the manual step in Pipeline A** — one visit per winner post,
two things copied. Neither is a bug to be engineered away.

### LIMIT 5 — pinned posts sit at the top of the grid, whatever their age

**Instagram allows up to 3 pinned posts.** `user` returns **grid order**, so a pinned post
occupies index 1, 2 or 3 no matter how old it is. Found live on Day 25, batch 1:

| Handle | Pinned at index | Age |
|---|---|---|
| `techie007.dev` | 1 | **757 days** |
| `theautomationguy.ai` | 1, 2 | 166 and 306 days |
| `_roshnichellani` | 1 | 327 days |
| `thevibefounder` | 1 | 189 days |

`nick_saraev` and `forseth.ai` had none — their dates descend cleanly from index 1.

**There is no flag and no field marking a post as pinned.** It is detected from date order:
find the longest run at the end of the list whose dates never increase; anything before it is
pinned. Never mark more than 3.

**Why it matters:** a pinned post is the creator's **own pick of their best work**, and it is
usually old, from a smaller account. Left in, it takes teardown slots while discovering nothing
(`theautomationguy.ai`'s two pinned sat at 17.61× and 11.00×), and it drags the median across
two eras of the account. `scout` excludes pinned posts from the median and the top 3, and still
hands them over in their own section — **what a creator chooses to pin is a signal, it just
never sets the baseline.**

### Other subcommands, and their state here

| Command | Access | State |
|---|---|---|
| `user <handle>` | read | ✅ the workhorse |
| `profile <handle>` | read | ✅ followers, bio — used by `qualify` |
| `download <url>` | read | ⚠️ **UNTESTED.** Exists, takes a post/reel/tv URL. |
| `saved` | read | ✅ but lossy — returns `comments: 0` for everything |
| `save --index N` | **write** | ✅ used once to verify index mapping. Writes to the burner. |
| `like`, `follow`, `comment`, `post`, `reel`, `story` | **write** | **NEVER USE.** Nothing in this engine posts or engages. |

Useful flags: `--window background` keeps a batch run off the screen. `-f json` for parsing,
`-f yaml` for reading.

---

## THE BURNER RULE — not optional

Instagram is read through a **logged-in browser session**, which means:

1. **Never the brand account.** `shubh.forge` is never used for this.
2. **Never the same browser profile as the brand account.** Same profile means same
   fingerprint, and a flagged burner drags the real account with it.
3. **A separate Chrome install** is used, not a Brave profile — cleaner isolation and it avoids
   OpenCLI having to detect a non-Chrome browser.

**The extension's permissions are broad, by design and by necessity:**

```
debugger · tabs · cookies · activeTab · alarms · storage · tabGroups · downloads
host_permissions: <all_urls>
```

That is DevTools-level control over **every site in that profile**. It is inherent to being a
generic "any site → CLI" bridge, and it is reachable only from `127.0.0.1:19825` on this
machine — never remotely.

> **The isolation IS the security control.** Whatever that Chrome profile can reach, the
> extension can reach. So that profile contains the burner Instagram and nothing else.
> Never sign into Google in it. Never browse anything personal in it.

**Source audit, Day 23:** cookies are written locally at `0600` and never transmitted;
`fetch-adapters.js` makes no network calls despite its name; the daemon binds
`127.0.0.1:19825` explicitly, not `0.0.0.0`.

---

## TRANSCRIPTS

```
opencli instagram download <url>     →  the mp4          ⚠️ UNTESTED
whisper <file>                       →  the spoken words  ✅ installed
ffmpeg                               →  frames, format    ✅ installed
```

Whisper runs **locally, offline, free** — no API key, no account. Default model `turbo`, device
`cpu`. It reads an audio or video **file**; it is not a dictation tool and does not use a
microphone.

**Only the winners get transcribed** — roughly two per creator, not every post. That is what
makes local transcription realistic.

---

## COST

**₹0.** Every tool above is free and open source. No paid API, no subscription beyond Claude
itself.

**Apify was assessed and rejected.** Its Instagram reel scraper genuinely returns view counts
and would cost about $0.66 per run inside the free tier — but the standing rule is free-only,
and OpenCLI covers the job without it. Recorded so the assessment is not repeated.

---

## THE RUNBOOK — running a tool step from Claude Code

Written so the step is repeatable by someone who has not read the rest of this file.

### Before any run — three checks, in order

**1 · The burner Chrome is open and logged in.** Not Brave. Not the profile carrying
`shubh.forge`. The separate Chrome install with the burner Instagram and nothing else. If it is
closed, OpenCLI has no session to bridge into and every command fails with an auth error.

**2 · The bridge answers.** In cmd.exe:

```
opencli instagram profile nick_saraev -f json
```

One known-good handle. It returns followers and bio in about three seconds. **If this fails,
stop** — nothing downstream will work, and the failure is the extension or the login, never the
skill.

**3 · Claude Code is started in the project root.**

```
cd /d D:\Claude-cowork\Content-Engine
claude
```

Skills load from `.claude/skills/` relative to where Claude Code starts. Starting anywhere else
means `/qualify` and `/scout` do not exist.

### Running a step

Invoke by slash command. The skill carries its own inputs, outputs and gates — **do not restate
them in the prompt.** Restating is how a skill and its caller drift apart, and the skill is the
source of truth.

```
/scout
```

Say what is different about this run, and nothing else:

> `/scout` — first live run. Handles are in `work/creators/handles.md`. Run four at a time and
> stop after the first batch so I can see the numbers before the rest.

### What good output looks like

- `work/creators/<slug>/raw/metrics.csv` gained rows, and **no duplicate
  `creator + date + caption`**
- `work/creators/<slug>/raw/pieces.md` holds **every post fetched**, flagged `WINNER` or
  `NORMAL`, with the post **INDEX** on each. Winners are that creator's **top 3 by
  engagement** — rank, not a threshold. `pieces.md` also carries **GAP** (highest ÷ median)
  for the creator, and a `FLAT` note when GAP < 1.5.
  **A pieces.md containing only winners is a failed run** — the control set is what makes
  "5 of 10" and "hits vs misses" possible downstream.
- Any creator with **fewer than 8 posts** was skipped, not scored
- Posts **under 7 days old** are marked `🌱 maturing`, not silently ranked

If any of those is missing, the skill did not run to completion — say so rather than using the
output.

### The three failures that will actually happen

| Symptom | Cause | Fix |
|---|---|---|
| `opencli: command not found` | not on PATH in that shell, or wrong machine | run in cmd.exe on Windows, never in a Cowork shell |
| auth / empty result | burner Chrome closed or logged out | open it, log in, re-run check 2 |
| `/scout` unknown command | junctions missing or Claude Code started elsewhere | `dir .claude\skills`, then `cd` to the project root |

### After the run

The files are on disk. **Cowork can read them** — it just could not produce them. Paste nothing;
say the run is done and analysis continues in Cowork against the real files.

---

## WHAT IS STILL UNTESTED — do not claim these work

1. `opencli instagram download <url>` — never run.
2. **Whisper against a real Instagram reel** — never run.
3. **Exa search** — configured, never queried.
4. ~~**A multi-creator batch**~~ — **RETIRED Day 25. Tested and passed.** All 22 handles were
   read in one sitting: 12 posts each except `forseth.ai` (10 — the account has 10). **No rate
   limiting, no auth drop, no empty result, and the two-in-a-row stop rule never fired.** 22
   sequential reads is proven safe. Nothing above 22 has been tried.

**Items 1–3 remain the risk surface — but none of them is on the critical path any more.**

> **A6 does not depend on 1 or 2.** `download` + Whisper are a convenience for producing
> `raw/<index>-transcript.md`. `creator-analyst`'s input contract names that **file**, never the
> tool that wrote it, so a transcript pasted in by hand is the identical input. Decided Day 25,
> session 2. Test the commands when convenient; do not let them gate a teardown.
