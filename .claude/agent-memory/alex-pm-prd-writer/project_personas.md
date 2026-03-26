---
name: CadenceSprout User Personas
description: Three user roles, their primary jobs-to-be-done, and key fears that shape product decisions
type: project
---

**Teacher (React Native mobile app)**
- Primary JTBD: Post class activity in ≤3 taps (camera roll → composer → POST)
- Secondary: Take attendance, see which parents viewed posts, track milestones
- Key fear: New app = more work. Must feel faster than WhatsApp.
- App access: Phone number + password login (Sanctum token, 30-day TTL)

**Parent (React Native mobile app + magic-link web view)**
- Primary JTBD: Know what my child did today without having to ask
- Secondary: React/comment, see milestone progress, receive year-end portfolio
- Key fear: Installing another app. Magic-link removes this — value before commitment.
- App access: Magic-link (no install, 3 free views) → OTP phone login → DPDP consent → feed
- Critical moment: First reaction (❤️) requires NO login — capture emotion before asking for commitment

**Admin / Principal (React + Vite web dashboard)**
- Primary JTBD: One-screen morning check — are teachers posting? Are parents engaged? Are fees collected?
- Secondary: Act on exceptions (message low-engagement teacher), manage admissions, export reports
- Key fear: Complexity. Must get the answer on the first screen.
- App access: Phone + password (or email); session-based auth for web

**Why:** These persona fears drive core UX decisions (3-tap post flow, magic-link first, dashboard engagement hero).
**How to apply:** When reviewing any feature, ask: does this make the teacher's daily job faster or slower? Does the parent have to do anything before seeing value?
