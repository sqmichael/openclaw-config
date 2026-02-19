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

## Where to Find Your Notifications

Your Telegram group has organized topics. Here's what's posted where:

| Topic | What Gets Posted There |
|-------|----------------------|
| **Admin/Invoice** | Invoice alerts, transcript status updates |
| **Events/Policy** | Luma policy alerts, calendar conflicts, event sync issues |
| **Dev Status** | System health updates, media sync status, blog generation |
| **LinkedIn Outreach** | New outreach batch notifications |
| **Content** | YouTube links, Luma blast copy, photo shortlists |
| **Community Sentiment** | Weekly WhatsApp sentiment digest |
| **Marketing Campaigns** | Analytics dashboards |

**Tip:** Mute the topics you don't need to check daily, keep notifications on for the ones relevant to your role.

---

## Key Integrations

The system connects to the tools you already use:

- **Gmail** — Scanned for invoices and receipts
- **Google Calendar** — Synced with Luma events
- **Google Sheets** — Tracks prospects, outreach, and photo shortlists
- **Google Drive** — Media files synced for processing
- **Notion** — Meeting transcripts stored here
- **Luma** — Events managed and monitored
- **WhatsApp** — Groups monitored for community sentiment
- **YouTube** — Videos processed and auto-uploaded

---

## Manual Workflow (When You Want Control)

For complex tasks that need your oversight, the system generates a plan and lets you decide when to execute it.

**How it works:**
1. The AI writes a build plan and saves it to the plans folder
2. You get notified that a new plan is ready
3. You review the plan and run it when you're ready

This gives you the benefits of AI planning with full human control over execution.

---

## Common Issues & Fixes

### Not Getting Notifications
- Check that you're in the right Telegram topic
- Make sure notifications aren't muted for that topic

### Something Stopped Working
- Check the "Dev Status" topic — system issues are posted there
- If it's urgent, ping @huangpf or the technical lead

### Need to Update a Setting
- Contact your technical lead (Michael)
- Don't try to change system settings yourself

---

## Who Does What

| Person | Role | What They Handle |
|--------|------|-----------------|
| **Owei** | Manager | Sales + operations (27 prospects) |
| **Sheina** | Admin | Facilities, invoicing, purchasing, LinkedIn outreach |
| **Fong Lian** | Marketing | XHS leads (3 prospects) |

The system routes notifications to the right person automatically.

---

## Summary

You have an AI assistant that:
- ✅ Checks your email for invoices every morning
- ✅ Keeps your events calendar synced
- ✅ Processes videos and uploads to YouTube
- ✅ Writes blog posts
- ✅ Analyzes community sentiment
- ✅ Handles LinkedIn outreach
- ✅ Sends you only what matters
- ✅ Costs less than before
- ✅ Keeps your data private

**It handles the routine. You handle the important.**

---

*Questions? Ping @huangpf in Telegram.*
