# Claude Cowork — Jarvis Setup Guide
## Get your personal AI assistant running in ~30 minutes

This guide builds your "Jarvis" — a bespoke AI workspace that learns your voice, tracks your accounts, briefs you every morning, and routes every task to the right context automatically.

Everything lives in a root folder called **Jarvis**. All workstations, memory files, automations, and resources are nested inside it.

---

## Before You Start

### Prerequisites
Connect these in Cowork **Settings → Connectors** before running any step:

| Connector | Required for |
| :---- | :---- |
| Gmail | Morning briefing, voice extraction, account sync |
| Slack | All scheduled tasks, briefings, DMs |
| Google Calendar | Morning briefing |
| Google Drive | Optional, recommended |

**Find your Slack User ID:** Slack → your profile → "More" → "Copy member ID". Looks like `U08XXXXXXXX`.

### How to use this guide
> **Always run each step in a new Cowork task.** Jarvis is the context — not the thread. Long threads produce slow, expensive, lower-quality results. One task per step. When you're done with a step, close it and open a new one.

After setup is complete:
1. In Cowork, go to **Settings → Default Folder**
2. Select your **Jarvis** folder
3. Every new task will now start with Jarvis context automatically loaded — no setup required

Anything in `[BRACKETS]` is yours to fill in.

---

## Step 0 — Jarvis Onboarding + Live Explainer

**Paste this in a new Cowork task first.** It creates your live Jarvis dashboard and recommends which workstations to build based on your actual role.

```
None

Do the following in order. Do not skip any part.

---

PART A: CREATE THE JARVIS ROOT FOLDER

Create the following folder and files to establish the Jarvis workspace skeleton.

FILE 1 — Jarvis/CLAUDE.md
# CLAUDE.md

## Memory System
At the start of every session, read MEMORY.md before responding. Be informed by it without announcing it.

When I say "remember this," write the information to MEMORY.md and confirm.

Where things go:
- Does it prescribe behavior? ("always," "never," "before X do Y") → add to CLAUDE.md
- Does it describe a fact that could change? (contacts, decisions, status) → add to MEMORY.md

## Preferences
- Professional but conversational tone. If it sounds like a corporate memo, rewrite it.
- Keep responses under 300 words unless I ask for more.
- Use bullet points for lists, prose for explanations.
- Give one strong recommendation. Don't offer 3 options unless I ask.
- Default to async communication (email, doc, recording) before suggesting a call.

## Rules
- Ask clarifying questions before starting a complex task.
- Match the formality level of the message I'm replying to.
- Before drafting a new email, check if a thread already exists with that recipient.
- If unsure about something, say so. Don't guess.
- Before writing any content on my behalf, read voice-principles.md in Jarvis/00_Resources/.
- Whenever a prompt references a person, organization, or account — even casually — route to Account Management HQ immediately and search for a matching sub-HQ before doing anything else. If a match is found, load that sub-HQ's CLAUDE.md and MEMORY.md and use that context. If no match is found, do not proceed with the original request yet — instead ask the intake questions to set up a new account sub-HQ, confirm the details, create it, then continue.

## Routing Map
| Workstation | Route here when I... |
| :---- | :---- |
| Email HQ | ...need to draft, reply to, or review any email |
| Account Management HQ | ...am working on any customer account |
| Workstation Factory | ...want to create a new workstation of any kind |

## References
| Resource | Read when... |
| :---- | :---- |
| voice-principles.md | Writing any content on my behalf |

## Creating New Workstations
When I ask you to create a new workstation, create a subfolder inside Jarvis/ and add:
1. CLAUDE.md — sections: Identity, Resources, Workflow, Editorial Rules
2. MEMORY.md — sections: Contacts, Key Decisions
3. [Workstation Name] Resources/ — empty folder

After creating, add a row to the Routing Map above.

---

FILE 2 — Jarvis/MEMORY.md
# MEMORY.md
*Last updated: [TODAY'S DATE]*

## Active Projects

## Core Memory
- I work at [COMPANY] as [YOUR ROLE].
- My name is [YOUR NAME] ([YOUR EMAIL]).
- My Slack User ID: [YOUR SLACK USER ID]

---

FILE 3 — Jarvis/00_Resources/voice-principles.md
# Voice Principles
*Scaffold — will be replaced after voice extraction in Step 1.*

## Tone
- Write like a clear, thoughtful colleague talking to a smart friend. Professional but not stiff.
- Be direct. State the key point first, then supporting context.
- If it sounds like a corporate memo or an AI wrote it, rewrite it.

## Sentence Style
- Vary sentence length so paragraphs flow naturally.
- Use connectors like "so," "because," "for example" instead of stacking short fragments.
- Keep paragraphs to 1-3 sentences in emails and written content.

## Words to Avoid
- Never use: "dive into," "game-changing," "straightforward," "leverage," "synergize," "circle back," "touch base"
- No em dashes. Use commas, colons, or periods instead.

## Formatting Defaults
- Bold key points for scannability.
- One idea per paragraph.
- Bullet points for lists, prose for explanations.

---

Confirm each file is created, then proceed to Part B.

---

PART B: ASK ME ONBOARDING QUESTIONS

Before building the live artifact, ask me the following questions one group at a time. Wait for my answers before proceeding.

GROUP 1 — Your Role
1. What is your job title and primary function?
2. What does a typical workday look like for you? Walk me through it.
3. What tools do you use most (email, Slack, CRM, project management, etc.)?

GROUP 2 — Your Work
4. What recurring tasks do you do every day or every week?
5. What are the most time-consuming things you do manually right now?
6. Do you manage external accounts or clients? If so, roughly how many?

GROUP 3 — Your Goals
7. What's the #1 thing you'd want Jarvis to handle for you?
8. Is there anything you're worried about delegating to an AI?

After I answer, do three things:
1. Recommend 3-5 workstations tailored to my role, with a one-sentence reason for each.
2. Note which workstations from the standard set (Email HQ, Account Management HQ, Workstation Factory) apply to me and why.
3. Tell me which scheduled automations make sense for my role.

Then proceed to Part C.

---

PART C: CREATE THE LIVE JARVIS ARTIFACT

Build a live HTML artifact called "jarvis-explainer" with the following structure.

The artifact has three tabs: "How Jarvis Works", "Your Setup", and "Example Usage".

--- TAB 1: HOW JARVIS WORKS ---

This tab is a visual, interactive explainer of the Jarvis system. Build it as a polished HTML page with these sections:

SECTION 1 — THE BRAIN DIAGRAM
An interactive SVG diagram showing how Jarvis works:
- Center node: "Jarvis" (your root folder + CLAUDE.md)
- Branches to: Memory (MEMORY.md), Voice (voice-principles.md), Workstations (Email HQ, Account HQ, etc.), Automations (scheduled tasks)
- Clicking a node reveals a tooltip explaining what that component does
- Use a clean, modern visual style

SECTION 2 — THE GOLDEN RULE (prominent callout box)
"Always work with Jarvis in a new task.
Select the Jarvis folder. Keep it short.
Long threads = slow, expensive, worse results."

SECTION 3 — HOW TO USE IT (3-column card layout)
Card 1 — Start a task: Open Cowork → New Task → select Jarvis folder → describe what you need
Card 2 — Remember something: Say "remember this" → Jarvis logs it to MEMORY.md automatically
Card 3 — Build new workstations: Describe what you need → Workstation Factory scaffolds it

SECTION 4 — YOUR WORKSTATIONS (cards based on my onboarding answers)
One card per recommended workstation. Each card shows: name, what routes there, why it's useful for my role.

--- TAB 2: YOUR SETUP ---

A checklist showing setup progress. Each step has a checkbox (stored in localStorage):
☐ Step 0 — Jarvis folder created + onboarding complete
☐ Step 1 — Root workspace + voice profile built
☐ Step 2 — Email HQ created
☐ Step 3 — Account Management HQ created
☐ Step 4 — Workstation Factory created
☐ Step 5a — Morning briefing scheduled
☐ Step 5b — Account sync scheduled
☐ Step 5c — Hourly sweep scheduled
☐ Step 5d — Voice refresh scheduled
☐ Step 6 — Account dashboard live

Below the checklist: "Set Jarvis as your default folder" with instructions.

--- TAB 3: EXAMPLE USAGE ---

This tab shows real, end-to-end examples of how to use Jarvis. Use a card-based layout where clicking a card expands the full example.

Include these 8 examples:

EXAMPLE 1 — Morning Briefing
Scenario: You start your day and want to know what needs attention.
What Jarvis does automatically: At 7am, scans your email and Slack, summarizes customer activity, lists today's calendar, and DMs you in Slack.
What you'd see: [Show a realistic mock Slack DM with formatted briefing output]
Manual equivalent: 20-30 minutes scanning email + Slack yourself

EXAMPLE 2 — Draft a Client Email
Scenario: A client emailed asking for a project status update.
Prompt to use: "Draft a reply to Sarah at Acme. She's asking for a status update on the Q3 integration project. We're on track, delayed on the API docs."
What Jarvis does: Routes to Email HQ → reads voice-principles.md → checks thread history → drafts a reply in your voice
What you get: A ready-to-review draft, matched to formality of original message

EXAMPLE 3 — Log an Account Update
Scenario: You just got off a call and learned a client is expanding their contract.
Prompt to use: "Remember this: Acme confirmed they want to expand to 3 new departments starting Q1. Decision maker is Sarah Chen."
What Jarvis does: Routes to Account Management HQ → appends to Acme's MEMORY.md with timestamp
Why it matters: Next time you ask about Acme, Jarvis already knows

EXAMPLE 4 — Prep for a Meeting
Scenario: You have a QBR with a client in 30 minutes.
Prompt to use: "I have a QBR with Acme in 30 minutes. Pull everything I need to know."
What Jarvis does: Reads Acme's MEMORY.md → checks recent Slack/email → summarizes open action items, key decisions, and anything overdue
What you get: A briefing doc, ready in under 60 seconds

EXAMPLE 5 — Build a New Workstation
Scenario: You want a dedicated workspace for managing your team's hiring pipeline.
Prompt to use: "Create a new workstation for managing our engineering hiring pipeline."
What Jarvis does: Routes to Workstation Factory → runs intake → scaffolds CLAUDE.md, MEMORY.md, and a resources folder → adds it to the routing map
What you get: A fully structured workstation ready for use

EXAMPLE 6 — Schedule a Recurring Task
Scenario: You want a weekly summary of all Slack mentions sent to you every Friday at 4pm.
Prompt to use: "Every Friday at 4pm, search Slack for all my mentions this week and DM me a summary."
What Jarvis does: Creates a scheduled task with a SKILL.md → registers the cron → runs automatically
What you get: A weekly digest, every Friday, zero effort

EXAMPLE 7 — Jarvis vs. Manual Decision Guide
Show a comparison table:

| Task | Use Jarvis | Do manually |
| :---- | :---- | :---- |
| Draft a client email | ✅ Always | |
| Make a final hiring decision | | ✅ Always |
| Summarize a long email thread | ✅ Always | |
| Sign a contract | | ✅ Always |
| Prep for a meeting | ✅ Always | |
| Have a sensitive HR conversation | | ✅ Always |
| Log notes after a call | ✅ Always | |
| Decide company strategy | | ✅ Always |
| Write a status update | ✅ Always | |
| Meet a client for the first time | | ✅ Often better |

EXAMPLE 8 — The "Remember This" Superpower
Scenario: You're in a meeting, on a call, or mid-conversation and learn something important.
Just say: "Remember this: [whatever you learned]"
Jarvis logs it to the right MEMORY.md with a timestamp.
Examples of what to remember:
- "Remember this: Marcus at ETG is our new main contact. Old contact Dana left the company."
- "Remember this: We promised Acme a sandbox environment by end of Q3."
- "Remember this: My manager wants me to focus on enterprise accounts in H2."

At the bottom of Tab 3, add a prominent section:
"New to this? Start here."
Recommended first 3 prompts after setup:
1. "Pull everything I need to know about [your biggest account]."
2. "Draft a reply to [recent email you received]."
3. "What's on my plate today?"

---

After creating all files and the artifact, confirm what was created and tell me which step to run next.
```

---

## Step 1 — Root Workspace + Voice Profile

*Same session as Step 0 is fine if files were just created. Otherwise, open a new task with the Jarvis folder selected.*

```
None

Read Jarvis/CLAUDE.md and Jarvis/MEMORY.md. Then do the following.

PART A: UPDATE MEMORY.md WITH MY DETAILS

Update Jarvis/MEMORY.md with:
- My name: [YOUR NAME]
- My email: [YOUR EMAIL]
- My role: [YOUR ROLE] at [YOUR COMPANY]
- My Slack User ID: [YOUR SLACK USER ID]
- My manager: [MANAGER NAME] ([MANAGER EMAIL])
- My team: [LIST TEAMMATES AND ROLES/EMAILS]
- Main tools: Gmail, Slack, Google Calendar[, add others]

---

PART B: EXTRACT MY VOICE FROM GMAIL

Connect to Gmail and do the following:

1. Search for 15-20 emails I sent to external contacts in the last 60 days ("in:sent newer_than:60d"). Focus on professional threads, not automated replies.

2. Analyze my actual writing patterns:
   - How do I open emails? What greetings do I use?
   - What's my sentence rhythm and average length?
   - What words or phrases do I use repeatedly?
   - How do I close messages?
   - What do I consistently avoid?
   - How formal or casual am I with different recipient types?

3. Rewrite Jarvis/00_Resources/voice-principles.md to reflect what you find. Keep the section structure. Replace the scaffold defaults with MY actual patterns.

4. Show me a summary of what you found before writing. Wait for my approval, then save the file.

Confirm each file is updated.
```

---

## Step 2 — Email HQ

```
None

Create a workstation called "Email HQ" inside the Jarvis folder.

Create Jarvis/Email HQ/CLAUDE.md:

# Email HQ

## Identity
You are [YOUR NAME]'s email strategist and drafting partner. Everything that involves drafting, replying to, or reviewing an email routes here — client updates, internal notes, cold outreach, vendor threads. You don't handle Slack messages, calendar invites, or documents.

## Resources
| Resource | Read when... |
| :---- | :---- |
| ../00_Resources/voice-principles.md | Drafting any email |

## Workflow
1. Read voice-principles.md before drafting anything.
2. Identify recipient type and match formality rules below.
3. Draft the email.
4. If replying: check whether an existing thread is open with this recipient first.
5. Flag anything sensitive before sending.

## Editorial Rules
Follow voice-principles.md. Additional email rules:

**Greetings**
- External clients/partners: "Hello [Name]," or "Hello [Team] Team,"
- Ongoing external thread replies: no greeting, go straight to content.
- Internal teammates: no greeting. Start with the message.

**Sign-off**
- No personal closing ("Best," "Thanks") before your name. The signature handles it.
- Exception: a standalone "Thanks" mid-message is fine when genuinely thanking someone.

**Formality by recipient**
- External clients (ongoing threads): direct and conversational. Quick replies are often one sentence.
- External clients (new threads or formal updates): open with "Updating that..." or "Following up from..."
- Internal team: terse. One to two sentences. No pleasantries.

**Conventions**
- Group emails to external recipients: "Hello all,"
- Open status updates with "Updating that..." or "Following up from our sync..."
- Use numbered lists for multiple open items.
- Close with "Please let me know if [X]" when action is needed.

---

Create Jarvis/Email HQ/MEMORY.md:

# Email HQ Memory
*Last updated: [TODAY'S DATE]*

## Contacts

## Key Decisions

---

Add this row to the Routing Map in Jarvis/CLAUDE.md:
"Email HQ | ...need to draft, reply to, or review any email"

Confirm all files created.
```

---

## Step 3 — Account Management HQ

```
None

Create a workstation called "Account Management HQ" inside the Jarvis folder.

Create Jarvis/Account Management HQ/CLAUDE.md:

# Account Management HQ

## Identity
This is [YOUR NAME]'s Account Management HQ. Everything related to managing customer accounts routes here — project status, action items, contacts, communications, and next steps. At the start of every session, read MEMORY.md in this folder.

## Resources
| Resource | Read when... |
| :---- | :---- |
| ../00_Resources/voice-principles.md | Drafting any external communication |

## Workflow

### Starting a session
1. Read this CLAUDE.md and MEMORY.md.
2. If the user's prompt references any person, organization, or account — even in passing — search MEMORY.md for a matching sub-HQ before doing anything else.
   - If a match is found: navigate to that sub-HQ, read its CLAUDE.md and MEMORY.md, and use that context to inform the response.
   - If no match is found: pause the original request and run the New Account Intake below. Do not proceed until the sub-HQ is created.
3. Check Slack and email for new activity on the account.
4. Summarize open action items with due dates. Flag anything overdue or due within 48 hours.

### New Account Intake
When a person, org, or account is mentioned and no sub-HQ exists, ask:
1. What is the full name of the account or organization?
2. Who is the main point of contact (name, role, email)?
3. What is the current status of the relationship? (prospect, active customer, partner, other)
4. Are there any open projects or action items I should log immediately?
5. Anything else I should know to start?

After collecting answers: create the sub-HQ, populate MEMORY.md with what was shared, add the account to the Managed Accounts table in this MEMORY.md, and add a routing row to Jarvis/CLAUDE.md. Then resume the original request.

### Tracking action items
- Log commitments in the account's MEMORY.md under Action Items.
- Every item must have an owner and due date if known.

### Creating a new account sub-HQ
When I say "create a new account for [Name]":
1. Create Jarvis/Account Management HQ/[Company] HQ/
2. Add CLAUDE.md and MEMORY.md (standard structure below).
3. Add org to MEMORY.md under "Managed Accounts."
4. Add routing row to Jarvis/CLAUDE.md.

### Standard sub-HQ structure
CLAUDE.md: Identity, Resources, Workflow, Editorial Rules
MEMORY.md sections: Contacts, Current Projects, Action Items, Key Decisions, Next Project

## Editorial Rules
Follow voice-principles.md.
- Be direct and specific. No filler.
- When flagging risk, lead with the impact, then the ask.
- Never overpromise on timelines.

---

Create Jarvis/Account Management HQ/MEMORY.md:

# Account Management HQ Memory
*Last updated: [TODAY'S DATE]*

## Managed Accounts
| Account | Sub-HQ | Status |
| :---- | :---- | :---- |
| [Add your accounts here] | | |

## Recent Sync Log

## Key Decisions

---

Now create my first account sub-HQ for "[YOUR FIRST ACCOUNT NAME]":

Jarvis/Account Management HQ/[Account] HQ/CLAUDE.md:

# [Account] HQ

## Identity
This is [YOUR NAME]'s workstation for [Account]. Route here for anything related to this account — project status, contacts, comms, action items, and next steps.

## Resources
| Resource | Read when... |
| :---- | :---- |
| ../../00_Resources/voice-principles.md | Drafting any communication |

## Workflow
1. Read MEMORY.md before every session.
2. Summarize open action items. Flag anything overdue or due within 48 hours.
3. Check Slack and email for new activity before drafting anything.

## Editorial Rules
Follow voice-principles.md.

---

Jarvis/Account Management HQ/[Account] HQ/MEMORY.md:

# [Account] — Memory
*Last updated: [TODAY'S DATE]*

## Contacts
| Name | Role | Email |
| :---- | :---- | :---- |

## Current Projects

## Action Items
| Owner | Item | Due Date | Status |
| :---- | :---- | :---- | :---- |

## Key Decisions

## Next Project

---

Add this row to the Routing Map in Jarvis/CLAUDE.md:
"Account Management HQ | ...am working on any customer account"

Confirm all files created.

To add more accounts later: "Create a new account sub-HQ for [Company Name]"
```

---

## Step 4 — Workstation Factory

```
None

Create a workstation called "Workstation Factory" inside the Jarvis folder.

Create Jarvis/Workstation Factory/CLAUDE.md:

# Workstation Factory

## Identity
You are my workspace architect. Your only job is to help design, structure, and create new Claude Cowork workstations correctly. Never skip intake. Never guess at missing fields. Always produce complete, correctly formatted files.

## Trigger Detection
Scan for workspace-creation intent at the start of every session:
- "I want a workspace for..."
- "Create a workstation that..."
- Any description of a role Claude should play repeatedly

Begin intake immediately if detected. Generate nothing until intake is complete.

## Intake Checklist
Required:
1. Name — short, role-specific, title-case
2. Identity — "You are [user's name]'s [role and purpose]."
3. Routing trigger — "...need to [verb] any [topic]."
4. Resources subfolder — what will live there?

Optional: Connected service, data scope, editorial rules

Default editorial rules (when none specified):
1. My default tone and greeting style in this context
2. How I adjust formality by audience type
3. Recurring structures or conventions I use
4. What I avoid in this context

## Output
Produce all three: (1) a creation prompt, (2) the CLAUDE.md content, (3) the MEMORY.md content.

## Editorial Rules
1. Never generate before intake is complete.
2. Always produce all three outputs.
3. Generate file contents only — never create files directly in this session.

---

Create Jarvis/Workstation Factory/MEMORY.md:

# Workstation Factory Memory
*Last updated: [TODAY'S DATE]*

## Workstations Created

## Key Decisions

---

Add this row to the Routing Map in Jarvis/CLAUDE.md:
"Workstation Factory | ...want to create a new workstation of any kind"

Confirm all files created.
```

---

## Step 5 — Scheduled Tasks

Four automations. Run each in a new task. Fill in your name, email, Slack User ID, and account list.

### 5a — Morning Briefing (7am daily → Slack DM)

```
None

Set up a scheduled task "morning-customer-briefing" at 7:00 AM daily.

Create Jarvis/Scheduled/morning-customer-briefing/SKILL.md:

---
name: morning-customer-briefing
description: Daily 7am briefing — customer emails + Slack threads, posted to my Slack DM
---

Build [YOUR NAME]'s ([YOUR EMAIL], Slack [YOUR SLACK USER ID]) daily morning briefing and post it to their Slack DM.

STEP 1 — CUSTOMER EMAILS (last 24-36h):
Run these Gmail searches and merge results:
1. "in:inbox newer_than:2d"
2. "in:sent newer_than:2d"
3. One per customer domain: "from:[domain.com] OR to:[domain.com] newer_than:4d" for each of: [LIST YOUR CUSTOMER DOMAINS]

Group threads by sender domain. For each account: subject, last sender + time, 1-2 sentence summary, any open action item for [YOUR NAME]. Ignore: login codes, password resets, no-reply mail, payment notices. Never post a briefing with just empty headers — if a section has nothing, write "Nothing new."

STEP 2 — PAIR SLACK THREADS:
For each account, search Slack for the account/customer name. One-line summary + permalink for any match.

STEP 3 — SLACK THREADS WORTH KNOWING:
Search last 2 days for mentions of [YOUR NAME]: "<@[YOUR SLACK USER ID]>" and "to:<@[YOUR SLACK USER ID]>". Also monitor threads from [LIST KEY TEAMMATES] about strategy, product direction, or decisions worth knowing. 1-2 lines per match, with permalink.

STEP 4 — CALENDAR:
List today's meetings (time, title, attendees).

FORMAT (Slack mrkdwn):
*:sunrise: Morning Briefing — <date>*
*:office: Customer Accounts*
*:speech_balloon: Slack — Worth Knowing*
*:calendar_spiral: Today's Calendar*
*:dart: Top action items for today*

DELIVERY: slack_send_message to [YOUR SLACK USER ID].

---

Register cron "0 7 * * *". Confirm task ID and next run time.
```

### 5b — Account Sync (6am + 6pm daily)

```
None

Set up a scheduled task "customer-account-sync" at 6:00 AM and 6:00 PM daily.

Create Jarvis/Scheduled/customer-account-sync/SKILL.md:

---
name: customer-account-sync
description: Twice-daily scan of Slack and email for customer updates — writes findings to MEMORY.md files
---

You are [YOUR NAME]'s account assistant. Scan Slack and Gmail for new activity and update MEMORY.md files.

## Accounts
[LIST EACH ACCOUNT AND PATH, e.g.:]
- **Acme Corp** — Jarvis/Account Management HQ/Acme HQ/MEMORY.md

## Steps
1. Search Slack for each account name (last 12 hours). Read full threads.
2. Search Gmail for each account name (last 12 hours).
3. Extract: account changes, key dates, requirements, risks, decisions, action items for [YOUR NAME].
4. Update each account's MEMORY.md — append only, never overwrite. Timestamp all entries.
5. Update Jarvis/Account Management HQ/MEMORY.md with a one-sentence summary of changes.
6. Report: which accounts had activity and what changed. Skip accounts with nothing new.

---

Register cron "0 6,18 * * *". Confirm.
```

### 5c — Hourly Account Sweep

```
None

Set up a scheduled task "customer-account-hourly-review" to run every hour.

Create Jarvis/Scheduled/customer-account-hourly-review/SKILL.md:

---
name: customer-account-hourly-review
description: Hourly account sweep — finds new Slack/email activity and updates MEMORY.md files
---

Run an hourly sweep for [YOUR NAME]. Search Slack and email for new activity in the last 2 hours across all managed accounts.

## Accounts
[LIST EACH ACCOUNT WITH SLACK KEYWORDS AND MEMORY.md PATH, e.g.:]
1. **Acme Corp** — Slack: #acme + keyword "Acme" | Jarvis/Account Management HQ/Acme HQ/MEMORY.md

## Steps
1. Search Slack (slack_search_public_and_private, sort by timestamp) for each account.
2. Search Gmail (newer_than:2h) for each account.
3. Extract: action items, decisions, project updates, feedback, new contacts.
4. Read existing MEMORY.md before updating. Only update with genuinely new info. Append, never overwrite.
5. Update Jarvis/Account Management HQ/MEMORY.md "Recent Sync Log" if anything changed materially.
6. Skip accounts with no new activity.

---

Register cron "0 * * * *". Confirm.
```

### 5d — Voice Principles Refresh (1st of each month)

```
None

Set up a scheduled task "voice-principles-monthly-refresh" to run on the 1st of each month at 8:00 AM.

Create Jarvis/Scheduled/voice-principles-monthly-refresh/SKILL.md:

---
name: voice-principles-monthly-refresh
description: Monthly refresh of voice-principles.md — re-analyzes recent writing to keep the profile current
---

You are refreshing [YOUR NAME]'s voice profile.

## Step 1 — Gather recent writing
Search Gmail for 15-20 emails sent to external contacts in the last 30 days ("in:sent newer_than:30d"). Prioritize professional threads over short replies.

## Step 2 — Analyze patterns
Extract:
- Greeting and sign-off style
- Sentence rhythm and paragraph length
- Words and phrases used repeatedly
- Things consistently avoided
- Formality by recipient type
- Any patterns that differ from the current voice-principles.md

## Step 3 — Compare to current file
Read Jarvis/00_Resources/voice-principles.md. Identify what has drifted or evolved.

## Step 4 — Update if meaningful changes found
If the analysis reveals material drift, update voice-principles.md. Keep the section structure. Preserve intentional rules. Only change what the writing evidence supports.

## Step 5 — DM [YOUR NAME]
Send a Slack DM to [YOUR SLACK USER ID] with:
- What changed (or "No material changes found")
- 2-3 example phrases that illustrate the update
- Confirm the file was updated (or left unchanged)

---

Register cron "0 8 1 * *". Confirm.
```

---

## Step 6 — Live Account Dashboard

*Run after your accounts are set up.*

```
None

Read all MEMORY.md files in Jarvis/Account Management HQ/ and its sub-HQs. Then create a live artifact called "account-dashboard" that:

1. Shows a card per account with: account name, open action items (owner + due date), last updated date
2. Flags overdue items in red, items due within 48 hours in yellow
3. Shows a header with today's date and total open action item count
4. Has a clean, professional card layout in a responsive grid

Use the actual data from my MEMORY.md files to seed the initial view.

Tell me how to refresh it after MEMORY.md files are updated.
```

---

## Quick Reference

### Automation Schedule
| Automation | When | What it does |
| :---- | :---- | :---- |
| Morning briefing | 7am daily | Emails + Slack + calendar → DM |
| Account sync | 6am + 6pm | Scans all accounts → updates MEMORY.md |
| Hourly sweep | Every hour | Lightweight account update |
| Voice refresh | 1st of month | Re-trains voice profile from Gmail |

### Power Phrases
- **"Remember this"** — logs anything to the right MEMORY.md automatically
- **"Create a new account sub-HQ for [Name]"** — scaffolds a full account workspace
- **"That doesn't sound like me — update voice-principles.md"** — corrects your voice profile on the spot
- **"What's on my plate today?"** — pulls open items across all accounts
- **"Prep me for my call with [Name]"** — reads account MEMORY.md + recent comms and briefs you

### The Golden Rule
> Open a new task. Select the Jarvis folder. Keep it short.
> Jarvis is the context — not the thread.
