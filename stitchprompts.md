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

---

### Screen T-2A: Manual Child Tag Picker Modal

**Prompt for Google Stitch:**

Design a modal child picker that slides up from the bottom of the Post Composer (T-2). This allows Sunita to manually add children to a post if AI detection didn't catch them or if she wants to add more.

**Context:**
- Parent: T-2 (Post Composer)
- Appearance: User taps "Add manually +" link at end of the children chips row
- Dismissal: Tap background overlay, swipe down, or tap close button
- iOS-first, React Native

**Layout:**
- Rounded rectangle modal, white surface `#FFFFFF`, bottom sheet style
- Handle: 4dp×32dp rounded pill `#E8E2D9`, centered 12dp from top
- Header row: "Add children" Inter Semibold 16sp `#1A1A1A`, right of header a close button "✕" Inter Regular 18sp `#6B6B6B`
- Search input: full width, 48dp tall, outlined `#E8E2D9` border, placeholder "Search children..." Inter Regular 14sp `#9A9A9A`, focus border sage green `#5C8B6E`
- Below search: scrollable list of all children in the class (16dp padding)

**UI Elements (Child Item):**
Each child in the list:
- Left: small circular profile photo (40dp, placeholder default avatar)
- Center: child name in Inter Semibold 14sp `#1A1A1A`, below it optional class or section in Inter Regular 12sp `#9A9A9A`
- Right: checkbox (24dp, unchecked = outlined `#E8E2D9`, checked = solid sage green `#5C8B6E` with white checkmark)
- Full-width tappable row, 12dp divider below, 8dp top/bottom padding

**States:**
- Empty search: Show all 12-15 children (paginate if >20)
- Typing: Filter list in real-time, show matching children only
- No matches: "No children found. Try another search." centered placeholder text

**Interactions:**
- Checkbox tap: toggle child, row ripple effect
- Close/swipe: dismiss modal, return to T-2 with selected children added to chips
- Done button (optional): full-width primary button at bottom, sage green `#5C8B6E`, "Add to post" — tapping dismisses modal

---

### Screen T-3: Post Detail

**Prompt for Google Stitch:**

Design the Post Detail screen where Sunita can view her post, see parent reactions and comments, and reply to parents. This appears after tapping a post card on T-1 (Home Feed).

**Context:**
- Entry: User taps a post card on T-1
- iOS-first, React Native, iPhone 14 Pro
- Metric: Parent engagement (comments, reactions), teacher response time

**Navigation / Menu (hardcoded):**
- Top-left: back arrow, "← Feed"
- Inherit teacher bottom tab bar but keep Feed context

**Layout:**
- Background: `#FAF7F2` (cream)
- Header: custom, 56dp tall, sage green `#5C8B6E` fill — left back arrow + "Post Details" Inter Semibold 16sp white, right: three-dot menu icon (share, delete, etc.)
- Content area (scrollable):

**UI Elements:**

1. **Post Card (mirrored from T-1):**
   - Full-bleed photo (4:3 aspect, responsive), 12dp top radius
   - Caption: Fraunces Italic 16sp `#1A1A1A`, 12dp padding
   - Child chips: solid sage green pills
   - Meta (left: timestamp, right: views) Inter Regular 12sp `#9A9A9A`
   - 8dp bottom padding, white surface

2. **Engagement Section:**
   - 16dp gap
   - Row: "👍 14 likes" Inter Semibold 14sp `#1A1A1A` | "💬 7 comments" Inter Semibold 14sp `#1A1A1A`
   - 1dp divider `#E8E2D9` below

3. **Comments Thread:**
   - 8dp padding
   - Each comment: small circular avatar (32dp, placeholder), left of comment body
   - Comment body: parent name Inter Semibold 13sp `#1A1A1A` + "2 hours ago" Inter Regular 11sp `#9A9A9A` stacked, below it comment text Fraunces Italic 14sp `#1A1A1A`
   - If teacher has replied: below comment is teacher's reply in a slight sage-tinted background card (`#F5F9F7`), indented 8dp, same structure
   - Full-width divider 1dp `#E8E2D9` between comments

4. **Reply Composer (sticky at bottom above tab bar):**
   - Row: small teacher avatar (32dp) + multiline input field, "Reply to Meera..." placeholder Inter Regular 13sp `#9A9A9A`
   - 40dp tall minimum, full-width, white surface, 1dp top border `#E8E2D9`

**Colors & Typography:**
- Cream background, white cards, sage headers, Fraunces for captions

**States:**
- Loading: skeleton cards for comments
- No comments: centered placeholder "No comments yet. Parents will see updates here." Inter Regular 14sp `#9A9A9A`
- Comment count badge: if 7+, show small chip "7+ comments" sage green

**Interactions:**
- Back arrow: navigate to T-1
- Tap reply input: keyboard appears, input gains sage border
- Send reply (tap return key): comment queues, optimistic UI shows comment immediately, [SYSTEM] offline queue handles persistence
- Three-dot menu: delete/edit options (delete with confirmation)

---

### Screen T-4: Attendance

**Prompt for Google Stitch:**

Design the Attendance marking screen for Sunita to mark daily attendance for her class in under 60 seconds. This is a lightweight, mobile-first tab in the teacher app, not a heavy admin dashboard.

**Context:**
- Tab in teacher mobile app (between Feed and Roster in tab bar)
- Use case: Sunita marks 15-20 children present/absent/leave each morning
- iOS-first, React Native

**Navigation / Menu (hardcoded):**
- Bottom tab bar: `Feed | Attendance | Roster | Profile` — Attendance is active (sage green icon)

**Layout:**
- Background: `#FAF7F2`
- Header: 56dp, white surface, top border 1dp `#E8E2D9`
  - Left: "Attendance" Inter Semibold 16sp `#1A1A1A`
  - Right: date picker "Today" Inter Regular 13sp `#6B6B6B` (tappable to select another date)
- Quick selector row: 3 large buttons in a row — "Mark All Present" (sage), "Mark All Absent" (grey), "Undo" (light grey) — 32dp tall, 8dp radius, Inter Regular 12sp
- Child list (scrollable):

**UI Elements (Child Item):**
- 56dp row height
- Left: child name Inter Regular 14sp `#1A1A1A`
- Right: 3-state toggle pill (32dp tall, 8dp radius):
  - State 1 (Present): filled sage green `#5C8B6E`, white "P" text Inter Semibold 12sp
  - State 2 (Absent): filled light red/pink (`#F5D5D5`), dark "A" text
  - State 3 (Leave): filled warm yellow (`#F5D9A8`), dark "L" text
- Tapping toggles through states; each tap gives haptic feedback
- Light divider 1dp `#E8E2D9` below each row

Bottom section:
- Summary bar: "Present: 18 / Absent: 1 / Leave: 1" Inter Regular 13sp `#6B6B6B`, white surface, 1dp top border
- [SAVE] button: full-width 48dp, sage green `#5C8B6E`, "Save Attendance" Inter Semibold 15sp white, 16dp padding

**Colors & Typography:**
- Cream background, white surface, sage primary, light red/yellow for state indicators

**States:**
- Default: all children unmarked (neutral grey state pills)
- Loading: skeleton rows
- Saved: toast "Attendance saved" Inter Regular 13sp white on `#4A8C5C` (success green), auto-dismiss 2s
- Empty class: "No children in this class yet. Add them in Roster settings." centered placeholder

**Interactions:**
- Tap state pill: cycle through P→A→L→(unmarked)
- Quick buttons: "Mark All Present" sets all to P instantly with cascade animation, "Undo" reverts to previous state if available
- Save button: validates 100% of children are marked, saves if true, else shows toast "Mark all children first"

---

### Screen T-5: Class Roster

**Prompt for Google Stitch:**

Design the Class Roster screen for Sunita to see all children in her class, view linked parents, and manage class membership. This is the child management hub, not a teacher data entry form.

**Context:**
- Tab in teacher mobile app
- Shows 15-20 children per class
- iOS-first, React Native

**Navigation / Menu (hardcoded):**
- Bottom tab bar: `Feed | Attendance | Roster | Profile` — Roster is active

**Layout:**
- Background: `#FAF7F2`
- Header: 56dp, white surface
  - Left: "Class Roster" Inter Semibold 16sp `#1A1A1A`
  - Right: "LKG A" Inter Regular 13sp `#6B6B6B` (class name, tappable to switch classes if teacher has multiple)
- Optional search row: input field 48dp tall, placeholder "Search child..." — only show if >10 children
- Child list (scrollable):

**UI Elements (Child Item):**
- 64dp row height
- Left: circular profile photo (48dp, placeholder default avatar) + child name in Inter Semibold 14sp `#1A1A1A`
- Below name optional attendance % badge: "94%" in small pill Inter Regular 11sp `#6B6B6B` on `#F0F0F0`
- Right: chevron icon "›" 20dp `#9A9A9A`
- Full-width tappable row, 1dp divider below

Tapping a child row → navigates to T-5A (Child Detail)

**States:**
- Loading: skeleton rows
- Empty: "No children in this class. Add them in settings." centered placeholder
- Search filtering: show matching children only, "No results" if none match

**Interactions:**
- Swipe left on child row: reveal delete/edit options (red "Remove" button)
- Tap chevron/row: navigate to T-5A
- Class dropdown: switch classes if teacher has multiple, roster updates

---

### Screen T-5A: Child Detail

**Prompt for Google Stitch:**

Design a child profile screen showing everything Sunita needs to know about one child: demographics, linked parents, milestones, recent posts, and incidents.

**Context:**
- Navigated from T-5 (Roster)
- Shows single child
- iOS-first, React Native

**Navigation / Menu (hardcoded):**
- Top-left: back arrow "← Roster"
- Inherit teacher bottom tab bar

**Layout:**
- Background: `#FAF7F2`
- Header: 56dp sage green `#5C8B6E`
  - Left: back arrow + child name "Rohan" Inter Semibold 16sp white
  - Right: three-dot menu
- Content (scrollable):

1. **Profile Card (white surface, 12dp radius, 16dp padding):**
   - Circular avatar (80dp, centered)
   - Child name Inter Semibold 18sp `#1A1A1A`, centered
   - "DOB: 2020-06-15 | Age: 3y 10m" Inter Regular 13sp `#9A9A9A`, centered

2. **Linked Parents Section:**
   - Header "Parents" Inter Semibold 14sp `#1A1A1A`, 8dp top gap
   - Parent item: avatar (32dp) + parent name "Meera" Inter Semibold 13sp + phone "98765 43210" Inter Regular 12sp `#6B6B6B`
   - Link status badge: green pill "✓ Linked" or grey "Not linked yet"
   - [+ Add Parent] link at end
   - 1dp divider

3. **Milestones Progress:**
   - Header "Milestones" Inter Semibold 14sp
   - Progress bars by NEP domain (5 domains): each domain — label "Social-Emotional" Inter Regular 12sp + progress bar (3/8 achieved, sage green fill) + "3/8" badge
   - [View All] link

4. **Recent Posts:**
   - Header "Recent Posts" Inter Semibold 14sp
   - 2-3 most recent post thumbnails (3:4 aspect, center-crop photo, no text), tappable to view post detail
   - [View All Posts] link

5. **Incidents:**
   - If any: header "Incidents" Inter Semibold 14sp
   - Each incident: small chip badge (severity color) + text "Fall on playground · 3 days ago" Inter Regular 12sp
   - Link [View Incident]

**Colors & Typography:**
- Sage header, cream background, white cards, Fraunces for headings

**Interactions:**
- Back arrow: navigate to T-5
- Tap [+ Add Parent]: open parent invitation modal/flow
- Tap parent item: show parent detail
- Tap milestone bar: expand section
- Tap post thumbnail: navigate to T-3 (Post Detail)

---

### Screen T-6: Milestone Tracker

**Prompt for Google Stitch:**

Design a screen where Sunita can see milestones achieved by all children in her class, grouped by NEP 2020 domain and child. This is a progress view, not a detailed tracker — show at a glance which children are thriving and where.

**Context:**
- Tab in teacher mobile app (Future: may be accessed from profile/settings)
- Shows NEP 2020 domains: Social-Emotional, Physical Development, Cognitive, Language, Creative
- iOS-first, React Native

**Navigation / Menu (hardcoded):**
- If a tab: `Feed | Attendance | Roster | Milestones | Profile` (Milestones active)
- Else: back arrow from wherever user navigates to this screen

**Layout:**
- Background: `#FAF7F2`
- Header: "Milestones" Inter Semibold 16sp `#1A1A1A`, white surface 56dp
- Toggle buttons (16dp padding): "By Domain" (active, sage green) | "By Child" (inactive grey) — for switching views
- Content area (scrollable):

**UI Elements (Domain View):**
For each NEP domain (5 total):
- Collapsible card 12dp radius white surface:
  - Header row: domain icon (24dp, placeholder) — domain name "Social-Emotional" Inter Semibold 14sp `#1A1A1A` — chevron right icon `#9A9A9A`
  - When expanded (top 4dp radius border sage green `#5C8B6E`):
    - List of 5-8 milestones under domain (e.g., "Shows empathy to peers", "Manages emotions with support")
    - Each milestone: checkbox (if editable) + text Inter Regular 13sp, progress bar at bottom showing "4 children achieved / 15 total"
    - If a specific child has achieved it: show small avatar (16dp) at progress bar end

**UI Elements (Child View):**
For each child in class:
- Row: child name Inter Semibold 14sp + "8 milestones achieved" Inter Regular 12sp `#9A9A9A`
- Progress bar: sage green, showing 8/40 total possible milestones (across 5 domains)
- Breakdown: "SE: 2 | PD: 2 | Cog: 2 | Lang: 1 | Creat: 1" Inter Regular 11sp `#6B6B6B`
- Expand chevron

**Colors & Typography:**
- Sage header, cream background, white cards

**States:**
- Loading: skeleton cards
- Empty: "No milestones recorded yet. Tag milestones when posting updates about children." centered placeholder
- Expanded domain/child: show full details

**Interactions:**
- Toggle "By Domain" ↔ "By Child": view switches with fade animation
- Tap domain/child row: expand/collapse
- Tap milestone checkbox (if milestone already achieved): confirm to un-achieve it (rare case)

---

### Screen T-6A: Milestone Picker Modal

**Prompt for Google Stitch:**

Design a modal that slides up from T-2 (Post Composer) when Sunita taps "Add milestones (optional)". This allows her to tag which NEP 2020 milestones the children in the post have achieved.

**Context:**
- Parent: T-2 (Post Composer)
- Appearance: Bottom sheet modal
- iOS-first, React Native

**Layout:**
- Rounded modal, white surface, handle 4dp×32dp at top
- Header: "Add Milestones" Inter Semibold 16sp, close button ✕
- Segmented control: "Domain" (active, sage green) | "Child" (grey)
- Search input: "Search milestone..." 48dp outlined inter Regular 13sp

**UI Elements (Domain View):**
- Expandable domain sections (5 domains total)
- Each domain expands to show 5-8 milestone checkboxes
- Each milestone: flex checkbox (24dp unchecked = `#E8E2D9` border, checked = sage `#5C8B6E` fill), text Inter Regular 13sp
- Full-width divider 1dp `#E8E2D9` between domains

**Interactions:**
- Checkbox tap: toggle milestone, refresh selection
- Close modal: return to T-2 with selected milestones populated
- Done button (optional): "Add Milestones" full-width primary at bottom

---

### Screen T-7: Profile / Settings

**Prompt for Google Stitch:**

Design the Teacher Profile & Settings screen with name, class assignment, notification options, and logout.

**Context:**
- Tab in teacher mobile app
- iOS-first, React Native

**Navigation / Menu (hardcoded):**
- Bottom tab bar: `Feed | Attendance | Roster | Profile` — Profile is active

**Layout:**
- Background: `#FAF7F2`
- Header: white surface 56dp, "Settings" Inter Semibold 16sp `#1A1A1A`
- Content (scrollable):

**UI Elements:**

1. **Profile Section (white card, 12dp radius, 16dp padding):**
   - Circular avatar (64dp)
   - Name "Sunita" Inter Semibold 16sp `#1A1A1A`
   - Phone number "+ 91 9876543210" Inter Regular 13sp `#6B6B6B`
   - [Edit Profile] button (outlined sage, 32dp)

2. **Class Assignment:**
   - Row: "Current Class" Inter Semibold 14sp — "LKG A" Inter Regular 13sp `#6B6B6B`
   - Chevron, tappable to switch classes

3. **Notifications Section (divider-separated):**
   - Label "Notifications" Inter Semibold 14sp
   - Toggle: "Parent reactions & comments" Inter Regular 13sp — toggle switch (on/off)
   - Toggle: "Daily posting nudge" Inter Regular 13sp — toggle switch
   - Toggle: "Push notifications" Inter Regular 13sp — toggle switch

4. **About & Legal:**
   - "App Version 1.0.0" Inter Regular 12sp `#9A9A9A`
   - Link "Privacy Policy" Inter Regular 12sp `#5C8B6E`
   - Link "Terms of Service" Inter Regular 12sp `#5C8B6E`

5. **[Logout] Button:**
   - Full-width 48dp, outlined red `#C0392B`, "Logout" Inter Semibold 15sp red

**Colors & Typography:**
- Cream background, white cards, sage primary, red logout

**Interactions:**
- Toggle switch: immediate state change
- [Edit Profile]: open edit form modal
- [Logout]: confirm dialog "Are you sure?" — yes/no, clear session

---

### Screen T-8: Daily Report Form

**Prompt for Google Stitch:**

Design an optional Daily Report form that Sunita can fill out in the evening to summarize the day for parents. This is lightweight and non-blocking — it should feel quick to fill (2-3 minutes), not like a burden.

**Context:**
- Accessible from T-1 (Home Feed) via a soft affordance like "Add daily summary" link
- A modal or dedicated screen
- iOS-first, React Native
- Goal: Provide parents with a structured summary of the day's mood, key learning areas, and highlights

**Navigation / Menu (hardcoded):**
- If modal: inherit from T-1
- If screen: back arrow "← Feed"

**Layout:**
- Background: warm cream `#FAF7F2` or sage-tinted `#F8FAF8`
- Header: "Daily Summary" Inter Semibold 16sp `#1A1A1A`
- Form (scrollable):

**UI Elements:**

1. **Class Mood (required):**
   - Label "How was the mood today?" Inter Regular 13sp
   - 4 clickable emoji/icon buttons in a row:
     - 😊 "Great" (sage green highlight when selected)
     - 😌 "Good"
     - 😐 "Okay"
     - 😔 "Challenging"
   - 56dp height buttons with text labels below

2. **Learning Highlights (optional):**
   - Label "What did the class focus on?" Inter Regular 13sp
   - Multiline text area 3 lines, outlined border, placeholder "E.g., block building, storytelling, outdoor play..." Inter Regular 13sp `#9A9A9A`

3. **Notable Moments (optional):**
   - Label "Any special moments?" Inter Regular 13sp
   - Multiline text area 3 lines, placeholder "E.g., Rohan shared a funny joke today..." Inter Regular 13sp `#9A9A9A`

4. **Share Setting:**
   - Row: toggle "Share with parents" Inter Regular 13sp — toggle switch (on by default)
   - Secondary text "Adds to tonight's digest notification" Inter Regular 12sp `#9A9A9A`

**Colors & Typography:**
- Warm palette, outlined form fields, sage green for buttons

**States:**
- Empty: all fields blank, submit button disabled
- Filled: submit button enabled sage green
- Submitted: toast "Daily summary saved & shared" Inter Regular 13sp white on `#4A8C5C`, close modal

**Interactions:**
- Mood button tap: highlight in sage, deselect others
- Text area focus: border turns sage green `#5C8B6E`
- Toggle "Share with parents": on/off state
- [Save & Share] button (bottom, full-width, 48dp, sage green): save form, trigger share to parents if toggled, close modal

---

### Screen T-9: Incident Report Form

**Prompt for Google Stitch:**

Design a form where Sunita can log incidents (falls, behavioral moments, medical, etc.) about children in her class. Incidents are stored in child records and can optionally notify parents.

**Context:**
- Accessible from T-2 (Post Composer) inline or from T-5A (Child Detail) [+ Log Incident]
- iOS-first, React Native
- Goal: Keep a structured log of notable events for compliance and parent communication

**Navigation / Menu (hardcoded):**
- Modal or screen depending on context
- Back arrow if full screen

**Layout:**
- Background: `#FAF7F2`
- Header: "Log Incident" Inter Semibold 16sp `#1A1A1A`
- Form (scrollable):

**UI Elements:**

1. **Child Selection (required):**
   - Label "Which child?" Inter Regular 13sp
   - Dropdown/search: "Select child..." Inter Regular 13sp `#9A9A9A`
   - Tapping opens child picker modal (T-2A style)

2. **Incident Type (required):**
   - Label "Type of incident" Inter Regular 13sp
   - Segmented picker (horizontal scroll if >5):
     - "Fall" | "Behavior" | "Medical" | "Social" | "Other"
     - Selected: sage green pill `#5C8B6E`, unselected: grey pill `#E8E2D9`

3. **Severity (required):**
   - Label "Severity" Inter Regular 13sp
   - Radio buttons (3 options):
     - "Minor" (light yellow `#F5D9A8`)
     - "Moderate" (orange `#E8A87C`)
     - "Major" (light red `#F5D5D5`)

4. **Description (required):**
   - Label "What happened?" Inter Regular 13sp
   - Multiline textarea 4 lines, placeholder "Describe the incident..." Inter Regular 13sp

5. **Actions Taken (optional):**
   - Label "Actions taken" Inter Regular 13sp
   - Multiline textarea 3 lines, placeholder "E.g., ice applied, teacher supervised..." Inter Regular 13sp

6. **Notify Parent (optional, prominent):**
   - Row: toggle "Notify parent" Inter Semibold 14sp `#1A1A1A` — toggle switch (defaults ON)
   - Secondary: "Parent will be notified immediately" Inter Regular 12sp `#9A9A9A`
   - Risk: if toggled OFF, show warning badge: "ℹ Parent won't be notified" in small pill `#F5D9A8`

**Colors & Typography:**
- Severity colors (yellow/orange/red), form outlined, sage green accent

**States:**
- Empty: submit button disabled
- Filled: submit button enabled sage green
- Submitted: toast "Incident logged" + [✓ Notify parent sent] if notified

**Interactions:**
- Type/severity selection: immediate visual feedback
- Text input: border turns sage on focus
- Toggle "Notify parent": show/hide warning
- [Save Incident] button: validate required fields, save, show confirmation if notified, close

---

## Section 4.2 — Parent App (Mobile)

---

### Screen P-0: Phone Number Entry / OTP Request

**Prompt for Google Stitch:**

Design the first onboarding screen where parents enter their phone number to receive a WhatsApp magic link or OTP. This is the entry point from the magic-link email/SMS Sunita sends.

**Context:**
- Parent taps "Tap here to see updates →" link in WhatsApp or SMS
- iOS-first, React Native, iPhone 14 Pro
- Goal: Get parent into CadenceSprout in <30 seconds without a password

**Navigation / Menu (hardcoded):**
- No persistent menu (pre-auth)
- No bottom tab bar

**Layout:**
- Background: `#FAF7F2` (warm cream), full bleed
- Vertically centered content, 24dp horizontal padding

**UI Elements:**

1. **Header:**
   - School logo (72dp circular, sun+leaf, warm yellow + sage), centered
   - Below: "Sunshine Preschool" Inter Semibold 14sp `#6B6B6B`, centered
   - Below: "CadenceSprout" Fraunces Regular 24sp `#1A1A1A`, centered
   - 40dp gap

2. **Copy:**
   - "See [Child name]'s school moments" Fraunces Italic 20sp `#1A1A1A`, centered
   - 12dp gap
   - "Warm, daily updates from their teacher" Inter Regular 14sp `#6B6B6B`, centered
   - 40dp gap

3. **Phone Input:**
   - Label "Phone number" Inter Regular 13sp `#6B6B6B`
   - Input field 48dp, outlined `#E8E2D9` border, +91 prefix + phone number (numeric keypad)
   - Placeholder "+91 98765 43210" in `#9A9A9A`

4. **Consent Checkbox:**
   - 16dp gap
   - Checkbox + text: "I agree to the Privacy Policy and DPDP consent" Inter Regular 12sp `#6B6B6B`, link "Privacy Policy" in sage green `#5C8B6E`

5. **[Send OTP] Button:**
   - Full-width 48dp, 8dp radius, `#5C8B6E`, "Send OTP" Inter Semibold 15sp white
   - 16dp gap

**Colors & Typography:**
- Cream background, sage primary, Fraunces headline, Inter for body

**States:**
- Empty: button disabled (muted sage)
- Typing: button enabled
- Loading: [Send OTP] shows white spinner
- Error: Below phone field, inline error text 13sp `#C0392B`: "Please enter a valid phone number"
- Success: Transition to P-0A with fade

**Interactions:**
- Keyboard appears: content animates up
- [Send OTP] tap: button disables, spinner appears, API calls backend to send OTP
- [SYSTEM] Backend sends OTP via Wapi (WhatsApp) or MSG91 (SMS) per System Design

---

### Screen P-0A: OTP Verification

**Prompt for Google Stitch:**

Design the OTP verification screen where parents enter the 6-digit OTP they received via WhatsApp/SMS.

**Context:**
- Follows P-0 after successful phone submission
- iOS-first, React Native
- Goal: Verify phone number, don't create friction

**Navigation / Menu (hardcoded):**
- No menu (pre-auth)

**Layout:**
- Background: `#FAF7F2`
- Vertically centered content, 24dp padding

**UI Elements:**

1. **Header:**
   - Back arrow (optional, soft) "← Go back"
   - "Verify your phone" Inter Semibold 18sp `#1A1A1A`, centered

2. **Copy:**
   - "Enter the code sent to +91 98765 43210" Inter Regular 14sp `#6B6B6B`, centered
   - 24dp gap

3. **OTP Input:**
   - 6 digit boxes in a row (48dp × 48dp each, 12dp gap between):
     - Each box: 1dp border `#E8E2D9`, 8dp radius, focused box border sage green `#5C8B6E`
     - Auto focus next box on digit entry
     - Numeric keypad, auto-submit when 6 digits entered

4. **Resend Link (optional):**
   - Below boxes: "Didn't receive code? Resend in 45s" Inter Regular 12sp `#9A9A9A`
   - After 45s, "Resend code" becomes a link in sage green

**Colors & Typography:**
- Cream background, sage focused border, Fraunces for headline

**States:**
- Empty: all boxes empty, borders grey
- Typing: active box border sage green
- Loading: boxes disabled, spinner appears
- Error: shake animation, boxes turn red border `#C0392B`, error message "Incorrect OTP" below
- Success: Transition to P-0B with fade, checkmark animation on final box

**Interactions:**
- Digit tap: keyboard, auto-focus next box
- Auto-submit on 6th digit: verify API call
- Resend link (after 45s): resend OTP to phone
- Back arrow: return to P-0

---

### Screen P-0B: Parent Registration (Name + Consent)

**Prompt for Google Stitch:**

After OTP verification, collect parent's name and confirm privacy/photo consent for face recognition.

**Context:**
- Follows P-0A
- iOS-first, React Native

**Navigation / Menu (hardcoded):**
- No menu (pre-auth)

**Layout:**
- Background: `#FAF7F2`
- Vertically centered content

**UI Elements:**

1. **Copy:**
   - "Let's get started" Fraunces Italic 18sp `#1A1A1A`, centered
   - 8dp gap

2. **Name Input:**
   - Label "Parent name" Inter Regular 13sp `#6B6B6B`
   - Input field 48dp, placeholder "e.g., Meera" Inter Regular 13sp
   - 16dp gap

3. **Consent Checkboxes:**
   - Checkbox 1: "I've received privacy and photo consent information" Inter Regular 13sp `#1A1A1A`, checkbox checked by default (grey)
   - Secondary: "We use photos to tag children with AI (optional)" Inter Regular 12sp `#9A9A9A`
   - 8dp gap
   - Checkbox 2: "I agree to CadenceSprout Terms of Service" Inter Regular 13sp, link "Terms" in sage
   - 24dp gap

4. **[Continue] Button:**
   - Full-width 48dp, `#5C8B6E`, "Continue" Inter Semibold 15sp white
   - Disabled until name is entered and Checkbox 2 is checked

**Colors & Typography:**
- Consent tone (warm, not legal), Fraunces headline

**States:**
- Empty: button disabled
- Filled + consented: button enabled
- Loading: spinner on button
- Success: Transition to P-3 (Parent Feed) with fade

**Interactions:**
- Checkbox toggle: immediate state change
- [Continue] tap: create parent record, transition to P-3

---

### Screen P-1: Parent Home (Feed First)

**Prompt for Google Stitch:**

For now, P-1 is a redirect to P-3 (Parent Feed). In future, this could be a home dashboard. For MVP, keep it simple.

---

### Screen P-2: DPDP Consent Screen

**Prompt for Google Stitch:**

A compliance screen where parents review and manage DPDP consent settings. Can appear post-registration (P-0C) or in Settings (P-8). 

**Context:**
- iOS-first, React Native

**Navigation / Menu (hardcoded):**
- If in settings flow: back arrow "← Settings"
- Else: no menu (pre-auth)

**Layout:**
- Background: `#FAF7F2`
- Header: "Your Consent & Privacy" Inter Semibold 16sp `#1A1A1A`, white surface 56dp
- Body (scrollable):

**UI Elements:**

1. **Consent Summary:**
   - Label "What data we collect" Inter Semibold 14sp
   - List (no bullets):
     - "Child photos & videos shared by teacher" Inter Regular 13sp
     - "Child name, date of birth, milestones" Inter Regular 13sp
     - "Parent name & phone number" Inter Regular 13sp
   - 16dp gap

2. **Data Usage:**
   - Label "How we use it" Inter Semibold 14sp
   - "To show you updates about your child" Inter Regular 13sp
   - "To suggest milestones using AI" Inter Regular 13sp
   - "To create a year-end portfolio" Inter Regular 13sp
   - 16dp gap

3. **Consent Toggles:**
   - Toggle 1: "Photos for AI child tagging (can help us show the right updates)" Inter Regular 13sp — toggle (default ON)
   - Secondary: "You can opt out anytime below" Inter Regular 12sp `#9A9A9A`
   - Toggle 2: "Photo sharing consent (school sees all tagged photos)" Inter Regular 13sp — toggle (default ON)
   - 16dp gap

4. **Data Rights:**
   - Header "Your Data Rights (DPDP Act)" Inter Semibold 14sp
   - Link "[Download my data]" Inter Regular 13sp `#5C8B6E`
   - Link "[Delete my account]" Inter Regular 13sp `#5C8B6E`
   - 16dp gap

5. **[Save Preferences] Button (bottom):**
   - Full-width 48dp, sage green `#5C8B6E`, "Save Preferences" Inter Semibold 15sp white

**Colors & Typography:**
- Compliance-appropriate (clear, not scary), sage accents

**States:**
- Loaded: all toggles reflect user's current settings
- Changed: [Save] button highlights
- Saved: toast "Preferences saved" Inter Regular 13sp white on `#4A8C5C`

**Interactions:**
- Toggle: immediate state change
- [Save]: persist consent choices, show confirmation, navigate back if from settings

---

### Screen P-3: Parent Home Feed

**Prompt for Google Stitch:**

Design the Parent Home Feed where Meera sees posts about her child Rohan. This is the primary engagement surface and should feel warm, personal, and effortless. Posts are teacher-tagged and confirmed.

**Context:**
- Primary daily screen for parents
- Shows posts about parent's child only
- iOS-first, React Native, iPhone 14 Pro
- Metric: Daily active parents, engagement (reactions + comments)

**Navigation / Menu (hardcoded):**
- Bottom tab bar: `Feed | Milestones | Portfolio | Profile` — Feed is active

**Layout:**
- Background: `#FAF7F2` (warm cream)
- Top: native status bar + custom header (56dp tall):
  - Left: school logo (32dp circular)
  - Center: school name "Sunshine Preschool" Inter Semibold 14sp + child name "Rohan" Inter Regular 12sp `#6B6B6B`
  - Right: notification bell icon (24dp) with red badge "2" if unread notifications

- Body: scrollable feed area, 16dp horizontal padding
- Bottom: tab bar (56dp, white surface, 1dp top border `#E8E2D9`)

**UI Elements (Post Card):**
Show 2-3 full post cards:

Post card (rounded 12dp, white surface, 2dp shadow):
- Full-bleed photo (4:3 ratio), top 12dp radius
- Below photo body (12dp padding):
  - Post caption: Fraunces Italic 16sp `#1A1A1A` — "Today Rohan showed amazing focus during puzzle work! He's developing such strong spatial awareness 🧩"
  - 8dp gap
  - Child chip (confirmed): solid sage green pill "Rohan" Inter Regular 12sp
  - 8dp gap
  - Metadata row: left — "Teacher: Sunita" Inter Regular 11sp `#9A9A9A` + "2 hours ago" — right — heart count "2" + comment count "1"
  - 8dp gap
  - Reaction row: left — [❤️] [😊] [👏] reaction buttons (32dp wide) — right — chat bubble [comment]

**FAB (optional):**
No FAB on parent feed (parents don't create content). If chat is available (Phase 2), floating message icon in bottom-right.

**Colors & Typography:**
- Warm cream background, white cards, sage primary, Fraunces captions

**States:**

*Loading:* Skeleton cards (cream `#EDE8DF` pulsing rectangles)

*Empty — no posts today:* Center placeholder:
- Warm illustration (teacher at desk, thinking) in muted watercolor style
- "No updates yet from Rohan's teacher" Inter Semibold 16sp `#1A1A1A` centered
- "Sunita usually shares moments in the morning — check back later!" Inter Regular 13sp `#9A9A9A`

*Notification badge:* If unread posts/comments, show red badge "2" on bell icon top-right

*[SYSTEM] Offline banner:* If offline, persistent 40dp banner below header: wifi-off icon + "You're offline — showing recent posts" Inter Regular 13sp white on `#C4784A` terracotta

*Dark mode:* Background `#1A1A1A`, cards `#242424`, caption `#F5F2EC`, metadata `#9A9A9A`, tab bar `#242424`

**Interactions:**
- Pull-to-refresh: swipe down, spinner in sage green
- Post card tap: navigate to P-4 (Post Detail) with hero image expand
- Reaction button tap: toggle reaction (heart fills red `#C0392B`, others unfilled), count updates immediately (optimistic UI)
- Comment button tap: scroll to comment section within post or navigate to P-4
- Tab switch: immediate, no animation
- Notification bell tap: navigate to P-7 (Notifications)

---

### Screen P-4: Post Detail

**Prompt for Google Stitch:**

Design the Post Detail screen where Meera can see a full post, read captions, see and write comments, and react.

**Context:**
- Navigated from P-3 (tapping a post)
- iOS-first, React Native
- Metric: Comment rate, reaction rate

**Navigation / Menu (hardcoded):**
- Top-left: back arrow "← Feed"
- Inherit bottom tab bar (Feed context)

**Layout:**
- Background: `#FAF7F2`
- Header: white surface 56dp, sage green `#5C8B6E` accent left border (4dp)
  - Left: back arrow + "Post" Inter Semibold 16sp `#1A1A1A`
  - Right: three-dot menu (share, save, etc.)

- Content (scrollable):

**UI Elements:**

1. **Photo (full-bleed, 4:3 ratio responsive height, 12dp corners)**

2. **Post Info Card (white, 12dp radius, 12dp padding below photo):**
   - Caption: Fraunces Italic 16sp `#1A1A1A`
   - 8dp gap
   - Child chip: solid sage "Rohan" Inter Regular 12sp
   - 8dp gap
   - Meta: "Posted by Sunita · 2 hours ago" Inter Regular 11sp `#9A9A9A`
   - 12dp gap

3. **Reaction Bar:**
   - Row: heart count + emoji indicators (❤️ 3 · 😊 1 · 👏 2)
   - Below: 4 reaction buttons (40dp wide each, centered): ❤️ 😊 👏 ➕ (more)
   - Each button is a pill: unfilled = outlined grey `#E8E2D9`, filled (parent has reacted) = solid color (red for ❤️, yellow for 😊, etc.)

4. **Comments Section:**
   - Header "3 comments" Inter Semibold 14sp `#1A1A1A`
   - 1dp divider `#E8E2D9`
   - Comment list (each comment):
     - Small avatar (32dp, placeholder)
     - Left: parent name "Meera" Inter Semibold 13sp + "2 hours ago" Inter Regular 11sp `#9A9A9A`
     - Below: comment text Fraunces Italic 13sp `#1A1A1A` — "This is amazing! Rohan loves puzzles at home too 🧩"
   - 1dp divider between comments

5. **Reply Composer (sticky at bottom above tab bar):**
   - Row: small parent avatar (32dp) + multiline input "Add a comment..." placeholder Inter Regular 13sp `#9A9A9A`
   - Input field grows up to 3 lines, then scrolls
   - Send button: checkmark icon or "→" on right when text is entered
   - 40dp row height minimum, white surface, 1dp top border `#E8E2D9`

**Colors & Typography:**
- Cream background, white cards, sage accents, Fraunces captions

**States:**
- Loading: skeleton comment cards
- No comments: "Be the first to comment!" centered placeholder
- Typing reply: input field border turns sage green, send button appears

**Interactions:**
- Back arrow: navigate to P-3
- Reaction button: toggle reaction, count updates optimistically
- Comment tap: show edit/delete menu if parent's own comment (3-dot icon)
- Reply input + send: queue comment, optimistic UI shows comment immediately
- Scroll to reply composer: auto-scroll when user is typing
- [SYSTEM] Offline handling: comments queue locally if offline, sync when online

---

### Screen P-5: Milestone Progress

**Prompt for Google Stitch:**

Design a screen where Meera can see Rohan's developmental progress across NEP 2020 domains, with achievement badges and linked evidence (posts).

**Context:**
- Tab in parent mobile app
- View-only for parents (no editing)
- iOS-first, React Native
- Metric: Parent engagement with developmental data

**Navigation / Menu (hardcoded):**
- Bottom tab bar: `Feed | Milestones | Portfolio | Profile` — Milestones is active

**Layout:**
- Background: `#FAF7F2`
- Header: white surface 56dp
  - "Rohan's Progress" Inter Semibold 16sp `#1A1A1A`
  - Below: "8 milestones achieved" Inter Regular 12sp `#9A9A9A`

- Body (scrollable):

**UI Elements:**

1. **Overall Progress:**
   - Row: "8 of 40 milestones" Inter Regular 13sp `#6B6B6B`
   - Progress bar (full-width, 24dp tall, 12dp radius, `#5C8B6E` sage green fill): 8/40 = 20%
   - Below: "Rohan is developing at a healthy pace" Inter Regular 12sp `#9A9A9A`, warm wording

2. **By Domain (5 cards, 1 per NEP domain):**
   - Card structure (white, 12dp radius, 12dp padding):
     - Header row: domain icon (24dp) + domain name "Social-Emotional" Inter Semibold 14sp `#1A1A1A` + chevron right
     - Progress bar: "2 of 8" + visual bar
     - Achievement badges (if >2 achieved): row of 2-3 small circular badges with milestone icons/names
   - When tapped: expand to show full list of domain milestones (achieved have checkmark, pending are greyed)

3. **Recent Achievements (optional):**
   - "Just Achieved" Inter Semibold 14sp
   - 1-2 latest milestone badges: "Shares toys with peers" (date) "2 days ago"

**Colors & Typography:**
- Green for progress indicators, warm palette, Inter for body

**States:**
- Loading: skeleton progress bars
- No milestones yet: "Rohan is just getting started! As the year progresses, achievements will appear here." centered placeholder

**Interactions:**
- Domain card tap: expand/collapse to show all milestones in that domain
- Milestone badge tap (on expanded view): show linked post evidence (photo + caption where this milestone was tagged)

---

### Screen P-6: Year-End Portfolio

**Prompt for Google Stitch:**

Design the Year-End Portfolio screen where Meera can browse, curate, download, and share Rohan's memory book for the year.

**Context:**
- Tab in parent mobile app
- Access to year's curated posts, milestones, achievements
- iOS-first, React Native
- Metric: Parent satisfaction, portfolio downloads/shares

**Navigation / Menu (hardcoded):**
- Bottom tab bar: `Feed | Milestones | Portfolio | Profile` — Portfolio is active

**Layout:**
- Background: `#FAF7F2`
- Header: white surface 56dp
  - "Rohan's Portfolio 2024" Fraunces Semibold 16sp `#1A1A1A` — warm and personal
  - Below: "32 moments captured" Inter Regular 12sp `#9A9A9A`

- Body (scrollable):

**UI Elements:**

1. **Portfolio Overview Card (white, 12dp radius, 12dp padding):**
   - Left: portfolio cover image (80dp×120dp, 4:3 crop of a favorite post from the year, default is class photo)
   - Right block:
     - Rohan's name "Rohan" Fraunces Italic 18sp `#1A1A1A`
     - "Age 3-4" Inter Regular 11sp
     - "School year 2024" Inter Regular 11sp
     - 2 buttons stacked:
       - [Download PDF] — outlined sage, 32dp tall
       - [Share Link] — solid sage, 32dp tall

2. **Milestone Summary:**
   - "Milestones Achieved: 8 / 40" Inter Regular 13sp
   - Visual: 5 small progress bars (one per domain), compact layout

3. **Timeline / Moments Grid:**
   - "All Moments" Inter Semibold 14sp, 16dp top
   - Grid of image thumbnails (3 columns, 4:3 ratio):
     - Each cell: post photo center-crop, 8dp border radius
     - On tap: full-screen lightbox view of post + caption + date
   - Pagination or infinite scroll to load more

4. **Filters (optional):**
   - Row of small chip buttons: "All" (active sage) | "Favorites" | "By Milestone" | "By Month"
   - Tapping "Favorites" filters to posts parent has saved
   - Tapping "By Milestone" groups by domain

**Colors & Typography:**
- Memory book aesthetic (warm, editorial), Fraunces for headings

**States:**
- Loading: skeleton grid
- Empty: "Portfolio coming soon as the year progresses!" placeholder
- Downloading: modal with progress bar + "Creating PDF..." Inter Regular 13sp
- Shared: toast "Share link copied to clipboard" Inter Regular 13sp white on `#4A8C5C`

**Interactions:**
- Grid tap: open full-screen lightbox (post + caption + date + swipe navigation)
- [Download PDF]: generate on-device or via server, download via share sheet
- [Share Link]: generate shareable link, show iOS share sheet (email, Messages, WhatsApp)
- Filter buttons: update grid in real-time
- Swipe in lightbox: view next/previous post

---

### Screen P-7: Notifications Center

**Prompt for Google Stitch:**

Design a Notifications screen where Meera can see in-app notifications (new posts, comments, incidents, fee reminders).

**Context:**
- Tab or accessible from header bell icon
- iOS-first, React Native

**Navigation / Menu (hardcoded):**
- Bottom tab bar: `Feed | Milestones | Portfolio | Profile` — or back arrow if modal
- Top-left back arrow if fullscreen

**Layout:**
- Background: `#FAF7F2`
- Header: white 56dp, "Notifications" Inter Semibold 16sp `#1A1A1A`
- Optional filter row: "All | Unread | Posts | Incidents | Fees" chip buttons
- Notification list (scrollable):

**UI Elements (Notification Item):**
- 64dp row height per notification
- Left: icon (24dp) representing notification type:
  - Post: photo thumbnail (circular 40dp crop) or 📸
  - Comment: chat bubble
  - Incident: warning ⚠️
  - Fee: payment 💰
- Center text block:
  - Title: "Sunita shared a new post: 'Block building' Inter Semibold 13sp `#1A1A1A`
  - Timestamp: "2 hours ago" Inter Regular 11sp `#9A9A9A`
  - Optional preview: "Rohan showed amazing…" grey text truncated
- Right: unread indicator (small dot if unread, removed on tap)
- 1dp divider below

**States:**
- Empty: "No notifications yet. Posts and updates will appear here." centered placeholder
- Unread badge: red dot or "3" count on bell icon in header
- All read: grey bell, no badge

**Interactions:**
- Notification tap: navigate to relevant screen (post → P-4, incident → P-10, fee → P-9, etc.)
- Swipe to dismiss: remove notification from list (visual, not delete-permanent)
- Mark as read: happens on tap automatically

---

### Screen P-8: Child Health & Medical Info

**Prompt for Google Stitch:**

Design a view-only screen where Meera can see Rohan's health info entered by school, and edit her own data (allergies, emergency contacts, etc.) with school approval.

**Context:**
- Accessible from Profile/Settings
- iOS-first, React Native

**Navigation / Menu (hardcoded):**
- Back arrow "← Settings" or profile context

**Layout:**
- Background: `#FAF7F2`
- Header: white 56dp, "Health & Medical Info" Inter Semibold 16sp `#1A1A1A`

**UI Elements:**

1. **Allergies Section (white card, 12dp padding):**
   - Label "Allergies" Inter Semibold 14sp
   - If present: list items like "Peanuts" Fraunces Italic 14sp `#C0392B` (red for allergy alerts)
   - If none: "No allergies recorded" Inter Regular 13sp `#9A9A9A`
   - [Edit] link Inter Regular 12sp `#5C8B6E` (opens inline edit or modal)

2. **Medical Conditions:**
   - Label "Medical Conditions" Inter Semibold 14sp
   - Items or "None recorded"
   - [Edit] link

3. **Medications:**
   - Label "Current Medications" Inter Semibold 14sp
   - Items with dosage or "None"
   - [Edit] link

4. **Emergency Contacts:**
   - Label "Emergency Contacts" Inter Semibold 14sp
   - List: "Primary: Meera (mother) · 98765 43210"
   - [Edit] link

5. **Doctor Info (optional):**
   - "Pediatrician: Dr. Sharma · 98754 32100"

**Colors & Typography:**
- Alert red `#C0392B` for allergies, warm palette

**States:**
- Loading: skeleton cards
- Approved edits: updated data visible
- Pending edit: banner "You've submitted updates — awaiting school approval"

**Interactions:**
- [Edit] link: open inline form or modal to edit that section
- Save custom data: [Update] button, shows "Pending approval" status, school admin approves
- Alert indicators: allergies shown in red for quick scanning

---

### Screen P-9: Fees & Payments

**Prompt for Google Stitch:**

Design a Fees screen where Meera can see invoices, outstanding balance, payment history, and pay an invoice. Phase 1: manual payment entry; Phase 2: Razorpay auto-payment.

**Context:**
- Accessible from Profile or main menu
- iOS-first, React Native

**Navigation / Menu (hardcoded):**
- Back arrow "← Settings" or tab

**Layout:**
- Background: `#FAF7F2`
- Header: white 56dp, "Fees & Payments" Inter Semibold 16sp `#1A1A1A`
- Content (scrollable):

**UI Elements:**

1. **Outstanding Balance (prominent card, sage or terracotta if overdue):**
   - Card: 12dp radius, 16dp padding
   - "Balance Due" Inter Regular 13sp `#6B6B6B`
   - "₹2,400" Fraunces Semibold 28sp `#1A1A1A`
   - "Due by Mar 31, 2024" Inter Regular 12sp (red `#C0392B` if overdue)
   - [Pay Now] button: full-width 40dp, sage green `#5C8B6E`, "Pay Now" Inter Semibold 14sp white

2. **Current Invoice (white card):**
   - Header "Current Invoice" Inter Semibold 14sp
   - Details table:
     - "Monthly Fee" | "₹2,000" Inter Regular 13sp
     - "Additional Charges" | "₹400" Inter Regular 13sp (if any)
     - ─────────────────
     - "Total Due" | "₹2,400" Inter Semibold 14sp `#1A1A1A`
   - "Due: Mar 31, 2024" Inter Regular 12sp
   - [Download Invoice] link Inter Regular 12sp `#5C8B6E`

3. **Payment History:**
   - Header "Recent Payments" Inter Semibold 14sp, 16dp top
   - List of past payments:
     - "Mar 2024: ₹2,000 paid on Mar 10" Inter Regular 13sp `#1A1A1A`
     - "Feb 2024: ₹2,000 paid on Feb 08" Inter Regular 13sp
   - Link "[View all receipts]" Inter Regular 12sp `#5C8B6E`

**Colors & Typography:**
- Sage for action, red for overdue, Fraunces for amount, Inter for metadata

**States:**
- No outstanding: "All fees paid ✓" green badge, no Pay button
- Overdue: card background slightly red-tinted, "Overdue by 5 days" in red
- Loading: skeleton cards
- Paid (after transaction): toast "Payment processed" Inter Regular 13sp white on `#4A8C5C`

**Interactions:**
- [Pay Now]: [SYSTEM] In Phase 1, navigate to payment form or manual entry flow; in Phase 2, Razorpay UPI/card modal
- [Download Invoice]: PDF download via share sheet
- [View all receipts]: navigate to payment history detail (or scroll shows all)

---

### Screen P-10: Documents & Records

**Prompt for Google Stitch:**

Design a documents screen where Meera can upload, view, and manage documents related to Rohan (ID proofs, medical reports, permission slips, etc.).

**Context:**
- Accessible from Profile/Settings or Records section
- iOS-first, React Native

**Navigation / Menu (hardcoded):**
- Back arrow

**Layout:**
- Background: `#FAF7F2`
- Header: "Documents" Inter Semibold 16sp `#1A1A1A`, white 56dp

**UI Elements:**

1. **Upload Area (white card, dashed border 2dp `#5C8B6E`):**
   - Center: 📄 icon (48dp) + "Tap to upload document" Inter Regular 13sp `#9A9A9A`
   - Secondary: "PDF, JPG, PNG — max 5MB" Inter Regular 11sp `#9A9A9A`
   - Full-width row, 56dp tall, 12dp padding, tappable

2. **Documents List (white cards, 12dp padding per item):**
   - Each document row:
     - Left: file type icon (📄 PDF, 🖼️ JPG)
     - Center: filename "Aadhaar.pdf" Inter Regular 13sp`#1A1A1A` + "Uploaded by parent" Inter Regular 11sp `#9A9A9A`
     - Right: three-dot menu (download, delete, info)
   - 1dp divider between docs

**States:**
- Empty: [Upload Area] + "No documents yet" placeholder
- Uploading: progress bar in document row (0–100%)
- Uploaded: ✓ checkmark, document appears in list
- Error: "Upload failed — try again" toast

**Interactions:**
- Tap upload area: file picker (Photos, Files)
- Select file: upload starts, progress bar shown
- Three-dot menu: download (iOS share sheet), delete (confirm), view details (file info modal)

---

### Screen P-11: Incident History

**Prompt for Google Stitch:**

Design an Incident History screen where Meera can see any logged incidents about Rohan (falls, behavioral notes, medical, etc.) with timestamps and school follow-ups.

**Context:**
- Accessible from Records/Profile
- iOS-first, React Native

**Navigation / Menu (hardcoded):**
- Back arrow

**Layout:**
- Background: `#FAF7F2`
- Header: "Rohan's Incidents" Inter Semibold 16sp, white 56dp

**UI Elements:**

1. **Incident Timeline (if incidents exist):**
   - Chronological list, most recent first
   - Each incident: white card 12dp padding
     - Top row: incident type badge (severity color) + type label "Fall" Inter Semibold 13sp
     - Severity: small pill badge — green "Minor", orange "Moderate", red "Major"
     - Date: "Mar 10 · 2:30 PM" Inter Regular 11sp `#9A9A9A`
     - Description: "Small tumble on playground. Scraped knee. Applied ice. Looked fine after 5 min." Inter Regular 13sp `#1A1A1A`
     - If school follow-up: "✓ Resolved · Teacher follow-up noted" Inter Regular 11sp `#4A8C5C` (green)
     - Tappable to expand and see full details + any photos/attachments

2. **No Incidents:**

 - Center: warm illustration (child playing safely)
   - "No incidents recorded" Inter Semibold 14sp `#1A1A1A`
   - "Rohan is doing well!" Inter Regular 12sp `#9A9A9A`

**Colors & Typography:**
- Severity colors (green/orange/red), warm palette

**States:**
- Loading: skeleton cards
- Expanded incident: details + full description + school comments + resolution status

**Interactions:**
- Incident card tap: expand to full view with all details and follow-up comments
- Collapse: tap again or back button

---

### Screen P-12: Parent Profile & Settings

**Prompt for Google Stitch:**

Design a profile screen where Meera can manage her name, phone, linked parents (mom/dad/guardian), and notification preferences.

**Context:**
- Tab in parent mobile app
- iOS-first, React Native

**Navigation / Menu (hardcoded):**
- Bottom tab bar: `Feed | Milestones | Portfolio | Profile` — Profile is active

**Layout:**
- Background: `#FAF7F2`
- Header: white 56dp, "Profile" Inter Semibold 16sp `#1A1A1A`
- Content (scrollable):

**UI Elements:**

1. **Parent Profile (white card, 12dp padding):**
   - Circular avatar (64dp) — placeholder default avatar, tappable to edit
   - Name "Meera" Inter Semibold 16sp `#1A1A1A`, tappable to edit
   - Phone "+91 98765 43210" Inter Regular 13sp `#9A9A9A`
   - Role "Mother" Inter Regular 12sp, tappable to edit (Mother/Father/Guardian)

2. **Linked Parents / Guardians:**
   - Header "Other guardians" Inter Semibold 14sp
   - List:
     - "Rakesh (Father) · 98754 32100" Inter Regular 13sp
     - Link [Edit] or [Remove]
   - Link "[+ Add Guardian]" Inter Regular 12sp `#5C8B6E`

3. **Linked Children:**
   - Header "Children" Inter Semibold 14sp
   - "Rohan (LKG A)" Inter Regular 13sp
   - Checkbox "Can also see updates for any siblings" Inter Regular 12sp (if multiple children)

4. **Actions:**
   - [Edit Profile] button: outlined sage, 36dp
   - [Change Password] link: Inter Regular 12sp `#5C8B6E`
   - [Logout] button: outlined red `#C0392B`, 36dp

**Colors & Typography:**
- Warm palette, sage primary, Fraunces for names

**Interactions:**
- Avatar tap: open photo picker to change
- Name/role tap: edit modals
- [Add Guardian]: open phone number input + registration flow
- [Edit Profile]: edit form modal
- [Logout]: confirm dialog, clear session

---

### Screen P-13: Notification Preferences

**Prompt for Google Stitch:**

Design a settings screen where Meera can control notification channels (push, WhatsApp, email) and frequency.

**Context:**
- Accessible from Profile settings
- iOS-first, React Native

**Navigation / Menu (hardcoded):**
- Back arrow "← Settings"

**Layout:**
- Background: `#FAF7F2`
- Header: white 56dp, "Notifications" Inter Semibold 16sp

**UI Elements:**

1. **Notification Channels:**
   - Label "How to notify me" Inter Semibold 14sp
   - Toggles:
     - "Push notifications" Inter Regular 13sp — toggle (default ON)
     - "WhatsApp" Inter Regular 13sp — toggle (default ON)
     - "Email digests" Inter Regular 13sp — toggle (default OFF)

2. **Notification Types:**
   - Label "What to notify me about" Inter Semibold 14sp
   - Checkboxes:
     - "New posts about Rohan" Inter Regular 13sp — checked
     - "Teacher replies to my comments" Inter Regular 13sp — checked
     - "Incident notifications" Inter Regular 13sp — checked
     - "Fee reminders" Inter Regular 13sp — checked
     - "Daily summary digest (evening)" Inter Regular 13sp — unchecked

3. **Do Not Disturb:**
   - Label "Quiet Hours" Inter Semibold 14sp
   - Time picker: "From 9:00 PM to 8:00 AM" Inter Regular 13sp
   - Secondary: "No notifications during these hours" Inter Regular 11sp `#9A9A9A`

4. **[Save Preferences] Button (bottom, full-width):**
   - Sage green `#5C8B6E`, 48dp

**Colors & Typography:**
- Toggles/checkboxes sage on active, Inter text

**States:**
- Loaded: all preferences reflect user settings
- Changed: [Save] button highlights
- Saved: toast "Preferences saved" white on `#4A8C5C`

**Interactions:**
- Toggle/checkbox: immediate state change
- Time picker: slide or tap to set hours
- [Save]: persist preferences to backend

---

### Screen P-14: Privacy & Data Management (DPDP)

**Prompt for Google Stitch:**

Design a privacy control screen where Meera can review what data we have (right to know), request data export (right to access), opt out of AI processing, and delete account (right to deletion).

**Context:**
- Accessible from Profile/Settings — "Privacy" link
- iOS-first, React Native
- Compliance screen (DPDP Act 2023, India)

**Navigation / Menu (hardcoded):**
- Back arrow "← Settings"

**Layout:**
- Background: `#FAF7F2`
- Header: white 56dp, "Privacy & Data" Inter Semibold 16sp

**UI Elements:**

1. **What Data We Have (white card, 16dp padding):**
   - Informational section (read-only):
   - List:
     - "Child name, DOB, photos" Inter Regular 13sp
     - "Parent name, phone, email" Inter Regular 13sp
     - "Posts, comments, reactions" Inter Regular 13sp
     - "Medical/health info" Inter Regular 13sp
     - "Incidents, agreements" Inter Regular 13sp
   - No editing, just transparency

2. **AI Processing Consent (white card, 16dp padding):**
   - Label "AI & Photo Analysis" Inter Semibold 14sp
   - Toggle "Allow AI to analyze child photos for tagging & milestones" Inter Regular 13sp — toggle (default ON)
   - Secondary: "Disable to prevent AI suggestions. School can still post photos." Inter Regular 11sp `#9A9A9A`

3. **Data Export (white card, 16dp padding):**
   - Label "Download Your Data" Inter Semibold 14sp
   - Secondary: "Get a copy of all data in a structured format (PDF/JSON)" Inter Regular 12sp
   - [Download Data] button: outlined sage, 36dp
   - Status: "Last downloaded: Mar 1, 2024" Inter Regular 11sp `#9A9A9A`

4. **Delete Account (white card, red-tinted background, 16dp padding):**
   - Label "Delete Account" Inter Semibold 14sp `#C0392B`
   - Secondary: "Permanently delete your account and all related data. This cannot be undone." Inter Regular 12sp `#6B6B6B`
   - [Delete Account] button: solid red `#C0392B`, 36dp
   - Warning: "All data will be removed after 30 days." Inter Regular 11sp `#C0392B`

**Colors & Typography:**
- Privacy-appropriate (clear, not scary), red for deletion, sage for actions

**States:**
- Downloading: [Download Data] shows spinner + "Preparing your data…"
- Downloaded: toast "Data downloaded to Files" + "Check back in 24h for updates" Inter Regular 11sp
- Delete confirmation modal: "Are you sure? This is permanent." — confirm/cancel

**Interactions:**
- Toggle AI: immediate state change
- [Download Data]: initiates on-device or server export, shows progress
- [Delete Account]: confirm modal, then initiate deletion with 30-day grace period notice

---

### Screen P-15: Logout / Session Management

For now, Logout is a button in P-12 (Profile). When tapped, confirm dialog appears: "Log out of Rohan's account?" — Yes/No. On Yes, clear session, navigate to login screen.

---

## Section 4.3 — Admin Dashboard (Web)

---

### Screen A-1: Admin Dashboard Home (Control Tower)

**Prompt for Google Stitch:**

Design the Admin Dashboard home screen for Rajesh (principal). This is his daily control center where he sees key metrics, alerts, and quick actions. Make it actionable, not dashboard-heavy — show exceptions first.

**Context:**
- Web only, React + Vite
- Desktop-first (1920×1080 primary, responsive to 1366×768)
- Metric: Admin time-to-action on alerts and exceptions

**Layout:**
- Background: soft cream `#FAF7F2`
- Left sidebar (200dp, fixed):
  - School logo (40dp circular)
  - "Sunshine Preschool" Inter Semibold 12sp `#1A1A1A`, truncated with hover tooltip
  - Navigation menu: Home (active sage green), Engagement, Admissions, Fees, Attendance, Staff, Records, Reports
  - Bottom: Settings, Logout

- Top header bar (56dp, white surface):
  - Left: selected school name + dropdown (if multi-schools)
  - Center: (empty, space for search)
  - Right: notification bell (with red badge count), user avatar + name dropdown

- Main content area (flexbox layout):

**UI Elements (above the fold):**

1. **Alerts & Exceptions (prominent, red/orange-tinted card, 16dp padding):**
   - Header "⚠️ Requires Action" Inter Semibold 14sp `#C0392B`
   - List of top 3 alerts:
     - "Nursery A: 1 post today (target 3) → [Message Sunita]" Inter Regular 13sp, right action button
     - "₹5,400 overdue from 2 families → [Send Reminders]" Inter Regular 13sp
     - "7 absences this week (Nursery B) → [Review]" Inter Regular 13sp
   - If no alerts: green checkmark "All clear!" `#4A8C5C`

2. **KPI Cards (grid of 4, each white surface 12dp radius, 16dp padding):**
   - Card 1: "Posts Today" — "12 posts" Fraunces Semibold 28sp + "Target: 15" Inter Regular 11sp `#9A9A9A`
   - Card 2: "Parent Engagement" — "68%" Fraunces Semibold 28sp sage green + "↑ 5% vs last week" Inter Regular 11sp `#4A8C5C`
   - Card 3: "Attendance %" — "94%" Fraunces Semibold 28sp + "3 absences logged" Inter Regular 11sp
   - Card 4: "Outstanding Fees" — "₹8,200" Fraunces Semibold 28sp + "2 families" Inter Regular 11sp `#C4784A`

3. **Quick Actions (horizontal button row):**
   - [Message Teachers] — outlined sage, 40dp
   - [Send Fee Reminders] — outlined terracotta
   - [Review Admissions] — outlined sage
   - [View Details] — outlined grey

4. **Engagement Trend (white card, 16dp padding, half-width):**
   - Header "Engagement Score (7 days)" Inter Semibold 14sp
   - Line chart: x-axis dates (Mon-Sun), y-axis score 0–100, sage green line with data points
   - Below: "Trending ↑ +8 points this week" Inter Regular 12sp `#4A8C5C`

5. **Class Performance (white card, 16dp padding, half-width):**
   - Header "Posts by Class" Inter Semibold 14sp
   - Bar chart: y-axis class names, x-axis post count
   - Bars: sage green, sorted descending
   - Nursery A: ████████ 8
   - Nursery B: █████ 5
   - LKG A: ███████ 7
   - etc.

6. **Bottom Section (below fold):**
   - [View Full Reports] link Inter Regular 13sp `#5C8B6E`
   - Last updated: "Updated 2 min ago" Inter Regular 11sp `#9A9A9A`

**Colors & Typography:**
- Cream background, white cards, sage primary for metrics, terracotta for secondary data, Fraunces for KPI values

**States:**
- Loading: skeleton cards (cream pulsing rectangles)
- School selector changed: re-fetch all data
- Alert dismissed: remove from list
- Alert action clicked: navigate to relevant screen with context pre-filled

**Interactions:**
- Alert button tap: navigate to relevant screen (Nursery A roster, fee management, etc.) with context showing the specific issue
- KPI tap: navigate to detailed dashboard (A-2 for engagement, A-5 for attendance, etc.)
- Chart hover: show data tooltips (date + value)
- Sidebar menu: navigate to other admin screens

---

### Screen A-2: Engagement Dashboard

**Prompt for Google Stitch:**

Design a detailed Engagement Dashboard where Rajesh can see posting trends, parent engagement, and identify low-performing classes with quick action to message teachers.

**Context:**
- Web, React + Vite
- Desktop-first, 1920×1080+
- Accessed from A-1 or sidebar menu

**Layout:**
- Sidebar + header as A-1
- Main content area:

**UI Elements:**

1. **KPI Summary Row (white cards, 16dp padding each):**
   - This Week: "45 posts" | "68% parent engagement" | "2.8 posts/class/day"
   - Comparison: "↑ 8%" | "↓ 3%" | "↑ 0.4"

2. **Engagement Trend Chart (white card, 400×300dp):**
   - Header "Posts Per Day (30-day trend)" Inter Semibold 14sp
   - Line chart: x-axis dates, y-axis post count
   - Multiple lines (one per class) with color-coded legend
   - Hover shows specific data for each class

3. **Class Performance Table (white card, full-width):**
   - Header "Classes Ranked by Engagement" Inter Semibold 14sp
   - Columns: Class | Posts This Week | Avg Per Day | Parent Engagement % | Status | Action
   - Rows:
     - Nursery A | 8 | 1.6 | 72% | ✓ Good | [Details]
     - LKG A | 7 | 1.4 | 68% | ⚠️ Caution | [Message Teacher]
     - Nursery B | 5 | 1.0 | 55% | 🔴 Low | [Message Teacher] + [Review]
   - Sort by column (ascending/descending)
   - Pagination if >10 classes

4. **Parent Engagement Breakdown (white card, half-width):**
   - Header "Parent Interaction Patterns" Inter Semibold 14sp
   - Pie chart: Reactions 40%, Comments 35%, Saves 15%, Shares 10%

5. **Recent Posts Preview (white card, half-width):**
   - Header "Latest Posts" Inter Semibold 14sp
   - 3-4 compact preview rows: class + teacher + timestamp + post preview caption (truncated)
   - Link [View All]

6. **Filters Row (top of content):**
   - Date range selector: "This Week" (active) | "This Month" | "All Time"
   - Class filter dropdown: "All Classes" or specific class
   - Engagement filter: "All" | "High" | "Medium" | "Low"

**Colors & Typography:**
- Sage for good status, orange for caution, red for low, Inter for body

**States:**
- Loading: skeleton tables and charts
- Filtered: table updates to show selected range/class
- Empty: "No data for this period" placeholder

**Interactions:**
- Date range tap: filter data, charts update
- Class filter: re-sort table, update charts
- Table row tap: navigate to that class detail
- [Message Teacher] button: open pre-filled message modal with class name
- [Details] button: show class-specific breakdown in modal/drawer
- Chart legend click: toggle visibility of that class's line

---

### Screen A-3: Admissions Pipeline

**Prompt for Google Stitch:**

Design the Admissions Pipeline where Rajesh can manage leads from inquiry → enrollment, track source, conversion funnel.

**Context:**
- Web, React + Vite
- Accessed from sidebar or A-1

**Layout:**
- Sidebar + header as A-1
- Main content area with two views: Pipeline (kanban) and List (table)

**UI Elements (Pipeline View — default):**

1. **Funnel Stages (horizontal columns, left to right):**
   - Inquiry (10) | Interested (6) | Scheduled (4) | Enrolled (2) | Converted (1)
   - Each column background: light sage tinted
   - Compact cards in each column:
     - Card height: 80dp, white surface, 8dp padding
     - Parent name "Meera" Inter Semibold 12sp
     - Child name "Rohan" Inter Regular 11sp
     - Contact "98765 43210" Inter Regular 10sp
     - Class "LKG A" badge
     - Date added "Mar 8" Inter Regular 10sp `#9A9A9A`

2. **Card Interactions (drag-and-drop):**
   - Drag card between columns to advance/regress lead through funnel
   - On drop: confirmation toast + backend sync

3. **Add Lead Button:**
   - "New Inquiry +" button in Inquiry column header
   - Opens modal: parent name, child name, contact, class interest, source (Website/Referral/Walk-in/Social), notes

4. **Funnel Stats (bottom):**
   - Conversion rate "2 enrolled / 10 inquiries = 20%"
   - Average time-to-enrollment "14 days"
   - Top source "Referral: 40% | Walk-in: 30% | Website: 20%"

**UI Elements (List View):**

1. **Table (sortable columns):**
   - Parent | Child | Contact | Class Interest | Source | Stage | Date Added | Actions
   - Rows: clickable to expand details
   - Bulk select: checkbox column, [Bulk Actions] button (message, move stage, archive)

2. **Actions per row:**
   - [Edit] — open edit form modal
   - [Move] — dropdown stage selector
   - [Message] — pre-filled message to parent
   - [Archive] — grey out, don't delete

**States:**
- Empty: "No inquiries yet. Click 'New Inquiry +' to get started." placeholder
- Loading: skeleton cards
- Filtered: support stage or source filter at top

**Interactions:**
- Toggle Pipeline ↔ List view: button top-right
- Drag card (pipeline): move stage, auto-save
- Click row (list): expand to full details modal
- [New Inquiry]: open form modal
- [Message]: pre-filled SMS/WhatsApp with parent name + child offer

---

### Screen A-4: Fee Management (Invoices)

**Prompt for Google Stitch:**

Design a Fee Management screen where Rajesh can create invoices, track payments, send reminders, and view overdue status.

**Context:**
- Web, React + Vite

**Layout:**
- Sidebar + header
- Main content area with tabs: Invoices | Payments | Settings

**UI Elements (Invoices Tab — default):**

1. **Summary Cards (top):**
   - "Total Outstanding: ₹8,200" Fraunces Semibold 24sp
   - "Overdue: ₹2,400" Fraunces Semibold 24sp terracotta `#C4784A`
   - "This Month Collected: ₹12,000" Fraunces Semibold 24sp sage green

2. **Invoice Table (white card, 16dp padding):**
   - Columns: Family | Child | Amount | Due Date | Status | Action
   - Status badges: "Paid" green | "Due" grey | "Overdue" red `#C0392B`
   - Rows (sample):
     - Meera | Rohan | ₹2,000 | Mar 31 | Due | [Pay] [Message]
     - Rakesh | Aarav | ₹2,400 | Mar 15 | Overdue | [Pay] [Message] [Resend Invoice]
   - Paginated if >20 invoices
   - Filters: Status, Date range, Family search

3. **[+ Create Invoice] Button:**
   - Opens form: Select child → Set amount → Set due date → [Create]

4. **Bulk Actions:**
   - Checkbox column, select multiple invoices
   - [Send Reminder to Selected] button — batch WhatsApp/SMS
   - [Mark as Paid] button — bulk update status

5. **Payments Tab:**
   - Timeline of payments received (date | family | amount | method)
   - Linked to original invoices

6. **Settings Tab:**
   - Fee configuration: Base fee amount | Due date of month |Payment methods enabled (UPI only in Phase 1, Razorpay Phase 2)
   - [Save Settings] button

**Colors & Typography:**
- Overdue red, paid green, Fraunces for amounts

**States:**
- Empty: "No invoices created yet. Click '+ Create Invoice' to get started."
- Overdue highlighted: row background light red tint
- Loading: skeleton table rows

**Interactions:**
- Row click: expand to full invoice detail (PDF view, payment history)
- [Create Invoice]: open form modal
- [Send Reminder]: pre-filled message to parent (WhatsApp/SMS)
- [Pay] button: link to payment flow (Phase 2: Razorpay; Phase 1: manual note)
- Filter: update table in real-time
- Bulk checkbox: enable [Send Reminder] + [Mark Paid] buttons

---

### Screen A-5: Attendance Dashboard

**Prompt for Google Stitch:**

Design an Attendance Dashboard where Rajesh can see aggregate attendance %, by-class breakdown, trends, and alert on low attendance.

**Context:**
- Web, React + Vite

**Layout:**
- Sidebar + header
- Main content area:

**UI Elements:**

1. **Summary Cards (top):**
   - "Overall Attendance" | "94%" Fraunces Semibold 24sp sage green
   - "This Week" | "↓ 2%" vs last week Inter Regular 11sp
   - "Marked Absent Today" | "3 children" Fraunces Semibold 20sp terracotta
   - "On Leave" | "2 children" Fraunces Semibold 20sp

2. **Trend Chart (white card, 400×300dp):**
   - Header "Attendance Trend (14 days)" Inter Semibold 14sp
   - Line chart: dates x-axis, attendance % y-axis (80–100%)
   - Sage green line, hover shows daily value
   - Threshold line: "Target 95%" dashed red

3. **By-Class Table (white card, full-width):**
   - Columns: Class | Present | Absent | Leave | Total | % Attendance | Status
   - Status badges: good if ≥95%, warn if 90-95%, alert if <90%
   - Sample rows:
     - Nursery A | 18 | 1 | 1 | 20 | 95% | ✓
     - Nursery B | 17 | 2 | 1 | 20 | 90% | ⚠️
     - LKG A | 19 | 0 | 1 | 20 | 100% | ✓

4. **Today's Absent List (white card, half-width):**
   - Header "Marked Absent Today"
   - List: child name + class + reason (optional)
   - Link [Review] to drill into attendance form

5. **Quick Mark Attendance (white card, half-width):**
   - For today, allow quick re-mark if needed
   - Date picker + class dropdown
   - Link [Edit Attendance]

6. **Filters:**
   - Date range: "Today" | "This Week" | "This Month"
   - Class filter: "All Classes" or specific

**Colors & Typography:**
- Green for good (≥95%), orange for warn, red for alert, Fraunces for %

**States:**
- Loading: skeleton chart and table
- Filtered: table and chart update

**Interactions:**
- Chart hover: show data tooltip (date + %)
- Row click: expand class detail (day-by-day breakdown)
- Filter: real-time update
- [Edit Attendance]: navigate to A-5 detailed view (grid editor)

---

### Screen A-6: Staff Management

**Prompt for Google Stitch:**

Design a Staff Management screen where Rajesh can see all staff, invite new staff, assign classes, manage roles.

**Context:**
- Web, React + Vite

**Layout:**
- Sidebar + header
- Main content area:

**UI Elements:**

1. **[+ Invite Staff] Button:**
   - Opens form: name, phone, role (Teacher/Admin/Principal), class assignment
   - Sends SMS invite with setup link

2. **Staff Table (white card, full-width):**
   - Columns: Name | Phone | Role | Class | Last Active | Status | Actions
   - Rows:
     - Sunita | 98765 43210 | Teacher | Nursery A | 2h ago | Active | [Edit] [Message] [Remove]
     - Neha | 98754 32100 | Teacher | LKG A | 5h ago | Active | [Edit] [Message] [Remove]
     - Rajesh | 98743 21089 | Principal | All | Now | Online | [Edit] [Settings]
   - Pagination if >20 staff

3. **Filters:**
   - Role: "All Roles" | "Teachers" | "Admins"
   - Class: "All Classes" or specific
   - Status: "All" | "Active" | "Inactive"

4. **Status Indicators:**
   - Green "Online" (active in last 30 min)
   - Grey "Offline" (inactive >30 min)
   - Red "Inactive" (no login in 7 days)

5. **Bulk Actions:**
   - Checkbox column, [Message Teachers] button for selected, [Remove] with confirmation

**Colors & Typography:**
- Online green, offline grey, inactive red, Inter for body

**States:**
- Empty: "No staff yet. Click '+ Invite Staff' to add someone."
- Loading: skeleton table rows
- Invited: row shows "Pending activation" status, resend invite link available

**Interactions:**
- [Invite Staff]: form modal
- Row click: expand to full staff detail (phone, email, classes, permissions)
- [Edit]: edit form
- [Message]: pre-filled message template
- [Remove]: confirm dialog, remove staff
- Filter: update table in real-time

---

### Screen A-7: School Settings

**Prompt for Google Stitch:**

Design a School Settings page where Rajesh can manage school name, logo, timezone, payment settings, etc.

**Context:**
- Web, React + Vite
- Accessed from sidebar menu or admin gear icon

**Layout:**
- Sidebar + header
- Main content area with form sections:

**UI Elements:**

1. **School Info Section (white card, 16dp padding):**
   - Logo upload: square area with current logo (placeholder), [Upload] button
   - School name: text input, Inter Regular 13sp, default "Sunshine Preschool"
   - Address: text input
   - Phone: text input
   - Timezone: dropdown (default "IST")
   - Website (optional): text input

2. **Branding Section:**
   - Brand color picker: sage green default, custom color input
   - School motto / tagline: text area
   - Featured photo (cover image for parent feed): upload area

3. **Fee Settings Section:**
   - Monthly fee amount: currency input
   - Invoice due date: day of month selector (e.g., 10th, 15th, etc.)
   - Late fee (optional): percentage or fixed amount
   - Accepted payment methods (checkboxes): UPI (always on), Credit Card (Phase 2), Bank Transfer (Phase 2)

4. **Notification Settings:**
   - WhatsApp API Key (dummy for Phase 1, required for production)
   - SMS Fallback enabled (checkbox)
   - Email enabled (checkbox)

5. **[Save All Changes] Button (sticky at bottom):**
   - Sage green, full-width, 48dp
   - Disabled until changes made

6. **Status Message (bottom):**
   - "Last saved: Mar 10 · 2:30 PM" Inter Regular 11sp `#9A9A9A`

**Colors & Typography:**
- Form fields outlined, sage primary

**States:**
- Loading: skeleton input fields
- Unsaved changes: [Save] button highlighted, small "✕ unsaved" badge next to section header
- Saving: spinner on [Save] button
- Saved: toast "Settings saved" white on `#4A8C5C`
- Error: inline error message below field in red

**Interactions:**
- Any input change: [Save] button highlights
- [Save]: persist to backend
- Logo upload: file picker, preview in real-time
- Color picker: open color wheel or hex input

---

### Screen A-8: Reports & Analytics

**Prompt for Google Stitch:**

Design a Reports screen where Rajesh can view detailed analytics, export data (attendance, engagement, fees), and access historical trends.

**Context:**
- Web, React + Vite
- Advanced analytics / BI layer

**Layout:**
- Sidebar + header
- Main content area with tabs: Engagement | Attendance | Fees | Admissions

**UI Elements (Engagement Tab — default):**

1. **Date Range Selector (top):**
   - "From: Mar 1" | "To: Mar 31" | [Apply]
   - Quick options: "This Month" | "Last 30 Days" | "Last Quarter"

2. **Summary Stats (cards):**
   - Total posts | Avg posts/day | Avg posts/class | Avg comments/post
   - All with trend indicators (↑ green, ↓ red, → grey)

3. **Detailed Charts:**
   - Posts per day (line)
   - Posts per class (bar)
   - Parent engagement rate (line, %)
   - Comment trends (area)
   - Busiest times of day (heatmap)

4. **Detailed Tables:**
   - Posts by class (sortable, filterable)
   - Posts by teacher (sortable)
   - Engagement per post (linked to actual post)

5. **[Export Report] Button:**
   - Dropdown: "PDF" | "CSV" | "Excel"
   - Generate and download file

6. **Attendance Tab:**
   - By-class attendance %, trends
   - Absent/leave patterns
   - [Export Attendance Log]

7. **Fees Tab:**
   - Collections by month, trend
   - Outstanding aging
   - Top/bottom payers
   -[Export Fee Report]

8. **Admissions Tab:**
   - Conversion funnel over time
   - Source attribution
   - Lead-to-enrollment time
   - [Export Admissions Report]

**Colors & Typography:**
- Charts in sage/terracotta palette, Inter for labels

**States:**
- Loading: skeleton charts
- Date range changed: charts update with transition animation
- Exporting: [Export] shows spinner + "Generating PDF…"

**Interactions:**
- Chart legend click: toggle series visibility
- Table row click: drill into detail (drill-down)
- Date range: real-time filter
- Export: generate file, download via browser

---

### Screen A-9: Fees & Payments Overview (KPI Dashboard)

For now, A-9 can be a consolidated view of "Fees at a Glance" combining key metrics (outstanding, collected, overdue) accessible from A-1, or reuse A-4 (Fee Management) as the primary. If a separate lite dashboard is needed, show just KPI cards + trends without full management forms.

---

### Screen A-10: Admissions Overview (Funnel & Analytics)

For now, A-10 can reuse A-3 (Admissions Pipeline) as the primary, or create a separate analytics view of funnel conversion rates, source attribution, recruitment effectiveness over time. Keep it lightweight and actionable.

---

### Screen A-11: Child Records & Compliance

**Prompt for Google Stitch:**

Design a Child Records master list where Rajesh can view all children, manage medical info, access permissions audit, and ensure compliance.

**Context:**
- Web, React + Vite

**Layout:**
- Sidebar + header
- Main content area:

**UI Elements:**

1. **Master Child List (white card, full-width):**
   - Columns: Child Name | DOB | Class | Linked Parents | Medical Notes | Incidents | Perms | Actions
   - Rows: clickable to expand detail
   - Filters: Class, medical alerts (allergies), incident history
   - Bulk actions: [Export Records], [Send Medical Form Reminder]

2. **[+ Add Child] Button:**
   - Opens form: name, DOB, class assignment, parent linking, upload enrollment photo
   - Triggers face recognition setup

3. **Medical Alerts (highlighted rows):**
   - Any child with critical allergies or conditions shows in yellow/red row
   - Quick view: hover shows allergy badges

4. **Search & Filters:**
   - Search by name Inter Regular 13sp placeholder "Search children…"
   - Class filter
   - Medical status filter (has allergies, medical conditions, etc.)

5. **Detail Modal (on row click):**
   - Child info, profile photo, DOB
   - Linked parents + contacts
   - Medical information (allergies, conditions, medications, doctor info)
   - Incidents (linked to child records)
   - Permissions audit (photo consent, AI consent date, DPDP opt-in status)
   - [Edit] buttons per section

6. **Permissions & Compliance Section:**
   - "Photo Usage Consent: ✓ Approved (Mar 5, 2024)"
   - "AI Photo Analysis: ✓ Approved (Mar 5, 2024)"
   - "DPDP Consent: ✓ Accepted (Mar 5, 2024)"
   - [Audit Trail] link shows who consented, when, revisions

7. **Bulk Export:**
   - [Export Child Records] button: CSV/PDF of all children + medical info
   - Compliance: anonymized option for reports

**Colors & Typography:**
- Red for allergies, green for approved consent, Inter body

**States:**
- Loading: skeleton table rows
- Empty: "No children yet. Click '+ Add Child' or bulk import from CSV"
- Medical alert: row background yellow/red tint
- Filtered: show only matching children

**Interactions:**
- Row click: expand detail modal
- [Edit]: edit form for each section
- [Upload] (medical docs): file picker
- Filter: real-time update
- [Export]: generate and download CSV/PDF

---

### Screen A-12: Staff Overview & Activity

For now, A-12 can reuse A-6 (Staff Management) as the primary interface. If a separate analytics dashboard is needed, show staff activity metrics (posts last 7 days, login frequency, average posting rate), teacher performance trends, and quick messaging.

---

### Screen A-13: Admin Login

**Prompt for Google Stitch:**

Design the Admin login screen for Rajesh to access the dashboard.

**Context:**
- Web, React + Vite
- Entry point to admin dashboard

**Layout:**
- Background: `#FAF7F2` (warm cream), full bleed
- Centered form, 60% of viewport height, max-width 400dp

**UI Elements:**

1. **Header:**
   - CadenceSprout logo (text: Fraunces, 32sp `#1A1A1A`)
   - "Admin Dashboard" Inter Semibold 14sp `#6B6B6B`, centered

2. **Form:**
   - Email input: label "Email" Inter Regular 13sp, field 48dp outlined, placeholder "admin@sunshine.com"
   - Password input: label "Password" Inter Regular 13sp, field 48dp outlined, toggle eye icon
   - [Log In] button: full-width 48dp, sage green `#5C8B6E`, "Log In" Inter Semibold 15sp white
   - Secondary: "Forgot password?" link Inter Regular 12sp `#5C8B6E`

3. **Support CTA (bottom):**
   - "Need help? Contact support@cadencesprout.com" Inter Regular 11sp `#9A9A9A`

**States:**
- Loading: [Log In] shows spinner
- Error: below password, inline error "Invalid credentials" Inter Regular 13sp `#C0392B`, shake animation
- Success: transition to A-1 dashboard

**Interactions:**
- [Log In] tap: validate, submit, transition on success, show error on failure
- Keyboard: standard form focus

---

## Section 4.4 — Teacher Web (React + Vite)

Web twins of Teacher Mobile (T-*) screens. Behavior parity required.

**Important:** All Teacher Web screens must expose the same AI signals, notification indicators, and engagement insights as their mobile counterparts. No feature should be hidden or degraded on web.

---

### Screen TW-1: Teacher Web Login

**Prompt for Google Stitch:**

Design a login screen for teachers to access the web version of CadenceSprout.

**Context:**
- Web, React + Vite
- Desktop-first (1920×1080)

**Layout:**
- Background: `#FAF7F2`, full bleed
- Centered form, 40% of viewport width, max-width 380dp

**UI Elements:**

1. **Branding:**
   - CadenceSprout wordmark (Fraunces Semibold 32sp)
   - School logo placeholder (sun+leaf, 64dp circular)
   - "Teacher Login" Inter Semibold 16sp `#6B6B6B`

2. **Form:**
   - Phone input: label "Phone number" +91 prefix, field 48dp outlined, numeric
   - Password input: field 48dp, toggle eye icon
   - [Log In] button: full-width 48dp, sage green

3. **Footer:**
   - "Powered by CadenceSprout" Inter Regular 11sp `#9A9A9A`

**States:**
- Identical to T-0 (mobile), but desktop-optimized layout

**Interactions:**
- Standard form submission, transition to TW-2 on success

---

### Screen TW-2: Teacher Web Home Feed

**Prompt for Google Stitch:**

Design the Teacher Web Home Feed. This is the web equivalent of T-1 (mobile). Must have feature parity: nudges, engagement insights, post creation access.

**Context:**
- Web, React + Vite
- Desktop-wide layout (2-column or 3-column possible)
- Same engagement metrics as T-1

**Layout:**
- Top fixed header: school logo + class selector dropdown + notification bell + profile icon
- Left sidebar (160dp fixed): navigation menu — Home (active sage green), Attendance, Roster, Milestones, Profile
- Main content area:
  - Optional right sidebar: recent actions, notifications summary (sticky)

**UI Elements:**

1. **Daily Status Banner (full-width, below header):**
   - Date + status line + CTA chip
   - Identical to T-1 daily banner

2. **Post Feed (scrollable center column, 2-column or 1-column):**
   - Post cards: same as T-1, but can be wider (full content column width)
   - 2 full cards visible above fold
   - Partial 3rd card at bottom signals scrollability

3. **Nudge Treatment:**
   - When no post today: banner prominently shows emotional nudge copy + [Share a moment] CTA
   - FAB replacement: web uses a sticky [+ New Post] button at bottom-right or in header

4. **[+ New Post] Button/FAB:**
   - Fixed bottom-right, 56dp circle, or top-right header button
   - When no post today: soft pulsing animation (same as mobile)

5. **Parent Engagement Indicator:**
   - Same as T-1: "14 / 18 parents viewed" per post

**Colors & Typography:**
- Identical palette to T-1

**States:**
- Skeleton loading, empty, nudge state — matched to T-1

**Interactions:**
- Post card click: expand to T-3 (Post Detail) view in modal or new page
- [+ New Post]: open T-2 (Composer) in modal or new page
- Tab navigation: instant, no loading
- Pull-to-refresh: not applicable on web, but refresh icon in header

---

### Screen TW-3: Teacher Web Post Composer

**Prompt for Google Stitch:**

Design the Post Composer for web. Feature parity with T-2, but optimized for desktop (drag-drop media, larger preview).

**Context:**
- Web, React + Vite
- Can be modal over TW-2 or full-page

**Layout (Modal):**
- Centered modal, ~800dp wide, scrollable content
- Modal header: close button + "New Post"
- Body: vertical layout

**UI Elements:**

1. **Media Upload Zone (top):**
   - Drag-drop area or file picker: "Drag photos/videos here or click to select"
   - Shows thumbnail preview if media selected (larger than T-2 on mobile)
   - Multiple media carousel: thumbnails of selected files, add more button

2. **Caption Field:**
   - Large multiline textarea (8 lines visible), placeholder "What happened in this moment?"
   - Fraunces Italic 16sp
   - Top-right ✨ badge and "AI drafted" label when AI caption ready

3. **Child Tagging:**
   - Label "Children in this moment" Inter Semibold 12sp
   - Chips row: confirmed (solid sage) + AI-suggested (dashed, with confidence % and quick ✓/✕ icons)
   - "Add manually +" text link at end, opens child picker modal/dropdown

4. **Milestones (optional):**
   - Collapsible section: "Add milestones (optional) ›" — reveals checkbox list or search picker

5. **Class Row:**
   - Dropdown/selector: "LKG A" — tappable to change class

6. **Bottom Action Bar:**
   - Left: optional "[Draft]" or "Save" link (auto-save happens server-side, but option to explicitly save as draft)
   - Right: [Discard] (red, outlined) | [POST] (sage green, filled)

**Colors & Typography:**
- Palette matched to T-2
- Typography: Fraunces for captions, Inter for labels

**States:**
- AI caption loading: shimmer, same as T-2
- Media uploading: progress bar per file
- Ready to post: [POST] button enabled

**Interactions:**
- Drag-drop media: accepts multiple files
- Media thumbnail: click to remove or reorder
- Child chip ✓/✕: confirm/remove AI tag
- Add manually +: open child list modal/dropdown (dropdown on web is cleaner than modal)
- [POST]: submit, show toast confirmation, close modal, refresh TW-2 feed

---

### Screen TW-4: Teacher Web Attendance

**Prompt for Google Stitch:**

Design the Attendance marking screen for web. Optimize for bulk marking (table layout preferred).

**Context:**
- Web, React + Vite

**Layout:**
- Sidebar + header
- Main content area:

**UI Elements:**

1. **Header Row:**
   - Left: "Attendance" Inter Semibold 16sp + date picker "Today"
   - Right: quick buttons "Mark All Present" | "Mark All Absent" | "Undo"

2. **Attendance Table (full-width, white card):**
   - Columns: Child Name | Present | Absent | Leave
   - Each status is a radio button or button toggle (not a pill like mobile)
   - Rows: 12-20 children depending on class size (paginate if >20)
   - Bottom row: summary "Present: 18 | Absent: 1 | Leave: 1"

3. **Bulk Actions:**
   - [Mark All Present], [Mark All Absent], [Undo] buttons at top
   - Interact with table state instantly

4. **[SAVE] Button (sticky at bottom):**
   - Full-width, 48dp, sage green

**Colors & Typography:**
- Present: sage green background on row if selected
- Absent: light red background
- Leave: light yellow background
- Matched to T-4 mobile

**States:**
- Loading: skeleton table rows
- Unsaved changes: [SAVE] button highlights
- Saved: toast "Attendance saved" white on `#4A8C5C`

**Interactions:**
- Table cell click: toggle state (cycle through Present → Absent → Leave → unmarked)
- Mark All buttons: set all rows to that state instantly
- [SAVE]: validate all marked, persist

---

### Screen TW-5: Teacher Web Class Roster

**Prompt for Google Stitch:**

Design the Roster for web. Table layout with filtering, sorting, parent management.

**Context:**
- Web, React + Vite

**Layout:**
- Sidebar + header
- Main content area:

**UI Elements:**

1. **Header:**
   - "Class Roster" Inter Semibold 16sp + class selector "LKG A"
   - Search input: "Search child…" Inter Regular 13sp
   - [+ Add Child] button (for admins/teachers who can add)

2. **Roster Table (full-width, white card):**
   - Columns: Child | Age | Attendance % | Linked Parent | Recent Posts | Actions
   - Rows: children in class (paginated if >20)
   - Click row: expand or navigate to T-5A (Child Detail)

3. **Actions Column:**
   - [View Child] button → navigates to T-5A
   - [Link Parent] link (if parent not linked)
   - [Message Parent] link → pre-filled SMS/WhatsApp
   - Three-dot menu: delete, edit, etc.

4. **Filters (above table):**
   - "All children" | "With parents" | "No parents linked" filter chips
   - Search in real-time as typing

**Colors & Typography:**
- Matched to T-5 mobile

**States:**
- Loading: skeleton table rows
- Empty: "No children in this class"
- Filtered: show matching children only

**Interactions:**
- Row click: expand to detail view (modal or drawer) or navigate to T-5A
- Search: filter in real-time
- [Link Parent]: open modal with phone number input + send invitation
- [Message Parent]: open pre-filled SMS/WhatsApp modal

---

### Screen TW-6: Teacher Web Milestones Tracker

**Prompt for Google Stitch:**

Design the Milestones Tracker for web. Table or card layout showing milestone progress by domain/child.

**Context:**
- Web, React + Vite

**Layout:**
- Sidebar + header
- Main content area with toggle: "By Domain" | "By Child" view

**UI Elements (By Domain View):**

1. **Domain Cards (grid or list):;**
   - Each card: domain name "Social-Emotional" + progress bar (4/8) + expand chevron
   - Expand reveals: list of milestones under that domain (checkboxes, if editable)

**UI Elements (By Child View):**

1. **Child Table:**
   - Columns: Child | Milestones Achieved | Domain Breakdown | Progress % | View
   - Rows: one per child in class
   - Domain Breakdown column: "SE: 2 | PD: 2 | Cog: 2 | Lang: 1 | Creat: 1"

2. **Interactions:**
   - Click child row: expand to show all milestones achieved for that child + AI suggestions
   - Toggle "By Domain" ↔ "By Child": switch view

**Colors & Typography:**
- Matched to T-6 mobile

**States:**
- Loading: skeleton cards/rows
- Empty: "No milestones recorded yet"

---

### Screen TW-7: Teacher Web Profile / Settings

**Prompt for Google Stitch:**

Design the Profile & Settings page for web.

**Context:**
- Web, React + Vite

**Layout:**
- Sidebar + header
- Main content area: form sections

**UI Elements:**

1. **Profile Section:**
   - Avatar (circular 64dp), name, phone, role
   - [Edit Profile] button → opens edit form

2. **Class Assignment:**
   - Current class dropdown/selector
   - [Change Class] button

3. **Notifications Section:**
   - Checkboxes: "Parent reactions", "Daily nudge", "Push notifications"
   - [Save Preferences] button

4. **[Logout] Button:**
   - Red outlined, bottom of page

**Colors & Typography:**
- Matched to T-7 mobile

**Interactions:**
- Edit inputs: [Save] button
- Toggles: auto-save or [Save] button
- [Logout]: confirm dialog

---

## Section 4.5 — Parent Web (React + Vite)

Web twins of Parent Mobile screens. Full parity required.

---

### Screen PW-1: Parent Web Magic-Link Landing (Feed First)

**Prompt for Google Stitch:**

Design the magic-link web view that a parent lands on after tapping a WhatsApp/SMS link. Show the child's feed immediately (no password), with optin for email/personalization.

**Context:**
- Web, React + Vite
- Desktop-first, but responsive to mobile browsers
- Entry point: magic-link URL from WhatsApp/SMS

**Layout:**
- Minimal header (just logos, no auth button since already authenticated via link token)
- Full-width feed view, similar to PW-2 but onboarding-focused

**UI Elements:**

1. **Welcome Banner (above feed):**
   - "Welcome back, Meera! 👋" Inter Semibold 16sp `#1A1A1A`
   - "Here are [Child]'s latest moments from school" Inter Regular 14sp `#6B6B6B`
   - [Dismiss] link right side

2. **Feed (full-width):**
   - Same as PW-2 Parent Feed, but no header menu initially
   - 2-3 full post cards visible above fold

3. **Optional CTA (sticky at bottom or in header):**
   - "[Install App for Notifications]" light button (or skip link)
   - "This link works forever — save it or install the app for easier access"

4. **Simplified Header (top 56dp, white surface):**
   - Left: school logo (40dp) + "Sunshine Preschool"
   - Right: notification bell (grey, not active since not authenticated app account)
   - No menu/tabs (keep simple for first-time experience)

**Colors & Typography:**
- Warm palette, Fraunces for welcome headline, Inter for body

**States:**
- Loading: skeleton cards
- Empty: "No updates yet from [Teacher]" placeholder

**Interactions:**
- Post card tap: navigate to PW-3 (Post Detail)
- Install App CTA: link to app store
- Dismiss banner: banner fades, feeds full to viewport

---

### Screen PW-2: Parent Web Full Feed (After OTP / Signup)

**Prompt for Google Stitch:**

Design the full Parent Feed for web after signup/login. This is the primary engagement surface for web-based parents.

**Context:**
- Web, React + Vite
- Desktop-first (1920×1080), responsive to tablet+
- Authenticated view with full menu access

**Layout:**
- Top fixed header (56dp, white surface):
  - Left: school logo (40dp) + school name + child name "Rohan"
  - Center: (empty space)
  - Right: notification bell (with red badge if unread), user profile dropdown
- Left sidebar (200dp fixed, white surface):
  - Navigation: Feed (active sage green) | Milestones | Portfolio | Profile
  - Settings link at bottom
  - Logout button at bottom
- Main content area (center, scrollable):
  - Feed: post cards in timeline view (single column or 2-column layout)
- Right sidebar (optional, 240dp, sticky):
  - Weekly digest preview / Today's summary / Quick links

**UI Elements (Feed Content):**

1. **Post Cards (full-width center column, ~600dp max-width, margin auto):**
   - Same card structure as P-3 mobile: photo, caption, child chip, metadata, reactions
   - Wider on desktop, card can show more detail
   - Hover effects: slight shadow increase, opacity change on buttons

2. **Reaction / Comment Section (below each post in card):**
   - Reactions: [❤️] [😊] [👏] [➕] buttons
   - "3 reactions, 2 comments" meta line
   - Expandable comments section (click to show comments)

3. **Pull to Refresh (optional, or just refresh button in header):**
   - Refresh icon in header top-right, click to refresh

4. **Right Sidebar (optional, sticky):**
   - "This Week" summary: "5 posts, 12 reactions from you"
   - "Today's Highlights" (2-3 key posts)
   - "Quick Links" (Portfolio, Milestones, Settings)

**Colors & Typography:**
- Warm cream background, white cards, sage primary, Fraunces captions, Inter body

**States:**
- Loading: skeleton cards (shimmer animation)
- Empty: "No updates yet. Check back soon!" placeholder
- Offline banner: persistent top banner "You're offline — showing cached posts" Inter Regular 13sp

**Interactions:**
- Post card click: expand to PW-3 (Post Detail) in modal or navigate to new page
- Reaction button: toggle reaction (heart fills red on click), count updates
- Comments expand: show/hide comment thread inline
- Tab navigation (left sidebar): instant switch between Feed, Milestones, Portfolio
- Notification bell: navigate to notification center (if implemented)

---

### Screen PW-3: Parent Web Post Detail

**Prompt for Google Stitch:**

Design the Post Detail page for web. Allows full viewing, commenting, reactions, sharing.

**Context:**
- Web, React + Vite
- Can be modal over PW-2 or full-page navigation

**Layout (Full page):**
- Same header + sidebar as PW-2
- Main content area: centered post detail view

**UI Elements:**

1. **Post Container (max-width 800dp, centered):**
   - Back link "← Back to Feed" top-left in smaller text Inter Regular 12sp `#5C8B6E`

2. **Post Content:**
   - Full-bleed photo (16:9 or 4:3 ratio, responsive)
   - Below photo: white card with padding
     - Caption: Fraunces Italic 18sp `#1A1A1A`
     - Child chip: sage green pill
     - Metadata: "Posted by Sunita · 2 hours ago" Inter Regular 12sp

3. **Reactions Bar (full-width card below post):**
   - Row: "3 reactions · 2 comments"
   - Reaction buttons: [❤️] [😊] [👏] [➕]
   - Share button: [Share] (iOS share sheet or pre-filled social links)
   - Save button: [Save to Portfolio]

4. **Comments Section (full-width card below reactions):**
   - Header: "Comments (2)" Inter Semibold 14sp
   - Comment list: each comment — avatar + parent name + timestamp + comment text
   - If teacher reply: indented, sage-tinted background
   - [Load more comments] link if >5

5. **Reply Composer (sticky at bottom or in card):**
   - Text input + [Send] button (or keyboard return/cmd-enter)
   - Grows as user types up to 3-4 lines, then scrolls
   - Green send button only appears when text present

6. **Right Sidebar (optional):**
   - Quick info: posting teacher, child, date
   - Related posts from teacher (thumbnails)

**Colors & Typography:**
- Cream background, white cards, sage primary, Fraunces captions

**States:**
- Loading: skeleton photo + comment cards
- No comments: "Be the first to comment!" placeholder
- Typing reply: input field border turns sage green

**Interactions:**
- Back link: navigate to PW-2 or close modal
- Reaction button: toggle state (fill with color on active), count updates
- Comments expand: reveal full comment thread
- Reply input: keyboard captures focus, grows as typing
- [Send] reply: optimistic UI shows comment, [SYSTEM] offline queue handles sync
- [Share]: open social share options (email, WhatsApp, copy link)
- [Save to Portfolio]: bookmark post, add to memory book

---

### Screen PW-4: Parent Web Milestone Progress

**Prompt for Google Stitch:**

Design the Milestones view for web. Show developmental progress by domain with evidence posts linked.

**Context:**
- Web, React + Vite

**Layout:**
- Same header + sidebar as PW-2
- Main content area:

**UI Elements:**

1. **Overview Card (top):**
   - "Your child's progress" Inter Semibold 18sp
   - "8 of 40 milestones achieved (20%)" Inter Regular 14sp
   - Overall progress bar

2. **Domain Cards (grid or vertical cards, 6-column layout on desktop, responsive):**
   - Each domain card: 12dp radius, white surface, 16dp padding
   - Domain name "Social-Emotional" Inter Semibold 14sp
   - Progress bar "2 of 8" Inter Regular 11sp
   - [View Details] link → expand to show all milestones in that domain

3. **Expanded Domain View (modal or below):**
   - Grid of milestone badges: achieved ones are filled sage green with checkmark, pending ones are outlined `#E8E2D9`
   - Each milestone badge: 64dp circle, icon + name, clickable
   - Milestone detail (on click): show linked post evidence (photo + caption)

4. **Recent Achievements (below domains):**
   - "Just Achieved" small section
   - 2-3 latest milestone badges with "2 days ago" timestamp

**Colors & Typography:**
- Sage for progress/achieved, cream background, Fraunces for milestone names

**States:**
- Loading: skeleton cards
- Empty: "Milestones will appear as Rohan grows!" placeholder

**Interactions:**
- Domain card click: expand to show all milestones, scroll within
- Milestone badge click: show linked post(s) as evidence modal/lightbox
- Back: collapse domain view

---

### Screen PW-5: Parent Web Profile / Settings

**Prompt for Google Stitch:**

Design the Profile page for web.

**Context:**
- Web, React + Vite

**Layout:**
- Same header + sidebar as PW-2, but Profile tab active
- Main content area: profile form sections

**UI Elements:**

1. **Profile Section (white card, 16dp padding):**
   - Avatar (64dp circular) + name "Meera" (editable)
   - Phone, role (Mother/Father/Guardian), linked child
   - [Edit] button → edit form

2. **Linked Guardians (white card):**
   - List: "Rakesh (Father) · 98754 32100"
   - [+ Add Guardian], [Edit], [Remove] links per guardian

3. **Preferences (white card):**
   - Notification toggles (same as P-13)
   - Language selector
   - Theme (light/dark)

4. **[Logout] Button (bottom, red outlined, full-width 48dp)**

**Colors & Typography:**
- Warm palette, Fraunces for headings, Inter for inputs

**Interactions:**
- [Edit]: open form modal or inline editing
- [Add Guardian]: phone input form
- Toggles/selects: auto-save or [Save] button
- [Logout]: confirm, clear session

---

### Screen PW-6: Parent Web Privacy Settings (DPDP Consent Management)

**Prompt for Google Stitch:**

Design the privacy control page for web. Identical to P-14 (mobile) but optimized for desktop layout.

**Context:**
- Web, React + Vite
- Same compliance requirements

**Layout:**
- Same header + sidebar
- Main content area: form sections

**UI Elements:**
- Identical to P-14, but form sections laid out horizontally or in wider columns
- Same toggles for AI consent, photo consent
- [Download Data] button, [Delete Account] button with confirmation dialogs

**Colors & Typography:**
- Privacy-appropriate (clear, not scary), red for deletion

**States:**
- Downloading: spinner + progress
- Deleting: confirmation dialog + 30-day notice
- Saved: toast "Preferences saved"

**Interactions:**
- Toggles: immediate state change
- [Download Data]: initiate export, download when ready
- [Delete Account]: confirm dialog, initiate deletion

---

## End of Stitch Prompts

All screens have been designed with complete specification for Google Stitch UI generation. Each prompt includes:
- Layout structure (desktop/mobile-specific)
- UI element definitions with colors, typography, spacing
- Component states and variations
- Interaction patterns and animations
- [SYSTEM] callouts for backend implementation (AI, offline, notifications, etc.)

Use these prompts with Google Stitch to generate high-fidelity UI prototypes and implementation code.

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

