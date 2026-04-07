# CadenceSprout — Phase 1 PRD
**All-in-One Preschool OS for Indian Preschools**

- **Author:** Alex (PM)
- **Date:** 2026-03-26
- **Status:** Feature Complete (Engagement + Full Preschool OS)
- **Version:** 3.0
- **Reviewed by:** CEO Review ✓ | Design Review ✓ | Eng Review ✓

---

## 🧠 CadenceSprout System Definition

### 🎯 North Star Metric

**% of parents who see at least 1 meaningful update about their child per day** ("% of parents receiving at least 1 update per day").

This is the single metric that should guide all engagement and OS decisions in Phase 1.

### Supporting Metrics

- **Daily teacher posting rate** (per class)
- **Parent weekly active rate (WAU)**
- **Average posts per class per week**
- **% of children with milestone coverage** (at least N milestones logged per term)
- **Parent engagement** (views, reactions, comments per post)

### 🔁 Core Loop (System View)

At a system level, CadenceSprout operates on a simple repeating loop:

> **Capture → Post → Notify → View → Re-engage → Capture**

Every feature and trigger should reinforce this loop for teachers and parents.

### ⚡ System Priorities (Non-negotiable)

| Priority | Feature           | Rule                          |
|----------|-------------------|-------------------------------|
| 🔥 P0    | Posting + Feed    | Must be fastest, never blocked |
| 🔥 P0    | Parent visibility | Every post must reach parents |
| 🟡 P1    | Milestones        | Passive + AI-assisted         |
| 🟡 P1    | Attendance        | Daily habit, < 60 sec         |
| 🟢 P2    | Daily report      | Optional, never interrupt flow |
| 🟢 P2    | Fees              | Calm, parent-first            |
| ⚪ P3    | Admin dashboards  | Insight, not primary UX       |

These priorities should be respected across design, engineering, and growth decisions. Conceptually:

- **P0 = Posting + Feed** (teacher and parent, mobile + web).
- **P1 = Milestones + Attendance** (child progress + core classroom ops).
- **P2 = Reports + Fees + Admin surfaces** (daily reports, fee flows, dashboards).

### 🔗 System Principles

- **Engagement-first, ERP-second** — the teacher and parent feeds remain the primary surfaces; ERP features are layered in as contextual, lightweight flows.
- **Nothing blocks posting** — no compliance step, form, or configuration screen should ever prevent a teacher from posting a simple update.
- **Everything connects to the feed** — posts, milestones, attendance, incidents, and daily reports ultimately flow back into the child/parent narrative.
- **AI assists, never interrupts** — AI suggestions (captions, child tags, milestones, summaries) should reduce friction, not add extra mandatory steps.
- **Compliance is visible but calm** — privacy, records, and incidents are clearly labelled and accessible, but never dominate the emotional story.
 - **Emotional > operational** — when in doubt, bias towards warm, human storytelling and reassurance over adding one more operational field or chart.

---

## Table of Contents

- [1. Product Intent](#1-product-intent)
- [2. Core Principles](#2-core-principles)
- [3. System Behaviors](#3-system-behaviors)
  - [3.1 Nudge Engine](#31-nudge-engine)
  - [3.2 Draft System](#32-draft-system)
  - [3.3 Offline System](#33-offline-system)
  - [3.4 AI System](#34-ai-system)
  - [3.5 Notification System](#35-notification-system)
- [4. Data Model (MANDATORY)](#4-data-model-mandatory)
- [5. Permissions](#5-permissions)
- [0. Feature Capability Matrix (NEW — LOCK BEFORE UI)](#0-feature-capability-matrix-new--lock-before-ui)
- [1. Executive Summary](#1-executive-summary)
- [1A. Core Engagement Loops (NEW)](#1a-core-engagement-loops-new)
  - [1B. Product Scope Expansion](#1b-product-scope-expansion)
  - [1C. MVP vs V1 (Delivery Cut)](#1c-mvp-vs-v1-delivery-cut)
  - [⚡ System Trigger Engine](#system-trigger-engine)
  - [🔗 Cross-Feature Connections](#cross-feature-connections)
- [2. User Personas](#2-user-personas)
- [3. Phase 1 Epics and User Stories](#3-phase-1-epics-and-user-stories)
  - [Epic 1: School Onboarding & Multi-Tenancy Foundation](#epic-1-school-onboarding--multi-tenancy-foundation)
  - [Epic 2: Child Enrollment & Parent Onboarding](#epic-2-child-enrollment--parent-onboarding)
  - [Epic 3: Teacher Post Flow (The Core Loop — FULLY REWRITTEN)](#epic-3-teacher-post-flow-the-core-loop--fully-rewritten)
  - [Epic 4: Parent Feed Experience (REWRITTEN)](#epic-4-parent-feed-experience-rewritten)
  - [Epic 5: Attendance Tracking](#epic-5-attendance-tracking)
  - [Epic 6: Fee Management](#epic-6-fee-management)
  - [Epic 7: Admin Dashboard & Engagement Score (REWRITTEN)](#epic-7-admin-dashboard--engagement-score-rewritten)
  - [Epic 8: Communication Layer (NEW)](#epic-8-communication-layer-new)
  - [Epic 9: Search & Retrieval (NEW)](#epic-9-search--retrieval-new)
  - [Epic 10: AI Intelligence Layer (EXPANDED)](#epic-10-ai-intelligence-layer-expanded)
  - [Epic 11: Admissions Management](#epic-11-admissions-management)
  - [Epic 12: Parent Engagement System (NEW)](#epic-12-parent-engagement-system-new)
  - [Epic 13: Admin Alerts & Intelligence (NEW)](#epic-13-admin-alerts--intelligence-new)
- [4. Screen Inventory](#4-screen-inventory)
  - [4.0 Screen ID → Epics Map (NEW)](#40-screen-id--epics-map-new)
  - [4.1 Teacher App (React Native — iOS + Android)](#41-teacher-app-react-native--ios--android)
  - [4.2 Parent App (React Native — iOS + Android)](#42-parent-app-react-native--ios--android)
  - [4.3 Admin / Principal Web Dashboard (React + Vite)](#43-admin--principal-web-dashboard-react--vite)
  - [4.4 Teacher Web (Browser — React + Vite)](#44-teacher-web-browser--react--vite)
  - [4.5 Parent Web (Browser)](#45-parent-web-browser)
- [5. Key API Contracts](#5-key-api-contracts)
  - [5A. Core Data Model (NEW — LOCK BEFORE BUILD)](#5a-core-data-model-new--lock-before-build)
  - [5B. Notification System (NEW)](#5b-notification-system-new)
  - [5C. Event Flows & State Persistence (NEW)](#5c-event-flows--state-persistence-new)
- [6. Non-Functional Requirements](#6-non-functional-requirements)
  - [6.1 DPDP Act 2023 Compliance](#61-dpdp-act-2023-compliance)
  - [6A. Permissions Matrix (NEW)](#6a-permissions-matrix-new)
  - [6.2 Performance Targets](#62-performance-targets)
  - [6.3 Accessibility](#63-accessibility)
  - [6.4 Security](#64-security)
  - [6B. Edge Case Handling (NEW)](#6b-edge-case-handling-new)
- [7. Technology Architecture](#7-technology-architecture)
- [8. Phase 2 — Post First 10 Paying Customers](#8-phase-2--post-first-10-paying-customers)
  - [Epic P2-1: Razorpay Auto-Billing](#epic-p2-1-razorpay-auto-billing)
  - [Epic P2-2: Hindi + Tamil Language Support](#epic-p2-2-hindi--tamil-language-support)
  - [Epic P2-3: Per-Class and Per-Teacher Engagement Score](#epic-p2-3-per-class-and-per-teacher-engagement-score)
  - [Epic P2-4: HRMS — Staff Management](#epic-p2-4-hrms--staff-management)
  - [Epic P2-5: Official WhatsApp Business API Migration](#epic-p2-5-official-whatsapp-business-api-migration)
  - [Epic P2-6: Offline-First Data Sync](#epic-p2-6-offline-first-data-sync)
  - [Epic P2-7: Extended Content — Quizzes, Library, Live Camera](#epic-p2-7-extended-content--quizzes-library-live-camera)
  - [Epic P2-8: On-Server ML Model for Milestone Suggestion](#epic-p2-8-on-server-ml-model-for-milestone-suggestion)
  - [Growth Hooks (NEW)](#growth-hooks-new)
- [9. Phase 3 — Franchise and Global](#9-phase-3--franchise-and-global)
  - [Epic P3-1: White-Label and Franchise Chain Support](#epic-p3-1-white-label-and-franchise-chain-support)
  - [Epic P3-2: Arabic Language and RTL UI (Dubai Market)](#epic-p3-2-arabic-language-and-rtl-ui-dubai-market)
  - [Epic P3-3: CRM Integrations](#epic-p3-3-crm-integrations)
  - [Epic P3-4: Southeast Asia Expansion](#epic-p3-4-southeast-asia-expansion)
  - [Epic P3-5: Schema-Per-Tenant (Enterprise Isolation)](#epic-p3-5-schema-per-tenant-enterprise-isolation)
- [10. Success Metrics](#10-success-metrics)
  - [Phase 1 Launch Criteria (Month 10)](#phase-1-launch-criteria-month-10)
  - [Engagement Score Definition](#engagement-score-definition)
  - [3-Month Pilot Milestones](#3-month-pilot-milestones)
  - [6-Month Growth Milestones](#6-month-growth-milestones)
  - [12-Month ARR Target](#12-month-arr-target)
  - [Leading Indicators (Weekly Tracking)](#leading-indicators-weekly-tracking)
- [Appendix: Pre-Build Blockers](#appendix-pre-build-blockers)

---

## 1. Product Intent

**Product intent:** CadenceSprout helps teachers share daily classroom moments with parents, turning the school day into a warm, ongoing story instead of a once-a-term report.

**Primary goal (Phase 1):** At least **1 meaningful update per child per day** visible to at least one guardian.

**Simple core loop (per child):**

> **Capture → Post → Parent views → Teacher feels reinforced → Repeat**

This per-child loop should remain the default lens for evaluating features, trade-offs, and experiments. See [🧠 CadenceSprout System Definition](#-cadencesprout-system-definition) for the system-level loop and metrics.

---

## 2. Core Principles

These are the day-to-day design and implementation rules that sit on top of the System Principles above:

1. **Speed > completeness** — shipping a fast, reliable way to share a moment beats adding one more field, filter, or configuration.
2. **ERP is optional, not mandatory** — attendance, fees, admissions, and records should be present and useful, but they **never block** posting or viewing the feed.
3. **AI assists, never blocks** — AI can draft captions, suggest tags, infer milestones, and summarise days; the human can always ignore, edit, or override with zero friction.
4. **Offline-first reliability** — teachers should be able to capture and queue posts even on flaky school Wi‑Fi; the system is responsible for safe delivery when connectivity returns.
5. **Warm, human communication** — copy, defaults, and visuals should feel like a friendly teacher talking to a parent, even when the content is operational (fees, incidents, attendance).

---

## 3. System Behaviors

This section summarises the cross-cutting system behaviours that power drafts, offline, nudges, AI, and notifications. Detailed event and trigger definitions live in [⚡ System Trigger Engine](#system-trigger-engine), [5B. Notification System (NEW)](#5b-notification-system-new), and [5C. Event Flows & State Persistence (NEW)](#5c-event-flows--state-persistence-new).

### 3.1 Nudge Engine

- **Scope:** One nudge **per teacher per class per day**.
- **Detection window:** 00:00–12:00 local time.
  - If **no successful POST_CREATED event** exists for that class in this window, the class is eligible.
- **Fire window:** The nudge is scheduled to fire between **12:00–12:15 PM local time**.
- **Cancel conditions:**
  - If a POST_CREATED event arrives **before** the nudge fires, the nudge is cancelled.
  - If the teacher dismisses the nudge, it is not re‑sent the same day.
- **Channel & surface:**
  - Delivered as an in‑app banner on **T‑1 / TW‑1** and, where appropriate, as a push notification (see [Notification System](#5b-notification-system-new)).

### 3.2 Draft System

- **Auto‑save cadence:** While composing a post (T‑2 / TW‑2):
  - Auto‑save the draft **at least every 10 seconds** after any change, and
  - On navigation away, app background, or app close.
- **Draft contents:** A draft captures **media references**, **caption text**, **tagged children**, and any **incident stub** attached in the composer.
- **Restore behaviour:**
  - On reopening the composer on the same day with an unsent draft, restore the draft and surface a light prompt: "You have an unsent draft from today" with **Resume** / **Discard**.
- **Failure handling:**
  - If upload fails after the teacher taps **POST**, the post remains in the feed as a **draft/outbox item** with a clear retry state; no content is lost.
  - The teacher can **tap to retry** or **cancel**; cancelling removes it from the queue and prevents it from reaching parents.

### 3.3 Offline System

Even before full offline-first (Phase 2), CadenceSprout must behave predictably on flaky networks.

- **Local queue:** When the device is offline or the network is unstable:
  - Post creations, comment submissions, and reactions are written to a **local outbox queue** instead of failing.
- **UI state:** Queued items are clearly marked as **"Sending when online"** (e.g., clock icon / "Queued") and are not shown in parent feeds until confirmed by the server.
- **Retry schedule (per item):**
  - 1st retry after **5 seconds**
  - 2nd retry after an additional **30 seconds**
  - 3rd retry after an additional **2 minutes**
  - Subsequent retries every **10 minutes** up to a configurable max.
- **Conflict & cancellation:**
  - If a queued item is successfully sent from another device for the same teacher/class, duplicates are deduplicated server‑side using idempotency keys.
  - The teacher can cancel any queued item from the outbox; cancelled items are never delivered to parents.

### 3.4 AI System

**AI Captioning**

- **Trigger:** When the teacher selects photo(s)/video(s) in the composer, a caption draft request is sent automatically.
- **Target latency:** AI caption visible in the composer in **< 3 seconds** (P75), with loading shimmer while pending.
- **Behaviour:**
  - The teacher can post the AI draft as‑is, edit freely, or delete and write their own.
  - If the caption job fails or times out, the caption field simply remains manual; no blocking error is shown.

**Face / Child Detection**

- The system runs face detection on uploaded media (where school + parent consent is given) to suggest child tags.
- **Confidence thresholds (summary; see [Epic 10: AI Intelligence Layer](#epic-10-ai-intelligence-layer-expanded) for detail):**
  - **> 90%** → high‑confidence suggested tag (pre‑checked chip).
  - **70–90%** → low‑confidence suggested tag (visually distinct; teacher must confirm).
  - **< 70%** → no suggestion.
- Child names only appear in the final caption where the tag has been teacher‑confirmed; otherwise captions use generic language ("the children", "the class").

### 3.5 Notification System

High-level behaviour (see [5B. Notification System (NEW)](#5b-notification-system-new) for the canonical event table):

**For teachers**

- **Parent interactions:** When a parent comments on or reacts to a teacher's post, the teacher receives an in‑app notification and, where enabled, a push notification **immediately**.
- **Midday posting reminder:** If there has been **no post today** for a class by around **12 PM local time**, the teacher receives a single **"No update yet today"** push/in‑app nudge for that class (see [3.1 Nudge Engine](#31-nudge-engine)).
  - One reminder per class per day; it is cancelled if a post is created before it fires.

**For parents**

- **New post about their child:** Push + optional WhatsApp notification **instantly** when a new post that includes their child is published.
- **Incident logged with parent notification enabled:** Immediate high‑priority notification (push +, where configured, WhatsApp) with calm, factual copy and a link to the relevant child record / incident detail.
- **Daily report (T‑8) shared:** When a daily report is saved and marked as shared, parents receive an evening notification in a **6 PM local-time window** summarising the day.

**Global rules**

- Cap at **3 push notifications per parent per day**; non‑critical events are batched into a daily digest where possible.
- WhatsApp is reserved for critical updates, high‑value engagement, and re‑engagement flows (onboarding, fee reminders, portfolios), not for spam.

---

## 4. Data Model (MANDATORY)

This section gives a **conceptual** view of the core records that power the engagement loop. The **authoritative schema** is defined in [5A. Core Data Model (NEW — LOCK BEFORE BUILD)](#5a-core-data-model-new--lock-before-build).

### 4.1 Post

Represents a single shareable classroom moment.

```text
Post {
  id: uuid
  class_id: uuid
  teacher_id: uuid
  media_urls: string[]    // photos / videos
  caption: string
  created_at: timestamp
  tagged_children: Child[]    // via PostChildTag join table
  milestones: Milestone[]     // via PostMilestone join table
}
```

### 4.2 Child

Represents an enrolled child and their relationships.

```text
Child {
  id: uuid
  class_id: uuid
  name: string
  dob: date
  parents: Parent[]   // Phase 1 stored as primary parent_id, expandable later
}
```

### 4.3 Draft (Composer / Outbox)

Represents unsent work in progress on the client and/or server.

```text
Draft {
  temp_id: uuid              // client-generated
  class_id: uuid
  teacher_id: uuid
  media_urls: string[]
  caption: string
  child_ids: uuid[]
  incident_stub?: IncidentStub   // optional inline incident
  saved_at: timestamp
  status: "local" | "queued" | "failed"
}
```

Drafts may never reach the server (purely local) but, when they do, they map 1:1 onto the eventual `Post` fields.

### 4.4 Incident

Represents a logged incident linked to children and, optionally, a contextual post.

```text
Incident {
  id: uuid
  child_ids: uuid[]      // one or more children involved
  class_id: uuid
  post_id?: uuid         // optional link back to a post
  type: string           // e.g., fall, behaviour, medical
  severity: "info" | "minor" | "major"
  description: string
  occurred_at: timestamp
  notify_parent: boolean
}
```

All incidents are written into **Child Records (A‑11)** and the child timeline, and can optionally trigger parent/admin notifications as defined in [3.5 Notification System](#35-notification-system).

---

## 5. Permissions

This is the high‑level view of who can see and edit what. The canonical, implementation-level matrix lives in [6A. Permissions Matrix (NEW)](#6a-permissions-matrix-new).

- **Teacher**
  - Can **view**: children and posts in their own class only.
  - Can **create/edit**: posts, attendance records for their class, and incident records attached to those posts/children.
  - Cannot access other classes or school‑wide data except where explicitly granted an admin role.

- **Parent**
  - Can **view**: posts, milestones, incidents, and records for **their own child only**.
    - A parent only sees a post if their child is tagged and the tag is teacher‑confirmed.
  - Can **act**: react to and comment on posts, manage notification and privacy settings for their child.

- **Admin / Principal**
  - Can **view**: all classes, children, posts, incidents, attendance, fees, and admissions data within their school.
  - Can **edit**: school, class, teacher, child, and fee records; resolve incidents; manage admissions pipelines.
  - Cannot see data across schools; access is scoped to their own school tenancy.

---

## 1. Executive Summary

### What is CadenceSprout?

CadenceSprout is an AI-native preschool operating system built specifically for Indian preschools — the first product in the market that combines a Seesaw-quality parent engagement feed with a full preschool ERP (attendance, fees, admissions, staff management) in a single, beautifully designed platform.

### The Problem

India has 1.8 million+ preschools. The vast majority — particularly standalone preschool chains running 2-10 centers — have no management software at all. Their daily workflow is: WhatsApp groups for parent communication, paper registers for attendance, Tally for fees, and paper portfolios for learning records. Higher-end preschools pay for two tools (a generic K-12 ERP + Seesaw) that were never designed for early childhood. The best-funded Indian competitor, Illumine ($2.5M seed, 3,000+ centers), remains English-first, has not matched Seesaw's UX quality, and lacks deep India-specific features.

### The Opportunity

The primary buyer — a standalone preschool chain owner competing locally for enrollments — has a clear trigger: their competitors who use Seesaw look more premium during admissions. CadenceSprout gives them that premium experience at a fraction of Seesaw's price, with ERP capabilities built in.

### Phase 1 Scope

Phase 1 ships the complete product foundation over 10 months:

**Seesaw Layer:** Parent feed (teacher posts photos/videos), AI activity tagging (child identification via AWS Rekognition + milestone suggestion + caption drafting via OpenRouter), NEP 2020 milestone tracker, WhatsApp magic-link parent onboarding, school-level engagement score dashboard, AI year-end developmental portfolio.

**ERP Layer:** Admissions management, fee management (manual invoicing), attendance tracking, staff management (names, roles, class assignment), self-serve school onboarding.

**Platform:** React Native mobile app (iOS + Android) for teachers and parents; React + Vite web dashboard for admins/principals; Laravel (PHP 8.2) backend with PostgreSQL row-level security for multi-tenancy.

### Why Now

A pilot school from Cadence Infotech's existing network is ready to go — the strongest possible pre-product demand signal. The tech stack is known to the team. The AI layer is technically feasible today at low cost. The market window is open: Illumine is going wide (56 countries), while CadenceSprout goes deep in India.

### Launch Target

Month 10. Success is 1 preschool chain (5+ centers) fully live, ≥70% of enrolled parents using the feed, ≥3 posts per class per day, self-serve onboarding live, NPS from teachers ≥ 30.

---

## 🆕 1B. Product Scope Expansion

CadenceSprout evolves from an engagement-first product into a full preschool operating system.

It consists of:

1. **Engagement Layer (Primary)**
  - AI-powered posts
  - Parent feed
  - Milestones & portfolio

2. **Operations Layer**
  - Fees & payments
  - Admissions CRM
  - Attendance & reporting
  - Staff management

3. **Compliance Layer**
  - Child records
  - Medical information
  - Incident tracking
  - Permissions

All operational features are embedded into existing flows to avoid ERP-style complexity.

---

## 🚀 1C. MVP vs V1 (Delivery Cut)

Phase 1 is broad. This section makes clear **what must exist for a usable pilot (MVP)** vs what rounds out **full V1**.

### MVP — "Post + See" (first live chain)

**Goal:** Prove the core engagement loop works in 1 pilot chain (5+ centres).

- **Teacher (Sunita)**
  - **T-1** — Teacher Feed (Home Feed) as the primary daily surface.
  - **T-2** — Composer (photo/video, caption, child tagging).
  - **T-5** — Class Roster (basic list of children + linked parents).
  - Web twins (TW-2/TW-3/TW-5) may be implemented, but are optional for the very first pilot.

- **Parent (Meera)**
  - **P-1** — Magic-link feed entry + OTP (with P-0/P-0A as needed).
  - **P-3** — Parent Feed with "Today at school" summary and story-like posts.
  - Web feed (PW-2) can ship later but must match P-3 behaviour when it does.

- **Admin (Rajesh)**
  - Basic school/class/teacher setup (Epics 1–2).
  - **Basic roster only** — read-only list of classes, children and linked parents; no dashboards, fees, or advanced reports.

**Out of scope for MVP (can be stubbed or manual):** Attendance flows, milestones UI, reports, fees, daily report, incident logging, advanced dashboards.

### V1 — "Operate + Learn" (Phase 1 complete)

**Goal:** Turn CadenceSprout into a **usable preschool OS** for a chain that wants both engagement and light operations.

- **Add for Teachers:**
  - Attendance (T-4 / TW-4) with < 60s per class target.
  - Milestone tracker (T-6 / TW-6) with AI suggestions from posts.
  - Daily report (T-8) — optional, quick structure on top of posts.
  - Incident logging (T-9) into child records.

- **Add for Parents:**
  - Milestone progress & portfolio (P-5, P-6, PW-4).
  - Incident history (P-11).
  - Fees overview & payments (P-9).

- **Add for Admins:**
  - Attendance dashboard (A-5).
  - Fees management + overview (A-4, A-9).
  - Admissions pipeline (A-3, A-10).
  - Child records & compliance hub (A-11).
  - Staff overview (A-6, A-12).

MVP must be **shippable on its own** and measured primarily on the **North Star** and basic teacher/parent satisfaction; V1 layers in attendance, milestones, reports, and fees without breaking the core posting + feed loop.

---

## 🆕 0. Feature Capability Matrix (NEW — LOCK BEFORE UI)

### 0.1 Persona Capability Definition

**Teacher (Content Creation + Classroom Ops)**

- AI-assisted post creation
- Child tracking (milestones, attendance)
- Parent interaction (comments + messaging)
- Class management (roster visibility)
- AI nudges for productivity

**Parent (Engagement + Trust Layer)**

- Personalized child feed
- React, comment, message teacher
- Milestone tracking + insights
- Portfolio + memory storage
- Notifications + summaries

**Admin / Principal (Control Tower)**

- Engagement monitoring
- Operational dashboards (attendance, fees)
- Staff & admissions management
- Alerts & insights

### 0.2 Platform Capability Mapping

| Capability           | Mobile App | Web App | Notes                   |
|----------------------|-----------:|--------:|-------------------------|
| Teacher Core Flow    |         ✅ |      ✅ | Strong                  |
| Parent Experience    |         ✅ |      ✅ | Strong                  |
| Admin Control        |         ❌ |      ✅ | Mobile gap              |
| Communication        |         ⚠️ |      ⚠️ | Needs upgrade           |
| Search               |         ❌ |      ❌ | Missing                 |
| AI Layer             |         ⚠️ |      ⚠️ | Needs expansion         |
| Offline              |         ❌ |      ❌ | Phase 2                 |

#### 🧠 CadenceSprout — Persona vs Platform Capability Matrix

##### 👩‍🏫 1. Teacher Persona — Capabilities

| Feature Area              | Teacher Mobile App                               | Teacher Web App                               | Gaps / Notes                                  |
|---------------------------|--------------------------------------------------|-----------------------------------------------|-----------------------------------------------|
| **Authentication**        | Phone + password login                           | Same                                          | ✅ Complete                                   |
| **Post Creation (Core Loop)** | Photo/video → AI caption → tag children → post  | Drag-drop media + same flow                   | ⚠️ No offline posting (Phase 2)              |
| **AI Captioning**         | Auto draft + edit                                | Same                                          | ⚠️ No tone/style control                      |
| **AI Child Tagging**      | Face recognition + confirm                       | Same                                          | ⚠️ No learning loop / correction feedback     |
| **Manual Tagging**        | Picker modal                                     | Table/search UI                               | ✅                                           |
| **Milestone Tagging**     | Optional tagging                                 | Same                                          | ⚠️ Taxonomy UX complexity risk                |
| **Feed View (Class)**     | Mobile feed                                      | 2-column desktop feed                         | ✅                                           |
| **Parent Engagement Insight** | "Viewed by X parents"                       | Same                                          | ⚠️ No per-parent insight                      |
| **Comments / Interaction**| View + reply                                     | Same                                          | ⚠️ No moderation tools                        |
| **Attendance**            | Mark daily                                       | Table bulk marking                            | ✅                                           |
| **Roster Management**     | View children + parents                          | Table + detail drawer                         | ⚠️ Cannot edit (admin dependent)              |
| **Child Detail View**     | Profile + milestones + posts                     | Same                                          | ✅                                           |
| **Milestone Tracker**     | Per child                                        | Same                                          | ⚠️ No insights (lagging/leading child)        |
| **Notifications**         | Toggles                                          | Same                                          | ⚠️ No smart reminders (AI nudges)             |
| **Settings / Profile**    | Full                                             | Full                                          | ✅                                           |

---

## 🧠 1A. Core Engagement Loops (NEW)

CadenceSprout is built around three reinforcing engagement loops — teacher, parent, and admin — that must all be healthy for the product to succeed.

**Teacher Loop**

- Capture moment → AI assists → Post → Parent reacts → Teacher feels validated → Repeat

**Parent Loop**

- Receive notification → View child update → React/comment → Emotional reward → Return daily

**Admin Loop**

- Check dashboard → Detect issues → Take action → Improve metrics → Repeat weekly

---

## ⚡ System Trigger Engine

The **System Trigger Engine** glues the engagement loops together. It defines when nudges, notifications, and summaries fire so that teachers keep posting, parents keep returning, and admins only see the important exceptions.

**High-level rules (summary):**

- **Teacher:**
  - No post by 12 PM → show T-1A emotional nudge.
  - No post by 2 PM → strong nudge + push notification.
- **Parent:**
  - New post → instant notification.
  - Not viewed within ~6 hours → gentle reminder.
- **Daily Report:**
  - Soft nudge around 4 PM.
  - Never blocks posting or core feed actions.
- **Incident:**
  - If "Notify parent" is ON in T-9 → instant parent alert + history entry.
- **Offline:**
  - All triggerable actions must **queue locally when offline** and auto-sync when back online; triggers fire based on the underlying events, not just when the app is open.

### 1. Teacher Nudges

| Trigger        | Condition             | Action                          |
|----------------|-----------------------|---------------------------------|
| Morning nudge  | No post by 10:30 AM   | Subtle banner on T-1 Home Feed  |
| Midday nudge   | No post by 12:00 PM   | Emotional banner (T-1A variant) |
| Strong nudge   | No post by 2:00 PM    | Strong CTA + push notification  |

- All nudges must respect the **"nothing blocks posting"** rule — they are encouragement, never mandatory dialogs.
- Strong nudges should be rate-limited so a teacher never feels spammed.

### 2. Parent Engagement

| Trigger        | Condition                    | Action                            |
|----------------|------------------------------|-----------------------------------|
| New post       | Post created for a child     | Push notification to linked parents |
| Not viewed     | 6 hours, parent hasn’t opened | Reminder notification (gentle)   |
| Weekly summary | Sunday evening               | Digest notification / summary card |

- New post notifications should be **child-specific and emotional**, not generic app spam.
- Weekly summary can roll up posts, milestones, and daily reports into a single, calm digest.

### 3. Daily Report Prompt

| Trigger      | Condition          | Action                        |
|--------------|--------------------|-------------------------------|
| After school | 3–5 PM local time  | Suggest Daily Report (T-8)    |
| Skip         | No interaction     | Do not repeat; no nagging     |

- Daily report prompts must always remain **optional** and should never block the core posting flow.

### 4. Fee Reminder

| Trigger    | Condition               | Action                                  |
|------------|-------------------------|-----------------------------------------|
| Upcoming   | 3 days before due date  | Soft reminder (P-9 + notification)     |
| Overdue    | 1 day after due date    | Highlight in parent feed / P-9         |
| Escalation | 7 days after due date   | Admin alert on A-1 / A-9 (overdue list) |

- Parent-side reminders must feel **calm and informational**, not aggressive collections.
- Admin escalation should surface as **alerts before charts** on the dashboard and Fees Overview.

### 5. Incident Flow

| Trigger        | Condition                | Action                                          |
|----------------|--------------------------|-------------------------------------------------|
| High severity  | Marked "High" in T-9    | Immediate parent + admin alert                  |
| Medium         | Saved in T-9             | Parent notified (if teacher enabled toggle)     |
| Low            | Saved in T-9             | Logged only (child record, no notification)     |

- All incidents are written into **Child Records (A-11)** and the **child timeline (T-5A)**.
- High severity flows must be implemented with extra care (clear copy, calm but unmissable UI).

---

## 🔗 Cross-Feature Connections

This section makes explicit how features depend on and reinforce each other. Everything ultimately connects back to **posts and the feed**.

### 📸 Post → Everything

- **Post → triggers parent notification** (immediate push for linked parents).
- **Post → updates daily summary** shown on P-3 (Parent Home Feed) and in weekly digests.
- **Post → suggests milestones** in T-6 (Milestone Tracker) via AI based on recent content.
- **Post → visible in child timeline** on T-5A (Child Detail / Timeline).

### 📊 Attendance → System

- **Attendance → shown in admin dashboard** (A-1, A-5) for class-level health.
- **Attendance → summarized in daily report** (T-8) so parents see presence as part of the day story.
- **Absence → optional parent visibility** — absent status can surface as a subtle note in parent surfaces when schools opt in.

### 🧠 Milestones

- **Milestones → suggested from posts (AI)** when the AI Intelligence Layer detects patterns.
- **Milestones → visible in parent progress** views (P-5, PW-4) so parents see long-term growth.
- **Milestones → appear in portfolio** (P-6, PW-4/PW-? as year-end/term-end exports).

### 🧾 Incident

- **Incident → appears in child timeline** (T-5A) with appropriate labels.
- **Incident → optional parent notification** via P-11 Incident History and notifications, based on T-9 sharing settings.
- **Incident → admin alert if severe** via A-1 dashboard alerts and A-11 Child Records.

### 💰 Fees

- **Overdue fees → appear in parent feed** as a subtle card and in P-9 Fees & Payments.
- **Payment → confirmation notification** to parents and reflected in A-9/A-4 admin views.
- **Admin → sees overdue list first (not charts)** in Fees Overview (A-9) and Fee Management (A-4).

### 📘 Daily Report

- **Daily report → appears in parent feed summary** (P-3) and weekly digest.
- **Daily report → aggregates:**
  - meals
  - naps
  - activities
  - attendance

---

### Design Principle: Engagement-First UI (NEW)

CadenceSprout treats engagement as the primary surface and ERP as supporting context.

- **Feed is always primary** — for both teachers and parents, the feed (posts and child updates) is the main entry point and first tab; operational tasks should not displace this.
- **ERP features are secondary and contextual** — fees, admissions, attendance, staff, and compliance surfaces appear where they naturally belong (e.g., tiles on the admin dashboard, cards under a child profile), not as heavyweight, standalone dashboards.
- **Avoid clutter and dashboard overload** — every screen should minimise cognitive load; we prefer a small number of high-signal tiles and views over dense tables and charts, especially on mobile.

---

## 2. User Personas

### Persona 1: The Teacher

**Name:** Sunita (representative)
**Role:** Preschool teacher, 1 class of 15-20 children
**Device:** Android smartphone (primary), school-issued tablet (sometimes)
**Technical comfort:** Comfortable with WhatsApp and smartphone apps; not a power user

**Primary Job-to-be-Done:** Document what happened in her class today and share it with parents — without it taking more than 5 minutes of her time.

**Secondary Jobs:**
- Take and submit daily attendance quickly
- Know which parents have seen her posts (she wants to know she's doing her job)
- Track individual children's developmental progress over time

**Current pain:**
- Spends 30+ min/day on WhatsApp — group messages, individual parent queries, managing who was missed
- Knows she should document more developmental moments but the WhatsApp friction stops her
- Has no structured way to record that "Rohan counted to 10 today" — it lives in her head or on a sticky note

**Fear:** That using a new app means more work, not less. The product must feel faster than WhatsApp for her to adopt it.

**Key insight from field research directive:** Watch what she doesn't send — the moments she witnesses and decides aren't worth the WhatsApp hassle. Those are the posts CadenceSprout must make effortless.

---

### Persona 2: The Parent

**Name:** Meera (representative)
**Role:** Working mother, child enrolled in nursery
**Device:** iPhone or mid-range Android
**Technical comfort:** High — uses Instagram, WhatsApp, Swiggy daily

**Primary Job-to-be-Done:** Know what her child did today without having to ask. Feel connected to her child's school day.

**Secondary Jobs:**
- React to and comment on her child's moments
- See her child's developmental progress over the year
- Receive and save the year-end portfolio to show family

**Current pain:**
- WhatsApp class groups are noisy — full of parent chatter, hard to find actual updates about her child
- When she does get an update, it's a blurry photo and a generic "morning activities" message
- She doesn't know what milestones her child has crossed — she only finds out at the parent-teacher meeting twice a year

**Fear:** Having to install another app. She already has too many. The magic-link design directly addresses this — she gets value before she commits to installing.

**Key insight:** The first moment she sees a photo of her child, captioned warmly, is the conversion moment. Everything before that is friction.

---

### Persona 3: The Admin / Principal

**Name:** Rajesh (representative)
**Role:** Principal or school owner, manages 1-5 centers
**Device:** Laptop or desktop (primary for admin work), smartphone for quick checks
**Technical comfort:** Medium — uses email, WhatsApp, Tally; not a SaaS-native user

**Primary Job-to-be-Done:** Know his schools are running well without being on-site at every one. Specifically: are teachers posting? Are parents engaged? Are fees collected?

**Secondary Jobs:**
- Act on exceptions fast (low-engagement class → message that teacher directly)
- Manage admissions pipeline (who inquired, who enrolled)
- See attendance and fee status across all centers in one view

**Current pain:**
- Has no aggregate visibility across centers — he calls teachers individually, which doesn't scale
- Uses separate tools for fees (Tally), attendance (paper), and parent communication (WhatsApp) — no single view
- Cannot show prospective parents a track record of parent engagement during admissions

**Fear:** Complexity. He is not a software person. The admin dashboard must give him the answer in the first screen, not after navigating 4 menus.

---

## 3. Phase 1 Epics and User Stories

### Overview

Phase 1 is organized into 7 core epics (Epics 1–7) covering the complete product. Epics 8–13 capture closely related Phase 2+ expansions that should be considered during design but are not in Phase 1 build scope. All stories are scoped to deliver Phase 1 launch criteria (Month 10).

---

### Epic 1: School Onboarding & Multi-Tenancy Foundation
**Goal:** Enable a school to sign up, configure their account, and invite teachers — without founder involvement.
**Priority:** P0 — nothing else works without this.
**Timeline:** Month 1-2

---

**Story 1.1: Self-Serve School Registration**
As a school owner, I want to register my school at cadencesprout.com so that I can start using the platform without speaking to a salesperson.

Acceptance Criteria:
- Given I visit cadencesprout.com/signup, when I enter school name, phone number, and create a password, then a new school account is created and I am redirected to the admin dashboard
- Given I complete registration, then my school gets a unique subdomain (e.g., sunrise-preschool.cadencesprout.com)
- Given registration is complete, then a Rekognition face collection is automatically created for my school (`school_{id}`)
- Given registration is complete, then I am shown a 4-step setup checklist: (1) Add your logo, (2) Create classes, (3) Add teachers, (4) Add children
- Given the school name is already taken, when I submit, then I see "This school name is taken — try adding your city (e.g., Sunrise Preschool Mumbai)"

---

**Story 1.2: School Profile & Branding Setup**
As a school admin, I want to upload my school logo and set my school name so that parents see a branded experience.

Acceptance Criteria:
- Given I am in School Settings, when I upload a logo image (PNG/JPG, max 5MB), then it is stored on S3 and displayed in the parent app header
- Given Phase 1, when the parent app loads, then it shows school logo + "Powered by CadenceSprout" side-by-side (full white-label is Phase 3)
- Given I update the school name, then all parent-facing views reflect the new name within 5 minutes

---

**Story 1.3: Class Creation**
As a school admin, I want to create classes and assign teachers so that the system knows which teacher manages which group of children.

Acceptance Criteria:
- Given I am in the Classes section, when I create a class with name, academic year, and teacher assignment, then the class appears in the teacher's app
- Given I create a class, when I assign a teacher who has not yet been invited, then the system shows "Invite this teacher first" with a shortcut to the invite flow
- Given a class is created, then it has a unique class_id used for all feed and attendance scoping
- Given I need multiple sections (e.g., Nursery A, Nursery B), then I can create them as separate classes and assign different teachers

---

**Story 1.4: Teacher Invitation**
As a school admin, I want to invite teachers by phone number so that they can log into the teacher app.

Acceptance Criteria:
- Given I enter a teacher's phone number and name, when I tap Invite, then the teacher receives an SMS with a one-time setup link
- Given the teacher taps the setup link, then they are prompted to set a password and are logged into the React Native teacher app
- Given the teacher is set up, then they appear in the Staff Management list with their name, role (Teacher), and class assignment
- Given I invite a teacher who is already registered, then the system shows "This phone number is already registered" without creating a duplicate

---

**Story 1.5: Multi-Tenancy Enforcement (Engineering)**
As the engineering team, I want PostgreSQL row-level security to enforce school_id isolation so that School A's data is never accessible to School B.

Acceptance Criteria:
- Given a teacher from School A makes any API request, when the RLS policy is applied, then queries only return rows where school_id matches School A
- Given a query is made without school_id in context, then the query returns 0 rows — not an error, not another school's data
- Given an integration test is run for multi-tenancy, then it explicitly proves School A's teacher cannot read School B's posts, children, or users
- Given any new table is created, then it must include school_id and a corresponding RLS policy before it is merged to main

---

### Epic 2: Child Enrollment & Parent Onboarding
**Goal:** Get children into the system with parent contact details and DPDP consent, enabling the feed and face recognition to work.
**Priority:** P0
**Timeline:** Month 1-2

---

**Story 2.1: Child Profile Creation**
As a school admin or teacher, I want to add a child's profile so that they can be tagged in posts and tracked for milestones.

Acceptance Criteria:
- Given I create a child profile, then the required fields are: name, date of birth, class assignment
- Given I create a child profile, then I can optionally upload an enrollment photo (used as the Rekognition reference face)
- Given an enrollment photo is uploaded, then it is stored at `children.face_embedding_s3_key` and a Rekognition IndexFaces call is queued
- Given no enrollment photo is uploaded, then face recognition is skipped for that child (manual tagging only)
- Given I add a child, then I see a prompt: "Add parent phone number to invite them to the feed"

---

**Story 2.2: Parent Invitation via Magic-Link**
As a school admin, I want to invite parents by phone number so that they receive a WhatsApp link to see their child's feed without installing an app.

Acceptance Criteria:
- Given I add a parent's phone number and name for a child, then the system creates a magic_link_tokens record (expires 30 days, max 10 uses)
- Given the token is created, then Wapi sends a WhatsApp message: "[School name]: [Child name] has been added to CadenceSprout. See their updates here: [magic-link URL]"
- Given Wapi delivery fails, then MSG91 sends an SMS fallback within 2 minutes
- Given one child has two parents (mother + father), then both can be added with separate phone numbers and separate magic links
- Given I add a parent, then they appear in the child's profile with status: "Invited — not yet activated"

---

**Story 2.3: Magic-Link Web View — Feed First**
As a parent, I want to tap a WhatsApp link and immediately see my child's feed so that I don't have to install an app to see the first update.

Acceptance Criteria:
- Given I tap a valid magic link, then the browser opens and within 2 seconds I see the most recent post for my child (full-bleed photo, caption, child tag)
- Given this is my first view, then no login prompt is shown — I see the feed immediately
- Given I tap the ❤️ reaction on a post, then the reaction is recorded without requiring any login
- Given I have viewed 3 posts (used_count >= 3), then a dismissible banner appears: "Get the app for all of [child name]'s updates" — this is a banner, not a modal, and never blocks the feed
- Given a magic link has expired (> 30 days) or exceeded max uses, then I see: "This link has expired. Ask your school to send a new one." with a WhatsApp link to the school's phone number (410 response)
- Given a magic link token is valid, then the used_count is incremented on each page load

---

**Story 2.4: Parent App Registration (OTP)**
As a parent who wants to install the app, I want to register with my phone number and OTP so that I get full access to my child's feed.

Acceptance Criteria:
- Given I tap "Get the app" from the magic-link web view, then I am directed to the App Store / Play Store
- Given I open the app for the first time, then I enter my phone number and request an OTP
- Given I enter the correct OTP, then I am logged in and my account is linked to my existing magic-link identity (same parent_id)
- Given I enter an expired OTP (> 10 minutes), then I see "This code has expired. Request a new one." with a Resend button
- Given I am a new parent not yet added by the school, then after OTP verification I see: "Ask your school to add you to [School Name]." with a WhatsApp link to the school's number

---

**Story 2.5: DPDP Consent Collection**
As a parent, I want to understand clearly what data CadenceSprout collects about my child so that I can give informed consent.

Acceptance Criteria:
- Given I log in to the app for the first time, then before I see the feed I am shown the DPDP consent screen
- Given the consent screen is shown, then it displays the school's logo at the top, the title "Your child's privacy is our first commitment.", and three individually-checkable items (all pre-checked):
  - "Share daily updates with you only"
  - "Recognise [child name] in class photos (AI — server-side)"
  - "Store data in India (deleted when you leave)"
- Given I uncheck any item, then I can still proceed — consent is per-type, not all-or-nothing
- Given I uncheck "Recognise [child name] in photos", then `children.dpdp_consent_at` remains NULL and face recognition is never called for that child
- Given I tap [See full privacy policy], then a modal opens with the full policy text — it does not navigate away from the consent screen
- Given I tap [I agree], then my consent choices are stored in `children.dpdp_consent_items` (jsonb) with a timestamp
- Given I have already given consent, then the consent screen is never shown again for that child
- Given I go to Profile > Data & Privacy, then I can revoke any consent type at any time
- Given I revoke face recognition consent, then a background job deletes my child's Rekognition data within 24 hours

---

### Epic 3: Teacher Post Flow (The Core Loop — FULLY REWRITTEN)
**Goal:** Enable teachers to capture → post → confirm engagement with minimal effort (< 5 minutes/day).
**Priority:** P0 — this is the product's primary daily usage loop.
**Timeline:** Month 3-4 (feed) + Month 5-6 (AI layer)

---

**Story 3.0: Daily Posting Guidance**
As a teacher, I want the app to guide me to post daily so I don’t forget.

Acceptance Criteria:
- If no post has been created by 12 PM local time, a reminder banner is shown on the Teacher Home Feed prompting the teacher to share an update. The copy should be emotionally framed from the parent's perspective (e.g., "Parents haven’t seen an update today" with subtext like "Share even a small moment from class").
- If no post has been created by 3 PM local time, the floating action button (FAB) on the Teacher Home Feed pulses to draw attention to posting.
- After at least one post is created for the day, the reminder banner and FAB pulse stop for that day and a positive reinforcement message is shown (e.g., "Nice work — today's update is live for parents.").

---

**Story 3.1: Photo/Video Selection**
As a teacher, I want to select photos or a video from my camera roll in 1 tap so that posting feels as fast as sending to WhatsApp.

Acceptance Criteria:
- Given I am on the Home Feed screen, then a floating action button (FAB) is visible at the bottom right at all times
- Given I tap the FAB, then the native camera roll opens immediately (system sheet) — no intermediate screen
- Given I select 1-4 photos, then I proceed to the Post Composer screen
- Given I select a video, then the system checks file size. If > 50MB, client-side compression runs (target output: < 10MB). If compression fails, I see "This video is too large — please trim it or choose a shorter clip."
- Given I select a video > 10MB that cannot be compressed under 10MB, then upload is rejected before it starts
- Given I tap the FAB and my camera roll permission is denied, then I see a prompt: "Camera roll access is needed to post photos" with a button to open Settings

---

**Story 3.2: Post Composer — AI Caption Draft**
As a teacher, I want to see an AI-drafted caption for my photo so that I don't have to write from scratch every time.

Acceptance Criteria:
- Given I have selected photo(s) and arrived at the Post Composer, then immediately an inline shimmer animation shows in the caption area with text "Drafting caption..."
- Given the AI caption is ready (< 3 seconds target), then it appears in Fraunces serif font with a subtle ✨ icon, and I can edit it inline
- Given the caption is editable, then if I modify it, `posts.caption_edited_by_teacher` is set to true (for DPDP audit trail)
- Given the OpenRouter API fails or times out, then the caption area shows an empty field with placeholder text "What happened in this moment?" — no error message is shown
- Given a caption is generated, then it is ≤2 sentences, warm in tone, and only names children who have been confirmed as tags (confidence > 80% AND teacher-confirmed) — unconfirmed children are referred to as "the children"
- Given the AI draft is generated, then the teacher can post as-is without any required edit

---

**Story 3.3: Post Composer — Child Tag Suggestions**
As a teacher, I want to see which children are in my photo (suggested by AI) so that I can confirm tags before posting.

Acceptance Criteria:
- Given I arrive at the Post Composer, then face recognition runs asynchronously in the background — it never blocks the posting UI
- Given face recognition is pending, then child chips display in a greyed/dashed state with text "Identifying..."
- Given face recognition returns results, then suggested chips are rendered under a label such as "AI detected these children" and each chip displays the child name plus a confidence indicator (e.g., "Rohan · 92%").
- Given face recognition returns results, then chips with confidence > 90% show as high-confidence suggestions, and chips with 70–90% show as low-confidence suggestions (visually distinct). Chips with < 70% confidence are not shown at all.
- Given I want to confirm or reject a suggested tag, then each AI-suggested chip exposes quick actions (✓ confirm / ✕ remove) so I can explicitly accept or remove the suggestion with one tap.
- Given I tap to confirm a suggested chip (via ✓ or by tapping the chip), then the chip turns into a "confirmed" state and the child's name may appear in the caption draft if applicable.
- Given I tap ✕ on a suggested chip, then the chip is removed and the child is removed from `post_children` and will not appear in parents' feeds.
- Given face recognition fails or no consent exists for a child, then no chips appear and I see "Add children manually" — a tappable area that opens a child picker from the class roster
- Given a child has no DPDP consent (`dpdp_consent_at IS NULL`), then Rekognition is NOT called for that child — they must be tagged manually
- Given I want to post without tagging any child, then this is allowed — the post goes to all parents in the class

---

**Story 3.4: Post Composer — Milestone Tags (Optional)**
As a teacher, I want to optionally tag developmental milestones I observed so that the milestone tracker is populated over time.

Acceptance Criteria:
- Given I am on the Post Composer, then a "Add milestones" tappable row is visible below the child tags section — it is clearly optional
- Given I tap "Add milestones", then a modal opens showing the NEP 2020 milestone taxonomy grouped by domain (physical, cognitive, language, social-emotional, aesthetic)
- Given I select a milestone, then it appears as a tag chip on the post
- Given the AI milestone suggestion runs, then 1-2 milestone suggestions may appear as pre-selected chips that I can accept or remove
- Given I skip milestone tagging, then the post publishes successfully — milestones are never required

---

**Story 3.5: Post Submission and Optimistic UI**
As a teacher, I want to tap Post and immediately see it in my feed so that I feel confident it was sent.

Acceptance Criteria:
- Given I tap [POST], then the post appears in the feed immediately (optimistic UI) — I do not wait for the upload to complete
- Given the upload is < 80% complete, then the optimistic post shows with a blurred/faded overlay and a progress bar
- Given the upload completes, then the blur is removed and the post appears in full quality
- Given the upload fails (network drop), then a toast appears: "Upload failed. Tap to retry." The post remains visible in my feed as a draft with a retry indicator and the underlying post content (media + caption + tags) is persisted so that no work is lost.
- Given I tap retry, then the upload resumes with exponential backoff (retry 1: 5s, retry 2: 10s, retry 3: 20s)
- Given the post is published, then a Pusher event is broadcast to all parents of tagged children on the `class.{class_id}.feed` channel
- Given the post is published, then a Wapi WhatsApp notification is sent to parents of tagged children (or all class parents if no specific tags): "[School name]: [Child name] had a great moment today! See it here: [magic-link]"

---

**Story 3.6: Optional Daily Report Fields (NEW)**
As a teacher, I want to optionally add a short daily report to my post so that admins and parents can see a structured summary of the day without adding extra work.

Acceptance Criteria:
- Given I am on the Post Composer, then there is an optional, collapsed "Daily report (optional)" section below the caption and tags, which I can expand to fill in structured fields such as: meal summary, nap summary, and key activities.
- Given I do not expand or fill any daily report fields, then posting works exactly as today and no extra fields are required; the feature must never block the core post flow.
- Given I choose to fill daily report fields, then those values are saved alongside the post in structured form (e.g., `post_daily_report` object) and can be surfaced in admin/parent reporting surfaces (e.g., daily summary, dashboards) without changing the visual layout of the core photo post.
- Given a daily report has already been submitted for today for a given class, then the composer can pre-fill or indicate that a report exists (e.g., "Daily report already added today"), and additional posts default to not including another report unless the teacher explicitly edits it.

---

**Story 3.7: Drafts and Offline Posting (NEW)**
As a teacher, I want my in-progress posts to be safely saved and retried if the network is unreliable so that I never lose work.

Acceptance Criteria:
- Given I have started composing a post (media selected and/or caption entered) but have not tapped [POST], then the app auto-saves my draft at sensible intervals (e.g., on navigation away or every N seconds) so that closing the composer does not lose my work.
- Given I re-open the Post Composer on the same day with an unsent draft, then I see a clear but lightweight prompt such as "You have an unsent draft from today" with actions to **Resume draft** or **Discard**.
- Given I tap **Resume draft**, then the previously saved media, caption, and child tags are restored into the composer.
- Given I tap **Discard**, then the draft is deleted and the composer starts empty.
- Given I tap [POST] while the device is offline or the network fails immediately, then the app informs me that the post will be sent when back online (e.g., "Offline — this post will send when you're back online"), and the post is queued locally for retry instead of being discarded.
- Given a post is queued for retry, then it appears in my feed as a draft/outbox item with a clear state indicator (e.g., clock icon / "Sending when online") and will automatically retry when connectivity is restored.
- Given I do not want a queued post to send anymore, then I can cancel it from the draft/outbox state (e.g., "Cancel" action on the draft card), which removes it from the queue and from parents' future feeds.

---

**Story 3.8: Inline Incident Logging (NEW)**
As a teacher, I want an optional way to log an incident while posting so that important events are recorded in context without requiring a separate complex workflow.

Acceptance Criteria:
- Given I am composing a post and something notable but sensitive happens (e.g., a minor fall, behavioural incident), then I can expand an "Incident (optional)" section in the composer that lets me add: incident type (dropdown), brief description, time, and whether parents should be notified.
- Given I submit a post with an incident attached, then the system creates a linked `incident` record associated to the child(ren), class, and post, and this record becomes visible in the admin's Child Records / Compliance view (Epic 16) without surfacing the full incident details in the public parent feed.
- Given an incident is logged with "notify parents" enabled, then the relevant parents receive an appropriate notification (e.g., "Your child had a minor incident today; please see the note from school.") and see a clear but sensitive note attached to the relevant post or in a dedicated incident section, per product copy decisions.
- Given no incident is logged, then the post behaves as a normal post and no incident records are created; the presence of the incident section must not alter the default post flow.

---

**Story 3.6: Teacher Home Feed (UPDATED)**
As a teacher, I want to know what I’ve done today and what is pending so I can complete my work quickly.

Acceptance Criteria (UPDATED):
- Given I open the app, then the top of the Home Feed shows a daily status header for today's date.
- Given I have not created any posts for my class today, then the daily status header shows a clear CTA to post (e.g., "No update yet — share a moment from today") that deep-links to the Post Composer.
- Given I have created at least one post today, then the daily status header shows positive reinforcement (e.g., "Today's update is live — parents are seeing it now") instead of a CTA.
- Given I scroll the Home Feed, then today's posts appear in a "Today" section at the top, followed by prior days' sections in reverse chronological order.
- Given the feed loads, then I see for each post: full-bleed photo, caption in Fraunces font, child tag chips, posted time, a "Viewed by X parents" count, and a "% reach" indicator (X ÷ total enrolled parents for the class).
- Given I am on the Home Feed, then the FAB is always visible in the bottom-right corner; if I have not yet posted for today, the FAB uses a pulsing animation state (per Story 3.0) until my first post for the day is successfully created.
- Given I pull to refresh, then new posts load and the daily status header and reach metrics update.
- Given the network is unavailable, then a persistent banner at the top shows "You're offline — showing saved content" while still showing the last known daily status header.
- Given I tap a post, then I see the Post Detail screen with full photo, full caption, child tags, milestone tags, and parent view count.

---

### Epic 4: Parent Feed Experience (REWRITTEN)
**Goal:** Ensure parents feel, "I didn’t miss anything important today" about their child’s school day.
**Priority:** P0
**Timeline:** Month 3-6

---

**Story 4.1: Parent Home Feed (UPDATED)**
As a parent, I want to quickly understand my child’s day so that I feel I haven’t missed anything important.

Acceptance Criteria:
- Given I open the parent app, then the top of the Home Feed shows a daily summary card for today's date before the list of posts.
- Given at least one post exists today where my child is tagged, then the daily summary card shows an emotional heading such as "Here’s what [child name] did today" plus a brief summary (e.g., number of moments shared, any milestones observed today).
- Given no posts exist yet today, then the daily summary card sets expectations positively (e.g., "Today’s update will appear after morning circle.") and does not show an empty feed as an error state.
- Given I scroll the Home Feed, then the structure is: (1) daily summary card, followed by (2) posts where my child is tagged, grouped by day in reverse chronological order.
- Given a post exists where my child is not tagged but the class posted, then that post is NOT shown in my personal feed.
- Given the feed is loading, then I see skeleton cards (warm cream rectangles, pulsing) for both the summary card and posts — not a spinner.
- Given I see a post card, then a subtle prompt (e.g., "React to let the teacher know you saw this") appears next to the ❤️ reaction to encourage engagement.
- Given I have reacted to or commented on all posts for today, then the daily summary card reflects this with a "You’re all caught up for today" message.
- Given the network fails, then I see: "Couldn't load — check your connection." with a Retry button, and the last known daily summary and posts remain visible (stale-while-revalidate).
- Given I scroll to the bottom of the feed, then the next page of older posts loads automatically (cursor-based pagination).
- Given my child's class has posted in the last 7 days but there are no posts where my child is tagged in that period, then the Home Feed shows a gentle empty state for this week (e.g., "This week has been quiet so far" and a smaller line such as "If you're expecting updates, you can check with your school.") instead of a hard error.
- Given I tap a "Check with your school" CTA from that empty state, then the app opens the platform's default mail/SMS/WhatsApp chooser prefilled with the school's contact details, so I can easily reach out without the product taking a strong stance on the channel.

---

**Story 4.2: Post Detail and Reactions**
As a parent, I want to react to a post and add a comment so that the teacher knows I saw it.

Acceptance Criteria:
- Given I tap a post in the feed, then I see a full-screen photo view with the caption, child tags, milestone tags (if any), post time, and school logo
- Given I tap the ❤️ reaction button, then my reaction is recorded immediately and the count increments
- Given I want to comment, then I can type a comment that is visible to the teacher in the Post Detail view
- Given a teacher sees a parent's comment, then they receive an in-app notification
- Given the teacher's post had an AI-drafted caption that was not edited, then there is no visible indication that AI wrote it — it appears as the teacher's own words
 - Given I react to or comment on today's posts from the Post Detail screen, then the Parent Home Feed daily summary card updates to reflect that I have engaged with today’s updates (e.g., shows a checkmark and "You’ve reacted to today’s update").
 - Given I notice that a post appears to show the wrong child or tags, then I can tap a clear but non-threatening control (e.g., "Report incorrect tagging") on the Post Detail screen.
 - Given I tap "Report incorrect tagging", then I see a simple confirmation dialog/sheet explaining that the issue will be shared with the school admin, with an optional text field and a primary "Send report" action.
 - Given I submit a tagging report, then the system records a structured `post_reports` event (post_id, parent_id, reason_text, type = INCORRECT_TAGGING) and shows a brief confirmation to the parent (e.g., "Thanks, we've shared this with the school.").

---

**Story 4.3: Milestone Progress View**
As a parent, I want to see a summary of which developmental milestones my child has crossed so that I understand their progress.

Acceptance Criteria:
- Given I navigate to my child's profile, then I see a "Milestones" section showing progress by domain (physical, cognitive, language, social-emotional, aesthetic)
- Given a milestone has been teacher-confirmed on a post, then it shows as achieved with the date
- Given no milestones have been logged yet, then I see: "Milestones will appear here as teachers observe them in class." — no CTA, educational tone
- Given I tap a milestone, then I see the posts where that milestone was observed (photo + caption)
 - Given a new milestone is observed today, then it can surface as a highlight in the Parent Home Feed daily summary card (e.g., "New milestone observed today in [domain]").

---

**Story 4.4: Year-End Portfolio (AI-Generated)**
As a parent, I want to receive an AI-generated year-end portfolio for my child so that I have a beautiful developmental record to keep.

Acceptance Criteria:
- Given the academic year ends (or the principal triggers portfolio generation), then the system queues a PortfolioGenerateJob for each child in the nightly batch queue
- Given the job runs, then it compiles all confirmed posts + milestone achievements for the child into a PDF document
- Given the PDF is generated, then the parent sees a "Year-End Portfolio Ready" notification
- Given I tap the notification, then I see a full-screen portfolio preview in the app
- Given I want to save the portfolio, then I can download it as a PDF
- Given a child has fewer than 5 posts in the year, then the portfolio is still generated with available content — no minimum threshold blocks generation
 - Given a new section of the portfolio becomes available (e.g., after year-end generation), then the Parent Home Feed daily summary card can surface this as an insight (e.g., "[Child name]’s year-end portfolio is ready to view").

---

**Story 4.5: Fees & Payments Visibility in Parent Experience (NEW)**
As a parent, I want fees and payments to be visible alongside my child's updates so that I don't have to juggle multiple tools to stay on top of school payments.

Acceptance Criteria:
- Given I am using the Parent app, then there is a simple, consistent entry point (e.g., "Fees" tab or card under Profile / Home) that lets me see pending and paid invoices for my child, reusing the same underlying fee data model as the Admin dashboard.
- Given an invoice is created or updated for my child, then I can see its status (Pending / Paid / Overdue), due date, and amount within the app, without needing to contact the school.
- Given online payments (UPI) are enabled for my school, then each pending invoice clearly shows a "Pay now" CTA that opens a UPI-compatible flow; after a successful payment, the invoice status updates to Paid within a reasonable time.
- Given an invoice becomes overdue, then I receive a gentle in-app notification and/or feed-level banner (per notification rules) reminding me to pay, without spamming or blocking access to my child's feed.

---

**Story 4.6: Incident Notifications and Child Documents (NEW)**
As a parent, I want to be notified about important incidents and have access to key documents so that I feel informed and reassured about my child's safety and records.

Acceptance Criteria:
- Given a teacher or admin logs an incident for my child with "notify parents" enabled, then I receive a clear, sensitive notification in the app (and optionally via WhatsApp/SMS per configuration) indicating that an incident occurred today, with a tap-through to a secure incident detail view.
- Given I open an incident detail, then I can see: date/time, high-level type (e.g., minor injury, behaviour), a brief description written by the school, and any relevant follow-up notes; incident details are **never** mixed into the public photo feed but are accessible from a dedicated "Incidents" section under my child's profile.
- Given the school uploads important child documents (e.g., birth certificate, ID proof, medical certificates) to my child's record, then I can view a list of available documents from a "Documents" section under my child's profile and securely view/download them where appropriate.
- Given no incidents or documents exist yet, then the respective sections show a gentle empty state explaining that incidents/documents will appear here when added, without suggesting that something is missing.

---

### Epic 5: Attendance Tracking
**Goal:** Enable teachers to take daily attendance in under 2 minutes per class.
**Priority:** P0 (required for ERP layer)
**Timeline:** Month 7-8

---

**Story 5.1: Daily Attendance — Teacher**
As a teacher, I want to mark attendance for my class each morning so that the school has a daily record.

Acceptance Criteria:
- Given I open the Attendance tab, then I see today's date and my class roster with Present / Absent toggles for each child
- Given today's attendance has not been taken, then I see a prominent CTA: "Take today's attendance."
- Given I mark all children and tap Submit, then attendance is saved and I see a confirmation: "Attendance submitted for [date]"
- Given a child is absent, then I can optionally add a reason (Sick / Family reason / Other) — this is optional, not required
- Given I submit attendance, then the admin dashboard attendance tile updates
- Given I reopen attendance after submission, then I can edit it until the end of the school day (midnight cutoff)

---

**Story 5.2: Attendance Dashboard — Admin**
As a school admin, I want to see attendance across all classes so that I can spot patterns.

Acceptance Criteria:
- Given I open the Attendance section in the web dashboard, then I see a school-wide heatmap: rows = classes, columns = dates (past 30 days), cells = attendance percentage (green ≥80%, amber 60-79%, red <60%)
- Given I click on a class-date cell, then I see the individual child attendance for that day
- Given attendance has not been submitted for a class today, then the cell shows "Not submitted" in grey
- Given I need to export attendance, then I can export a CSV for any date range

---

**Story 5.3: Attendance Insight (Admin)**
As a school admin, I want to see attendance trends and low-attendance alerts so that I can intervene early.

Acceptance Criteria:
- Given I open the Attendance section or Dashboard, then I can see school-level and class-level attendance trends over a selectable period (e.g., 7 and 30 days), highlighting classes with declining attendance.
- Given a class’s average attendance drops below a defined threshold (e.g., < 60% over the last 7 school days), then it appears in a "Low attendance" alert list for admins.
- Given an individual child has been absent for several consecutive days (configurable, e.g., ≥3), then an alert is generated so the admin can follow up with the family.
- Given I click any low-attendance alert, then I am taken to the relevant class-day or child-level detail view with attendance history pre-filtered.

---

### Epic 6: Fee Management
**Goal:** Enable admins to create and track manual invoices for school fees, replacing Tally/spreadsheet workflows.
**Priority:** P0 (required for Phase 1 billing)
**Timeline:** Month 7-8

---

**Story 6.1: Fee Invoice Creation**
As a school admin, I want to create a fee invoice for a student so that I have a formal record of what is owed.

Acceptance Criteria:
- Given I navigate to Fee Management and select a child, when I tap "Create Invoice", then I can enter: fee type (Tuition / Activity / Transport / Other), amount, due date, and a description
- Given I create an invoice, then it appears in the child's fee history with status: Pending
- Given I need to create invoices for a full class at once, then I can select a class and bulk-create the same invoice for all enrolled children
- Given I tap "Preview Invoice", then I see a formatted invoice that can be printed (CSS `@media print` compatible)

---

**Story 6.2: Fee Payment Tracking**
As a school admin, I want to mark invoices as paid and see overdue fees so that I can follow up efficiently.

Acceptance Criteria:
- Given a payment is received, when I mark an invoice as Paid and enter the payment method (Cash / UPI / Bank transfer), then the invoice status updates to Paid with timestamp
- Given an invoice is past its due date and unpaid, then it appears in the "Overdue" section in the Fee Management dashboard
- Given the admin dashboard loads, then the Fee tile shows: "X invoices overdue" and the total overdue amount
- Given no invoices are outstanding, then the fee tile shows: "You're all caught up! No pending fees." — a positive state
- Given I need to export fee records, then I can export a CSV of all invoices for any date range

---

**Story 6.3: Fee Status in Admin Dashboard**
As a school admin, I want to see fee collection status at a glance on my dashboard so that I don't need to go into fee management to know if there's a problem.

Acceptance Criteria:
- Given I open the admin dashboard, then the Fee tile shows: total invoiced this month, total collected, and count of overdue invoices
- Given there are overdue invoices, then the tile shows an alert indicator (terracotta color)
- Given I tap the Fee tile, then I am taken to the Fee Management screen filtered to Overdue

---

**Story 6.4: Parent Fee Visibility**
As a parent, I want to see my child’s pending school fees and reminders in the app so that I can stay on top of payments.

Acceptance Criteria:
- Given I am a parent with an active child profile, then I can access a "Fees" view or card from my app (e.g., via Profile or a Fees tab) showing my child’s invoices.
- Given an invoice exists for my child, then I can see: fee type, amount, due date, and status (Pending / Paid / Overdue).
- Given an invoice is overdue, then it is clearly labeled as Overdue and appears at the top of my fee list with a gentle reminder message.
- Given I have no pending or overdue invoices, then the Fees view shows a positive reinforcement state (e.g., "All caught up — no pending fees for [child name].").
- Given the school has provided payment instructions (e.g., UPI, bank transfer), then each pending invoice includes a "How to pay" section or link.
- Given a payment is marked as Paid by the school, then the status in my parent app updates within a reasonable time (e.g., within 1 hour) without requiring reinstall or re-login.

---

### Epic 7: Admin Dashboard & Engagement Score (REWRITTEN)
**Goal:** Enable admins to identify issues and act within seconds from a single dashboard view.
**Priority:** P0
**Timeline:** Month 5-6 (engagement score) + Month 7-8 (ERP tiles)

---

**Story 7.1: Dashboard Home — Engagement Score Hero**
As a school admin, I want to see my school's parent engagement score as the first thing on my dashboard so that I know immediately if teachers are posting and parents are viewing.

Acceptance Criteria:
- Given I open the web dashboard, then the hero section shows the current engagement score as a large number (e.g., "73%") with a trend arrow (↑ or ↓) and the previous week's score ("was 61% last week")
- Given the score is ≥ 70%, then it displays in sage green (#5C8B6E) with positive reinforcement: "Parents are loving it!"
- Given the score is < 30%, then it displays in terracotta (#C4784A) with an alert badge and: "3 classes haven't posted this week."
- Given it is the school's first week (no prior history), then the trend arrow is hidden and the text reads: "Come back next week to see your trend."
- Given no parents are enrolled yet, then the hero shows: "Add parents to start measuring engagement." with a link to enrollment
- Given I want to understand how the score is calculated, then a small info icon opens a tooltip: "Engagement = parents who viewed at least 1 post this week ÷ total enrolled parents"

---

**Story 7.2: Dashboard Tiles — Posts, Attendance, Fees**
As a school admin, I want to see today's posts, attendance, and fee status in three tiles below the engagement score so that I have a complete morning check in one view.

Acceptance Criteria:
- Given I open the dashboard, then three tiles appear below the engagement score: (1) Posts Today, (2) Attendance Today, (3) Fee Alerts
- Given the Posts Today tile loads, then it shows: total posts today, broken down by class
- Given the Attendance Today tile loads, then it shows: % of classes that have submitted attendance today
- Given the Fee Alerts tile loads, then it shows: count of overdue invoices
- Given I tap any tile, then I navigate to the corresponding detailed view (Posts, Attendance, or Fee Management)

---

**Story 7.7: Fee Lifecycle & Revenue Overview (NEW)**
As a school admin, I want a clear view of fee plans, collections, and overdue amounts so that I can manage revenue without deep spreadsheets.

Acceptance Criteria:
- Given I open the Admin dashboard, then in addition to the core engagement hero and tiles, there is a concise fee/revenue summary widget or tile that shows: total invoiced this period, total collected, and total overdue, with a quick visual indicator if overdue exceeds a threshold.
- Given I tap the fee/revenue summary, then I am taken to a fees dashboard or filtered Fee Management view where I can drill down by class, fee plan, and time range to see which families are overdue and by how much.
- Given new invoices are created or payments recorded, then the dashboard-level fee KPIs update on the next refresh or within a defined polling window so I can rely on them during daily checks.

---

**Story 7.8: Admissions Funnel Overview (NEW)**
As a school admin, I want to see my admissions pipeline at a glance on the dashboard so that I know if future enrollments are on track.

Acceptance Criteria:
- Given I open the Admin dashboard, then an admissions funnel widget is visible, summarising counts at each stage (e.g., New Inquiry, Tour Scheduled, Seat Offered, Enrolled, Not Joining) for the current and upcoming academic terms.
- Given I tap any stage in the admissions funnel, then I am taken to the Admissions CRM view (Epic 15) pre-filtered to that stage and term, so I can follow up with specific leads.
- Given there is a sudden drop-off between stages (e.g., many tours but few seats offered), then the funnel widget can surface a subtle alert or highlight, and this pattern can also feed into Admin Intelligence (Epic 13) for more detailed insights.

---

**Story 7.9: Staff Overview Snapshot (NEW)**
As a school admin, I want a high-level staff overview on the dashboard so that I can understand staff coverage and potential issues quickly.

Acceptance Criteria:
- Given I open the Admin dashboard, then a staff snapshot tile is visible, showing: total active staff, staff per center/class, and any key alerts (e.g., unassigned classes, staff with missing profiles) sourced from the Staff Management module (Epic 17).
- Given staff attendance and leave tracking is enabled, then the staff snapshot can also show today's presence overview (e.g., "3 staff on leave today"), with a CTA that deep-links into the staff attendance/leave view.
- Given I tap the staff snapshot tile, then I am taken to the Staff Management view where I can see staff profiles, assignments, and relevant filters.

---

**Story 7.3: Class Breakdown Table**
As a school admin, I want to see engagement ranked by class so that I can identify and act on low-activity classes.

Acceptance Criteria:
- Given I scroll below the tiles, then I see a Class Breakdown table sorted by engagement percentage, lowest first
- Given a class has not posted this week, then its engagement shows as 0% in red
- Given I see a low-engagement class, then each row has a quick-action: "Message teacher" — tapping opens a pre-filled WhatsApp message to that teacher's phone number: "Hi [Teacher name], can you post an update for your class today?"
- Given I tap a class row, then I navigate to a class-level detail view showing posts, attendance, and enrolled children

---

**Story 7.4: Engagement Score Calculation (Engineering)**
As the engineering team, I want the engagement score to be calculated as a weekly snapshot so that it does not impact read performance.

Acceptance Criteria:
- Given a scheduled job runs every Sunday at midnight, then it calculates and stores a new `engagement_snapshots` record per school: score_pct = (parents who viewed ≥1 post this week / total enrolled parents) × 100
- Given the dashboard loads, then it reads from the `engagement_snapshots` table — it does not recalculate on request
- Given a school has 0 enrolled parents, then the snapshot stores score_pct = 0 and a flag indicating "no parents enrolled"
- Given the snapshot calculation is tested, then: score = 100 when all parents viewed ≥1 post; score = 0 when no parents viewed; score is stored as integer, not floating point

---

**Story 7.5: Alerts Panel**
As a school admin, I want a single alerts panel that surfaces the most important issues (engagement, fees, attendance) so that I know where to act first.

Acceptance Criteria:
- Given I open the Dashboard Home (A-1), then an Alerts panel appears at the top of the screen, above the engagement hero and tiles.
- Given there are issues detected by the system, then alerts are grouped by type (e.g., Low engagement, Fee issues, Attendance issues) with a short description and severity indicator.
- Given a "Low engagement" alert exists, then it clearly states the affected classes or segments (e.g., "3 classes have engagement < 30% this week").
- Given a "Fee issues" alert exists, then it summarizes the number of overdue invoices and total overdue amount.
- Given an "Attendance issues" alert exists, then it highlights classes with low attendance or missing submissions (e.g., "Attendance not submitted for 2 classes today").
- Given any alert is shown, then it includes a clear CTA button or link (e.g., "View class", "Go to Fees", "View attendance") that deep-links to the relevant detailed screen with filters applied.
 - Given a "Low engagement" alert exists and I tap its CTA, then I am taken to the engagement drilldown or Class Breakdown view pre-filtered to only the affected classes, with those rows scrolled into view so I can immediately see which teachers/classes need attention.
 - Given a "No posts today"-type alert exists (e.g., "3 classes haven't posted today"), then tapping its CTA opens a pre-filtered Posts/Classes view listing only classes with zero posts today, including teacher names and a per-row quick action (e.g., "Message teacher") so I can prompt them to post.

---

**Story 7.6: Engagement Drilldown**
As a school admin, I want to drill down into engagement to see inactive parents and class-level insights so that I can take targeted action.

Acceptance Criteria:
- Given I am on the Dashboard Home and tap the engagement score hero or a class row in the Class Breakdown table, then I can open an engagement drilldown view.
- Given the drilldown view loads, then I can filter by class and time range (e.g., this week, last week) and see engagement by class and segment.
- Given I select a class, then I see a list of parents for that class with indicators such as "Active this week" vs. "Inactive this week" based on view activity.
- Given I view a list of inactive parents, then I can export the list or trigger a follow-up (e.g., via pre-filled WhatsApp message or email template) to encourage re-engagement.
- Given I return to the Dashboard, then the engagement score and Alerts panel reflect the latest drilldown data on the next refresh cycle — there is no separate recalculation path.

---

---
### Epic 8: Communication Layer (NEW)
**Goal:** Provide a structured communication layer so important messages move out of ad-hoc WhatsApp and into CadenceSprout.

Scope (Phase 2/expansion):
- Teacher announcements to all parents in a class or group.
- 1:1 parent–teacher messaging tied to a child.
- Admin broadcasts to all parents or staff across one or more centers.

**Modes**

1. **Announcements**
  - One-to-many (teacher → class).
  - No replies OR limited emoji reactions.
  - High visibility for important updates.
2. **1:1 Chat (Phase 2)**
  - Parent ↔ Teacher.
  - Threaded messages with read receipts.
3. **Admin Broadcast**
  - Admin → all parents or staff.
  - Priority messages (closures, urgent alerts).

**Guardrails**

- No spam:
  - Teachers limited to a configurable number of announcements per day.
- Clear separation of surfaces:
  - Feed = memories and stories.
  - Communication = actions, logistics, and coordination.

---

**Story 8.1: Class Announcements (Teacher → Parents)**
As a teacher, I want to send a one-way announcement to all parents in my class so that important updates are not lost in the feed or WhatsApp.

Acceptance Criteria:
- Given I am on the Teacher app, when I tap "New Announcement" from the Communication tab or FAB, then I can select my class (pre-filled in most cases) and compose a short text message (max 500 characters).
- Given I send an announcement, then all parents linked to that class receive a notification tagged as "Announcement" and see the message in a dedicated Announcements view (not mixed into the photo feed).
- Given announcements are one-way in Phase 2, then parents can react with emojis (👍 ❤️ 🙏) but cannot reply with text in the same thread.
- Given a teacher attempts to send more than the configured daily limit of announcements, then the app shows a friendly error: "You've reached today's announcement limit. Please combine non-urgent updates."

---

**Story 8.2: Announcements Inbox for Parents**
As a parent, I want a clear inbox of school/teacher announcements so that I can quickly catch up on important information.

Acceptance Criteria:
- Given I open the Parent app, then there is a Communication / Announcements tab separate from the photo feed.
- Given I have unread announcements, then the tab shows a badge with the count of unread items.
- Given I open the Announcements tab, then announcements are listed with: title (first line), sender (Teacher name or School name), timestamp, and a small "Important" icon for high-priority messages.
- Given I tap an announcement, then I can read the full text and see any attached links or documents.
- Given I mark an announcement as read by opening it, then it no longer counts toward the unread badge.

---

**Story 8.3: 1:1 Parent–Teacher Chat (Phase 2)**
As a parent, I want to message my child's teacher directly from CadenceSprout so that I don't have to juggle WhatsApp threads for school communication.

Acceptance Criteria:
- Given 1:1 chat is enabled for my school, then from a post or from my child's profile I can tap "Message Teacher" to open a chat thread with that teacher.
- Given I open a 1:1 chat, then I see message bubbles with sender labels ("You" vs. teacher name), timestamps, and read indicators (single tick = sent, double tick = read).
- Given I send a message, then the teacher receives a notification with the child's name and a snippet of the message.
- Given chat is disabled for a school or temporarily turned off, then the UI shows a clear state: "Direct messaging is currently managed via your school. Please contact the office for urgent issues."

---

**Story 8.4: Admin Broadcasts to All Parents or Staff**
As a school admin, I want to send broadcast messages to all parents or all staff so that I can communicate closures and important policies in one step.

Acceptance Criteria:
- Given I am on the Admin dashboard, when I navigate to Communication → Broadcast, then I can choose my audience: All Parents, All Staff, or specific classes.
- Given I compose a broadcast and send it, then it appears as an announcement in the Parent or Teacher apps (depending on audience) and is marked with the school name as sender.
- Given a broadcast is marked as "Urgent" by the admin, then parents receive both an in-app notification and a WhatsApp/SMS fallback (subject to notification system rules and consent).
- Given a broadcast is sent, then an entry is stored in a "Broadcast log" with timestamp, sender, audience, and delivery counts (delivered/failed).

---

### Epic 9: Search & Retrieval (NEW)
**Goal:** Make it easy to quickly find the right child, parent, teacher, or post across the system.

Scope (Phase 2/expansion):
- Parent search (e.g., find a parent by name or phone number from admin dashboard).
- Teacher search (e.g., find a teacher by name or class).
- Basic content search for posts by child name or date range.

---

**Story 9.1: Global Search on Admin Dashboard**
As a school admin, I want a single search box on the dashboard to quickly find any parent, child, teacher, or class so that I don't have to navigate multiple menus.

Acceptance Criteria:
- Given I am on the Admin dashboard, then a global search box is visible in the top navigation bar.
- Given I type at least 3 characters, then search suggestions appear grouped by entity type (Parents, Children, Teachers, Classes) with labels like "Meera (Parent)" or "Nursery A (Class)".
- Given I select a suggestion, then I am taken directly to the relevant detail view (Parent profile, Child profile, Teacher profile, or Class view).
- Given I search for something I am not allowed to see (e.g., another school's data), then no results are returned — search is always scoped by `school_id`.

---

**Story 9.2: Parent Search from Admissions and Fees**
As a school admin, I want to search for a parent by name or phone number from Admissions and Fee Management so that I can quickly locate their records.

Acceptance Criteria:
- Given I am on the Admissions or Fee Management screen, then a contextual search box is available at the top.
- Given I enter a parent's name or phone number, then matching parents are listed with child name, class, and status (e.g., Active, Inquiry).
- Given I tap a parent in the search results, then I see a combined view of their child(ren), fee invoices, and admissions history.

---

**Story 9.3: Content Search for Posts by Child and Date**
As a parent or teacher, I want to search posts by child name and date range so that I can quickly find specific memories or evidence.

Acceptance Criteria:
- Given I am on the Parent or Teacher feed, when I tap the search icon, then I can filter posts by child (chip selector) and date range (from/to).
- Given I apply a filter, then only posts matching that child and date range appear in the feed.
- Given no posts are found, then an empty state appears: "No posts found for this child and date range. Try adjusting your filters."

---

**Story 9.4: Search Performance and Safeguards (Engineering)**
As the engineering team, I want search to be fast and respect permissions so that it doesn't introduce latency or privacy issues.

Acceptance Criteria:
- Given typical school sizes (up to 50 staff and 500 parents), then search response time must be < 500ms for 95% of requests.
- Given search is implemented, then all queries are scoped by `school_id` via database or query builder (no client-side filtering to enforce tenancy).
- Given role-based permissions, then parents only see their own child(ren) and related posts in search; teachers see only their classes; admins see the entire school.

---

### Epic 10: AI Intelligence Layer (EXPANDED)
**Goal:** Use AI to summarize activity, nudge behavior, and surface insights for teachers, parents, and admins.

Scope (Phase 2/expansion):
- Daily summary generation for parents (used in Parent Home Feed summary card).
- Teacher nudges (e.g., reminders to post, suggestions on what to share).
- Parent insights (e.g., patterns in engagement, milestone highlights over time).

---

**Story 10.1: Daily Parent Summary Generation**
As a parent, I want a daily summary of my child's activity so that I can understand the day at a glance without scrolling through every post.

Acceptance Criteria:
- Given the daily summary job runs once per day (evening, local time), then it aggregates that day’s posts and key events per child into a short summary string and highlight bullets.
- Given a summary exists for today, then the Parent Home Feed shows a summary card at the top with: "Today at school" title, 1–3 bullet highlights, and a CTA to "View all posts".
- Given there were no posts for my child today, then the summary card is either hidden or shows a gentle state like "No updates today — check back tomorrow." (configurable per product decision).
- Given AI summary generation fails, then the app falls back to a simple rule-based summary (e.g., "2 posts today" with thumbnails) without blocking the feed.

---

**Story 10.2: Teacher Posting Nudges**
As a teacher, I want timely nudges to post when I haven't shared anything today so that I stay on track with the expected posting cadence.

Acceptance Criteria:
- Given it is 12 PM local time and I have not posted for my class today, then I receive a non-intrusive push notification: "Share one moment from your morning? Parents are waiting 👀" (exact copy to be finalized with Design).
- Given I tap the nudge notification, then I am taken directly into the post composer with my class pre-selected.
- Given I post after receiving a nudge, then no further "post today" nudges are sent that day.
- Given I repeatedly ignore nudges for 3 consecutive days, then the system reduces nudge frequency (e.g., to every other day) and flags this in the Admin dashboard as a potential low-engagement teacher.

---

**Story 10.3: Parent Engagement Insights**
As a parent, I want simple insights about my child's engagement and milestones so that I feel reassured about their development.

Acceptance Criteria:
- Given my child has accumulated posts with milestone tags, then the Parent app can show a "Highlights" view summarizing recent milestones (e.g., "Rohan has shown 3 new language milestones in the last 30 days").
- Given there is enough data, then the insights view shows simple trends (e.g., "Most active on Mon/Wed" or "Lots of storytime photos this month").
- Given there is insufficient data, then the insights view shows an encouraging message instead of blank charts.

---

**Story 10.4: Admin Intelligence Snapshot**
As a school admin, I want AI-curated insights about engagement, attendance, and fees so that I can spot patterns without deep analysis.

Acceptance Criteria:
- Given the weekly intelligence job runs, then it produces 3–5 bullet insights per school (e.g., "Nursery A has the highest parent engagement", "Overdue fees increased 15% vs. last month").
- Given I open the Admin dashboard on Monday, then a "This week’s insights" panel appears below the main tiles with those bullets.
- Given an insight references a metric, then the metric is linkable to a relevant detail view (e.g., clicking an engagement insight opens the engagement drilldown filtered to that class).

---

**Story 10.5: Child Skill Insight Banner for Teachers (NEW)**
As a teacher, I want simple AI-generated insights about a child's emerging skills so that I know what to observe and document next.

Acceptance Criteria:
- Given a child has accumulated enough tagged posts and milestones (e.g., ≥ 5 posts with milestone tags or consistent themes), then the Milestone Tracker view (T-6) may show an optional AI insight banner at the top (e.g., "Based on recent posts, Rohan may be developing: • Spatial reasoning • Fine motor skills").
- Given the AI insight banner is shown, then it is clearly labeled as an AI suggestion (e.g., "AI insight") and uses warm, non-clinical language that avoids any diagnosis; it frames suggestions as possibilities, not facts.
- Given I tap the AI insight banner, then the milestone list scrolls or highlights to the relevant domain(s) and suggested milestones so I can review and confirm or add observations.
- Given AI insight generation fails or there is insufficient data, then no banner is shown and the Milestone Tracker behaves as a normal manual view — the absence of a banner is not presented as an error.

---

### Epic 11: Admissions Management
**Goal:** Enable schools to track inquiries through to enrollment, replacing paper registers and WhatsApp-based admission tracking.
**Priority:** P1 (important for ERP completeness; not the first thing schools care about)
**Timeline:** Month 7-8

---

**Story 11.1: Admissions Inquiry Capture**
As a school admin, I want to record a new inquiry so that I don't lose track of prospective parents.

Acceptance Criteria:
- Given I navigate to Admissions, when I tap "New Inquiry", then I can enter: parent name, phone number, child name, child age, class of interest, inquiry source (Walk-in / Phone / Referral / Social media / Other)
- Given I save the inquiry, then it appears in the Admissions pipeline with status: New Inquiry
- Given I tap an inquiry, then I can view all fields, add notes, and update the status

---

**Story 11.2: Admissions Pipeline Stages**
As a school admin, I want to move inquiries through stages so that I know where each prospective child is in the process.

Acceptance Criteria:
- Given an inquiry exists, then it can be moved through these stages: New Inquiry → Tour Scheduled → Tour Done → Seat Offered → Enrolled → Not Joining
- Given I move a record to "Enrolled", then I am prompted to create a child profile from the inquiry data (pre-fills name, DOB, class)
- Given an inquiry has been in the same stage for > 14 days, then it shows a "Follow up?" indicator in the pipeline view
- Given I mark an inquiry as "Not Joining", then it moves to an archived state but is not deleted

---

**Story 11.3: Enrollment to Child Profile**
As a school admin, I want to convert an admitted inquiry into a full child profile so that I don't have to re-enter the data.

Acceptance Criteria:
- Given I convert an inquiry to enrollment, then a child profile is pre-created with the inquiry data (name, DOB, class)
- Given the child profile is created from enrollment, then I am immediately prompted to: (1) upload an enrollment photo for face recognition, and (2) add parent phone numbers for magic-link invitation
- Given I complete these steps, then the child appears in the teacher's class roster and the parent invitation is sent

---

### Epic 12: Parent Engagement System (NEW)
**Goal:** Build a holistic parent engagement system beyond the core feed so that parents stay informed and emotionally connected.

Scope (Phase 2/expansion):
- Daily digest of posts and key events (e.g., via app notification or summary view).
- Ability for parents to save or download favorite posts and memories.
- Smooth multi-child support for parents with more than one enrolled child.

---

**Story 12.1: Daily Digest View in Parent App**
As a parent, I want a daily digest view so that I can see the most important updates about my child in one place.

Acceptance Criteria:
- Given the daily digest is generated, then the Parent app offers a "Today" tab or section summarizing today’s posts, milestones, and announcements for my child(ren).
- Given I open the digest, then I see: number of posts, key milestones (if any), and any unread announcements for the day.
- Given I have more than one child, then the digest clearly separates content per child (e.g., tabs or labeled sections).

---

**Story 12.2: Save / Favorite Posts**
As a parent, I want to save favorite posts so that I can easily find and revisit my favourite memories.

Acceptance Criteria:
- Given I am viewing a post, then I can tap a "Save" or "Bookmark" icon to add it to my favorites.
- Given I have saved posts, then a "Saved" section is available in the Parent app where all favorited posts appear chronologically.
- Given I un-save a post, then it is removed from the Saved list but remains in the main feed.

---

**Story 12.3: Year-End Portfolio Download and Sharing**
As a parent, I want to download or share my child's year-end portfolio so that I can keep and share a record of their preschool journey.

Acceptance Criteria:
- Given the AI portfolio generation job has completed, then the Parent app shows a "Download portfolio" CTA on the child's profile.
- Given I tap "Download portfolio", then I receive a PDF file with curated posts, milestones, and summary text.
- Given I choose to share the portfolio, then I can use my device share sheet to send a link or file, which includes subtle "Powered by CadenceSprout" branding.

---

**Story 12.4: Multi-Child Support**
As a parent with more than one enrolled child, I want to switch between children easily so that I can keep track of each child's updates.

Acceptance Criteria:
- Given I have multiple children enrolled, then the Parent app clearly shows which child I am currently viewing (name + avatar) and lets me switch via a simple selector.
- Given I switch children, then the feed, digest, and saved posts all update to show content for the selected child.
- Given I only have one child enrolled, then no confusing child-switcher UI is shown.

---

### Epic 13: Admin Alerts & Intelligence (NEW)
**Goal:** Give admins proactive intelligence and alerts so they can manage by exception instead of micromanaging.

Scope (Phase 2/expansion):
- Engagement alerts (e.g., classes or parents with low engagement over time).
- Fee alerts (e.g., rising overdue balance, classes with high unpaid ratios).
- Attendance alerts (e.g., low attendance trends, frequent absentees).

---

**Story 13.1: Configurable Alert Rules**
As a school admin, I want to configure basic alert rules for engagement, fees, and attendance so that the system notifies me about what matters most.

Acceptance Criteria:
- Given I open the Admin dashboard settings, then there is an "Alerts" configuration section with default thresholds for engagement, overdue fees, and attendance.
- Given I adjust a threshold (e.g., engagement < 40%), then future alerts use the new value while past alerts remain unchanged.
- Given no configuration changes are made, then sensible defaults (defined in product) are applied.

---

**Story 13.2: Engagement Alert Feed**
As a school admin, I want a feed of engagement-related alerts so that I can see patterns and take action.

Acceptance Criteria:
- Given a class or segment fails the engagement threshold for 2 consecutive weeks, then an engagement alert is generated and added to the Alerts feed with class name, score, and trend.
- Given I open an engagement alert, then I can jump directly to the engagement drilldown view for that class.
- Given I mark an alert as resolved, then it is archived but still visible in history for future reference.

---

**Story 13.3: Fee and Attendance Intelligence Alerts**
As a school admin, I want alerts for worrying fee and attendance patterns so that I can intervene early.

Acceptance Criteria:
- Given overdue fees exceed a configurable percentage of total billed amount (e.g., > 20%), then a "Fee risk" alert is created with the amount, number of affected families, and suggested next steps.
- Given a class has unusually low attendance for 3 consecutive days, then an "Attendance risk" alert is created with class name and attendance trend.
- Given I click a fee alert, then I am taken to the Fee Management view filtered to overdue invoices; given I click an attendance alert, then I am taken to the attendance view filtered to the affected class and dates.

---

**Story 13.4: Alert Delivery Channels**
As a school admin, I want critical alerts delivered via multiple channels so that I don’t miss urgent issues.

Acceptance Criteria:
- Given an alert is marked as "Critical" by the rules engine (e.g., engagement collapse, large overdue spike), then I receive both an in-app dashboard alert and an email/WhatsApp notification (subject to notification system rules and DPDP consent).
- Given an alert is informational only, then it appears in the Alerts panel but does not trigger external notifications.
- Given I disable external notifications for alerts in settings, then only in-app alerts are shown.

---

### Epic 14: Fees & Payments (NEW)
**Goal:** Enable complete fee lifecycle from plan setup to collection and alerts.

Scope (Phase 1/expansion blend):
- Fee plan setup per class/term.
- Invoice generation (single and bulk).
- Online payments (UPI) integration.
- Payment tracking and overdue alerts.

---

**Story 14.1: Fee Plan Setup**
As a school admin, I want to define fee plans so that invoices can be generated consistently for each class and term.

Acceptance Criteria:
- Given I navigate to the Fees & Payments configuration area, then I can create fee plans with: name (e.g., "Nursery 2026–27 Tuition"), amount, billing frequency (monthly/termly), due dates, and applicable classes.
- Given a fee plan is created, then it can be attached to one or more classes so that invoices can be generated in bulk for enrolled children.
- Given I update a fee plan, then future invoices use the new configuration while previously generated invoices remain unchanged for auditability.

---

**Story 14.2: Invoice Generation & Bulk Invoicing**
As a school admin, I want to generate invoices (individually or in bulk) so that parents know what to pay and when.

Acceptance Criteria:
- Given a fee plan exists, then I can generate invoices in bulk for all children in the associated class(es) for a given billing period with a single action.
- Given I need to create or adjust an invoice for a specific child, then I can create/edit a single invoice with custom amount, due date, and notes without affecting the underlying fee plan.
- Given invoices are generated, then each invoice has a unique identifier, child/parent linkage, status (Pending / Paid / Overdue), due date, and optional notes visible to parents.

---

**Story 14.3: Online Payments (UPI) Integration**
As a parent, I want to pay school fees online via UPI so that I can complete payments quickly from my phone.

Acceptance Criteria:
- Given my school has enabled online payments and configured their UPI/payment provider, then each pending invoice in the Parent app shows a "Pay now" CTA that launches a UPI-compatible flow with the correct amount, invoice reference, and payee details.
- Given a payment is successful, then the payment provider notifies CadenceSprout via webhook/callback and the invoice status is updated to Paid, with payment method and transaction reference stored.
- Given a payment fails or is cancelled, then the invoice remains Pending and I see a clear, non-technical message in the app encouraging me to retry or contact the school if needed.

---

**Story 14.4: Payment Tracking & Alerts**
As a school admin, I want clear visibility into paid, pending, and overdue invoices so that I can follow up efficiently.

Acceptance Criteria:
- Given I open the Fees & Payments dashboard, then I can filter invoices by status (Pending / Paid / Overdue), class, and date range, and see aggregated totals per segment.
- Given an invoice passes its due date without payment, then it automatically moves to Overdue and contributes to overdue totals and fee alerts in the Admin dashboard and Admin Alerts epics.
- Given overdue invoices exceed a configured threshold (e.g., > 20% of total billed in a period), then a fee alert is generated (per Epics 7 and 13) with a CTA to view the list of overdue families.

---

### Epic 15: Admissions CRM (NEW)
**Goal:** Convert inquiries into enrollments with a simple, visual pipeline.

Scope:
- Lead capture.
- Pipeline tracking (Kanban-style stages).
- Follow-ups and tasks.
- Conversion from lead to enrolled student.

---

**Story 15.1: Lead Capture**
As a school admin, I want to quickly capture new inquiries so that I don't lose potential enrollments.

Acceptance Criteria:
- Given I navigate to the Admissions CRM, then I can add a new lead with: parent name, phone, child name, age, class of interest, source, and notes.
- Given a lead is created, then it appears in the first stage of the admissions pipeline (e.g., New Inquiry) with a clear card showing key details and contact actions.

---

**Story 15.2: Pipeline Tracking (Kanban)**
As a school admin, I want to move leads through pipeline stages so that I can see where each prospect stands.

Acceptance Criteria:
- Given I am viewing the admissions pipeline, then leads are displayed in Kanban columns by stage (e.g., New Inquiry → Tour Scheduled → Tour Done → Seat Offered → Enrolled → Not Joining).
- Given I drag-and-drop or otherwise move a lead card between columns, then the lead's stage is updated and the change is logged with timestamp and user.
- Given a lead remains in the same stage beyond a configurable number of days, then it is visually flagged (e.g., "Follow up?") to prompt action.

---

**Story 15.3: Follow-Ups & Tasks**
As a school admin, I want to schedule and track follow-ups so that leads don't go cold.

Acceptance Criteria:
- Given I open a lead detail, then I can add follow-up tasks with due dates and notes (e.g., "Call parent on Friday"), and mark them as done.
- Given a follow-up is due or overdue, then it appears in a simple task list view and may surface as an admin-level reminder or alert.

---

**Story 15.4: Conversion to Student**
As a school admin, I want to convert a won lead into a child profile so that I don't have to re-enter data.

Acceptance Criteria:
- Given I move a lead to "Enrolled", then I am prompted to create a child profile using the existing lead details (child name, DOB, class), reusing the existing Admissions → Child Enrollment flows.
- Given a child profile is created from a lead, then the lead is marked as Converted and linked to the child record for future reference.

---

### Epic 16: Child Records & Compliance (NEW)
**Goal:** Maintain a complete, compliant record for each child.

Scope:
- Core child profile and documents.
- Medical information.
- Emergency contacts.
- Incident reports.

---

**Story 16.1: Child Profile & Documents**
As a school admin, I want to store key documents against each child's profile so that records are easily accessible and auditable.

Acceptance Criteria:
- Given I open a child's admin profile, then I can upload and manage documents (e.g., birth certificate, ID proof, medical certificates) with type labels and upload dates.
- Given a document is uploaded, then it is stored securely (e.g., S3) and visible in both admin views and the parent-facing "Documents" section where appropriate.

---

**Story 16.2: Medical Info & Emergency Contacts**
As a school admin, I want to record medical information and emergency contacts so that staff know how to respond in case of issues.

Acceptance Criteria:
- Given I edit a child's record, then I can capture key medical info (e.g., allergies, chronic conditions, medications) and at least two emergency contacts (name, relationship, phone).
- Given medical information exists, then teachers see a concise, privacy-respecting summary in relevant contexts (e.g., a banner in Child Detail view) without exposing full details in the parent app.

---

**Story 16.3: Incident Reports**
As a school admin, I want a structured incident log so that any important events (e.g., injuries, behavioural incidents) are recorded and auditable.

Acceptance Criteria:
- Given an incident is logged from the teacher app (inline with a post) or from the admin dashboard, then a structured incident record is created with: child(ren) involved, date/time, type, description, severity, and whether parents were notified.
- Given I open the Incident log for a child or class, then I can filter by date range and incident type and see links back to the originating posts or notes.
- Given an incident is marked as requiring parent notification, then its status reflects whether notifications were sent and acknowledged, and this status can feed into parent-facing incident views.

---

### Epic 17: Staff Management (NEW)
**Goal:** Manage the staff lifecycle and ensure classes are properly staffed.

Scope:
- Staff profiles.
- Assignments to classes/centers.
- Attendance & leave (lite).
- Role-based permissions.

---

**Story 17.1: Staff Profiles & Roles**
As a school admin, I want to manage staff profiles so that I know who is working where and in what capacity.

Acceptance Criteria:
- Given I open Staff Management, then I can create and edit staff profiles with name, role (e.g., Teacher, Admin, Support), phone, email (optional), and center/class assignments.
- Given a staff profile exists, then it appears in lists used elsewhere in the product (e.g., assigning a class teacher, messaging staff) with up-to-date role and assignment.

---

**Story 17.2: Staff Attendance & Leave (Lite)**
As a school admin, I want a light-weight view of staff attendance and leave so that I can see staffing gaps.

Acceptance Criteria:
- Given staff attendance tracking is enabled, then I can record or import simple attendance/leave statuses (Present / Absent / On leave) for each staff member per day.
- Given I open the staff attendance view, then I can see at-a-glance which staff are present, absent, or on leave today, and drill down into history for a given staff member.

---

**Story 17.3: Role-Based Permissions**
As a system admin, I want to assign roles and permissions so that staff only see what they need.

Acceptance Criteria:
- Given I manage staff roles, then I can assign high-level permission profiles (e.g., Teacher, Admin, Owner) that map to capabilities across the app (e.g., can view fees, can edit child records, can view incidents).
- Given a staff member's role is changed, then their access rights update accordingly on next login without affecting historical audit trails.

---

### Epic 18: Structured Learning (NEW)
**Goal:** Add a light-weight structured learning layer on top of daily posts.

Scope:
- Lesson planning.
- Daily reports.
- Assignments (lite, age-appropriate).

---

**Story 18.1: Lesson Planning (Lite)**
As a teacher, I want to plan simple lesson outlines so that I have a structured view of what to cover each day/week.

Acceptance Criteria:
- Given I open the Lesson Planning view, then I can add short plans per day or week with fields like theme, activities, and materials, linked to a class.
- Given a plan exists for today, then it can subtly inform AI suggestions (e.g., caption hints or milestone suggestions) and be visible to admins in a read-only planning overview.

---

**Story 18.2: Daily Reports (Extended)**
As a teacher/admin, I want to aggregate optional daily report fields into a structured view so that parents and admins can see a concise daily summary.

Acceptance Criteria:
- Given teachers optionally fill daily report fields in the post composer (Epic 3), then the system can generate a structured daily report per class and child (e.g., meals, naps, key activities) without additional manual work.
- Given I open a Daily Reports view (admin or parent-facing, depending on role), then I can see the daily report for the most recent school days, with clear indication when a day has no report data.

---

**Story 18.3: Assignments (Lite)**
As a teacher, I want to send occasional simple assignments or at-home activities so that parents can extend learning at home without complexity.

Acceptance Criteria:
- Given I create an assignment, then I can specify: title, short description, due date, and which class/children it applies to, and parents see it in a dedicated, non-noisy section (not mixed into the photo feed).
- Given an assignment is created, then parents receive a notification and can mark it as done; completion can be surfaced lightly in admin/teacher views without strict grading.

## 4. Screen Inventory

This section maps every screen in the product to its role, purpose, route, and key elements.

At the **admin level**, note the following relationships between screens:
- `A-1 Dashboard Home` surfaces high-signal alerts and tiles and then deep-links into the relevant OS module homes and tables.
- `A-9 Fees & Payments Overview` is the **fees module home**; `A-4 Fee Management (List)` is the detailed invoice table behind it.
- `A-10 Admissions Overview` is the **admissions module home**; `A-3 Admissions Pipeline` is the detailed Kanban board behind it.
- `A-12 Staff Management Overview` is the **staff module home**; `A-6 Staff Management` is the detailed staff table behind it.
- `A-11 Child Records` is the central compliance hub surfacing per-child documents, medical info, emergency contacts, and incidents.

---

### 4.0 Screen ID → Epics Map (NEW)

Quick reference linking key screens to the epics and stories that define their behavior.

| Persona / Surface      | Screen ID & Name                    | Primary Epic(s) / Stories                                 |
|------------------------|--------------------------------------|-----------------------------------------------------------|
| Teacher (mobile)       | **T-1 Home Feed**                   | Epic 3 – Stories 3.0, 3.6                                 |
| Teacher (mobile)       | **T-2 / T-2A Post Composer**        | Epic 3 – Stories 3.1–3.5, 3.7; Epic 10 – AI caption/tagging |
| Teacher (mobile)       | **T-5A Child Detail / Timeline**    | Epic 3 – Child overview & timeline                        |
| Teacher (mobile)       | **T-6 Milestone Tracker**           | Epic 3 – Story 3.4; Epic 10 – Story 10.5 (AI insight banner) |
| Teacher (mobile)       | **T-8 Daily Report Form**           | Epic 3 – Story 3.6; Epic 18 – Story 18.2 (Daily Reports)  |
| Teacher (mobile)       | **T-9 Incident Report Form**        | Epic 3 – Story 3.8; Epic 16 – Story 16.3 (Incident Reports) |
| Parent (mobile)        | **P-3 Parent Home Feed**            | Epic 4 – Stories 4.1–4.2; Epic 10 – Story 10.1 (daily summary) |
| Parent (mobile)        | **P-5 Milestone Progress**          | Epic 4 – Story 4.3; Epic 10 – Story 10.3 (parent insights) |
| Parent (mobile)        | **P-6 Year-End Portfolio**          | Epic 4 – Story 4.4; Epic 12 – Stories 12.2–12.3           |
| Parent (mobile)        | **P-9 Fees & Payments**             | Epic 6 – Story 6.4; Epic 14 – Stories 14.3–14.4           |
| Parent (mobile)        | **P-10 Documents & Records**        | Epic 16 – Story 16.1                                      |
| Parent (mobile)        | **P-11 Incident History**           | Epic 4 – Story 4.6; Epic 16 – Story 16.3                  |
| Admin Web              | **A-1 Dashboard Home**              | Epic 7 – Stories 7.1–7.6; Epic 13 – Stories 13.1–13.4     |
| Admin Web              | **A-4 Fee Management (List)**       | Epic 6 – Stories 6.1–6.3; Epic 14 – Story 14.4 (drilldown from A-9) |
| Admin Web              | **A-9 Fees & Payments Overview**    | Epic 14 – Stories 14.1–14.4; Epic 7 – Story 7.7 (module home → A-4) |
| Admin Web              | **A-10 Admissions Pipeline Overview** | Epic 11 – Stories 11.1–11.3; Epic 15 – Stories 15.1–15.4; Epic 7 – Story 7.8 (module home → A-3) |
| Admin Web              | **A-11 Child Records**              | Epic 16 – Stories 16.1–16.3                               |
| Admin Web              | **A-12 Staff Management Overview**  | Epic 17 – Stories 17.1–17.3; Epic 7 – Story 7.9 (module home → A-6) |
| Teacher Web            | **TW-2 Teacher Web Home Feed**      | Epic 3 – Teacher web feed equivalent; Epic 7 – engagement feedback context |
| Parent Web             | **PW-2 Parent Web Full Feed**       | Epic 4 – Stories 4.1–4.2; Epic 10 – Story 10.1            |

This table is not exhaustive; it highlights the most important Screen ↔ Epic connections so reviewers can quickly jump between UX and requirements.

---

### 4.1 Teacher App (React Native — iOS + Android)

---

**Screen T-0: Teacher Login**
- Route: `/login` (native screen, pre-auth)
- Entry point: App cold launch (unauthenticated), logout redirect
- Purpose: Authenticate teacher via phone number + password (Sanctum token auth); shared entry point that detects role and redirects accordingly

Key elements:
- School logo / CadenceSprout wordmark centered
- Phone number input field (numeric keypad, +91 prefix)
- Password input field (masked, show/hide toggle)
- [Log In] primary button (sage green, full width)
- "Forgot password?" link → phone number + OTP reset flow
- Post-login redirect logic: role = teacher → T-1 Home Feed; role = parent → P-3 Parent Feed; role = admin → A-1 Dashboard

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| Default | Screen loads | Empty phone + password fields, Log In button |
| Typing | Input active | Keyboard visible, field highlighted |
| Loading | Log In tapped | Button shows spinner, inputs disabled |
| Error | Invalid credentials | Inline error below password: "Incorrect phone number or password." — inputs remain filled |
| Success | Valid credentials | Brief success flash, redirect to T-1 |

---

**Screen T-1: Home Feed (REWRITTEN)**
- Route: `/` (default tab)
- Entry point: App launch, bottom nav tab 1
- Purpose: Drive daily posting behavior by showing status, posts, and engagement at a glance.

Key elements:
- Daily status header for today's date (e.g., "No update yet — share a moment" or "Today's update is live")
- Post feed: full-bleed photo (4:3), caption in Fraunces font, child tag chips, time ago, parent view count, and % reach
- Engagement indicators: "Viewed by X parents" and "% reach" on each post
- FAB (floating action button, sage green, bottom right) — always visible; can pulse when no post exists yet for today
- Bottom tab nav: Feed | Attendance | Roster | Profile

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| Loading | App opens | Skeleton daily status header + skeleton cards (warm cream pulsing rectangles) |
| Empty (new class, 0 students) | No children added yet | Daily status header plus "Add your students to get started." + Add Students button |
| No post today yet | Class exists, no post today | Daily status header with CTA to post; past posts visible under previous days |
| Normal | At least one post today | Daily status header with positive reinforcement; today's posts shown first, then earlier days |
| Offline | No network | Persistent top banner "You're offline — showing saved content"; last known daily status and posts cached |

---

**Screen T-2: Post Composer**
- Route: Modal, triggered by FAB
- Entry point: FAB tap on T-1
- Purpose: Enable a teacher to compose and publish a post in ≤3 taps

Key elements:
- Full-bleed photo preview (4:3, crop center-fill)
- Caption field (Fraunces font, AI-drafted content or editable placeholder)
- Caption shimmer / ✨ AI indicator
- Child tag chips (AI-suggested: dashed until confirmed; confirmed: solid sage green)
- "Add children manually" link
- "Add milestones (optional)" row
- Class selector (defaults to teacher's class)
- [POST] button (primary, sage green, full width)
- [Back] to discard

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| Loading AI caption | Photo selected | Inline shimmer in caption area: "Drafting caption..." |
| AI caption ready | < 3 seconds | Caption in Fraunces italic + ✨ icon |
| AI caption failed | OpenRouter timeout | Empty caption field, placeholder: "What happened in this moment?" |
| Face recognition pending | Photo uploaded | Child chips show as grey/dashed: "Identifying..." |
| Face recognition complete | Rekognition returns | Confirmed chips solid, unconfirmed chips dashed |
| Face recognition failed | Rekognition error | "Couldn't auto-tag — add children manually." Grey chips become tappable |
| Upload in progress | POST tapped | Progress bar in FAB area; optimistic post visible (blurred if < 80%) |
| Upload failed | Network drop | Toast: "Upload failed. Tap to retry." |

---

**Screen T-2A: Manual Child Tag Picker**
- Route: Bottom sheet / modal overlay from T-2 Post Composer
- Entry point: Tap "Add children manually" from T-2 or tap an unconfirmed chip
- Purpose: Allow teachers to manually search, select, confirm, or remove child tags when AI suggestion is absent or incorrect

Key elements:
- Modal header: "Tag children in this post"
- Search input: placeholder "Search by child name"
- Class roster list:
  - Child photo or initial avatar
  - Child name
  - Selection checkbox or chip state
- Selected children summary row pinned above footer
- [Done] primary button
- [Clear all] secondary text action

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| Loading | Modal opens, class roster fetching | Skeleton child rows |
| Default | Roster loaded | Search + selectable list of all children in class |
| Search active | Query entered | Filtered roster list |
| No results | Search query has no matches | "No children found for [query]." |
| Selection made | One or more children selected | Selected summary row + Done button enabled |

Interactions & Behaviors:
- Selecting a child immediately adds them to the selected summary row
- Deselecting a child removes the chip from T-2 after Done is tapped
- [Done] closes the modal and returns selected tags to T-2
- [Clear all] removes all selected children after confirmation if 2 or more are selected

Data Requirements:
- Class roster: `child_id`, `name`, `photo_url`, `class_id`
- Current selected tags from T-2

---

**Screen T-3: Post Detail**
- Route: `/post/:id`
- Entry point: Tap post card on T-1
- Purpose: Show full post details including parent engagement

Key elements:
- Full-screen photo with swipe for multiple photos
- Caption (Fraunces font)
- Child tags with confirmation status
- Milestone tags (if any)
- Parent view count ("Seen by 12 of 18 parents")
- Comment thread
- Posted timestamp

---

**Screen T-4: Attendance**
- Route: `/attendance` (bottom nav tab 2)
- Entry point: Bottom nav
- Purpose: Daily class attendance marking

Key elements:
- Date header (today's date, with back-navigation for corrections)
- Class roster list: child photo thumbnail, name, Present / Absent toggle
- Optional absence reason picker (per child)
- [Submit Attendance] button (primary)
- Submission confirmation state

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| Not yet taken | App opens, attendance not submitted | "Take today's attendance." CTA header, all children unset |
| In progress | Teacher is marking | Toggles active, Submit button enabled when all marked |
| Submitted | Submit tapped | Confirmation: "Attendance submitted." Read-only view, editable until midnight |

---

**Screen T-5: Class Roster**
- Route: `/roster` (bottom nav tab 3)
- Entry point: Bottom nav
- Purpose: View all children in the teacher's class; see parent contact info

Key elements:
- Child list: photo thumbnail, name, age, parent name(s), parent status (Invited / Active / Not invited)
- Search bar
- Tap child → child detail (name, DOB, parent(s), milestone summary, recent posts)

---

**Screen T-5A: Child Detail / Timeline View (UPDATED)**
- Route: `/child/:id`
- Entry point: Tap child row on T-5 Class Roster
- Purpose: Give the teacher a single-child overview including profile, parent contact information, milestone summary, and a unified timeline of this child's posts and milestone events.

Key elements:
- Child header:
  - Child photo
  - Child name
  - Date of birth / age
  - Class name
- Parent section:
  - Parent/guardian names
  - Relationship labels
  - Phone numbers
  - Parent status badges (Active / Invited / Not invited)
- Quick actions:
  - Call parent
  - Message parent on WhatsApp
  - View milestones
- Milestone summary card:
  - Domain-wise progress snapshot
  - "View full milestone tracker" CTA → T-6
- Child timeline section:
  - Chronological timeline of this child's story across the year, combining posts and milestone events into a single list (most recent at top).
  - Each timeline item shows: date, type badge (Post / Milestone / Post + Milestone), brief description (e.g., first line of caption or milestone name), and an indicator if a new domain has recently become active.
  - Timeline items with media link to T-3 Post Detail; timeline items that are milestone-only link to the relevant section in T-6.

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| Loading | Child detail opens | Skeleton header, parent rows, and post cards |
| No timeline events | Child has no tagged posts and no logged milestones yet | "No moments recorded for this child yet. As you post and log milestones, they'll appear here." |
| No parent linked | Child exists but parent record not added | "No parent contact added yet." + prompt to contact admin |
| Normal | Child data available | Full profile + parent section + milestone summary + unified timeline of posts and milestones |

Interactions & Behaviors:
- Tapping View milestones deep-links into T-6 for the same child
- WhatsApp action opens the default WhatsApp deep link with the parent's phone number pre-filled
- Timeline items are sorted reverse-chronologically (most recent at top)
- Tapping a timeline item that includes a post opens T-3 Post Detail at that post.
- Tapping a timeline item that is milestone-only opens T-6 Milestone Tracker focused on that milestone/domain.

Data Requirements:
- Child profile: `child_id`, `name`, `dob`, `age`, `photo_url`, `class_name`
- Parent links: `parent_id`, `name`, `relationship`, `phone`, `invite_status`
- Milestone summary by domain
- Joined view of child's tagged posts and milestone events for timeline construction

---

**Screen T-6: Milestone Tracker (per child)**
- Route: `/child/:id/milestones`
- Entry point: Tap child in Roster → Milestones tab
- Purpose: View and add milestone observations for a specific child, and (when available) see simple AI-generated insights about emerging skills.

Key elements:
- Domain tabs: Physical | Cognitive | Language | Social-Emotional | Aesthetic
- Milestone list: milestone name, age range, achieved / not yet, date achieved
- "Observed in post" link (taps through to the post where milestone was tagged)
- Add milestone button (opens NEP 2020 taxonomy picker)
 - Optional AI insight banner at the top (when sufficient data exists), labeled clearly as AI-generated (e.g., "AI insight") and summarising potential emerging skills/domains based on recent posts (e.g., "Based on recent posts, Rohan may be developing: • Spatial reasoning • Fine motor skills").

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| No milestones logged | New child, no posts with tags | "Milestones will appear here as you observe them in class." |
| Milestones present | Posts with milestone tags exist | Domain-grouped list with achieved milestones highlighted; if enough data exists, a subtle AI insight banner appears above the list with suggested domains/skills and can be tapped to scroll/highlight relevant milestones. |

---

**Screen T-6A: Milestone Picker**
- Route: Modal overlay from T-6 or T-2 Post Composer
- Entry point: Tap Add milestone button from T-6 or "Add milestones (optional)" from T-2
- Purpose: Let teachers browse and attach milestones from the NEP 2020 taxonomy without memorising the framework

Key elements:
- Modal header: "Select milestone"
- Domain tabs: Physical | Cognitive | Language | Social-Emotional | Aesthetic
- Search field: "Search milestones"
- Milestone list rows:
  - Milestone title
  - Domain
  - Age range
  - Selection control
- Selected milestones tray pinned above footer
- [Add selected milestones] primary button

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| Loading | Modal opens, taxonomy fetching | Skeleton milestone rows |
| Default | Taxonomy loaded | Domain tabs + milestone rows |
| Search active | Query entered | Filtered milestone list |
| No results | Search query has no matches | "No milestones found for [query]." |
| Selection made | One or more milestones selected | Selected tray visible + Add button enabled |

Interactions & Behaviors:
- Domain tabs filter the list instantly without closing the modal
- Teachers can multi-select milestones before confirming
- Added milestones return to the source screen as chips or list items

Data Requirements:
- Taxonomy source: `milestone_id`, `domain`, `title`, `description`, `age_range_months`
- Current selected milestone IDs

---

**Screen T-7: Profile / Settings**
- Route: `/profile` (bottom nav tab 4)
- Entry point: Bottom nav
- Purpose: Teacher account settings, notification behavior, app preferences, support access, and logout

Key elements:
- Top app bar:
  - Center title: "Profile & Settings"
  - Right-side edit icon for profile editing
- Profile card:
  - Teacher photo or initial avatar
  - Teacher full name
  - Role + class assignment (e.g. "Class Teacher · LKG A")
  - School name
- Notifications section:
  - New parent comment toggle
  - Daily reminder to post toggle
  - Attendance reminder toggle
- App Preferences section:
  - Language row (Phase 1: English only; future language selector hidden until enabled)
  - Media upload quality row (Auto / Data Saver / High)
  - Clear cached media row
- Permissions section:
  - Camera roll permission status
  - Push notification permission status
  - "Open system settings" action when required permissions are denied
- Help & About section:
  - Contact school admin
  - Privacy policy link
  - App version + build number
- Account section:
  - [Log Out] button (full-width, destructive styling)

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| Loading | Screen opens, profile/preferences fetching | Skeleton profile card + skeleton settings rows |
| Default | Data loaded successfully | Profile card + grouped settings rows + Log Out button |
| Permission denied | Camera roll or notifications denied at OS level | Inline warning row with amber icon + "Open Settings" action |
| Save success | Toggle or preference updated | Toast: "Settings updated." |
| Save failed | API/network failure on settings update | Inline error on affected row + Retry action |
| Logged out | Logout confirmed | Redirect to T-0 Teacher Login |

Interactions & Behaviors:
- Edit icon opens profile edit sub-screen or bottom sheet
  - Editable: display name, profile photo
  - Read-only: school name, assigned class
- Notification toggles save optimistically, then reconcile with server response
- Tapping camera roll or notification permission row opens native system settings if permission is denied
- Tapping Language opens a selector sheet; in Phase 1 only English is selectable
- Tapping Clear cached media opens a confirmation sheet before clearing local media cache
- Tapping Log Out opens confirmation sheet: "Log out of CadenceSprout on this device?"

Data Requirements:
- Teacher profile: `name`, `avatar_url`, `role`, `class_name`, `school_name`
- Preferences:
  - `notify_parent_comments`
  - `notify_daily_post_reminder`
  - `notify_attendance_reminder`
  - `language`
  - `media_upload_quality`
- Client permission state:
  - photo library permission
  - push notification permission
- App metadata:
  - app version
  - build number

---

**Screen T-8: Daily Report Form**
- Route: Modal or nested section from T-2 Post Composer; optionally accessible from T-1 header ("Daily report")
- Entry point: Expand "Daily report (optional)" section from T-2, or tap a "Daily report" CTA on T-1
- Purpose: Capture structured, optional daily report fields (meals, naps, key activities) without disrupting the core post flow

Key elements:
- Header: "Daily report for [Class name], [Date]"
- Fields:
  - Meal summary (dropdown + free-text notes)
  - Nap summary (time range, quality, optional notes)
  - Key activities (multi-select chips + optional free-text)
- Optional per-child notes link (e.g., for specific children who need extra context)
- [Save report] primary button; [Cancel] secondary action or close icon

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| Empty | First time opening today | Blank fields with short helper text explaining optional nature |
| Partially filled | Draft exists for today | Previously entered values restored, with a subtle "Draft saved" indicator |
| Saved | Save tapped | Confirmation toast (e.g., "Daily report saved"), then modal closes or stays with disabled Save until further edits |

Interactions & Behaviors:
- Saving the form writes a structured daily report object linked to the class (and optionally children) and the day; it can be reused in admin and parent daily report views.
- The form never blocks posting: teachers can ignore it entirely and still post photos normally.
- If opened from a specific post composer, saving the daily report associates it with that post's date but not necessarily only that post.

Data Requirements:
- Class identifier and date
- Structured fields for meals, naps, and activities
- Optional links to child IDs for per-child notes

---

**Screen T-9: Incident Report Form**
- Route: Modal overlay from T-2 Post Composer, T-5A Child Detail, or admin-initiated incident logging
- Entry point: Tap "Add incident" or expand the "Incident (optional)" section while creating a post or viewing a child
- Purpose: Allow teachers to log structured incidents in context, feeding the Child Records & Compliance system without cluttering the main feed

Key elements:
- Header: "Incident report for [Child name]" (or [Class name] when multiple children involved)
- Fields:
  - Incident type (dropdown: Minor injury / Behaviour / Health / Other)
  - Date & time (auto-filled, editable)
  - Description (multi-line text)
  - Severity (Low / Medium / High)
  - Notify parents toggle (Yes/No)
- Linked post preview (if opened from a specific post)
- [Save incident] primary button; [Cancel] secondary action

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| New incident | Opened from child or post with no existing incident | Empty form with child/post context pre-filled |
| Editing | Incident opened from admin or teacher view for update (where allowed) | Fields populated with existing values |
| Saved | Save tapped | Confirmation toast (e.g., "Incident saved"), and form closes back to source screen |

Interactions & Behaviors:
- Saving creates or updates a structured `incident` record linked to one or more children, a class, and optionally a post.
- If "Notify parents" is enabled, a follow-up workflow is triggered to send parent notifications and mark the incident as pending/complete notification.
- Teachers can back out without saving, and no incident record is created.

Data Requirements:
- Child IDs and class ID
- Incident metadata: type, date/time, description, severity, notify_parents flag
- Optional linked post ID

---

### 4.2 Parent App (React Native — iOS + Android)

---

**Screen P-0: Parent App Phone Number Entry / OTP Request**
- Route: `/auth/login` (native screen, pre-auth)
- Entry point: App cold launch before authentication; tap "Get the app" from magic-link web flow
- Purpose: Start parent authentication using phone number and OTP

Key elements:
- School logo / CadenceSprout wordmark centered
- Intro copy: "See every update from your child's day"
- Phone number input with +91 prefix
- [Send OTP] primary button
- Secondary link: "Open via WhatsApp link instead" (for users who arrived without a valid link)
- Legal footnote: "By continuing, you agree to receive a one-time verification code."

States:
| State | Trigger | What the parent sees |
|---|---|---|
| Default | Screen loads | Empty phone number field, Send OTP button disabled |
| Typing | Number entered | Send OTP enabled when number is valid |
| Loading | Send OTP tapped | Button spinner, field disabled |
| Invalid number | Validation fails | Inline error: "Enter a valid phone number." |
| OTP sent | API success | Brief success message then redirect to P-0A |
| Send failed | SMS provider or API failure | Error banner + Retry action |

Interactions & Behaviors:
- Numeric keypad opens on input focus
- Valid Indian phone number format required before enabling Send OTP
- Successful submit navigates to P-0A and carries masked phone number context

Data Requirements:
- Phone number input
- OTP request API result

---

**Screen P-0A: Parent App OTP Verification**
- Route: `/auth/verify`
- Entry point: Successful OTP request from P-0
- Purpose: Verify parent identity and complete login before consent and feed access

Key elements:
- Header showing masked phone number
- 6-digit OTP input
- Countdown timer for resend eligibility
- [Verify OTP] primary button
- [Resend code] secondary action
- [Change phone number] link → back to P-0

States:
| State | Trigger | What the parent sees |
|---|---|---|
| Default | Screen opens | Empty 6-digit OTP input, Verify button disabled |
| Typing | Digits entered | Verify button enabled once all 6 digits are filled |
| Loading | Verify tapped | Button spinner, inputs disabled |
| Invalid OTP | Server returns 401 | Inline error: "That code is incorrect or expired." |
| Resend available | Timer reaches 0 | Resend code link becomes active |
| Success | OTP valid | Redirect to P-2 if consent required, else P-3 |

Interactions & Behaviors:
- Auto-advance between OTP fields as each digit is typed
- Paste of full 6-digit code populates all fields
- Successful verification stores the Sanctum token securely on device

Data Requirements:
- Masked phone number
- OTP verification API result
- `dpdp_consent_required` flag from auth response

---

**Screen P-1: Magic-Link Web View (Feed First)**
- Route: `https://cs.app/f?t={token}` (web, no install required)
- Entry point: WhatsApp message link
- Purpose: Show parent their child's latest post immediately, no friction

Key elements:
- School logo + "Powered by CadenceSprout" header
- Most recent post: full-bleed photo, caption, child name tag
- ❤️ reaction button (no login required for first reaction)
- Soft install banner (dismissible, appears after 3 views): "Get the app for all of [child name]'s updates"

States:
| State | Trigger | What the parent sees |
|---|---|---|
| Valid token, first visit | Link tapped | Full post, no login prompt |
| Valid token, 3+ views | used_count ≥ 3 | Soft install banner appears (not modal) |
| Expired token | expires_at past or used_count > 10 | "This link has expired. Ask your school to send a new one." + WhatsApp school link |

---

**Screen P-2: DPDP Consent Screen**
- Route: Modal, first app launch only
- Entry point: First login completion
- Purpose: Collect informed, per-type DPDP consent

Key elements:
- School logo header
- Title: "Your child's privacy is our first commitment."
- Three individually-checkable consent items (all pre-checked by default)
- [See full privacy policy] link → opens modal overlay
- [I agree →] primary CTA

---

**Screen P-3: Parent Home Feed (REWRITTEN)**
- Route: `/` (default tab)
- Entry point: App launch
- Purpose: Deliver a simple, emotional daily story of the child so parents feel they didn’t miss anything.

Key elements:
- Daily summary card at the top ("Here’s what [child name] did today") with count of today’s posts and any key highlights
- Personalized post feed: full-bleed photos, captions in Fraunces font, child tag, time ago — only where the child is tagged
- Emotional context: gentle copy that frames the day (e.g., "Morning circle", "Art time", milestone highlights)
- Engagement prompts: ❤️ reaction and subtle text ("React to let the teacher know") on each card
- Bottom tab nav: Feed | Milestones | Portfolio | Profile

States:
| State | Trigger | What the parent sees |
|---|---|---|
| Loading | App opens | Skeleton daily summary card + skeleton post cards (warm cream pulsing rectangles) |
| Empty (not yet enrolled) | Child profile exists but no posts | Daily summary card explaining no updates yet + "Your child's first update will appear here soon." + WhatsApp school link |
| Empty (child not added) | Parent account exists but no child linked | Message: "Ask your school to add you to [School Name]." + WhatsApp school link; no posts |
| No posts today | Posts exist but not today | Daily summary card explaining there are no new updates yet; past posts visible with "All quiet so far today. Check back after morning circle!" header |
| No posts for this child this week | Class has posted in the last 7 days but no posts where this child is tagged | Gentle empty state in the summary card and/or feed for the current week (e.g., "This week has been quiet so far" and a smaller line such as "If you're expecting updates, you can check with your school.") plus a non-pushy CTA (e.g., "Check with your school") that opens the platform's default mail/SMS/WhatsApp chooser prefilled with the school's contact details. |
| Network error | No connection | "Couldn't load — check your connection." + Retry; last known daily summary and posts remain visible |
| Normal | Posts exist | Daily summary card followed by reverse-chronological feed of tagged posts |

---

**Screen P-4: Post Detail**
- Route: `/post/:id`
- Entry point: Tap post card on P-3
- Purpose: Full post view with reactions and comments

Key elements:
- Full-screen photo (swipe for multiple)
- Caption (Fraunces font, large)
- Child name tag
- Milestone tags (if any — displayed as soft labels, not buttons)
- ❤️ reaction (tappable)
- Comment input field
- Comment thread
 - Optional "Report incorrect tagging" control (button or text link) allowing parents to flag if they believe the wrong child has been tagged or appears in the media; tapping opens a simple confirmation sheet/dialog with optional text field and a primary "Send report" action that records a structured `post_reports` event and then shows a brief thank-you message.

---

**Screen P-5: Milestone Progress**
- Route: `/milestones` (bottom nav tab 2)
- Entry point: Bottom nav
- Purpose: Show parent their child's developmental progress by domain

Key elements:
- Child name + class at top
- Domain tabs: Physical | Cognitive | Language | Social-Emotional | Aesthetic
- Progress indicator per domain (e.g., "4 of 16 milestones observed")
- Milestone list: name, date observed, link to post where it was observed

States:
| State | Trigger | What the parent sees |
|---|---|---|
| No milestones | New term, nothing logged yet | "Milestones will appear here as teachers observe them in class." |
| Milestones present | Teacher has tagged milestones | Domain-grouped list, achieved milestones highlighted in sage green |

---

**Screen P-6: Year-End Portfolio**
- Route: `/portfolio` (bottom nav tab 3)
- Entry point: Bottom nav + notification
- Purpose: Display and enable download of the AI-generated year-end portfolio

Key elements:
- Portfolio cover (school logo, child photo, child name, academic year)
- Preview of portfolio sections (photo highlights, milestone achievements by domain)
- [Download PDF] button
- "Your portfolio is being prepared" state (before generation completes)

States:
| State | Trigger | What the parent sees |
|---|---|---|
| Not yet generated | Academic year ongoing | "Your child's year-end portfolio will be ready at the end of the school year." |
| Generating | Job queued | "We're preparing [child name]'s portfolio. This may take a few minutes." |
| Ready | PDF generated | Full preview + Download button |

---

**Screen P-7: Notifications**
- Route: `/notifications`
- Entry point: Bell icon in header or notification tap
- Purpose: Show all activity notifications for the parent

Key elements:
- Notification list: post updates, milestone achievements, portfolio ready
- Mark all as read
- Notification preferences link → Profile > Notifications

---

**Screen P-8: Profile / Data & Privacy**
- Route: `/profile` (bottom nav tab 4)
- Entry point: Bottom nav
- Purpose: Account settings, notification preferences, DPDP consent management

Key elements:
- Parent name
- Phone number (read-only)
- Notification preferences: Per-post vs. Daily digest toggle
- Data & Privacy section:
  - Show current consent status per type
  - [Revoke] button per consent item (shows confirmation dialog before action)
- [Log Out] button

---

**Screen P-9: Fees & Payments**
- Route: `/fees` (tab or card from Profile / Home)
- Entry point: Tap "Fees" from the main navigation, profile, or a prominent card on the Parent Home
- Purpose: Give parents a clear view of pending, paid, and overdue fees and, where enabled, a simple way to pay online

Key elements:
- Header: "Fees & Payments for [Child name]"
- Invoice list grouped by status (Pending, Overdue, Paid)
- For each invoice: fee type, amount, due date, status badge, optional notes
- "How to pay" section per invoice (e.g., payment instructions) when online payments are not enabled
- "Pay now" CTA for pending invoices when online UPI payments are enabled

States:
| State | Trigger | What the parent sees |
|---|---|---|
| Loading | Screen opens | Skeleton rows for invoice list |
| No invoices | No fee records yet | "No fees have been issued yet for [child name]." positive empty state |
| All paid | Only paid invoices | "All caught up — no pending fees for [child name]." |
| Pending/Overdue | Unpaid invoices exist | Pending and Overdue sections appear at top with gentle copy; Overdue items highlighted but not blocking access to the rest of the app |

Interactions & Behaviors:
- Tapping an invoice opens a detail view with full notes and payment history.
- Tapping "Pay now" launches the configured online payment/UPI flow; on success, the invoice status updates to Paid on the next refresh.

---

**Screen P-10: Documents & Records**
- Route: `/documents` (under child profile)
- Entry point: Tap "Documents" from the child's profile or a card in the Parent Milestone/Portfolio area
- Purpose: Allow parents to securely view key documents the school has uploaded for their child

Key elements:
- Header: "Documents for [Child name]"
- Document list: document name, type (e.g., Birth certificate, ID proof, Medical certificate), upload date, and file size/icon
- [View] / [Download] actions per document (subject to platform capabilities)

States:
| State | Trigger | What the parent sees |
|---|---|---|
| Loading | Screen opens | Skeleton list rows |
| No documents | No records yet | "Documents shared by your school will appear here." explanation |
| Documents present | One or more documents uploaded | Scrollable list of documents |

Interactions & Behaviors:
- Tapping a document opens an in-app viewer where supported or hands off to the OS viewer.
- Downloads respect authentication/authorisation; links expire appropriately and are not shareable beyond intended scope.

---

**Screen P-11: Incident History**
- Route: `/incidents` (under child profile)
- Entry point: Tap "Incidents" from the child's profile, or via a notification about a new incident
- Purpose: Give parents a clear, sensitive view of any recorded incidents involving their child

Key elements:
- Header: "Incident history for [Child name]"
- List of incident cards: date, high-level type (e.g., Minor injury, Behaviour), short summary, and status (e.g., Notified, Acknowledged)
- Tap-through incident detail view showing: date/time, type, description, follow-up notes, and any recommended next steps

States:
| State | Trigger | What the parent sees |
|---|---|---|
| Loading | Screen opens | Skeleton cards |
| No incidents | No incident records | "No incidents have been recorded for [child name]." with reassuring copy |
| Incidents present | One or more incidents exist | Chronological list (most recent first) of incident cards |

Interactions & Behaviors:
- Tapping a card opens the full incident detail view.
- Where appropriate, parents can mark an incident as acknowledged (e.g., "I’ve read this"), updating internal status without changing the record.

---

### 4.3 Admin / Principal Web Dashboard (React + Vite)

---

**Screen A-1: Dashboard Home (REWRITTEN)**
- Route: `/dashboard`
- Entry point: Login redirect, sidebar nav
- Purpose: Enable fast decision making by surfacing alerts and key metrics in one view.

Key elements:
- Alerts panel at the top (low engagement, fee issues, attendance issues) with CTAs into detailed views
- Engagement score hero: large number, trend arrow, delta label
- Operational tiles: Posts Today | Attendance Today | Fee Alerts
- Class Breakdown table (sorted by engagement %, lowest first) with "Message teacher" quick-action per row

States:
| State | Trigger | What the admin sees |
|---|---|---|
| First week | No prior snapshot | Alerts panel (likely empty) + score shown, trend arrow hidden, "Come back next week..." message |
| Score < 30% | Low engagement | Alerts panel with low-engagement alerts; score in terracotta + alert: "X classes haven't posted this week" |
| Score ≥ 70% | Healthy engagement | Alerts panel may be empty or low severity; score in sage green + "Parents are loving it!" |
| No parents enrolled | 0 parents added | Alerts panel may surface "No parents enrolled"; "Add parents to start measuring engagement." + enrollment link |

---

**Screen A-2: Parent Feed (Read-Only)**
- Route: `/feed`
- Entry point: Sidebar nav
- Purpose: Principal oversight of all posts across all classes

Key elements:
- All posts from all classes (reverse chronological)
- Class filter dropdown
- Teacher filter
- Search by child name
- Read-only: no post creation

---

**Screen A-3: Admissions Pipeline**
- Route: `/admissions`
- Entry point: Sidebar nav
- Purpose: Track inquiries through to enrollment

Key elements:
- Kanban-style column view: New Inquiry | Tour Scheduled | Tour Done | Seat Offered | Enrolled | Not Joining
- Inquiry card: child name, parent name, phone, date of inquiry
- [New Inquiry] button (opens create form)
- "Follow up?" indicator on cards > 14 days in same stage
- Click card → inquiry detail with status update + notes

States:
| State | Trigger | What the admin sees |
|---|---|---|
| Empty | No inquiries added | "No inquiries yet." + "Add first inquiry" CTA |
| Normal | Inquiries exist | Pipeline columns populated |

---

**Screen A-4: Fee Management**
- Route: `/fees`
- Entry point: Sidebar nav or Fee tile on A-1
- Purpose: Create, track, and manage student fee invoices

Key elements:
- Summary row: Total invoiced (this month) | Total collected | Overdue count + amount
- Invoice list with filters: All | Pending | Paid | Overdue
- [Create Invoice] button (opens form)
- [Bulk Create] button (for whole-class invoicing)
- Invoice row: child name, class, fee type, amount, due date, status, [Mark Paid] action
- Print invoice action (CSS print-friendly)

States:
| State | Trigger | What the admin sees |
|---|---|---|
| No fees | New school, no invoices | "No invoices yet. Create your first invoice." |
| All paid | No outstanding invoices | "You're all caught up! No pending fees." — positive state |
| Overdue items | Past due date, unpaid | Overdue section highlighted in terracotta |

---

**Screen A-5: Attendance Dashboard**
- Route: `/attendance`
- Entry point: Sidebar nav or Attendance tile on A-1
- Purpose: School-wide attendance visibility

Key elements:
- Heatmap table: rows = classes, columns = past 30 days, cells = attendance percentage
- Cell color: green ≥80%, amber 60-79%, red <60%, grey = not submitted
- Click cell → class-day detail: individual child presence/absence
- Export CSV button (date range picker)

---

**Screen A-6: Staff Management**
- Route: `/staff`
- Entry point: Sidebar nav
- Purpose: Manage teacher accounts and class assignments

Key elements:
- Staff list: name, role, class assignment, invite status (Active / Invited / Pending)
- [Invite Teacher] button
- Click staff row → edit name, role, class assignment
- [Remove from school] button (confirmation required)

---

**Screen A-7: School Settings**
- Route: `/settings`
- Entry point: Sidebar nav
- Purpose: School branding, configuration, and WhatsApp template setup

Key elements:
- School name (editable)
- Logo upload (PNG/JPG, max 5MB)
- School phone number (used for parent WhatsApp escalation link)
- WhatsApp notification template preview
- Academic year dates (used for portfolio generation trigger)
- Subscription status (plan, children enrolled, billing period) — manual invoicing Year 1

---

**Screen A-8: Reports**
- Route: `/reports`
- Entry point: Sidebar nav
- Purpose: Export historical data

Key elements:
- Report type selector: Attendance | Fee Collection | Engagement History
- Date range picker
- Class filter
- [Export CSV] button
- Last 5 exports listed with download links

---
**Screen A-9: Fees & Payments Overview**
- Route: `/fees` (module home)
- Entry point: Sidebar nav or Fee tile / Fee lifecycle widget on A-1
- Purpose: Provide a consolidated overview of fee plans, invoice status, and revenue metrics with links into detailed invoice and plan views

Key elements:
- Summary KPIs: total invoiced this period, total collected, total overdue, and collection percentage
- Highlighted alerts: overdue invoices exceeding configured thresholds
- Quick links: "View invoices" (A-4), "Manage fee plans" (configuration view), and export actions

States:
| State | Trigger | What the admin sees |
|---|---|---|
| No fee data | New school | Guidance on creating first fee plan and invoices |
| Normal | Active billing | KPI cards + charts or simple tables, plus quick links |

---

**Screen A-10: Admissions Pipeline Overview**
- Route: `/admissions` (module home)
- Entry point: Sidebar nav or Admissions funnel widget on A-1
- Purpose: High-level admissions CRM view summarising pipeline health, with deep links into the Kanban pipeline (A-3) and lead details (Epic 15)

Key elements:
- Funnel summary: counts per stage (New Inquiry, Tour Scheduled, Tour Done, Seat Offered, Enrolled, Not Joining)
- Conversion and drop-off percentages between stages
- Quick filters by term/academic year
- CTA: "Open pipeline board" → A-3, "View leads" → list view

States:
| State | Trigger | What the admin sees |
|---|---|---|
| No leads | No admissions data yet | "No inquiries yet." + CTA to add first inquiry |
| Active pipeline | Leads exist | Funnel with counts and conversion percentages, plus quick filters |

---

**Screen A-11: Child Records**
- Route: `/children` or `/records`
- Entry point: Sidebar nav section ("Child Records"), or links from incidents/fees/admissions
- Purpose: Central admin-facing view of each child's full record, including profile, documents, medical info, emergency contacts, and incident history

Key elements:
- Search and filters (by name, class, status)
- Child list: name, class, status, indicators for missing key data (e.g., no medical info, no emergency contacts)
- Child detail drawer/page showing:
  - Core profile
  - Documents list
  - Medical summary
  - Emergency contacts
  - Incident history summary

States:
| State | Trigger | What the admin sees |
|---|---|---|
| Loading | Screen opens | Skeleton rows and detail placeholders |
| No children | School not yet onboarded | Guidance to add classes/children first |
| Normal | Children exist | Filterable list and detail view |

---

**Screen A-12: Staff Management Overview**
- Route: `/staff` (module home)
- Entry point: Sidebar nav or Staff snapshot tile on A-1
- Purpose: Overview of staff profiles, assignments, and attendance/leave (lite), with links into detailed staff management views

Key elements:
- KPI tiles: total staff, staff per center, staff with missing assignments/profiles
- Current-day attendance/leave snapshot (if enabled): present / on leave / absent counts
- Staff table shortcut: list of staff with role, class/center, and quick actions to edit profile or view attendance history

States:
| State | Trigger | What the admin sees |
|---|---|---|
| No staff | No staff profiles yet | "No staff added yet." + CTA to add first staff member |
| Normal | Staff profiles exist | KPIs + snapshot + quick links into full Staff Management (A-6) views |

---

**Screen A-13: Login**
- Route: `/login`
- Entry point: Direct URL, unauthenticated redirect
- Purpose: Admin / Principal authentication

Key elements:
- School subdomain or email field
- Password field
- [Log In] button
- "Forgot password?" link → phone number + OTP reset flow

---

### 4.4 Teacher Web (Browser — React + Vite)

Teachers who access CadenceSprout from a laptop or desktop browser receive a responsive web experience. Primary viewport: 1280px. Tablet viewport: 768px. Layout adapts from the mobile app screens but takes advantage of the wider canvas — sidebar navigation replaces the bottom tab bar, multi-column layouts replace single-column stacks, and drag-and-drop replaces tap-based media selection. Unless otherwise noted, the Teacher Web experience mirrors the core behaviors of the Teacher mobile app (T-1 to T-7), including AI caption/child-tag behavior, engagement metrics, and basic offline/error states.

---

**Screen TW-1: Teacher Web Login**
- Route: `https://{school}.cadencesprout.com/login` or `cadencesprout.com/login`
- Entry point: Direct URL, unauthenticated redirect from any teacher web route
- Purpose: Authenticate teacher via phone number + password (Sanctum token); shared entry point — role detected post-login, redirect to appropriate home screen

Key elements:
- Centered card layout (max-width 420px) on warm cream background
- CadenceSprout wordmark + school logo above card
- Phone number field (+91 prefix, numeric)
- Password field (masked, show/hide toggle icon)
- [Log In] primary button (sage green, full width)
- "Forgot password?" link → OTP reset flow
- Post-login redirect: role = teacher → TW-2; role = parent → PW-2; role = admin → A-1

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| Default | Page loads | Empty form, disabled Log In button |
| Filled | Inputs populated | Log In button enabled (sage green) |
| Loading | Log In clicked | Button spinner, inputs disabled |
| Error | Invalid credentials | Red inline error below password field: "Incorrect phone number or password." |
| Success | Valid credentials | Redirect to TW-2 Home Feed |

---

**Screen TW-2: Teacher Web Home Feed**
- Route: `/feed`
- Entry point: Post-login redirect, left sidebar nav link
- Purpose: Class-level post feed on wider canvas; primary daily landing screen for web-using teachers

Key elements:
- Left sidebar (240px): school logo, nav links (Feed, Attendance, Roster, Milestones, Profile), teacher avatar + name at bottom
- Main content area: 2-column grid of post cards at 1280px; single column at 768px
- Post card: full-bleed 4:3 photo, caption in Fraunces font, child tag chips, time ago, parent view count badge
- [+ New Post] button in sidebar (primary, sage green) — opens TW-3 Post Composer
- Class selector dropdown in header (if teacher has multiple classes)
- Pull-to-refresh equivalent: refresh icon button in header
 - Engagement feedback strip near the top of the feed summarising recent parent engagement for the selected class (e.g., "80% of parents engaged today — great job!" or "Only 30% of parents saw yesterday's update — consider sharing another moment"), using the same underlying engagement metrics as the admin dashboard.

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| Loading | Page loads | Skeleton cards (2-column) — warm cream pulsing rectangles; engagement strip placeholder skeleton |
| Empty | No children added | "Add your students to get started." + Add Students button |
| No posts today | Posts exist but not today | Past posts visible, date section header: "No posts yet today" |
| Normal | Posts exist | Reverse-chronological 2-column grid plus engagement feedback strip (when data available) at the top of the main content area |
| Offline | No network | Top banner: "You're offline — showing saved content" |

---

**Screen TW-3: Teacher Web Post Composer**
- Route: `/post/new` (full page or large modal overlay)
- Entry point: [+ New Post] button on TW-2
- Purpose: Compose and publish a class post with photo upload, AI caption, child tags, and milestone tags — desktop-optimised with drag-and-drop

Key elements:
- Two-panel layout (1280px): left panel = media upload/preview; right panel = caption, tags, controls
- Left panel: drag-and-drop upload zone (dashed border, sage green accent) + "Browse files" button; supports 1-4 photos or 1 video; photo preview grid (4:3, max 4 tiles)
- Right panel: caption textarea (Fraunces font, AI-drafted or manual); ✨ AI indicator when drafting; child tag chip row (confirmed: solid sage green; pending: dashed grey); "Add children manually" link; "Add milestones (optional)" expandable row; class selector; [Publish Post] primary button
- Keyboard shortcut: Cmd/Ctrl + Enter to publish
- Discard: [Cancel] link navigates back to TW-2

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| No media | Composer opens | Drag-and-drop zone prominent, right panel disabled |
| Media selected | File dropped / browsed | Photo preview renders, AI caption drafting begins, right panel enabled |
| AI drafting | Photo uploaded | Right panel caption area shows shimmer: "Drafting caption..." |
| AI caption ready | < 3 seconds | Caption populates in Fraunces italic + ✨ icon |
| Face recognition pending | Photo uploaded | Child chips show grey/dashed "Identifying..." |
| Face recognition complete | Rekognition returns | Confirmed chips solid, low-confidence chips dashed |
| Upload in progress | Publish clicked | Progress bar across top of composer; button disabled |
| Upload failed | Network drop | Toast: "Upload failed. Click to retry." |

---

**Screen TW-4: Teacher Web Attendance**
- Route: `/attendance`
- Entry point: Left sidebar nav
- Purpose: Daily attendance marking; desktop table view makes it easy to mark multiple children in one scan

Key elements:
- Date header with back-navigation arrows (mark previous days, edit until midnight)
- Attendance table: columns = Child Photo | Child Name | Present | Absent | Absence Reason (optional)
- Each row has Present / Absent radio-style toggle (click to toggle)
- Bulk action: [Mark All Present] button above table
- Optional absence reason: inline dropdown per absent child (Sick / Family reason / Other)
- [Submit Attendance] primary button (bottom of table, sticky on scroll)
- Submission confirmation banner: "Attendance submitted for [date]" (sage green)

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| Not yet taken | Page loads, no submission today | "Take today's attendance." prominent header, all rows unset |
| In progress | Marking in progress | Rows updating, Submit button enabled once all marked |
| Submitted | Submit clicked | Confirmation banner, table becomes read-only (edit option remains until midnight) |
| Past date | Back-nav to prior date | Shows historical record, read-only if past midnight cutoff |

---

**Screen TW-5: Teacher Web Class Roster**
- Route: `/roster`
- Entry point: Left sidebar nav
- Purpose: View and manage all children in the teacher's class; see parent contact info and status

Key elements:
- Search bar (filters by child name or parent name)
- Roster table: columns = Photo | Child Name | Age | Parent Name(s) | Parent Status | Actions
- Parent status badges: Active (sage green) | Invited (amber) | Not Invited (grey)
- Row click → child detail drawer (slides in from right): child photo, DOB, parent phone numbers, milestone summary, recent posts
- [Add Child] button (if teacher has admin rights — otherwise hidden)

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| Loading | Page loads | Skeleton table rows |
| Empty | No children added | "No children in this class yet." + prompt to contact admin |
| Normal | Children exist | Full table |
| Search active | Query typed | Filtered rows, "No results for [query]" if no match |

---

**Screen TW-6: Teacher Web Milestone Tracker (per child)**
- Route: `/roster/:child_id/milestones`
- Entry point: Child row click on TW-5 → Milestones tab in detail drawer
- Purpose: Per-child milestone view; desktop allows seeing multiple domains side-by-side

Key elements:
- Child header: photo, name, class, age
- Domain tab row: Physical | Cognitive | Language | Social-Emotional | Aesthetic
- Per-domain: milestone list (milestone name, age range, achieved/not yet status, date observed, link to source post)
- [Add Milestone] button → opens NEP 2020 taxonomy picker modal
- Progress summary bar per domain (e.g., "4 of 16 milestones observed")
- Side-by-side 2-column domain layout at 1280px; single column at 768px

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| No milestones | New child | "Milestones will appear here as you observe them in class." |
| Milestones present | Posts with milestone tags exist | Domain-grouped lists, achieved milestones highlighted in sage green |
| Loading | Page loads | Skeleton milestone rows |

---

**Screen TW-7: Teacher Web Profile / Settings**
- Route: `/profile`
- Entry point: Left sidebar nav
- Purpose: Manage teacher account details, browser preferences, notification behavior, and logout from the web experience

Key elements:
- Two-column layout at desktop:
  - Left: profile summary card with teacher avatar, name, role, class, school
  - Right: grouped settings panels
- Settings panels:
  - Notifications: parent comment alerts, daily posting reminder, attendance reminder
  - Preferences: language, upload quality default
  - Permissions/help: browser notification status, privacy policy, contact admin
  - Account: [Log Out]
- App/browser version and environment metadata in About section

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| Loading | Page opens | Skeleton profile card + skeleton setting panels |
| Default | Data loads | Profile summary + editable settings panels |
| Browser notifications blocked | Permission denied in browser | Warning banner + "Enable in browser settings" guidance |
| Save success | Setting updated | Inline success toast |
| Save failed | API/network failure | Inline error on affected control |

Interactions & Behaviors:
- Setting toggles save optimistically
- Notification permission row reflects browser-native permission state
- Log Out opens confirmation modal before ending session

Data Requirements:
- Teacher profile
- Web preference settings
- Browser notification permission state
- App version/build metadata

---

### 4.5 Parent Web (Browser)

Parents receive a web view either via a WhatsApp magic-link (no login required) or after completing OTP login. The web experience is optimised for mobile browsers first (parents following a WhatsApp link open it on their phone) but is also fully usable on desktop. Primary viewport: 375px (mobile browser); secondary: 768px (tablet); tertiary: 1280px (desktop). Unless otherwise noted, the Parent Web experience mirrors the core behaviors of the Parent mobile app (P-1 to P-8), including personalised child scoping, summary cards, notifications, and error/offline handling.

---

**Screen PW-1: Parent Web Magic-Link Feed**
- Route: `https://cs.app/f?t={signed_jwt}` (web, no install required)
- Entry point: WhatsApp link tap, SMS link tap
- Purpose: Show parent their child's most recent post immediately without any login friction; gateway to converting to full app install

Key elements:
- School logo + "Powered by CadenceSprout" header (max-height 56px)
- Most recent post: full-bleed 4:3 photo, caption in Fraunces font, child name tag chip
- ❤️ reaction button (no login required for first reaction; tap records reaction server-side)
- Scroll down reveals older posts (paginated, 10 per page)
- Soft install banner (dismissible, appears after 3 page views): "Get the app for all of [child name]'s updates" — banner, never a blocking modal
- Footer: "Secured by CadenceSprout · Privacy Policy"

States:
| State | Trigger | What the parent sees |
|---|---|---|
| Valid token, first visit | Link tapped | Full post feed, no login prompt |
| Valid token, 3+ views | used_count ≥ 3 | Soft install banner appears at top (dismissible) |
| No posts yet | Class exists but no posts | "Your child's teacher hasn't posted yet. Check back soon!" — warm illustration |
| Expired token | expires_at past or used_count > 10 | "This link has expired. Ask your school to send a new one." + WhatsApp school link (410 page) |
| Loading | Page loads | Full-bleed skeleton card pulsing |

---

**Screen PW-2: Parent Web Full Feed (After OTP Login)**
- Route: `https://cs.app/feed` (authenticated web session)
- Entry point: OTP login completion, magic-link "Get full history" CTA
- Purpose: Full chronological feed of all posts where the parent's child is tagged; persistent web session post-login

Key elements:
- Header: school logo, "Good morning, [Parent name]" greeting, notification bell icon with an unread indicator (e.g., badge/dot) when there are unread notifications; tapping the bell opens the Notifications view (PW-7).
- Feed: full-bleed post cards (4:3 photos, Fraunces captions, child tags, time ago, ❤️ reaction)
- Bottom nav (mobile browser): Feed | Milestones | Portfolio | Profile
- Top nav (desktop): inline nav links in header
- Cursor-based infinite scroll pagination

States:
| State | Trigger | What the parent sees |
|---|---|---|
| Loading | Page loads | Skeleton cards (warm cream pulsing rectangles) |
| Empty | No posts yet | "Your child's first update will appear here soon." — no CTA, warm illustration |
| No posts today | Posts exist but not today | Past posts visible; "All quiet so far today. Check back after morning circle!" section header |
| Network error | Connection lost | "Couldn't load — check your connection." + Retry button |
| Normal | Posts exist | Reverse-chronological feed |

---

**Screen PW-3: Parent Web Post Detail**
- Route: `https://cs.app/post/:id`
- Entry point: Tap post card on PW-1 or PW-2
- Purpose: Full-screen post view with photo, caption, milestone tags, and reaction/comment interaction

Key elements:
- Full-bleed photo (edge-to-edge on mobile, max-width 800px centered on desktop)
- Caption in Fraunces font (large, warm, editorial)
- Child name tag chip (sage green)
- Milestone tags (soft label chips, non-interactive display)
- ❤️ reaction button + count
- Comment input field (text, send on Enter/tap)
- Comment thread (parent comment + any teacher reply)
- Posted timestamp + school logo
- [Back to feed] back navigation

States:
| State | Trigger | What the parent sees |
|---|---|---|
| Loading | Page loads | Blurred photo placeholder + skeleton text |
| Normal | Post loaded | Full photo + caption + interactions |
| Photo gallery | Multiple photos | Horizontal swipe carousel (mobile); thumbnail strip (desktop) |
| Post not found | Invalid post ID | "This post is no longer available." with back to feed link |

---

**Screen PW-4: Parent Web Milestone Progress**
- Route: `https://cs.app/milestones`
- Entry point: Bottom nav (mobile) / header nav (desktop); notification tap for milestone achievement
- Purpose: Visual overview of child's developmental milestone progress by NEP 2020 domain

Key elements:
- Child name + class header
- Domain cards (5 domains: Physical | Cognitive | Language | Social-Emotional | Aesthetic): each card shows domain name, icon, progress bar, and "X of Y milestones observed"
- Expanded domain view (click/tap card): milestone list — milestone name, age range, achieved status (sage green checkmark or grey dot), date observed, link to post where observed
- Achieved milestone taps through to the post where the milestone was logged

States:
| State | Trigger | What the parent sees |
|---|---|---|
| No milestones | Nothing logged yet | "Milestones will appear here as teachers observe them in class." — educational, no CTA |
| Some achieved | Partial progress | Mixed achieved (sage green) and not yet (grey) milestones |
| Loading | Page loads | Skeleton domain cards |

---

**Screen PW-5: Parent Web Profile / Settings**
- Route: `https://cs.app/profile`
- Entry point: Bottom nav Profile tab on mobile; header nav Profile on desktop
- Purpose: Let parents manage account details, notification preferences, privacy access, and logout from the web experience

Key elements:
- Profile summary card:
  - Parent name
  - Masked phone number
  - School name
  - Linked child or children summary
- Settings groups:
  - Notifications:
    - Per-post notifications toggle
    - Daily digest toggle
  - Privacy:
    - Data & Privacy row → PW-6
    - Privacy policy row
  - About:
    - App/web version
  - Account:
    - [Log Out] button

States:
| State | Trigger | What the parent sees |
|---|---|---|
| Loading | Page opens | Skeleton profile card + settings rows |
| Default | Data available | Profile card + grouped settings sections |
| Save success | Notification preference updated | Toast: "Settings updated." |
| Save failed | API/network failure | Inline error on affected row |

Interactions & Behaviors:
- Notification preferences save optimistically
- Data & Privacy row opens PW-6
- Log Out returns user to PW-1 or PW-2 depending on next entry path

Data Requirements:
- Parent profile: `name`, `phone`, `school_name`
- Linked child summary
- Notification preference settings
- App/web version metadata

---

**Screen PW-6: Parent Web Privacy Settings (DPDP Consent Management)**
- Route: `https://cs.app/profile/privacy`
- Entry point: PW-5 Profile / Settings → Data & Privacy; DPDP consent screen initial setup
- Purpose: Allow parents to view, modify, and revoke DPDP consent choices at any time; India DPDP Act compliance

Key elements:
- Page title: "Your child's privacy controls"
- School logo + child name context
- Three consent toggle rows (matching initial consent screen):
  1. "Share daily updates with you only" — toggle
  2. "Recognise [child name] in class photos (AI — server-side)" — toggle
  3. "Store data in India (deleted when you leave)" — toggle (non-revocable informational; toggle read-only with tooltip explanation)
- Each toggle row: consent type label, description text, current status (On/Off), toggle control
- Revoking face recognition: shows confirmation dialog before action — "Removing AI recognition means [child name] won't be automatically tagged in new photos. Teachers can still tag manually. This will delete existing recognition data within 24 hours. Are you sure?"
- [See full privacy policy] link → modal with full policy text
- Consent history: "Last updated: [date]" caption per toggle
- [Save changes] button (primary, sage green) — only appears when a toggle has been changed

States:
| State | Trigger | What the parent sees |
|---|---|---|
| Default (all consented) | First load post-consent | All toggles On, no Save button visible |
| Toggle changed | Parent modifies a toggle | Save button appears (sage green) |
| Revoke confirmation | Face recognition toggled Off | Confirmation dialog modal before save |
| Saved | Save clicked | Toast: "Privacy settings updated." |
| Revocation pending | Face recognition revoked | "Existing recognition data will be deleted within 24 hours." info banner |

---

## 5. Key API Contracts

All endpoints are prefixed `/api/v1/`. All authenticated requests require `Authorization: Bearer {sanctum_token}`. Multi-tenancy is enforced via middleware — `school_id` is extracted from the authenticated user, not accepted as a request parameter (to prevent tenancy bypass).

### 5A. Core Data Model (NEW — LOCK BEFORE BUILD)

This is the single source of truth for backend, AI, and analytics. Any schema change must be reflected here before implementation.

**Entities (Phase 1 scope)**

- **School**
  - `id`
  - `name`
  - `logo_url`
  - `subdomain`
  - `created_at`
- **Class**
  - `id`
  - `school_id`
  - `name`
  - `academic_year`
  - `teacher_id`
- **Teacher**
  - `id`
  - `school_id`
  - `name`
  - `phone`
  - `role` (Teacher / Admin in staff context)
- **Parent**
  - `id`
  - `school_id`
  - `name`
  - `phone`
- **Child**
  - `id`
  - `class_id`
  - `parent_id` (primary contact; Phase 1 simple model)
  - `name`
  - `dob`
- **Post**
  - `id`
  - `class_id`
  - `teacher_id`
  - `media_url` (or array `media_urls`)
  - `caption`
  - `created_at`
- **PostChildTag**
  - `id`
  - `post_id`
  - `child_id`
  - `confidence_score` (AI)
  - `confirmed_by_teacher` (boolean)
- **Milestone**
  - `id`
  - `domain` (NEP)
  - `name`
  - `age_range`
- **PostMilestone**
  - `post_id`
  - `milestone_id`
  - `suggested_by_ai` (boolean)
  - `confirmed_by_teacher` (boolean)
- **EngagementEvent**
  - `id`
  - `parent_id`
  - `post_id`
  - `type` (`view` / `like` / `comment`)
  - `timestamp`
- **Attendance**
  - `id`
  - `child_id`
  - `class_id`
  - `date`
  - `status` (`present` / `absent`)
- **Invoice** (Phase 1 basic)
  - `id`
  - `parent_id`
  - `amount`
  - `due_date`
  - `status` (`pending` / `paid` / `overdue`)

### 5B. Notification System (NEW)

The notification system is core to retention and adoption. It orchestrates push, WhatsApp, and in-app surfaces.

#### Notification Events

| Event              | Channel            | Timing    | Priority |
|--------------------|--------------------|-----------|----------|
| New post           | Push + WhatsApp    | Instant   | High     |
| Milestone achieved | Push               | Instant   | Medium   |
| No post today      | Teacher push       | 12 PM     | High     |
| Low engagement     | Admin dashboard    | Daily     | High     |
| Fee reminder       | WhatsApp           | Scheduled | Medium   |
| Portfolio ready    | Push + WhatsApp    | Instant   | High     |

#### Rules

- Max 3 push notifications per day per parent.
- WhatsApp is used only for:
  - Critical updates
  - Re-engagement
- Batch low-priority notifications into a daily digest where possible.

#### Fallback Logic

- If push delivery fails (e.g., token invalid), enqueue a WhatsApp fallback where the event type allows it.
- If WhatsApp delivery fails, retry via a queue with a maximum of 3 attempts before dropping the event and logging it for review.

---

### 5.1 Authentication

**POST `/api/v1/auth/login`**
Teacher / Admin password login.

Request:
```json
{
  "phone": "+919876543210",
  "password": "string"
}
```

Response 200:
```json
{
  "token": "string",
  "user": {
    "id": "uuid",
    "name": "string",
    "role": "teacher | admin",
    "school_id": "uuid",
    "school_name": "string"
  }
}
```

Response 401: `{ "message": "Invalid credentials" }`

---

**POST `/api/v1/auth/otp/request`**
Parent OTP request (sends SMS via MSG91).

Request:
```json
{
  "phone": "+919876543210"
}
```

Response 200: `{ "message": "OTP sent" }`

---

### 🧬 5C. Event Flows & State Persistence (NEW)

This section captures the **backend event system** that turns UI actions into system behaviour. Events are emitted from the Laravel backend and processed via queues (Horizon workers). All handlers must be **idempotent**.

#### 🔁 Core Events (summary)

- **`POST_CREATED`**
  - → Notify parents (push / in-app).
  - → Update feeds (T-1/TW-2, P-3/PW-2) and class/child "day updated" flags.
  - → Trigger milestone AI suggestion workers.
- **`ATTENDANCE_MARKED`** (a.k.a. `ATTENDANCE_SUBMITTED`)
  - → Update admin attendance dashboard and class-level summaries.
  - → Feed attendance into reports/export.
- **`INCIDENT_LOGGED`**
  - → Save a structured record into the child timeline.
  - → Notify parent immediately when sharing is enabled.
- **`DAILY_REPORT_SAVED`**
  - → Attach summary to that day’s child/class story.
  - → Surface in the parent feed and daily/weekly summaries.

#### 5C.1 Canonical Domain Events

| Event name          | Emitted when…                               | Synchronous effects (within request)                          | Asynchronous consumers / side-effects                      |
|---------------------|---------------------------------------------|----------------------------------------------------------------|------------------------------------------------------------|
| `POST_CREATED`      | Teacher successfully creates a post (T-2/TW-3) | Insert `posts`, `post_child_tags`, optional `post_milestones` | Parent notifications, milestone suggestion worker, daily summary aggregator, engagement snapshot, "day updated" flag per class/child |
| `ATTENDANCE_MARKED` | Teacher submits attendance for a class (T-4/TW-4) | Upsert `attendance` rows for each child                        | Admin attendance dashboards (A-1, A-5), absence alerts (if enabled), daily report pre-fill (T-8)                     |
| `DAILY_REPORT_SAVED`| Teacher saves a daily report (T-8)          | Upsert daily report record for `class_id` + `date`             | Parent daily summary surface on P-3/PW-2, weekly digest builder                                      |
| `INCIDENT_LOGGED`   | Teacher saves incident form (T-9)           | Insert incident record linked to `child_id` and `class_id`     | Child timeline enrichment (T-5A), admin alerts, parent notifications / P-11 history (per sharing settings)          |
| `INVOICE_STATUS_CHANGED` | Invoice is created/updated (A-4/A-9)  | Upsert `invoices` row with new `status`                        | Fee reminders/overdue notifications (P-9), admin overdue lists (A-4, A-9), feed cards for overdue fees              |
| `PARENT_VIEWED_POST`| Parent opens a post (P-3/P-4/PW-2/PW-3)     | Insert `engagement_events` row (`view`), update last_seen_at   | Engagement score calculation, teacher "seen by X of Y" stats, low-engagement alerts for admins                    |

Each domain event should have a clear **source screen(s)** and **primary epics** (see Screen Inventory and Epics sections) so ownership is unambiguous.

#### 5C.2 State Persistence & Idempotency Rules

- **Events are immutable** — handlers should never modify past events, only derive new state (rows or aggregates).
- **Idempotent handlers:** if a queue job retries, re-processing the same event **must not duplicate** notifications, invoices, or aggregates.
  - Example: `POST_CREATED` handlers should check whether notifications have already been enqueued for the given `post_id` before creating new ones.
- **Derived state examples:**
  - Engagement score snapshots (`engagement_snapshots`) derived from `EngagementEvent` and `Post`.
  - Per-class "day updated" flag derived from presence of `POST_CREATED` for that class+date.
  - Attendance summary per class derived from `Attendance` rows.

#### 5C.3 Relation to Trigger Engine & Metrics

- The **System Trigger Engine** (Section ⚡) operates on top of these events — e.g., `POST_CREATED` and `PARENT_VIEWED_POST` feed into teacher/parent nudges.
- The **Success Metrics** (Section 10) rely on these same events as their data source (North Star, teacher posting rate, WAU, etc.).
- Any new engagement or OS behaviour should first be modelled as a **new domain event** before UI is designed, to keep the system coherent.

---

**POST `/api/v1/auth/otp/verify`**
Parent OTP verification.

Request:
```json
{
  "phone": "+919876543210",
  "otp": "123456"
}
```

Response 200:
```json
{
  "token": "string",
  "user": {
    "id": "uuid",
    "name": "string",
    "role": "parent",
    "school_id": "uuid"
  },
  "dpdp_consent_required": true
}
```

Response 401: `{ "message": "Invalid or expired OTP" }`

---

**GET `/f?t={signed_jwt}`**
Magic-link resolution (web view, not API — returns HTML).
- 200: Renders the parent web view, increments `magic_link_tokens.used_count`
- 410: Token expired or `used_count > 10` — renders error page

---

### 5.2 Posts

**POST `/api/v1/posts`**
Create a new post (teacher only). Initiates AI caption and face recognition jobs.

Request:
```json
{
  "class_id": "uuid",
  "media_keys": ["s3-key-1", "s3-key-2"],
  "caption": "string | null",
  "tagged_children": ["child_uuid_1", "child_uuid_2"],
  "milestone_ids": ["milestone_uuid_1"]
}
```

Response 201:
```json
{
  "post": {
    "id": "uuid",
    "status": "draft",
    "media_urls": ["https://cdn.cadencesprout.com/..."],
    "caption": "string | null",
    "ai_caption_draft": null,
    "tagged_children": [],
    "milestones": [],
    "created_at": "ISO8601"
  }
}
```

Notes:
- Media is uploaded directly to S3 via pre-signed URL before this call (see 5.4)
- This call immediately dispatches `CaptionDraftJob` (ai-fast queue) and `FaceRecognitionJob` (ai-slow queue)
- AI results are pushed back via Pusher, not polling

---

**GET `/api/v1/posts`**
Paginated class feed (teacher) or child feed (parent).

Query parameters:
- `cursor` (string, optional) — cursor for next page
- `class_id` (uuid, optional — teacher only, if teacher has multiple classes)

Response 200:
```json
{
  "data": [
    {
      "id": "uuid",
      "teacher": { "id": "uuid", "name": "string" },
      "class": { "id": "uuid", "name": "string" },
      "media_urls": ["https://cdn..."],
      "caption": "string",
      "tagged_children": [
        { "id": "uuid", "name": "string", "confirmed_by_teacher": true }
      ],
      "milestones": [
        { "id": "uuid", "domain": "cognitive", "title": "Counting to 10" }
      ],
      "reactions_count": 12,
      "parent_view_count": 18,
      "posted_at": "ISO8601"
    }
  ],
  "next_cursor": "string | null",
  "has_more": true
}
```

Notes:
- For parent role: automatically filters to posts where `post_children.child_id` matches the parent's linked children (`parent_child` table) and `confirmed_by_teacher = true`
- For teacher role: returns all posts for their class(es)
- For admin role: returns all posts for the school (used on A-2)
- Cursor-based pagination — no offset/page number

---

**PATCH `/api/v1/posts/:id`**
Update caption or confirm/remove child tags (teacher only).

Request:
```json
{
  "caption": "string",
  "confirmed_children": ["child_uuid_1"],
  "removed_children": ["child_uuid_2"],
  "status": "posted | archived"
}
```

Response 200: Updated post object (same shape as GET /posts item)

---

**POST `/api/v1/posts/:id/reactions`**
Parent (or magic-link guest) reacts to a post.

Request:
```json
{
  "type": "love"
}
```

Response 201: `{ "reactions_count": 13 }`
Note: Magic-link guests can react without a Sanctum token using their guest session cookie.

---

### 5.3 Child Management

**GET `/api/v1/children`**
List all children for the teacher's class or admin's school.

Query parameters:
- `class_id` (uuid, optional)

Response 200:
```json
{
  "data": [
    {
      "id": "uuid",
      "name": "string",
      "dob": "YYYY-MM-DD",
      "class": { "id": "uuid", "name": "string" },
      "face_recognition_enabled": true,
      "dpdp_consent_at": "ISO8601 | null",
      "parents": [
        { "id": "uuid", "name": "string", "phone": "+91...", "relationship": "mother", "status": "active | invited | pending" }
      ]
    }
  ]
}
```

---

**POST `/api/v1/children`**
Create a child profile (admin only).

Request:
```json
{
  "name": "string",
  "dob": "YYYY-MM-DD",
  "class_id": "uuid",
  "enrollment_photo_key": "s3-key | null"
}
```

Response 201: Child object

---

**POST `/api/v1/children/:id/parents`**
Add a parent to a child (admin only). Triggers magic-link invitation.

Request:
```json
{
  "name": "string",
  "phone": "+919876543210",
  "relationship": "mother | father | guardian"
}
```

Response 201:
```json
{
  "parent": { "id": "uuid", "name": "string", "status": "invited" },
  "magic_link_sent": true
}
```

---

**GET `/api/v1/children/:id/milestones`**
Milestone progress for a specific child.

Response 200:
```json
{
  "child": { "id": "uuid", "name": "string" },
  "domains": [
    {
      "domain": "cognitive",
      "total": 16,
      "achieved": 4,
      "milestones": [
        {
          "id": "uuid",
          "title": "Counting to 10",
          "achieved": true,
          "achieved_at": "ISO8601",
          "post_id": "uuid | null"
        }
      ]
    }
  ]
}
```

---

### 5.4 Media Upload

**POST `/api/v1/media/presign`**
Request a pre-signed S3 upload URL (teacher only).

Request:
```json
{
  "filename": "photo.jpg",
  "content_type": "image/jpeg",
  "size_bytes": 2048000
}
```

Response 200:
```json
{
  "upload_url": "https://s3.amazonaws.com/...",
  "s3_key": "schools/{school_id}/posts/{uuid}/photo.jpg",
  "expires_in": 300
}
```

Notes:
- Client uploads directly to S3 using the `upload_url` (PUT request, no backend involved)
- On upload completion, client calls `POST /api/v1/posts` with the `s3_key`
- S3 bucket policy blocks public access; CloudFront distribution provides the CDN URL used in `media_urls`

---

### 5.5 Attendance

**POST `/api/v1/attendance`**
Submit daily attendance (teacher only).

Request:
```json
{
  "class_id": "uuid",
  "date": "YYYY-MM-DD",
  "records": [
    { "child_id": "uuid", "present": true, "reason": null },
    { "child_id": "uuid", "present": false, "reason": "sick" }
  ]
}
```

Response 201: `{ "message": "Attendance submitted", "date": "YYYY-MM-DD", "class_id": "uuid" }`

---

**GET `/api/v1/attendance`**
Get attendance records (admin: all classes, teacher: own class).

Query parameters:
- `class_id` (uuid, optional)
- `date_from` (YYYY-MM-DD)
- `date_to` (YYYY-MM-DD)

Response 200:
```json
{
  "data": [
    {
      "date": "YYYY-MM-DD",
      "class": { "id": "uuid", "name": "string" },
      "submitted": true,
      "present_count": 14,
      "absent_count": 2,
      "total": 16
    }
  ]
}
```

---

### 5.6 Fee Management

**POST `/api/v1/fees/invoices`**
Create a fee invoice (admin only).

Request:
```json
{
  "child_id": "uuid",
  "fee_type": "tuition | activity | transport | other",
  "amount": 3500.00,
  "due_date": "YYYY-MM-DD",
  "description": "April Tuition Fee"
}
```

Response 201: Invoice object

---

**PATCH `/api/v1/fees/invoices/:id`**
Update invoice status (mark as paid).

Request:
```json
{
  "status": "paid",
  "payment_method": "cash | upi | bank_transfer",
  "paid_at": "ISO8601"
}
```

Response 200: Updated invoice object

---

**GET `/api/v1/fees/invoices`**
List invoices (admin only).

Query parameters:
- `status` (pending | paid | overdue | all)
- `class_id` (uuid, optional)
- `date_from`, `date_to`

Response 200: Paginated invoice list

---

### 5.7 Engagement Score

**GET `/api/v1/dashboard/engagement`**
Get the school-level engagement score (admin only).

Response 200:
```json
{
  "current_week": {
    "week_starting": "YYYY-MM-DD",
    "score_pct": 73,
    "active_parents": 36,
    "total_parents": 49
  },
  "previous_week": {
    "score_pct": 61
  },
  "trend": "up | down | stable | insufficient_data"
}
```

---

**GET `/api/v1/dashboard/summary`**
Dashboard summary tiles (admin only).

Response 200:
```json
{
  "posts_today": {
    "total": 12,
    "by_class": [
      { "class_id": "uuid", "class_name": "Nursery A", "count": 4 }
    ]
  },
  "attendance_today": {
    "classes_submitted": 4,
    "total_classes": 6,
    "pct": 67
  },
  "fee_alerts": {
    "overdue_count": 3,
    "overdue_amount": 10500.00
  }
}
```

---

## 6. Non-Functional Requirements

### 6.1 DPDP Act 2023 Compliance

The Digital Personal Data Protection Act 2023 applies directly to CadenceSprout because the product processes personal data (including photos and videos) of minors.

**Consent requirements:**
- Explicit, informed, per-type consent must be obtained from parents before any personal data of their child is processed
- Consent must be granular: separate consent for (1) sharing updates, (2) AI face recognition, (3) data residency and retention
- Consent must be revocable at any time from Profile > Data & Privacy
- Revocation of face recognition consent must trigger deletion of Rekognition data within 24 hours (SLA documented in privacy policy)
- Consent screen must be shown exactly once per parent per child — never shown again after consent is given
- Every consent change (grant or revoke) must be written to an audit log with timestamp

**Data residency:**
- All media (photos, videos) must be stored on AWS S3 in the `ap-south-1` (Mumbai) region
- PostgreSQL database must be hosted in India
- No personal data of Indian minors may be routed through data centers outside India

**Data retention and deletion:**
- Parents must be able to request deletion of all their child's data
- On deletion request: all media deleted from S3, all posts and tags for that child deleted, Rekognition face collection entry deleted
- Deletion must complete within 30 days of request (align with DPDP Act timelines)
- Deletion confirmation sent to parent via SMS

**POCSO documentation:**
- CadenceSprout does not store or process any data related to abuse reports
- Teachers cannot post media from outside the school context
- School admins can report and remove content flagged as inappropriate

**Legal review:**
- DPDP compliance review by qualified legal counsel must be completed and signed off before product launch (Month 2 deadline per CEO Plan)
- Privacy policy must be reviewed by legal counsel before it is shown to parents

---

### 6A. Permissions Matrix (NEW)

Permissions are critical for DPDP compliance and for maintaining parent trust. The table below summarizes who can see and edit what.

| Role    | Can View              | Can Edit            | Restrictions                        |
|---------|-----------------------|---------------------|-------------------------------------|
| Teacher | Children in own class | Posts, attendance   | Cannot access other classes         |
| Parent  | Own child only        | Reactions, comments | Cannot see other children           |
| Admin   | Entire school         | All (school-scoped) | Full access at school scope only    |

**Special Rules**

- Parents ONLY see posts where their child is tagged and confirmed by the teacher.
- Group photos are visible to a parent only if their child is tagged on that post.
- Teachers must confirm AI child tagging before a post becomes visible to parents.

---

### 6.2 Performance Targets

**API response times (95th percentile):**
- Feed load (`GET /api/v1/posts`): < 500ms
- Post creation (`POST /api/v1/posts`): < 300ms (returns immediately; AI jobs are async)
- Dashboard summary (`GET /api/v1/dashboard/summary`): < 800ms
- Magic-link resolution: < 1000ms

**AI job times:**
- Caption draft (CaptionDraftJob, ai-fast queue): < 3 seconds end-to-end (teacher sees result in composer)
- Face recognition (FaceRecognitionJob, ai-slow queue): < 30 seconds (teacher sees tag suggestions in post detail or composer after posting)
- Portfolio generation (PortfolioGenerateJob, ai-batch queue): < 5 minutes per child (nightly batch, not real-time)

**Media:**
- Thumbnail generation: S3 + CloudFront CDN serves thumbnails within 2 seconds of upload on Indian mobile networks (tested at 4G speeds)
- Client-side video compression: < 60 seconds for a 50MB video on a mid-range Android device

**Feed pagination:**
- Cursor-based pagination only; no offset pagination
- Page size: 20 posts per page
- Feed with 1,000+ posts must load first page in < 500ms

**Pusher real-time:**
- Post published → parent receives Pusher event within 2 seconds (P95)
- On Pusher reconnect: client fetches posts since `last_seen_at` to backfill missed events

---

### 6.3 Accessibility

**React Native (Teacher + Parent apps):**
- Minimum touch target: 44×44pt (iOS) / 48×48dp (Android) on all interactive elements
- All Text components use `allowFontScaling={true}` — tested at 200% system font size
- All interactive elements have `accessibilityLabel` set
- Photo components have `accessibilityLabel` set to the post caption text (for screen readers)
- Color contrast: all text on background combinations must meet WCAG AA (4.5:1 ratio minimum)
- Keyboard: form inputs must advance with `returnKeyType="next"`; final input uses `returnKeyType="done"`
- Offline feedback: persistent banner "You're offline — showing saved content" when network unavailable

**React + Vite Admin Dashboard (Web):**
- Responsive at 375px (mobile), 768px (tablet), 1280px (desktop)
- At < 768px: bottom tab navigation, single-column stacked layout
- Keyboard navigable tables — all table rows reachable by keyboard
- Focus ring visible on all interactive elements (never `outline: none`)
- Fee invoices and attendance reports must print cleanly (`@media print` CSS)

---

### 6.4 Security

**Authentication:**
- Sanctum tokens: 30-day TTL, invalidated on logout
- OTP TTL: 10 minutes
- Magic-link JWT: 24-hour TTL, max 10 uses
- Tokens stored in React Native SecureStore (not AsyncStorage)

**Multi-tenancy:**
- PostgreSQL RLS enforces `school_id` isolation on every query
- `school_id` is never accepted as a request parameter — it is always derived from the authenticated user's token
- An integration test proving cross-tenant data isolation must exist and pass in CI before any feature code ships

**Media access:**
- S3 bucket is private; media is served exclusively through CloudFront with signed URLs
- Pre-signed upload URLs expire after 5 minutes

**Face recognition:**
- Rekognition is called only when `children.dpdp_consent_at IS NOT NULL`
- A CI test must enforce this gate — failure means a DPDP violation

---

### 6B. Edge Case Handling (NEW)

Robust handling of AI and data edge cases is essential for trust.

**AI Errors**

- Teachers can:
  - Remove incorrect child tags suggested by AI.
  - Add missing child tags manually.
- Parents can:
  - Report incorrect tagging (for example, "This is not my child") from the post detail view, which flags the post for admin review.

**Data Issues**

| Scenario                    | Resolution                               |
|-----------------------------|------------------------------------------|
| Duplicate child             | Admin merge tool                         |
| Wrong parent linked         | Admin reassigns child to correct parent  |
| Teacher posted wrong class  | Editable within 10 minutes, then locked  |

**System Failures**

- Upload fails → retry queue + clear manual retry affordance in the UI.
- AI caption fails → fallback to manual caption input with a friendly prompt.
- Face recognition fails → manual child tagging remains available and is clearly surfaced.

---

### 6.5 Internationalisation Infrastructure

- `react-i18next` must be integrated from Month 1 for both the React Native app and the React + Vite web dashboard
- All user-facing strings must use i18n keys — no hardcoded English strings in JSX
- English is the only supported language at launch
- Hindi and Tamil strings are Phase 2 (Month 12 target) — the infrastructure must be ready to accept them without a refactor

---

### 6.6 Cost and Infrastructure

- All infrastructure runs on AWS `ap-south-1` (Mumbai) for India data residency
- Unit cost target at launch: ~₹790/school/month (50 children, 5 classes, 3 teachers) — see ENG_REVIEW.md cost model
- Revenue at launch pricing: ₹20/child × 50 children = ₹1,000/school/month
- Gross margin at launch: ~21% — thin, improving to ~60-70% with Phase 2 AI optimization
- Rekognition cost optimization: batch face recognition at end-of-day rather than per-post from Month 1 where technically feasible (saves ~$3/school/month)

---

## 7. Technology Architecture

### 7.1 Stack Decisions

| Layer | Technology | Rationale |
|-------|-----------|-----------|
| **Backend API** | Laravel (PHP 8.2) + Sanctum + Horizon | Team already knows Laravel; ships Day 1 with no ramp-up. Sanctum handles mobile token auth; Horizon manages async AI queues natively. |
| **Database** | PostgreSQL + Row Level Security | RLS enforces `school_id` isolation at the DB layer — a query without tenant context returns 0 rows, making cross-tenant data leaks structurally impossible. |
| **Queue / background jobs** | Laravel Horizon + Redis | Three priority queues for AI work: `ai-fast` (caption drafting, <3s), `ai-slow` (face recognition, <30s), `ai-batch` (portfolio generation, nightly). |
| **Mobile app** | React Native (iOS + Android) | One codebase for teacher app + parent app. Team has existing React Native expertise. |
| **Web admin dashboard** | React + Vite | Team knows React JS. SSR not needed for a B2B internal dashboard — Next.js adds complexity with no benefit here. |
| **Media storage** | AWS S3 (ap-south-1) + CloudFront CDN | India data residency. Pre-signed URL pattern: API issues the URL, client uploads directly to S3. Media never passes through the API server. |
| **Real-time feed** | Pusher + Laravel Echo | When a teacher posts, Pusher broadcasts to parents of that class who are online. Native Laravel integration. Free tier covers pilot phase. |
| **AI / LLM gateway** | OpenRouter (multi-model routing) | Routes caption drafting to cheapest model that meets quality bar. Gemini Flash (~$0.0001/call) for standard captions; escalates to GPT-4o-mini (~$0.0003/call) if quality score < 7. 5–10× cheaper than locking into a single provider. |
| **On-server ML** | Fine-tuned small model (Phase 2) | Milestone suggestion engine trained on NEP 2020 taxonomy using Phase 1 usage data. Phase 1 uses LLM for this. |
| **Face recognition** | AWS Rekognition | Only viable server-side face recognition for ages 3–6. ML Kit does face *detection* only — not recognition. Called only after explicit DPDP consent. |
| **Notifications** | Wapi (WhatsApp) → MSG91 (SMS fallback) | Wapi is an unofficial WhatsApp gateway (~95% uptime). MSG91 triggers on Wapi failure. Migrate to official WhatsApp Business API post-launch. |
| **CI/CD** | GitHub Actions | Standard: lint → test → build → deploy. |

---

### 7.2 System Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│                        CLIENT LAYER                               │
│                                                                    │
│  React Native App              React + Vite Admin                │
│  (Teacher + Parent)            (Principal / Admin)               │
│  iOS + Android                 Web Browser                       │
└─────────────────────┬────────────────────────┬───────────────────┘
                      │                        │
                      ▼                        ▼
┌──────────────────────────────────────────────────────────────────┐
│                   LARAVEL REST API (/api/v1/*)                    │
│                                                                    │
│  Auth:         Sanctum tokens (mobile) + session (web)           │
│  Multi-tenant: school_id middleware → Postgres RLS               │
│  Versioning:   /api/v1/* — breaking changes go to /api/v2/*      │
└──────────┬───────────────────────────────────┬───────────────────┘
           │                                   │
           ▼                                   ▼
┌──────────────────┐             ┌─────────────────────────────────┐
│   PostgreSQL     │             │      LARAVEL HORIZON QUEUES      │
│   + RLS policy   │             │                                   │
│   + Redis        │             │  ai-fast   (3 workers, <3s)      │
│                  │             │    ├─ CaptionDraftJob            │
│   school_id set  │             │    └─ MilestoneTagJob            │
│   on every DB    │             │                                   │
│   connection;    │             │  ai-slow   (2 workers, <30s)     │
│   RLS enforces   │             │    └─ FaceRecognitionJob          │
│   automatically  │             │                                   │
└──────────────────┘             │  ai-batch  (1 worker, nightly)   │
                                 │    └─ PortfolioGenerateJob        │
                                 └──────────────┬──────────────────┘
                                                │
                                 ┌──────────────▼──────────────────┐
                                 │        EXTERNAL SERVICES         │
                                 │                                   │
                                 │  OpenRouter ──► Gemini Flash     │
                                 │      └─ escalate ► GPT-4o-mini  │
                                 │                                   │
                                 │  AWS Rekognition (face ID)       │
                                 │  AWS S3 ap-south-1 + CloudFront  │
                                 │  Pusher (real-time feed)         │
                                 │  Wapi ──► MSG91 (notifications)  │
                                 └─────────────────────────────────┘
```

---

### 7.3 Multi-Tenancy Model

Every table has a `school_id` column. PostgreSQL Row Level Security enforces it at the database connection level — not in application code.

```
Middleware chain on every authenticated request:
  1. auth:sanctum          → validate token
  2. SetTenantFromToken    → extract school_id from user record
  3. PostgresRLS           → SET app.current_school_id = {school_id}
                              RLS policy runs on EVERY query

Result: a query that omits a school_id filter returns 0 rows.
Cross-tenant data leaks are structurally impossible.
```

DPDP implication: data deletion scoped to `school_id` — a single scoped delete removes all data cleanly with no orphaned records.

---

### 7.4 Data Model (Core Tables)

```
schools         id, name, logo_url, brand_color, subdomain

users           id, school_id, role (teacher|parent|admin),
                name, phone, email, otp_secret

children        id, school_id, name, dob, class_id,
                face_embedding_s3_key, dpdp_consent_at

classes         id, school_id, name, academic_year, teacher_id

parent_child    parent_id, child_id, relationship

posts           id, school_id, teacher_id, class_id,
                media_urls (jsonb), caption, ai_caption_draft,
                caption_edited_by_teacher, ai_model_used,
                ai_cost_usd, status (draft|posted|archived)

post_children   post_id, child_id, confidence_score,
                confirmed_by_teacher

milestones      id, domain, code, title, description,
                age_range_months  (~80 rows, NEP 2020 pre-loaded)

post_milestones post_id, milestone_id, suggested_by_ai,
                confirmed_by_teacher

engagement_     school_id, week_starting, score_pct,
snapshots       active_parents, total_parents

magic_link_     id, parent_id, child_id, token_hash,
tokens          expires_at, used_count, max_uses (default 10)
```

Key indexes: `(school_id, class_id, created_at DESC)` on posts, `(child_id, post_id)` on post_children.

---

### 7.5 AI Pipeline — Caption Drafting

```
Teacher selects photo → taps POST
         │
         ▼
POST /api/v1/posts  (draft record created instantly — non-blocking)
         │
         ▼  CaptionDraftJob → 'ai-fast' queue
         │
         ▼
OpenRouter quality router:
  Input: photo S3 key + confirmed child names + class + time of day
  │
  ├─ Step 1: Gemini Flash (~$0.0001/call)
  │    Quality score (0–10):
  │      +2 child name present
  │      +2 length > 10 words
  │      +3 no hallucinated details
  │      +3 warm tone (sentiment check)
  │
  ├─ Score ≥ 7 → use draft
  └─ Score < 7 → escalate to GPT-4o-mini (~$0.0003/call)
         │
         ▼
Draft pushed via Pusher to teacher's compose screen
Teacher reviews → edits if needed → posts
Failure: timeout or both models fail → empty caption box,
         placeholder "What happened in this moment?" — post never blocked
```

---

### 7.6 AI Pipeline — Face Recognition

```
Post created → FaceRecognitionJob → 'ai-slow' queue (async)
         │
         ▼
DPDP gate: child.dpdp_consent_at IS NOT NULL?
  NO  → skip entirely. Post goes live untagged. ✓
  YES → continue
         │
         ▼
AWS Rekognition SearchFacesByImage
  Collection: 'school_{school_id}'
  (built at enrollment from reference photo)
         │
  confidence > 90%   → suggest tag (pre-checked)
  confidence 70–90%  → suggest tag (teacher must confirm)
  confidence < 70%   → no suggestion
         │
         ▼
Pusher notifies teacher → confirms or dismisses tags
Only confirmed tags visible to parents
```

---

### 7.7 Magic-Link Parent Onboarding

```
Admin adds parent phone → signed JWT generated
  {parent_id, child_id, school_id, exp: 24h}
         │
         ▼
Wapi WhatsApp: "Rohan had a great morning! → [link]"
         │
         ▼
Parent taps → browser opens → guest session (no login)
Feed-first: post visible immediately
         │
  visits 1–3: token auth (no prompt)
  visit 4+:   OTP phone prompt
         │
         ▼
OTP login → full Sanctum session
DPDP consent screen (once per parent per child)
  ☑ Share daily updates with you only
  ☑ Recognise [child] in class photos (AI)
  ☑ Store data in India (deleted when you leave)
         │
         ▼
Notification preferences → feed
```

---

### 7.8 Media Pipeline

Client-side compression before upload — large files never hit the API server.

```
Teacher selects media
  Photo → react-native-image-resizer → ≤ 500KB
  Video → react-native-video-compress → ≤ 10MB
         │
         ▼
GET /api/v1/media/upload-url  (Laravel issues pre-signed S3 URL)
         │
         ▼
Client uploads directly to S3 (bypasses API server)
         │
         ▼
PATCH /api/v1/posts/{id}  (upload complete, S3 key stored)
CloudFront CDN serves media to parents

S3 Lifecycle (automatic):
  Day   0–90:   Standard, full resolution
  Day  90–365:  Lambda recompresses to 480p (~50% size reduction)
  Day 365+:     Glacier Deep Archive ($0.00099/GB/month)
  Portfolio PDFs: Standard forever (thumbnails only)
```

---

### 7.9 Cost Model (Unit Economics)

Per-school per month at 50 children, 5 classes, 3 teachers:

| Cost item | Monthly cost (USD) |
|-----------|--------------------|
| AWS S3 + CloudFront CDN | ~$0.54 |
| AWS Rekognition (face recognition) | ~$4.50 |
| OpenRouter (caption drafting) | ~$0.90 |
| MSG91 SMS fallback | ~$2.70 |
| Pusher, Redis, PostgreSQL (amortised) | ~$0.80 |
| **Total per school / month** | **~$9.50 (~₹790)** |

Revenue at ₹20/child × 50 children = **₹1,000/school/month → ~21% gross margin at launch.**

Primary cost lever: Rekognition ($4.50) is 47% of cost. Phase 2 optimisation (batch processing + on-server ML model) reduces cost to ~$3–4/school/month → **60–70% gross margin**.

**Pricing decision:** Do not fix final pricing until Month 3 when real usage costs are confirmed from pilot data. The model supports ₹50/child/month at 60–70% margin post-Phase 2 optimisation.

---

## 8. Phase 2 — Post First 10 Paying Customers

Phase 2 begins when: 10+ paying schools are live, NPS ≥ 30, and the Phase 1 product is stable. These epics are not in scope during Phase 1 and must not be built early.

---

### Epic P2-1: Razorpay Auto-Billing

**Trigger:** Manual invoicing is operationally unsustainable beyond 20 schools.

**User stories:**

| Story | As a… | I want to… | So that… |
|-------|--------|------------|----------|
| P2-1.1 | School admin | Add a Razorpay-linked payment method | Monthly fees are charged automatically |
| P2-1.2 | School admin | Set per-child billing amount and billing cycle | Each school can have its own pricing |
| P2-1.3 | System | Verify billed child count against attendance records | Schools cannot under-report enrollment to reduce fees |
| P2-1.4 | School admin | View billing history and download invoices | Finance and accounting are self-serve |
| P2-1.5 | Parent | Receive fee payment reminder and pay online | No cash or bank transfer needed |

**Acceptance criteria (P2-1.3 — fraud prevention):**
- If billed enrollment < 90% of average daily attendance over trailing 30 days → alert sent to CadenceSprout admin
- Alert includes: school name, billed count, attendance-derived count, delta
- School is not auto-suspended — human review required

---

### Epic P2-2: Hindi + Tamil Language Support

**Trigger:** Phase 1 i18n infrastructure (react-i18next) is already in place. Phase 2 adds the string translations.

**User stories:**

| Story | As a… | I want to… | So that… |
|-------|--------|------------|----------|
| P2-2.1 | Teacher | Switch app language to Hindi or Tamil | I can use CadenceSprout in my native language |
| P2-2.2 | Parent | Receive WhatsApp notifications in my language | I understand updates without translation |
| P2-2.3 | AI caption system | Draft captions in the teacher's app language | Parents receive captions in a language they read |
| P2-2.4 | Admin | Set school-level default language | New users default to the school's primary language |

**Acceptance criteria (P2-2.1):**
- Language toggle available in Profile → Settings
- All UI strings, error messages, and empty states translated (no English fallback visible to end user)
- Language preference persisted across sessions and app reinstalls
- RTL layout NOT required for Hindi/Tamil (left-to-right scripts)

**Scope note:** Marathi, Telugu, Kannada are Phase 3. Arabic + RTL is Phase 3.

---

### Epic P2-3: Per-Class and Per-Teacher Engagement Score

**Trigger:** School owners with 5+ classes need to identify which teacher is not posting, not just the school-level aggregate.

**User stories:**

| Story | As a… | I want to… | So that… |
|-------|--------|------------|----------|
| P2-3.1 | Principal | See engagement score broken down by class | I can identify which class has low parent activity |
| P2-3.2 | Principal | See posts-per-day broken down by teacher | I can have a data-backed conversation with underperforming teachers |
| P2-3.3 | Teacher | See my own class's engagement score | I'm motivated by the number going up |
| P2-3.4 | System | Store per-class snapshots weekly | Historical trends available for principal review |

**Acceptance criteria (P2-3.1):**
- Class breakdown table on admin dashboard, sorted by engagement % ascending (lowest first)
- One-tap action: "Message teacher" opens WhatsApp with teacher's number pre-filled
- Data is weekly snapshot, not real-time (same formula as school-level score)

---

### Epic P2-4: HRMS — Staff Management

**Trigger:** Schools with 10+ staff need payroll, leave, and performance tracking beyond Phase 1's names/roles/class-assignment.

**User stories:**

| Story | As a… | I want to… | So that… |
|-------|--------|------------|----------|
| P2-4.1 | Admin | Record staff salary, pay cycle, and bank details | Monthly payroll is calculated in the system |
| P2-4.2 | Teacher | Apply for leave and see remaining leave balance | I don't need to call HR or fill a paper form |
| P2-4.3 | Admin | Approve or reject leave requests | Leave management is auditable |
| P2-4.4 | Admin | Record staff attendance (check-in/check-out) | Payroll deductions for absences are accurate |
| P2-4.5 | Admin | Set performance goals and record appraisal notes | Annual reviews have a data trail |

**Schema note:** Phase 1 `users` table must include nullable HRMS fields (`salary`, `pay_cycle`, `bank_details_encrypted`) so Phase 2 adds columns without a data migration.

---

### 🚀 Growth Hooks (NEW)

Built-in virality and growth loops that tie product value to acquisition.

1. **Shareable Moments**
   - Parents can share selected posts externally.
   - Shared views include subtle "Powered by CadenceSprout" branding.
2. **Portfolio Sharing**
   - Year-end portfolio PDFs can be shared via link.
   - Acts as a marketing asset during admissions season.
3. **Admissions Loop**
   - Inquiry source tracking and referral tagging for new leads.
4. **WhatsApp Entry Funnel**
   - Magic link → web feed → app install as the default funnel.

**Metrics (how we know these are working)**

- **Shareable Moments:** % of posts that are shared externally at least once each week.
- **Portfolio Sharing:** % of active parents who open or download the year-end portfolio.
- **Admissions Loop:** % of new admissions that have a captured referral source or tagged referrer.
- **WhatsApp Entry Funnel:** Magic-link → app install conversion rate (see Success Metrics → Leading Indicators).

---

### Epic P2-5: Official WhatsApp Business API Migration

**Trigger:** Wapi (unofficial bridge) is blocked or unreliable. Official API provides guaranteed delivery, read receipts, and rich message templates.

**User stories:**

| Story | As a… | I want to… | So that… |
|-------|--------|------------|----------|
| P2-5.1 | System | Send WhatsApp notifications via official API | Delivery is guaranteed and auditable |
| P2-5.2 | School admin | Use school-branded WhatsApp sender name | Parents see "[School Name]" not a generic number |
| P2-5.3 | System | Track delivery and read receipts per notification | Engagement data is accurate |

**Migration note:** Phase 1 Wapi integration must be behind a feature flag / adapter interface so Phase 2 can swap the provider without touching notification logic.

---

### Epic P2-6: Offline-First Data Sync

**Trigger:** Semi-urban and rural preschool markets have unreliable connectivity. Teachers cannot post when network drops.

**User stories:**

| Story | As a… | I want to… | So that… |
|-------|--------|------------|----------|
| P2-6.1 | Teacher | Create a post while offline | It uploads automatically when network returns |
| P2-6.2 | Teacher | Take attendance offline | Records sync when connection is restored |
| P2-6.3 | Parent | View cached posts when offline | I can see recent content without a connection |
| P2-6.4 | System | Resolve conflicts when the same data is edited offline on two devices | No data is lost |

**Technical approach:** WatermelonDB (React Native) for local-first storage with sync to the Laravel backend. Conflict resolution: last-write-wins for posts, server-authoritative for attendance.

---

### Epic P2-7: Extended Content — Quizzes, Library, Live Camera

**User stories (high-level — detailed spec at Phase 2 planning):**

| Story | Feature |
|-------|---------|
| P2-7.1 | Interactive quizzes — teachers assign, children complete on parent's phone |
| P2-7.2 | Children's library — curated digital books and audio stories per age group |
| P2-7.3 | Live camera / daycare view — parent can see classroom live stream during school hours |
| P2-7.4 | Bus tracking — real-time GPS tracking of school bus, ETA notifications to parents |
| P2-7.5 | Infirmary — health incident logging (injury, fever, medication) with parent notification |
| P2-7.6 | Supplies / warehouse — consumable stock tracking for school supplies |

---

### Epic P2-8: On-Server ML Model for Milestone Suggestion

**Trigger:** Phase 1 LLM costs for milestone tagging are ~$0.0003/post. At 10,000 posts/day, that's $3/day. A fine-tuned on-server model eliminates this.

**User stories:**

| Story | As a… | I want to… | So that… |
|-------|--------|------------|----------|
| P2-8.1 | System | Suggest NEP 2020 milestones from post caption using on-server model | AI cost per post approaches zero at scale |
| P2-8.2 | Product team | Retrain the model quarterly on confirmed milestone tags | Suggestions improve over time |

**Training data:** Phase 1 `post_milestones` table where `suggested_by_ai = true` AND `confirmed_by_teacher = true`. Minimum 10,000 confirmed tags before Phase 2 model training begins.

---

## 9. Phase 3 — Franchise and Global

Phase 3 begins when: India PMF is confirmed (ARR > ₹1Cr, NPS ≥ 50). Franchise chain conversations should start Month 10 but deals close in Phase 3.

---

### Epic P3-1: White-Label and Franchise Chain Support

**Trigger:** Eurokids, Kidzee, Bachpan, Podar Jumbo Kids — each with 1,000–1,200 centers — require per-chain branding.

**User stories:**

| Story | As a… | I want to… | So that… |
|-------|--------|------------|----------|
| P3-1.1 | Franchise chain admin | Apply chain-wide branding (logo, colors, name) | All centers under the chain look consistent |
| P3-1.2 | Franchise chain admin | Remove all CadenceSprout branding | Parents see only the chain's brand |
| P3-1.3 | Franchise chain admin | View engagement scores across all centers | I can identify underperforming centers chain-wide |
| P3-1.4 | Individual center admin | Manage their center independently | Day-to-day ops don't require chain-level access |
| P3-1.5 | System | Bill the franchise chain at a negotiated per-center rate | Enterprise pricing differs from individual school pricing |

**Architecture note:** Phase 1 must use design tokens (not hardcoded hex values) for all brand colors. Phase 3 white-labeling replaces tokens per chain — no code changes required.

---

### Epic P3-2: Arabic Language and RTL UI (Dubai Market)

**Trigger:** Dubai preschool market has similar dynamics to India — Seesaw is expensive. Arabic + RTL unlocks the GCC market.

**User stories:**

| Story | As a… | I want to… | So that… |
|-------|--------|------------|----------|
| P3-2.1 | Teacher | Use CadenceSprout in Arabic | I can work in my native language |
| P3-2.2 | Parent | Receive updates in Arabic | I understand my child's progress |
| P3-2.3 | System | Render all UI elements right-to-left | Arabic text and layout feels native, not mirrored |
| P3-2.4 | AI caption system | Draft captions in Arabic | Teachers in Arabic-medium schools can post in Arabic |

**Technical note:** RTL requires layout changes in React Native (`I18nManager.forceRTL(true)`) and React admin (`dir="rtl"` + CSS logical properties). This is a significant engineering effort — budget 4–6 weeks.

---

### Epic P3-3: CRM Integrations

**Trigger:** Franchise chains use Salesforce, HubSpot, or Zoho for admissions pipeline management. CadenceSprout admissions data needs to flow into their CRM.

**User stories:**

| Story | As a… | I want to… | So that… |
|-------|--------|------------|----------|
| P3-3.1 | School admin | Sync admissions inquiries to Salesforce/HubSpot/Zoho | My sales team works in one CRM |
| P3-3.2 | School admin | Pull enrolled child data from the CRM | No double-entry between CRM and CadenceSprout |
| P3-3.3 | System | Provide a webhook API for CRM integrations | Third-party CRM vendors can build integrations |

---

### Epic P3-4: Southeast Asia Expansion

**Trigger:** Post India PMF. Indonesia, Vietnam, Philippines have similar market dynamics — Seesaw is expensive, WhatsApp is dominant, and preschool chains are underserved.

**User stories (high-level):**

| Story | Feature |
|-------|---------|
| P3-4.1 | Bahasa Indonesia language support |
| P3-4.2 | Vietnamese language support |
| P3-4.3 | Filipino (Tagalog) language support |
| P3-4.4 | Local payment gateways (GoPay, VNPay, GCash) |
| P3-4.5 | Data residency in SEA region (AWS ap-southeast-1) |
| P3-4.6 | Local curriculum framework alignment (PAUD Indonesia, etc.) |

---

### Epic P3-5: Schema-Per-Tenant (Enterprise Isolation)

**Trigger:** Large franchise chains with strict data isolation requirements (e.g., Eurokids requiring each center's data to be physically isolated for compliance or legal reasons).

**User stories:**

| Story | As a… | I want to… | So that… |
|-------|--------|------------|----------|
| P3-5.1 | Franchise chain legal team | Each center's data in a separate Postgres schema | A data breach at one center cannot expose others |
| P3-5.2 | System | Run migrations across N schemas automatically | Adding a new feature doesn't require N manual migrations |
| P3-5.3 | System | Provision a new schema when a center is onboarded | New centers are isolated from day one |

**Note:** Row-level tenancy (Phase 1 model) is sufficient for 99% of customers. This epic exists only for franchise chains with specific compliance mandates. Do not build prematurely.

---

## 10. Success Metrics

This section formalises the **System Definition metrics** (North Star + supporting metrics) and ties them directly to feature levers and the System Trigger Engine.

### 10.1 Phase 1 Launch Criteria (Month 10)

These are the pass/fail criteria that define a successful Phase 1 launch. All must be true before the product is considered launched.

| Criterion | Target | How Measured | Primary Levers |
|---|---|---|---|
| Pilot school chain fully live | 1 chain, 5+ centers, daily active teachers and parents | Admin dashboard — classes with ≥1 post/day for 2 consecutive weeks | Onboarding flow (Epics 1–2), A-1 dashboard, support playbook |
| **North Star: parent daily visibility** | ≥60% of enrolled parents see ≥1 post per day for trailing 14 days (pilot) | Event tracking: per-parent daily views on P-3/PW-2; cross-checked with engagement snapshots | Teacher posting cadence (T-1/TW-2), Parent notifications, Trigger Engine §2 (Parent Engagement) |
| Parent feed adoption | ≥70% of enrolled parents active in last 7 days | Engagement score ≥70% on pilot school for 2 consecutive weeks | Magic-link onboarding (P-0/P-1), app install funnel, weekly digest trigger |
| Teacher posting cadence | ≥3 posts per class per day | `posts` table — average posts/class/day over trailing 14 days | T-1/T-2 UX, Teacher nudges (Trigger Engine §1), admin coaching via A-1 |
| Self-serve onboarding live | A new school can sign up and invite teachers without founder involvement | End-to-end test: new school completes onboarding in < 15 minutes with no support contact | Epics 1–2 flows, error handling, docs |
| Manual invoicing live | At least 3 schools using fee management for monthly invoices | Fee invoices created and marked paid for at least 1 billing cycle | A-4/A-9 UX, soft fee reminders (Trigger Engine §4) |
| Teacher NPS | ≥30 | In-app NPS survey sent to teachers at Month 10 | Overall UX quality, posting friction, reliability |

### 10.2 System Metrics (aligned with System Definition)

These mirror the **System Definition** section and should be tracked weekly for the pilot and monthly across all schools.

| Metric (from System Definition) | Definition | Trigger / Feature Levers |
|---|---|---|
| **North Star: % of parents who see ≥1 meaningful update/day** | Parents with ≥1 post view per day ÷ total enrolled parents, measured over trailing 14 days | Posting UX (T-1/T-2/TW-2), New post notifications & reminders (Trigger Engine §2), Feed relevance & performance |
| Daily teacher posting rate | Average posts per class per day over trailing 7/14 days | Teacher nudges (Trigger Engine §1), emotional reinforcement on T-1/TW-2, admin coaching via A-1 |
| Parent weekly active rate (WAU) | Parents with ≥1 app or web session and ≥1 view in last 7 days ÷ total enrolled parents | New post notifications, reminder notifications (Trigger Engine §2), Weekly summary/digest, Daily Report visibility (P-3) |
| Avg posts per class per week | Total posts per class per week (7-day) | Same as posting rate; also influenced by AI captioning/child tagging friction |
| % children with milestone coverage | Children with ≥N milestones logged in the term ÷ total children | AI milestone suggestions from posts (Cross-Feature: Milestones), T-6/TW-6 UX, admin prompts in A-11 |
| Parent engagement (views / reactions) | Avg views, reactions, comments per post (segmented by class/school) | Copy/visuals on P-3/P-4/PW-2/PW-3, notification tuning, incident/daily report surfacing, growth prompts |

**Metric → Screen/Epic Map (for ownership)**

| Metric | Primary Screens / Surfaces | Primary Epics |
|---|---|---|
| **North Star: parent daily visibility** | P-3 Parent Feed (mobile), P-4 Child Timeline, PW-2 Parent Feed (web), TW-2 Teacher Feed (web) | Epic 3 – Teacher Posting Loop, Epic 4 – Parent Feed & Engagement |
| Daily teacher posting rate | T-1 Teacher Home & Feed, T-2 Create Post, TW-2 Teacher Feed (web), A-1 Admin Dashboard (posting tile) | Epic 3 – Teacher Posting Loop, Epic 7 – Admin Dashboard |
| Parent weekly active rate (WAU) | P-3/PW-2 feeds, notifications entry points, login/onboarding screens | Epic 4 – Parent Feed & Engagement, Epic 9 – Parent Engagement System |
| % children with milestone coverage | T-6/TW-6 Milestone entry, P-6/PW-6 Milestone views, A-11 Child Records | Epic 5 – Portfolios & Milestones, Epic 15 – Child Records & Compliance |
| Parent engagement (views / reactions) | P-3/PW-2 feed cards, P-4 Child Timeline, reaction/comment components | Epic 4 – Parent Feed & Engagement, Epic 9 – Parent Engagement System |

Engineering and product should maintain a simple dashboard where each of these metrics appears alongside the **linked triggers** so changes to the Trigger Engine can be seen in the data.

### 10.3 Engagement Score Definition

School-level engagement score = (parents who viewed ≥1 post in the trailing 7 days ÷ total enrolled parents) × 100

- Stored as a weekly snapshot in `engagement_snapshots`. Not recalculated on read.
- Directly related to the **North Star** but on a 7-day horizon instead of daily.
- The formula and its inputs must be shared with the pilot school owner before launch so they understand what they are looking at.

### 10.4 3-Month Pilot Milestones

| Milestone | Target |
|---|---|
| Pilot school live | 1 school, 5+ centers |
| Teacher posting | ≥3 posts/class/day |
| Parent app adoption | ≥70% of enrolled parents active |
| Principal dashboard weekly use | Principal views dashboard ≥3 times/week |

### 10.5 6-Month Growth Milestones

| Milestone | Minimum | Stretch |
|---|---|---|
| Paying preschool chains | 3 chains (15+ centers) | 10 chains (50+ centers) |
| Teacher NPS | ≥30 | ≥50 |
| Parent activity definition | Opened app + viewed ≥1 post in last 7 days | — |
| Pipeline | At least 1 franchise chain in sales pipeline | — |

### 10.6 12-Month ARR Target

- 50 paying chains → ₹50L+ ARR
- Pricing at Month 12: ₹40-60/child/month (up from ₹20-30 at launch)
- Condition for price increase: 10+ paying schools live AND teacher NPS ≥ 30
- Illumine customer win: at least 1 school that switched from Illumine (moat validation)

### 10.7 Leading Indicators (Weekly Tracking)

These should be monitored weekly from Day 1 of the pilot, not just at month-end reviews:

| Indicator | Healthy Signal | Warning Signal |
|---|---|---|
| Posts per class per day (Teacher posting rate) | ≥3 | < 1 for 3 consecutive days |
| Parent feed open rate (toward North Star) | ≥60% of enrolled parents daily | < 30% 7-day active |
| WhatsApp switching rate | > 50% of notified parents opening app vs. staying on WhatsApp link | < 30% (see CEO Plan risk #1) |
| AI caption acceptance rate | > 60% of captions posted without teacher edit | < 30% (indicates AI quality issue) |
| Magic-link to app install conversion | ≥30% of magic-link users install the app within 7 days | < 15% (reconsider install nudge UX) |
| Face recognition accuracy | < 5% false positive rate on confirmed tags | > 10% (impacts teacher trust) |
| Daily summary usage rate | ≥60% of active parents view or scroll past the daily summary card at least 5 days/week | < 30% of active parents see the daily summary card (summary not adding value) |
| Messaging usage rate | ≥40% of active classes have at least 1 parent–teacher message or announcement per week | < 20% of classes using in-app messaging or announcements (communication staying on WhatsApp) |
| Teacher nudge effectiveness (Trigger Engine §1) | ≥40% of teachers who receive a "post today" nudge create at least 1 post that day | < 20% of nudged teachers posting (nudges not effective or poorly timed; revisit triggers/copy) |
| Post share rate | ≥10% of posts are shared externally at least once per week | < 3% of posts shared externally (growth hooks underused) |
| Referral-tagged admissions share | ≥30% of new admissions have a referral source or tagged referrer recorded | < 10% of admissions with referral source captured (growth loop not closing) |

---

## Appendix: Pre-Build Blockers

The following items from TODOS.md must be resolved before build begins. They are recorded here for product accountability.

| Blocker | Owner | Deadline | Status |
|---|---|---|---|
| DPDP Act legal review assigned and initiated | Founder | End of Month 2 | Open |
| NEP 2020 milestone taxonomy defined (~80 indicators, 5 domains) | Product Lead | Before Month 3 AI work | Open |
| AI pair programming pilot (React web feed prototype) shipped to pilot school | Founder/PM | Week 3-4 of Month 1 | Open |
| Pricing hypothesis validated with first 3 paying customers | Founder | Before Month 2 Razorpay scope decision | Open |
| Pilot school confirmed and start date set | Founder | Month 1 | Secured |

---

*This PRD covers Phase 1 (Sections 1–7, 10), Phase 2 (Section 8), and Phase 3 (Section 9). Phase 2 and Phase 3 epics are intentionally high-level — they will be detailed at the start of each phase based on Phase 1 learnings.*
