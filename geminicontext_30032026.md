# CadenceSprout Context (Date: 30-03-2026)

This document captures the current state, architecture, design, and roadmap of **CadenceSprout**, an "All-in-One Preschool OS for India" focused on standalone preschool chains.

## 1. Project Overview & Vision
CadenceSprout replaces the fragmented stack of WhatsApp groups, paper registers, Tally, and generic ERPs/Seesaw for Indian preschools. 
- **Core Loop:** Teacher takes a 15-second video -> AI identifies children -> AI suggests developmental milestones -> AI drafts caption -> Parents see a branded, beautiful update.
- **Target Audience:** Standalone preschool chains running 2-10 centers in India.
- **Pricing Strategy:** ₹20–₹30/child/month (launch rate), scaling to ₹40–₹60/child/month. Manual invoicing in Year 1.
- **Key Differentiators vs. Competitors (like Illumine):** India-first depth, regional languages (Phase 2), NEP 2020/NCERT curriculum alignment, high-end editorial design, and WhatsApp magic-link onboarding.

## 2. Technical Stack
- **Backend API:** Laravel (PHP 8.2) + Sanctum + Horizon + Redis
- **Database:** PostgreSQL with Row Level Security (RLS) for multi-tenancy (enforcing `school_id`)
- **Mobile Apps:** React Native (iOS + Android) for Teachers and Parents
- **Web Admin:** React + Vite
- **Cloud/Infrastructure:** AWS S3 (ap-south-1 for DPDP data residency) + CloudFront
- **Real-time:** Pusher + Laravel Echo
- **AI / LLM:** OpenRouter (routing Gemini Flash to GPT-4o-mini for caption generation & milestone suggestions)
- **Face Recognition:** AWS Rekognition (server-side, gated by strict DPDP consent)
- **Notifications:** Wapi (WhatsApp bridge) with MSG91 (SMS fallback)

## 3. Product Scope (Phase 1 - 10 Months)
### Seesaw Layer (Parent Engagement)
- **Daily Feed:** Teacher posts photos/videos (optimistic UI upload with background S3 sync, client-side video compression under 50MB).
- **AI Tagging Pipeline:**
  - *Face Recognition:* Background job via Rekognition against `school_{id}` collection. Only tags children with active DPDP consent.
  - *Caption Generation:* Background job via OpenRouter. Drafts 1-2 warm sentences. Fallback to placeholder on failure.
- **Milestone Tracker:** Based on NEP 2020 Foundational Stage taxonomy (~80 indicators across 5 domains).
- **Parent Onboarding:** WhatsApp magic-links for friction-free initial access (view 3 posts before prompting app install).
- **Portfolio:** Nightly batch job to auto-generate PDFs of annual child development at year-end.

### Core ERP Layer
- **Admissions Management:** Inquiry -> Tour -> Enrollment tracking.
- **Fee Management:** Manual invoice generation and collection tracking. 
- **Attendance:** Teacher-facing daily marking with school-wide heatmaps for admins.
- **Staff & School Management:** Self-serve onboarding on cadencesprout.com, basic staff assignment (names, roles, classes).
- **Engagement Score:** Admin dashboard showing `(parents viewing ≥1 post/week) / (total parents)`.

## 4. Design System 
- **Aesthetic:** Warm, editorial, premium (not generic SaaS/edtech).
- **Colors:** Cream background (`#FAF7F2`), White surfaces (`#FFFFFF`), Sage Green primary (`#5C8B6E`), Terracotta accent (`#C4784A`).
- **Typography:** `Fraunces` (serif) for headlines and AI captions; `Inter` for UI labels, buttons, and metadata.
- **User Personas:**
  - *Sunita (Teacher):* Needs < 3 taps to post. Needs offline/low-bandwidth resilience.
  - *Meera (Parent):* Wants friction-free updates without noisy WhatsApp groups.
  - *Rajesh (Principal):* Needs a morning dashboard with clear engagement, attendance, and fee alerts.

## 5. Security, Privacy & Constraints
- **DPDP Act 2023 Compliance:** Mandatory. Granular, revocable parental consent required for (1) app usage, (2) server-side face recognition, and (3) India data residency. If face info consent is revoked, Rekognition data is deleted within 24 hours.
- **Multi-Tenancy:** PostgreSQL Row Level Security (RLS) is used. It is a critical requirement to have RLS integration tests to prevent cross-school data leakage.

## 6. Current Status & Next Steps
- **Project Phase:** Pre-build, entering implementation sprint (Month 1).
- **Completed:** Office Hours (Strategy), CEO Review (Scope), Design Review (UX), PRD & Engineering Review (Arch). `stitchprompts.md` contains detailed Google Stitch generation prompts for 15+ screens.
- **Urgent TODOs:**
  1. *AI Pair Programming Pilot:* Ship a working React web feed prototype to the pilot school using Claude Code by Week 3-4 to validate the WhatsApp switching behavior.
  2. *Legal Review:* DPDP compliance sign-off.
  3. *Taxonomy Setup:* Load NCERT/NEP 2020 milestones before AI build.
  4. *Engineering Criticals:* Write RLS integration test, DPDP gate test for Rekognition, Rekognition collection INIT on onboarding, S3 upload retry UI, and Pusher offline fallback.

*Generated from repo files: README.md, CEO_PLAN.md, DESIGN.md, ENG_REVIEW.md, PRD.md, TODOS.md, stitchprompts.md.*
