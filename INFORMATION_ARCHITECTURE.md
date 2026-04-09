# CadenceSprout — Information Architecture & System Overview

**Document Version:** 1.0  
**Last Updated:** April 7, 2026  
**Purpose:** Complete information architecture for CadenceSprout Phase 1, organized by persona capability, system flows, and screen hierarchy.

---

## Table of Contents

1. [System Overview](#system-overview)
2. [Core System Loops](#core-system-loops)
3. [Persona Capability Matrix](#persona-capability-matrix)
4. [Platform & Device Architecture](#platform--device-architecture)
5. [Screen Hierarchy by Persona](#screen-hierarchy-by-persona)
6. [Feature Organization & Priority](#feature-organization--priority)
7. [Data Model & Relationships](#data-model--relationships)
8. [Navigation Flows](#navigation-flows)
9. [System Constraints & Rules](#system-constraints--rules)
10. [Appendix: Screen Inventory](#appendix-screen-inventory)

---

## 1. System Overview

### 1.1 Product Definition

CadenceSprout is an **AI-native, all-in-one preschool operating system** for Indian standalone preschool chains. It combines:

1. **Engagement Layer** (primary) — AI-powered posts, parent feed, milestones, and portfolio
2. **Operations Layer** — Fees, admissions, attendance, staff management
3. **Compliance Layer** — Child records, medical information, incidents, permissions

### 1.2 North Star Metric

**% of parents who see at least 1 meaningful update about their child per day**

All product decisions, features, and trade-offs are calibrated to this metric.

### 1.3 System Principles (Non-Negotiable)

| Principle | Rule |
|-----------|------|
| **Engagement-first, ERP-second** | Teacher and parent feeds remain primary surfaces; ERP features are contextual, lightweight flows |
| **Nothing blocks posting** | No compliance, form, or configuration screen prevents teachers from posting simple updates |
| **Everything connects to feed** | Posts, milestones, attendance, incidents, daily reports all flow into the child narrative |
| **AI assists, never interrupts** | AI suggestions (captions, child tags, milestones) reduce friction; always optional |
| **Compliance is visible, not dominant** | Privacy and records are clearly labelled and accessible; never interrupt emotional storytelling |

---

## 2. Core System Loops

### 2.1 Teacher Loop

```
Capture moment 
  ↓
AI assists (caption + child tagging)
  ↓
Post to parent feed
  ↓
Parent reacts / comments
  ↓
Teacher feels validated + sees parent engagement
  ↓
Repeat (next post)
```

**Key entry point:** Teacher Feed (T-1)  
**Engagement trigger:** Nudge if no post by 12 PM  
**Success signal:** ≥3 posts per class per day

### 2.2 Parent Loop

```
Receive notification
  ↓
Tap magic-link / open app
  ↓
View child update (warm, captioned photo)
  ↓
React / comment / feel emotionally connected
  ↓
Return to check for updates daily
```

**Key entry point:** Parent Feed (P-3)  
**Conversion moment:** First warm photo with caption  
**Success signal:** 70%+ parent launch rate from magic-link

### 2.3 Admin Loop

```
Check dashboard
  ↓
Detect exceptions (low engagement, unpaid fees, low attendance)
  ↓
Take action (message teacher, follow up parent, resolve incident)
  ↓
Check metrics improved week-over-week
  ↓
Repeat weekly
```

**Key entry point:** Admin Dashboard (A-1)  
**Exception signal:** Engagement score, attendance %  
**Success signal:** Admin can act on exceptions within 5 minutes

### 2.4 System-Level Loop

```
Capture → Post → Notify → View → Re-engage → Capture
```

This loop applies to the entire system. Every notification, nudge, and feature reinforces this cycle.

---

## 3. Persona Capability Matrix

### 3.1 Capability Definitions by Persona

#### 👩‍🏫 **Teacher (Sunita)** — Content Creation + Classroom Ops

| Capability | Description | Platform |
|------------|-------------|----------|
| **AI-Assisted Post Creation** | Compose photo/video + auto caption draft + child tagging | Mobile ✅ / Web ✅ |
| **Child Tracking** | Milestones, attendance, profiles | Mobile ✅ / Web ✅ |
| **Parent Engagement Insight** | See who viewed posts, reply to comments | Mobile ✅ / Web ✅ |
| **Class Management** | View roster, link parents, manage permissions | Mobile ✅ / Web ✅ |
| **AI Nudges** | Productivity reminders (no post yet today) | Mobile ✅ / Web ⚠️ |
| **Attendance** | Mark daily attendance for class (<60s) | Mobile ✅ / Web ✅ |
| **Incident Logging** | Log child incidents, notify parents | Mobile ✅ / Web ✅ |
| **Offline Posting** | Queue posts when offline, sync when online | Mobile ❌ (Phase 2) / Web ❌ |

---

#### 👶 **Parent (Meera)** — Engagement + Trust Layer

| Capability | Description | Platform |
|------------|-------------|----------|
| **Personalized Child Feed** | See photos, updates, milestones for their child only | Mobile ✅ / Web ✅ |
| **Reaction & Comment** | React to posts, reply to teacher messages | Mobile ✅ / Web ✅ |
| **Milestone Tracking** | View child's developmental progress across NEP 2020 milestones | Mobile ✅ / Web ✅ |
| **Year-End Portfolio** | Access downloadable memory book with all year's posts | Mobile ✅ / Web ✅ |
| **Parent Notifications** | Opt-in push, WhatsApp, email summaries | Mobile ✅ / Web ⚠️ |
| **Settings & Privacy** | Manage notifications, view/change permissions | Mobile ✅ / Web ✅ |
| **Fee History** | View invoices, payment history, due dates | Mobile ✅ / Web ✅ |
| **Incident History** | View logged incidents about their child | Mobile ✅ / Web ✅ |
| **Magic-Link Access** | Enter feed without full app install | Mobile ✅ (web) / Web ✅ |

---

#### 🎯 **Admin / Principal (Rajesh)** — Control Tower

| Capability | Description | Platform |
|------------|-------------|----------|
| **School Setup** | Register, configure branding, billing | Web ✅ / Mobile ❌ |
| **Class & Teacher Management** | Create classes, invite teachers, assign class assignments | Web ✅ / Mobile ❌ |
| **Child Enrollment** | Add children, link parents, manage profiles | Web ✅ / Mobile ⚠️ |
| **Engagement Monitoring** | Dashboard showing posts/day, parent engagement, posting trend | Web ✅ / Mobile ⚠️ |
| **Attendance Aggregate** | Dashboard: attendance % by class, trends | Web ✅ / Mobile ❌ |
| **Fee Management** | Create invoices, track payments, send reminders | Web ✅ / Mobile ❌ |
| **Admissions Pipeline** | Lead inquiries, convert to enrollment, track source | Web ✅ / Mobile ❌ |
| **Staff & Permissions** | Manage staff roles, access levels, class assignments | Web ✅ / Mobile ❌ |
| **Child Records & Compliance** | Access child medical info, incidents, permissions audit trail | Web ✅ / Mobile ❌ |
| **Incident Management** | View, resolve, follow up on logged incidents | Web ✅ / Mobile ⚠️ |
| **Alerts & Exceptions** | Smart alerts: low-engagement class, unpaid fees, incident escalation | Web ✅ / Mobile ❌ |

---

### 3.2 Platform Capability Summary

| **Feature Area** | **Teacher Mobile** | **Teacher Web** | **Parent Mobile** | **Parent Web** | **Admin Web** | **Required for MVP?** |
|---|:---:|:---:|:---:|:---:|:---:|---|
| **Authentication** | ✅ | ✅ | ✅ | ✅ | ✅ | MVP |
| **Post Creation** | ✅ | ✅ | ❌ | ❌ | ❌ | MVP (Mobile + Web) |
| **AI Captioning** | ✅ | ✅ | ❌ | ❌ | ❌ | MVP |
| **AI Child Tagging** | ✅ | ✅ | ❌ | ❌ | ❌ | MVP |
| **Parent Feed** | ❌ | ❌ | ✅ | ✅ | ❌ | MVP |
| **Teacher Feed** | ✅ | ✅ | ❌ | ❌ | ❌ | MVP |
| **Attendance** | ✅ | ✅ | ❌ | ❌ | ✅ | V1 |
| **Milestones** | ✅ | ✅ | ✅ | ✅ | ✅ | V1 |
| **Incidents** | ✅ | ✅ | ✅ | ✅ | ✅ | V1 |
| **Fees** | ❌ | ❌ | ✅ | ✅ | ✅ | V1 |
| **Admin Dashboard** | ❌ | ❌ | ❌ | ❌ | ✅ | MVP/V1 |
| **Search** | ❌ | ❌ | ❌ | ❌ | ❌ | Phase 2 |
| **Offline** | ❌ | ❌ | ❌ | ❌ | ❌ | Phase 2 |

---

## 4. Platform & Device Architecture

### 4.1 Platform Stack

```
┌─────────────────────────────────────────────────────────┐
│                    CLIENT LAYER                          │
├─────────────────┬──────────────────┬──────────────────┤
│ Teacher App     │ Parent App       │ Admin Dashboard  │
│ (React Native)  │ (React Native)   │ (React + Vite)   │
│ iOS + Android   │ iOS + Android    │ Web Browser      │
└────────┬────────┴────────┬─────────┴────────┬────────┘
         │                 │                  │
         └─────────────────┼──────────────────┘
                           │
                ┌──────────▼──────────┐
                │   API GATEWAY       │
                │   (Node.js / Express) │
                └──────────┬──────────┘
                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
    ┌───▼────┐    ┌───────▼──────┐   ┌──────▼────┐
    │ Auth   │    │ Core Backend  │   │  AI Layer │
    │Service │    │ (Laravel)     │   │(OpenRouter)│
    └────────┘    │ PostgreSQL    │   │AWS Rekog  │
                  │ Row-Level SEC │   └───────────┘
                  └───────────────┘
                        │
    ┌───────────────────┼─────────────────┐
    │                   │                 │
┌──▼────┐        ┌──────▼────┐     ┌─────▼──┐
│  S3   │        │  Wapi     │     │ Twilio │
│(Media)│        │(WhatsApp) │     │ (SMS)  │
└───────┘        └───────────┘     └────────┘
```

### 4.2 Device Primary Use Cases

| Platform | Primary Use | Secondary Use | Design Pattern |
|----------|------------|---------------|-----------------|
| **Teacher Mobile** | Capture moment, post, mark attendance | Check notifications, reply comments | Action-first, stream-based |
| **Teacher Web** | Dashboard, bulk operations, detailed editing | Same as mobile | Content-first, table-based |
| **Parent Mobile** | Check feed, see updates, react | Manage settings, view portfolio | Story-based, notification-driven |
| **Parent Web** | Browse feed, manage, download portfolio | Secondary checking | Feed-based, grid-based |
| **Admin Web** | Monitor metrics, take action, configure | Review details, bulk import | Dashboard-first, detail-drawer |

---

## 5. Screen Hierarchy by Persona

### 5.1 Teacher Navigation Hierarchy

#### Mobile (React Native)

```
Teacher App (Root)
│
├─ On-Boarding
│  ├─ T-0: Splash / Login Redirect
│  ├─ T-0A: Phone + Password Login
│  └─ T-0B: First-Time Setup Wizard
│
├─ Primary Flows (Bottom Tab Navigation)
│  ├─ HOME Tab (T-1: Teacher Feed)
│  │  ├─ T-1: My Class Feed (default view)
│  │  ├─ T-1A: Nudge Banner (if no post)
│  │  ├─ Post Detail → Comments/Reactions
│  │  ├─ Swipe Action → Mark Attendance
│  │  └─ [+] Button → Composer
│  │
│  ├─ COMPOSE Tab (T-2: Composer)
│  │  ├─ T-2: Composer (photo/video, caption, child tags, milestones)
│  │  ├─ T-2A: AI Caption Loading
│  │  ├─ T-2B: Child Picker Modal
│  │  ├─ T-2C: Milestone Picker Modal
│  │  ├─ T-2D: Incident Inline Reporter
│  │  └─ [POST] → Submit / Queue if offline
│  │
│  ├─ ROSTER Tab (T-5: Class Roster)
│  │  ├─ T-5: List of children + attendance status
│  │  ├─ T-5A: Child Detail (name, parent, milestones, profile photo)
│  │  ├─ T-5B: Attendance Quick-Mark Modal
│  │  ├─ T-5C: Milestone Progress View
│  │  ├─ T-5D: Incident History
│  │  └─ [Link Parent] → Invitation flow
│  │
│  ├─ DAILY REPORT Tab (T-8: Optional)
│  │  ├─ T-8: Quick daily summary form (class mood, learning areas, notes)
│  │  └─ [SAVE] → Share with parents or keep private
│  │
│  └─ MENU Tab (Settings)
│     ├─ T-10: Profile & Settings
│     ├─ T-10A: Class & Roster Management
│     ├─ T-10B: Notification Settings
│     ├─ T-10C: Offline Status
│     └─ T-10D: Logout
│
└─ Secondary / Detail Screens
   ├─ T-3: Milestones Tracker (scrollable view by child or by skill)
   ├─ T-4: Attendance History (view past attendance)
   ├─ T-6: Child Profile deep-dive
   ├─ T-7: Incident Detail & Follow-up
   └─ T-11: Messages / Parent Conversations
```

#### Web (React + Vite)

```
Teacher Web (Root)
│
├─ On-Boarding
│  ├─ TW-0: Splash / Login page
│  └─ TW-0A: Phone/Email + Password login
│
├─ Dashboard Layout (Sidebar + Main)
│  │
│  ├─ Navigation Sidebar
│  │  ├─ School logo / Name
│  │  ├─ Class selector dropdown
│  │  ├─ Home (TW-1)
│  │  ├─ Composer (TW-2)
│  │  ├─ Feed (TW-3)
│  │  ├─ Roster (TW-5)
│  │  ├─ Attendance (TW-4)
│  │  ├─ Milestones (TW-6)
│  │  ├─ Daily Report (TW-8)
│  │  └─ Settings (TW-10)
│  │
│  ├─ Main Content Area
│  │  │
│  │  ├─ TW-1: Home / Dashboard
│  │  │  ├─ Class performance summary
│  │  │  ├─ Today's posts status
│  │  │  ├─ Action items (if any)
│  │  │  └─ Quick stats (parent engagement, attendance)
│  │  │
│  │  ├─ TW-2: Composer
│  │  │  ├─ Drag-drop media upload
│  │  │  ├─ Caption editor (with AI draft)
│  │  │  ├─ Child multi-select checkboxes
│  │  │  ├─ Milestone tagging
│  │  │  ├─ Incident inline form
│  │  │  └─ [POST] → Preview & submit
│  │  │
│  │  ├─ TW-3: Feed (2-column layout)
│  │  │  ├─ Left column: Today's posts
│  │  │  ├─ Right column: Parent comments, reactions
│  │  │  └─ Scroll to see older posts
│  │  │
│  │  ├─ TW-4: Attendance Table
│  │  │  ├─ Grid: child rows × date columns
│  │  │  ├─ Checkbox marking
│  │  │  ├─ Bulk import option
│  │  │  ├─ Summary: attendance %
│  │  │  └─ [SAVE] → Submit for day
│  │  │
│  │  ├─ TW-5: Roster Table
│  │  │  ├─ Columns: name, DOB, parent, attendance %, recent posts
│  │  │  ├─ Click row → Child detail drawer
│  │  │  ├─ [Invite Parent] → Flow
│  │  │  └─ [Manage] → Linked parents, permissions
│  │  │
│  │  ├─ TW-6: Milestones
│  │  │  ├─ View by child (list of milestones achieved)
│  │  │  ├─ View by domain (NEP 2020 domains, coverage %)
│  │  │  ├─ AI suggestions pane (inferred from posts)
│  │  │  └─ Tag milestones → Auto-link to child
│  │  │
│  │  ├─ TW-8: Daily Report
│  │  │  ├─ Structured form: class mood, learning areas, highlights
│  │  │  ├─ Pull from today's posts
│  │  │  └─ [SAVE & SHARE]
│  │  │
│  │  └─ TW-10: Settings
│  │     ├─ Profile: name, phone, role
│  │     ├─ Class assignment
│  │     ├─ Notification preferences
│  │     ├─ Privacy settings
│  │     └─ [Logout]
│  │
│  └─ Detail Drawers / Modals (appear on right)
│     ├─ Child Detail panel
│     ├─ Post detail & comments
│     ├─ Incident form
│     └─ Milestone suggestion panel
│
└─ Hidden / Less Frequent
   ├─ TW-7: Help & Documentation
   └─ TW-11: Sync Status
```

---

### 5.2 Parent Navigation Hierarchy

#### Mobile (React Native)

```
Parent App (Root)
│
├─ On-Boarding
│  ├─ P-0: Splash / Magic-Link Entry
│  ├─ P-0A: OTP Verification (if first time)
│  ├─ P-0B: Name + Create Passcode
│  └─ P-0C: Notification Permission Prompt
│
├─ Primary Tab Navigation
│  │
│  ├─ FEED Tab (P-3: Parent Feed — PRIMARY)
│  │  ├─ P-3: Scrollable feed of child's posts (reverse cronological)
│  │  │  ├─ Post card: photo, caption, timestamp, teacher name
│  │  │  ├─ [React] → reaction picker (emoji)
│  │  │  ├─ [Comment] → inline comment form
│  │  │  └─ Share / Save to portfolio
│  │  ├─ P-4: Post Detail / Comments View
│  │  └─ P-4A: Teacher Reply (if teacher responds to comment)
│  │
│  ├─ PORTFOLIO Tab (P-5 / P-6: Milestones & Memory)
│  │  ├─ P-5: Milestone Progress
│  │  │  ├─ View by domain (NEP 2020 areas)
│  │  │  ├─ Progress bar: milestones achieved / total
│  │  │  ├─ Achievement badge view
│  │  │  └─ Linked posts showing evidence
│  │  │
│  │  └─ P-6: Portfolio (Year-end memory book)
│  │     ├─ Curated posts from the year
│  │     ├─ [Download] as PDF
│  │     ├─ [Share] with family
│  │     └─ [Print] option
│  │
│  ├─ ACTIVITY Tab (P-7: Notifications & Messages)
│  │  ├─ P-7: In-app notification list
│  │  │  ├─ New post alerts
│  │  │  ├─ Comment replies (from teacher)
│  │  │  ├─ Incident notifications
│  │  │  └─ System messages (fees due, etc.)
│  │  │
│  │  └─ P-7A: Message Thread (if teacher → parent messaging available)
│  │
│  ├─ RECORDS Tab (P-8 / P-11: Health, Incidents, Fees)
│  │  ├─ P-8: Child Health & Medical Info (read-only)
│  │  │  ├─ Medical conditions, allergies
│  │  │  ├─ Emergency contacts
│  │  │  └─ [Edit] → Editable by parent, authorized by admin
│  │  │
│  │  ├─ P-9: Fees & Payment History
│  │  │  ├─ Current outstanding balance
│  │  │  ├─ Invoice list
│  │  │  ├─ [Pay Now] → Razorpay flow (Phase 2)
│  │  │  └─ Payment history
│  │  │
│  │  └─ P-11: Incident History
│  │     ├─ Logged incidents about child
│  │     ├─ Severity badge + resolved status
│  │     └─ Follow-up notes
│  │
│  └─ MENU Tab (Settings & Profile)
│     ├─ P-12: Profile & Settings
│     │  ├─ Child profile (name, school, class, teacher)
│     │  ├─ Parent name + contact
│     │  ├─ Linked parents (if siblings enrolled)
│     │  └─ [Manage Linked Accounts]
│     │
│     ├─ P-13: Notification Preferences
│     │  ├─ Push notification opt-in
│     │  ├─ WhatsApp opt-in
│     │  ├─ Email opt-in
│     │  ├─ Notification frequency
│     │  └─ Do Not Disturb window
│     │
│     ├─ P-14: Privacy & Permissions
│     │  ├─ View which data is shared
│     │  ├─ Manage photo consent (for face recognition)
│     │  ├─ Download my data (DPDP)
│     │  ├─ Delete account
│     │  └─ Privacy policy / FAQs
│     │
│     └─ T-15: Logout / Switch Account
│
└─ Secondary Screens
   ├─ P-16: Child Profile (view-only)
   ├─ P-17: Class & Schedule Info
   ├─ P-18: Contact Teacher (if messaging available)
   └─ P-19: Help & FAQ
```

#### Web (React + Vite)

```
Parent Web (Root)
│
├─ On-Boarding
│  ├─ PW-0: Magic-link landing page
│  ├─ PW-0A: OTP verification
│  ├─ PW-0B: Registration form (name, email, password setup)
│  └─ PW-0C: Notification preferences
│
├─ Dashboard Layout (Sidebar + Main)
│  │
│  ├─ Navigation Sidebar
│  │  ├─ School logo
│  │  ├─ Child name / photo
│  │  ├─ Feed (PW-2 / PW-3)
│  │  ├─ Milestones & Portfolio (PW-4)
│  │  ├─ Records & Docs (PW-5)
│  │  ├─ Messages (PW-6)
│  │  ├─ Settings (PW-7)
│  │  └─ [Logout]
│  │
│  ├─ Main Content Area
│  │  │
│  │  ├─ PW-2: Feed Home (with search/filter)
│  │  │  ├─ Timeline view: posts reverse-chronological
│  │  │  ├─ Post cards (larger than mobile)
│  │  │  ├─ Reaction quick-access
│  │  │  ├─ Comment thread inline or expanded
│  │  │  └─ Sidebar: stats (posts/week, milestones achieved, etc.)
│  │  │
│  │  ├─ PW-3: Post Detail Page
│  │  │  ├─ Full-screen post with larger photo
│  │  │  ├─ Caption + metadata (teacher, date, class)
│  │  │  ├─ Reactions section
│  │  │  ├─ Comments thread (nested)
│  │  │  ├─ [Reply] → inline form
│  │  │  └─ [Save to Portfolio] button
│  │  │
│  │  ├─ PW-4: Portfolio & Milestones
│  │  │  ├─ Tab 1: Milestones (domain views, progress bars)
│  │  │  ├─ Tab 2: Memory Book
│  │  │  │  ├─ Curated posts grid
│  │  │  │  ├─ [Download as PDF]
│  │  │  │  ├─ [Share Link] (for family)
│  │  │  │  └─ [Print]
│  │  │  └─ Tab 3: Achievements (badges, certificates)
│  │  │
│  │  ├─ PW-5: Child Records & Docs
│  │  │  ├─ Section 1: Medical & Health
│  │  │  ├─ Section 2: Incidents (with severity)
│  │  │  ├─ Section 3: Fee History & Payments
│  │  │  └─ Section 4: Permissions & Consent
│  │  │
│  │  ├─ PW-6: Messages (if applicable)
│  │  │  ├─ Teacher conversation list
│  │  │  ├─ Message thread
│  │  │  └─ [Send] form
│  │  │
│  │  └─ PW-7: Settings & Profile
│  │     ├─ Child & Parent Info
│  │     ├─ Notification Settings
│  │     ├─ Privacy & Consent
│  │     ├─ Help Links
│  │     └─ [Logout]
│  │
│  └─ Right Sidebar (on desktop) / Drawers
│     ├─ Quick stats (posts/week)
│     ├─ Today's highlights
│     └─ Upcoming due dates (fees, etc.)
│
└─ Secondary Pages
   ├─ PW-8: Search (cross posts, milestones)
   ├─ PW-9: Notifications Center (popup)
   └─ PW-10: Privacy & Help
```

---

### 5.3 Admin Navigation Hierarchy

#### Web Only (React + Vite — No Mobile in MVP/V1)

```
Admin Dashboard (Root)
│
├─ On-Boarding / Authentication
│  ├─ Admin-0: Login page
│  ├─ Admin-0A: Phone + Password login
│  ├─ Admin-0B: School registration flow
│  ├─ Admin-0C: School profile setup
│  └─ Admin-0D: Initial class + teacher setup
│
├─ Main Dashboard Layout (Sidebar + Main)
│  │
│  ├─ Left Sidebar Navigation
│  │  ├─ School selector (if managing multiple centers)
│  │  ├─ School logo + name
│  │  ├─ Home / Dashboard (A-1)
│  │  ├─ Engagement (A-2)
│  │  ├─ Operations
│  │  │  ├─ Admissions (A-3)
│  │  │  ├─ Fees (A-4, A-9)
│  │  │  ├─ Attendance (A-5)
│  │  │  └─ Staff & Roles (A-6, A-12)
│  │  ├─ Compliance
│  │  │  ├─ Child Records (A-11)
│  │  │  └─ Incidents (A-13)
│  │  ├─ Settings
│  │  │  ├─ School Profile
│  │  │  ├─ Users & Permissions
│  │  │  ├─ Integrations
│  │  │  └─ Billing & Plan
│  │  └─ [Logout]
│  │
│  ├─ Main Content Area
│  │
│  ├─ A-1: Dashboard Home (Control Tower)
│  │  ├─ Key Metrics Summary
│  │  │  ├─ This week's engagement score (with trend)
│  │  │  ├─ Posts/class/day (with target)
│  │  │  ├─ Parent launch rate (from magic-links)
│  │  │  ├─ Attendance % (overall + by class)
│  │  │  ├─ Fee collection % + outstanding
│  │  │  └─ Incident count + severity
│  │  │
│  │  ├─ Alerts & Exceptions (High Priority)
│  │  │  ├─ Classes below posting threshold
│  │  │  ├─ Unpaid invoices
│  │  │  ├─ Low attendance flags
│  │  │  ├─ High-severity incidents
│  │  │  └─ Teachers without recent activity
│  │  │
│  │  ├─ Quick Actions
│  │  │  ├─ [Invite Teacher]
│  │  │  ├─ [Add Class]
│  │  │  ├─ [Message Low-Engagement Teacher]
│  │  │  └─ [View Today's Posts Across All Classes]
│  │  │
│  │  └─ Week-over-week trend chart
│  │
│  ├─ A-2: Engagement Dashboard
│  │  ├─ Posts per day (graph over last 30 days)
│  │  ├─ By class: engagement breakdown
│  │  ├─ Parent engagement (comments + reactions)
│  │  ├─ Parent launch rate (from magic-link invites)
│  │  ├─ Most engaged class drill-down
│  │  ├─ At-risk classes (low posting) + [Message Teacher]
│  │  └─ [Export Report]
│  │
│  ├─ A-3: Admissions Pipeline
│  │  ├─ Lead list with status (inquiry → enrolled)
│  │  │  ├─ Lead source tracking
│  │  │  ├─ Inquiry date + follow-up history
│  │  │  ├─ [Add Inquiry] form
│  │  │  ├─ [Move to Next Stage] button per inquiry
│  │  │  └─ [Enroll] → creates child profile
│  │  │
│  │  ├─ Conversion funnel chart
│  │  ├─ [Bulk Invite] → add multiple children + parents
│  │  └─ Export lead list
│  │
│  ├─ A-4 / A-9: Fees & Billing
│  │  ├─ Invoice Management
│  │  │  ├─ Create invoice (amount, child, due date)
│  │  │  ├─ Invoice list: due, paid, overdue
│  │  │  ├─ [Send Reminder] → to parent (WhatsApp / SMS)
│  │  │  ├─ [Mark Paid] (manual entry, Phase 2 = auto via Razorpay)
│  │  │  └─ [Download PDF] receipt
│  │  │
│  │  ├─ Fee Overview
│  │  │  ├─ Total outstanding
│  │  │  ├─ Collection % this month
│  │  │  ├─ Aging report (0-30, 30-60, 60+ days overdue)
│  │  │  └─ [Settings] → annual fee, payment schedule
│  │  │
│  │  └─ Payment history (all receipts)
│  │
│  ├─ A-5: Attendance Dashboard
│  │  ├─ Aggregate view
│  │  │  ├─ School attendance % (today, this week, this month)
│  │  │  ├─ By class: attendance breakdown
│  │  │  ├─ Trend chart (14-day rolling)
│  │  │  └─ Alert if below threshold
│  │  │
│  │  ├─ Detail by class
│  │  │  ├─ Date selector
│  │  │  ├─ Grid: children × date
│  │  │  ├─ Marked /unmarked / absent
│  │  │  ├─ [Bulk Mark] option
│  │  │  └─ [Export] CSV
│  │  │
│  │  └─ Per-child view
│  │     └─ Attendance history for individual child
│  │
│  ├─ A-6 / A-12: Staff & Roles
│  │  ├─ Staff List
│  │  │  ├─ Name, role (Teacher / Admin), class, phone
│  │  │  ├─ Last active timestamp
│  │  │  ├─ [Invite New Staff] → SMS invite with setup link
│  │  │  ├─ [Edit] → update role, class assignment
│  │  │  └─ [Remove] → revoke access
│  │  │
│  │  ├─ Roles & Permissions
│  │  │  ├─ Predefined roles (Teacher, Admin, Principal)
│  │  │  ├─ Custom role creation (Phase 2)
│  │  │  └─ Permission matrix view
│  │  │
│  │  └─ Activity log
│  │     └─ Who logged in, what actions taken (Phase 2)
│  │
│  ├─ A-11: Child Records & Compliance
│  │  ├─ Child Master List
│  │  │  ├─ Columns: name, DOB, enrollment date, class, photo
│  │  │  ├─ [Search] by name
│  │  │  ├─ [Bulk Import] from CSV
│  │  │  └─ [Add Child] form
│  │  │
│  │  ├─ Child Detail View
│  │  │  ├─ Basic info (name, DOB, class, parents, photo)
│  │  │  ├─ Medical/Health info (readlnronly view, editable by parent)
│  │  │  ├─ Allergies, medical conditions, emergency contacts
│  │  │  ├─ Incidents tied to child (read-only)
│  │  │  ├─ Permissions & consent (photo usage, DPDP opt-in)
│  │  │  └─ [Print Child Record] for file
│  │  │
│  │  └─ Linked Parents
│  │     ├─ View linked parents for each child
│  │     ├─ [Link New Parent] → add another phone / email
│  │     └─ [Unlink] → remove access
│  │
│  ├─ A-13: Incident Management
│  │  ├─ Incident List
│  │  │  ├─ Type, severity, child(ren), date, status
│  │  │  ├─ Filter by: severity, type, class, unresolved
│  │  │  ├─ [View] → detail modal
│  │  │  └─ [Mark Resolved]
│  │  │
│  │  ├─ Incident Detail
│  │  │  ├─ Logged incident info
│  │  │  ├─ Parent notification status (sent, pending, opted-out)
│  │  │  ├─ Follow-up notes
│  │  │  ├─ [Add Follow-up Note]
│  │  │  └─ [Resend Notification to Parent] (if not sent)
│  │  │
│  │  └─ Incidents by Class
│  │     └─ Class-level incident trend
│  │
│  ├─ School Settings
│  │  ├─ School Info
│  │  │  ├─ School name, address, phone
│  │  │  ├─ Logo / Branding (displayed in parent app)
│  │  │  └─ Time zone
│  │  │
│  │  ├─ Classes Setup
│  │  │  ├─ Class list with assigned teachers
│  │  │  ├─ [Create Class]
│  │  │  ├─ [Edit] class details
│  │  │  └─ [Archive] class
│  │  │
│  │  ├─ Users & Access Control
│  │  │  ├─ Admin user list
│  │  │  ├─ Invite new admin
│  │  │  └─ Permission matrix
│  │  │
│  │  ├─ Integrations & Webhooks
│  │  │  ├─ WhatsApp config
│  │  │  ├─ SMS provider config (Phase 2)
│  │  │  └─ Future integrations
│  │  │
│  │  └─ Billing & Plan
│  │     ├─ Current subscription
│  │     ├─ Seats used / available
│  │     ├─ [Upgrade Plan]
│  │     └─ Payment method & history
│  │
│  └─ Hidden / Advanced
│     ├─ A-7: Admissions Lead Management
│     ├─ A-8: Fee Settings & Schedule
│     └─ A-10: Bulk Data Operations
│
└─ Right Sidebar (Desktop) / Drawers
   ├─ Quick alerts panel
   ├─ Quick actions
   └─ Help & documentation
```

---

## 6. Feature Organization & Priority

### 6.1 Priorty Tiers (System-Level)

| Tier | Feature | Rule | Owner | Target |
|------|---------|------|-------|--------|
| 🔥 **P0** | Posting + Feed | Must be fastest, never blocked | Teacher + Parent | MVP |
| 🔥 **P0** | Parent visibility | Every post must reach parents | System | MVP |
| 🟡 **P1** | Milestones | Passive + AI-assisted | Teacher + Parent | V1 |
| 🟡 **P1** | Attendance | Daily habit, <60s | Teacher + Admin | V1 |
| 🟢 **P2** | Daily report | Optional, never interrupt flow | Teacher | V1 |
| 🟢 **P2** | Fees | Calm, parent-first | Admin + Parent | V1 |
| ⚪ **P3** | Admin dashboards | Insight, not primary UX | Admin | V1 |

### 6.2 Feature Groups by Layer

#### **Engagement Layer (P0 / P1)**

| Feature | MVP | V1 | Phase 2 |
|---------|-----|----|----|
| Teacher Post Creation (photo + caption + tags) | ✅ | ✅ | ✅ |
| AI Captioning | ✅ | ✅ | ✅ |
| AI Child Face Detection | ✅ | ✅ | ✅ |
| Parent Feed | ✅ | ✅ | ✅ |
| Reactions & Comments | ✅ | ✅ | ✅ |
| Teacher nudge engine | ✅ | ✅ | ✅ |
| Notifications (WhatsApp + Push) | ✅ | ✅ | ✅ |
| Milestones Tracking (NEP 2020) | ❌ | ✅ | ✅ |
| AI Milestone Suggestions | ❌ | ✅ | ✅ |
| Year-End Portfolio (PDF) | ❌ | ✅ | ⚠️ (Enhanced) |
| Offline Posting (queue + sync) | ❌ | ❌ | ✅ |
| Search Posts | ❌ | ❌ | ✅ |

#### **Operations Layer (P1 / P2)**

| Feature | MVP | V1 | Phase 2 |
|---------|-----|----|----|
| Attendance Tracking | ❌ | ✅ | ✅ |
| Attendance Dashboard | ❌ | ✅ | ✅ |
| Fee Invoice Generation | ❌ | ✅ | ✅ |
| Fee Payment (manual) | ❌ | ✅ | ✅ |
| Fee Payment (Razorpay auto) | ❌ | ❌ | ✅ |
| Admissions Pipeline | ❌ | ✅ | ✅ |
| Lead Inquiry Tracking | ❌ | ✅ | ✅ |
| Staff Management | ❌ | ✅ | ✅ |
| Daily Report | ❌ | ✅ | ✅ |

#### **Compliance Layer (P2 / P3)**

| Feature | MVP | V1 | Phase 2 |
|---------|-----|----|----|
| Child Records (Medical) | ❌ | ✅ | ✅ |
| Incident Logging | ❌ | ✅ | ✅ |
| Incident Notification | ❌ | ✅ | ✅ |
| DPDP Consent Tracking | ❌ | ✅ | ✅ |
| Data Privacy Controls | ❌ | ✅ | ✅ |
| Export Data (DPDP) | ❌ | ✅ | ✅ |
| Audit Trail | ❌ | ❌ | ✅ |

---

## 7. Data Model & Relationships

### 7.1 Core Entity Relationships

```
┌────────────────────────────────────────────────────────┐
│                    School (Tenant)                      │
│  • school_id (PK)                                      │
│  • name, address, phone, timezone                      │
│  • logo_s3_key, subscription_tier                      │
│  • rekognition_collection_id                           │
└────────┬───────────────────────────────────────────────┘
         │
         ├─────────────────┬──────────────────┬─────────────────┐
         │                 │                  │                 │
         │                 ▼                  ▼                 ▼
    ┌────▼──────┐   ┌──────────────┐   ┌──────────────┐  ┌──────────────┐
    │   Class   │   │   Teacher    │   │    Child     │  │    Parent    │
    │-----------|   |--------------|   |--------------|  |--------------|
    │ class_id  │   │ teacher_id   │   │ child_id     │  │ parent_id    │
    │ school_id │   │ school_id    │   │ school_id    │  │ school_id    │
    │ name      │   │ name, phone  │   │ name, DOB    │  │ phone, email │
    │ teacher_id├──▼│ role         │   │ class_id ┌───┼─▶│ linked_child │
    │ year      │   │ class_id     │   │ photo_s3│   │  │ magic_tokens │
    └───────────┘   └──────────────┘   │ face_key│   │  └──────────────┘
         │                              │ linked  │   │
         │                              │ parents ├───┘
         │                              │ (via FK)│
         │                              └────┬────┘
         │                                   │
         │      ┌────────────────────────────┼────────────────────┐
         │      │                            │                    │
         │      ▼                            ▼                    ▼
    ┌─────────────────┐     ┌───────────────────┐  ┌──────────────────┐
    │      Post       │     │    Attendance     │  │    Milestone     │
    │─────────────────|     |-------------------|  |------------------|
    │ post_id         │     │ attendance_id     │  │ milestone_id     │
    │ class_id        │     │ class_id          │  │ school_id        │
    │ teacher_id      │     │ child_id          │  │ child_id         │
    │ caption         │     │ date              │  │ domain (NEP)     │
    │ media_urls[]    │     │ status (present..)│  │ achieved_date    │
    │ created_at      │     │ marked_at         │  │ source (post/tag)│
    └────┬────────────┘     └───────────────────┘  └──────────────────┘
         │
    ┌────┴────────────────┬─────────────────────────┐
    │                     │                         │
    ▼                     ▼                         ▼
┌────────────────┐  ┌──────────────┐      ┌──────────────┐
│ PostChildTag   │  │   Comment    │      │  Incident    │
│────────────────|  |--------------|      |--------------|
│ post_id        │  │ comment_id   │      │ incident_id  │
│ child_id       │  │ post_id      │      │ class_id     │
│ confidence     │  │ parent_id    │      │ child_id[]   │
│ confirmed      │  │ content      │      │ type         │
└────────────────┘  │ created_at   │      │ severity     │
                    │ teacher_reply│      │ notify_parent│
                    └──────────────┘      │ created_at   │
                                          └──────────────┘

┌───────────────────┐    ┌────────────────────┐
│     Reaction      │    │ DailyReport        │
│───────────────────|    |───────────────────-|
│ reaction_id       │    │ report_id          │
│ post_id           │    │ class_id           │
│ parent_id         │    │ teacher_id         │
│ emoji_type        │    │ date               │
│ created_at        │    │ mood, learning_..  │
└───────────────────┘    │ shared_with_parent │
                         └────────────────────┘

┌─────────────────────┐   ┌────────────────────┐
│   Draft / Outbox    │   │     Invoice        │
│─────────────────────|   |────────────────────│
│ draft_id            │   │ invoice_id         │
│ class_id            │   │ school_id          │
│ teacher_id          │   │ child_id           │
│ caption             │   │ parent_id          │
│ media_urls[]        │   │ amount             │
│ status (local..)    │   │ due_date           │
│ child_ids[]         │   │ status (due..)     │
└─────────────────────┘   │ created_at         │
                          └────────────────────┘
```

---

### 7.2 Data Access Patterns (Row-Level Security)

Every query is scoped by `school_id`. Examples:

| Entity | Teacher Can See | Parent Can See | Admin Can See |
|--------|-----------------|----------------|---------------|
| Post (in their class) | ✅ Own class posts | ❌ Only about their child | ✅ All posts in school |
| Child (roster) | ✅ Own class | ✅ Only their child | ✅ All children in school |
| Comment (on a post) | ✅ Teacher replies | ✅ If on their child's post | ✅ All |
| Attendance (own class) | ✅ Own class only | ❌ | ✅ All classes |
| Incident (their class) | ✅ Own class | ✅ About their child | ✅ All |
| Invoice | ❌ | ✅ For their child | ✅ All invoices |

---

## 8. Navigation Flows

### 8.1 Critical User Journeys

#### 👩‍🏫 **Teacher: "Post a moment in <5 minutes"**

```
[Teacher opens app]
  ↓
[T-1: Teacher Feed home]
  ↓
[Tap + (Composer button)]
  ↓
[T-2: Composer]
  ├─ Camera → take photo
  ├─ Auto-load caption draft (AI)
  ├─ Tap to select child(ren)
  ├─ Preview milestones AI suggests
  └─ [POST]
    ↓
  [Post queued / sent]
  ↕ (offline: stays in draft until online)
  ↓
[T-1: Post appears in feed]
```

**Target:** <5 minutes, <3 taps.

---

#### 👶 **Parent: "See update about my child"**

```
Option A: Magic-link (first time, no app install)
  [Parent receives WhatsApp]
  ↓
  [Tap link → P-0: Magic-link entry page]
  ↓
  [P-0A: OTP verification] (60s)
  ↓
  [P-3: Parent feed → sees today's posts about child]
  ↓
  [Tap post → reactions / comments]
  ↓
  (Optional) [Install app for future updates]

Option B: Installed app (returning parent)
  [Open app]
  ↓
  [P-3: Parent feed]
  ↓
  [Swipe to refresh / see new posts]
  ↓
  [Tap post → see details, react, comment]
```

**Target:** <30s to first photo after opening.

---

#### 🎯 **Admin: "Check on low-engagement class and take action"**

```
[Open dashboard → A-1: Home]
  ↓
[Alert: "Nursery A posted 1 time today (target = 3)"]
  ↓
[Click alert → expand details]
  ↓
[See: Nursery A, teacher = Sunita, last post = 8 AM]
  ↓
[Quick action: [Message Sunita]]
  ↓
[Modal: Pre-filled message]
  ├─ "Hi Sunita, Nursery A is on track! 1 post so far. Keep going 🎉"
  └─ [SEND via WhatsApp]
  ↓
[Check next alert]
```

**Target:** <2 minutes to identify + act on 3 alerts.

---

### 8.2 Onboarding Flows

#### **School Admin Onboarding**

```
[cadencesprout.com/signup]
  ↓
[Sign-up form: school name, phone, password]
  ↓
[Email verification]
  ↓
[A-0B: Setup wizard]
  ├─ Step 1: Upload logo
  ├─ Step 2: Create 1st class (e.g., "Nursery A")
  ├─ Step 3: Invite 1st teacher (SMS invite → teacher setup)
  ├─ Step 4: Add children (bulk or one-by-one)
  └─ [DONE → A-1: Dashboard]
```

---

#### **Teacher Onboarding**

```
[Receive SMS: "Set up your CadenceSprout account: [link]"]
  ↓
[T-0A: Login page]
  ↓
[Enter phone + set password]
  ↓
[T-0B: Welcome tour (skip-able)]
  ├─ "Here's how to post"
  ├─ "Your class roster"
  └─ "See parent reactions"
  ↓
[T-1: Teacher feed → ready to post]
```

---

#### **Parent Onboarding**

```
[Receive WhatsApp: "Sunita posted a photo of [Child]. See it here: [magic-link]"]
  ↓
[Tap link → P-0: Magic link page]
  ↓
[P-0A: Enter OTP (sent via SMS/WhatsApp)]
  ↓
[P-0B: Enter parent name]
  ↓
[P-0C: Notification preferences]
  ↓
[P-3: Parent feed → see child's post]
```

---

## 9. System Constraints & Rules

### 9.1 Scope Constraints

| Area | Rule | Rationale |
|------|------|-----------|
| **Offline** | Queue-based; Phase 2 full offline | Complexity vs MVP value tradeoff |
| **Search** | Phase 2; use feed filters for now | MVP focus is posting + feed |
| **Messaging** | Teacher ↔ Parent 1:1 messaging Phase 2 | Distraction from core loop |
| **Admin Mobile** | Web-only in Phase 1 | Lower usage volume, desktop-primary |
| **Multi-Child** | Parent can see 1 child in MVP; Phase 2 = siblings | Rostering complexity |
| **Compliance** | DPDP Act consent tracking, data export | India-specific legal requirement |
| **Language** | English in Phase 1; Hindi + Tamil Phase 2 | Time to market |

### 9.2 System Rules

| Rule | Implementation |
|------|-----------------|
| **Nothing blocks posting** | Composer must never require optional fields; AI suggestions are optional |
| **Post appears instantly in teacher feed** | Optimistic UI; revert only on actual failure |
| **Parent always sees their child's posts** | If child is tagged + confirmed, post is visible; permission check on every render |
| **One post per teacher per class per day nudge** | Trigger: 12 PM, one per class, cancelled if post arrives |
| **Attachment quota** | Max 10 media files per post (videos count as 1 each) |
| **Draft auto-save** | Every 10 seconds or on app background |
| **API rate limits** | 100 req/min per teacher, 50 req/min per parent |

### 9.3 Performance Targets

| Metric | Target | Notes |
|--------|--------|-------|
| **Post composition time** | <2 min end-to-end | Includes AI caption |
| **Post publish latency** | <3 sec after tap | Optimistic UI |
| **Parent feed load** | <2 sec first paint | Must feel instant |
| **AI caption generation** | <3 sec (P75) | Show shimmer while waiting |
| **Face detection** | <5 sec per photo | Background job |
| **Page load (web)** | <3 sec (P75) | Vite optimized |

---

## 10. Appendix: Screen Inventory

### 10.1 Complete Screen List by Persona

#### **Teacher App (Mobile + Web)**

| ID | Name | Tier | Mobile | Web | Description |
|:---|:-----|:----:|:-------:|:---:|-------------|
| T-0 | Login / Splash | Core | ✅ | ✅ | Phone + password login |
| T-0A | Setup Wizard | Onboarding | ✅ | ✅ | First-time tour (skip-able) |
| T-1 | Teacher Feed | P0 | ✅ | ✅ | Daily feed of class posts |
| T-1A | Nudge Banner | P0 | ✅ | ✅ | "No update yet" reminder |
| T-2 | Composer | P0 | ✅ | ✅ | Photo + caption + tags + milestones |
| T-2A | AI Caption Loading | P0 | ✅ | ✅ | Shimmer while caption generates |
| T-2B | Child Picker | P0 | ✅ | ✅ | Modal to select children for tagging |
| T-2C | Milestone Picker | P1 | ✅ | ✅ | Modal to tag milestones |
| T-2D | Incident Form | P1 | ✅ | ✅ | Inline incident reporting |
| T-3 | Milestones Tracker | P1 | ✅ | ✅ | View milestones achieved by child |
| T-4 | Attendance History | P1 | ✅ | ✅ | View past attendance records |
| T-5 | Class Roster | P0 | ✅ | ✅ | List of children + parents + status |
| T-5A | Child Detail | P0 | ✅ | ✅ | Child profile + milestones + history |
| T-5B | Quick Mark Attendance | P1 | ✅ | ✅ | Fast modal for marking attendance |
| T-5C | Milestone Progress | P1 | ✅ | ✅ | Per-child milestone view |
| T-5D | Incident History | P1 | ✅ | ✅ | Incidents logged for child |
| T-6 | Child Profile Deep-Dive | P1 | ✅ | ✅ | Full child record + linked posts |
| T-7 | Incident Detail | P1 | ✅ | ✅ | View + follow-up on incident |
| T-8 | Daily Report | P2 | ✅ | ✅ | Optional daily summary form |
| T-9 | Incident Logger | P1 | ✅ | ✅ | New incident entry form |
| T-10 | Profile & Settings | Core | ✅ | ✅ | Name, class, notifications |
| T-10A | Class Management | Core | ✅ | ✅ | Switch classes, manage roster link |
| T-10B | Notifications | Core | ✅ | ✅ | Opt-in push, WhatsApp, offline |
| T-10C | Offline Status | P2 | ✅ | ⚠️ | Show sync queue status |
| T-10D | Logout | Core | ✅ | ✅ | — |
| T-11 | Messages / Conversations | Phase2 | ❌ | ❌ | 1:1 teacher ↔ parent messaging |

#### **Parent App (Mobile + Web)**

| ID | Name | Tier | Mobile | Web | Description |
|:---|:-----|:----:|:-------:|:---:|-------------|
| P-0 | Magic-Link Entry | MVP | ✅ | ✅ | Landing page from WhatsApp link |
| P-0A | OTP Verification | MVP | ✅ | ✅ | SMS/WhatsApp OTP entry |
| P-0B | Name Registration | MVP | ✅ | ✅ | Parent name + passcode setup |
| P-0C | Permissions | MVP | ✅ | ✅ | Notifications + camera consent |
| P-1 | App Home | MVP | ✅ | ✅ | (Redirects to P-3) |
| P-3 | Parent Feed | MVP | ✅ | ✅ | Scrollable timeline of child updates |
| P-4 | Post Detail | MVP | ✅ | ✅ | Full-screen post + comments |
| P-4A | Teacher Reply | MVP | ✅ | ✅ | View teacher's comment reply |
| P-5 | Milestones & Progress | V1 | ✅ | ✅ | NEP 2020 domain progress view |
| P-6 | Year-End Portfolio | V1 | ✅ | ✅ | Memory book + download + share |
| P-7 | Notifications / Activity | V1 | ✅ | ✅ | In-app notification center |
| P-7A | Messages / Thread | Phase2 | ❌ | ❌ | Conversation with teacher |
| P-8 | Health & Medical Info | V1 | ✅ | ✅ | Read-only medical + edit by parent |
| P-9 | Fees & Payment History | V1 | ✅ | ✅ | Invoices + pay button (Phase2 = Razorpay) |
| P-11 | Incident History | V1 | ✅ | ✅ | Logged incidents about child |
| P-12 | Profile & Settings | MVP | ✅ | ✅ | Name, child, linked parents |
| P-13 | Notification Preferences | V1 | ✅ | ✅ | Push/WhatsApp/email opt-in |
| P-14 | Privacy & Permissions | V1 | ✅ | ✅ | Photo consent, DPDP, data delete |
| P-15 | Logout / Switch Account | MVP | ✅ | ✅ | — |
| P-16 | Child Profile (Read) | MVP | ✅ | ✅ | Child basic info + school class |
| P-17 | Class & Schedule | Phase2 | ❌ | ❌ | Class schedule + teacher bios |
| P-18 | Contact Teacher | Phase2 | ❌ | ❌ | Direct message or feedback form |
| P-19 | Help & FAQ | MVP | ✅ | ✅ | In-app help center |

#### **Admin Dashboard (Web Only)**

| ID | Name | Tier | Web | Description |
|:---|:-----|:----:|:---:|-------------|
| A-0 | Login / Registration | Core | ✅ | School signup + admin login |
| A-0A | School Profile Setup | Core | ✅ | Logo, name, timezone, billing |
| A-0B | School Setup Wizard | Core | ✅ | Classes, teachers, children, parents |
| A-1 | Home Dashboard | MVP | ✅ | KPIs, alerts, quick actions |
| A-2 | Engagement Dashboard | MVP | ✅ | Posts/day, parent engagement, trends |
| A-3 | Admissions Pipeline | V1 | ✅ | Lead inquiries, conversion funnel |
| A-4 | Fees Overview | V1 | ✅ | Summary: outstanding, collection % |
| A-5 | Attendance Dashboard | V1 | ✅ | Aggregate attendance + by-class detail |
| A-6 | Staff Management | V1 | ✅ | Teacher list, roles, activity |
| A-7 | Admissions Lead Management | V1 | ✅ | Detailed CRM for lead pipeline |
| A-8 | Fee Settings | V1 | ✅ | Configure fee amount, schedule |
| A-9 | Invoice Management | V1 | ✅ | Create, send reminders, mark paid |
| A-10 | Bulk Data Ops | Phase2 | ✅ | Bulk import children, teachers, etc. |
| A-11 | Child Records & Compliance | V1 | ✅ | Master list, medical, incidents, DPDP |
| A-12 | Staff & Permissions | V1 | ✅ | Detailed staff list, role matrix |
| A-13 | Incident Management | V1 | ✅ | Log, track, follow-up incidents |
| A-14 | Subscription & Billing | Core | ✅ | Plan, seats, payment method |
| A-15 | Audit & Logs | Phase2 | ✅ | Activity audit trail, data export |

---

## Appendix B: Persona × Capability Matrix (Summary)

```
                    | Teacher | Parent | Admin
--------------------|---------|--------|-------
Posting & Feed      |   ✅✅  |  ✅✅   |  ✅
Attendance          |   ✅    |  ❌    |  ✅✅
Milestones          |   ✅    |  ✅    |  ✅
Incidents           |   ✅    |  ✅    |  ✅
Fees                |   ❌    |  ✅    |  ✅✅
Admissions          |   ❌    |  ❌    |  ✅✅
Staff Mgmt          |   ❌    |  ❌    |  ✅
Compliance          |   ⚠️    |  ✅    |  ✅
Notifications       |   ✅    |  ✅    |  ⚠️
Offline             |   ❌    |  ❌    |  ❌
Search              |   ❌    |  ❌    |  ❌
```

---

## Appendix C: MVP vs V1 Feature Breakdown

### **MVP ("Post + See")**

**Teacher:**
- T-0, T-0A (login, setup)
- T-1, T-1A (feed + nudge)
- T-2, T-2A, T-2B (composer + AI + child picker)
- T-5, T-5A (roster + child detail)
- T-10 (settings)

**Parent:**
- P-0, P-0A, P-0B, P-0C (onboarding)
- P-3, P-4, P-4A (feed + posts + comments)
- P-12, P-13, P-14, P-15 (settings)
- P-16 (child profile read)

**Admin:**
- A-0, A-0A, A-0B (school setup)
- A-1, A-2 (home + engagement dashboard)

---

### **V1 ("Operate + Learn")**

**Additions for Teacher:**
- T-3, T-4 (milestones tracker + history)
- T-5B, T-5C, T-5D (quick attendance + milestones + incidents)
- T-8, T-9 (daily report + incident logger)
- T-10A, T-10B (class management + notifications)

**Additions for Parent:**
- P-5, P-6 (milestones + portfolio)
- P-7 (notifications)
- P-8, P-9, P-11 (health, fees, incidents)

**Additions for Admin:**
- A-3, A-4, A-5, A-6 (admissions, fees, attendance, staff)
- A-7, A-8, A-9 (detailed CRM, fee settings, invoices)
- A-11, A-12, A-13 (child records, staff detailed, incidents)

---

**Document End**

---

## Revision History

| Version | Date | Author | Change |
|---------|------|--------|--------|
| 1.0 | 2026-04-07 | AI | Initial IA document based on PRD v3.0 |

