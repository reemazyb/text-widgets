---
name: text-widgets
description: >-
  Use when an AI agent or bot should show status, queues, progress, streaks, a
  timer, a dashboard, or summary cards in chat using compact monospace
  box-drawing text widgets (≤46 chars wide, paired with clickable links below).
---
# Text Widgets

Chat UIs show text, images, files, and choice buttons—not live HTML widgets. Draw widgets in monospace text instead, and send a fresh block on each update.

## Core Rules
- Wrap box-drawing and aligned widgets in a ```fenced code block``` so monospace alignment holds across desktop and mobile.
- **Hard width limit: ≤ 46 characters per line** inside code blocks (counting emojis as 2 chars). Chat bubbles sit in a narrow centered column (~52 chars wide), so anything wider clips on the right. Wrap details across 2–3 short lines inside a card instead of making wide rows.
- Keep each widget to 3–10 lines. Send one widget per message unless combining a top status strip with 2–3 cards or a queue receipt.
- Use only real numbers from a tool, file, or user input. Never invent progress or metrics.
- **Clickable links**: Links inside ```code blocks``` are not clickable. Whenever a widget names tickets, PRs, threads, or pages, put a compact clickable markdown links line immediately below the code block.
- **When to pair with a full-width Page/Canvas**: When a queue has many rows or wide multi-column details (e.g., 20+ open tickets with summaries, owners, staleness, and actions), render the high-level **Status strip + Top Action Cards + Backlog Breakdown** as Text Widgets in chat, and put the full filterable table on a full-width Page/Canvas.
- Pair interactive decisions with native choice buttons (2–4 short options) so the user taps instead of typing commands.
- Percent bars are 16–20 cells wide: `filled = round(pct / 5)` of `▓`, remainder `░`.

## Widget Library (all ≤ 46 chars wide)

**Status strip** (fleet or queue counts at a glance)
```
🤖 24 bots · ⏱ 9 on · ⏸ 2 · ❗ 1 urgent
📥 0 unowned · 🔥 6 stale · 📋 18 open
```

**Action / Decision Card** (ticket, blocker, or bot needing a decision)
```
┌ #1 Acme Billing Cutoff ───── 🔴 4h
│ Verify webhook cert + deploy v2.4
│ (API-104) & 3 env keys (OPS-118)
│ → Verify cert; hand OPS-118 to Alex
└────────────────────────────────────
```
Badges: `🟢 healthy/done` · `🟡 waiting/stale` · `🔴 urgent/critical` · `⚪ on demand`

**Queue / Backlog Breakdown** (grouped counts + staleness bars)
```
───── OPEN QUEUE BY OWNER & AGE ─────
Alex     ▓▓▓▓▓▓░░░░ 12 open · 4 >7d
Sam      ▓▓▓▓▓▓░░░░ 13 open ·reassgn
Jordan   ▓▓▓▓░░░░░░  8 open · 1 >7d
Taylor   ▓▓▓░░░░░░░  6 open · 2 >7d
Casey    ▓▓░░░░░░░░  4 open · 0 >7d
─────────────────────────────────────
```

**Compact Queue Receipt** (numbered priority list that never clips)
```
───── NEXT UP · Sun 25 Oct 16:00 ────
1. API-104      🟡 10m · retry webhook
2. Auth Upgrade 🟡 2d  · 2 role scopes
3. OPS-118      🟡 5d  · billing sync
4. Portal SSO   🟡 5d  · filter rule
5. SUP-309      🟡 6d  · invoice export
✔ Done: cert · #82 · staging · docs
─────────────────────────────────────
```

**Progress bar**
```
🍅 FOCUS 2/4 · API schema migration
▓▓▓▓▓▓▓▓▓▓▓░░░░░░░░░ 55% · 11m left
```

**Heatmap** (weekly or monthly activity)
```
     S  M  T  W  T
wk1 🟩 🟩 🟨 ⬜ 🟩
wk2 🟩 🟩 🟩 🟩 🟨
```
Legend: `🟩 good` · `🟨 partial` · `⬜ none` · `🟥 missed`

**Garden / streak** (habits that build over time)
```
🍅🍅🍅🥀🍅🍅   streak 🔥2
```
Legend: `🍅 done` · `🥀 skipped` · `🌱 in progress`

**Boss bar** (large milestone or backlog epic chipped away)
```
👾 EPIC-402 ▓▓▓░░░░░░░░░░░░░ 15% · 3 left
```

**Timeline**
```
08:30 ●── morning digest
10:00 ●── deep work 🍅🍅
13:00 ○── code review
```

## Steps
1. Pick the smallest widget combination that answers the user's question (e.g., Status strip + Decision Cards + Backlog Breakdown).
2. Keep every code-block line ≤ 46 characters so it never clips inside the chat column.
3. Populate strictly from verified state.
4. Put clickable markdown links (and a full-width Page/Canvas link when applicable) on one compact line right under the widget, followed by optional choice buttons.
