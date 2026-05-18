<!--
  ╔══════════════════════════════════════════════════════════════╗
  ║                        CLEARDESK                            ║
  ║         When everything feels urgent,                       ║
  ║              one thing is actually next.                    ║
  ╚══════════════════════════════════════════════════════════════╝
-->

<div align="center">

<br/>

```
╔═══════════════════════════════════════╗
║                                       ║
║           C L E A R D E S K          ║
║                                       ║
║   When everything feels urgent,       ║
║   one thing is actually next.         ║
║                                       ║
╚═══════════════════════════════════════╝
```

<br/>

[![Live App](https://img.shields.io/badge/LIVE%20APP-Open%20ClearDesk-%237c3aed?style=for-the-badge&labelColor=06060f)](https://yourname.github.io/cleardesk)
[![License](https://img.shields.io/badge/LICENSE-MIT-10b981?style=for-the-badge&labelColor=06060f)](LICENSE)
[![Stack](https://img.shields.io/badge/STACK-Vanilla%20HTML%2FJS-%234f46e5?style=for-the-badge&labelColor=06060f)](index.html)
[![Zero Dependencies](https://img.shields.io/badge/DEPS-Zero-f59e0b?style=for-the-badge&labelColor=06060f)](#)

<br/>

</div>

---

## The Problem

> A student sits down to study.  
> Their brain holds **15 things at once.**  
> Three chapters unread. Two assignments due. Mock tomorrow.  
> Every item feels equally urgent.  
> They don't know where to start.  
> They open YouTube instead.  
> **40 minutes gone.**  
> They feel worse. This repeats every single day during exam season.

This is not a time management problem.

**It is a clarity problem.**

The student has the material. They don't have a system that strips the noise and tells them: *right now, do exactly this one thing.*

---

## What ClearDesk Does

```
┌─────────────────────────────────────────────────────────┐
│                                                         │
│  01  →  Dump everything in your head. One line each.   │
│                                                         │
│  02  →  Hit "Clear My Desk"                            │
│                                                         │
│  03  →  App scores each item on 3 silent axes          │
│         · Exam relevance                               │
│         · Time sensitivity                             │
│         · Actionability right now                      │
│                                                         │
│  04  →  ONE thing surfaces. One calm sentence: why.    │
│                                                         │
│  05  →  Timer starts. You work. You mark it done.      │
│                                                         │
│  06  →  Next item surfaces. Repeat until desk = clear. │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

---

## Why Nothing Else Solves This

| Tool | Why it fails |
|---|---|
| **Todo apps** | Multiply the overwhelm — more items, more decisions |
| **Pomodoro timers** | Assume you already know what to work on |
| **Notion** | Setup overhead when you're already paralysed |
| **Journaling** | Slow and narrative — this needs fast and decisive |
| **ChatGPT** | Requires prompting — cognitive load the student doesn't have |
| **ClearDesk** | ✦ Takes the noise. Returns one thing. |

---

## Priority Scoring Engine

Client-side only. No API. No data leaves your browser.

```
Priority Score = (exam_relevance × 1.5) + (time_sensitivity × 1.2) + actionability
```

```
EXAM RELEVANCE  (0 → 3)
────────────────────────────────────────────────────────────
chapter · topic · revision · mock · exam · study        →  3
assignment · submit · deadline · due · paper            →  2
email · message · reply · call · person                 →  1
everything else                                         →  0

TIME SENSITIVITY  (0 → 3)
────────────────────────────────────────────────────────────
today · tonight · tomorrow · urgent · asap · now        →  3
this week · soon · by [day]                             →  2
someday · later · eventually · next week                →  0
default (no keyword)                                    →  1

ACTIONABILITY  (0 → 3)
────────────────────────────────────────────────────────────
< 8 words                                               →  3
8 – 15 words                                            →  2
> 15 words · "figure out" · "think about"               →  1
```

**Reason sentence logic:**
- `exam_relevance = 3` → *"This directly affects your exam. Everything else can wait."*
- `time_sensitivity = 3, exam_relevance = 2` → *"This is due soon and still unfinished. Handle it first."*
- `actionability = 3` → *"This is concrete and doable right now. Start here."*
- default → *"Your brain flagged this most. Trust it."*

---

## Features

```
✦  Brain Dump        Free-form input. No structure required. Just write.
✦  Priority Engine   3-axis scoring. Silent. Client-side. Instant.
✦  One Thing         Single next action + one calm reason sentence.
✦  Focus Timer       SVG ring. 15 / 25 / 45 min presets. ±5 min nudge.
✦  Queue Panel       Ranked remainder. Colour-coded. Collapsible.
✦  Session Memory    localStorage. Resumes on reload. No account needed.
✦  Done State        Desk cleared. Count shown. Clean exit.
```

---

## Timer Controls

```
Before start:
  [ −5 ]  [ 15 min ]  [ 25 min ]  [ 45 min ]  [ +5 ]
              ↑ presets    ↑ default    ↑ nudges ↑

During countdown:
  [ ⏸ Pause ]  [ ↺ Reset ]

On completion:
  [ ✓ Finished it ]  [ → Need more time ]
```

Nudge buttons clamp between **5 min floor** and **90 min ceiling.**  
No audio. Visual-only — avoids mobile permission prompts.

---

## Stack

```
index.html
├── HTML            structure
├── CSS             dark glass design system (inline)
│   ├── Layered backdrop-filter blur + noise grain texture
│   ├── SVG timer ring with gradient stroke + pulse animation
│   ├── Glass card system  ·  base + elevated variants
│   ├── Button system  ·  primary · secondary · done states
│   └── Staggered reveal · slide transitions · shimmer sweep
└── JS              vanilla · no framework · no bundler
    ├── Priority scoring engine (3-axis, keyword-based)
    ├── Placeholder cycling (3 strings, 4s fade interval)
    ├── Timer (SVG ring progress + setInterval countdown)
    ├── Queue renderer (ranked · colour-coded · collapsible)
    └── localStorage session persistence (resume on reload)

Fonts → DM Serif Display · Outfit  via Google Fonts CDN
Deps  → zero
Size  → single file
```

---

## Deploy

**GitHub Pages — under 2 minutes**

```
1.  github.com/new  →  public repo  →  create
2.  Upload index.html to root
3.  Settings → Pages → Deploy from branch → main → / (root)
4.  Live at:  https://[you].github.io/[repo]/
```

**Play Store — browser-based via PWABuilder**

```
1.  pwabuilder.com
2.  Paste your GitHub Pages URL
3.  Build → Android → Download .aab
4.  Upload to Google Play Console
```

---

## Who It's For

```
· CA / CFA / CPA aspirant  —  2 weeks from a high-stakes exam
· University student        —  6 things due, zero clarity on which matters first
· Anyone who has ever       —  opened a productivity app and felt more overwhelmed
```

Zero learning curve. Open the app. See a text box and a button. That is the entire interface on load.

---

## File Structure

```
cleardesk/
├── index.html      ←  the entire app. self-contained.
├── README.md       ←  this file
└── LAUNCH.md       ←  pre-ship checklist + deploy steps
```

---

## License

```
MIT — use it · fork it · ship it · build on it
No attribution required. No strings attached.
```

---

<div align="center">

<br/>

```
╔══════════════════════════════════╗
║                                  ║
║   Desk cleared.                  ║
║   Come back when the             ║
║   noise starts again.            ║
║                                  ║
╚══════════════════════════════════╝
```

<br/>

*Built for students who have everything they need except clarity.*

<br/>

</div>
