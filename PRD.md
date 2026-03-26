# CadenceSprout — Phase 1 PRD
**All-in-One Preschool OS for Indian Preschools**

- **Author:** Alex (PM)
- **Date:** 2026-03-26
- **Status:** Draft
- **Version:** 1.0
- **Reviewed by:** CEO Review ✓ | Design Review ✓ | Eng Review ✓

---

## Table of Contents

1. [Executive Summary](#1-executive-summary)
2. [User Personas](#2-user-personas)
3. [Phase 1 Epics and User Stories](#3-phase-1-epics-and-user-stories)
4. [Screen Inventory](#4-screen-inventory)
5. [Key API Contracts](#5-key-api-contracts)
6. [Non-Functional Requirements](#6-non-functional-requirements)
7. [Out of Scope — Phase 2 and Phase 3](#7-out-of-scope--phase-2-and-phase-3)
8. [Success Metrics](#8-success-metrics)

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

Phase 1 is organized into 8 epics covering the complete product. All stories are scoped to deliver Phase 1 launch criteria (Month 10).

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

### Epic 3: Teacher Post Flow (The Core Loop)
**Goal:** Enable a teacher to post a class activity in ≤3 taps, with AI-generated caption and child tags.
**Priority:** P0 — this is the product's primary daily usage loop.
**Timeline:** Month 3-4 (feed) + Month 5-6 (AI layer)

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
- Given face recognition returns results, then chips with confidence > 90% show as suggested (green chip, child name), and chips with 70-90% show with a low-confidence indicator. Chips with < 70% confidence are not shown
- Given I tap a chip to confirm a tag, then the chip turns solid and the child's name appears in the caption draft if applicable
- Given I tap a chip to remove a suggested tag, then the child is removed from `post_children` and will not appear in parents' feeds
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
- Given the upload fails (network drop), then a toast appears: "Upload failed. Tap to retry." The post remains visible in my feed as a draft with a retry indicator
- Given I tap retry, then the upload resumes with exponential backoff (retry 1: 5s, retry 2: 10s, retry 3: 20s)
- Given the post is published, then a Pusher event is broadcast to all parents of tagged children on the `class.{class_id}.feed` channel
- Given the post is published, then a Wapi WhatsApp notification is sent to parents of tagged children (or all class parents if no specific tags): "[School name]: [Child name] had a great moment today! See it here: [magic-link]"

---

**Story 3.6: Teacher Home Feed**
As a teacher, I want to see all posts for my class so that I know what has been shared today.

Acceptance Criteria:
- Given I open the app, then the Home Feed shows posts for my class in reverse chronological order (most recent first)
- Given the feed loads, then I see for each post: full-bleed photo, caption in Fraunces font, child tags, posted time, and a "viewed by X parents" count
- Given my class has no posts yet, then I see: "Add your students to get started." with a button to the Class Roster
- Given there are no posts today but prior posts exist, then recent posts are shown with today's date section header showing "No posts yet today"
- Given I pull to refresh, then new posts load
- Given the network is unavailable, then a persistent banner at the top shows "You're offline — showing saved content"
- Given I tap a post, then I see the Post Detail screen with full photo, full caption, child tags, milestone tags, and parent view count

---

### Epic 4: Parent Feed Experience
**Goal:** Give parents a beautiful, reliable daily window into their child's school day.
**Priority:** P0
**Timeline:** Month 3-6

---

**Story 4.1: Parent Home Feed**
As a parent, I want to see my child's feed showing only posts where my child is tagged so that I see a personalized view.

Acceptance Criteria:
- Given I open the parent app, then I see posts in reverse chronological order where my child is tagged (confirmed by teacher)
- Given a post exists where my child is not tagged but the class posted, then that post is NOT shown in my personal feed
- Given the feed is loading, then I see skeleton cards (warm cream rectangles, pulsing) — not a spinner
- Given no posts exist yet, then I see an illustration with: "Your child's first update will appear here soon. Teachers usually post after morning circle." — no CTA
- Given there are no posts today but prior posts exist, then recent posts are shown with a "No updates today yet — check back after morning circle!" section header
- Given the network fails, then I see: "Couldn't load — check your connection." with a Retry button. Previously loaded content remains visible (stale-while-revalidate)
- Given I scroll to the bottom of the feed, then the next page loads automatically (cursor-based pagination)

---

**Story 4.2: Post Detail and Reactions**
As a parent, I want to react to a post and add a comment so that the teacher knows I saw it.

Acceptance Criteria:
- Given I tap a post in the feed, then I see a full-screen photo view with the caption, child tags, milestone tags (if any), post time, and school logo
- Given I tap the ❤️ reaction button, then my reaction is recorded immediately and the count increments
- Given I want to comment, then I can type a comment that is visible to the teacher in the Post Detail view
- Given a teacher sees a parent's comment, then they receive an in-app notification
- Given the teacher's post had an AI-drafted caption that was not edited, then there is no visible indication that AI wrote it — it appears as the teacher's own words

---

**Story 4.3: Milestone Progress View**
As a parent, I want to see a summary of which developmental milestones my child has crossed so that I understand their progress.

Acceptance Criteria:
- Given I navigate to my child's profile, then I see a "Milestones" section showing progress by domain (physical, cognitive, language, social-emotional, aesthetic)
- Given a milestone has been teacher-confirmed on a post, then it shows as achieved with the date
- Given no milestones have been logged yet, then I see: "Milestones will appear here as teachers observe them in class." — no CTA, educational tone
- Given I tap a milestone, then I see the posts where that milestone was observed (photo + caption)

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

### Epic 7: Admin Dashboard & Engagement Score
**Goal:** Give principals a single-screen morning check that tells them if their schools are healthy.
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

### Epic 8: Admissions Management
**Goal:** Enable schools to track inquiries through to enrollment, replacing paper registers and WhatsApp-based admission tracking.
**Priority:** P1 (important for ERP completeness; not the first thing schools care about)
**Timeline:** Month 7-8

---

**Story 8.1: Admissions Inquiry Capture**
As a school admin, I want to record a new inquiry so that I don't lose track of prospective parents.

Acceptance Criteria:
- Given I navigate to Admissions, when I tap "New Inquiry", then I can enter: parent name, phone number, child name, child age, class of interest, inquiry source (Walk-in / Phone / Referral / Social media / Other)
- Given I save the inquiry, then it appears in the Admissions pipeline with status: New Inquiry
- Given I tap an inquiry, then I can view all fields, add notes, and update the status

---

**Story 8.2: Admissions Pipeline Stages**
As a school admin, I want to move inquiries through stages so that I know where each prospective child is in the process.

Acceptance Criteria:
- Given an inquiry exists, then it can be moved through these stages: New Inquiry → Tour Scheduled → Tour Done → Seat Offered → Enrolled → Not Joining
- Given I move a record to "Enrolled", then I am prompted to create a child profile from the inquiry data (pre-fills name, DOB, class)
- Given an inquiry has been in the same stage for > 14 days, then it shows a "Follow up?" indicator in the pipeline view
- Given I mark an inquiry as "Not Joining", then it moves to an archived state but is not deleted

---

**Story 8.3: Enrollment to Child Profile**
As a school admin, I want to convert an admitted inquiry into a full child profile so that I don't have to re-enter the data.

Acceptance Criteria:
- Given I convert an inquiry to enrollment, then a child profile is pre-created with the inquiry data (name, DOB, class)
- Given the child profile is created from enrollment, then I am immediately prompted to: (1) upload an enrollment photo for face recognition, and (2) add parent phone numbers for magic-link invitation
- Given I complete these steps, then the child appears in the teacher's class roster and the parent invitation is sent

---

## 4. Screen Inventory

This section maps every screen in the product to its role, purpose, route, and key elements.

---

### 4.1 Teacher App (React Native — iOS + Android)

---

**Screen T-1: Home Feed (Class Feed)**
- Route: `/` (default tab)
- Entry point: App launch, bottom nav tab 1
- Purpose: Show all posts for the teacher's class; primary daily landing screen

Key elements:
- School logo + class name in header
- Post cards: full-bleed photo (4:3), caption in Fraunces font, child tag chips, time ago, parent view count
- FAB (floating action button, sage green, bottom right) — always visible
- Bottom tab nav: Feed | Attendance | Roster | Profile

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| Loading | App opens | Skeleton cards — warm cream pulsing rectangles |
| Empty (new class, 0 students) | No children added yet | "Add your students to get started." + Add Students button |
| No posts today | Class exists, posts exist but not today | Past posts visible, today's section header: "No posts yet today" |
| Normal | Posts exist | Reverse-chronological post feed |
| Offline | No network | Persistent top banner "You're offline — showing saved content" |

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

**Screen T-6: Milestone Tracker (per child)**
- Route: `/child/:id/milestones`
- Entry point: Tap child in Roster → Milestones tab
- Purpose: View and add milestone observations for a specific child

Key elements:
- Domain tabs: Physical | Cognitive | Language | Social-Emotional | Aesthetic
- Milestone list: milestone name, age range, achieved / not yet, date achieved
- "Observed in post" link (taps through to the post where milestone was tagged)
- Add milestone button (opens NEP 2020 taxonomy picker)

States:
| State | Trigger | What the teacher sees |
|---|---|---|
| No milestones logged | New child, no posts with tags | "Milestones will appear here as you observe them in class." |
| Milestones present | Posts with milestone tags exist | Domain-grouped list with achieved milestones highlighted |

---

**Screen T-7: Profile / Settings**
- Route: `/profile` (bottom nav tab 4)
- Entry point: Bottom nav
- Purpose: Teacher account settings, notification preferences, logout

Key elements:
- Teacher name and photo
- School name
- Notification preferences toggle
- App version
- [Log Out] button

---

### 4.2 Parent App (React Native — iOS + Android)

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

**Screen P-3: Parent Home Feed**
- Route: `/` (default tab)
- Entry point: App launch
- Purpose: Personalized feed of posts where the parent's child is tagged

Key elements:
- School logo + "Good morning, [Parent name]" greeting
- Post cards: full-bleed photo, caption in Fraunces font, child tag, time ago
- Reaction button (❤️) on each card
- Bottom tab nav: Feed | Milestones | Portfolio | Profile

States:
| State | Trigger | What the parent sees |
|---|---|---|
| Loading | App opens | Skeleton cards — warm cream pulsing rectangles |
| Empty (not yet enrolled) | Child profile exists but no posts | "Your child's first update will appear here soon." + WhatsApp school link |
| Empty (child not added) | Parent account exists but no child linked | "Ask your school to add you to [School Name]." + WhatsApp school link |
| No posts today | Posts exist but not today | Past posts visible; "All quiet so far today. Check back after morning circle!" header |
| Network error | No connection | "Couldn't load — check your connection." + Retry. Stale content stays visible |
| Normal | Posts exist | Reverse-chronological feed of tagged posts |

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

### 4.3 Admin / Principal Web Dashboard (React + Vite)

---

**Screen A-1: Dashboard Home**
- Route: `/dashboard`
- Entry point: Login redirect, sidebar nav
- Purpose: Morning check-in — one screen to know if schools are healthy

Key elements:
- Engagement score hero: large number, trend arrow, delta label
- Three metric tiles: Posts Today | Attendance Today | Fee Alerts
- Class Breakdown table (sorted by engagement %, lowest first)
- "Message teacher" quick-action per class row (opens WhatsApp pre-fill)

States:
| State | Trigger | What the admin sees |
|---|---|---|
| First week | No prior snapshot | Score shown, trend arrow hidden, "Come back next week..." message |
| Score < 30% | Low engagement | Score in terracotta + alert: "X classes haven't posted this week" |
| Score ≥ 70% | Healthy engagement | Score in sage green + "Parents are loving it!" |
| No parents enrolled | 0 parents added | "Add parents to start measuring engagement." + enrollment link |

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

**Screen A-9: Login**
- Route: `/login`
- Entry point: Direct URL, unauthenticated redirect
- Purpose: Admin / Principal authentication

Key elements:
- School subdomain or email field
- Password field
- [Log In] button
- "Forgot password?" link → phone number + OTP reset flow

---

## 5. Key API Contracts

All endpoints are prefixed `/api/v1/`. All authenticated requests require `Authorization: Bearer {sanctum_token}`. Multi-tenancy is enforced via middleware — `school_id` is extracted from the authenticated user, not accepted as a request parameter (to prevent tenancy bypass).

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

## 7. Out of Scope — Phase 2 and Phase 3

The following items are explicitly NOT in Phase 1. They must not be built, specced in stories, or implied in acceptance criteria.

### Phase 2 (Post First 10 Paying Customers)

- **Razorpay auto-billing** — Year 1 billing is manual invoicing only. No subscription automation, no card-on-file, no recurring charges.
- **Hindi and Tamil language support** — i18n infrastructure is built in Phase 1; string translations are Phase 2. No Hindi or Tamil strings ship in Phase 1.
- **Per-teacher and per-class engagement score breakdown** — Phase 1 ships school-level aggregate only. Drill-down by class or teacher is Phase 2.
- **HRMS** — Payroll, leave management, performance reviews. Phase 1 staff management is: name, role, class assignment only.
- **Offline-first data sync** — Phase 1 is progressive loading with stale-while-revalidate. True local-first sync for low-bandwidth markets is Phase 2.
- **On-server fine-tuned ML model for milestones** — Phase 1 uses Claude API via OpenRouter. A fine-tuned model trained on Phase 1 usage data is Phase 2.
- **Enrollment verification / billing fraud prevention** — Attendance-as-billing-source-of-truth audit is Phase 2 when auto-billing requires it.
- **Interactive quizzes and children's library** — Phase 2.
- **Live camera / daycare monitoring** — Phase 2.
- **Bus tracking** — Phase 2.
- **Infirmary and health records** — Phase 2.
- **Warehouse and supplies management** — Phase 2.
- **Teacher Training Module** — Phase 2.
- **Website Management Module** — Phase 2.
- **WhatsApp Business API (official)** — Phase 1 uses Wapi bridge with MSG91 SMS fallback. Official API migration is post-launch.
- **Marathi, Telugu, Kannada language support** — Phase 2 / Phase 3.

### Phase 3 (Franchise and Global)

- **Franchise chain enterprise sales** — Eurokids, Kidzee, Bachpan, Podar Jumbo Kids. Phase 3 outreach begins Month 10 using Phase 1-2 case studies.
- **Full white-label** — CadenceSprout branding removal for franchise chains. Phase 1 is "school logo + Powered by CadenceSprout". Full white-label architecture must be token-based from Phase 1 to enable this without a rewrite.
- **CRM integrations** — Phase 3.
- **Arabic language and RTL UI** — Dubai market, Phase 3.
- **Southeast Asia expansion** — Indonesia, Vietnam, Philippines — post India PMF (ARR > ₹1Cr, NPS ≥ 50).
- **Schema-per-tenant isolation** — Row-level tenancy is sufficient for Phase 1 and Phase 2. Franchise chains requiring schema-per-tenant isolation are Phase 3.

---

## 8. Success Metrics

### Phase 1 Launch Criteria (Month 10)

These are the pass/fail criteria that define a successful Phase 1 launch. All must be true before the product is considered launched.

| Criterion | Target | How Measured |
|---|---|---|
| Pilot school chain fully live | 1 chain, 5+ centers, daily active teachers and parents | Admin dashboard — classes with ≥1 post/day for 2 consecutive weeks |
| Parent feed adoption | ≥70% of enrolled parents active in last 7 days | Engagement score ≥70% on pilot school for 2 consecutive weeks |
| Teacher posting cadence | ≥3 posts per class per day | `posts` table — average posts/class/day over trailing 14 days |
| Self-serve onboarding live | A new school can sign up and invite teachers without founder involvement | End-to-end test: new school completes onboarding in < 15 minutes with no support contact |
| Manual invoicing live | At least 3 schools using fee management for monthly invoices | Fee invoices created and marked paid for at least 1 billing cycle |
| Teacher NPS | ≥30 | In-app NPS survey sent to teachers at Month 10 |

### Engagement Score Definition

School-level engagement score = (parents who viewed ≥1 post in the trailing 7 days ÷ total enrolled parents) × 100

Stored as a weekly snapshot in `engagement_snapshots`. Not recalculated on read. The formula and its inputs must be shared with the pilot school owner before launch so they understand what they are looking at.

### 3-Month Pilot Milestones

| Milestone | Target |
|---|---|
| Pilot school live | 1 school, 5+ centers |
| Teacher posting | ≥3 posts/class/day |
| Parent app adoption | ≥70% of enrolled parents active |
| Principal dashboard weekly use | Principal views dashboard ≥3 times/week |

### 6-Month Growth Milestones

| Milestone | Minimum | Stretch |
|---|---|---|
| Paying preschool chains | 3 chains (15+ centers) | 10 chains (50+ centers) |
| Teacher NPS | ≥30 | ≥50 |
| Parent activity definition | Opened app + viewed ≥1 post in last 7 days | — |
| Pipeline | At least 1 franchise chain in sales pipeline | — |

### 12-Month ARR Target

- 50 paying chains → ₹50L+ ARR
- Pricing at Month 12: ₹40-60/child/month (up from ₹20-30 at launch)
- Condition for price increase: 10+ paying schools live AND teacher NPS ≥ 30
- Illumine customer win: at least 1 school that switched from Illumine (moat validation)

### Leading Indicators (Weekly Tracking)

These should be monitored weekly from Day 1 of the pilot, not just at month-end reviews:

| Indicator | Healthy Signal | Warning Signal |
|---|---|---|
| Posts per class per day | ≥3 | < 1 for 3 consecutive days |
| Parent feed open rate | ≥60% of enrolled parents daily | < 30% 7-day active |
| WhatsApp switching rate | > 50% of notified parents opening app vs. staying on WhatsApp link | < 30% (see CEO Plan risk #1) |
| AI caption acceptance rate | > 60% of captions posted without teacher edit | < 30% (indicates AI quality issue) |
| Magic-link to app install conversion | ≥30% of magic-link users install the app within 7 days | < 15% (reconsider install nudge UX) |
| Face recognition accuracy | < 5% false positive rate on confirmed tags | > 10% (impacts teacher trust) |

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

*This is a Phase 1 PRD only. Phase 2 and Phase 3 features are explicitly out of scope and listed in Section 7.*
