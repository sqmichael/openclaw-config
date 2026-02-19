# OpenClaw Automation System

*Your AI assistant that runs 24/7, handling the boring stuff so you can focus on what matters.*

---

## What This Does

This system is like having a digital employee that never sleeps. It handles routine tasks across your email, calendar, events, and social media automatically. When something needs your attention, it sends you a message. When something can be handled automatically, it just does it.

**Think of it as:** A smart assistant that checks your inbox, manages your events, processes your videos, and keeps your team updated — all without you lifting a finger.

---

## Daily Automated Tasks

Every day, the system wakes up and does these things:

### Morning (8:30-9:00 AM)

| Task | What It Does | Where You See Results |
|------|-------------|----------------------|
| **Invoice Watcher** | Checks Gmail for new invoices, receipts, and payment confirmations | Telegram "Admin/Invoice" topic |
| **Event Policy Check** | Makes sure upcoming events follow your venue rules | Telegram "Events/Policy" topic |
| **Event Sync** | Keeps Luma events and Google Calendar in sync, warns about room conflicts | Telegram "Events/Policy" topic |

### Early Morning (3:00-4:30 AM)

| Task | What It Does | Where You See Results |
|------|-------------|----------------------|
| **Media Mirror** | Syncs files from Google Drive to local storage | Telegram "Dev Status" topic |
| **Video Processor** | Transcribes videos, adds subtitles, prepares for YouTube | YouTube + Telegram "Content" topic |
| **Photo Shortlist** | Scores new event photos, picks the best ones | Google Sheet + Telegram "Content" topic |

### Evening (10:00 PM)

| Task | What It Does | Where You See Results |
|------|-------------|----------------------|
| **Daily Blog** | Writes a blog post based on recent activity | Telegram "Dev Status" topic |

### Weekly Tasks

| Day | Task | What It Does |
|-----|------|-------------|
| **Friday 6 PM** | **Transcript Check** | Looks for new meeting transcripts in Notion, starts content pipeline |
| **Saturday 9 AM** | **LinkedIn Outreach** | Prepares connection requests for recent event attendees |
| **Sunday 6 PM** | **Community Sentiment** | Analyzes WhatsApp group mood, sends summary |

---

## How It Decides What to Tell You

The system uses **three models** depending on the job:

| Model | Best For | Cost |
|-------|---------|------|
| **Kimi K2.5** (Primary) | Routine tasks, structured data, notifications | Cheap |
| **Claude Sonnet** (Fallback) | Complex analysis, nuanced content | Medium |
| **Claude Opus** (Manual only) | High-quality writing, important decisions | Expensive |

**Example:**
- Invoice scanning → **Kimi** (it's just pattern matching)
- Blog writing → **Sonnet** or **Opus** (needs creativity)
- Community sentiment analysis → **Opus** (needs to understand sarcasm, context)

---

## The Manual Workflow (When Quality Matters)

Sometimes you want human oversight. Here's the approved workflow for complex tasks:

### Step 1: Kimi Generates a Plan
Kimi writes a build plan as a markdown file and saves it to `~/plans/`

### Step 2: You Get Notified
A watcher script sees the new file and tells you (via terminal or notification)

### Step 3: You Execute with Claude Code
You open Termux (on your phone) or terminal, and run:
```bash
claude --cwd ~/claude-builds < ~/plans/filename.md
```

This keeps you compliant with Anthropic's terms while still getting automation benefits.

---

## Telegram Topics Explained

Your Telegram group (-1003765921384) has organized threads:

| Topic ID | Name | What Gets Posted There |
|----------|------|----------------------|
| 19 | Admin/Invoice | Invoice alerts, transcript status |
| 75 | Events/Policy | Luma policy alerts, calendar conflicts |
| 262 | Dev Status | System health, sync status, blog generation |
| 276 | LinkedIn Outreach | New outreach batch notifications |
| 278 | Content | YouTube links, Luma blast copy, photo shortlists |
| 300 | Community Sentiment | Weekly WhatsApp sentiment digest |
| 334 | Marketing Campaigns | Analytics dashboards |
| 343 | Community Sentiment | Weekly digests |

---

## Key Integrations

### Google Workspace
- **Gmail:** Scanned for invoices (read-only, specific searches)
- **Calendar:** Synced with Luma events
- **Sheets:** Used for tracking prospects, LinkedIn outreach, photo shortlists
- **Drive:** Media files synced locally for processing

### Notion
- **Event Transcripts Database:** Whisper transcripts stored here, trigger content pipeline
- Database ID: `aad338ec-73d1-4604-b9f0-7ef29ed820c0`

### Luma
- Events managed via API (read-only for guests, no messaging API available)
- Calendar ID: `cal-dq6sVvBponL8shq`

### WhatsApp
- Group monitoring for sentiment analysis
- Selective responses (only when mentioned or high value)

### YouTube
- Videos processed with Whisper transcription
- Auto-uploaded to playlist: "Co-work Fridays @ SQCo — 2026"
- Subtitles styled with Geist Medium font

---

## Cost Savings

Switching to Kimi K2.5 as primary saves approximately **60-70%** on AI costs:

| Model | Input Cost | Output Cost | Your Use Case |
|-------|-----------|-------------|---------------|
| Kimi K2.5 | $0.70/million | $2.80/million | Routine automation |
| Sonnet 4.5 | $3.00/million | $15.00/million | Complex analysis |
| Opus 4.6 | $15.00/million | $75.00/million | High-quality content |

**Typical daily savings:** $3-5/day → $90-150/month

---

## Quick Commands

### Check System Status
```bash
openclaw status
```

### List Active Sessions
```bash
openclaw sessions list
```

### Switch Model (if needed)
```bash
/model kimi      # Use Kimi
/model sonnet    # Use Sonnet
/model opus      # Use Opus (if available)
```

### Start the Plans Watcher
```bash
~/plans/watcher.sh
```

### Check Logs
```bash
tail -f ~/plans/watcher.log
```

---

## Security Notes

- **API Keys:** Stored in environment variables, never in code
- **OAuth:** Only used for official clients (Claude Code CLI)
- **Data:** Private data stays private, no training on your content
- **Access:** Tailscale network restricts access to your devices only

---

## Troubleshooting

### Model Falls Back to Sonnet
If you see Claude responding instead of Kimi, it means:
1. Kimi failed to respond (rate limit, error)
2. The task required capabilities Kimi doesn't have

This is normal — the fallback system is working.

### Watcher Not Notifying
Check if it's running:
```bash
ps aux | grep watcher
```

Restart if needed:
```bash
nohup bash ~/plans/watcher.sh > ~/plans/watcher.log 2>&1 &
```

### Cron Jobs Not Running
Check cron status:
```bash
openclaw cron list
```

---

## People on the Team

- **Owei:** Manager — sales + ops (27 prospects in tracker)
- **Sheina:** Admin — facilities, invoicing, purchasing (handles LinkedIn outreach)
- **Fong Lian:** Marketing — XHS leads (3 prospects in tracker)

The system sends appropriate notifications to each person's workflow.

---

## Want to Add Something New?

The system is modular. New features can be added as:
1. **Cron jobs** — for scheduled tasks
2. **Hooks** — for event-driven actions
3. **Skills** — for specific capabilities

Talk to your technical lead (or the AI) about what you need.

---

## Summary

You have an AI assistant that:
- ✅ Checks your email for invoices every morning
- ✅ Keeps your events calendar synced
- ✅ Processes videos and uploads to YouTube
- ✅ Writes blog posts
- ✅ Analyzes community sentiment
- ✅ Handles LinkedIn outreach
- ✅ Never uses your data for training
- ✅ Costs 60-70% less than before
- ✅ Stays within legal compliance

**It handles the routine. You handle the important.**

---

*Last updated: February 19, 2026*
*System: OpenClaw 2026.2.17*
*Primary Model: Kimi K2.5 (Moonshot AI)*
