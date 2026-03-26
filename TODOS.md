# CadenceSprout — TODOS

Generated from /office-hours + /plan-ceo-review + /plan-eng-review on 2026-03-26

---

## URGENT (before build starts)

- [ ] **AI pair programming pilot** — Ship a working React web-based parent feed prototype to the pilot school using Claude Code by Week 3-4 of Month 1. Measure: what % of parents click the link vs. stay on WhatsApp. Gate: if < 30% adoption after 2 weeks, investigate before expanding full build scope.

- [ ] **DPDP Act legal review** — Assign legal counsel. Deadline: end of Month 2. Product handles photos/videos of minors — need explicit parental consent flows, data residency in India, and documented data retention/deletion policy signed off before launch.

- [ ] **Pricing validation** — Hypothesis: ₹20–₹30/child/month at launch. Validate with first 3 paying schools before setting list price. Plan: raise to ₹40–₹60/child/month at Month 12 once 10+ schools live and NPS ≥ 30.

- [ ] **NEP 2020 milestone taxonomy** — Download NCERT Foundational Stage Curriculum (FSC) document (public, 2022). Define ~80 developmental indicators across 5 domains (physical, cognitive, language, social-emotional, aesthetic). Must be loaded into the system before AI tagging is built (Month 3). Owner: Product Lead.

---

## Phase 1 (Month 1–10)

- [ ] **i18n backbone from Month 1** — Even though app launches English-only, build the i18n infrastructure (react-i18next or equivalent) from the start so Hindi + Tamil strings can be added without a refactor.

- [ ] **Manual-tag fallback for AI child identification** — AWS Rekognition face recognition on ages 3–6 in motion video is hard. Build a "tag children manually" flow as the default, with AI suggestions as an overlay. Never block posting on face ID quality.

- [ ] **Engagement score formula documentation** — Document and agree on the formula before building: School-level score = (parents who viewed ≥1 post this week / total enrolled parents) × 100. Stored as weekly snapshot. Share with pilot school owner before launch so they know what they're looking at.

- [ ] **WhatsApp Wapi reliability plan** — Wapi is an unofficial WhatsApp gateway (~95% uptime). Build SMS fallback via MSG91 from day one. Plan migration to official WhatsApp Business API within 6 months of launch.

- [ ] **Wireframe teacher posting flow** — The product lives or dies on teachers posting daily. The posting flow must be ≤3 taps from camera roll to posted. Design this before Month 3 engineering begins. Recommend: run `/plan-design-review` first.

- [ ] **Month 5–6 scope gate decision** — If behind schedule at Month 5 review: cut AI year-end portfolio (defer to Phase 2). Keep: AI tagging, milestone tracker, parent app, engagement score. Document this decision so the team doesn't debate it under pressure.

---

## Phase 2 (post first 10 paying customers)

- [ ] **Razorpay auto-billing** — Per-child/month automated billing. Year 1 is manual invoicing. Implement Razorpay subscription billing in Phase 2 with enrollment verification (attendance records as source of truth to prevent under-reporting).

- [ ] **Hindi + Tamil language support** — i18n backbone built in Phase 1. Add Hindi and Tamil string translations in Phase 2 (target Month 12). Arabic for Dubai market is Phase 3.

- [ ] **Per-teacher + per-class engagement score breakdown** — Phase 1 ships school-level only. Phase 2 adds per-class and per-teacher breakdown for principal management use.

- [ ] **White-label theme layer** — Franchise chains (Eurokids, Kidzee, etc.) will need per-chain branding. Design the theme/white-label architecture in Month 8–9 of Phase 1 so Phase 3 franchise deals don't require a rewrite.

- [ ] **Offline-first data sync** — Low-bandwidth is Phase 1 (progressive loading, compressed media). True offline-first (local-first data sync) is Phase 2 for semi-urban/rural preschool market expansion.

- [ ] **Enrollment verification mechanism** — When auto-billing starts (Phase 2), need fraud protection: alert if attendance records show more children than billed enrollment.

- [ ] **HRMS (payroll, leave, performance)** — Phase 2. Staff management in Phase 1 is names + roles + class assignment only. Design Phase 1 staff schema to accommodate HRMS fields without data migration.

---

## Phase 3 (franchise + global)

- [ ] **Franchise chain outreach** — Eurokids (~1,200 centers), Kidzee, Bachpan, Podar Jumbo Kids. Use Phase 1–2 case studies as proof. One franchise deal = instant scale. 6–18 month sales cycle — start conversations in Month 10.

- [ ] **Dubai / Arabic market** — Post India PMF (ARR > ₹1Cr, NPS ≥ 50). Arabic language + right-to-left UI support. Similar market dynamics to India (Seesaw is expensive there too).

- [ ] **Southeast Asia expansion** — Indonesia, Vietnam, Philippines. Post India PMF only.

---

## Engineering (from /plan-eng-review — must do before build)

- [ ] **RLS integration test** — Write a test proving School A's teacher cannot read School B's data. Missing `school_id` filter must return 0 rows, not leak. Write this before any feature code ships. Critical: a failure here is a DPDP data breach.

- [ ] **DPDP gate test for Rekognition** — Write a test proving `FaceRecognitionJob` skips Rekognition when `children.dpdp_consent_at IS NULL`. Must run in CI. DPDP violation risk if this fails silently.

- [ ] **Rekognition collection init on school signup** — When a school is created, auto-create its Rekognition face collection (`school_{id}`). If missing, face recognition jobs crash silently. Add to Month 1-2 school onboarding flow.

- [ ] **S3 upload retry UI** — If direct S3 upload fails (network drop), post gets stuck in `draft` with no feedback. Add: client-side retry with exponential backoff + "Upload failed — tap to retry" toast. Indian mobile networks will trigger this.

- [ ] **Pusher offline fallback** — If Pusher is down, parents miss posts until next app open. Add: on reconnect, fetch posts since `last_seen_at`. Prevents missed posts during Pusher downtime (~5% on free tier).

---

## NOT doing (explicit decisions)

- ~~No-code pilot (Glide/Softr)~~ — Replaced by AI pair programming prototype using Claude Code
- ~~Razorpay in Phase 1~~ — Year 1 is manual invoicing; auto-billing is Phase 2
- ~~ML Kit on-device face recognition~~ — ML Kit does face detection, not recognition; using AWS Rekognition server-side instead
- ~~Hindi/Tamil at launch~~ — English-first; languages are Phase 2
- ~~Rollback gate~~ — Full product mandate; Month 5–6 scope gate is the safety valve
