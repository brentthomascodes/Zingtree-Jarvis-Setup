# Jarvis — Your Personal AI Workspace for Claude Cowork

Jarvis is a structured AI workspace built on top of [Claude Cowork](https://claude.ai). It gives you a persistent, context-aware assistant that knows your voice, tracks your accounts, briefs you every morning, and routes every task to the right place — automatically.

This repo contains the complete setup guide to get your own Jarvis running in about 30 minutes.

---

## What Is Jarvis?

Jarvis is not a single prompt. It's a folder-based system that lives inside Claude Cowork and gives the AI persistent memory, a voice profile trained on your actual writing, dedicated workstations for different types of work, and background automations that run without you asking.

Every piece of context Jarvis needs is stored in files — CLAUDE.md (rules and routing), MEMORY.md (facts, decisions, contacts), and voice-principles.md (your writing style). When you open a new task with the Jarvis folder selected, the AI reads those files automatically and picks up exactly where you left off.

---

## How It Works

```
Jarvis/
├── CLAUDE.md               ← Rules, routing map, preferences
├── MEMORY.md               ← Facts, decisions, active projects
├── 00_Resources/
│   └── voice-principles.md ← Your writing style, extracted from Gmail
├── Email HQ/               ← Drafts, replies, thread management
├── Account Management HQ/  ← One sub-workspace per customer account
│   └── Acme HQ/
│       ├── CLAUDE.md
│       └── MEMORY.md
├── Workstation Factory/    ← Scaffolds new workstations on demand
└── Scheduled/              ← Background automation skill files
```

**The routing engine** — Jarvis reads your request, checks the Routing Map in CLAUDE.md, and loads the right workstation's context before responding. Email → Email HQ. Anything mentioning a company or person → Account Management HQ (creates a sub-workspace on the spot if none exists).

**Memory** — Say "remember this" at any point and Jarvis logs it to the correct MEMORY.md with a timestamp. No manual notes.

**Voice** — Your voice profile is extracted from your actual sent emails and updated monthly. Drafts sound like you, not like an AI.

**Automations** — Four scheduled tasks run in the background: a morning briefing (Slack DM at 7am), twice-daily account syncs, an hourly sweep, and a monthly voice refresh.

---

## Benefits

**For individuals**
- Start every task with full context — no re-explaining who you are or what you're working on
- Drafts in your voice, not generic AI prose
- Every customer account has its own memory that builds over time
- Morning briefing surfaces what needs attention before you open your inbox

**For teams**
- Shareable setup — anyone at your org can run this guide and have a Jarvis tuned to their role in 30 minutes
- Consistent account tracking across team members
- Workstation Factory makes it easy to add new specialized assistants as your workflow evolves

**vs. using Claude with no setup**
| Without Jarvis | With Jarvis |
| :---- | :---- |
| Re-explain context every session | Context loads automatically |
| Generic AI tone in drafts | Writes in your voice |
| No memory between sessions | MEMORY.md persists everything |
| Manual account tracking | Sub-workspaces with full history |
| No proactive briefings | 7am Slack briefing, daily |
| One-size-fits-all responses | Routed to the right workstation |

---

## Getting Started

### Prerequisites

Before running any setup step, connect these in Cowork **Settings → Connectors**:

| Connector | Required for |
| :---- | :---- |
| Gmail | Morning briefing, voice extraction, account sync |
| Slack | All automations and briefings |
| Google Calendar | Morning briefing |
| Google Drive | Optional, recommended |

You'll also need your **Slack User ID** — find it in Slack under your profile → "More" → "Copy member ID". It looks like `U08XXXXXXXX`.

### Setup Steps

Open the **[Jarvis Setup Guide](./Jarvis%20Setup%20Guide.md)** and run each step as its own Cowork task, in order:

| Step | What it builds | Time |
| :---- | :---- | :---- |
| Step 0 | Jarvis root folder + onboarding + live explainer artifact | ~5 min |
| Step 1 | Root workspace files + voice profile from Gmail | ~10 min |
| Step 2 | Email HQ workstation | ~2 min |
| Step 3 | Account Management HQ + first account sub-workspace | ~3 min |
| Step 4 | Workstation Factory | ~2 min |
| Step 5a–d | Four scheduled automations | ~5 min |
| Step 6 | Live account dashboard artifact | ~3 min |

**After setup:** Go to Cowork **Settings → Default Folder**, select your **Jarvis** folder. Every new task will load Jarvis context automatically.

### The Golden Rule

> **Always work with Jarvis in a new task.**
> Select the Jarvis folder. Keep sessions short and focused.
> Long threads = slow, expensive, worse results. Jarvis is the context — not the thread.

---

## Key Commands

Once Jarvis is running, these phrases do the heavy lifting:

| Say this | What happens |
| :---- | :---- |
| `"Remember this: [anything]"` | Logged to MEMORY.md with timestamp |
| `"What's on my plate today?"` | Pulls open items across all accounts |
| `"Prep me for my call with [Name]"` | Reads account context + recent comms |
| `"Create a new account sub-HQ for [Company]"` | Scaffolds a full account workspace |
| `"That doesn't sound like me — update voice-principles.md"` | Corrects your voice profile |
| `"Create a new workstation for [purpose]"` | Routes to Workstation Factory |

---

## Adding Workstations Over Time

Jarvis is designed to grow with you. When you need a new specialized assistant (a hiring pipeline tracker, a content calendar, a legal review workspace), just say:

> "Create a new workstation for [describe what you need]"

Workstation Factory runs an intake, scaffolds the CLAUDE.md and MEMORY.md, and adds it to the routing map.

---

## Automation Schedule

| Task | When | What it does |
| :---- | :---- | :---- |
| Morning briefing | 7am daily | Emails + Slack + calendar → Slack DM |
| Account sync | 6am + 6pm | Scans all accounts → updates MEMORY.md |
| Hourly sweep | Every hour | Lightweight account activity check |
| Voice refresh | 1st of each month | Re-extracts voice patterns from Gmail |

---

## Questions or Issues

This setup was built for the Zingtree team. For questions, reach out to [brent@zingtree.com](mailto:brent@zingtree.com).
