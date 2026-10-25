# text-widgets

Compact, zero-dependency text widgets for AI agents living in chat (Slack, Telegram, Discord, Cursor, Claude Code, Grok Bot).

Chat interfaces are great for conversation and terrible for dashboards. When you run a fleet of scheduled agents or track daily work in chat, prose summaries turn into walls of text. **text-widgets** gives agents a strict, scannable visual grammar—status strips, cards, 20-cell progress bars, emoji heatmaps, receipts, and boss bars—that renders cleanly in any monospace code block.

## Quick Preview

```
🤖 24 bots · ⏱ 9 routines on · ⏸ 2 paused · 💤 3 idle · ❗ 1 needs you

┌ Triage Bot ───────────── 🟢 healthy
│ inbound support queue
│ ⏱ weekdays 08:30 · last run 2h ago
└───────────────────────────────────

👾 EPIC-402 ▓▓▓░░░░░░░░░░░░░░░░░ 15% HP · 3 tasks left
```

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
| **Progress bar** | Pomodoro timers, long-running jobs, migration progress |
| **Status strip** | One-line fleet, CI, or queue summary |
| **Card** | Single bot, service, or deployment health |
| **Heatmap** | Weekly/monthly habits, SLA compliance, commit streaks |
| **Receipt** | End-of-session or end-of-day work summary |
| **Garden / streak** | Focus blocks (`🍅`), daily streaks (`🔥`) |
| **Boss bar** | Chipping away at an epic, migration, or bug backlog |
| **Leaderboard** | Top noisy alerts, bot run counts, queue volume |
| **Timeline** | Daily schedule or incident sequence |

## Design Rules

1. **3–8 lines max.** If it scrolls on mobile, it's not a widget.
2. **20-cell bars.** `filled = round(pct / 5)` using `▓` and `░`.
3. **Real data only.** Agents must never hallucinate progress bars or green badges.
4. **One sentence below.** Let the visual carry the status; put actions on native chat buttons.

## Prior Art & Credits

Inspired by [Scannable Reports](https://clawhub.ai/rmarji/skills/scannable-reports), [OrchestKit glyph](https://github.com/yonatangross/orchestkit), [wascii](https://github.com/leonardocandiani/wascii), and [MCP-UI](https://github.com/MCP-UI-Org/mcp-ui).

## License

MIT © [Reemaz Baig](https://reemazyb.com)
