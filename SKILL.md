---
name: text-widgets
description: >-
  Use when an AI agent or bot should show status, progress, streaks, a timer,
  a dashboard, or a summary as a compact visual in chat instead of prose:
  progress bars, status strips, cards, heatmaps, receipts, streak gardens,
  boss bars, leaderboards, and timelines.
---
# Text Widgets

Chat UIs show text, images, files, and choice buttons—not live HTML widgets. Draw widgets in monospace text instead, and send a fresh block on each update.

## Rules
- Wrap box-drawing and aligned widgets in a ```fenced code block``` so monospace alignment holds across desktop and mobile.
- Keep each widget to 3–8 lines. Send one widget per message unless combining a top status strip with 2–3 cards.
- Use only real numbers from a tool, file, or user input. Never invent progress or metrics.
- Below the widget, add at most one sentence of plain prose.
- Pair interactive flows with native choice buttons (2–4 short options) where supported so the user taps instead of typing commands.
- Percent bars are 20 cells wide: `filled = round(pct / 5)` of `▓`, remainder `░`.

## Widget Library

**Progress bar**
```
🍅 FOCUS 2/4 · API schema migration
▓▓▓▓▓▓▓▓▓▓▓░░░░░░░░░  55% · 11 min left
```

**Status strip** (fleet or system counts at a glance)
```
🤖 24 bots · ⏱ 9 routines on · ⏸ 2 paused · 💤 3 idle · ❗ 1 needs you
```

**Card** (single service, bot, or job)
```
┌ Triage Bot ───────────── 🟢 healthy
│ inbound support queue
│ ⏱ weekdays 08:30 · last run 2h ago
└───────────────────────────────────
```
Badges: `🟢 healthy` · `🟡 paused/idle 7+ days` · `🔴 erroring` · `⚪ on demand`

**Heatmap** (weekly or monthly activity)
```
     S  M  T  W  T
wk1 🟩 🟩 🟨 ⬜ 🟩
wk2 🟩 🟩 🟩 🟩 🟨
```
Legend: `🟩 good` · `🟨 partial` · `⬜ none` · `🟥 missed`

**Receipt** (end of a focus block, deploy, or day)
```
───── RECEIPT · Sun 25 Oct ─────
 planned   auth token rotation
 done      ✔ patch · ✔ integration test
 focus     50 min
────────────────────────────────
```

**Garden / streak** (habits that build over time)
```
🍅🍅🍅🥀🍅🍅   streak 🔥2
```
Legend: `🍅 done` · `🥀 skipped` · `🌱 in progress`

**Boss bar** (large milestone or backlog epic chipped away)
```
👾 EPIC-402 ▓▓▓░░░░░░░░░░░░░░░░░ 15% HP · 3 tasks left
```

**Leaderboard / ranked list**
```
1. Inbox Triage   ▓▓▓▓▓▓▓▓ 41 runs
2. Health Checks  ▓▓▓▓▓    26
3. Release Bot    ▓▓▓      14
```

**Timeline**
```
08:30 ●── morning digest
10:00 ●── deep work 🍅🍅
13:00 ○── code review
```

## Steps
1. Pick the smallest widget that answers the user's question.
2. Populate it strictly from verified state.
3. Send the widget, followed by at most one sentence and optional tap-to-act choice buttons.
