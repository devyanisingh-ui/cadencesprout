# CadenceSprout — Stitch Prompts

Google Stitch UI generation prompts for all CadenceSprout screens. Each prompt is fully self-contained — Stitch needs no other document to generate the screen.

---

## Design Philosophy — CadenceSprout

CadenceSprout is not an ERP.

It is a daily storytelling tool that helps teachers share small, meaningful classroom moments with parents.

All design decisions must follow:

1. Posting must take < 30 seconds
2. ERP features must be optional and non-blocking
3. Emotional warmth > data density
4. Nudges should guide, never guilt
5. Parents consume stories, not dashboards

## Important: UX vs System Boundary

This document defines UI, interaction, and experience.

Any logic related to:
- Triggers (nudges, notifications)
- Offline sync
- AI processing
- Data persistence

Must be implemented as per the System Design document (Section 5).

---

## Master Screen Table (V2)

Unified view of all screens, organized by **persona**, **app**, and **feature** so Stitch prompts can be scoped quickly.

| Persona | App | Screen ID | Screen Name | Platform | Feature / Epic | Section | Status |
|---------|-----|-----------|------------|----------|----------------|---------|--------|
| Teacher | Teacher Mobile | T-0 | Teacher Login | Mobile (iOS-first) | Login & Authentication (Core Platform) | 4.1 Teacher App | ❌ Pending |
| Teacher | Teacher Mobile | T-1 | Home Feed (Class Feed) | Mobile (iOS-first) | Teacher Home Feed & Core Loop (Epic 3) | 4.1 Teacher App | ❌ Pending |
| Teacher | Teacher Mobile | T-2 | Post Composer | Mobile (iOS-first) | Post Creation (Epic 3) | 4.1 Teacher App | ❌ Pending |
| Teacher | Teacher Mobile | T-2A | Manual Child Tag Picker | Mobile (iOS-first) | Child Tagging (Epic 3) | 4.1 Teacher App | ❌ Pending |
| Teacher | Teacher Mobile | T-3 | Post Detail | Mobile (iOS-first) | Post Detail & Engagement (Epic 3) | 4.1 Teacher App | ❌ Pending |
| Teacher | Teacher Mobile | T-4 | Attendance | Mobile (iOS-first) | Attendance Marking (Epic 5) | 4.1 Teacher App | ❌ Pending |
| Teacher | Teacher Mobile | T-5 | Class Roster | Mobile (iOS-first) | Roster Management (Epics 1 & 2) | 4.1 Teacher App | ❌ Pending |
| Teacher | Teacher Mobile | T-5A | Child Detail | Mobile (iOS-first) | Child Profile & Parent Links (Epics 2 & 4) | 4.1 Teacher App | ❌ Pending |
| Teacher | Teacher Mobile | T-6 | Milestone Tracker (per child) | Mobile (iOS-first) | Milestone Tracking (Epic 4 & AI Layer) | 4.1 Teacher App | ❌ Pending |
| Teacher | Teacher Mobile | T-6A | Milestone Picker | Mobile (iOS-first) | Milestone Tagging (Epic 4 & AI Layer) | 4.1 Teacher App | ❌ Pending |
| Teacher | Teacher Mobile | T-7 | Profile / Settings | Mobile (iOS-first) | Teacher Profile & Settings (Core Platform) | 4.1 Teacher App | ❌ Pending |
| Teacher | Teacher Mobile | T-8 | Daily Report Form | Mobile (iOS-first) | Daily Report (Epics 3 & 18) | 4.1 Teacher App | ❌ Pending |
| Teacher | Teacher Mobile | T-9 | Incident Report Form | Mobile (iOS-first) | Incidents & Compliance (Epic 16) | 4.1 Teacher App | ❌ Pending |
| Parent | Parent Mobile | P-0 | Phone Number Entry / OTP Request | Mobile (iOS-first) | Magic-Link & Onboarding (Epic 2) | 4.2 Parent App | ❌ Pending |
| Parent | Parent Mobile | P-0A | OTP Verification | Mobile (iOS-first) | Magic-Link & Onboarding (Epic 2) | 4.2 Parent App | ❌ Pending |
| Parent | Parent Mobile | P-1 | Magic-Link Web View (Feed First) | Mobile (iOS-first) | Web Feed First Experience (Epic 2 & 4) | 4.2 Parent App | ❌ Pending |
| Parent | Parent Mobile | P-2 | DPDP Consent Screen | Mobile (iOS-first) | DPDP Consent & Privacy (Section 6.1) | 4.2 Parent App | ❌ Pending |
| Parent | Parent Mobile | P-3 | Parent Home Feed | Mobile (iOS-first) | Parent Feed Experience (Epic 4) | 4.2 Parent App | ❌ Pending |
| Parent | Parent Mobile | P-4 | Post Detail | Mobile (iOS-first) | Parent Post Detail & Reactions (Epic 4) | 4.2 Parent App | ❌ Pending |
| Parent | Parent Mobile | P-5 | Milestone Progress | Mobile (iOS-first) | Milestone Progress (Epic 4 & 10) | 4.2 Parent App | ❌ Pending |
| Parent | Parent Mobile | P-6 | Year-End Portfolio | Mobile (iOS-first) | AI Portfolio (Epic 7 & 10) | 4.2 Parent App | ❌ Pending |
| Parent | Parent Mobile | P-7 | Notifications | Mobile (iOS-first) | Notifications & Alerts (5B Notification System) | 4.2 Parent App | ❌ Pending |
| Parent | Parent Mobile | P-8 | Profile / Data & Privacy | Mobile (iOS-first) | Profile, DPDP & Consent Management (Section 6) | 4.2 Parent App | ❌ Pending |
| Parent | Parent Mobile | P-9 | Fees & Payments | Mobile (iOS-first) | Fees & Payments (Epics 6 & 14) | 4.2 Parent App | ❌ Pending |
| Parent | Parent Mobile | P-10 | Documents & Records | Mobile (iOS-first) | Child Documents & Records (Epic 16) | 4.2 Parent App | ❌ Pending |
| Parent | Parent Mobile | P-11 | Incident History | Mobile (iOS-first) | Incident History (Epics 4 & 16) | 4.2 Parent App | ❌ Pending |
| Admin | Admin Web | A-1 | Dashboard Home | Web | Admin Dashboard & Engagement Score (Epic 7) | 4.3 Admin Web | ❌ Pending |
| Admin | Admin Web | A-2 | Parent Feed (Read-Only) | Web | Parent Feed Monitoring (Epic 4 & 7) | 4.3 Admin Web | ❌ Pending |
| Admin | Admin Web | A-3 | Admissions Pipeline | Web | Admissions Management (Epic 11) | 4.3 Admin Web | ❌ Pending |
| Admin | Admin Web | A-4 | Fee Management | Web | Fee Management (Epic 6 & 14) | 4.3 Admin Web | ❌ Pending |
| Admin | Admin Web | A-5 | Attendance Dashboard | Web | Attendance Tracking (Epic 5) | 4.3 Admin Web | ❌ Pending |
| Admin | Admin Web | A-6 | Staff Management | Web | Staff Management / HRMS (Epic 17) | 4.3 Admin Web | ❌ Pending |
| Admin | Admin Web | A-7 | School Settings | Web | School Settings & Branding (Epic 1) | 4.3 Admin Web | ❌ Pending |
| Admin | Admin Web | A-8 | Reports | Web | Reports & Analytics (Epics 5–7) | 4.3 Admin Web | ❌ Pending |
| Admin | Admin Web | A-9 | Fees & Payments Overview | Web | Fees Overview & KPIs (Epic 14) | 4.3 Admin Web | ❌ Pending |
| Admin | Admin Web | A-10 | Admissions Overview | Web | Admissions Funnel & KPIs (Epic 15) | 4.3 Admin Web | ❌ Pending |
| Admin | Admin Web | A-11 | Child Records | Web | Child Records & Compliance (Epic 16) | 4.3 Admin Web | ❌ Pending |
| Admin | Admin Web | A-12 | Staff Overview | Web | Staff Overview & Status (Epic 17) | 4.3 Admin Web | ❌ Pending |
| Admin | Admin Web | A-13 | Login | Web | Admin Login & Authentication (Core Platform) | 4.3 Admin Web | ❌ Pending |
| Teacher | Teacher Web | TW-1 | Teacher Web Login | Web | Login & Authentication (Core Platform) | 4.4 Teacher Web | ❌ Pending |
| Teacher | Teacher Web | TW-2 | Teacher Web Home Feed | Web | Teacher Home Feed (Epic 3) | 4.4 Teacher Web | ❌ Pending |
| Teacher | Teacher Web | TW-3 | Teacher Web Post Composer | Web | Post Creation (Epic 3) | 4.4 Teacher Web | ❌ Pending |
| Teacher | Teacher Web | TW-4 | Teacher Web Attendance | Web | Attendance Marking (Epic 5) | 4.4 Teacher Web | ❌ Pending |
| Teacher | Teacher Web | TW-5 | Teacher Web Class Roster | Web | Roster Management (Epics 1 & 2) | 4.4 Teacher Web | ❌ Pending |
| Teacher | Teacher Web | TW-6 | Teacher Web Milestone Tracker (per child) | Web | Milestone Tracking (Epic 4 & 10) | 4.4 Teacher Web | ❌ Pending |
| Teacher | Teacher Web | TW-7 | Teacher Web Profile / Settings | Web | Teacher Profile & Settings (Core Platform) | 4.4 Teacher Web | ❌ Pending |
| Parent | Parent Web | PW-1 | Parent Web Magic-Link Feed | Web | Magic-Link Web Feed (Epic 2 & 4) | 4.5 Parent Web | ❌ Pending |
| Parent | Parent Web | PW-2 | Parent Web Full Feed (After OTP Login) | Web | Parent Feed Experience (Epic 4) | 4.5 Parent Web | ❌ Pending |
| Parent | Parent Web | PW-3 | Parent Web Post Detail | Web | Parent Post Detail & Reactions (Epic 4) | 4.5 Parent Web | ❌ Pending |
| Parent | Parent Web | PW-4 | Parent Web Milestone Progress | Web | Milestone Progress (Epic 4 & 10) | 4.5 Parent Web | ❌ Pending |
| Parent | Parent Web | PW-5 | Parent Web Profile / Settings | Web | Profile & Settings (Core Platform) | 4.5 Parent Web | ❌ Pending |
| Parent | Parent Web | PW-6 | Parent Web Privacy Settings (DPDP Consent Management) | Web | DPDP Consent & Privacy (Section 6.1) | 4.5 Parent Web | ❌ Pending |

---

## Persona & App Views (Quick Reference)

High-level slices of the master table so design and engineering can see each persona’s surfaces in order of their core journey.

### 👩‍🏫 Teacher — Mobile App

**Auth & Entry**
- T-0 — Teacher Login

**Core Daily Loop (Post → Engagement → Next Post)**
- T-1 — Home Feed (Class Feed)
- T-2 — Post Composer
- T-2A — Manual Child Tag Picker
- T-3 — Post Detail

**Classroom Ops (ERP-lite)**
- T-4 — Attendance
- T-5 — Class Roster
- T-5A — Child Detail

**Progress & Settings**
- T-6 — Milestone Tracker (per child)
- T-6A — Milestone Picker
- T-7 — Profile / Settings

### 👩‍🏫 Teacher — Web App

**Auth & Entry**
- TW-1 — Teacher Web Login

**Core Daily Loop**
- TW-2 — Teacher Web Home Feed
- TW-3 — Teacher Web Post Composer

**Classroom Ops**
- TW-4 — Teacher Web Attendance
- TW-5 — Teacher Web Class Roster

**Progress & Settings**
- TW-6 — Teacher Web Milestone Tracker (per child)
- TW-7 — Teacher Web Profile / Settings

### 👩‍👧 Parent — Mobile App

**Onboarding & Consent**
- P-0 — Phone Number Entry / OTP Request
- P-0A — OTP Verification
- P-1 — Magic-Link Web View (Feed First)
- P-2 — DPDP Consent Screen

**Daily Experience**
- P-3 — Parent Home Feed
- P-4 — Post Detail
- P-7 — Notifications

**Progress, Portfolio & Privacy**
- P-5 — Milestone Progress
- P-6 — Year-End Portfolio
- P-8 — Profile / Data & Privacy

### 👩‍👧 Parent — Web App

**Entry & Feed**
- PW-1 — Parent Web Magic-Link Feed
- PW-2 — Parent Web Full Feed (After OTP Login)
- PW-3 — Parent Web Post Detail

**Progress & Settings**
- PW-4 — Parent Web Milestone Progress
- PW-5 — Parent Web Profile / Settings
- PW-6 — Parent Web Privacy Settings (DPDP Consent Management)

### 👨‍💼 Admin / Principal — Web App

**Auth & Entry**
- A-9 — Login
- A-1 — Dashboard Home

**Engagement & Monitoring**
- A-2 — Parent Feed (Read-Only)
- A-8 — Reports

**ERP — Admissions, Fees, Attendance, Staff**
- A-3 — Admissions Pipeline
- A-4 — Fee Management
- A-5 — Attendance Dashboard
- A-6 — Staff Management

**Configuration**
- A-7 — School Settings

---

## Design System Reference (applies to all screens)

**Brand:** CadenceSprout — a warm, editorial app for Indian preschool teachers. Think Seesaw meets a boutique Indian school newsletter. Never generic, never cold.

**Palette (light mode):**
- Background: `#FAF7F2` (warm cream)
- Surface / card: `#FFFFFF`
- Primary action: `#5C8B6E` (sage green)
- Accent: `#C4784A` (terracotta)
- Text primary: `#1A1A1A`
- Text secondary: `#6B6B6B`
- Divider: `#E8E2D9`
- Success: `#4A8C5C`
- Error: `#C0392B`

**Palette (dark mode):**
- Background: `#1A1A1A`
- Surface / card: `#242424`
- Primary action: `#7AAF8C` (lighter sage)
- Accent: `#D4875A` (lighter terracotta)
- Text primary: `#F5F2EC`
- Text secondary: `#9A9A9A`
- Divider: `#333333`

**Typography:**
- Headlines / post captions: Fraunces (serif, italic feel) — warmth and personality
- UI labels, body, buttons: Inter (sans-serif) — clean and readable
- Font sizes: body 14sp, label 12sp, heading 18sp, caption 16sp

**Components:**
- Buttons: 48dp tall, 8dp radius, full-width primary in sage green
- Cards: 12dp radius, 2dp shadow (elevation 2), white surface on cream background
- Bottom tab nav: 4 tabs, active tab in sage green, inactive in `#9A9A9A`
- FAB: 56dp circle, sage green, bottom-right, 16dp from screen edge
- Input fields: 48dp tall, outlined style, 8dp radius, sage green focus border
- Child chips: 28dp tall, 8dp radius pill — solid sage green when confirmed, dashed border when AI-suggested/unconfirmed
- Skeleton loaders: warm cream (#EDE8DF) pulsing rectangles

**School placeholder:** "Sunshine Preschool" with a sun+leaf icon (circular, warm yellow + green)

**Persona names:** Sunita (teacher), Meera (parent), Rohan / Aarav / Priya (children), Rajesh (admin/principal)

**Platform:** React Native, iOS-first (iPhone 14 Pro viewport: 393×852pt). Safe area insets respected. Bottom tab nav sits above home indicator.

### Global Prompt & UX Rules (ERP, Finance, Compliance, Admin)

These rules apply across all Stitch prompts whenever you touch **ERP / OS features** (fees, admissions, records, staff, reports) so they stay lightweight and embedded inside engagement flows.

**ERP features (global prompt rule):**
- Must feel **lightweight**, not like a heavy enterprise ERP.
- Must be **embedded inside existing flows** (feed, post composer, roster, child profile, parent feed) instead of separate, intimidating control panels.
- Must **avoid dashboard-heavy designs** by default — prefer focused cards, inline banners, and contextual actions over dense widgets.

**Financial UX rules (fees & payments):**
- **Highlight overdue fees clearly** (chips, badges, or subtle banners) without shaming language.
- Use a strong, primary CTA label: **"Pay Now"** for payment actions.
- Always show **trust indicators** near payment CTAs (e.g., lock icon + "Secure UPI payment" note, masked payment details, or known payment partner logos).

**Compliance UX rules (records, documents, incidents):**
- Show simple, human-readable **privacy labels** near sensitive sections (e.g., "Visible to school only", "Shared with parents").
- Use a **secure upload UI**: clear "Upload document" button, progress indicator, success/error states; never auto-upload from camera roll.
- Clearly **indicate sensitive data** (medical info, emergency contacts, ID proofs, incident details) with discreet icons/labels and keep them visually separate from casual content.

**Admin UX rules (principal / admin web):**
- Use **tables** for large, multi-row data sets (fees, admissions, staff) with clear column headers.
- Always enable **filters, search, and bulk actions** for high-volume admin work; avoid one-by-one only flows.
- **Prioritize alerts and exceptions** (overdue fees, pending admissions, incidents) visually **above stats/graphs** — admins should see "what needs attention" first.

**Teacher-facing prompt additions:**
- Allow **optional reporting fields** (e.g., meals, naps, activities, incidents) that teachers can fill when they have time; never block core posting on these.
- Keep the core **posting flow fast** — Sunita should be able to share a simple photo + caption in **under 30 seconds** with zero ERP fields.
- Do **not overload the UI**: show ERP bits behind light affordances like "Add daily report" or "Log incident" links, rather than stuffing them into the main composer by default.

**Parent-facing prompt additions:**
- Maintain a warm, **emotional tone** — parents should feel they are reading their child’s story, not using a finance/compliance app.
- Make **financial and compliance features feel simple**: clear status, one primary action, and short explanations instead of complex dashboards.
- **Avoid overwhelming parents** with dense tables or jargon; use plain labels, progressive disclosure ("View details"), and small chunks of information.

---

## Hardcoded Navigation Rules

Every prompt must explicitly include its navigation/menu. Do not invent, rename, hide, or swap menu items between screens.

- Teacher mobile primary menu: `Feed | Attendance | Roster | Profile`
- Teacher mobile detail screens: keep teacher menu context and use back navigation; do not create extra tabs
- Teacher mobile modals/bottom sheets: no separate menu; inherit invoking screen context
- Parent mobile authenticated menu: `Feed | Milestones | Portfolio | Profile`
- Parent mobile pre-auth screens: no persistent menu
- Teacher web sidebar: `Feed | Attendance | Roster | Milestones | Profile`
- Parent web authenticated navigation:
  - Mobile bottom nav: `Feed | Milestones | Portfolio | Profile`
  - Desktop header nav: `Feed | Milestones | Portfolio | Profile`
- Settings and privacy screens must keep `Profile` as the active menu context

**Cross-platform parity (web vs mobile):**
- Unless a prompt explicitly calls out a difference, **all core behaviors must match between mobile and web** for the same persona: notifications indicators, portfolio access, AI hints/labels, and error/offline handling.
- Teacher Web screens (TW-2/TW-3/TW-6) should expose the same AI signals as Teacher Mobile (T-2/T-6) — e.g., AI-suggested children/captions and milestone insights.
- Parent Web screens (PW-2/PW-3/PW-4/PW-5) should surface notification indicators and weekly/portfolio views on par with Parent Mobile (P-3/P-4/P-5/P-6/P-7).

**Offline & failure behavior (global):**
- [SYSTEM] Offline sync, local queues, retries, and draft persistence are implemented according to the System Design document (Section 5).
- When offline, screens that depend on networked content must show a clear offline banner and fall back to cached content; actions that create content (posts, comments, milestones) should **queue locally** and sync when online.
- Critical upload failures (media, posts) must always present a recoverable state (e.g., saved to Drafts with a clear "Retry upload" CTA) rather than discarding work.

---

## Section 4.1 — Teacher App (Mobile)

---

### Screen T-0: Teacher Login

**Prompt for Google Stitch:**

Design a mobile login screen for CadenceSprout, a warm and editorial preschool app used by Indian teachers.

**Navigation / Menu (hardcoded):**
- No persistent menu on this pre-auth screen
- Do not show the teacher bottom tab bar here

**Layout:**
- iPhone 14 Pro viewport (393×852pt), portrait orientation
- Background: `#FAF7F2` (warm cream), full bleed
- Vertically centered content block, roughly 60% of screen height, horizontally padded 24dp on each side
- Top area: school logo placeholder — circular icon (sun + leaf motif, warm yellow #F5C842 + sage green #5C8B6E), 72×72dp, centered, followed by "Sunshine Preschool" in Inter Semibold 14sp, `#6B6B6B`, 8dp below the icon
- Below school name: "CadenceSprout" wordmark in Fraunces Regular 24sp, `#1A1A1A`, centered, 24dp below
- 40dp vertical gap before the form

**UI Elements:**
- Phone number field: full width, 48dp tall, outlined (1dp border `#E8E2D9`, 8dp radius), left side shows "+91" prefix in Inter Regular 14sp `#6B6B6B` with a vertical divider, numeric keypad triggers on focus, placeholder "Phone number" in `#9A9A9A`
- 16dp gap
- Password field: full width, 48dp tall, same outlined style, placeholder "Password" in `#9A9A9A`, right side shows eye icon (24dp, `#9A9A9A`) to toggle mask/unmask
- 12dp gap
- "Forgot password?" right-aligned text link, Inter Regular 13sp, `#5C8B6E` (sage green)
- 24dp gap
- [Log In] primary button: full width, 48dp tall, 8dp radius, fill `#5C8B6E`, label "Log In" in Inter Semibold 16sp white
- Footer at bottom of screen: "Powered by CadenceSprout" centered, Inter Regular 11sp `#9A9A9A`

**Colors & Typography:**
- Background `#FAF7F2`, form fields white surface, primary sage `#5C8B6E`
- Font: Inter throughout; wordmark in Fraunces

**States (include all as artboard variants or annotated states):**

*Default:* Empty phone and password fields, Log In button enabled but visually muted (full opacity sage green)

*Typing:* Active field gets 2dp sage green border `#5C8B6E`, keyboard slides up, content block shifts up to stay visible above keyboard

*Loading:* Log In button shows a small white spinner (20dp) replacing the label; inputs are disabled (opacity 0.5); no other change

*Error (invalid credentials):* Below the password field, inline error text in `#C0392B` Inter Regular 13sp: "Incorrect phone number or password." — fields retain their current values, border turns red `#C0392B`

*Success:* Brief green checkmark flash on the button (200ms), then transition away to Home Feed

*Dark mode:* Background `#1A1A1A`, card/fields on `#242424` surface, text `#F5F2EC`, sage green lightens to `#7AAF8C`, borders `#333333`, secondary text `#9A9A9A`

**Interactions & Animations:**
- Keyboard appears: content block translates up smoothly (spring animation, 300ms)
- Log In tap: button scale-down 0.97 on press (haptic feedback), spinner appears
- Error shake: form block does a brief horizontal shake (2 cycles, 150ms total) on invalid credentials
- Transition to Home Feed: fade + slide-up (300ms)

---

### Screen T-1: Home Feed (Class Feed)

**Prompt for Google Stitch:**

System Intent:
- Drive a consistent **daily posting habit** from Sunita without guilt or pressure.
- Make it obvious **when parents haven’t seen anything today** and gently nudge a new post.
- Keep the screen emotionally warm and low-friction so posting feels like sharing, not work.

Metric:
- Primary: North Star (parents seeing ≥1 meaningful update per day), teacher posting rate.
- Secondary: Posts per class per week, % days with at least one post.

Design the Home Feed screen of CadenceSprout, the primary daily landing screen for Sunita (a preschool teacher at Sunshine Preschool). This is a mobile screen, React Native, iOS-first (iPhone 14 Pro, 393×852pt).

**Navigation / Menu (hardcoded):**
- Render the bottom tab bar exactly as: `Feed | Attendance | Roster | Profile`
- Feed is active

**Layout:**
- Background: `#FAF7F2` (warm cream), full bleed
- Top: native status bar (dark icons on cream) + custom header (56dp tall): left side — circular school logo (sun+leaf, 32dp), right of logo — "Sunshine Preschool" Inter Semibold 14sp `#1A1A1A` stacked above "LKG A" Inter Regular 12sp `#6B6B6B`; right side of header — notification bell icon 24dp `#6B6B6B`
- Immediately below header: **daily status banner** (56dp tall, full width, 16dp horizontal padding) with warm cream background slightly darker than page (`#F3EEE5`):
  - Left: date + status line in Inter Regular 13sp — e.g. "Today · No update yet" (grey) or "Today · Update posted" (sage).
  - Right: small CTA chip when no post exists today — solid sage pill "Share a moment" that, when tapped, opens Post Composer.
- Below the banner: scrollable feed area between banner and tab bar, 16dp horizontal padding.
- Bottom: tab bar (56dp, white surface, top border 1dp `#E8E2D9`): 4 tabs left to right — Feed (active, sage green icon + label), Attendance (inactive grey), Roster (inactive grey), Profile (inactive grey). Each tab: 24dp icon + 11sp label below, tappable area full-width tab zone

**UI Elements (Post Card):**
Show 2 full post cards and a partial third card (to signal scrollability):

Post card structure (12dp radius, white surface, 2dp shadow):
- Full-bleed photo (4:3 ratio, 345dp wide, ~259dp tall, top 12dp radius, bottom flush) — placeholder: warm classroom scene or colorful finger painting
- Card body below photo, 12dp padding:
  - Caption in Fraunces Italic 16sp `#1A1A1A`: e.g. "Rohan showed incredible focus during block building today — spatial reasoning is blooming! 🌱"
  - 8dp gap
  - Child chips row: solid sage green pill chips (28dp tall, 8dp radius, `#5C8B6E` fill, white text Inter Regular 12sp) — e.g. "Rohan" "Aarav" "Priya"
  - 8dp gap
  - Bottom meta row: left — "2 hours ago" Inter Regular 12sp `#9A9A9A`; right — eye icon + "14 / 18 parents viewed" Inter Regular 12sp `#9A9A9A`

FAB: 56dp circle, `#5C8B6E` sage green, white `+` icon (24dp), fixed bottom-right, 16dp from right edge, 16dp above tab bar top. When **no post exists today**, apply a soft pulsing halo animation (slight scale/opacity pulse) to gently nudge posting.

**Colors & Typography:**
- Cream background, white cards, sage green primary, Fraunces for captions, Inter for metadata

**States (as variants):**

*Loading (skeleton):* Replace post cards with skeleton cards — same card dimensions, photo area is a warm cream `#EDE8DF` pulsing rectangle (shimmer animation left-to-right), caption area is 3 lines of rounded rectangles in `#EDE8DF`, chip area is 2 oval placeholders

*Empty — no students yet:* Remove post cards. Center in body: a warm illustration placeholder (e.g. an empty classroom with chairs and sunlight, soft watercolor style), below it: "Add your students to get started" Inter Semibold 16sp `#1A1A1A`, below that a secondary button (outlined sage green): "Add Students"

*No posts today (morning default):* Daily status banner shows "Today · No update yet" with the "Share a moment" CTA chip. Past posts (from previous days) appear below, grouped under date headers.

*Midday nudge (no post by ~12 PM):* Daily status banner copy escalates to an emotional nudge: headline line "Parents haven’t seen an update today" in Inter Semibold 14sp `#C4784A` with secondary text "Share one simple moment from class" in Inter Regular 13sp `#6B6B6B`. The CTA chip label becomes **"Share a moment"** and visually pulses once when the teacher returns to the app after 12 PM.
- [SYSTEM] Midday nudge trigger timing and frequency are defined in the System Design document (Section 5); this screen only specifies the visual treatment.

*Post already created today:* Daily status banner shows "Today · Update posted" in sage green with a soft success icon (checkmark in circle). If Sunita has posted on **2+ consecutive days**, add a second line of copy: "You’ve shared 3 days in a row 🌱 — parents love this." to build a gentle streak habit. FAB no longer pulses.

*[SYSTEM] Offline banner:* Persistent horizontal banner (40dp tall, `#C4784A` terracotta fill) pinned below the custom header: left — wifi-off icon 16dp white, "You're offline — showing saved content" Inter Regular 13sp white

*Dark mode:* Background `#1A1A1A`, cards `#242424`, caption text `#F5F2EC`, meta text `#9A9A9A`, tab bar `#242424`, header `#1A1A1A`, FAB `#7AAF8C`

**Interactions & Animations:**
- Pull-to-refresh: standard iOS spinner in sage green, refreshes feed
- FAB tap: spring scale-up animation (0.95→1.05→1.0, 200ms), opens Post Composer as modal slide-up
- Post card tap: navigates to Post Detail (T-3) with a hero image expand transition
- Tab switch: immediate, no animation, icon + label color transitions to/from sage
- Skeleton to content: fade-in per card as data loads (stagger 80ms per card)

---

### Screen T-1A: Teacher Nudge State (Midday)

**Prompt for Google Stitch:**

Design a focused variant of the T-1 Home Feed banner that appears when Sunita opens the app around midday and hasn’t posted yet. This is not a separate screen, but a **named state** of T-1 for design clarity.

**Context:**
- Entry point: Sunita opens the app after ~12 PM on a school day and there is still no post for today.
- Goal: Gently nudge her to share a small moment, without guilt.

**Layout (reuse T-1):**
- Same header and feed layout as T-1.
- Banner at top uses:
  - Background `#FEF3E7` (slightly warmer than `#F3EEE5`).
  - Left text block:
    - Line 1: "Parents haven’t seen an update today" Inter Semibold 14sp `#C4784A`.
    - Line 2: "Share even a small moment from class" Inter Regular 13sp `#6B6B6B`.
  - Right: pill button "Share a moment" (solid sage) that opens T-2.

**States & Microcopy:**
- Single primary state when no post exists today and local time is AFTER ~12 PM.
- Once today’s post is created, the banner reverts to the normal "Today · Update posted" success state from T-1 and T-1A no longer appears.

**Interactions & Animations:**
- When Sunita first lands on this state, the banner and CTA gently fade/slide in from top (200ms) to draw attention.
- The CTA pill may use a very soft scale pulse (1.0→1.04→1.0) once to hint at action, but avoid aggressive or repeating animations.

---

### Screen T-2: Post Composer

**Prompt for Google Stitch:**

System Intent:
- Make it possible for Sunita to create a rich post in **under 30 seconds**.
- Let AI assist (captions, child detection) but **never block or slow down** posting.
- Preserve a calm, focused space where losing work is nearly impossible (drafts, offline queue).
  - [SYSTEM] Drafts, offline queue, retries, and AI processing are implemented according to the System Design document (Section 5); this prompt only defines how those states appear.

Metric:
- Primary: Teacher posting rate, posts per class per week.
- Secondary: Time-to-post (median seconds to create a post), draft completion rate.

Design the Post Composer screen for CadenceSprout's teacher app. This is a modal that slides up over the Home Feed when Sunita taps the FAB. iPhone 14 Pro, 393×852pt, React Native, iOS-first.

**Navigation / Menu (hardcoded):**
- No separate menu inside this modal
- Inherit teacher app navigation context from Home Feed: `Feed | Attendance | Roster | Profile`

**Layout:**
- Background: `#FAF7F2` (warm cream), fills the full modal
- Modal handle: 4dp×32dp rounded pill in `#E8E2D9`, centered, 12dp from top
- Header row (56dp, no border): left — "✕ Discard" Inter Regular 15sp `#C0392B`; center — "New Post" Inter Semibold 16sp `#1A1A1A`; right — [POST] button 36dp tall 8dp radius `#5C8B6E` fill white text Inter Semibold 15sp
- Body: vertically scrollable, 16dp horizontal padding

Content order top to bottom:
1. **Photo preview area** — full-width, 4:3 ratio with responsive height, 12dp radius, shows selected photo center-cropped. Below the photo: small row of thumbnail chips if multiple photos (28dp tall each), with a "+" add more chip at the end
2. **Caption field** (16dp top gap) — multiline, min 3 lines, no visible border, placeholder in Fraunces Italic 16sp `#9A9A9A`: "What happened in this moment?" When AI caption is present: Fraunces Italic 16sp `#1A1A1A` text appears. Top-right corner of caption area: a small ✨ badge (16dp, `#5C8B6E`) indicating AI-drafted
3. **AI Suggestions section** (12dp top gap) — small label row above the children chips: label "AI detected these children" Inter Semibold 12sp `#6B6B6B` with a subtle info icon ("i") that, on hover/long-press, explains "Based on this photo; please confirm before posting." This label only appears when AI has suggestions.
  - [SYSTEM] AI detection, confidence scores, and suggestion logic come from the backend/AI layer defined in the System Design; the UI only presents suggested chips and confirmations.
4. **Children row** (8dp below label) — chips for suggested and confirmed children. Chips: solid sage for confirmed, dashed border sage for AI-suggested (same pill style, dashed 1.5dp border `#5C8B6E`, sage text, transparent fill). Each **AI-suggested** chip shows small confidence text inside (e.g., "Rohan · 92%" in Inter Regular 11sp `#6B6B6B`) and includes in-chip quick actions: a tiny ✓ icon on the left edge (confirm) and ✕ on the right edge (remove). Tapping ✓ converts the chip to solid sage and hides the confidence text; tapping ✕ removes the chip. "Add manually +" text link at end of chip row, Inter Regular 13sp `#5C8B6E`
5. **Milestones row** (12dp top gap) — "Add milestones (optional) ›" full-width tappable row, Inter Regular 14sp `#6B6B6B`, right chevron icon; 1dp top/bottom dividers in `#E8E2D9`
6. **Class row** (0dp gap, below milestones divider) — "Class: LKG A ›" same row style — tappable to change class if teacher has multiple

**Colors & Typography:**
- Same warm palette; caption uses Fraunces for that editorial feel; all other text Inter

**States (as variants):**

*[SYSTEM] AI caption loading:* Caption area shows a shimmer animation — two lines of `#EDE8DF` rounded rectangles pulsing, with "Drafting caption..." in Inter Regular 13sp `#9A9A9A` above them

*[SYSTEM] AI caption ready:* Caption text populates with a gentle fade-in; ✨ badge visible; cursor placed at end for editing. When there is at least one photo selected and AI caption + child suggestions are ready, surface a **one-tap "Post now" shortcut** near the [POST] button that uses the AI caption and suggested child tags as-is, for ultra-fast posting.

*[SYSTEM] AI caption failed:* Caption area shows empty placeholder only, ✨ badge absent; a subtle toast at bottom: "AI caption unavailable — write your own" Inter Regular 13sp white on `#333333`, 4dp radius, auto-dismiss 3s

*Face recognition pending:* Child chips all grey dashed with "..." label, small spinner (12dp) inside each chip

*Face recognition complete:* Some chips turn solid sage (confirmed), some remain dashed (low confidence). Each AI-suggested chip shows its confidence (e.g., "Aarav · 78%") and inline ✓/✕ affordances for quick confirm/remove. A helper text line "Couldn't identify 2 children — add manually" appears if any children remain uncertain.

*Upload in progress (POST tapped):* [POST] button becomes a horizontal progress bar (same 36dp height, fills left to right in sage green, remaining fill in `#E8E2D9`); optimistic post card appears on the feed behind the (partially transparent) modal

*[SYSTEM] Upload failed:* Toast at bottom of screen (persistent, not auto-dismiss): "Upload failed — tap to retry" Inter Semibold 14sp, `#FAF7F2` text on `#C4784A` terracotta background, full width with a "Retry" button right-aligned. The current post (media + caption + selected children) is automatically **saved as a Draft** so Sunita never loses work.

*[SYSTEM] Drafts state:* If Sunita closes the composer without posting, the current content is auto-saved into a "Drafts" bucket. When she re-opens Post Composer from T-1, show a subtle banner at the top of the modal: "You have an unsent draft from today" with actions: [Resume draft] and "Discard" text link.

*[SYSTEM] Offline mode:* If the device is offline when she taps [POST], show a small inline notice above the footer: "Offline — this post will send when you're back online". The post is queued locally and will retry automatically when connectivity returns; until then it appears in Drafts/Outbox with a clock icon.

*Dark mode:* Background `#1A1A1A`, caption area `#242424`, chip fills and borders adjusted, shimmer in `#333333`

**Interactions & Animations:**
- Modal slides up from bottom (spring, 350ms); background dims to 40% black overlay
- Photo tap: opens native image picker
- Caption field: cursor auto-placed after AI text; typing replaces AI draft (✨ badge remains as attribution)
- POST tap: haptic feedback (medium impact), progress bar animates, modal closes on success with a "Posted!" confetti burst (3 colored dots: sage, terracotta, cream, 500ms)
- Discard tap: confirmation bottom sheet "Discard this post?" with [Discard] (red) and [Keep editing] (sage)
 - [SYSTEM] Auto-save: small unobtrusive "Saved to draft" microcopy fades in near the header every ~10 seconds while editing or when the user navigates away without posting; persistence and retry rules follow the System Design.

---

### Screen T-3: Post Detail

**Prompt for Google Stitch:**

Design the Post Detail screen for CadenceSprout's teacher app. Sunita taps a post card from the Home Feed to see full details and parent engagement. iPhone 14 Pro, 393×852pt, React Native, iOS-first.

**Navigation / Menu (hardcoded):**
- Keep teacher app navigation context as `Feed | Attendance | Roster | Profile`
- Use back navigation in the header; do not add a second tab bar

**Layout:**
- Background: `#FAF7F2` (warm cream)
- Header (56dp): back chevron `←` left 24dp `#1A1A1A`, center "Post" Inter Semibold 16sp, right: share icon 24dp `#6B6B6B`
- Body: scrollable, no horizontal padding on the photo

Content top to bottom:
1. **Full-bleed photo** — 393dp wide, ~295dp tall (4:3), flush to screen edges, no radius. If multiple photos: horizontal swipe carousel with page dots (5dp circles, active sage green, inactive `#E8E2D9`) pinned bottom-right of image
2. **Post meta block** (16dp padding, 16dp top gap): "2 hours ago · LKG A" Inter Regular 12sp `#9A9A9A`
3. **Caption** (8dp top gap): Fraunces Italic 18sp `#1A1A1A`, e.g. "Rohan showed incredible focus during block building today — spatial reasoning is blooming! 🌱" Full text, no truncation
4. **Children chips** (12dp top gap): label "Children tagged:" Inter Semibold 12sp `#6B6B6B`, then chip row: solid sage chips per child
5. **Milestones block** (12dp top gap, only if milestones exist): label "Milestones observed:" Inter Semibold 12sp `#6B6B6B`, then list of milestone tags — small pill with `#EDE8DF` fill, `#6B6B6B` text, e.g. "Spatial reasoning" "Motor skills"
6. **Engagement block** (12dp top gap, 1dp top divider `#E8E2D9`): eye icon `#5C8B6E` + "Seen by 14 of 18 parents" Inter Semibold 14sp `#1A1A1A`; below: horizontal progress bar (345dp, 8dp tall, 4dp radius, sage green fill proportional to 14/18)
7. **Comments section** (16dp top gap, 1dp top divider): "Comments (3)" Inter Semibold 14sp `#1A1A1A`; each comment: circular avatar (32dp) + name Inter Semibold 13sp + comment text Inter Regular 13sp + timestamp 11sp `#9A9A9A`; parent name in terracotta `#C4784A` to distinguish from teacher

**Colors & Typography:** Cream background, white content blocks, Fraunces for caption, Inter elsewhere, sage engagement accent

**States:**

*Loading:* Skeleton version — photo area is a pulsing cream rectangle, caption area is 3 lines skeleton, engagement block skeleton

*No comments:* Comments section shows "No comments yet." Inter Regular 13sp `#9A9A9A`, centered

*Dark mode:* Background `#1A1A1A`, content `#242424`, text `#F5F2EC`, page dots adjusted, engagement bar lighter sage

**Interactions & Animations:**
- Hero image expand transition from feed card (shared element animation, 300ms)
- Photo swipe: horizontal scroll snap between images, page dots update
- Pull down from top: dismiss back to feed (iOS-style interactive dismiss)
- Parent avatar tap: no navigation (read-only in teacher view)

---

### Screen T-4: Attendance

**Prompt for Google Stitch:**

System Intent:
- Allow Sunita to **complete daily attendance in under 60 seconds** for a typical class.
- Keep the UI simple enough that she can mark attendance one-handed between activities.
- Quietly ensure data quality for admin/ops without turning this into a heavy ERP screen.

Note: This feature must never block core posting flow.

Design the Attendance screen for CadenceSprout's teacher app. Sunita marks daily attendance from the bottom nav. iPhone 14 Pro, 393×852pt, React Native, iOS-first.

**Navigation / Menu (hardcoded):**
- Render the bottom tab bar exactly as: `Feed | Attendance | Roster | Profile`
- Attendance is active

**Layout:**
- Background: `#FAF7F2` (warm cream)
- Header (56dp): center — "Attendance" Inter Semibold 16sp; left — `←` back chevron (only shown when viewing a past date); right — calendar icon 24dp `#6B6B6B`
- Below header: date row (40dp, 16dp horizontal padding): left `‹` arrow, center "Thursday, 26 March 2026" Inter Semibold 14sp `#1A1A1A`, right `›` arrow (disabled for today — greyed out); back-navigation allows corrections up to 7 days
- Below date: class + stats row: "LKG A · 22 children" Inter Regular 13sp `#6B6B6B`, right side: "Present: 18 · Absent: 2" Inter Regular 13sp `#5C8B6E` (updates live as teacher marks)
- Body: flat scrollable list, 16dp horizontal padding, 8dp between rows
- Bottom: [Submit Attendance] full-width button (48dp, 8dp radius, `#5C8B6E` fill white text Inter Semibold 16sp), floating above tab bar with 16dp padding on all sides; white background behind it with 1dp top border `#E8E2D9`
- Bottom tab bar (same as T-1, Attendance tab active in sage)

**UI Elements (Attendance Row):**
Each row (68dp tall, white card, 8dp radius, 12dp horizontal padding, 4dp vertical padding):
- Left: circular child photo (44dp, placeholder warm placeholder avatar with child initial, sage green background)
- Right of photo: child name Inter Semibold 15sp `#1A1A1A` + below it: age "4 yrs" Inter Regular 12sp `#9A9A9A`
- Far right: Present/Absent toggle — custom 2-state pill toggle (72dp × 32dp, 16dp radius): present state fills sage green `#5C8B6E` with "P" Inter Semibold 12sp white; absent state fills `#E8E2D9` with "A" Inter Regular 12sp `#9A9A9A`
- If absent: a small "reason ›" tappable text appears below the toggle in Inter Regular 12sp `#C4784A` terracotta

Show approximately 6–7 rows visible before scroll.

**Colors & Typography:** Cream background, white rows, sage presence toggle, terracotta absence accent

**States:**

*Not yet taken (initial load):* All toggles in unset/neutral state — grey pill with no "P" or "A" active, placeholder appearance; date header shows today; Submit button is disabled (opacity 0.5) until all children are marked

*In progress:* Some rows marked P (sage), some A (grey+A), some still unset; counter in stats row updates: "Present: 12 · Absent: 3 · Unmarked: 7"; Submit button remains disabled while any unmarked remain

*All marked, not submitted:* Submit button becomes fully enabled (full opacity sage); "All 22 marked ✓" appears in the stats row in sage green

*Submitted:* All toggles become read-only (opacity 0.7, no tap response); button changes to "✓ Attendance Submitted" with a green checkmark, disabled state; a toast at top: "Attendance saved for today" auto-dismisses 3s; top-right edit icon appears for corrections until midnight

*Past date (viewing corrections):* Date row shows the past date, right `›` arrow is enabled up to today; "Submitted" badge in sage green shown next to the date; rows are editable; Submit button shows "Update Attendance"

*Dark mode:* Background `#1A1A1A`, rows `#242424`, toggle present `#7AAF8C`, absent `#333333`, text `#F5F2EC`

**Interactions & Animations:**
- Toggle tap: spring animation (toggle thumb slides 200ms), haptic feedback (light)
- Absence reason: bottom sheet slides up with preset reasons (Sick / Family function / Unspecified) + free text field
- Submit tap: medium haptic, button spins briefly, then success state
- Date navigation arrows: slide in new roster from left/right (200ms)

---

### Screen T-5: Class Roster

**Prompt for Google Stitch:**

Design the Class Roster screen for CadenceSprout's teacher app. Sunita views all children in her class and their parent contact status. iPhone 14 Pro, 393×852pt, React Native, iOS-first.

**Navigation / Menu (hardcoded):**
- Render the bottom tab bar exactly as: `Feed | Attendance | Roster | Profile`
- Roster is active

**Layout:**
- Background: `#FAF7F2` (warm cream)
- Header (56dp): center "Class Roster" Inter Semibold 16sp; right — search icon 24dp `#6B6B6B`
- Search bar (appears when search icon tapped, 48dp tall, 16dp padding): outlined field, 8dp radius, placeholder "Search children…" Inter Regular 14sp `#9A9A9A`, sage green focus border
- Class summary strip (40dp, 16dp horizontal padding): "LKG A · 22 children" Inter Regular 13sp `#6B6B6B`, right side: "18 parents active" Inter Regular 13sp `#5C8B6E`
- Body: flat scrollable list, 16dp horizontal padding, 8dp between rows
- Bottom tab bar (Roster tab active in sage)

**UI Elements (Roster Row):**
Each row (72dp tall, white card, 8dp radius, 12dp padding):
- Left: circular child photo avatar (48dp, warm placeholder with initial, different pastel background per child — rotate through: `#E8F4EC` sage-tint, `#FEF3E7` terracotta-tint, `#F0EBE3` cream-tint)
- Center block: child name Inter Semibold 15sp `#1A1A1A`; below — "4 yrs · Adm #2341" Inter Regular 12sp `#9A9A9A`; below — parent name "Parent: Meera" Inter Regular 12sp `#6B6B6B`
- Right: parent status badge (pill, 24dp tall, 8dp horizontal padding, Inter Regular 11sp):
  - Active: `#E8F4EC` fill, `#4A8C5C` text "Active"
  - Invited: `#FEF3E7` fill, `#C4784A` text "Invited"
  - Not invited: `#F0EBE3` fill, `#9A9A9A` text "Not invited"
- Right edge: chevron `›` 16dp `#9A9A9A`

Show approximately 7–8 rows before scroll. First row: Aarav (Active), Second: Priya (Active), Third: Rohan (Invited), Fourth: child with "Not invited" for contrast.

**Colors & Typography:** Warm tinted avatars, status badges with semantic colours, Inter throughout

**States:**

*Default list:* Rows as above, search bar hidden

*Search active:* Search bar visible below header, keyboard up, list filters in real-time to matching children; no match: "No children match 'xyz'" centered in body Inter Regular 14sp `#9A9A9A`

*Child detail (tap on row):* Navigate to a detail sheet (show as bottom sheet or full screen — design as full screen): child name as header, 80dp circular avatar, DOB + age, parent name(s) with phone number (masked: 98765 ••••0), parent status badge, "Recent posts (3) ›" tappable row, "Milestones ›" tappable row, "Attendance this month: 18/22 days" row

*Dark mode:* Background `#1A1A1A`, rows `#242424`, avatars use darker tint versions, status badges darken fills, text `#F5F2EC`

**Interactions & Animations:**
- Search icon tap: search bar slides down (200ms) and keyboard appears
- Row tap: push navigation with slide-left transition (standard iOS)
- Search clear: rows animate back to full list (subtle fade)

---

### Screen T-6: Milestone Tracker (per child)

**Prompt for Google Stitch:**

Design the Milestone Tracker screen for CadenceSprout's teacher app. Sunita views and records developmental milestones for a specific child (Rohan, age 4). This is accessed from the Class Roster by tapping a child. iPhone 14 Pro, 393×852pt, React Native, iOS-first.

**Navigation / Menu (hardcoded):**
- Keep teacher app navigation context as `Feed | Attendance | Roster | Profile`
- Use back navigation as the primary way out; do not add a milestone-specific bottom menu

**Layout:**
- Background: `#FAF7F2` (warm cream)
- Header (56dp): back `←` left, center "Rohan's Milestones" Inter Semibold 16sp, right: "Add +" Inter Semibold 14sp `#5C8B6E` (tappable)
- Child identity strip (72dp, white surface, 16dp padding, no radius): circular photo (48dp, warm placeholder), "Rohan" Inter Semibold 16sp `#1A1A1A`, below "LKG A · 4 yrs" Inter Regular 13sp `#9A9A9A`. Right side: milestone progress ring (circular progress indicator, 48dp, sage green arc, center shows "12/20" in Inter Semibold 12sp `#1A1A1A`)
  - **AI insight banner** (40dp tall, 16dp horizontal padding, 8dp radius, sits directly under the child strip): warm cream `#FEF3E7` background with a small ✨ icon on the left. Copy in Inter Regular 13sp:
    - [SYSTEM] AI-generated insight content (domains/skills from recent posts) is produced by the AI layer defined in the System Design; this banner only renders the supplied text.
  - Title line: "Based on recent posts, Rohan may be developing:" in `#C4784A`.
  - Subtext (wrap if needed): "• Spatial reasoning   • Fine motor skills" in `#6B6B6B`.
  - This banner only appears when AI has a confident suggestion; otherwise the space collapses.
- Domain tab bar (48dp, horizontal scroll if needed): 5 tabs — Physical | Cognitive | Language | Social-Emotional | Aesthetic. Active tab: Inter Semibold 14sp `#1A1A1A` with 2dp sage green underline; inactive: Inter Regular 14sp `#9A9A9A`
- Body: scrollable milestone list for selected domain, 16dp horizontal padding
- Bottom: standard tab bar (not shown when accessed as detail view — show back navigation only)

**UI Elements (Milestone Row):**
Each milestone row (white card, 12dp padding, 8dp radius, 8dp gap between rows):
- Left: status icon (24dp circle): achieved — `#5C8B6E` filled circle with white checkmark; not yet — `#E8E2D9` circle with no icon
- Center: milestone name Inter Semibold 14sp `#1A1A1A`, e.g. "Balances on one foot for 5 seconds"; below — age range Inter Regular 12sp `#9A9A9A` "Ages 3.5–4.5"; if achieved: date "Observed 12 Mar 2026" Inter Regular 11sp `#5C8B6E`
- Right (if achieved): "Seen in post ›" tappable text Inter Regular 12sp `#C4784A` terracotta with arrow

Show in Cognitive tab: 4–5 milestones, mix of achieved (checkmark) and not-yet. Example milestones:
- "Sorts objects by 2 attributes" — Achieved (12 Mar)
- "Counts to 10 correctly" — Achieved (20 Feb)
- "Understands cause and effect" — Not yet
- "Names 5+ colours correctly" — Not yet
- "Follows 3-step instructions" — Achieved (5 Mar)

**Colors & Typography:** Warm cream base, white cards, sage green achievement accents, Fraunces not used here (this is data, not editorial), Inter throughout

**States:**

*No milestones logged (new child):* Domain tab shows empty state: a small warm illustration (growth seedling icon in sage + terracotta), "Milestones will appear here as you observe them" Inter Regular 14sp `#9A9A9A`, centered; "Add Observation +" button below (outlined sage green, 48dp)

*AI insight available:* AI banner is visible under the child identity strip, highlighting 1–3 likely domains/skills from recent posts. Tapping the banner gently scrolls to the relevant domain tab (e.g., Cognitive) and briefly highlights milestones that match the suggested skills.

*Domain switching:* Tabs slide to active, list fades to new domain content (150ms fade)

*Add milestone (tap "Add +"):* Bottom sheet slides up: NEP 2020 domain selector (5 domain pills), then a scrollable list of milestones in that domain. Tap a milestone to mark it observed today. "Date" field (defaults to today, editable). "Link to post (optional) ›" field. [Save] button sage green full-width.

*Dark mode:* Background `#1A1A1A`, cards `#242424`, text `#F5F2EC`, achievement icons lighter sage `#7AAF8C`, tab underline same sage, not-yet circles `#333333`

**Interactions & Animations:**
- Domain tab switch: underline slides to new tab (spring, 200ms), list content fades in/out
- Milestone row tap: row expands to show "Mark as observed" action if not achieved; shows full post link if achieved
- Progress ring: animated fill on load (arc sweeps from 0 to current, 600ms ease-out)
- Add bottom sheet: spring slide-up from bottom (350ms)
 - AI banner: subtle fade-in on first load; tap scrolls/animates the relevant domain tab into view and flashes a soft outline around related milestones.

---

### Screen T-7: Profile / Settings

**Prompt for Google Stitch:**

Design the Profile & Settings screen for CadenceSprout's teacher app. Sunita accesses this from the bottom nav to manage her account and preferences. iPhone 14 Pro, 393×852pt, React Native, iOS-first.

**Navigation / Menu (hardcoded):**
- Render the bottom tab bar exactly as: `Feed | Attendance | Roster | Profile`
- Profile is active

**Layout:**
- Background: `#FAF7F2` (warm cream)
- Header: none (this is a tab, no back button); top of body serves as the visual header
- Bottom tab bar (Profile tab active in sage)
- Body: non-scrollable for first viewport; if content overflows, allow scroll

Content top to bottom (16dp horizontal padding throughout):

1. **Profile card** (white card, 12dp radius, 16dp padding, 16dp top gap): circular photo placeholder (72dp, sage green background with "S" initial for Sunita), right of photo: "Sunita Sharma" Inter Semibold 18sp `#1A1A1A`; below — "Class Teacher · LKG A" Inter Regular 14sp `#6B6B6B`; below — "Sunshine Preschool" Inter Regular 13sp `#9A9A9A`
   Right of card: a small `›` edit icon (16dp `#9A9A9A`) indicating tappable for profile edit

2. **Settings section** (16dp top gap): section header "Notifications" Inter Semibold 13sp `#9A9A9A` uppercase 11sp letter-spacing

   Setting rows (same white card, rows separated by 1dp dividers `#E8E2D9`):
   - "New parent comment" row: label Inter Regular 15sp `#1A1A1A`, right: iOS-style toggle (on, sage green)
   - "Daily attendance reminder" row: same style, toggle on, sage green
   - "Post published confirmation" row: toggle off (`#E8E2D9`)

3. **About section** (12dp top gap): section header "About" same style
   - "App version" row: label left, "v1.0.0" Inter Regular 14sp `#9A9A9A` right, no chevron
   - "Privacy Policy ›" row: label sage green, chevron right
   - "Terms of Service ›" row: same

4. **Log Out button** (24dp top gap): full-width outlined button (48dp, 1.5dp border `#C0392B`, 8dp radius, "Log Out" Inter Semibold 16sp `#C0392B`, no fill — white/transparent background)

**Colors & Typography:** Warm cream, white cards, sage toggles, red logout — clear visual hierarchy, all Inter

**States:**

*Default:* As above, notifications on/on/off

*Toggle tap:* Toggle animates between on (sage green thumb right) and off (grey thumb left), spring animation 200ms, saves preference immediately (no save button needed)

*Log Out tap:* Confirmation alert (iOS native alert style): "Log out of CadenceSprout?" with [Cancel] (default) and [Log Out] (red destructive). On confirm: session cleared, transition to T-0 Login screen

*Profile edit (tap edit icon):* Navigate to edit screen (or in-place field editing): name field, photo picker, read-only class + school

*Dark mode:* Background `#1A1A1A`, profile card + settings card `#242424`, section headers `#9A9A9A`, dividers `#333333`, text `#F5F2EC`, toggles: on = `#7AAF8C`, off = `#444444`

**Interactions & Animations:**
- Tab arrives: profile card fades in (150ms), settings rows stagger-fade in (80ms each)
- Toggle: haptic light on change
- Log Out confirm: transition to Login with a full fade (400ms) — not a slide (implies session reset, not navigation)
- Privacy/Terms links: open in-app browser (SFSafariViewController)

---

### Screen T-2A: Manual Child Tag Picker

**Prompt for Google Stitch:**

Design a bottom-sheet child tag picker for CadenceSprout's teacher app. This sheet opens from the Post Composer when AI tagging is missing or incorrect. The design should feel quick, confidence-building, and teacher-friendly on a busy classroom day.

**Navigation / Menu (hardcoded):**
- No separate menu inside this bottom sheet
- Inherit teacher app navigation context from the invoking screen: `Feed | Attendance | Roster | Profile`

**Layout:**
- iPhone 14 Pro viewport, presented as a bottom sheet over a dimmed Post Composer background
- Sheet height: ~78% of screen, white surface `#FFFFFF`, top corners 20dp radius
- Top handle: 4×36dp pill in `#E8E2D9`, centered, 10dp from top
- Header row: left "Cancel" in Inter Regular 15sp `#6B6B6B`, center title "Tag children in this post" Inter Semibold 16sp `#1A1A1A`, right [Done] text button in sage `#5C8B6E`
- Body padding: 16dp horizontal
- Search field at top: 48dp tall, outlined, 10dp radius, search icon 16dp, placeholder "Search by child name"
- Scrollable child roster list below:
  - Each row 60dp tall, white background
  - Left: 36dp circular avatar/photo
  - Middle: child name Inter Medium 15sp `#1A1A1A`
  - Right: empty circle selector or filled sage check chip when selected
- Selected tray pinned above footer: horizontal row of selected child chips in solid sage green with white text

**States:**

*Default:* Full roster list, no child selected, Done button disabled at 50% opacity

*Search active:* Keyboard up, filtered roster list updates live

*Selection made:* One or more selected chips appear in tray, Done button enabled

*No results:* Warm empty state with small magnifier icon and copy "No children found for 'Ria'" in Inter Regular 14sp `#9A9A9A`

*Loading:* Skeleton list rows with avatar circles + text bars

*Dark mode:* Sheet `#242424`, dim overlay deeper, rows `#242424`, text `#F5F2EC`, borders `#333333`, selected chips `#7AAF8C`

**Interactions & Animations:**
- Sheet slides up with spring animation (350ms)
- Selecting a child animates check indicator and adds chip to tray with scale-in
- Done closes sheet and returns selected chips to Post Composer
- Clear selection via chip `x` icon removes child with fade-out

---

### Screen T-5A: Child Detail

**Prompt for Google Stitch:**

Design a mobile child detail screen for CadenceSprout's teacher app. This screen opens when a teacher taps a child in the class roster. It should feel informative and warm, like a single child's living classroom profile.

**Navigation / Menu (hardcoded):**
- Keep teacher app navigation context as `Feed | Attendance | Roster | Profile`
- Use back navigation in the header; do not add child-specific tabs

**Layout:**
- iPhone 14 Pro viewport, portrait
- Background `#FAF7F2`
- Native-style header with back chevron left, title "Child Profile" centered, more icon right
- Scrollable body, 16dp horizontal padding
- Top profile card:
  - White card, 16dp radius, 18dp padding
  - Top row: 72dp child photo, right side child name in Fraunces Regular 24sp `#1A1A1A`
  - Subtext: age, DOB, class name in Inter Regular 14sp `#6B6B6B`
- Parent section card:
  - Section title "Family Contacts" uppercase Inter Semibold 11sp `#9A9A9A`
  - Parent rows with relationship label, phone number, status badge
  - Quick action icons for call and WhatsApp on each row
- **Timeline card (core child timeline view):**
  - Section title "Timeline" Inter Semibold 13sp `#9A9A9A`.
  - Vertical timeline running down the left (thin `#E8E2D9` line with small circles for each event).
  - Each event row shows, in chronological order:
    - Date (e.g., "24 Mar") and type pill ("Post" or "Milestone") on the left.
    - For Post events: thumbnail, short caption, and link text "Open post ›".
    - For Milestone events: milestone name ("Counts to 10 correctly"), domain chip (e.g., "Cognitive"), and link text "View milestone ›".
  - Show at least 5–6 mixed events (posts and milestones) to emphasize the combined view.
- Milestone summary card (optional, below Timeline if space):
  - Compact domain bars or rings summarizing coverage.
  - CTA row: "View full milestone tracker ›".

**States:**

*Normal:* All cards visible with parent info, milestone summary, recent posts

*No parent linked:* Parent card shows warm empty state: "No parent contact added yet." with muted illustration

*No recent posts or milestones:* Timeline card shows a warm empty state: "This child’s stories and milestones will appear here once you start posting and logging observations." with a small illustration.

*Loading:* Skeleton header card, skeleton parent rows, skeleton post previews

*Dark mode:* Background `#1A1A1A`, cards `#242424`, text `#F5F2EC`, dividers `#333333`

**Interactions & Animations:**
- Back returns to roster with slide-right transition
- WhatsApp icon opens external WhatsApp deep link
- Tapping a **Post** event opens T-3 Post Detail
- Tapping a **Milestone** event opens T-6 filtered to that milestone
- View full milestone tracker CTA also pushes to T-6

---

### Screen T-6A: Milestone Picker

**Prompt for Google Stitch:**

Design a milestone picker bottom sheet for CadenceSprout's teacher app. The picker is used to browse and attach NEP 2020 milestones without overwhelming the teacher. It should feel structured, educational, and lightweight.

**Navigation / Menu (hardcoded):**
- No separate menu inside this bottom sheet
- Inherit teacher app navigation context from the invoking screen: `Feed | Attendance | Roster | Profile`

**Layout:**
- Presented as a bottom sheet over either the Post Composer or Child Milestone Tracker
- Sheet height ~82% of screen, white surface, 20dp top corners
- Header: "Select milestone" centered, Cancel left, [Add] right in sage green
- Search field below header: 48dp outlined input, placeholder "Search milestones"
- Domain tab row below search:
  - 5 horizontally scrollable pills: Physical, Cognitive, Language, Social-Emotional, Aesthetic
  - Active pill filled sage green with white text; inactive pills white with sage border/text
- Scrollable list of milestone rows:
  - Title Inter Medium 15sp `#1A1A1A`
  - Domain/age metadata in Inter Regular 12sp `#9A9A9A`
  - Checkbox or selected state on right
- Selected tray pinned above footer with compact selected milestone count and chips

**States:**

*Default:* Domain tabs visible, list populated, Add button disabled

*Search active:* Filtered results update live

*Selection made:* Add button enabled, selected tray visible

*No results:* Educational empty state with copy "No milestones found for your search."

*Loading:* Skeleton pills + skeleton list rows

*Dark mode:* Sheet `#242424`, text `#F5F2EC`, inactive pills dark with `#333333` border, active pill `#7AAF8C`

**Interactions & Animations:**
- Tab switches animate underline/fill transition 180ms
- Selecting a milestone animates checkbox fill + tray chip insertion
- Add button returns selected milestones to source screen
- Sheet closes with spring slide-down

---

### Screen T-8: Daily Report Form

**Prompt for Google Stitch:**

System Intent:
- Offer a **gentle, optional** way to add structure to the day without interrupting posting.
- Keep completion time under ~30 seconds for a basic class-level report.
- Make it clear what’s shared with parents while keeping the tone light and non-bureaucratic.

Note: This feature must never block core posting flow.

Design a **lightweight, optional Daily Report form** for CadenceSprout's teacher app. This form lets Sunita add a structured end-of-day summary for the class (and optionally per child) **without slowing down** her core posting loop. It is a bottom-sheet modal launched from the Home Feed (T-1) or Post Composer (T-2).

**Navigation / Menu (hardcoded):**
- No separate menu inside this modal.
- Inherit teacher app navigation context from the invoking screen: `Feed | Attendance | Roster | Profile`.
- The Daily Report is **optional and non-blocking** — Sunita can always close it and continue posting normally.

**Layout:**
- iPhone 14 Pro viewport, presented as a bottom sheet over T-1 or T-2.
- Sheet height ~80% of screen, white surface `#FFFFFF`, top corners 20dp radius, dimmed warm-cream backdrop.
- Top handle: 4×36dp pill `#E8E2D9`, centered 10dp from top.
- Header row (56dp, 16dp horizontal padding):
  - Left: "Cancel" text button, Inter Regular 15sp `#6B6B6B` (closes sheet, [SYSTEM] auto-saves draft silently according to the Drafts rules in the System Design).
  - Center: title "Daily report" Inter Semibold 16sp `#1A1A1A`.
  - Right: primary text button **[Save]** in `#5C8B6E` (enabled once a minimum set of fields is filled).
- Body: vertically scrollable, 16dp horizontal padding, warm cream `#FAF7F2` background behind cards.

Content top to bottom:
1. **Context strip** (white card, 12dp radius, 12dp padding):
  - Left: class + date line: "LKG A · Today" Inter Regular 13sp `#6B6B6B`.
  - Right: small privacy label pill: lock icon + "Visible to parents" Inter Regular 11sp `#6B6B6B` (Compliance UX rule: clarify sharing scope).

2. **Quick overall summary** card:
  - White card, 12dp radius, 16dp padding.
  - Label: "Today in class" Inter Semibold 13sp `#6B6B6B`.
  - Multiline text area (3–5 lines), Fraunces Italic 15sp `#1A1A1A`, placeholder: "One or two lines about how the day felt…".
  - Subtext below in Inter Regular 12sp `#9A9A9A`: "Optional · Parents will see this in their daily summary".

3. **Structured daily fields** (chips + very short pickers — ERP must feel light):
  - Section label: "Quick details (optional)" Inter Semibold 13sp `#6B6B6B`.
  - A slim helper row at the top right of this section (only when a previous day's report exists) with a subtle text button "Use yesterday's format" Inter Regular 12sp `#5C8B6E` that, when tapped, pre-selects the same meals/naps/activities structure and defaults from the last report.
  - Three compact white cards stacked with minimal inputs:
    - **Meals:** segmented controls or chips (e.g., "Ate well", "Ate less", "Special snack"). Only one required; allow multi-select.
    - **Naps / Rest:** toggle row "Nap time today" with radio options: `No naps · Short naps · Good rest`.
    - **Activities:** small chips row (e.g., "Art", "Outdoor", "Story time", "Music"); allow multi-select.
  - Keep each card to **one line of controls + a short helper line**, no long forms.

4. **Per-child notes (strictly optional):**
  - Collapsible card titled "Add notes for specific children (optional)" with a right chevron.
  - When expanded: vertical list of up to 3 child chips (e.g., those frequently tagged today) with tiny note icon.
  - Tapping a child opens a **micro-note row** in place (single-line text input, Inter 13sp, max 80 chars) — think WhatsApp status length, not a full report.

5. **Link to incidents (if any):**
  - Subtle row at the bottom: small alert icon + "Log an incident from today" text link in `#C4784A` that opens T-9 Incident Report Form.
  - Helper copy: "Only for notable safety/behaviour events" in Inter Regular 11sp `#9A9A9A`.

**Colors & Typography:**
- Use the existing warm palette; keep cards and inputs visually light.
- Fraunces only for the free-text summary; all structured UI (chips, pickers, labels) uses Inter.

**States:**

*Default (empty but gentle):*
- Summary field empty; quick fields unselected; Save disabled at 60% opacity.
- A small helper line above the first card: "Optional — takes under 30 seconds" in Inter Regular 12sp `#9A9A9A` (Teacher prompt rule: **keep posting flow fast**).

*Partially filled:*
- At least one of: summary, meals, naps, activities, or child note is filled.
- Save becomes enabled, primary color `#5C8B6E`.

*Saved for today:*
- On Save, sheet dismisses with a success toast on T-1: "Daily report saved for parents" in a soft sage banner.
- Re-opening Daily Report for today loads previous values for quick edits.
 - When a previous day’s report exists, "Use yesterday's format" appears as a shortcut in the Quick details section to reuse that structure and defaults.

*Skip / Cancel:*
- Cancel closes the sheet without nagging; microcopy on T-1 remains light: e.g., "You can add a daily report anytime".

*Offline:*
- Inline banner at top of sheet: wifi-off icon + "Offline — this will sync when you're back online" in Inter Regular 12sp white on terracotta `#C4784A`.
  - [SYSTEM] Offline sync, queuing, and retry behavior follow the System Design document (Section 5); this prompt only defines the visual banner.

**Interactions & Animations:**
- Sheet slides up with spring animation (350ms); dimmed background on T-1/T-2.
- Chips and toggles use quick 150ms scale/fill transitions.
- Save tap: light haptic, sheet slides down; T-1 banner briefly pulses when the new daily report is saved.
- Per-child notes expand/collapse with 200ms height animation.

---

### Screen T-9: Incident Report Form

**Prompt for Google Stitch:**

System Intent:
- Support **calm, clear, and compliant** logging of incidents without overwhelming Sunita.
- Capture the minimum structured data admins need, with optional rich context when she has time.
- Make privacy and parent visibility explicit so teachers feel safe documenting sensitive events.

Note: This feature must never block core posting flow.

Design a **structured, compliance-aware Incident Report form** for CadenceSprout's teacher app. Sunita uses this to log safety or behaviour incidents for a child, often from the Child Detail screen (T-5A) or Post Composer (T-2). It must feel calm, clear, and quick — **not** like a heavy HR/ERP screen.

**Navigation / Menu (hardcoded):**
- No separate menu inside this modal.
- Inherit teacher navigation context from the invoking screen: `Feed | Attendance | Roster | Profile`.
- Opened as a full-height modal (or tall bottom sheet) over T-2 or T-5A; uses back/close for exit.

**Layout:**
- iPhone 14 Pro viewport, portrait.
- Full-screen modal with warm cream background `#FAF7F2`.
- Header (56dp, 16dp horizontal padding):
  - Left: back chevron `←` `#1A1A1A`.
  - Center: title "Log incident" Inter Semibold 16sp.
  - Right: primary text button [Save] in `#5C8B6E` (enabled once required fields are complete).
- Body: scrollable, 16dp horizontal padding.

Content blocks:
1. **Child & context card** (white, 12dp radius, 16dp padding):
  - Child avatar + name (e.g., "Rohan"), class ("LKG A"), Inter typographic style consistent with T-5A.
  - If launched from Child Detail, child is preselected and non-editable.
  - Small link "Change child" if launched from T-2, opening a compact child picker.

2. **Incident basics** card:
  - Label row: "Incident details" Inter Semibold 13sp `#6B6B6B`.
  - **Type**: horizontal chip group (e.g., "Minor injury", "Behaviour", "Medical", "Other"), single-select.
  - **Date & time**: inline fields with date picker + time picker, defaulting to "Today" and current time.
  - **Location**: simple text field with placeholder "Classroom, playground, bus…".

3. **Description & actions taken:**
  - Multiline text area (4–6 lines), Fraunces Regular 15sp `#1A1A1A`, placeholder: "What happened, and what did you do?".
  - Optional short field "First aid / support given" Inter Regular 13sp `#6B6B6B` with smaller text box.

4. **Severity & follow-up:**
  - Severity radio group in a small white card: `Low · Medium · High` with gentle color cues (Low = grey, Medium = amber, High = terracotta outline, **no** alarming full-red fills).
  - Checkbox: "Admin should review this" (Admin UX hook, but still teacher-friendly copy).

5. **Parent notification & privacy (Compliance UX):**
  - White card with lock icon and title "Sharing" Inter Semibold 13sp.
  - Row with toggle: "Notify parent now"; when on, show short info text: "Parent will see this incident in their app".
  - Small privacy footnote below in Inter Regular 11sp `#9A9A9A`: "Visible to school staff and this child's parents. Not visible to other parents." (Compliance rule: clear **privacy label**).

**Colors & Typography:**
- Same warm palette; avoid harsh reds.
- Structured form text in Inter; free-text description in Fraunces for warmth.

**States:**

*Default:* Required fields empty, [Save] disabled, helper copy at top: "For notable safety or behaviour events only" in Inter Regular 12sp `#9A9A9A`.

*Ready to save:* Type, date/time, description, and child selected; Save enabled.

*Saved (no parent notification):*
- Toast at bottom: "Incident saved to record" on sage background.
- Incident appears in child timeline (T-5A) and admin views, but **no** parent notification is sent.

*Saved with parent notification ON:*
- Toast: "Incident saved and shared with parent".
- Connects to parent Incident History (P-11); triggers calm notification copy.

*Validation errors:* Inline red messages for missing required fields, e.g., "Add a short description of what happened".

*Offline:* Banner like T-2/T-8: "Offline — will sync when you're back online".
  - [SYSTEM] Offline queuing and retry semantics are defined centrally in the System Design; this screen simply reuses the shared offline banner pattern.

**Interactions & Animations:**
- Smooth field focus scrolls the form so labels never hide under the keyboard.
- Save tap: medium haptic, modal dismiss with slide-down.
- Severity selection & toggles animate fill/outline in 150ms.

---

*End of Section 4.1 — 13 screens (T-0 through T-9, plus T-2A, T-5A, T-6A)*

---

## Section 4.2 — Parent App (Mobile)

---

### Screen P-0: Parent App Phone Entry / OTP Request

**Prompt for Google Stitch:**

Design a mobile phone number entry and OTP request screen for CadenceSprout's parent app. This is the first native app screen a parent sees after tapping "Get the app" from a WhatsApp magic-link flow. The goal is to feel warm, premium, and friction-light, like a boutique school app rather than a banking or telecom OTP screen.

**Navigation / Menu (hardcoded):**
- No persistent parent menu on this pre-auth screen
- Do not show `Feed | Milestones | Portfolio | Profile` yet

**Layout:**
- iPhone 14 Pro viewport (393×852pt), portrait orientation
- Background: `#FAF7F2` (warm cream), full bleed
- Safe area respected; content vertically arranged with generous breathing room
- Top 20% of screen: warm branded welcome block
  - Circular school logo placeholder (72×72dp) centered — sun + leaf motif in warm yellow `#F5C842` and sage green `#5C8B6E`
  - 12dp below: "Sunshine Preschool" in Inter Semibold 14sp `#6B6B6B`, centered
  - 20dp below: "See every update from your child's day" in Fraunces Regular 28sp `#1A1A1A`, centered, max width 300dp, 120% line-height
  - 12dp below: supporting copy in Inter Regular 15sp `#6B6B6B`, centered: "Enter your phone number to get a one-time code and continue."
- Middle content block (24dp horizontal padding, 32dp top gap from hero):
  - White surface card, 16dp radius, 20dp padding, subtle shadow (`0 2px 8px rgba(0,0,0,0.06)`)
  - Phone number label in Inter Semibold 13sp `#6B6B6B`
  - 8dp gap
  - Phone number input: full width, 52dp tall, outlined 1.5dp border `#E8E2D9`, 10dp radius
    - Left fixed prefix area: `+91` in Inter Regular 15sp `#6B6B6B`
    - Vertical divider after prefix
    - Input placeholder: "Phone number" in Inter Regular 15sp `#9A9A9A`
  - 12dp gap
  - Legal footnote: Inter Regular 12sp `#9A9A9A`, 140% line-height: "By continuing, you agree to receive a one-time verification code by SMS."
  - 20dp gap
  - [Send OTP] primary button: full width, 52dp tall, 10dp radius, fill `#5C8B6E`, label Inter Semibold 16sp white
  - 12dp gap
  - Secondary text link centered: "Open via WhatsApp link instead" in Inter Medium 14sp `#C4784A`
- Bottom area pinned above home indicator:
  - Small reassurance row centered with shield/check icon 14dp in sage and text "Private by design. Your child's data stays protected." in Inter Regular 12sp `#9A9A9A`

**Colors & Typography:**
- Background `#FAF7F2`
- Surface `#FFFFFF`
- Primary action `#5C8B6E`
- Accent link `#C4784A`
- Text primary `#1A1A1A`
- Text secondary `#6B6B6B`
- Dividers/borders `#E8E2D9`
- Headline uses Fraunces; all interactive and support text uses Inter

**States (include all as artboard variants or annotated states):**

*Default:* Empty phone field, Send OTP button disabled at 55% opacity, no error text

*Typing:* Numeric keypad visible, input border becomes 2dp sage green `#5C8B6E`, Send OTP button enabled once a valid 10-digit Indian number is entered

*Loading:* Send OTP button shows a white spinner (20dp) replacing the label, field disabled at 50% opacity, no full-screen loader

*Invalid number:* Inline error below input in Inter Regular 13sp `#C0392B`: "Enter a valid phone number." Input border turns red `#C0392B`

*Send failed:* Full-width inline error banner inside the card, 10dp radius, pale terracotta background `#F7E3D8`, left error icon 16dp terracotta, text `#A14F2A`: "We couldn't send your code. Please try again."

*Success / OTP sent:* Brief success banner in soft sage background `#E7F2EA` with check icon + text "Code sent to +91 98XXXX3210", then transition to OTP verification screen

*Dark mode:* Background `#1A1A1A`, card `#242424`, headline `#F5F2EC`, body text `#9A9A9A`, input border `#333333`, primary button `#7AAF8C`, accent link `#D4875A`

**Interactions & Animations:**
- Screen load: logo and headline fade/slide up together (250ms), card follows with slight stagger (120ms delay)
- Input focus: border color transition 150ms ease, card shifts upward slightly to accommodate keyboard
- Send OTP tap: button scales to 0.97 on press with light haptic feedback
- Success: success banner fades in, then whole screen transitions with fade + slide-left to OTP verification (300ms)
- WhatsApp link tap: opens external deep link or web fallback, not an in-app browser

---

### Screen P-0A: Parent App OTP Verification

**Prompt for Google Stitch:**

Design a mobile OTP verification screen for CadenceSprout's parent app. This screen immediately follows phone number entry. It should feel calm, trustworthy, and premium, not transactional or banking-like. The parent should feel they are one short step away from seeing their child's updates.

**Navigation / Menu (hardcoded):**
- No persistent parent menu on this pre-auth screen
- Do not show `Feed | Milestones | Portfolio | Profile` yet

**Layout:**
- iPhone 14 Pro viewport (393×852pt), portrait orientation
- Background: `#FAF7F2` warm cream
- Safe area respected; vertically centered content with generous whitespace
- Top area:
  - Small back chevron at top-left, 24dp, `#6B6B6B`
  - 28dp below: headline in Fraunces Regular 30sp `#1A1A1A`, centered: "Enter your code"
  - 12dp below: supporting text in Inter Regular 15sp `#6B6B6B`, centered, max width 300dp: "We sent a 6-digit code to +91 98XXXX3210"
- Main card centered on screen with 24dp horizontal padding:
  - White card, 16dp radius, 24dp padding, subtle shadow
  - OTP input row centered: 6 individual boxes, each 44×52dp, 10dp radius, 1.5dp border `#E8E2D9`, white fill, 10dp gap between boxes
  - Each OTP digit uses Inter Semibold 22sp `#1A1A1A`, centered
  - 16dp gap
  - Countdown / helper row centered: "Resend in 00:24" in Inter Regular 13sp `#9A9A9A`
  - 20dp gap
  - [Verify OTP] primary button, full width, 52dp height, 10dp radius, fill `#5C8B6E`, label Inter Semibold 16sp white
  - 12dp gap
  - Secondary text link centered: "Change phone number" in Inter Medium 14sp `#C4784A`
- Bottom reassurance note above home indicator: lock icon 14dp + "Secure sign in for your child's private feed" in Inter Regular 12sp `#9A9A9A`

**Colors & Typography:**
- Same CadenceSprout parent palette as P-0
- Fraunces only for the headline
- Inter for inputs, buttons, helper text, links

**States (include all as artboard variants or annotated states):**

*Default:* Empty OTP boxes, Verify button disabled at 55% opacity

*Typing:* Active box border becomes 2dp sage green `#5C8B6E`, entered boxes show digits, focus auto-advances

*Loading:* Verify button shows white spinner; OTP boxes disabled at 50% opacity

*Invalid OTP:* Inline error under OTP row in Inter Regular 13sp `#C0392B`: "That code is incorrect or expired." All boxes keep current digits, borders turn red

*Resend available:* Timer reaches zero, helper row becomes tappable text link in terracotta `#C4784A`: "Resend code"

*Success:* A small success banner appears inside the card: soft sage background, check icon, text "Verified", then transition to consent or feed

*Dark mode:* Background `#1A1A1A`, card `#242424`, boxes `#242424`, borders `#333333`, digits `#F5F2EC`, button `#7AAF8C`, helper text `#9A9A9A`

**Interactions & Animations:**
- Auto-advance to next OTP box on digit entry
- Full-code paste fills all 6 boxes instantly
- Verify tap scales button to 0.97 with light haptic feedback
- Success transitions with fade + slide-left to next screen (300ms)
- Back tap returns to P-0 with slide-right transition

---

### Screen P-1: Magic-Link Web View (Feed First)

**Prompt for Google Stitch:**

Design the P-1 Magic-Link Web View screen for CadenceSprout. This is a frictionless mobile web view accessed directly from a WhatsApp link, allowing parents to see their child's latest update instantly without installing the app or logging in.

**Navigation / Menu (hardcoded):**
- No persistent menu on this screen.
- Because this is a pre-auth web view, do not include any bottom tab bar, top hamburger menu, or side drawer.

**Layout:**
- iPhone 14 Pro viewport (393×852pt), portrait orientation.
- Background: `#FAF7F2` (warm cream), full bleed.
- Header (64dp tall, no background, 1dp bottom border `#E8E2D9`): Centered block containing the school logo (circular 32×32dp placeholder with a warm yellow `#F5C842` and sage green `#5C8B6E` sun+leaf motif), followed immediately below by "Powered by CadenceSprout" in Inter Regular 12sp `#9A9A9A`.
- Body: Vertically scrollable, with 16dp horizontal padding around content.
- Floating soft install banner (conditional): Anchored to the bottom of the viewport, 16dp above the bottom edge.

**UI Elements (Primary Post Card):**
- Card container (white surface `#FFFFFF`, 12dp border radius, 2dp shadow `elevation: 2` or `box-shadow: 0 2px 4px rgba(0,0,0,0.05)`).
- Full-bleed photo: 4:3 aspect ratio (e.g., 361dp wide × 270dp tall) anchored to the top of the card with top 12dp border radii. Placeholder image: A vibrant preschool activity like finger painting.
- Card Body (below photo, 16dp padding on all sides):
  - Caption: Fraunces Italic 18sp `#1A1A1A`. Example text: "Aarav had a wonderful time exploring colors today! 🌱"
  - 12dp gap.
  - Child Name Tag: Solid pill (28dp tall, 8dp radius), fill `#5C8B6E`, text "Aarav" in Inter Regular 12sp `#FFFFFF`.
  - 16dp gap.
  - Action Row: Circular ❤️ reaction button (44×44dp, `#FAF7F2` background, 20dp heart icon in `#9A9A9A` for default, `#C0392B` for liked). Next to it, text "React to this moment" in Inter Regular 13sp `#6B6B6B`.

**UI Elements (Soft Install Banner):**
- Floating card anchored at the bottom: 12dp radius, `#FFFFFF` background, 4dp shadow (`box-shadow: 0 4px 12px rgba(0,0,0,0.1)`), 16dp padding all around.
- Left side: "Get the app for all of Aarav's updates" in Inter Semibold 14sp `#1A1A1A`, max width 200dp.
- Right side: [Get App] button, 36dp tall, 8dp radius, fill `#5C8B6E`, text Inter Semibold 13sp white.
- Dismiss icon: Small '✕' (16dp, `#9A9A9A`) in the top right corner.

**Colors & Typography:**
- Background `#FAF7F2`, Surface `#FFFFFF`, Primary `#5C8B6E`, Accent (Heart) `#C0392B`.
- Fraunces (serif) only for the caption text. Inter (sans-serif) for all other UI labels and helper copy.

**States (include all as artboard variants or annotated states):**

*First visit (Default):* Header and post card visible. Soft install banner is hidden. Heart icon is outline `#9A9A9A`.

*Reacted State:* Heart icon fills solid `#C0392B`.

*Seen 3+ times:* Floating soft install banner appears at the bottom.

*Expired token:* Post card is hidden. Centered in the body is the text "This link has expired. Ask your school to send a new one." in Inter Regular 16sp `#1A1A1A`. Below it, a full-width primary button "Contact School via WhatsApp" (48dp tall, 8dp radius, fill `#5C8B6E`, text white Inter Semibold 16sp).

*Dark mode:* Background `#1A1A1A`, card surfaces `#242424`, primary text `#F5F2EC`, secondary text `#9A9A9A`, sage primary `#7AAF8C`, divider borders `#333333`.

**Interactions & Animations:**
- Reaction tap: Heart icon turns `#C0392B` instantly with a quick scale-bounce (1.0 → 1.3 → 1.0 over 200ms) and light haptic feedback.
- Banner dismiss (✕) tap: Banner slides down out of the viewport and fades (250ms ease-out).
- Get App tap: Normal button press state, then navigates to the app store.

---
### Screen P-2: DPDP Consent Screen

**Prompt for Google Stitch:**

Design a DPDP consent screen for CadenceSprout's parent mobile app. This screen appears immediately after OTP verification for a new parent and must clearly explain data usage and collect three granular consents, while feeling warm and trustworthy, not legalistic.

**Navigation / Menu (hardcoded):**
- No persistent parent menu yet; this is still part of onboarding.
- Do not show `Feed | Milestones | Portfolio | Profile` until the parent has made a choice.

**Layout:**
- iPhone 14 Pro viewport (393×852pt), portrait.
- Background: `#FAF7F2` (warm cream).
- Safe area respected; vertically scrollable body.
- Top header (56dp): back chevron left (24dp `#6B6B6B`), centered title "Your child's privacy" in Inter Semibold 16sp, no right action.
- Below header: warm intro block with child context:
  - Child avatar (56dp circle) + child name (e.g., "Aarav") and class ("Nursery A") in Inter.
  - Short reassuring copy in Inter Regular 14sp `#6B6B6B`: "You control how Aarav's photos and data are used. You can change this anytime."
- Main content card: white surface, 16dp radius, 20dp padding, 16dp vertical gap between consent rows.
  - Each consent row contains: title, description, and a toggle.
- Sticky bottom action bar: full-width [Continue] primary button and subtle "Not now" text link.

**Consent Rows (three separate switches):**
1. **Share updates in the app**
  - Description: "Allow the school to share photos and updates about your child with you inside CadenceSprout."
  - Toggle default: ON.
2. **Face recognition (optional)**
  - Description: "Use secure face recognition so teachers can quickly tag your child in group photos. You can turn this off anytime."
  - Toggle default: OFF (requires explicit opt-in).
3. **Store data in India**
  - Description: "Your child's data is stored securely in India (AWS Mumbai). We never sell data to third parties."
  - This may appear as read-only informational row with a check icon rather than a toggle, depending on legal guidance.

**States:**

*Default:* All rows visible. Share updates ON, face recognition OFF, storage row informational. Continue button enabled.

*Toggles changed:* Continue button remains enabled. Under the card, a tiny caption "You can change these anytime from Profile → Data & Privacy" in Inter Regular 11sp `#9A9A9A`.

*Face recognition turned OFF after being ON previously:* Confirmation modal explaining that existing Rekognition data will be deleted within 24 hours, with [Turn off & delete] (destructive) and [Keep on] (secondary) buttons.

*Dark mode:* Background `#1A1A1A`, card `#242424`, text `#F5F2EC`, dividers `#333333`, primary button `#7AAF8C`.

**Interactions & Animations:**
- Continue tap: light haptic, transition to P-3 Parent Home Feed.
- Toggles animate with 180ms spring.
- Modal appears with scale + fade.

---

### Screen P-3: Parent Home Feed

**Prompt for Google Stitch:**

System Intent:
- Tell an **emotional, story-like view** of the child’s day instead of a generic feed.
- Help parents feel caught up with **one glance** (summary first, then posts).
- Keep finance/compliance details out of the way so this screen always feels warm and joyful.

Metric:
- Primary: North Star (parents seeing ≥1 meaningful update per day), parent WAU.
- Secondary: Daily view rate for P-3/PW-2, average posts viewed per active parent session.

Design the Parent Home Feed screen for CadenceSprout's parent mobile app. This is Meera's daily landing page to see a warm story of her child's day, not just a reverse-chronological feed.

**Navigation / Menu (hardcoded):**
- Bottom tab bar must be exactly: `Feed | Milestones | Portfolio | Profile`.
- `Feed` is active.

**Layout:**
- iPhone 14 Pro viewport (393×852pt), portrait.
- Background: `#FAF7F2`.
- Top header (56dp): left — child avatar (32dp) + "Aarav" Inter Semibold 15sp; below name: "Sunshine Preschool" Inter Regular 12sp `#6B6B6B`; right — bell icon for notifications.
  - [SYSTEM] Bell unread state, notification count, and routing to P-7 are driven by the Notification System in the System Design; this prompt only defines icon placement and visual style.
- Directly below header: **Daily summary card** (white, 16dp radius, 16dp padding):
  - Title: "Today at school" in Fraunces Regular 18sp `#1A1A1A`.
  - 2–3 bullet points in Inter Regular 13sp `#6B6B6B`, e.g. "● Aarav explored colors with finger painting" / "● Outdoor playtime with friends".
  - Small footer line "Updated at 4:15 PM" in Inter Regular 11sp `#9A9A9A`.
  - If no posts today, card instead shows soft empty state: "No updates yet today — check back this evening." with a small illustration.
- Below summary: a narrow **"This week’s highlights" strip** (optional when there have been posts this week) — small label "This week" Inter Semibold 12sp `#6B6B6B` and one line of copy like "3 new moments from Aarav" Inter Regular 12sp `#6B6B6B`, optionally with 1–2 tiny thumbnail chips that scroll to those posts when tapped.
- Below that: **Today’s posts** section label "Today" Inter Semibold 13sp `#6B6B6B` and feed cards for today.
- Below today: previous days grouped with date headers: e.g. "Yesterday", "Mon, 24 Mar".
- Bottom: tab bar as specified.

**UI Elements (Post Card for Parent):**
- Similar to Teacher Home Feed but parent-focused:
  - Photo card (white card, 12dp radius, full-bleed 4:3 image on top).
  - Caption in Fraunces Italic 16sp.
  - Small line: "From Sunita · LKG A" Inter Regular 12sp `#6B6B6B`.
  - Below: pill "Aarav" (solid sage) if multiple children, show only this child’s tag.
  - Footer row: left — "2h ago"; right — reaction count (heart icon + "12") and comment count (speech bubble icon + "3").

**States:**

*Loading:* Summary card shows skeleton lines; feed list displays skeleton cards.

*No posts yet overall:* Instead of summary and feed, show centered illustration + copy: "Your child's stories will appear here once the school starts posting." and a line "Ask your school if CadenceSprout is set up for your class.".

*No posts for this child (recent week):* When the class is posting but there are no posts tagged for the currently selected child in the last 7 days, show a softer empty state in place of today's summary and this week's group: a friendly illustration and copy: "This week has been quiet so far" with a smaller line "If you're expecting updates, you can check with your school." and a secondary CTA button "Check with your school" that opens the default mail/SMS/WhatsApp chooser with the school contact prefilled.

*Multiple children:* Header becomes child-switcher pill row (e.g. chips with each child's name). Summary and feed update when switching.

*Dark mode:* Background `#1A1A1A`, cards `#242424`, text `#F5F2EC`, tabs on dark bar.

**Interactions & Animations:**
- Pull-to-refresh on feed.
- Post tap navigates to P-4 Post Detail with hero image expand.
- Daily summary card tap scrolls to first post for today.

---

### Screen P-4: Parent Post Detail

**Prompt for Google Stitch:**

Design the Post Detail screen for the parent app. Meera taps a post from the Home Feed to see it full-screen, react, and read comments.

**Navigation / Menu (hardcoded):**
- Keep parent navigation as `Feed | Milestones | Portfolio | Profile` with Feed active.
- Use a back chevron in the header; do not add extra tabs.

**Layout:**
- Background `#FAF7F2`.
- Header (56dp): back chevron left, center "Post" Inter Semibold 16sp, right — share icon (for system share sheet).
- Body: scrollable.

Content top to bottom:
1. Full-width photo (4:3, hero image).
2. Caption block: Fraunces Italic 18sp, then "From Sunita · LKG A" line.
3. Child chips: "Aarav" pill.
4. Engagement line: small text "You and 11 others reacted" with heart icon.
5. Comments section: list of parent comments, with parent avatar, name, comment text, timestamp.
6. Comment input area pinned at bottom when keyboard closed: text field "Add a comment…" + send icon.

7. **Report issue row:** A lightweight row at the end of the content stack (above the comment input) with a small flag icon and text button "Report incorrect tagging" in Inter Regular 13sp `#C4784A`. This should feel secondary and non-scary.

**States:**
- No comments yet: show "Be the first to react or comment".
- Reaction toggled: heart fills and animates.
- Dark mode variant consistent with P-3.

**Interactions & Animations:**
- Hero expand from feed thumbnail.
- Keyboard handling for comment input.
- Share icon opens system share.
 - Tapping **Report incorrect tagging** opens a simple confirmation sheet: title "Report an issue with this post", description "We'll notify the school admin so they can fix it.", a multiline optional text field, and primary [Send report] button. After sending, show a small toast "Thanks, we've shared this with the school.".

---

### Screen P-5: Milestone Progress

**Prompt for Google Stitch:**

Design the Milestone Progress screen for the parent app. Meera taps the `Milestones` tab to see how her child is progressing against NEP 2020 domains.

**Navigation / Menu (hardcoded):**
- Bottom tab bar: `Feed | Milestones | Portfolio | Profile`.
- `Milestones` is active.

**Layout:**
- Background `#FAF7F2`.
- Header: "Milestones" with child avatar + name.
- Body: vertical scroll.
- Top: summary card with ring charts per domain (Physical, Cognitive, Language, Social-Emotional, Aesthetic), each showing % completed.
- Below: timeline section "Recent milestones" with chips showing key achievements and dates.
- CTA row "View detailed tracker (teacher view)" indicating that detailed logging is teacher-led.

**States:**
- No milestones: friendly empty state explaining that milestones will appear as teachers log them.
- Dark mode variant.

---

### Screen P-6: Year-End Portfolio

**Prompt for Google Stitch:**

Design the Year-End Portfolio screen for the parent app. Meera can preview, download, and share a beautifully laid out PDF of her child's year.

**Navigation / Menu (hardcoded):**
- Bottom tab bar: `Feed | Milestones | Portfolio | Profile`.
- `Portfolio` is active.

**Layout:**
- Background `#FAF7F2`.
- Header: "Year-end portfolio" with child name.
- Body: preview card showing cover page thumbnail (photo collage + title), short description of what’s inside, and key stats (e.g., "85 posts · 24 milestones tagged").
- Buttons: [View PDF] primary, [Download] secondary, [Share] tertiary.

**States:**
- Not ready yet: card shows skeleton + text "Your portfolio is being prepared. We'll notify you when it’s ready.".
- Ready: full preview + enabled buttons.
- Dark mode variant.

---

### Screen P-7: Notifications

**Prompt for Google Stitch:**

Design the Notifications screen for the parent app, listing chronological updates like new posts, comments, announcements, and portfolio readiness.

[SYSTEM] This screen displays notifications provided by the Notification System (as per the System Design, Section 5B). All trigger rules (what generates a notification, batching into digests vs. instant pushes, and read/unread state) are defined there; this prompt only specifies how those items are rendered and grouped.

**Navigation / Menu (hardcoded):**
- Accessible from bell icon on P-3; keep `Feed` tab active.

**Layout:**
- Background `#FAF7F2`.
- Header: back chevron + title "Notifications".
- Body: grouped notifications by day ("Today", "Yesterday"). Each row shows icon, title (e.g., "New post from LKG A"), snippet, and timestamp.

**States:**
- All caught up: illustration + "You're all caught up" message.
- Unread notifications highlighted with slightly stronger background.

---

### Screen P-8: Profile / Data & Privacy

**Prompt for Google Stitch:**

Design the Profile and Data & Privacy screen for the parent mobile app, where Meera can update basic info and manage DPDP-related settings.

**Navigation / Menu (hardcoded):**
- Bottom tab bar: `Feed | Milestones | Portfolio | Profile`.
- `Profile` is active.

**Layout:**
- Background `#FAF7F2`.
- Top profile card: parent name, masked phone, school name, linked child chips.
- Settings sections:
  - Notifications (toggles for post alerts, daily digest).
    - [SYSTEM] The meaning of each toggle (which events generate alerts vs. daily digest and at what times) is defined by the Notification System in the System Design; this screen only exposes the switches.
  - Data & Privacy (row linking to a mobile privacy detail view mirroring PW-6 behaviour).
  - About & Support (privacy policy, terms, contact support).
  - Log Out button.

**States:**
- Default, loading, and dark mode variants similar to PW-5.

---

### Screen P-9: Fees & Payments

**Prompt for Google Stitch:**

Design a **simple, trust-building Fees & Payments screen** for the parent mobile app. Meera views all invoices, sees what’s overdue, and can **Pay Now** with clear trust indicators — without feeling like she’s in a complex finance app.

**Navigation / Menu (hardcoded):**
- Bottom tab bar: `Feed | Milestones | Portfolio | Profile` (unchanged).
- `Profile` remains the active tab when this screen is opened from a "Fees" row in P-8 or from a soft banner in the feed.
- Use a back chevron in the header to return to the previous screen; do **not** add a new bottom tab for Fees.

**Layout:**
- Background `#FAF7F2`.
- Header (56dp): back chevron left, centered title "Fees & payments" Inter Semibold 16sp, no right action.
- Body: scrollable area with 16dp horizontal padding.

Content top to bottom:
1. **Summary hero card (light, non-dashboard):**
  - White card, 16dp radius, 16dp padding.
  - Line 1: "Total due" Inter Regular 12sp `#6B6B6B`.
  - Large amount text (e.g., "₹12,500") in Fraunces Regular 24sp `#1A1A1A`.
  - Subtext: next due date or "All caught up" in Inter Regular 13sp.
  - If there are overdue invoices, show a small terracotta pill in the top-right: "Overdue" `#C4784A` with white text.

2. **Trust strip (Financial UX rule):**
  - Narrow row below hero card, lock icon 14dp + text "Secure UPI payment · Encrypted and handled by trusted providers" in Inter Regular 11sp `#9A9A9A`.

3. **Invoice list (cards, not tables):**
  - Vertical list of white cards, 12dp radius, 12dp padding, 8dp gap.
  - Each card shows:
    - Top line: Month / period (e.g., "April 2026 fees") Inter Semibold 14sp `#1A1A1A`.
    - Second line: "Child · Class" ("Rohan · LKG A") Inter Regular 12sp `#6B6B6B`.
    - Third line: amount on the left ("₹3,500"), due date on the right ("Due 10 Apr").
    - Status pill at bottom-left:
     - **Paid:** pill `#E8F4EC` with text `#4A8C5C` "Paid".
     - **Pending:** pill `#F0EBE3` with text `#6B6B6B` "Pending".
     - **Overdue:** pill `#FEF3E7` with text `#C4784A` "Overdue" and a thin terracotta left border.
    - Primary CTA at bottom-right for **Pending** or **Overdue** invoices: solid sage button 40dp tall, 8dp radius, label **"Pay Now"** in Inter Semibold 14sp white.

4. **Light filters (optional):**
  - Compact filter chip row pinned above invoice list: `All | Pending | Overdue | Paid` — single-select, horizontally scrollable if needed.

**Colors & Typography:**
- Keep warm, editorial feel; avoid dense tables.
- Use Fraunces only for the summary amount; invoice details and CTAs use Inter.

**States:**

*All caught up:*
- Summary hero shows "Total due ₹0" and text "You’re all caught up".
- Below, a soft illustration and copy: "We’ll let you know whenever there’s something to pay." No invoice cards.

*Upcoming fee due soon (e.g., in 3 days):*
- Summary hero shows the total upcoming amount and subtext like "Next payment due in 3 days".
- Upcoming invoice cards show a neutral **"Due soon"** pill (e.g., light neutral background with calm grey text) instead of "Pending" to avoid sounding late.
- Do **not** use alarming colors; keep copy calm: "You’ll get a reminder if this isn’t paid on time." with the same **Pay Now** CTA available.

*Mixed statuses:*
- Some Paid, some Pending, some Overdue; Overdue cards visually stand out but do not use alarming copy.

*Overdue-focused:* (filter = Overdue)
- Only overdue cards visible; total overdue amount highlighted in summary hero subtext.

*Payment in progress:*
- When Meera taps **"Pay Now"**, open a bottom sheet with payment method selection and show a small trust badge again.
- The Pay Now button switches to a spinner + "Processing…" state.

**Interactions & Animations:**
- Filter chip taps animate selection with 150ms background/fill transition.
- Pay Now tap: button scale 0.97 on press + light haptic.
- On payment success, show a soft sage banner at top: "Payment received" and morph the card’s status pill from Overdue/Pending to Paid with a quick color transition.

---

### Screen P-10: Documents & Records

**Prompt for Google Stitch:**

Design a **calm, organized Documents & Records screen** for the parent mobile app. Meera can view and download important documents related to her child (admissions forms, ID proofs, medical info, school policies). It should feel like a **safe drawer**, not a technical document manager.

**Navigation / Menu (hardcoded):**
- Bottom tab bar: `Feed | Milestones | Portfolio | Profile`.
- Accessed from P-8 (Profile / Data & Privacy) via a "Documents & records" row; keep `Profile` as active tab.
- Use a back chevron in the header; no new tabs.

**Layout:**
- Background `#FAF7F2`.
- Header (56dp): back chevron left, title "Documents & records" centered.
- Body: 16dp horizontal padding, scrollable.

Content:
1. **Intro text:**
  - Short, reassuring copy at top: "Your child’s important documents, in one safe place" in Inter Regular 14sp `#6B6B6B`.

2. **Sectioned list of documents:**
  - Use section headers (Inter Semibold 12sp `#9A9A9A`, uppercase) like:
    - "Admissions & identity"
    - "Medical & permissions"
    - "School policies".
  - Under each section, show white row cards (no heavy table grids):
    - Left: icon (PDF sheet, image, shield, etc.) 24dp.
    - Middle: document title in Inter Medium 14sp `#1A1A1A` and smaller subtitle (e.g., "Uploaded 5 Mar 2026") in 12sp `#6B6B6B`.
    - Right: compact pill button "View" (outlined sage) and secondary icon button for download (down-arrow), or a single combined label "View / Download" if you want to keep it lighter.

3. **Compliance UX – privacy labels:**
  - Each row shows a subtle privacy label under the subtitle in Inter Regular 11sp `#9A9A9A`, e.g.:
    - "Visible to you and school"
    - "School-only · summary only shown here".

**Colors & Typography:**
- Same parent palette; no bright warning colors — only use terracotta subtly for highly sensitive docs (e.g., small icon accent).

**States:**

*Default:* 1–3 sections with a few documents in each.

*Empty (no documents yet):*
- Warm illustration (folder with leaf) and copy: "The school hasn’t shared any documents yet. They’ll appear here once available." with no CTAs.

*Error loading:* Inline banner `#F7E3D8` with text "We couldn’t load documents. Pull to refresh or try again later.".

**Interactions & Animations:**
- Row tap on "View" opens an in-app document viewer (full-screen) with simple controls (back, share, download).
- Pull-to-refresh refreshes the list, using the standard iOS spinner styled in sage.

---

### Screen P-11: Incident History

**Prompt for Google Stitch:**

Design an **Incident History screen** for the parent mobile app where Meera can calmly review any incidents logged for her child (via T-9). The tone should be reassuring and clear, not alarming.

**Navigation / Menu (hardcoded):**
- Bottom tab bar: `Feed | Milestones | Portfolio | Profile`.
- Accessed from P-8 (Profile / Data & Privacy) via row "Safety & incidents" or from notifications; keep `Profile` as active tab.
- Use a back chevron; no new tabs.

**Layout:**
- Background `#FAF7F2`.
- Header (56dp): back chevron left, title "Incidents" Inter Semibold 16sp.
- Body: 16dp horizontal padding, scrollable.

Content:
1. **Intro / reassurance block:**
  - Small info card at top: light sage background `#E7F2EA`, 12dp radius, 12dp padding.
  - Copy in Inter Regular 13sp `#4A8C5C`: "The school logs notable safety or behaviour events here so you’re always informed.".
  - Subtext in 12sp `#6B6B6B`: "Most days will have no incidents at all." (Parent prompt rule: **keep emotional tone, avoid fear**).

2. **Incident timeline list:**
  - Group by date (section headers like "24 Mar 2026").
  - Each incident card (white, 12dp radius, 12dp padding, 8dp gap) includes:
    - Top row: type + severity chips, e.g.: "Minor injury" pill and a subtle severity pill (`Low`, `Medium`, `High`) — use light outlines, not harsh fills.
    - Second line: time + location ("11:20 am · Playground").
    - Body text: short teacher-written description (2–3 lines) in Inter Regular 13sp `#1A1A1A`.
    - Footer row:
     - Left: small label "Logged by Sunita" in 11sp `#6B6B6B`.
     - Right: status pill:
      - "Awaiting acknowledgement" (light amber outline) or
      - "Acknowledged" (soft sage pill).
     - Optional CTA button **"I’ve read this"** for incidents awaiting acknowledgement.

3. **Empty / no incidents:**
  - Illustration of a happy child and copy: "No incidents have been logged for your child" in Inter Semibold 14sp, with supporting line "If anything important happens at school, it will always be shared here.".

**Colors & Typography:**
- Use mostly neutral and sage tones; terracotta appears only as small accents for medium/high severity text, not as full card backgrounds.

**States:**

*Default with some incidents:* 3–4 cards across recent months, most marked as Acknowledged.

*Awaiting acknowledgement:* At least one card with the status pill and CTA **"I’ve read this"**.

*After acknowledgement:* Tapping "I’ve read this" flips the status pill to "Acknowledged" and removes the CTA.

**Interactions & Animations:**
- "I’ve read this" tap triggers a quick pill state change + light haptic.
- Cards expand/collapse vertically if you want to support a "View more" link for longer descriptions.
- Pull-to-refresh updates the list.

---

## Section 4.3 — Admin Web

---

### Screen A-1: Dashboard Home

**Prompt for Google Stitch:**

Design the Admin Dashboard Home screen for CadenceSprout’s web app. This is Rajesh’s morning control tower: alerts, engagement score, today’s posts/attendance/fees, and class-level breakdown, with clear CTAs.

Metric:
- Primary: Engagement score (parents with ≥1 meaningful update/day), % classes with healthy posting, % classes with submitted attendance.
- Secondary: Fee overdue rate, admissions follow-up completion rate.

**Navigation / Menu (hardcoded):**
- Left sidebar navigation: `Dashboard | Parent Feed | Admissions | Fees | Attendance | Staff | Reports | Settings`.
- `Dashboard` is active.

**Layout:**
- Desktop-first viewport 1280×900px, responsive down to 1024×768.
- Background `#FAF7F2`.
- Left sidebar 240px, main content area flexible.
- Main content top-to-bottom:
  1. **Alerts panel** (full-width, above everything):
    - White card with 16px radius and 24px padding.
    - Title "Alerts" Inter Semibold 16px.
    - Pills or rows for alert groups: Low engagement, Fee issues, Admissions issues, Attendance issues, each with count and severity color.
    - Each alert row has a clear CTA button that deep-links into the relevant OS overview page:
      - Low engagement → filtered engagement drilldown / class table.
      - Fee issues → **A-9 Fees & Payments Overview**, pre-filtered to overdue.
      - Admissions issues → **A-10 Admissions Overview**, focused on follow-ups.
      - Attendance issues → A-5 Attendance Dashboard.
  2. **Engagement hero** row:
    - Large engagement score (e.g., "73%") in Fraunces 40px, with arrow up/down icon and previous week text.
    - Short supporting line: "Parents are loving it!" or problem text if low.
  3. **Summary tiles** row beneath hero:
    - Tiles such as: Posts Today, Attendance Today, Fee Alerts, Admissions Funnel, Staff Snapshot.
    - Each tile shows primary metric and small breakdown text, with click-through:
      - Fee Alerts → **A-9 Fees & Payments Overview**.
      - Admissions Funnel → **A-10 Admissions Overview**.
      - Staff Snapshot → **A-12 Staff Overview**.
  4. **Class breakdown table**:
    - Columns: Class, Engagement %, Posts this week, Parents inactive, Quick Actions.
    - Sorted ascending by Engagement %.
    - Each row has "Message teacher" quick action and click-through to drilldown.

**States:**
- Healthy: hero in sage, encouraging copy, few alerts.
- Warning: hero in terracotta tone, Alerts panel shows multiple issues.
- Empty: if no parents enrolled yet, hero explains what to do next, tiles and table show placeholders.

**Interactions & Animations:**
- Alert CTA navigates to filtered views (Engagement drilldown, Fees, Attendance).
- Clicking the **Low engagement** alert focuses the class breakdown table, pre-filtered to classes below a threshold (e.g., <60%) so Rajesh immediately sees which classes need attention.
- Clicking the **No posts today** alert opens a list or filtered view of teachers/classes with zero posts today, from which Rajesh can click through to message a teacher or open the Parent Feed for that class.
- Class row click opens engagement drilldown page.
- Tiles clickable to detailed pages.

---

### Screen A-2: Parent Feed (Read-Only)

**Prompt for Google Stitch:**

Design the read-only Parent Feed screen for the Admin web app. Rajesh should be able to see what parents are seeing in the app, filter by class/child, and spot content issues, without being able to edit posts.

**Navigation / Menu (hardcoded):**
- Left sidebar: `Dashboard | Parent Feed | Admissions | Fees | Attendance | Staff | Reports | Settings`.
- `Parent Feed` is active.

**Layout:**
- Desktop viewport 1280×900px.
- Background `#FAF7F2`.
- Left sidebar 240px; main content flexible.
- Main content:
  - Page header: "Parent Feed" in Fraunces Regular 28px, subcopy "Read-only view of what parents see" in Inter Regular 14px `#6B6B6B`.
  - Filter bar: dropdowns for Class (All / each class), Child (All / specific), and Date range; search box for caption text.
  - Feed area: responsive grid of post cards (1 column at narrow widths, 2 columns at >= 1200px).

**Post Card (Admin read-only view):**
- Similar visual style to parent post cards:
  - Thumbnail image at top (4:3), white card, 12px radius.
  - Caption snippet (2 lines max) in Fraunces Italic 16px.
  - "From [Teacher] · [Class]" line.
  - Child name chips for tagged children.
  - Engagement mini-row: eye icon + "14 / 18 parents viewed"; comment and reaction counts.
  - Subtle label if the post is hidden or reported.

**States:**
- Default: feed list populated, filters set to "All".
- Filtered: only posts matching filters show; header shows chip "Nursery A · Last 7 days".
- No results: centered message "No posts match your filters" with guidance to adjust filters.

**Interactions:**
- Card click opens a side-panel or modal with full post detail (reuse T-3 / P-4 layout, but read-only) and quick admin actions like "Report to school" or "Mark as inappropriate" (if in scope later).
- Filters update feed instantly.

---

### Screen A-3: Admissions Pipeline

**Prompt for Google Stitch:**

Design the Admissions Pipeline screen for the Admin web app. Rajesh should see inquiries flowing from New → Enrolled in a simple, auditable way aligned with the Phase 1 admissions epic.

**Navigation / Menu (hardcoded):**
- Left sidebar: `Dashboard | Parent Feed | Admissions | Fees | Attendance | Staff | Reports | Settings`.
- `Admissions` is active.

**Layout:**
- Desktop viewport 1280×900px.
- Background `#FAF7F2`.
- Main content header: "Admissions" with small description "Track inquiries through to enrollment".
- Two possible layout patterns (pick one and be consistent):
  - **Kanban-style columns** for each stage: New Inquiry, Tour Scheduled, Tour Done, Seat Offered, Enrolled, Not Joining.
  - Or a **table view** with a Stage column and filters.
- For Stitch, favor a **kanban-like layout** for clarity:
  - 6 equal-width columns across the content area, horizontally scrollable if needed.
  - Each column labeled with stage name and count badge.
  - Inquiry cards in each column show: child name, parent name, phone, class of interest, source, created date.

**Key UI pieces:**
- New inquiry button: [New Inquiry] primary button near header (opens modal with fields from PRD: parent name, phone, child name, age, class of interest, source, notes).
- Card drag & drop between stages to change status (or use a stage dropdown on the card);
- Inline stage change confirmation is NOT required; changes are saved immediately.

**States:**
- Default: populated boards with some cards across each stage.
- Empty: friendly empty state when there are no inquiries, with CTA "Add first inquiry".
- Overdue follow-up: cards in any stage for >14 days show a subtle badge "Follow up?" as per PRD.

**Interactions:**
- Drag card between columns to change stage.
- Click card to open detail drawer on the right: full fields, notes area, and CTA to "Convert to enrollment" which pre-fills child profile.

---

### Screen A-4: Fee Management

**Prompt for Google Stitch:**

Design the Fee Management screen for the Admin web app. Rajesh should be able to see invoices, their status, and basic per-parent balances in a clear, filterable table.

**Navigation / Menu (hardcoded):**
- Left sidebar: `Dashboard | Parent Feed | Admissions | Fees | Attendance | Staff | Reports | Settings`.
- `Fees` is active.

**Layout:**
- Desktop viewport 1280×900px.
- Background `#FAF7F2`.
- Header: "Fee Management" + secondary line "Create, track and record payments".
- Controls row:
  - Filters: Class, Billing cycle (This month, Last month, Custom), Status (All / Pending / Paid / Overdue).
  - [New Invoice] primary button.
- Main table:
  - Columns: Invoice #, Parent, Child, Class, Due date, Amount, Status, Last payment, Actions.
  - Status pill colors: Pending (grey), Paid (sage), Overdue (terracotta).
  - Totals row at top or bottom: "Total outstanding", "Overdue amount".

**States:**
- Default: mixed statuses, some overdue highlighted.
- Filtered to overdue: show only overdue invoices and emphasize total overdue amount.
- Empty: explanation "No invoices created yet" with CTA to create first invoice.

**Interactions:**
- Row click opens a right-hand invoice detail drawer: line items (if any), history of status changes, and "Mark as paid" control.
- [New Invoice] opens a modal with parent search field, amount, due date, and notes.
- Table supports column sorting (by due date, amount).

---

### Screen A-5: Attendance Dashboard

**Prompt for Google Stitch:**

Design the Attendance Dashboard screen for the Admin web app. Rajesh should be able to see daily attendance submission status and trends by class.

**Navigation / Menu (hardcoded):**
- Left sidebar: `Dashboard | Parent Feed | Admissions | Fees | Attendance | Staff | Reports | Settings`.
- `Attendance` is active.

**Layout:**
- Desktop viewport 1280×900px.
- Background `#FAF7F2`.
- Header: "Attendance" + date picker (default today).
- Top row cards:
  - "Classes submitted" (% and count).
  - "Average attendance today" (%).
  - "Classes missing attendance" (count) with CTA "View classes".
- Below: class table:
  - Columns: Class, Teacher, Submitted? (Yes/No), Present, Absent, Submission time.
  - Rows with red/highlight for missing submissions.
- Secondary tab or section: "Trends" with simple chart of attendance % over last 30 days.

**States:**
- All classes submitted: top card shows 100%, no red rows.
- Some missing: red-highlighted rows and clear call-to-action.
- No data (new school): empty state with explanation.

**Interactions:**
- Date picker changes table to that date.
- Clicking a class row opens detail view with list of children marked present/absent for that day.

---

### Screen A-6: Staff Management

**Prompt for Google Stitch:**

Design the Staff Management screen for the Admin web app. In Phase 1 this primarily manages staff records (names, roles, classes); Phase 2 (HRMS) will add salary/leave details, so leave space for future growth.

**Navigation / Menu (hardcoded):**
- Left sidebar: `Dashboard | Parent Feed | Admissions | Fees | Attendance | Staff | Reports | Settings`.
- `Staff` is active.

**Layout:**
- Desktop viewport 1280×900px.
- Background `#FAF7F2`.
- Header: "Staff" + [Add staff] primary button.
- Main area: table of staff members.
  - Columns: Name, Role (Teacher / Admin), Class(es) assigned, Phone, Status (Active / Inactive).
  - Optional hidden columns for Phase 2: Salary, Pay cycle (can be included in detail drawer, not main table yet).

**States:**
- Default: several teachers + one or two admins.
- Empty: "No staff added yet" with CTA to add first staff.

**Interactions:**
- Row click opens staff detail drawer with full info: contact details, assigned classes, and placeholders for HRMS data (salary, bank details) clearly marked as Phase 2 (can be greyed out or labelled "Coming later").
- [Add staff] opens modal with fields from PRD (name, phone, role, class assignment).

---

### Screen A-7: School Settings

**Prompt for Google Stitch:**

Design the School Settings screen for the Admin web app. This is where Rajesh configures school name, logo, classes, and basic preferences.

**Navigation / Menu (hardcoded):**
- Left sidebar: `Dashboard | Parent Feed | Admissions | Fees | Attendance | Staff | Reports | Settings`.
- `Settings` is active.

**Layout:**
- Desktop viewport 1280×900px.
- Background `#FAF7F2`.
- Header: "School Settings".
- Content split into panels:
  - **School Profile**: logo upload, school name, address.
  - **Classes**: list of classes with add/edit/remove controls.
  - **Branding & Colors** (Phase 1 minimal, Phase 3 white-label later): show current logo, simple tagline.
  - **Notification defaults**: toggles for which notifications are enabled by default for new teachers/parents.

**States:**
- Default: existing school data filled in.
- Editing: Save/Cancel controls visible for modified fields.

**Interactions:**
- Logo upload uses file picker and shows preview.
- Adding a class opens small modal with name and academic year.
- Save actions show top-right toast on success.

---

### Screen A-8: Reports

**Prompt for Google Stitch:**

Design the Reports screen for the Admin web app. This is a simple place for Rajesh to export or download data for attendance, posts, and fees.

**Navigation / Menu (hardcoded):**
- Left sidebar: `Dashboard | Parent Feed | Admissions | Fees | Attendance | Staff | Reports | Settings`.
- `Reports` is active.

**Layout:**
- Desktop viewport 1280×900px.
- Background `#FAF7F2`.
- Header: "Reports" + small description "Download CSV reports for offline analysis".
- Cards for each report type:
  - **Attendance report**: picker for date range + [Download CSV].
  - **Engagement report**: picker for date range + class filter + [Download CSV].
  - **Fees report**: picker for billing cycle + [Download CSV].

**States:**
- Default: all report tiles visible.
- Generating: show inline spinner/text "Preparing report…".
- Error: inline error with retry option.

**Interactions:**
- Download triggers file download; keep UI non-blocking.

---
 
### Screen A-9: Fees & Payments Overview

**Prompt for Google Stitch:**

Design the **Fees & Payments Overview** screen for the Admin web app. This is the **module home** for Fees, giving Rajesh a quick view of total invoiced, collected, overdue, and which groups of parents need attention — before diving into detailed tables (A-4).

**Navigation / Menu (hardcoded):**
- Left sidebar: `Dashboard | Parent Feed | Admissions | Fees | Attendance | Staff | Reports | Settings`.
- `Fees` is active.
- This is the **overview** page; the detailed invoice table remains A-4.

**Layout:**
- Desktop viewport 1280×900px.
- Background `#FAF7F2`.
- Left sidebar 240px; main content flexible.

Main content top-to-bottom:
1. **Header row:**
  - Title: "Fees & payments" in Fraunces 28px.
  - Subcopy: "High-level view of fee collection and overdue risk" in Inter 14px `#6B6B6B`.
  - Right side: primary button **[Open fee table]** (navigates to A-4) and secondary **[Create invoice]**.

2. **KPI strip (Admin UX: alerts before stats):**
  - Horizontal row of 3–4 metric tiles, each white 16px-radius card with 16px padding:
    - **Total invoiced this month** (₹, big number).
    - **Collected this month** (₹ + % of invoiced).
    - **Overdue amount** (₹) — if >0, show terracotta accent border and small alert pill "Needs attention".
    - **Parents overdue** (count) — with a mini link "View list" that jumps to a filtered table in A-4.

3. **Alerts panel (ERP alerts first):**
  - Card titled "Fee alerts" Inter Semibold 16px.
  - Inside, list of alert rows (no more than 3–5), each with:
    - Label (e.g., "10 parents overdue > 30 days", "3 classes with >20% overdue").
    - Severity color (sage for mild, terracotta outline for serious).
    - CTA button such as "View in Fee Management" or "Filter by class" (links into A-4 with pre-applied filters).
    - Include an **"Upcoming dues"** style alert when there is a cluster of invoices due in the next ~3 days (e.g., "22 invoices due in the next 3 days") so Rajesh can act before they become overdue.

4. **Collections trend & breakdown:**
  - Two side-by-side cards:
    - Left: simple line or bar chart of collections over the last 6 months.
    - Right: pie or stacked bar showing distribution of statuses this month (Paid vs Pending vs Overdue).
  - Charts should be visually simple — **no complex BI** feel.

5. **Quick lists (tables with filters & bulk actions):**
  - Below charts, two compact tables (Admin UX rule: use tables for large data):
    - Table A: "Top overdue classes" with columns: Class, Overdue amount, Parents overdue, Quick action (e.g., "View invoices").
    - Table B: "Recent payments" with columns: Date, Parent, Child, Amount, Method.
  - Each table includes a "View all" link to the detailed A-4 table.

**States:**

*Healthy collection:*
- Overdue amount tile shows low values; alerts list is short or empty; charts skew towards Paid.

*Upcoming dues spike (next 3 days):*
- Even if Overdue is low, show an "Upcoming dues" alert row (e.g., "Many invoices due in the next 3 days") in the Fee alerts panel.
- Optionally surface a small neutral badge in the KPI strip under **Total invoiced this month** like "₹X due in next 3 days".
- CTAs should encourage proactive outreach or filters in A-4 (e.g., "View upcoming"), not emergency language.

*Stressed collection:*
- Overdue tile and alerts panel visually emphasize the issue (terracotta outlines, not heavy fills).
- At least one alert row: "Overdue > 30 days" with a strong CTA.

*Empty (no invoices yet):*
- Hero area shows friendly empty state: "No fee records yet" with CTA **"Create first invoice"**.
- Charts and tables show placeholders or are hidden.

**Interactions & Animations:**
- Clicking KPI tiles or alert CTAs navigates to A-4 with filters applied (e.g., "Status: Overdue").
- Tables support column sorting where it makes sense but default to most-recent / highest-risk.
- Subtle hover states on cards and rows; avoid flashy animations.

---

### Screen A-10: Admissions Overview

**Prompt for Google Stitch:**

Design the **Admissions Overview** screen for the Admin web app. This is the high-level **funnel + KPI** view for admissions, complementing the detailed Kanban pipeline (A-3).

**Navigation / Menu (hardcoded):**
- Left sidebar: `Dashboard | Parent Feed | Admissions | Fees | Attendance | Staff | Reports | Settings`.
- `Admissions` is active.

**Layout:**
- Desktop viewport 1280×900px.
- Background `#FAF7F2`.
- Main content:

1. **Header row:**
  - Title "Admissions" (Fraunces 28px) with subcopy "Track inquiries from first contact to enrollment".
  - Right: primary button **[Open pipeline board]** (links to A-3), secondary **[Add inquiry]**.

2. **Funnel summary (Admin UX: alerts + stats):**
  - Horizontal **funnel visualization** card showing counts by stage:
    - New inquiry → Tour scheduled → Tour done → Seat offered → Enrolled → Not joining.
  - Each stage shows count + conversion % to next stage.
  - If any stage has unusually high drop-off, highlight with subtle terracotta label "High drop-off".

3. **Key KPIs row:**
  - Tiles for:
    - Inquiries this month.
    - Conversion rate (New → Enrolled).
    - Median time to enroll.
    - Lost inquiries (Not joining).

4. **Alerts & follow-ups:**
  - Card "Follow-ups needed" listing 3–10 inquiries that:
    - Have been idle in a stage more than N days.
    - Or are near decision deadline.
  - Columns: Child, Stage, Days in stage, Quick action ("Open in pipeline").
  - CTA at card-level: "View all follow-ups" going to A-3 with filters.

5. **Source breakdown table:**
  - Table summarizing inquiries by source: `Source | Inquiries | Enrolled | Conversion %`.
  - Include typical sources: Walk-in, Website, WhatsApp, Referral, Fair/Expo.

**States:**

*Default busy season:*
- Funnel and KPIs populated; follow-up card has multiple entries.

*Quiet season:*
- Fewer inquiries; KPIs still present but follow-up card may show a short "No urgent follow-ups" line.

*Empty (school not using admissions yet):*
- Warm empty state encouraging Rajesh to add first inquiry; hide detailed tables.

**Interactions & Animations:**
- Clicking a funnel stage filters the follow-up list and offers a link to A-3 with that stage active.
- Table rows clickable to open inquiry detail side-drawer (same as A-3 detail).

---

### Screen A-11: Child Records

**Prompt for Google Stitch:**

Design the **Child Records** screen for the Admin web app. This is the compliance-focused hub where Rajesh can search, filter, and open detailed child records (profile, documents, medical info, emergency contacts, incidents).

**Navigation / Menu (hardcoded):**
- Left sidebar: `Dashboard | Parent Feed | Admissions | Fees | Attendance | Staff | Reports | Settings`.
- For now, access Child Records via Dashboard alerts or settings links (you can optionally show a "Children" entry in the nav but don’t redesign the whole nav here).

**Layout:**
- Desktop viewport 1280×900px.
- Background `#FAF7F2`.

1. **Header & filters:**
  - Title "Child records" in Fraunces 28px.
  - Filter bar below with:
    - Search box (by child name, admission #).
    - Class dropdown.
    - Status filter (Active / Alumni).
  - Right side: pill button "Export list".

2. **Main records table (Admin UX: table + filters):**
  - White table card with columns:
    - Child name.
    - Class.
    - Admission number.
    - Parents linked (count or names).
    - Docs status (e.g., "Complete", "Missing docs", "Expiring soon").
    - Incidents (count in last 12 months).
  - Each row clickable; row hover state.

3. **Detail drawer (right side) when a row is clicked:**
  - Slides in from the right ~360px wide.
  - Tabs or stacked sections for:
    - **Profile:** DOB, gender, address, admission details.
    - **Documents:** list with privacy labels (reuse P-10 style) — show which docs are missing.
    - **Medical & emergency:** allergy info, medications, emergency contacts.
    - **Incidents:** recent incidents from T-9 (list with date, type, link to full incident).
  - Clear **privacy labels** at the top: e.g., "Visible to school staff only".

**States:**

*Default:* Table with several rows, some marked as "Missing docs" or "Expiring soon".

*Filtered:* Filters applied at top; table shows subset.

*Empty:* If no records, show empty state encouraging Rajesh to import or add via Admissions (A-3/A-10).

**Interactions & Animations:**
- Filters and search update table instantly.
- Row click slides in detail drawer; closing drawer returns focus to the same table row.
- In Documents section, missing docs may have a CTA "Request from parent" (even if not fully specified in PRD, leave room for later).

---

### Screen A-12: Staff Overview

**Prompt for Google Stitch:**

Design the **Staff Overview** screen for the Admin web app. This is the at-a-glance staff module home that complements the detailed Staff Management table (A-6).

**Navigation / Menu (hardcoded):**
- Left sidebar: `Dashboard | Parent Feed | Admissions | Fees | Attendance | Staff | Reports | Settings`.
- `Staff` is active.

**Layout:**
- Desktop viewport 1280×900px.
- Background `#FAF7F2`.

1. **Header:**
  - Title "Staff" in Fraunces 28px.
  - Right side: primary **[Open staff table]** (links to A-6) and secondary **[Add staff]**.

2. **Snapshot tiles (Admin UX: alerts first):**
  - Row of tiles for:
    - Total staff.
    - Teachers vs non‑teaching staff.
    - Today’s presence (e.g., "24 of 27 present").
    - Leaves today (count).
  - Any anomalies (e.g., low presence) show a small terracotta-labeled alert.

3. **Today’s attendance overview:**
  - Compact table: `Name | Role | Class | Status (Present/On leave/Absent)`.
  - Filter chip row above: `All | Teachers | Admin | Support`.
  - Bulk action affordance: checkbox column + "Send message" bulk action.

4. **Roles & distribution card:**
  - Simple chart or text summary of staff by role and class coverage.
  - Example: list of classes with teacher names and a small icon if a class is missing a primary teacher.

**States:**

*Normal day:* Most staff present; one or two on leave; no alerts.

*Short-staffed:* Today’s presence tile and overview table highlight multiple absences; optional alert text "3 classes with no homeroom teacher present".

*Empty (no staff added):* Empty state encouraging Rajesh to add first staff.

**Interactions & Animations:**
- Clicking snapshot tiles filters the staff table below (e.g., clicking "On leave" filters to those rows).
- Bulk selection toggles checkboxes and activates bulk action bar.

---

### Screen A-13: Login

**Prompt for Google Stitch:**

Design the Admin web login screen for CadenceSprout. This should feel consistent with the teacher login but optimized for desktop use by school admins.

**Navigation / Menu (hardcoded):**
- No sidebar; this is a pre-auth page.

**Layout:**
- Desktop viewport 1280×900px.
- Split layout:
  - Left 50%: warm illustration or brand story (Sunshine Preschool with children artwork, etc.).
  - Right 50%: login form card.
- Background `#FAF7F2`.
- Login card:
  - White, 16px radius, 32px padding.
  - "CadenceSprout Admin" heading in Fraunces 24px.
  - Subcopy "Sign in to manage your preschool" in Inter 14px.
  - Fields: phone number (or email/phone) and password, similar styling to T-0 but desktop-sized.
  - [Log In] primary button.
  - "Forgot password?" link.

**States:**
- Default, typing, loading, error (invalid credentials) similar to T-0.

**Interactions & Animations:**
- Simple, no heavy animation; subtle hover states on button and inputs.

---

## Section 4.4 — Teacher Web

---

### Screen TW-1: Teacher Web Login

**Prompt for Google Stitch:**

Design a desktop login screen for CadenceSprout's teacher web app. This is the browser equivalent of T-0 but optimized for keyboard use and a 1280×900px viewport.

**Navigation / Menu (hardcoded):**
- No sidebar; this is a pre-auth page.

**Layout:**
- Desktop viewport 1280×900px.
- Background `#FAF7F2`.
- Split layout:
  - Left 55%: school branding and product story.
  - Right 45%: login form card.
- Left panel:
  - "Sunshine Preschool" logo (sun + leaf) top-left.
  - Large headline "CadenceSprout for Teachers" in Fraunces 32px.
  - Short supporting copy about making it easy to share classroom stories.
- Right panel (login card):
  - White card, 20px radius, subtle shadow, centered vertically.
  - Heading "Teacher sign in".
  - Fields: phone number, password, [Log In] button, "Forgot password?" link.
  - Small note: "Use the same account as your mobile app".

**States:**
- Default: empty fields.
- Typing: active field has sage focus border.
- Loading: [Log In] shows spinner and disables fields.
- Error: inline red error below password.

**Interactions:**
- Enter key submits form.
- Forgot password link opens simple modal explaining reset flow (email/phone) without designing the full reset screen.

---

### Screen TW-2: Teacher Web Home Feed

**Prompt for Google Stitch:**

System Intent:
- Mirror the **daily posting loop** of T-1 on web so teachers can keep habits from any device.
- Contribute directly to **teacher posting rate** and the **North Star (parent daily visibility)** from the System Definition.
- Maintain near feature-parity with T-1, while taking advantage of desktop space (sidebar, engagement feedback) without becoming dashboard-heavy.

Metric:
- Primary: Teacher posting rate (including web), contribution to North Star.
- Secondary: Posts per class per week from web, % days with at least one post (web or mobile).

Design the Teacher Web Home Feed screen. This mirrors T-1 but uses a left sidebar and wider layout. Sunita should see her daily posting status, today’s feed, and quick ways to post from desktop.

**Navigation / Menu (hardcoded):**
- Left sidebar nav exactly: `Feed | Attendance | Roster | Milestones | Profile`.
- `Feed` is active.

**Layout:**
- Desktop viewport 1280×900px, background `#FAF7F2`.
- Left sidebar 240px: school logo, nav items, mini-profile.
- Main content:
  - Page header row with:
    - "Today in class" title.
    - Small subcopy "Share one story every day".
    - Right-aligned [New post] primary button.
  - Daily status banner (full-width card):
    - State A (no post today): warm terracotta accent, copy "You haven't shared today's story yet", secondary text "Parents are waiting for one moment from today.", inline [Post now] button.
    - State B (posted): sage accent, copy "Today's story is shared", and a link "View today's post".
  - Feed area:
    - Single column of post cards with photo, caption, child tags, engagement stats.
    - Optional filter pill row for "Today", "This week", "All".

  - **Engagement feedback strip** (optional card below banner): when enough data exists, show a slim card with copy like "80% parents engaged today — great job!" in Inter Semibold 14px `#4A8C5C` and a softer subline "Aim for at least one story each day". This mirrors the emotional reinforcement in the mobile feed.

**States:**
- No posts today: banner in State A, feed shows last few days below.
- Today posted: banner in State B, today's post pinned at top.
- Empty (new teacher): empty state card with illustration and CTA to create first post.
 - High engagement day: engagement feedback strip shows a positive message ("Parents are loving your updates this week"), reinforcing behavior.

**Interactions:**
- [New post] and banner CTA open TW-3 composer (modal or full-screen overlay).
- Post card click opens detailed post view (reuse T-3 layout adapted to web, but you do not need a separate screen ID).

---

### Screen TW-3: Teacher Web Post Composer

**Prompt for Google Stitch:**

Design the desktop web post composer for teachers. This is launched from TW-2 and should feel like a focused writing/drafting space for one story per day.

**Navigation / Menu (hardcoded):**
- Underlying sidebar remains `Feed | Attendance | Roster | Milestones | Profile`, with `Feed` active.
- Composer appears as a centered modal or full-screen overlay above TW-2.

**Layout:**
- Desktop viewport 1280×900px.
- Dimmed background behind composer.
- Composer card:
  - Width ~800px, max-height 80% viewport, scrollable body.
  - Header row: "New class story" title + close (X) icon.
  - Two-column inside layout where space allows:
    - Left: media preview area.
    - Right: caption and metadata.
- Elements:
  - Drag-and-drop area for photo/video or "Upload from computer" button.
  - Caption textarea with Fraunces styling for preview feel.
  - Child tagging chips list with an **AI suggestions** label when available ("AI detected these children") and AI-suggested dashed chips similar to T-2, including confidence text and quick ✓/✕ actions.
    - [SYSTEM] AI child detection and suggestion logic for these chips is owned by the backend/AI services per the System Design; this screen mirrors the same behavior as T-2.
  - Class selector (if teacher has multiple classes).
  - Visibility summary text ("Shared with parents of [Class]").
  - Bottom action bar: [Post now] primary, [Save draft] secondary, word count.

**States:**
- Empty (no media, no caption).
- Draft in progress with media + caption.
- Error (missing required fields) — inline message at top of form.
 - AI suggestions available: AI label + dashed chips with confidence; teacher can confirm/remove suggested children before posting.

**Interactions:**
- Dragging a file into the window highlights the media drop zone.
- Child chips selectable/deselectable with clear visual state.
- Post now closes composer and returns to TW-2 with new post at top.

---

### Screen TW-4: Teacher Web Attendance

**Prompt for Google Stitch:**

Design the attendance screen for teachers on web. This parallels T-4 but uses a table-based layout so Sunita can quickly mark present/absent for an entire class with keyboard/mouse.

**Navigation / Menu (hardcoded):**
- Sidebar nav: `Feed | Attendance | Roster | Milestones | Profile`.
- `Attendance` is active.

**Layout:**
- Desktop viewport 1280×900px, background `#FAF7F2`.
- Header: "Attendance" with date picker (default today) and class dropdown.
- Below header: small status pill "Not submitted" or "Submitted at 9:12 AM".
- Main table:
  - Columns: Child name, Status (Present / Absent), Notes (optional), Last updated.
  - Rows for each child in class.
- Sticky bottom bar when there are unsaved changes: "11 present · 3 absent" and [Submit attendance] primary button.

**States:**
- Default (not submitted): all children default to Present, status pill "Not submitted".
- Submitted: controls disabled, status pill "Submitted" with time.
- Partial edits (before submit): bottom bar visible.

**Interactions:**
- Clicking Present/Absent toggles state (radio buttons or segmented control).
- Keyboard shortcuts optional (e.g., up/down to move between rows, P/A keys) but don’t over-specify behavior.
- Submit attendance shows small success toast and locks in values for the day.

---

### Screen TW-5: Teacher Web Class Roster

**Prompt for Google Stitch:**

Design the class roster screen on web. This parallels T-5, letting Sunita see and manage the list of children in each class from desktop.

**Navigation / Menu (hardcoded):**
- Sidebar nav: `Feed | Attendance | Roster | Milestones | Profile`.
- `Roster` is active.

**Layout:**
- Desktop viewport 1280×900px, background `#FAF7F2`.
- Header: "Class roster" with class dropdown and [Add child] button.
- Main table:
  - Columns: Child name, Parent name(s), Contact, Status (Active/Inactive).
  - Optional column: Tags (e.g., "Bus", "Allergy").
- Right-side detail drawer pattern reused from admin when clicking a child row.

**States:**
- Default: populated table.
- Empty class: friendly message and CTA to add first child.

**Interactions:**
- Row click opens child detail drawer (align with T-5A content: child photo, profile fields, parent contacts, class info).
- [Add child] opens modal with minimal fields for Phase 1 (name, class, parent contact).

---

### Screen TW-6: Teacher Web Milestone Tracker (per child)

**Prompt for Google Stitch:**

Design the web milestone tracker screen for a single child, parallel to T-6 but with more space for lists and history.

**Navigation / Menu (hardcoded):**
- Sidebar nav: `Feed | Attendance | Roster | Milestones | Profile`.
- `Milestones` is active.

**Layout:**
- Desktop viewport 1280×900px.
- Header row:
  - Back link "← All children".
  - Child avatar and name.
  - Class label.
- Two-column layout:
  - Left: list of milestone categories and filters.
  - Right: selected category details and logged milestones.
- Right pane content:
  - Timeline of milestone entries (date, description, related posts, teacher notes).
  - [Add milestone] button.

**States:**
- Default with some milestones logged.
- No milestones yet: empty state with CTA to add first milestone.

**Interactions:**
- Category click filters the right-hand list.
- [Add milestone] opens modal or side panel that reuses fields from T-6 (choose milestone, date, optional link to post).

---

### Screen TW-7: Teacher Web Profile / Settings

**Prompt for Google Stitch:**

Design a desktop-first profile and settings screen for CadenceSprout's teacher web app. This should feel like the browser companion to the teacher mobile app: warm, editorial, and calm, but with the efficiency of a modern web settings page.

**Navigation / Menu (hardcoded):**
- Render the left sidebar exactly as: `Feed | Attendance | Roster | Milestones | Profile`
- Profile is active

**Layout:**
- Desktop viewport 1280×900px
- Background `#FAF7F2`
- Persistent left sidebar (240px) matching the teacher web app with logo, nav links, teacher mini-profile at bottom
- Main content area with 40px page padding
- Page header: "Profile & Settings" in Fraunces Regular 32px `#1A1A1A`, subcopy in Inter Regular 15px `#6B6B6B`
- Two-column main layout:
  - Left column (340px): profile summary card
  - Right column (fluid): stacked settings panels
- Cards/panels: white, 16px radius, subtle shadow, 24px padding

**Content:**
- Left profile card:
  - 88px avatar
  - Teacher name
  - Role and class assignment
  - School name
  - Small edit profile button
- Right settings panels:
  - Notifications with 3 toggles
  - Preferences with language and upload quality dropdowns
  - Browser permissions/help panel with browser notification status banner
  - Account panel with logout button and app version text

**States:**

*Default:* All settings visible, toggles in current state

*Browser notifications blocked:* Amber inline banner with "Enable in browser settings" CTA

*Save success:* Top-right toast "Settings updated."

*Save failed:* Inline row-level error message beneath the changed control

*Loading:* Skeleton profile card + skeleton rows in each panel

**Interactions & Animations:**
- Toggles update optimistically
- Dropdown menus open below trigger with soft scale/fade
- Logout opens centered confirmation modal
- Sidebar remains static; only content area scrolls if needed

---

## Section 4.5 — Parent Web

---

### Screen PW-1: Parent Web Magic-Link Feed

**Prompt for Google Stitch:**

Design the magic-link entry feed for parents on the web. This is what Meera sees when she taps a magic-link from WhatsApp/SMS and lands in the browser before full OTP login.

**Navigation / Menu (hardcoded):**
- Mobile bottom nav: do **not** show yet; treat this as a lightweight preview.
- Desktop header nav: minimal (logo + "CadenceSprout"), no full app nav.

**Layout:**
- Primary focus: the post or feed content the link referred to.
- Background `#FAF7F2`.
- Top bar with school logo, "Sunshine Preschool" and small text "Powered by CadenceSprout".
- Main card centered (mobile and desktop) showing either:
  - Single post the link is for, or
  - Short feed snippet (last 3 posts) if the link is generic.
- Below content: call-to-action strip with text "See more stories and milestones" and a [Continue] button that leads into the full login flow (P-0/P-0A equivalent on web).

**States:**
- Default: post/mini-feed visible, CTA visible.
- Error (expired link): friendly message and button "Request a new link".

**Interactions:**
- Scrolling shows limited historical posts (e.g., last 3–5), without full navigation.
- Tapping [Continue] pushes Meera into the full parent web app onboarding.

---

### Screen PW-2: Parent Web Full Feed (After OTP Login)

**Prompt for Google Stitch:**

System Intent:
- Mirror the **emotional, story-first** experience of P-3 for parents who land on web instead of mobile.
- Act as a full participant in the **North Star** and parent WAU metrics (System Definition) — a parent session here counts just like P-3.
- Preserve cross-platform parity for feed behavior and notifications while keeping the layout calm and non-ERP.

Metric:
- Primary: North Star (parents seeing ≥1 meaningful update per day), parent WAU.
- Secondary: P-3/PW-2 combined daily view rate, average posts viewed per active parent web session.

Design the main Parent Web Feed screen for authenticated parents. This mirrors P-3 but adapted for responsive web, with a clear daily summary card and grouped posts.

**Navigation / Menu (hardcoded):**
- Mobile bottom nav: `Feed | Milestones | Portfolio | Profile` with `Feed` active.
- Desktop header nav: `Feed | Milestones | Portfolio | Profile` with `Feed` active.

**Layout:**
- Mobile web first (375×812px), responsive up to desktop width.
- Background `#FAF7F2`.
- Header bar:
  - School logo left, page title "Today" or "Feed" center, lightweight user avatar or initials right.
  - A notifications bell icon in the header (or in the top-right corner on desktop) with a small sage dot when there are unread notifications, mirroring the P-3/P-7 behavior on mobile. Tapping it navigates to the notifications view (or opens a notifications panel if implemented on web).
    - [SYSTEM] Unread counts, bell dot state, and navigation target are handled by the Notification System; this header only shows the indicator and click/tap affordance.
- Content stack:
  - "Story of the day" summary card at top with:
    - Short summary sentence for the day (from AI / Epic 10 conceptually).
      - [SYSTEM] Generation of this daily summary line is handled by the AI layer per the System Design; this prompt only defines where and how the text is displayed.
    - Chips for children if multiple children.
    - Quick list of how many new posts today.
  - Below, feed of post cards grouped by day (Today, Yesterday, Earlier this week).
  - Each card mirrors parent mobile post cards: photo, caption, child tags, teacher/class line, reactions/comments summary.

**States:**
- Default with posts from today and previous days.
- No posts today: summary card shifts to "No new stories today" and highlights last post from this week.
- Multi-child: summary card and feed show child filters/toggles.

**Interactions:**
- Clicking a post opens PW-3 post detail view overlay or dedicated page.
- On desktop, a two-column layout is allowed (feed left, simple sidebar right) but keep design calm and not dashboard-like.

---

### Screen PW-3: Parent Web Post Detail

**Prompt for Google Stitch:**

Design the detailed post view for parents on the web, corresponding to P-4 but responsive for browsers.

**Navigation / Menu (hardcoded):**
- Mobile bottom nav: `Feed | Milestones | Portfolio | Profile` with `Feed` active.
- Desktop header nav: `Feed | Milestones | Portfolio | Profile` with `Feed` active.

**Layout:**
- Mobile: full-screen page with back button to PW-2.
- Desktop: centered card or side panel layout above a dimmed background.
- Content pieces:
  - Large media (image/video) at top.
  - Caption in Fraunces Italic, slightly larger than body text.
  - Child chips (for each tagged child), class/teacher line.
  - Timestamp.
  - Reactions bar (heart, smile, etc.) with counts.
  - Comments list with parent name, comment text, timestamp.

**States:**
- Default: content fully loaded.
- No comments: show "No comments yet" placeholder.
- Loading: skeleton for media and text.

**Interactions:**
- Reaction icons clickable (toggle state) where permitted.
- Comment input at bottom (if in scope) with send button.

---

### Screen PW-4: Parent Web Milestone Progress

**Prompt for Google Stitch:**

Design the milestone progress screen for parents on the web, aligned with P-5 but optimized for larger screens.

**Navigation / Menu (hardcoded):**
- Mobile bottom nav: `Feed | Milestones | Portfolio | Profile` with `Milestones` active.
- Desktop header nav: `Feed | Milestones | Portfolio | Profile` with `Milestones` active.

**Layout:**
- Mobile web first, responsive up to desktop.
- Background `#FAF7F2`.
- For single child:
  - Header with child avatar, name, and class.
  - Progress overview card with simple visual (e.g., number of milestones logged, categories covered).
  - List of milestone categories; each expandable to show items and which are logged.
- For multiple children:
  - Child selector at top (chips or dropdown) switching the content below.

**States:**
- Child with many milestones: show various categories partially complete.
- No milestones yet: empty state encouraging parents to look forward to updates.

**Interactions:**
- Category tap/click expands/collapses details.
- Links from milestones to related posts can open PW-3 post detail.

---

### Screen PW-5: Parent Web Profile / Settings

**Prompt for Google Stitch:**

Design a mobile-first responsive profile and settings screen for CadenceSprout's parent web experience. This screen should feel family-friendly, private, and lightweight, with a strong sense of trust.

**Navigation / Menu (hardcoded):**
- Mobile bottom nav must be exactly: `Feed | Milestones | Portfolio | Profile`
- Desktop header nav must be exactly: `Feed | Milestones | Portfolio | Profile`
- Profile is active in both cases

**Layout:**
- Primary viewport mobile web 375×812px, but include responsive hints for desktop
- Background `#FAF7F2`
- Mobile header with school logo left, page title centered, no heavy chrome
- Scrollable body with 16dp horizontal padding
- Top profile card:
  - Parent name
  - Masked phone number
  - School name
  - Linked child summary
- Grouped white settings cards:
  - Notifications card with per-post and daily digest toggles
  - Privacy card with "Data & Privacy ›" and "Privacy Policy ›" rows
  - About card with app/web version row
  - Account card with outlined red Log Out button
- On desktop, center content in a 720px column with more breathing room

**States:**

*Default:* Profile card + all settings groups visible

*Loading:* Skeleton profile card and skeleton rows

*Save success:* Toast "Settings updated."

*Save failed:* Inline error under affected toggle row

*Dark mode:* Background `#1A1A1A`, cards `#242424`, text `#F5F2EC`, dividers `#333333`

**Interactions & Animations:**
- Toggle switches animate smoothly with 180ms spring
- Data & Privacy row navigates to PW-6
- Log Out opens centered confirmation modal on desktop, bottom sheet confirmation on mobile

---

### Screen PW-6: Parent Web Privacy Settings

**Prompt for Google Stitch:**

Design a web view privacy settings screen for CadenceSprout's parent web experience. This screen manages DPDP consent and must feel serious, transparent, and reassuring without becoming legalistic or cold.

**Navigation / Menu (hardcoded):**
- Mobile bottom nav must be exactly: `Feed | Milestones | Portfolio | Profile`
- Desktop header nav must be exactly: `Feed | Milestones | Portfolio | Profile`
- Keep `Profile` as the active menu context

**Layout:**
- Mobile web viewport 375×812px primary, responsive up to desktop
- Background `#FAF7F2`
- Header: back chevron, title "Your child's privacy controls", school logo context
- Centered content column with 16dp horizontal padding mobile, 720px max width desktop
- Main white card with 18dp radius, 20dp padding:
  - Child context row with child avatar and name
  - Three consent rows, each with:
    - Title in Inter Semibold 15sp `#1A1A1A`
    - Description text in Inter Regular 13sp `#6B6B6B`
    - Toggle on right
    - "Last updated: [date]" caption below where applicable
  - One consent row is informational/read-only and uses a disabled toggle appearance
  - Link row: "See full privacy policy"
- Sticky bottom action area:
  - [Save changes] primary button only visible when changes have been made

**States:**

*Default:* All current consent states visible, Save button hidden

*Toggle changed:* Save button appears from bottom with slide-up animation

*Revoke confirmation:* Face-recognition toggle off opens modal dialog with warm white surface, destructive confirm, and explanatory text

*Saved:* Top toast "Privacy settings updated."

*Revocation pending:* Soft terracotta info banner: "Existing recognition data will be deleted within 24 hours."

*Dark mode:* Background `#1A1A1A`, card `#242424`, text `#F5F2EC`, borders `#333333`, primary button `#7AAF8C`

**Interactions & Animations:**
- Toggle animations use smooth spring motion
- Save bar slides up only when there are unsaved changes
- Privacy policy opens in modal overlay on mobile and centered modal on desktop
- Destructive confirmation modal uses red confirm button and neutral cancel button

---
 
## Draft & Data Safety Rule

No teacher input should ever be lost.

All user-generated content must:
- Auto-save locally
- Be recoverable from Drafts
- Retry on failure

