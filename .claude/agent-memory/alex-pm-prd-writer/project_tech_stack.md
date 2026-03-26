---
name: CadenceSprout Tech Stack (Locked)
description: All technology decisions locked after CEO + Eng Review on 2026-03-26; do not re-open these in future sessions
type: project
---

All decisions locked as of 2026-03-26. Do not re-open without explicit user instruction.

| Layer | Technology |
|---|---|
| Backend API | Laravel (PHP 8.2) + Sanctum + Horizon |
| Database | PostgreSQL + Row Level Security (school_id on every table) |
| Queue | Laravel Horizon + Redis |
| Mobile app | React Native (iOS + Android) — both teacher and parent apps |
| Web admin dashboard | React + Vite (NOT Next.js — SSR not needed) |
| Media storage | AWS S3 ap-south-1 + CloudFront CDN |
| Real-time | Pusher + Laravel Echo |
| AI/LLM | OpenRouter → Gemini Flash (primary) → GPT-4o-mini (escalation) |
| Face recognition | AWS Rekognition (server-side; ML Kit rejected — only detects, doesn't recognize) |
| Notifications | Wapi (WhatsApp) → MSG91 SMS fallback |
| CI/CD | GitHub Actions |

**Multi-tenancy:** PostgreSQL RLS enforces school_id isolation at DB layer. school_id never accepted as request param — always derived from authenticated user's token.

**AI queue architecture:**
- ai-fast (3 workers): CaptionDraftJob < 3s, MilestoneTagJob < 3s
- ai-slow (2 workers): FaceRecognitionJob < 30s
- ai-batch (1 worker, nightly): PortfolioGenerateJob

**Design system:**
- Background: #FAF7F2 (warm cream)
- Primary accent: #5C8B6E (sage green)
- Secondary accent: #C4784A (terracotta)
- Display font: Fraunces serif (captions, child names, AI drafts)
- UI font: Inter sans-serif
- Component library: React Native Paper v5 (mobile), shadcn/ui (web) — both with custom token overrides

**Why:** These are locked after CEO + Eng Review. Raising them again wastes team time. Reference these as facts.
**How to apply:** When writing specs or stories, use these technology names precisely. Do not suggest alternatives unless the user explicitly asks.
