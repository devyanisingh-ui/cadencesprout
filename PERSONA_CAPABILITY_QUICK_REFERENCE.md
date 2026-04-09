# CadenceSprout — Persona Capability Matrix & Quick Reference

**Purpose:** At-a-glance reference for persona capabilities, platform features, and system organization.

---

## 📊 Persona Capability Heatmap

### Teacher (Sunita) — Content Creation + Classroom Ops

```
CORE CAPABILITIES:
┌─────────────────────────────────────────────────────┐
│ ✅✅ POSTING (P0)                                    │
│     • Photo/video capture                           │
│     • AI caption draft + manual edit                │
│     • AI child face detection + confirm             │
│     • Manual child picker                           │
│     • Optional milestone tagging                    │
│     • Offline queue support (Phase 2)               │
│                                                     │
│ ✅✅ FEED (P0)                                       │
│     • View own class posts                          │
│     • See parent reactions & comments               │
│     • Engagement insights (who viewed)              │
│     • Reply to parent comments                      │
│                                                     │
│ ✅ ATTENDANCE (P1)                                  │
│     • Mark daily attendance (<60s)                  │
│     • View attendance history                       │
│     • Bulk marking (web)                            │
│                                                     │
│ ✅ MILESTONES (P1)                                  │
│     • View milestones by child                      │
│     • Tag milestones from composer                  │
│     • AI suggestions                                │
│                                                     │
│ ✅ INCIDENTS (P1)                                   │
│     • Log incidents inline in composer              │
│     • View incident history by child                │
│     • Notify parents (if enabled)                   │
│                                                     │
│ ✅ ROSTER (P0)                                      │
│     • View class children list                      │
│     • Child detail (profile, milestones, posts)     │
│     • Link parents for each child                   │
│                                                     │
│ ✅ DAILY REPORT (P2)                                │
│     • Optional quick summary form                   │
│     • Share with parents (optional)                 │
│                                                     │
│ ✅ NOTIFICATIONS (P0)                               │
│     • Parent reaction & comment alerts              │
│     • Nudge if no post by 12 PM                     │
│     • Customizable preferences                      │
│                                                     │
│ ❌ OFFLINE (Phase 2)                                │
│     • Queue posts when offline                      │
│     • Auto-sync when online                         │
│                                                     │
│ ❌ SEARCH (Phase 2)                                 │
│     • Search own posts                              │
│     • Filter by child, date, milestone              │
│                                                     │
│ ❌ MESSAGING (Phase 2)                              │
│     • 1:1 teacher ↔ parent messages                 │
└─────────────────────────────────────────────────────┘

PLATFORM SUPPORT:
  📱 Mobile (React Native): Full support for all P0/P1
  🖥️  Web (React + Vite): Full parity with mobile
```

---

### Parent (Meera) — Engagement + Trust Layer

```
CORE CAPABILITIES:
┌─────────────────────────────────────────────────────┐
│ ✅✅ FEED (P0 / MVP)                                 │
│     • View child's posts (teacher-confirmed tags)   │
│     • Warm, captioned photos                        │
│     • Reverse-chronological timeline                │
│     • Scroll to older posts                         │
│                                                     │
│ ✅✅ REACTIONS & COMMENTS (P0 / MVP)                │
│     • React with emoji                              │
│     • Reply with text comment                       │
│     • See teacher responses                         │
│                                                     │
│ ✅ MILESTONES & PORTFOLIO (P1 / V1)                 │
│     • View NEP 2020 domain progress                 │
│     • See milestones achieved                       │
│     • Download PDF memory book                      │
│     • Share portfolio with family                   │
│                                                     │
│ ✅ HEALTH & RECORDS (P1 / V1)                       │
│     • View medical info (read-only)                 │
│     • Update own info (with school approval)        │
│     • Emergency contacts                            │
│                                                     │
│ ✅ INCIDENTS (P1 / V1)                              │
│     • View incident history                         │
│     • Severity & resolution status                  │
│     • Follow-up notes                               │
│                                                     │
│ ✅ FEES & PAYMENTS (P2 / V1)                        │
│     • View outstanding balance                      │
│     • Invoice list & payment history                │
│     • Download receipts                             │
│     • Manual payment entry (w/ admin)               │
│     • Razorpay auto-payment (Phase 2)               │
│                                                     │
│ ✅ NOTIFICATIONS (MVP +)                            │
│     • New post alerts (push + WhatsApp)             │
│     • Teacher comment replies                       │
│     • Incident notifications (if enabled)           │
│     • Fee reminders (if enabled)                    │
│     • Daily digest option                           │
│     • Customizable opt-in settings                  │
│                                                     │
│ ✅ SETTINGS & PRIVACY (MVP)                         │
│     • Name + profile                                │
│     • Linked parents (siblings)                     │
│     • Notification preferences                      │
│     • Photo consent for face recognition            │
│     • DPDP data export / delete                      │
│                                                     │
│ ✅ MAGIC-LINK (MVP)                                 │
│     • Access feed without full app install          │
│     • Web-based entry point                         │
│     • One-time password (no password needed)        │
│                                                     │
│ ❌ MESSAGING (Phase 2)                              │
│     • 1:1 messages with teacher                     │
│                                                     │
│ ❌ SEARCH (Phase 2)                                 │
│     • Search posts by keyword, date, milestone      │
└─────────────────────────────────────────────────────┘

PLATFORM SUPPORT:
  📱 Mobile (React Native + Magic-Link Web): Full support
  🖥️  Web (React + Vite + Magic-Link): Full parity
```

---

### Admin / Principal (Rajesh) — Control Tower

```
CORE CAPABILITIES:
┌─────────────────────────────────────────────────────┐
│ ✅✅ SCHOOL SETUP (Core / MVP)                       │
│     • Self-serve registration                       │
│     • Logo + branding setup                         │
│     • Create classes                                │
│     • Invite teachers via SMS                       │
│                                                     │
│ ✅✅ ENGAGEMENT MONITORING (MVP)                     │
│     • KPI dashboard (posts/day, engagement %)       │
│     • Alerts: low-engagement classes                │
│     • Engagement score by class trend               │
│     • Quick message to low-engagement teachers      │
│                                                     │
│ ✅ ATTENDANCE (P1 / V1)                             │
│     • Aggregate attendance % (school + by class)    │
│     • Detail by class (grid view)                   │
│     • Trend chart (14-day rolling)                  │
│     • Alert if % below threshold                    │
│     • Bulk import (Phase 2)                         │
│                                                     │
│ ✅ FEES & BILLING (P2 / V1)                         │
│     • Create invoices (amount, due date)            │
│     • Invoice list + status (due, paid, overdue)    │
│     • Send reminder (WhatsApp / SMS)                │
│     • Mark as paid (manual in Phase 1)              │
│     • Aging report (0-30, 30-60, 60+ days)         │
│     • Razorpay auto-billing (Phase 2)               │
│                                                     │
│ ✅ ADMISSIONS (P1 / V1)                             │
│     • Inquiry lead pipeline                         │
│     • Track inquiry → enroll → payment              │
│     • Lead source attribution                       │
│     • Conversion funnel chart                       │
│     • Bulk invite children + parents                │
│                                                     │
│ ✅ STAFF MANAGEMENT (P1 / V1)                       │
│     • Staff list (name, role, class, phone)         │
│     • Invite new staff (SMS setup link)             │
│     • Assign classes to teachers                    │
│     • Remove access                                 │
│     • Activity tracking (Phase 2)                   │
│                                                     │
│ ✅ CHILD RECORDS (P2 / V1)                          │
│     • Master child list                             │
│     • Child demographic info                        │
│     • Medical / health information                  │
│     • Allergies + emergency contacts                │
│     • Enrollment photo (for face recognition)       │
│     • Bulk import from CSV                          │
│                                                     │
│ ✅ INCIDENTS (P1 / V1)                              │
│     • Incident log (type, severity, child, date)    │
│     • Filter by: type, severity, class, unresolved  │
│     • Parent notification status                    │
│     • Add follow-up notes                           │
│     • Mark as resolved                              │
│                                                     │
│ ✅ ROSTER & PERMISSIONS (P0)                        │
│     • View class + child structure                  │
│     • Link parents to children                      │
│     • Manage linked parents                         │
│     • Permission matrix (read-only in MVP)          │
│                                                     │
│ ✅ ALERTS & EXCEPTIONS (MVP)                        │
│     • Classes below posting threshold               │
│     • Unpaid invoices + aging                       │
│     • Low attendance                                │
│     • High-severity incidents                       │
│     • Teachers inactive                             │
│     • One-click action (message, follow-up)         │
│                                                     │
│ ✅ INTEGRATIONS (Phase 2+)                          │
│     • WhatsApp config                               │
│     • SMS provider setup                            │
│     • Razorpay account linking                      │
│     • Webhook management                            │
│                                                     │
│ ✅ SUBSCRIPTION & BILLING (Core)                    │
│     • Plan + seats                                  │
│     • Payment method                                │
│     • Upgrade / downgrade                           │
│                                                     │
│ ❌ NO MOBILE (Web-only in Phase 1)                  │
│     • Dashboard is desktop-first                    │
│     • Mobile admin apps Phase 2                     │
└─────────────────────────────────────────────────────┘

PLATFORM SUPPORT:
  🖥️  Web (React + Vite): Full support
  📱 Mobile: Not in MVP/V1 (Phase 2)
```

---

## 📱 Platform Feature Matrix

### MVP vs V1 vs Phase 2

```
TEACHER
┌────────────────────────────┬─────┬────┬────────┐
│ Feature                    │ MVP │ V1 │ Phase2 │
├────────────────────────────┼─────┼────┼────────┤
│ Logging in                 │ ✅  │ ✅ │   ✅   │
│ Posting (photo + caption)  │ ✅  │ ✅ │   ✅   │
│ AI captioning              │ ✅  │ ✅ │   ✅   │
│ AI child tagging           │ ✅  │ ✅ │   ✅   │
│ Feed view (class posts)    │ ✅  │ ✅ │   ✅   │
│ Parent reactions & comments│ ✅  │ ✅ │   ✅   │
│ Roster management          │ ✅  │ ✅ │   ✅   │
│ Child detail view          │ ✅  │ ✅ │   ✅   │
│ Nudge engine (no post yet) │ ✅  │ ✅ │   ✅   │
│ Attendance marking         │ ❌  │ ✅ │   ✅   │
│ Milestones tracker         │ ❌  │ ✅ │   ✅   │
│ Incident logging           │ ❌  │ ✅ │   ✅   │
│ Daily report               │ ❌  │ ✅ │   ✅   │
│ Offline posting + sync     │ ❌  │ ❌ │   ✅   │
│ Search posts               │ ❌  │ ❌ │   ✅   │
│ 1:1 messaging w/ parent    │ ❌  │ ❌ │   ✅   │
└────────────────────────────┴─────┴────┴────────┘

PARENT
┌────────────────────────────┬─────┬────┬────────┐
│ Feature                    │ MVP │ V1 │ Phase2 │
├────────────────────────────┼─────┼────┼────────┤
│ Magic-link entry           │ ✅  │ ✅ │   ✅   │
│ OTP verification           │ ✅  │ ✅ │   ✅   │
│ Parent feed                │ ✅  │ ✅ │   ✅   │
│ Posts detail & comments    │ ✅  │ ✅ │   ✅   │
│ Reactions (emoji)          │ ✅  │ ✅ │   ✅   │
│ Settings & profile         │ ✅  │ ✅ │   ✅   │
│ Health & records           │ ❌  │ ✅ │   ✅   │
│ Milestones & portfolio     │ ❌  │ ✅ │   ✅   │
│ Incident history           │ ❌  │ ✅ │   ✅   │
│ Fees & payments            │ ❌  │ ✅ │   ✅   │
│ Notification center        │ ❌  │ ✅ │   ✅   │
│ 1:1 messaging w/ teacher   │ ❌  │ ❌ │   ✅   │
│ Razorpay payments          │ ❌  │ ❌ │   ✅   │
│ Search                     │ ❌  │ ❌ │   ✅   │
└────────────────────────────┴─────┴────┴────────┘

ADMIN
┌────────────────────────────┬─────┬────┬────────┐
│ Feature                    │ MVP │ V1 │ Phase2 │
├────────────────────────────┼─────┼────┼────────┤
│ School registration        │ ✅  │ ✅ │   ✅   │
│ School setup (logo, etc)   │ ✅  │ ✅ │   ✅   │
│ Home dashboard (KPIs)      │ ✅  │ ✅ │   ✅   │
│ Engagement dashboard       │ ✅  │ ✅ │   ✅   │
│ Class creation             │ ✅  │ ✅ │   ✅   │
│ Teacher invitations        │ ✅  │ ✅ │   ✅   │
│ Attendance dashboard       │ ❌  │ ✅ │   ✅   │
│ Fees & invoices            │ ❌  │ ✅ │   ✅   │
│ Admissions pipeline        │ ❌  │ ✅ │   ✅   │
│ Staff management           │ ❌  │ ✅ │   ✅   │
│ Child records              │ ❌  │ ✅ │   ✅   │
│ Incident management        │ ❌  │ ✅ │   ✅   │
│ Razorpay auto-billing      │ ❌  │ ❌ │   ✅   │
│ Bulk import                │ ❌  │ ❌ │   ✅   │
│ Audit logs                 │ ❌  │ ❌ │   ✅   │
└────────────────────────────┴─────┴────┴────────┘
```

---

## 🎯 Screen Count by Tier

### MVP ("Post + See")

```
TEACHER APP:
  • Onboarding: T-0, T-0A (2 screens)
  • Feed & Composing: T-1, T-1A, T-2, T-2A, T-2B (5 screens)
  • Roster: T-5, T-5A (2 screens)
  • Settings: T-10 (1 screen)
  ─────────────────────────
  TOTAL: 10 screens

PARENT APP (+ Web via magic-link):
  • Onboarding: P-0, P-0A, P-0B, P-0C (4 screens)
  • Feed: P-3, P-4, P-4A (3 screens)
  • Settings: P-12, P-13, P-14, P-15, P-16 (5 screens)
  ─────────────────────────
  TOTAL: 12 screens

ADMIN DASHBOARD (Web):
  • Setup: A-0, A-0A, A-0B (3 screens)
  • Monitoring: A-1, A-2 (2 screens)
  ─────────────────────────
  TOTAL: 5 screens

MVP TOTAL: 27 screens (lightweight, shippable)
```

### V1 ("Operate + Learn")

```
ADDITION TO TEACHER: +8 screens
  T-3 (milestones), T-4 (attendance history), T-5B (quick mark),
  T-5C (milestone progress), T-5D (incidents), T-8 (daily report),
  T-9 (incident logger), T-10A, T-10B

ADDITION TO PARENT: +8 screens
  P-5 (milestones), P-6 (portfolio), P-7 (notifications),
  P-8 (health), P-9 (fees), P-11 (incidents)

ADDITION TO ADMIN: +9 screens
  A-3 (admissions), A-4 (fees overview), A-5 (attendance),
  A-6 (staff), A-7 (lead mgmt), A-8 (fee settings),
  A-9 (invoices), A-11 (child records), A-13 (incidents)

V1 TOTAL: ~52 screens (complete Phase 1 product)
```

---

## 🔄 Core System Loops

### Teacher Loop (Engagement Cycle)

```
┌─────────────┐
│ 1. Capture  │ → Moment happens in classroom
└──────┬──────┘
       │
       ▼
┌──────────────┐
│ 2. Compose   │ → Open app, snap photo, write caption
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ 3. AI Assist │ → Auto-caption, child tags, milestones
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ 4. Post      │ → One tap, appears in feed instantly
└──────┬───────┘
       │
       ▼
┌──────────────────┐
│ 5. Parent Reacts │ → "Loved!", comment, emoji
└──────┬───────────┘
       │
       ▼
┌──────────────┐
│ 6. Validated │ → Sees engagement → feels motivated
└──────┬───────┘
       │
       └───────────────┐
                       │ Repeat
                       ▼
                  (Next moment)
```

**KPI:** 3+ posts per class per day

---

### Parent Loop (Engagement Cycle)

```
┌──────────────┐
│ 1. Notified  │ → "Rohan posted a moment!"
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ 2. Opens App │ → Tap magic-link or app
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ 3. Sees Post │ → Warm photo + caption (< 2s)
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ 4. Reacts    │ → ❤️ / 😊 / 👍 + comment
└──────┬───────┘
       │
       ▼
┌──────────────────┐
│ 5. Emotionally   │ → Connected to child's day
│    Satisfied     │
└──────┬───────────┘
       │
       └───────────────┐
                       │ Next day
                       ▼
                   (Check app)
```

**KPI:** 70%+ daily active parents from magic-link invites

---

### Admin Loop (Operations Cycle)

```
┌──────────────────┐
│ 1. Check         │ → Open dashboard (A-1)
│    Metrics       │
└──────┬───────────┘
       │
       ▼
┌──────────────────┐
│ 2. Spot Alert    │ → "Nursery A: 1 post (target 3)"
└──────┬───────────┘
       │
       ▼
┌──────────────────┐
│ 3. Investigate   │ → Last post: 8 AM, teacher: Sunita
└──────┬───────────┘
       │
       ▼
┌──────────────────┐
│ 4. Act Fast      │ → [Message Teacher] (pre-filled)
└──────┬───────────┘
       │
       ▼
┌──────────────────┐
│ 5. Follow Up     │ → Check Nursery A posting again
└──────┬───────────┘
       │
       └───────────────┐
                       │ Weekly
                       ▼
                   (Next review)
```

**KPI:** Admin can act on 3 alerts in <2 minutes

---

## 📊 Engagement Score Definition

```
Engagement Score = 
    (Posts/day/class × 0.4) +
    (Parent launch rate × 0.3) +
    (Comments + reactions/post × 0.2) +
    (Attendance % × 0.1)

Target (Month 10): 75+ / 100
```

**Components:**
- **Posts/day/class** (40%): Minimum 3 per class per day
- **Parent launch rate** (30%): % of magic-link invites who opened feed
- **Engagement/post** (20%): Avg comments + reactions per post
- **Attendance %** (10%): Operational health

---

## 🚀 Launch Checklist

### MVP Shippable (Month 1-4)

```
REQUIRED FOR FIRST PILOT SCHOOL:

TEACHER
 ✅ Login + onboarding
 ✅ Composer (photo + caption + tags)
 ✅ AI captioning + child detection
 ✅ Feed view for teacher
 ✅ Roster + child detail
 ✅ Nudge engine (no post yet)
 ✅ Mobile + Web parity
 ✅ Notification: parent reactions

PARENT
 ✅ Magic-link onboarding (no password)
 ✅ Parent feed (posts about child)
 ✅ Reactions & comments
 ✅ Settings + privacy
 ✅ Mobile web + installed app

ADMIN
 ✅ School registration
 ✅ Class + teacher setup
 ✅ Home dashboard (KPIs)
 ✅ Engagement score

BACKEND
 ✅ Multi-tenancy (RLS in PostgreSQL)
 ✅ Face recognition setup (AWS Rekognition)
 ✅ WhatsApp notifications (Wapi)
 ✅ SMS fallback (MSG91)
 ✅ S3 media upload
 ✅ API rate limiting

SUCCESS CRITERIA:
 • 1 pilot chain (5+ centers) fully live
 • ≥70% enrolled parents using feed
 • ≥3 posts per class per day
 • NPS from teachers ≥ 30
```

---

## 🎓 Quick Personas vs Screens

### Where Sunita (Teacher) Spends Time

```
T-1 (Feed)           40%  ← Monitoring posts / reactions
T-2 (Composer)       35%  ← Creating posts (core job)
T-5 (Roster)         15%  ← Checking children + parents
T-10 (Settings)       5%  ← Rare
T-8 (Daily Report)    5%  ← Optional, evening only
```

### Where Meera (Parent) Spends Time

```
P-3 (Feed)           60%  ← Scrolling child updates
P-4 (Post Detail)    25%  ← Reading, reacting, commenting
P-6 (Portfolio)      10%  ← End-of-year browsing
P-12 (Settings)       5%  ← Occasional
```

### Where Rajesh (Admin) Spends Time

```
A-1 (Home)           30%  ← Morning check-in (alerts)
A-2 (Engagement)     25%  ← Weekly monitoring
A-5 (Attendance)     15%  ← Weekly/daily
A-4 (Fees)           15%  ← As needed
A-3 (Admissions)     10%  ← Sales cycle dependent
Other (records, etc)  5%  ← Compliance
```

---

## 💾 Data Scope Rules

### Every Request Is Scoped by `school_id`

```
Teacher requests data    → Can only see rows where school_id = their school
                           AND class_id = their class

Parent requests data     → Can only see rows where school_id = their school
                           AND child_id = linked to them

Admin requests data      → Can only see rows where school_id = their school
                           (no class/child filtering)

Database: PostgreSQL Row-Level Security (RLS) enforces this at the query level.
Result: Never rely on the API to filter — the database enforces isolation.
```

---

## 📋 Summary: What Goes Where

| Concern | Where | Owner | Priority |
|---------|-------|-------|----------|
| **Teacher posts** | T-2 Composer | Teacher | P0 |
| **Parent sees updates** | P-3 Feed | System (notifications) | P0 |
| **Admin monitors engagement** | A-1/A-2 Dashboard | Admin | MVP |
| **Attendance tracking** | T-4 (teacher) + A-5 (admin) | Teacher/Admin | P1 |
| **Milestones** | T-3 / P-5 / A-11 | Teacher/Parent/Admin | P1 |
| **Fees** | P-9 (parent) + A-4/A-9 (admin) | Admin/Parent | P2 |
| **Incidents** | T-9 (log) + P-11 (view) + A-13 (manage) | Teacher/Parent/Admin | P1 |
| **Compliance** | A-11 (records) + P-14 (privacy) | Admin/Parent | Ongoing |

---

**Version:** 1.0 | **Date:** 2026-04-07 | **Ref:** INFORMATION_ARCHITECTURE.md

