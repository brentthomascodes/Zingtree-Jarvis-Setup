# Jarvis — AI Workspace for Claude Cowork

## Setup (30 minutes)

1. Connect **Gmail, Slack, Google Calendar** in Cowork → Settings → Connectors
2. Grab your **Slack User ID** (your profile → More → Copy member ID)
3. Open the **[Jarvis Setup Guide](./Jarvis%20Setup%20Guide.md)** — copy each step's prompt, paste it into a new Cowork task, run it in order
4. When done: Cowork → Settings → **Default Task Context** → select your **Jarvis** folder

That's it. Every new task now loads with full context automatically.

---

## Why it's worth the 30 minutes

- **No re-explaining yourself** — Jarvis knows your role, accounts, and preferences from session one
- **Drafts in your voice** — extracted from your actual sent emails, updated monthly
- **Persistent memory** — say "remember this" and it's logged; no manual notes
- **Account tracking** — every customer gets its own sub-workspace that builds context over time
- **Proactive briefings** — 7am Slack DM surfacing what needs attention before you open your inbox

---

## How it works

```
Jarvis/
├── CLAUDE.md            ← Your rules, routing map, preferences
├── MEMORY.md            ← Facts, decisions, active projects
├── 00_Resources/
│   └── voice-principles.md
├── Email HQ/
├── Account Management HQ/
└── Workstation Factory/
```

Jarvis is a folder that lives inside Cowork. When you open a task with Jarvis selected as your default context, the AI reads your CLAUDE.md and MEMORY.md automatically — so it already knows who you are, how you work, and what's going on.

Your CLAUDE.md has a routing map: when you mention an account, it loads Account Management HQ. When you need to draft an email, it loads Email HQ. New workstations can be scaffolded on demand via Workstation Factory.

**To use it:** open a new Cowork task (Jarvis folder selected), describe what you need, and go. Keep tasks short and focused — Jarvis is the context, not the thread.

---

Questions? [brent@zingtree.com](mailto:brent@zingtree.com)
