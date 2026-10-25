# text-widgets

Compact, zero-dependency text widgets for AI agents living in chat (Slack, Telegram, Discord, Cursor, Claude Code, Grok Bot).

Chat columns are about 52 characters wide. A prose summary of a bot fleet or a ticket queue becomes a wall of text. **text-widgets** gives agents a compact monospace grammar for that column: status strips, action cards, queue breakdowns, receipts, progress bars, heatmaps, and boss bars. Keep each line inside a widget at 46 characters or fewer. Count each emoji as 2 characters.

## Quick Preview

```
🤖 24 bots · ⏱ 9 on · ⏸ 2 · ❗ 1 urgent
📥 0 unowned · 🔥 6 stale · 📋 18 open

┌ #1 Acme Billing Cutoff ───── 🔴 4h
│ Verify webhook cert + deploy v2.4
│ (API-104) & 3 env keys (OPS-118)
│ → Verify cert; hand OPS-118 to Alex
└────────────────────────────────────

───── OPEN QUEUE BY OWNER & AGE ─────
Alex     ▓▓▓▓▓▓░░░░ 12 open · 4 >7d
Sam      ▓▓▓▓▓▓░░░░ 13 open ·reassgn
Jordan   ▓▓▓▓░░░░░░  8 open · 1 >7d
Taylor   ▓▓▓░░░░░░░  6 open · 2 >7d
Casey    ▓▓░░░░░░░░  4 open · 0 >7d
─────────────────────────────────────

───── NEXT UP · Sun 25 Oct 16:00 ────
1. API-104      🟡 10m · retry webhook
2. Auth Upgrade 🟡 2d  · 2 role scopes
3. OPS-118      🟡 5d  · billing sync
4. Portal SSO   🟡 5d  · filter rule
5. SUP-309      🟡 6d  · invoice export
✔ Done: cert · #82 · staging · docs
─────────────────────────────────────
```

[API-104](https://example.com/tickets/API-104) · [OPS-118](https://example.com/tickets/OPS-118) · [SUP-309](https://example.com/tickets/SUP-309) · [#82](https://example.com/pull/82)

For a queue of 20 or more rows, send this summary in chat and put the full table on a Page/Canvas: [Open the full queue](https://example.com/canvas/queue).

## Install as an Agent Skill

Copy `SKILL.md` into your agent's skill directory:

```bash
mkdir -p ~/.agents/skills/text-widgets
curl -sL https://raw.githubusercontent.com/reemazyb/text-widgets/main/SKILL.md \
  -o ~/.agents/skills/text-widgets/SKILL.md
```

Works with any [agentskills.io](https://agentskills.io)-compatible runtime.

## Included Widgets

| Widget | Best for |
| :--- | :--- |
| **Status strip** | Fleet or queue counts at a glance |
| **Action / Decision Card** | A ticket, blocker, or bot that needs a decision |
| **Queue / Backlog Breakdown** | Open work grouped by owner, with age |
| **Compact Queue Receipt** | A numbered priority list that stays inside the column |
| **Progress bar** | Pomodoro timers, long-running jobs, migration progress |
| **Heatmap** | Weekly or monthly habits, SLA compliance, commit streaks |
| **Garden / streak** | Focus blocks (`🍅`) and daily streaks (`🔥`) |
| **Boss bar** | An epic, migration, or bug backlog |
| **Timeline** | A daily schedule or an incident sequence |

## Design Rules

1. **46 characters per line.** Inside a code block, count each emoji as 2 characters. A chat column is about 52 characters wide. If a detail does not fit, wrap it across 2–3 short lines inside the card.
2. **3–10 lines.** Send one widget per message. You can combine a status strip with 2–3 cards or a queue receipt.
3. **16–20 cell bars.** `filled = round(pct / 5)` using `▓` and `░`.
4. **Real data only.** Use numbers from a tool, a file, or the user. Do not invent progress, counts, or badges.
5. **Links sit under the block.** A link inside a code block is not clickable. When the widget names a ticket, pull request, thread, or page, put one compact markdown links line immediately below the fence.
6. **Wide tables go on a Page/Canvas.** For 20 or more rows, or for wide multi-column detail, send the status strip, top action cards, and backlog breakdown in chat. Put the full filterable table on a full-width Page/Canvas and link it under the widget.
7. **Choice buttons for decisions.** Offer 2–4 short options so the reader taps instead of typing a command.

## Prior Art & Credits

Inspired by [Scannable Reports](https://clawhub.ai/rmarji/skills/scannable-reports), [OrchestKit glyph](https://github.com/yonatangross/orchestkit), [wascii](https://github.com/leonardocandiani/wascii), and [MCP-UI](https://github.com/MCP-UI-Org/mcp-ui).

## License

MIT © [Reemaz Baig](https://reemazyb.com)
