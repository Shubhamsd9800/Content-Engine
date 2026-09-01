# _INTAKE-SOURCE.md — where the reel words live before they land in `raw/`

**Created Day 25, session 2.** Read this before hunting for transcripts.

---

## THE ARTIFACT

**Reel Intake** — the collection sheet for all 22 creators and 66 winning reels.

```
https://claude.ai/code/artifact/ea592260-8a95-4032-a863-ff76dcab221d
```

It holds, per reel: **post URL · full caption · transcript · a screenshots-dropped flag.**
It saves by republishing itself, so the words are inside the published HTML.

### How a session reads it

**Cowork only.** Use the Artifact tool with `action: "read"` and that URL. The words come back
as the page's HTML; the state is a JSON block with id `intake-state`, keyed `<handle>::<index>`.

**Claude Code cannot read it.** No artifact access on that surface. Claude Code's job here stays
what `tooling.md` says it is: OpenCLI, yt-dlp, Whisper, the Chrome bridge. Never the artifact.

If the URL above ever fails, the artifact can be found by listing Shubham's artifacts and
looking for the title **Reel Intake**.

---

## THE SCREENSHOTS — a different route, and not in the artifact

Frames live on disk, never in the page:

```
work/creators/<slug>/raw/frames/post-<index>/
```

66 folders, one per winning reel. Filenames are irrelevant — the folder names the post.
**An image inside an artifact is unreadable to a session** (it arrives as encoded text), which is
why frames go to disk and words go to the page. Tested Day 25 s2, both directions.

---

## THIS FILE IS A STAGING POINTER, NOT THE MEMORY

**The artifact is an input device. The folder is the record.** Once a creator's reels are read,
their words are written into:

```
work/creators/<slug>/raw/pieces.md            URL + FULL CAPTION slots filled
work/creators/<slug>/raw/<index>-transcript.md  one file per winner, headed with its numbers
```

After that the artifact is a convenience, not a dependency — `creator-analyst` reads `raw/`
and has never known where the words came from.

**Do not let 66 transcripts exist only at a URL.** Transcribe-to-disk on the same day they are
read, and push.
