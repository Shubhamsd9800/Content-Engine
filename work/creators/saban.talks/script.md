# script — saban.talks

**RUN** Day 27, 1 Sep 2026 · **2 scripts** (#9 never collected — Shubham's Day 26 decision)
**VERIFIED against `pieces.md`: PASS**
**Ratios:** engagement median 1,429 · likes median 1,262 · GAP **2.48x engagement / 2.53x likes**
⚠️ **RANK FLIP ON LIKES:** #10 (2.53x) edges past #8 (2.41x). On engagement #8 leads.
**The difference is 501 comments on #8 — and those comments are the content.** See below.

> ## ⚠️ HE IS THE ONLY PURE TEACHER ON THE WATCHLIST.
> No tool giveaway. No gate. No prompt pack. No "comment X". **#10 is 450 words of mobile
> engineering explained properly, and it is his best post on likes.**
> `handles.md` parks him at 2.5x — *"Flat"* — and that is true and beside the point.
> **Thirty-one scripts in, he is the only one who teaches something the reader could not
> have found by clicking a link.**

---

## ── SCRIPT #10 · 2.25x / **2.53x** · ~450 words — the longest script in the project ──

```
PACKAGING      caption: ~110 words of real technical detail — Remote Config, Server-Driven UI,
                        what OTA does and does not replace, and the exact list of things that
                        force a new store build (Kotlin, Swift, native SDKs, permissions,
                        manifests, entitlements)
               expectation set: your apps change without updating, and there is a real reason.

CLICK CONFIRM  "तो ये सोचा है तुम्हारे **Netflix, Blinkit, Instagram** जैसे apps पर **बिना
                update किये UI change कैसे हो जाता है?**"
               ("have you ever wondered how the UI on your Netflix, Blinkit, Instagram changes
                 without you updating them?")
               confirms ✅ · beats ✅
               → 🔴 **NAME IT: THE UNNOTICED THING.** Not a problem, not a price, not a tool —
                 **something that happens to the viewer constantly and that they have never
                 once questioned.** It creates curiosity out of nothing, requires zero
                 authority, and the three named apps do the work of any statistic.
               → **A genuinely new hook family. Nothing in `swipe.md`'s fourteen covers it.**

               ⚠️ **AND THEN THE SECOND SENTENCE, WHICH IS THE REAL DEVICE:**
                 "**अगर तुम खुद का mobile app vibe code करने जा रहे हो, तो कैसे बिना app review
                  करवाए अपने changes user के device पर push कर सकते हो?**"
                 ("and if you're going to vibe-code your own mobile app — how do you push your
                   changes to a user's device without going through app review?")

               → 🔴 **NAME IT: THE TWO-QUESTION OPEN.**
                 **Q1 is BROAD** — anyone who uses Instagram qualifies. It buys the scroll.
                 **Q2 is PRACTITIONER** — only someone building an app qualifies. It buys the
                 save, the follow and the relevance.
                 **He gets both awareness levels in two sentences, and he does not have to
                 choose.**
               → **THIS DIRECTLY ANSWERS AN OPEN PROBLEM IN `swipe.md`.** Step 5 of this skill
                 and `niche.md`'s Koe note both say: *broad openings travel, practitioner
                 openings convert, and Shubham cannot afford a practitioner opening yet.*
                 **The two-question open means he does not have to pick one.** Broad question
                 first, then the same thing pointed at what the reader is building.

INTRO          context ✅ (Q1) · common belief ✅ (implicit: apps update through the store)
               contrarian ✅ ("it isn't always OTA… sometimes Remote Config, sometimes
                             Server-Driven UI") · proof ✗ — **none, and none needed: he simply
                             knows the material and it shows within twenty seconds**
               plan ~ ("बहुत सारे तरीकों में से एक तरीका होता है OTA")
               → FOUR OF FIVE.

BODY           a genuine lesson, in five beats:
                 1  the two layers — JavaScript on top, the binary/native layer underneath
                 2  what can be pushed OTA — JS bundles, assets, fonts, images, styling
                 3  ⭐ **THE SAME EXAMPLE, TWICE, WITH ONE VARIABLE CHANGED:**
                    "मान लो तुम्हारे app में एक button था — click करने पर दूसरी screen खुलनी
                     चाहिए थी, पर work नहीं कर रहा — तो तुम OTA update से bug fix करा सकते हो।
                     **अगर वही button** native चीज़ों से interact कर रहा होता — click करने पर
                     **camera खुलना चाहिए था**, या **audio record होना चाहिए था** — तो उसके लिए
                     तुम्हें नया build बनाना पड़ता है जिसको app store review करता है।"
                    → **NAME IT: THE SAME EXAMPLE, ONE VARIABLE CHANGED.** Same button. Case A
                      opens a screen → OTA works. Case B opens the camera → needs a build.
                      **This is how you teach a BOUNDARY**, and it is the clearest single
                      teaching move in thirty-one scripts. The reader now owns the rule, not
                      the fact.
                 4  the mechanism end to end — server builds a new JS bundle and a manifest →
                    app launches → checks the manifest → downloads → verifies and caches
                    locally → shows on next reboot
                 5  the alternatives named — server-driven UI, feature flagging, remote configs
               verdict: **ESCALATING and genuinely instructional.**

VALUE LOOP     what 5/5 · **how 5/5** · why 4/5
               → **The only script in thirty-one to score 4+ on all three.**
                 `_roshnichellani` #11 is the only other one close.

REHOOKS        the boundary example is the retention — the viewer waits to learn where the
               line falls. **No verbal seam lines.**

OUTRO          ⭐ **"तो तुम्हारे दिमाग में खुराफाती idea है कि मैं पूरा का पूरा app ही क्यों ना
               OTA update करा दूँ — **but please avoid that**, क्योंकि अगर तुमने कोई गलत bug
               push कर दिया तो next time जब भी user app खोलेगा, सब affect होने वाले हैं।
               तो only try to ship small bugs and fixes."**
               → 🔴 **NAME IT: THE ANTICIPATED MISUSE.** He predicts the clever-but-wrong thing
                 the reader is *about to go and do* with what he just taught, and heads it off.
                 **This is not the pre-emptive objection** (which answers a doubt about the
                 claim). **It answers the reader's next ACTION.**
               → **Cousin of the anti-lazy instruction** (`developer_mannjadwani`, `socialmasla`)
                 — same family: *cost yourself something to make the reader competent.*
               then: "save कर लो future के लिए, दोस्त के साथ share कर दो, page follow कर लो.
               **I'll see you in the next one.**"
               → **NO GATE.** Save, share, follow. Nothing withheld.

NATIVE EMBED   NONE — nothing is sold. **Second script in thirty-one with no offer at all**
               (the other is `_roshnichellani` #11).

E vs R         **BEAT at the two-question open, and beaten again at the boundary example** —
               the viewer expected an explanation and received a rule they can apply.

WHAT TO STEAL  1. 🔴 **THE TWO-QUESTION OPEN.** Broad question, then the same thing pointed at
                  what the reader is building. **Both awareness levels, two sentences.**
               2. 🔴 **THE UNNOTICED THING.** Open on something that happens to the reader
                  constantly and that they have never questioned. Name three products they use.
               3. 🔴 **THE SAME EXAMPLE, ONE VARIABLE CHANGED.** How to teach a boundary.
               4. **THE ANTICIPATED MISUSE.** "You're about to think X. Don't, and here's why."
WHAT TO DROP   Nothing. **⚠️ At 450 words this is the longest script in the project and it is
               his best post on likes — which sits directly against `theautomationguy.ai` #6
               (55 words, 25.55x). Length is not the variable. Density is.**
```

---

## ── SCRIPT #8 · 2.48x / 2.41x · ~180 words ── ⚠️ transcript ends mid-word

```
PACKAGING      caption: "Share your portfolio with others in the comment section 🙌 and take
                        inspiration from others and make [one]"
               → ⚠️ **THE CAPTION IS NOT AN ASK FOR ATTENTION. IT IS AN ASK FOR THEIR WORK.**

CLICK CONFIRM  "**तुम्हें खुद शर्म आ जाएगी** जब तुम comment में बाकी लोगों की portfolio website
                देखोगे और तुमने अभी तक portfolio website नहीं बनाई है।"
               ("you'll be ashamed of yourself when you see everyone else's portfolio websites
                 in the comments and you still haven't built one")
               confirms ✅ · beats ✅
               → **NAME IT: THE PEER-COMPARISON SHAME.** The pressure does not come from him —
                 **it comes from the comment section**, which he is simultaneously creating.
               → ⚠️ **FLAGGED, NOT RECOMMENDED.** It works: 501 comments, his highest, and
                 they are real. **But `voice.md` and `niche.md` do not run on making the reader
                 feel bad**, and an engineering audience at 1.5 years will read shame as
                 posturing. **The mechanic below is the part worth taking; the shame is not.**

INTRO          context ✅ · common belief ✅ (you should have a portfolio — universally agreed
               and universally ignored) · contrarian ✗ · proof ✗ · plan ✅ ("मैं तुम्हें एक
               idea देता हूँ") → THREE OF FIVE.

BODY           ⭐ **A BUILD SPEC, given away in the reel:**
                 "portfolio पर अपने बारे में बताना है वो तो डाल ही दो — **plus एक ChatGPT जैसा
                  interface बनाओ, एक text area दो एकदम centre में**, जहाँ कोई भी आएगा और पूछेगा
                  'ये बंदा क्या करता है, कितना experience है, कौन से projects बनाए हैं' — कोई भी
                  LLM API use कर सकते हो, **but कुछ random stuff throw नहीं करना चाहिए** — वो
                  सिर्फ तुम्हारे बारे में detail बताएगा।"
               → 🔴 **NAME IT: THE BUILDABLE SPEC.** Not a resource, not a link — **an idea
                 specific enough that the reader could start this evening**, including the
                 constraint that makes it not-terrible ("it must not hallucinate about you").
               → **This is what a ring-1 post looks like when the thing handed over is an IDEA
                 rather than somebody else's tool.** It requires no repo, no affiliate, no
                 curation — and it sidesteps `swipe.md`'s **curator-only** rejection entirely.
               ⚠️ transcript ends mid-word. The close is not recoverable.

VALUE LOOP     what 3/3 · how 2/3 · why 1/3

OUTRO          ⚠️ not recoverable from the transcript. The CAPTION carries the real close:
               **"Share your portfolio with others in the comment section and take inspiration
               from others."**
               → 🔴 **NAME IT: THE PEER SHOWCASE.** He asks the audience to post **their own
                 work**, not to request his. **The comment section becomes the resource.**
               → **501 comments — the most on his account — and NOT ONE of them is gate bait.**
                 Compare `projectonepercent01` #8: 3 likes, 597 comments. **Same order of
                 comment volume, opposite kind of comment.**
               → **And he runs it repeatedly:** control post #6, *"We're reviewing some
                 developer portfolio websites 👀"*, 1.23x with 331 comments. **2 of his top 4
                 posts are peer-showcase formats.**

E vs R         BEAT — but by an uncomfortable route.

WHAT TO STEAL  1. 🔴 **THE PEER SHOWCASE.** Ask the reader to post their work. The comment
                  section becomes the value, the comments are real, and **nothing is withheld
                  to get them.** ⚠️ Needs *some* audience — but far less than a gate does,
                  because the reward is other people's work, not yours.
               2. 🔴 **THE BUILDABLE SPEC.** Hand over an idea specific enough to start today,
                  including the one constraint that makes it good.
WHAT TO DROP   ⚠️ **The shame frame.** Take the peer showcase; drop "तुम्हें शर्म आ जाएगी".
               The same post works as *"post yours below and take a look at what everyone
               else has built"* — which is what the caption already says.
```

---

## ── CAPTIONS ──

| # | words | JOB | CTA | gate |
|---|---|---|---|---|
| #10 | ~110 | **THE ARGUMENT** — real technical detail, incl. the exact native-change list | "save + share" | **none** |
| #8 | ~18 | **THE INVITATION** — asks for the reader's work | "share yours" | **none** |

> **#8's caption is a SIXTH caption job, and it is new: THE INVITATION.**
> argument · list · shelf · gate · title/nothing · **invitation.**
> The first five ask the reader to *take* something. **This one asks them to give.**

**Control captions #5, #7, #11, #12 are 100+ word technical arguments with no CTA at all** —
*"API cancellation = stopping a request that's no longer needed. It prevents race conditions,
saves b[andwidth]…"*. **This account writes to be read, not to be harvested.**
→ **Third account whose captions would survive as LinkedIn posts unedited**
(`nick_saraev`, `_roshnichellani`, **this one**) — and the only one of the three that teaches.

---

## ── ACROSS THESE TWO SCRIPTS ──

```
context        ✅✅
common belief  ✅✅   2 of 2 — always something universally agreed and universally ignored
plan           ~✅
contrarian     ✅✗
proof          ✗✗    NEVER. He proves nothing and demonstrates competence instead.
```

**What both do the same:** open on the reader's own situation · no gate, no DM, no funnel ·
a save/share/follow close · **`how` scores 5/5 and 2/3 — he is the second-most instructional
account after `developer_mannjadwani`, and unlike him he also scores on `why`.**

> ### THE FINDING: HE PROVES NOTHING AND IT DOES NOT COST HIM.
>
> Thirty-one scripts in, every other winning account leans on proof — an artifact
> (`forseth.ai`), a screen (`developer_mannjadwani`), a borrowed name (`jasoncooperson`,
> `_roshnichellani`), strangers' reviews (`socialmasla`), a personal discovery (`techie007.dev`).
>
> **`saban.talks` has none of it. He just knows the material, and twenty seconds in it is
> obvious.** *"The JavaScript layer sits on top of the binary layer"* cannot be faked, and a
> reader who builds apps knows that instantly.
>
> 🔴 **THIS IS THE MOST DIRECTLY USABLE FINDING ON THE WATCHLIST FOR SHUBHAM'S ACTUAL POSITION.**
> `niche.md` records the authority problem precisely: capability real, independent client
> evidence pending, **and content must not claim what has not been delivered.**
> **Demonstrated competence is not a claim.** Explaining a boundary correctly — what OTA can
> and cannot push, and why — **proves the thing without asserting it**, and it is available on
> day twenty-seven with zero followers, zero clients and zero artifacts.
>
> **`handles.md` parked him for a flat 2.5x. On the question of how to have authority without
> a track record, he is the most valuable account in the project.**

---

## ── PROMOTION NOTES ──

| candidate | status |
|---|---|
| 🔴 **THE TWO-QUESTION OPEN** | ⚠️ 1 of 2, one account. **Solves the broad-vs-practitioner problem `swipe.md` and `niche.md` both leave open. Flag hard.** |
| 🔴 **THE UNNOTICED THING** | ⚠️ 1 of 2. **A hook family none of the 14 in `swipe.md` covers.** |
| 🔴 **THE SAME EXAMPLE, ONE VARIABLE CHANGED** | ⚠️ 1 of 2. **The clearest teaching move in 31 scripts.** |
| 🔴 **THE PEER SHOWCASE** | ⚠️ 2 of his top 4 posts. **Real comments, no gate, no withholding. Directly relevant to the gate question.** |
| 🔴 **THE BUILDABLE SPEC** | ⚠️ 1 of 2. **Sidesteps the curator-only rejection.** |
| **THE ANTICIPATED MISUSE** | ✅ **anti-lazy family, third account** (`developer_mannjadwani`, `socialmasla`). **Clears.** |
| **DEMONSTRATED COMPETENCE INSTEAD OF PROOF** | ⚠️ 2 of 2, one account. **The authority answer for 1.5 years. Flag hard.** |
| **THE ARGUMENT CAPTION** | ✅ **third account.** LinkedIn-relevant. |
| **THE PEER-COMPARISON SHAME** | ⚠️ **Works — 501 real comments. FLAGGED AGAINST `voice.md`. Take the showcase, drop the shame.** |
| **No gate, 2 of 2, at 2.5x organic** | ⚠️ **Third account running zero gates** (`socialmasla`, `techie007.dev`). |
